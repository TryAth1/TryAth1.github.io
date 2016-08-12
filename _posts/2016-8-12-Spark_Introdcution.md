---
layout: post
title: Spark 介绍(翻译)
date: 2016-8-12
categories: blog
tags: [大数据]
description: 本篇是对Edx上伯克利大学的Introduction to Apache Spark的Lesson 1a的翻译
---

# Spark Introduction

[TOC]

## 1.Intro

在spark中,驱动器和执行器会进行交流,驱动器中包含了需要做的任务,然后会被分成多个子任务交给执行器去完成,最后结果返回到驱动器。

在Databricks中代码的执行是在Spark驱动器的JVM(Java Virtual Machine)中,而不是在执行器的的JVM中,而在Jupter Notebook是在它的kernel中执行的。如果没有Spark的功能被使用,那么没有任务会被分配到执行器中。

为了使用Spark和它的DataFrame API ,我们需要使用SQLContext。当运行Spark的时候,我们需要先创建一个SparkContext,然后我们可以从SparkContext创建一个SqlContext。当SparkContext创建完毕后,它会向master请求资源核的分配,master就会为你专门分配资源核,这些资源核不会被用到其他地方。当使用Databricks的时候,SparkContext和SQLContext都自动的为我们创建好了,sc是SparkContext,而sqlContext是SQLContext。

每个Spark应用都包括了一个驱动程序同时在执行器JVM上使用多个并行操作,既可以在一个集群中运行也可以在本地运行。在DataBricks中,"DataBricks Shell"就是驱动程序,而在本地运行的时候,pyspark是驱动程序。

在所有的情况下,驱动程序包含了对the main loop for the program和在集群中创建分布式的数据集并在数据集上使用transformation和action的操作。

驱动程序连接Spark使用SparkContext对象,这代表了和一个计算集群的连接。一个Spark SQL context对象是主要使用Spark Dataframe和 SQL语句的方式,一个SQLContext可以用来创建DataFrames,允许我们在数据上直接进行操作。

接下来让我们打印sqlContext来看看它的类型:

```python
#打印sqlContext的类型
type(sqlContext)
#output:pyspark.sql.context.HiveContext
```

我们可以看到类型是HiveContext,这就意味着现在和我们进行交互的Spark版本支持Hive(Hive是Hadoop的数据库语言)。用Hive来编写Spark是一个好主意,即使你没有一个Hive metastore。正如Spark项目导论所说的 ,一个HiveContext比基本的SqlContext有更多的功能,另外的一些功能包括可以使用更加复杂的HiveQL解析语句来进行查询,使用UDFs(用户自定义功能),还有从Hive 表读取数据的能力。为了使用HiveContext,我们不需要任何现存的Hive配置,所有对SqlContext有用的数据源对HiveContext仍然有效。

在pyspark或notebook的外部,SQLContext从低一级的SparkContext创建,SparkContext常用来创建RDDs(Resilient Distributed Datasets),一个RDD是Spark在内部表现数据的形式,DataFrame通常以RDDs的形式呈现。

尽管你可以和RDDs直接进行交互,但是Dataframes更好,因为它更快,并且无论你在Spark中使用什么语言(Python,R,Scala或者Java),它都是一样的。

在本次课程中,我们将很少与SparkContext进行交互,而使用的是DataFrames,但需要知道的是在pyspark或者notebook中已经存在了SparkContext,并保存在了sc变量中,通常我们可以使用sc来查看我们使用的Spark版本。

```python
#查看版本
sc.version
```

## 2.在DF中使用transformation和actions

在Spark中使用lazy evaluation,也就是说transformation不会执行,直到有actions

|              transformation              |                 actions                  |
| :--------------------------------------: | :--------------------------------------: |
| `select()`, `filter()`, `distinct()`, `dropDuplicates()`, `orderBy()`, `groupBy()` | `first()`, `take()`, `count()`, `collect()`, `show()` |

### 1.dataframe的结构

