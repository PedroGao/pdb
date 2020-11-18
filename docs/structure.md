# 项目结构和代码阅读

> 在每个项目接手之前一定要适当阅读当前项目结构和代码！

## 概述

`simple-db-hw` 是 MIT 6.830 的数据库课程实验，用于实现一个简单的数据库。

## 代码

- AbstractDbFileIterator.java 
    Helper for implementing DbFileIterators. Handles hasNext()/next() logic.
    帮助我们实现 DbFileIterators，即数据库文件迭代器。用于处理 `hasNext` 和 `next` 逻辑。
- Aggregate.java
    The Aggregation operator that computes an aggregate (e.g., sum, avg, max, min). 
    Note that we only support aggregates over a single column, grouped by a single column.
    聚合操作，用于 sum，avg，max，min 的计算。
    注意：我们仅支持一个列（单个字段）的聚合操作和分组（group by）。
- Aggregator.java
    The common interface for any class that can compute an aggregate over a list of Tuples.
    公共接口，用于在元组列表上作聚合操作  
- BTreeChecker.java
    This class is only used for error-checking code.
    B树检查器
- BTreeEntry.java
    Each instance of BTreeEntry stores one key and two child page ids.
    B树节点，每一个节点都存储了一个 key 和两个子页 ids。
- BTreeFileEncoder.java
    BTreeFileEncoder reads a comma delimited text file and converts it to pages of binary data in the appropriate format for simpledb B+ tree pages.
    B树文件解码器，读数据文件并将其转换为 B+树的页    
- BTreeFile.java
    BTreeFile is an implementation of a DbFile that stores a B+ tree.
    B树文件，DbFile 的一种实现，存储 B+ 树
- BTreeHeaderPage.java
    Each instance of BTreeHeaderPage stores data for one page of a BTreeFile and implements the Page interface that is used by BufferPool.
    B+树头部页，每一个B+树头部页头部页都保存了 BTreeFile 中的一页（头部）数据。BTreeHeaderPage 实现了 Page 接口，被 BufferPool 使用。
- BTreeInternalPage.java
    Each instance of BTreeInternalPage stores data for one page of a BTreeFile and implements the Page interface that is used by BufferPool.
    B+树内部数据页，存储了 BTreeFile 中的一页数据，实现了 Page 接口，被 BufferPool 使用
- BTreeLeafPage.java
    Each instance of BTreeLeafPage stores data for one page of a BTreeFile and implements the Page interface that is used by BufferPool.
    B+树页子页
- BTreePageId.java
     Unique identifier for BTreeInternalPage, BTreeLeafPage, BTreeHeaderPage and BTreeRootPtrPage objects. 
     内存页，页子页，头部页和指针页的唯一 ID。
- BTreePage.java
     Each instance of BTreeInternalPage stores data for one page of a BTreeFile and implements the Page interface that is used by BufferPool.
     B+树页的虚基类。
- BTreeRootPtrPage.java
    BTreeRootPtrPage stores the pointer to the root node used in the B+ tree and implements Page Interface that is used by BufferPool.
    BTreeRootPtrPage 存储了指向B+树根节点的指针，实现了 Page 接口，被 BufferPool 使用。
- BTreeScan.java
    BTreeScan is an operator which reads tuples in sorted order according to a predicate.
    BTreeScan 是一个根据条件(predicate)顺序读取元组的操作子。
- BTreeUtility.java
    Helper methods used for testing and implementing random features. 
    B+树帮助函数
- BufferPool.java
    BufferPool manages the reading and writing of pages into memory from disk. Access methods call into it to retrieve pages, and it fetches
    pages from the appropriate location.
    核心类，管理读取和写入内存中的页到磁盘。访问方法取回数据页，并且获取数据页在合适的位置。
- Catalog.java
    The Catalog keeps track of all available tables in the database and their associated schemas.
    Catalog 保存了所有在数据库中可用的表和相关的范式(schemas)。
