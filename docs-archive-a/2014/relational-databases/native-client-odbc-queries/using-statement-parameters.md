---
title: Using 语句参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577591"
---
# <a name="using-statement-parameters"></a><span data-ttu-id="091be-102">使用语句参数</span><span class="sxs-lookup"><span data-stu-id="091be-102">Using Statement Parameters</span></span>
  <span data-ttu-id="091be-103">参数在 SQL 语句中是一种变量，它使 ODBC 应用程序能够：</span><span class="sxs-lookup"><span data-stu-id="091be-103">A parameter is a variable in an SQL statement that can enable an ODBC application to:</span></span>  
  
-   <span data-ttu-id="091be-104">有效地为表中的列提供值。</span><span class="sxs-lookup"><span data-stu-id="091be-104">Efficiently provide values for columns in a table.</span></span>  
  
-   <span data-ttu-id="091be-105">在构造查询条件时增强用户交互。</span><span class="sxs-lookup"><span data-stu-id="091be-105">Enhance user interaction in constructing query criteria.</span></span>  
  
-   <span data-ttu-id="091be-106">管理**text**、 **ntext**和**image**数据以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定于数据的 C 数据类型。</span><span class="sxs-lookup"><span data-stu-id="091be-106">Manage **text**, **ntext**, and **image** data and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types.</span></span>  
  
 <span data-ttu-id="091be-107">例如， **part**表包含名为**PartID**、 **Description**和**Price**的列。</span><span class="sxs-lookup"><span data-stu-id="091be-107">For example, a **Parts** table has columns named **PartID**, **Description**, and **Price**.</span></span> <span data-ttu-id="091be-108">若要添加不带参数的部分，需要构造 SQL 语句，例如：</span><span class="sxs-lookup"><span data-stu-id="091be-108">To add a part without parameters requires constructing an SQL statement such as:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 <span data-ttu-id="091be-109">尽管使用已知的值集插入一行时可接受此语句，但要求应用程序插入多行时使用此语句会很不适合。</span><span class="sxs-lookup"><span data-stu-id="091be-109">Although this statement is acceptable for inserting one row with a known set of values, it is awkward when an application is required to insert several rows.</span></span> <span data-ttu-id="091be-110">ODBC 可通过使应用程序将 SQL 语句中的任何数据值替换为参数标记来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="091be-110">ODBC addresses this by letting an application to replace any data value in an SQL statement by a parameter maker.</span></span> <span data-ttu-id="091be-111">这种参数标记由问号 (?) 表示。</span><span class="sxs-lookup"><span data-stu-id="091be-111">This is denoted by a question mark (?).</span></span> <span data-ttu-id="091be-112">在下面的示例中，三个数据值被替换为参数标记：</span><span class="sxs-lookup"><span data-stu-id="091be-112">In the following example, three data values are replaced with parameter markers:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="091be-113">参数标记然后被绑定到应用程序变量。</span><span class="sxs-lookup"><span data-stu-id="091be-113">The parameter markers are then bound to application variables.</span></span> <span data-ttu-id="091be-114">若要插入新行，应用程序只需设置变量的值并执行此语句。</span><span class="sxs-lookup"><span data-stu-id="091be-114">To insert a new row, the application has only to set the values of the variables and execute the statement.</span></span> <span data-ttu-id="091be-115">然后，驱动程序检索变量的当前值并将其发送至数据源。</span><span class="sxs-lookup"><span data-stu-id="091be-115">The driver then retrieves the current values of the variables and sends them to the data source.</span></span> <span data-ttu-id="091be-116">如果多次执行此语句，则应用程序可通过准备此语句使该进程更加有效。</span><span class="sxs-lookup"><span data-stu-id="091be-116">If the statement is executed multiple times, the application can make the process even more efficient by preparing the statement.</span></span>  
  
 <span data-ttu-id="091be-117">每个参数标记均按从左到右的顺序由其分配至参数的序号引用。</span><span class="sxs-lookup"><span data-stu-id="091be-117">Each parameter marker is referenced by its ordinal number assigned to the parameters from left to right.</span></span> <span data-ttu-id="091be-118">在 SQL 语句中，最左侧的参数标记的序号值为 1；下一个的序号为 2，以此类推。</span><span class="sxs-lookup"><span data-stu-id="091be-118">The leftmost parameter marker in an SQL statement has an ordinal value of 1; the next one is ordinal 2, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="091be-119">本节内容</span><span class="sxs-lookup"><span data-stu-id="091be-119">In This Section</span></span>  
  
-   [<span data-ttu-id="091be-120">绑定参数</span><span class="sxs-lookup"><span data-stu-id="091be-120">Binding Parameters</span></span>](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="091be-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="091be-121">See Also</span></span>  
 [<span data-ttu-id="091be-122">&#40;ODBC&#41;执行查询</span><span class="sxs-lookup"><span data-stu-id="091be-122">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
