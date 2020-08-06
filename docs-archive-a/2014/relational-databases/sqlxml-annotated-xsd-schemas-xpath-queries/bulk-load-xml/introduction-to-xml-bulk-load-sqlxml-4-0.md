---
title: SQLXML 4.0)  (XML 大容量加载简介 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f3e0e78edd967e5fcb7377312c1811d34cb1ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682780"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="b22b6-102">XML 大容量加载简介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b22b6-102">Introduction to XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="b22b6-103">XML 大容量加载是一个独立的 COM 对象，可用于将半结构化 XML 数据加载到 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="b22b6-103">XML Bulk Load is a stand-alone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="b22b6-104">您可以使用 INSERT 语句和 OPENXML 函数将 XML 数据插入到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库；但是，当需要插入大量 XML 数据时，大容量加载实用工具提供了更好的性能。</span><span class="sxs-lookup"><span data-stu-id="b22b6-104">You can insert XML data into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database by using an INSERT statement and the OPENXML function; however, the Bulk Load utility provides better performance when you need to insert large amounts of XML data.</span></span>  
  
 <span data-ttu-id="b22b6-105">XML 大容量加载对象模型的 Execute 方法采用两个参数：</span><span class="sxs-lookup"><span data-stu-id="b22b6-105">The Execute method of the XML Bulk Load object model takes two parameters:</span></span>  
  
-   <span data-ttu-id="b22b6-106">带批注的 XML 架构定义 (XSD) 或 XML 数据精简 (XDR) 架构。</span><span class="sxs-lookup"><span data-stu-id="b22b6-106">An annotated XML Schema Definition (XSD) or XML-Data Reduced (XDR) schema.</span></span> <span data-ttu-id="b22b6-107">XML 大容量加载实用工具解释此映射架构和在标识要插入 XML 数据的 SQL Server 表时在该架构中指定的批注。</span><span class="sxs-lookup"><span data-stu-id="b22b6-107">The XML Bulk Load utility interprets this mapping schema and the annotations that are specified in the schema in identifying the SQL Server tables into which the XML data is to be inserted.</span></span>  
  
-   <span data-ttu-id="b22b6-108">XML 文档或文档片段（文档片段是没有单个顶级元素的文档）。</span><span class="sxs-lookup"><span data-stu-id="b22b6-108">An XML document or document fragment (a document fragment is a document without a single top-level element).</span></span> <span data-ttu-id="b22b6-109">可以指定 XML 大容量加载可读取的文件名或流。</span><span class="sxs-lookup"><span data-stu-id="b22b6-109">A file name or a stream from which XML Bulk Load can read can be specified.</span></span>  
  
 <span data-ttu-id="b22b6-110">XML 大容量加载解释此映射架构，并标识要插入 XML 数据的表。</span><span class="sxs-lookup"><span data-stu-id="b22b6-110">XML Bulk Load interprets the mapping schema and identifies the table(s) into which the XML data is to be inserted.</span></span>  
  
 <span data-ttu-id="b22b6-111">本部分假定您熟悉以下 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能：</span><span class="sxs-lookup"><span data-stu-id="b22b6-111">It is assumed that you are familiar with the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="b22b6-112">带批注的 XSD 架构和 XDR 架构。</span><span class="sxs-lookup"><span data-stu-id="b22b6-112">Annotated XSD and XDR schemas.</span></span> <span data-ttu-id="b22b6-113">有关带批注的 XSD 架构的详细信息，请参阅[&#40;SQLXML 4.0&#41;中带批注的 Xsd 架构简介](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b22b6-113">For more information about annotated XSD schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="b22b6-114">有关带批注的 XDR 架构的信息，请参阅[SQLXML 4.0&#41;中 &#40;弃用的带批注 Xdr 架构](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b22b6-114">For information about annotated XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="b22b6-115">大容量插入机制，例如 [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT 语句和 bcp 实用工具。</span><span class="sxs-lookup"><span data-stu-id="b22b6-115">bulk insert mechanisms, such as the [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement and the bcp utility.</span></span> <span data-ttu-id="b22b6-116">有关详细信息，请参阅[&#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)和[bcp 实用工具](../../../tools/bcp-utility.md)BULK INSERT。</span><span class="sxs-lookup"><span data-stu-id="b22b6-116">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) and [bcp Utility](../../../tools/bcp-utility.md).</span></span>  
  
## <a name="streaming-of-xml-data"></a><span data-ttu-id="b22b6-117">XML 数据流式处理</span><span class="sxs-lookup"><span data-stu-id="b22b6-117">Streaming of XML Data</span></span>  
 <span data-ttu-id="b22b6-118">由于源 XML 文档可能很大，因此无法将整个文档读入内存以进行大容量加载处理。</span><span class="sxs-lookup"><span data-stu-id="b22b6-118">Because the source XML document can be large, the entire document is not read into memory for bulk load processing.</span></span> <span data-ttu-id="b22b6-119">XML 大容量加载而是将 XML 数据解释为流并读取它。</span><span class="sxs-lookup"><span data-stu-id="b22b6-119">Instead, XML Bulk Load interprets the XML data as a stream and reads it.</span></span> <span data-ttu-id="b22b6-120">当该实用工具读取数据时，该工具标识数据库表，并根据 XML 数据源生成相应记录，然后再将这些记录发送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以便插入。</span><span class="sxs-lookup"><span data-stu-id="b22b6-120">As the utility reads the data, it identifies the database table(s), generates the appropriate record(s) from the XML data source, and then sends the record(s) to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="b22b6-121">例如，以下源 XML 文档包含 **\<Customer>** 元素和 **\<Order>** 子元素：</span><span class="sxs-lookup"><span data-stu-id="b22b6-121">For example, the following source XML document consists of **\<Customer>** elements and **\<Order>** child elements:</span></span>  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 <span data-ttu-id="b22b6-122">XML 大容量加载读取元素时，将为 **\<Customer>** Customertable 生成记录。</span><span class="sxs-lookup"><span data-stu-id="b22b6-122">As XML Bulk Load reads the **\<Customer>** element, it generates a record for the Customertable.</span></span> <span data-ttu-id="b22b6-123">读取 **\</Customer>** 结束标记后，XML 大容量加载会将该记录插入到中的表中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b22b6-123">When it reads the **\</Customer>** end tag, XML Bulk Load inserts that record into the table in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b22b6-124">同样，在读取 **\<Order>** 元素时，XML 大容量加载将为 orderaddeddate 生成一条记录，然后在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 读取结束标记时将该记录插入到表中 **\</Order>** 。</span><span class="sxs-lookup"><span data-stu-id="b22b6-124">In the same way, when it reads the **\<Order>** element, XML Bulk Load generates a record for the Ordertable, and then inserts that record into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table upon reading the **\</Order>** end tag.</span></span>  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a><span data-ttu-id="b22b6-125">事务和非事务 XML 大容量加载操作</span><span class="sxs-lookup"><span data-stu-id="b22b6-125">Transacted and Nontransacted XML Bulk Load Operations</span></span>  
 <span data-ttu-id="b22b6-126">XML 大容量加载可以以事务或非事务模式运行。</span><span class="sxs-lookup"><span data-stu-id="b22b6-126">XML Bulk Load can operate in either a transacted or a nontransacted mode.</span></span> <span data-ttu-id="b22b6-127">如果在非事务模式下进行大容量加载，则性能通常是最佳的：也就是说，Transaction 属性设置为 FALSE) 并且满足以下条件之一：</span><span class="sxs-lookup"><span data-stu-id="b22b6-127">Performance is usually optimal if you are bulk loading in a nontransacted mode: that is, the Transaction property is set to FALSE) and either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="b22b6-128">要向其大容量加载数据的表为空，且没有任何索引。</span><span class="sxs-lookup"><span data-stu-id="b22b6-128">The tables into which the data is bulk loaded are empty with no indexes.</span></span>  
  
