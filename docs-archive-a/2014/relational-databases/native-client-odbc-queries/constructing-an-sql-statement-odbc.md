---
title: 构造 SQL 语句 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c454f936c49335555ca09b190e4d604c9fbad64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577612"
---
# <a name="constructing-an-sql-statement-odbc"></a><span data-ttu-id="43d73-102">构造 SQL 语句 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="43d73-102">Constructing an SQL Statement (ODBC)</span></span>
  <span data-ttu-id="43d73-103">ODBC 应用程序基本上通过执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来执行所有的数据库访问。</span><span class="sxs-lookup"><span data-stu-id="43d73-103">ODBC applications perform almost all of their database access by executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="43d73-104">这些语句的形式取决于应用程序的要求。</span><span class="sxs-lookup"><span data-stu-id="43d73-104">The form of these statements depends on the application requirements.</span></span> <span data-ttu-id="43d73-105">SQL 语句可以采用下列方式构造：</span><span class="sxs-lookup"><span data-stu-id="43d73-105">SQL statements can be constructed in the following ways:</span></span>  
  
-   <span data-ttu-id="43d73-106">硬编码</span><span class="sxs-lookup"><span data-stu-id="43d73-106">Hard-coded</span></span>  
  
     <span data-ttu-id="43d73-107">应用程序作为固定任务执行的静态语句。</span><span class="sxs-lookup"><span data-stu-id="43d73-107">Static statements performed by an application as a fixed task.</span></span>  
  
-   <span data-ttu-id="43d73-108">运行时构造</span><span class="sxs-lookup"><span data-stu-id="43d73-108">Constructed at run time</span></span>  
  
     <span data-ttu-id="43d73-109">运行时构造的 SQL 语句使用户可以通过使用常用子句（如 SELECT、WHERE 和 ORDER BY）来调整语句。</span><span class="sxs-lookup"><span data-stu-id="43d73-109">SQL statements constructed at run time that enable the user to tailor the statement by using common clauses, such as SELECT, WHERE, and ORDER BY.</span></span> <span data-ttu-id="43d73-110">这包括用户输入的即席查询。</span><span class="sxs-lookup"><span data-stu-id="43d73-110">This includes ad hoc queries entered by users.</span></span>  
  
 <span data-ttu-id="43d73-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]客户端 ODBC 驱动程序仅对不受支持的 ODBC 和 ISO 语法 [!INCLUDE[ssDE](../../includes/ssde-md.md)] （驱动程序转换为）分析 SQL 语句 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="43d73-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC driver parses SQL statements only for ODBC and ISO syntax not directly supported by the [!INCLUDE[ssDE](../../includes/ssde-md.md)], which the driver transforms into [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="43d73-112">其他所有 SQL 语法将按原样传递给[!INCLUDE[ssDE](../../includes/ssde-md.md)]，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在此确定该语法是否为有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="43d73-112">All other SQL syntax is passed to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] unchanged, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will determine if it is valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="43d73-113">这种方法具有两个好处：</span><span class="sxs-lookup"><span data-stu-id="43d73-113">This approach yields two benefits:</span></span>  
  
-   <span data-ttu-id="43d73-114">降低开销</span><span class="sxs-lookup"><span data-stu-id="43d73-114">Reduced overhead</span></span>  
  
     <span data-ttu-id="43d73-115">由于驱动程序只需扫描较少的 ODBC 和 ISO 子句，因而最大程度地减少了其处理开销。</span><span class="sxs-lookup"><span data-stu-id="43d73-115">Processing overhead for the driver is minimized because it only has to scan for a small set of ODBC and ISO clauses.</span></span>  
  
-   <span data-ttu-id="43d73-116">灵活性</span><span class="sxs-lookup"><span data-stu-id="43d73-116">Flexibility</span></span>  
  
     <span data-ttu-id="43d73-117">程序员可以调整其应用程序的可移植性。</span><span class="sxs-lookup"><span data-stu-id="43d73-117">Programmers can tailor the portability of their applications.</span></span> <span data-ttu-id="43d73-118">若要增强针对多个数据库的可移植性，可优先使用 ODBC 和 ISO 语法。</span><span class="sxs-lookup"><span data-stu-id="43d73-118">To enhance portability against multiple databases, use primarily ODBC and ISO syntax.</span></span> <span data-ttu-id="43d73-119">若要使用特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的增强功能，可使用相应的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法。</span><span class="sxs-lookup"><span data-stu-id="43d73-119">To use enhancements specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the appropriate [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span> <span data-ttu-id="43d73-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序支持完整的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法，因此基于 ODBC 的应用程序可以利用中的所有功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="43d73-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the complete [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax so ODBC-based applications can take advantage of all the features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="43d73-121">SELECT 语句中的列列表应当只包含执行当前任务所需的列。</span><span class="sxs-lookup"><span data-stu-id="43d73-121">The column list in a SELECT statement should contain only the columns required to perform the current task.</span></span> <span data-ttu-id="43d73-122">这样做不仅可减少通过网络发送的数据量，还可降低数据库更改对应用程序的影响。</span><span class="sxs-lookup"><span data-stu-id="43d73-122">Not only does this reduce the amount of data sent across the network, but also it reduces the effect of database changes on the application.</span></span> <span data-ttu-id="43d73-123">如果应用程序未引用表中的列，则应用程序不受对该列所做任何更改的影响。</span><span class="sxs-lookup"><span data-stu-id="43d73-123">If an application does not reference a column from a table, then the application is not affected by any changes made to that column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d73-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43d73-124">See Also</span></span>  
 [<span data-ttu-id="43d73-125">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="43d73-125">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
