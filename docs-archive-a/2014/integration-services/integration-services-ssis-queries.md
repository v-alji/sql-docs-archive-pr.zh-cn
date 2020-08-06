---
title: Integration Services (SSIS) 查询 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Query Builder [Integration Services]
- queries [Integration Services]
- statements [Integration Services]
- queries [Integration Services], about queries in packages
ms.assetid: 8822bd29-4575-46c8-92a0-1a39bc2604c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5119ff27606ce4e43f65cc129f3caac764e78e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586859"
---
# <a name="integration-services-ssis-queries"></a><span data-ttu-id="dfbdc-102">Integration Services (SSIS) 查询</span><span class="sxs-lookup"><span data-stu-id="dfbdc-102">Integration Services (SSIS) Queries</span></span>
  <span data-ttu-id="dfbdc-103">执行 SQL 任务、OLE DB 源、OLE DB 目标以及查找转换都可以使用 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-103">The Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation can use SQL queries.</span></span> <span data-ttu-id="dfbdc-104">在执行 SQL 任务中，SQL 语句可以创建、更新和删除数据库对象与数据；运行存储过程以及执行 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-104">In the Execute SQL task, the SQL statements can create, update, and delete database objects and data; run stored procedures; and perform SELECT statements.</span></span> <span data-ttu-id="dfbdc-105">在 OLE DB 源和查找转换中，SQL 语句通常为 SELECT 语句或 EXEC 语句。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-105">In the OLE DB source and the Lookup transformation, the SQL statements are typically SELECT statements or EXEC statements.</span></span> <span data-ttu-id="dfbdc-106">后者经常用于运行可返回结果集的存储过程。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-106">The latter most frequently run stored procedures that return result sets.</span></span>  
  
 <span data-ttu-id="dfbdc-107">可以对查询进行分析，以确定它是否有效。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-107">A query can be parsed to establish whether it is valid.</span></span> <span data-ttu-id="dfbdc-108">如果分析的查询使用到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的连接，则在分析、执行该查询后，执行结果（成功或失败）将分配给分析结果。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-108">When parsing a query that uses a connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the query is parsed, executed, and the execution outcome (success or failure) is assigned to the parsing outcome.</span></span> <span data-ttu-id="dfbdc-109">如果该查询使用的是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]之外的数据连接，则仅分析该语句。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-109">If the query uses a connection to a data other than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the statement is parsed only.</span></span>  
  
 <span data-ttu-id="dfbdc-110">SQL 语句可以通过直接在设计器中输入来定义，或通过指定文件连接或包含该语句的变量来定义。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-110">The SQL statement can be defined either by entering it directly in the designer, or by specifying a file connection or a variable that contains the statement.</span></span>  
  
## <a name="direct-input-sql"></a><span data-ttu-id="dfbdc-111">直接输入 SQL</span><span class="sxs-lookup"><span data-stu-id="dfbdc-111">Direct Input SQL</span></span>  
 <span data-ttu-id="dfbdc-112">查询生成器可用于执行 SQL 任务的用户界面中、OLE DB 源、OLE DB 目标和查找转换中。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-112">Query Builder is available in the user interface for the Execute SQL task, the OLE DB source, the OLE DB destination, and the Lookup transformation.</span></span> <span data-ttu-id="dfbdc-113">查询生成器提供下列优势：</span><span class="sxs-lookup"><span data-stu-id="dfbdc-113">Query Builder offers the following advantages:</span></span>  
  
-   <span data-ttu-id="dfbdc-114">以直观方式工作或使用 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-114">Work visually or with SQL commands.</span></span>  
  
     <span data-ttu-id="dfbdc-115">查询生成器包括多个图形窗格和一个文本窗格，前者用于直观地编写查询，后者用于显示查询的 SQL 文本。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-115">Query Builder includes graphical panes that compose your query visually and a text pane that displays the SQL text of your query.</span></span> <span data-ttu-id="dfbdc-116">您既可以在图形窗格中工作，也可以在文本窗格中工作。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-116">You can work in either the graphical or text panes.</span></span> <span data-ttu-id="dfbdc-117">查询生成器会同步这两个视图，因此查询文本和图形表示形式始终匹配。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-117">Query Builder synchronizes the views so that the query text and graphical representation always match.</span></span>  
  