-   <span data-ttu-id="b22b6-129">表具有数据和唯一索引。</span><span class="sxs-lookup"><span data-stu-id="b22b6-129">The tables have data and unique indexes.</span></span>  
  
 <span data-ttu-id="b22b6-130">非事务方法不能保证在大容量加载进程发生错误时回滚（但是可以进行部分回滚）。</span><span class="sxs-lookup"><span data-stu-id="b22b6-130">The nontransacted approach does not guarantee a rollback if something goes wrong in the bulk load process (although partial rollbacks can happen).</span></span> <span data-ttu-id="b22b6-131">非事务大容量加载适用于数据库为空的情况。</span><span class="sxs-lookup"><span data-stu-id="b22b6-131">The nontransacted bulk load is appropriate when the database is empty.</span></span> <span data-ttu-id="b22b6-132">因此，如果发生错误，您可以清除数据库并重新启动 XML 大容量加载。</span><span class="sxs-lookup"><span data-stu-id="b22b6-132">Therefore, if something does go wrong, you can clean the database and start XML Bulk Load again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b22b6-133">在非事务模式下，XML 大容量加载使用并提交默认的内部事务。</span><span class="sxs-lookup"><span data-stu-id="b22b6-133">In nontransacted mode, XML Bulk Load uses a default internal transaction and commits it.</span></span> <span data-ttu-id="b22b6-134">当 Transaction 属性设置为 TRUE 时，XML 大容量加载不会对此事务调用 commit。</span><span class="sxs-lookup"><span data-stu-id="b22b6-134">When the Transaction property is set to TRUE, XML Bulk Load does not call commit on this transaction.</span></span>  
  
 <span data-ttu-id="b22b6-135">如果将 Transaction 属性设置为 TRUE，则 XML 大容量加载会创建临时文件，每个文件对应于映射架构中标识的每个表。</span><span class="sxs-lookup"><span data-stu-id="b22b6-135">If the Transaction property is set to TRUE, XML Bulk Load creates temporary files, one for each table that is identified in the mapping schema.</span></span> <span data-ttu-id="b22b6-136">XML 大容量加载首先将源 XML 文档中的记录存储到这些临时文件中。</span><span class="sxs-lookup"><span data-stu-id="b22b6-136">XML Bulk Load first stores the records from the source XML document in these temporary files.</span></span> <span data-ttu-id="b22b6-137">接着，[!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT 语句检索这些文件中的上述记录，并将其存储到相应的表中。</span><span class="sxs-lookup"><span data-stu-id="b22b6-137">Then, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement retrieves these records from the files and stores them in the corresponding tables.</span></span> <span data-ttu-id="b22b6-138">可以使用 TempFilePath 属性指定这些临时文件的位置。</span><span class="sxs-lookup"><span data-stu-id="b22b6-138">You can specify the location for these temporary files by using the TempFilePath property.</span></span> <span data-ttu-id="b22b6-139">您必须确保用于 XML 大容量加载的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帐户有权访问此路径。</span><span class="sxs-lookup"><span data-stu-id="b22b6-139">You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account used with XML Bulk Load has access to this path.</span></span> <span data-ttu-id="b22b6-140">如果未指定 TempFilePath 属性，则将使用在 TEMP 环境变量中指定的默认文件路径来创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="b22b6-140">If the TempFilePath property is not specified, the default file path that is specified in the TEMP environment variable is used to create the temporary files.</span></span>  
  
 <span data-ttu-id="b22b6-141">如果将 Transaction 属性设置为 FALSE (默认设置) ，XML 大容量加载将使用 OLE DB 接口 IRowsetFastLoad 大容量加载数据。</span><span class="sxs-lookup"><span data-stu-id="b22b6-141">If the Transaction property is set to FALSE (the default setting), XML Bulk Load uses the OLE DB interface IRowsetFastLoad to bulk load the data.</span></span>  
  
 <span data-ttu-id="b22b6-142">如果 ConnectionString 属性设置连接字符串，并且 Transaction 属性设置为 TRUE，则 XML 大容量加载会在其自己的事务上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="b22b6-142">If the ConnectionString property sets the connection string, and the Transaction property is set to TRUE, XML Bulk Load operates in its own transaction context.</span></span> <span data-ttu-id="b22b6-143">（例如，XML 大容量加载启动其自己的事务，并根据需要提交或回滚。）</span><span class="sxs-lookup"><span data-stu-id="b22b6-143">(For example, XML Bulk Load starts its own transaction, and commits or rolls back as appropriate.)</span></span>  
  
 <span data-ttu-id="b22b6-144">如果 ConnectionCommand 属性设置了与现有连接对象的连接，并且 Transaction 属性设置为 TRUE，则在成功或失败的情况下，XML 大容量加载不会发出 COMMIT 或 ROLLBACK 语句。</span><span class="sxs-lookup"><span data-stu-id="b22b6-144">If the ConnectionCommand property sets the connection with an existing connection object and the Transaction property is set to TRUE, XML Bulk Load does not issue a COMMIT or ROLLBACK statement in the case of a success or a failure, respectively.</span></span> <span data-ttu-id="b22b6-145">如果出现错误，XML 大容量加载则返回相应的错误消息。</span><span class="sxs-lookup"><span data-stu-id="b22b6-145">If there is an error, XML Bulk Load returns the appropriate error message.</span></span> <span data-ttu-id="b22b6-146">执行 COMMIT 或 ROLLBACK 语句由启动该大容量加载的客户端决定。</span><span class="sxs-lookup"><span data-stu-id="b22b6-146">The decision to issue a COMMIT or ROLLBACK statement is left to the client that initiated the bulk load.</span></span> <span data-ttu-id="b22b6-147">用于 XML 大容量加载的 connection 对象应为 ICommand 类型或 ADO 命令对象。</span><span class="sxs-lookup"><span data-stu-id="b22b6-147">The connection object that is used for XML Bulk Load should be of type ICommand or be an ADO command object.</span></span>  
  
 <span data-ttu-id="b22b6-148">在 SQLXML 4.0 中，不能将 ConnectionObject 与 Transaction 属性设置为 FALSE 一起使用。</span><span class="sxs-lookup"><span data-stu-id="b22b6-148">In SQLXML 4.0, a ConnectionObject cannot be used with the Transaction property set to FALSE.</span></span> <span data-ttu-id="b22b6-149">ConnectionObject 不支持非事务模式，因为无法在传入的会话中打开多个 IRowsetFastLoad 接口。</span><span class="sxs-lookup"><span data-stu-id="b22b6-149">The nontransacted mode is not supported with a ConnectionObject because it is impossible to open more than one IRowsetFastLoad interface on a passed-in session.</span></span>  
  
  