- CostCard.java
    Class returned by JoinOptimizer#computeCostAndCardOfSubplan specifying the cost and cardinality of the optimal plan represented by plan.
    执行计划中的消耗和基数，优化计划。
- Database.java
    Database is a class that initializes several static variables used by the database system.
    核心类，数据库，初始化一些静态变量用于数据库系统
- DbException.java
    Generic database exception class
    通用的数据库异常类
- DbFileIterator.java
    DbFileIterator is the iterator interface that all SimpleDB Dbfile should implement.
    数据库文件接口，迭代器接口。
- DbFile.java
    The interface for database files on disk. Each table is represented by a single DbFile. DbFiles can fetch pages and iterate through tuples.
    磁盘数据库文件接口。每一个表都被表现为一个数据库文件，数据库文件可以获取数据页和迭代元组。
- DeadlockException.java
    Exception that is thrown when a deadlock occurs.
    死锁一场。
- Debug.java
    Debug is a utility class that wraps println statements and allows more or less command line output to be turned on.
    基础 Debug 类，允许或多或少的命令行被打开，其实就是 debug 日志。
- Delete.java
    The delete operator. Delete reads tuples from its child operator and removes them from the table they belong to.
    删除操作。从孩子操作子中读取元组并且删除它们。
- Field.java
    Interface for values of fields in tuples in SimpleDB.
    字段类接口；元组中字段的值。
- Filter.java
    Filter is an operator that implements a relational select.
    Operator 过滤器；关系选择的操作。
- HashEquiJoin.java
    The Join operator implements the relational join operation.
    Operator join 操作。
- HeapFileEncoder.java
    HeapFileEncoder reads a comma delimited text file or accepts an array of tuples and converts it to 
    pages of binary data in the appropriate format for simpledb heap pages.
    HeapFile 解码器。
- HeapFile.java
     HeapFile is an implementation of a DbFile that stores a collection of tuples in no particular order.
     DbFile 的一种实现，存储无序的元组集合。
- HeapPageId.java
    Unique identifier for HeapPage objects.
    HeapPage 的唯一标识。
- HeapPage.java
    Each instance of HeapPage stores data for one page of HeapFiles and implements the Page interface that is used by BufferPool.
    Page 的一种实现，HeapFile 由多个 HeapPage 实现。
- IndexOpIterator.java
    IndexDBIterator is the interface that index access methods implement in SimpleDb.
    索引操作接口。
- IndexPredicate.java
    IndexPredicate compares a field which has index on it against a given value IndexOpIterator.
    索引断言，用于比较字段。
- Insert.java
    Inserts tuples read from the child operator into the tableId specified in the constructor.
    插入 Operator。
- IntegerAggregator.java
    Knows how to compute some aggregate over a set of IntFields.
    整数聚合。
- IntField.java
    Instance of Field that stores a single integer.
    整数字段。
- IntHistogram.java
    A class to represent a fixed-width histogram over a single integer-based field.
    固定宽度的直方图，在整数字段的基础上。
- Join.java
    The Join operator implements the relational join operation.
    Join 聚合 operator。
- JoinOptimizer.java
    The JoinOptimizer class is responsible for ordering a series of joins optimally, 
    and for selecting the best instantiation of a join for a given logical plan.
    聚合优化器。
- JoinPredicate.java
    JoinPredicate compares fields of two tuples using a predicate. JoinPredicate is most likely used by the Join operator.
    Join 断言。比较两个元组的字段。
- LogFile.java
    LogFile implements the recovery subsystem of SimpleDb. 
    日志文件，用于 SimpleDb 的恢复子系统，类似于 MySQL 的 bin-log。
- LogicalFilterNode.java
    A LogicalFilterNode represents the parameters of a filter in the WHERE clause of a query. 
    逻辑过滤节点。表示 WHERE 语句上的参数。
- LogicalJoinNode.java
    A LogicalJoinNode represens the state needed of a join of two tables in a LogicalQueryPlan.
    逻辑聚合节点。两个表之间的聚合操作。