-   <span data-ttu-id="dfbdc-118">联接相关表。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-118">Join related tables.</span></span>  
  
     <span data-ttu-id="dfbdc-119">如果将多个表添加到查询中，查询生成器将自动确定这些表之间的关系，并构造适当的联接命令。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-119">If you add more than one table to your query, Query Builder automatically determines how the tables are related and constructs the appropriate join command.</span></span>  
  
-   <span data-ttu-id="dfbdc-120">查询或更新数据库。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-120">Query or update databases.</span></span>  
  
     <span data-ttu-id="dfbdc-121">可以使用查询生成器利用 Transact-SQL SELECT 语句来返回数据，或使用查询生成器来创建可更新、添加或删除数据库记录的查询。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-121">You can use Query Builder to return data using Transact-SQL SELECT statements, or to create queries that update, add, or delete records in a database.</span></span>  
  
-   <span data-ttu-id="dfbdc-122">即时查看和编辑结果。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-122">View and edit results immediately.</span></span>  
  
     <span data-ttu-id="dfbdc-123">可以执行查询，使用网格中可滚动浏览和编辑数据库中记录的记录集。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-123">You can execute your query and work with a recordset in a grid that lets you scroll through and edit records in the database.</span></span>  
  
 <span data-ttu-id="dfbdc-124">尽管表面上看查询生成器的作用仅限于创建 SELECT 查询，但您可以在文本窗格中键入其他类型的 SQL 语句，例如 DELETE 和 UPDATE。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-124">Although Query Builder is visually limited to creating SELECT queries, you can type the SQL for other types of statements such as DELETE and UPDATE statements in the text pane.</span></span> <span data-ttu-id="dfbdc-125">图形窗格将自动更新，以反映您所键入的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-125">The graphical pane is automatically updated to reflect the SQL statement that you typed.</span></span>  
  
 <span data-ttu-id="dfbdc-126">通过在任务流或数据流组件对话框中或“属性”窗口中键入查询，您还可以提供直接输入。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-126">You can also provide direct input by typing the query in the task or data flow component dialog box or the Properties window.</span></span>  
  
 <span data-ttu-id="dfbdc-127">有关详细信息，请参阅 [Query Builder](../../2014/integration-services/query-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-127">For more information, see [Query Builder](../../2014/integration-services/query-builder.md).</span></span>  
  
## <a name="sql-in-files"></a><span data-ttu-id="dfbdc-128">文件形式的 SQL</span><span class="sxs-lookup"><span data-stu-id="dfbdc-128">SQL in Files</span></span>  
 <span data-ttu-id="dfbdc-129">执行 SQL 任务的 SQL 语句还可以驻留在单独的文件中。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-129">The SQL statement for the Execute SQL task can also reside in a separate file.</span></span> <span data-ttu-id="dfbdc-130">例如，您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的查询编辑器等工具来编写查询，将查询保存到文件，然后在运行包时从该文件读取查询。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-130">For example, you can write queries using tools such as the Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], save the query to a file, and then read the query from the file when running a package.</span></span> <span data-ttu-id="dfbdc-131">该文件可以只包含要运行的 SQL 语句以及注释。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-131">The file can contain only the SQL statements to run and comments.</span></span> <span data-ttu-id="dfbdc-132">若要使用存储在文件中的 SQL 语句，您必须提供指定文件名和位置的文件连接。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-132">To use a SQL statement stored in a file, you must provide a file connection that specifies the file name and location.</span></span> <span data-ttu-id="dfbdc-133">有关详细信息，请参阅 [File Connection Manager](connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-133">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="sql-in-variables"></a><span data-ttu-id="dfbdc-134">变量形式的 SQL</span><span class="sxs-lookup"><span data-stu-id="dfbdc-134">SQL in Variables</span></span>  
 <span data-ttu-id="dfbdc-135">如果执行 SQL 任务中 SQL 语句的源是一个变量，您需要提供包含该查询的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-135">If the source of the SQL statement in the Execute SQL task is a variable, you provide the name of the variable that contains the query.</span></span> <span data-ttu-id="dfbdc-136">该变量的 Value 属性包含查询文本。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-136">The Value property of the variable contains the query text.</span></span> <span data-ttu-id="dfbdc-137">可以将该变量的 ValueType 属性设置为字符串数据类型，然后键入 SQL 语句或将该语句复制到 Value 属性中。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-137">You set the ValueType property of the variable to a string data type and then type or copy the SQL statement into the Value property.</span></span> <span data-ttu-id="dfbdc-138">有关详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)和[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="dfbdc-138">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
  
