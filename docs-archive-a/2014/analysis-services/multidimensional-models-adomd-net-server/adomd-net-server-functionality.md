---
title: ADOMD.NET 服务器功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f00215c6bcc0104c920be29e0837288a469b252e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687320"
---
# <a name="adomdnet-server-functionality"></a><span data-ttu-id="babeb-102">ADOMD.NET 服务器功能</span><span class="sxs-lookup"><span data-stu-id="babeb-102">ADOMD.NET Server Functionality</span></span>
  <span data-ttu-id="babeb-103">所有 ADOMD.NET 服务器对象都可对服务器上的数据和元数据提供只读访问。</span><span class="sxs-lookup"><span data-stu-id="babeb-103">All ADOMD.NET server objects provide read-only access to the data and metadata on the server.</span></span> <span data-ttu-id="babeb-104">若要检索数据和元数据，则可使用 ADOMD.NET 服务器对象模型，因为该服务器对象模型不支持架构行集。</span><span class="sxs-lookup"><span data-stu-id="babeb-104">To retrieve data and metadata, you use the ADOMD.NET server object model as the server object model does not support schema rowsets.</span></span>  
  
 <span data-ttu-id="babeb-105">使用 ADOMD.NET 服务器对象，可以 (UDF) 或存储过程创建用户定义的函数 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="babeb-105">With ADOMD.NET server objects, you can create a user defined function (UDF) or a stored procedure for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="babeb-106">这些进程内方法是通过使用多维表达式 (MDX)、数据挖掘扩展插件 (DMX) 或 SQL 之类的语言创建的查询语句调用的。</span><span class="sxs-lookup"><span data-stu-id="babeb-106">These in-process methods are called through query statements created in languages such as Multidimensional Expressions (MDX), Data Mining Extensions (DMX), or SQL.</span></span> <span data-ttu-id="babeb-107">这些进程内方法还可提供附加功能而不会有网络通信的延迟。</span><span class="sxs-lookup"><span data-stu-id="babeb-107">These in-process methods also provide added functionality without the latencies associated with network communications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="babeb-108">[Microsoft.analysisservices.sharepoint.integration.dll. AdomdServer. AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120))对象仅支持 DMX。</span><span class="sxs-lookup"><span data-stu-id="babeb-108">The [Microsoft.AnalysisServices.AdomdServer.AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) object only supports DMX.</span></span>  
  
## <a name="what-is-a-udf"></a><span data-ttu-id="babeb-109">什么是 UDF？</span><span class="sxs-lookup"><span data-stu-id="babeb-109">What is a UDF?</span></span>  
 <span data-ttu-id="babeb-110">*UDF*是一种具有以下特征的方法：</span><span class="sxs-lookup"><span data-stu-id="babeb-110">A *UDF* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="babeb-111">可以在查询上下文中调用 UDF。</span><span class="sxs-lookup"><span data-stu-id="babeb-111">You can call the UDF in the context of a query.</span></span>  
  
-   <span data-ttu-id="babeb-112">UDF 可以使用任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="babeb-112">The UDF can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="babeb-113">UDF 可以返回各种类型的数据。</span><span class="sxs-lookup"><span data-stu-id="babeb-113">The UDF can return various types of data.</span></span>  
  
 <span data-ttu-id="babeb-114">下面的示例使用了虚拟的 UDF `FinalSalesNumber`：</span><span class="sxs-lookup"><span data-stu-id="babeb-114">The following example uses the fictional UDF, `FinalSalesNumber`:</span></span>  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a><span data-ttu-id="babeb-115">什么是存储过程？</span><span class="sxs-lookup"><span data-stu-id="babeb-115">What is a Stored Procedure?</span></span>  
 <span data-ttu-id="babeb-116">*存储过程*是一种具有以下特征的方法：</span><span class="sxs-lookup"><span data-stu-id="babeb-116">A *stored procedure* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="babeb-117">您可以使用 MDX [call](/sql/mdx/mdx-data-manipulation-call)语句自行调用存储过程。</span><span class="sxs-lookup"><span data-stu-id="babeb-117">You call a stored procedure on its own with the MDX [CALL](/sql/mdx/mdx-data-manipulation-call) statement.</span></span>  
  
-   <span data-ttu-id="babeb-118">存储过程可以使用任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="babeb-118">A stored procedure can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="babeb-119">存储过程可以返回数据集、`IDataReader` 或空结果。</span><span class="sxs-lookup"><span data-stu-id="babeb-119">A stored procedure can return a dataset, an `IDataReader`, or an empty result.</span></span>  
  
 <span data-ttu-id="babeb-120">下面的示例使用了虚拟的存储过程 `FinalSalesNumbers`：</span><span class="sxs-lookup"><span data-stu-id="babeb-120">The following example uses the fictional stored procedure, `FinalSalesNumbers`:</span></span>  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a><span data-ttu-id="babeb-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="babeb-121">See Also</span></span>  
 [<span data-ttu-id="babeb-122">ADOMD.NET 服务器编程</span><span class="sxs-lookup"><span data-stu-id="babeb-122">ADOMD.NET Server Programming</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