在df中,是一系列的行组成,每行由命名好的列组成,更加正式一点的定义是,df必须有一个框图,这也就是说每一列必须有名字和类型,一些数据来源有已经搭建好的框图,如RDBMs数据集,Parquet文件,NoSQL数据集如Cassandra,一些其他的数据来源没有计算机可读的框图,但是你通常可以创建一个。

## 3.分布式数据及使用collection来创建一个df

在Spark中,数据集以列表的形式呈现,而列表被分成了不同的部分储存在不同的机器上,每一部分都保存着独一无二的数据集的子集,Spark把数据集成为RDDs,甚至DF都以RDDs的形式呈现,附带另外的元文件。

一个Spark的特征是,和其他数据分析结构相比(如Hadoop),在内存中储存数据而不是在硬盘里面。这使得Spark应用运行速度快得多,因为不需要从硬盘上读取数据,下图展示了Spark如何切分数据并保存在内存中的过程。

![](http://oam2zfeyb.bkt.clouddn.com/spark.png)

### 创建DF

我们使用sqlContext.createDataFrame()

```
dataDF = sqlContext.createDataFrame(data, ('last_name', 'first_name', 'ssn', 'occupation', 'age'))
#因为df有框图,所以第二个参数传递column的name

#查看框图 schema
dataDF.printSchema()
##root
 |-- last_name: string (nullable = true)
 |-- first_name: string (nullable = true)
 |-- ssn: string (nullable = true)
 |-- occupation: string (nullable = true)
 |-- age: long (nullable = true)
 
##注册新创建的DF
sqlContext.registerDataFrameAsTable(dataDF,"dataframe")

##被分成了几个部分
dataDF.rdd.getNumPartitions()

```

## 4.关于DF 和 Queries

当你使用DF或者SparkSQL,你在建立一个查询计划,每一个对DF的操作都对查询计划添加个一些信息,当你最后使用actions,对于之前的操作都被出发了,会发生下面几件事情:

①.Spark的Catalyst 优化器分析查询计划(未优化的逻辑查询计划),希望能够优化它,优化包括但不限于重新安排和结合filter()操作来提高效率,将decimal操作转换成效率更高的long整形操作,将一些操作根据数据集进行转化,如filter()操作转换成where语句,如果数据来源是传统的SQL RDBMS,这些优化语句的结果就是一个经过优化的逻辑查询计划。

②.一旦Catalyst有了一个优化过的逻辑查询计划,接着它会从中创建多个物理计划,特别的,它在低一级的Spark的RDDs上执行查询。

③.Catalyst通过损耗优化目标来决定使用哪个物理计划,这就是说它会选择效率最高的哪一个。

④.最后,一旦物理RDD执行计划被建立完成,Spark就会执行这个工作

你可以使用explain()来查看使用的查询计划,默认展示最后的查询计划,你也可以传递True参数来获得所有的计划。

让我们使用一组transformation来看查询计划是怎么影响改变好的DF,不用太在意这看起来像乱码,当你随着ApacheSpark 获得更多的经验的时候,explain()会帮助你更好的理解你的DF操作。

## 5.使用select从每个value 减 1

到目前为止,我们创建了一个分布式的DF,被分成了多个部分,每个部分都被储存在我们集群中的单个机器上。让我们看看当我们对数据集进行基础操作的时候会发生什么?许多有用的数据集操作可以简单描述成对数据集里的每个item进行做了些什么,这些平行的数据非常的方便因为每个在数据集的item都能被单独的进行处理,互不影响。因此,Spark可以平行化进行操作。

其中使用最多的的DF操作是select(),它和SQL的select语句有几分想像,你可以从df中选出特定的列,你甚至可以使用select()基于现有的DF列创建新的列,我们可以使用select()来创建一个新的列减少现有的age列。

select()是一个transformation,它返回一个新的DF,包含了原来的DF以及操作添加到查询计划里面,但它在集群中没有执行任何东西,当转换DF的时候,我们建立了一个查询计划,查询计划会被优化,按照RDDs进行执行,被Spark执行只有我们使用action操作的时候。

```python
# Transform dataDF through a select transformation and rename the newly created '(age -1)' column to 'age'
# Because select is a transformation and Spark uses lazy evaluation, no jobs, stages,
# or tasks will be launched when we run this code.
subDF = dataDF.select('last_name', 'first_name', 'ssn', 'occupation', (dataDF.age - 1).alias('age'))
```

```
使用subDF.explain(True) 来查看进程
```

## 6.使用collect来查看数据

为了看到列表元素减1,我们需要在驱动器里创建一个新的列表,数据来源于分布在执行器支点的数据,为了完成这个操作,我们在DF后面加上collect(),collect()通常在transformation后面使用,确保返回到驱动器的是一小部分的数据,这可以被完成因为数据返回到驱动器的必须和驱动器可利用的内存相匹配,不然会崩溃。

collect()是我们碰到的第一个action操作,action操作使得Spark执行lazy变换操作,计算等会由action返回的值。在我们的例子中,这意味着任务现在会被分配执行createDataFrame,select,和collect操作。

看看我们之前进行的操作:

```
dataDF = sqlContext.createDataFrame(data, ('last_name', 'first_name', 'ssn', 'occupation', 'age'))
subDF = dataDF.select('last_name', 'first_name', 'ssn', 'occupation', (dataDF.age - 1).alias('age'))
results = subDF.collect()
print results
##前两步因为没有action操作,所以实际上是不执行的
#一开始在createDataFrame的时候列表数据被分成了多个部分,然后在这多个部分中进行了select的操作和计算,最后collect()触发这一系列的操作,结果合并返回到驱动器里面
subDF.show() #返回前20行,并且更加美观,
subDF.show(n=30,truncate=False) #显示前30行,不缩略
display(subDF) #显示更加美观

```

## 7.count()

每个部分计算它的计数,并在驱动器里面进行求和。

如果说之前我们没有collect()操作,那么count()作为actions同样也会触发前面的操作。

```python
print dataDF.count()
print subDF.count()
#结果是一样的
```

## 8.使用filter transformation 以及用collect()来查看数据

filter()方法是一个transformation操作,它从输入的DF创造了一个新的符合过滤条件的DF

```python
filteredDF = subDF.filter(subDF.age < 10)
filteredDF.show(truncate=False)
filteredDF.count()
```

## 9.Python lambda function和User Defined Functions

Python支持使用一行的函数

lambda函数从LISP借鉴而来,支持无论什么时候需要函数,他们在语句构成上只有一句话,lambda是一种方式,可以无论什么时候使用不需要语义,	你总是可以定义一个正常的函数,但是使用lambda是等价的而且更加小巧,理论上你可以使用lambda,在你想要压缩你的代码,并且不需要循环进行使用。

这里,代替为filter()定义一个单独的函数,我们将使用在句中的lambda()函数,同时我们会注册那个lambda作为一个Spark User-Defined-Function(UDF),UDF是一个函数的包装纸,允许让我们在DF 查询中进行使用。

```python
from pyspark.sql.types import BooleanType
less_ten = udf(lambda s: s < 10, BooleanType())
lambdaDF = subDF.filter(less_ten(subDF.age))
lambdaDF.show()
lambdaDF.count()

# Let's collect the even values less than 10
even = udf(lambda s: s % 2 == 0, BooleanType())
evenDF = lambdaDF.filter(even(lambdaDF.age))
evenDF.show()
evenDF.count()
```

## 10.其他的DF action

### 1.查看数据

一个有用的方法观察数据集的前几行来获得一些初步的信息可以通过actions如first(),take(),show(),返回结果取决于数据集是怎么分区的,用take(n)代替collect(),或用first()来查看第一行数据

### 2.orderBy

```python
dataDF.orderBy(dataDF['age'])  # sort by age in ascending order; returns a new DataFrame
dataDF.orderBy(dataDF.last_name.desc()) # sort by last name in descending order

# Get the five oldest people in the list. To do that, sort by age in descending order.
display(dataDF.orderBy(dataDF.age.desc()).take(5))
```

在这里的表达式里面,我们不能使用dataDF.orderBy("age".desc()) ,因为"age"是字符串没有desc()方法。所以要写成dataDF.orderBy(dataDF.age.desc())

### 3.distinct 和 drop duplicates

```python
tempDF = sqlContext.createDataFrame([("Joe", 1), ("Joe", 1), ("Anna", 15), ("Anna", 12), ("Ravi", 5)], ('name', 'score'))
tempDF.distinct().show()
print dataDF.dropDuplicates(['first_name', 'last_name']).count()
```

### 4.drop

```
dataDF.drop('occupation').drop('age').show()
```

### 5.groupBy

groupBy是最有用的transformation之一,它允许你在DF上使用aggregations。

不像其他的一些DF transformation,groupBy不返回一个新的DF,而是一个特殊的GroupedData,包含了多个函数

最常使用的是count(),也有min(),max(),avg()

这些函数方法创建一个新的列,返回一个新的DF

```python
dataDF.groupBy('occupation').count().show(truncate=False)
dataDF.groupBy().avg('age').show(truncate=False)
#+--------+
|avg(age)|
+--------+
|24.4108 |
+--------+
print "Maximum age: {0}".format(dataDF.groupBy().max('age').first()[0])
print "Minimum age: {0}".format(dataDF.groupBy().min('age').first()[0])
#Maximum age: 47
#Minimum age: 1
```

### 6.sample

当分析数据的时候,sample() transformation通常非常有用,它从数据集随机返回数据,有一个withReplacement的变量,当=True的时候决定了是否从母数据集中每一次抽取的样本是一样的,还有一个变量是fraction,决定了你想返回的 数据比例,还有一个seed参数,允许你选择一个seed 值,那么seed值一样的时候,返回的结果是一样的。

```python
sampledDF = dataDF.sample(withReplacement=False, fraction=0.10)
print sampledDF.count()
sampledDF.show()
```

## 11.Cache DF和保存选项

### 1.cache()

为了效率,Spark把DF保存在内存中,正式一点的 说法是在内存中以RDDs的形式执行DF,通过把数据内容存放在内存里,Spark可以快速的获取数据,无论怎么样,内存毕竟是有限的, 所以如果你在内存中存放了太多的分支,Spark会自动的从内存中删掉一部分来为新的留出空间,但是如果你在之后重新想和删掉的部分进行交互,那么Spark会重新创建,但这需要一定的时间。

所以如果你准备使用一个DF不止一次,最好使用cache()让Spark来把这个DF保存在内存中,无论怎么样,你需要用action来触发,如collect()或count()在cache()执行之前,换句话说,cache是lazy的,它仅仅告诉Spark这个DF是需要被保存的,所以需要使用action来具象化数据,这样下次你使用DF的时候,Spark会使用保存好的数据,而不是从原始数据重新创建一个DF。

```python
# Cache the DataFrame
filteredDF.cache()
# Trigger an action
print filteredDF.count()
# Check if it is cached
print filteredDF.is_cached
```

### 2.unpersist

Spark会自动释放内存,所以如果一个DF需要重复被使用的话,那么最好用cache(),但是在用完之后,我们也可以使用unpersist()来释放DF,使得不再占用内存

```python
# If we are done with the DataFrame we can unpersist it so that its memory can be reclaimed
filteredDF.unpersist()
# Check if it is cached
print filteredDF.is_cached
```

## 12.一些建议

​在写代码的 时候,推荐以以下形式书写

```python
 df2 = df1.transformation1()
 df2.action1()
 df3 = df2.transformation2()
 df3.action2()
 ##更加可读的代码
 # Final version
from pyspark.sql.functions import *
(dataDF
 .filter(dataDF.age > 20)
 .select(concat(dataDF.first_name, lit(' '), dataDF.last_name), dataDF.occupation)
 .show(truncate=False)
 )
```