- LogicalPlan.java
    LogicalPlan represents a logical query plan that has been through the parser and is ready to be processed by the optimizer.
    逻辑执行计划。表示一个已经通过了解析器，并准备被优化器处理的执行计划。
- LogicalScanNode.java
    A LogicalScanNode represents table in the FROM list in a LogicalQueryPlan.
    逻辑扫描节点（AST 树上）。FROM 语句上的参数。
- LogicalSelectListNode.java
    A LogicalSelectListNode represents a clause in the select list in a LogicalQueryPlan.
    逻辑 select 列表节点。select 语句上的参数。
- LogicalSubplanJoinNode.java
    A LogicalSubplanJoinNode represens the state needed of a join of a table to a subplan in a LogicalQueryPlan.
    子聚合语句节点。
- OperatorCardinality.java
    A utility class, which computes the estimated cardinalities of an operator tree.
    基础类。用于预估操作树的基数。
- Operator.java
    Abstract class for implementing operators. 
    操作子的虚基类。
- OpIterator.java
    OpIterator is the iterator interface that all SimpleDB operators should implement.
    迭代器接口，所有的 SimpleDB 操作子都需要实现这个接口。
- OrderBy.java
    OrderBy is an operator that implements a relational ORDER BY.
    排序操作子。
- PageId.java
    PageId is an interface to a specific page of a specific table. 
    页ID，接口，唯一标识，一个特定表中的特定页。
- Page.java
    Page is the interface used to represent pages that are resident in the BufferPool. 
    页接口，表示在 BufferPool 中存在的数据页。
- Parser.java
    SQL 解析器。
- ParsingException.java
    解析一场。
- Permissions.java
    Class representing requested permissions to a relation/file.
    数据库文件的访问权限，只读还是读写。
- PlanCache.java
    A PlanCache is a helper class that can be used to store the best way to order a given set of joins.
    帮助类，存储排序 join 的最佳路径
- Predicate.java
    Predicate compares tuples to a specified Field value.
    断言，通过特定的字段来比较元组
- Project.java
    Project is an operator that implements a relational projection.
    Project 操作子。
- Query.java
    Query is a wrapper class to manage the execution of queries. 
    管理查询的执行。
- QueryPlanVisualizer.java
    查询计划可视化。
- RecordId.java
    A RecordId is a reference to a specific tuple on a specific page of a specific table.
    记录 id。
- SeqScan.java
    SeqScan is an implementation of a sequential scan access method that reads each tuple of a table in no particular order.
    线性扫描，在没有任何排序的情况下，阅读数据表的每一行数据。
- SimpleDb.java
    启动类，SimpleDB
- StringAggregator.java
    Knows how to compute some aggregate over a set of StringFields.
    字符串聚合操作。 
- StringField.java
    Instance of Field that stores a single String of a fixed length.
    定长的字符串字段。
- StringHistogram.java
    A class to represent a fixed-width histogram over a single String-based field.
    字符串字段直方图。
- TableStats.java
    TableStats represents statistics about base tables in a query.
    数据表状态，性能指标。 
- TransactionAbortedException.java
    Exception that is thrown when a transaction has aborted.
    事物中止异常。
- TransactionId.java
    TransactionId is a class that contains the identifier of a transaction.
    事物 ID。
- Transaction.java
    Transaction encapsulates information about the state of a transaction and manages transaction commit / abort.
    事物类。提交或者中止。
- TupleDesc.java
    TupleDesc describes the schema of a tuple.
    描述元组的范式。即记录中字段的类型。
- TupleIterator.java
   记录迭代器。
- Tuple.java
    元组，即表记录。
- Type.java
    字段类型。整数类型还是字符串类型。
- Utility.java
    Helper methods used for testing and implementing random features.
    帮助方法。

## 注意

- tuple 对应数据表中的一条记录，一条记录包含多个字段值。

## 资料

- 一个大佬的总结笔记：https://blog.csdn.net/hjw199666/article/details/103824797。