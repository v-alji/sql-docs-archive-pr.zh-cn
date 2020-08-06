---
title: 访问存储过程中的查询上下文 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682428"
---
# <a name="accessing-query-context-in-stored-procedures"></a><span data-ttu-id="43f27-102">访问存储过程中的查询上下文</span><span class="sxs-lookup"><span data-stu-id="43f27-102">Accessing Query Context in Stored Procedures</span></span>
  <span data-ttu-id="43f27-103">存储过程的执行上下文可以作为 ADOMD.NET 服务器对象模型的 `Context` 对象出现在存储过程代码中。</span><span class="sxs-lookup"><span data-stu-id="43f27-103">The execution context of a stored procedure is available within the code of the stored procedure as the `Context` object of the ADOMD.NET server object model.</span></span> <span data-ttu-id="43f27-104">这是只读上下文，存储过程不能修改它。</span><span class="sxs-lookup"><span data-stu-id="43f27-104">This is a read-only context and cannot be modified by the stored procedure.</span></span> <span data-ttu-id="43f27-105">此对象的以下属性可用。</span><span class="sxs-lookup"><span data-stu-id="43f27-105">The following properties are available on this object.</span></span>  
  
|<span data-ttu-id="43f27-106">属性</span><span class="sxs-lookup"><span data-stu-id="43f27-106">Property</span></span>|<span data-ttu-id="43f27-107">类型</span><span class="sxs-lookup"><span data-stu-id="43f27-107">Type</span></span>|<span data-ttu-id="43f27-108">说明</span><span class="sxs-lookup"><span data-stu-id="43f27-108">Description</span></span>|  
|--------------|----------|-----------------|  
|<span data-ttu-id="43f27-109">**CurrentCube**</span><span class="sxs-lookup"><span data-stu-id="43f27-109">**CurrentCube**</span></span>|<span data-ttu-id="43f27-110">多维数据集</span><span class="sxs-lookup"><span data-stu-id="43f27-110">Cube</span></span>|<span data-ttu-id="43f27-111">当前查询上下文的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="43f27-111">The cube for the current query context.</span></span>|  
|<span data-ttu-id="43f27-112">**CurrentDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="43f27-112">**CurrentDatabaseName**</span></span>|<span data-ttu-id="43f27-113">String</span><span class="sxs-lookup"><span data-stu-id="43f27-113">String</span></span>|<span data-ttu-id="43f27-114">当前数据库的标识符。</span><span class="sxs-lookup"><span data-stu-id="43f27-114">The identifier of the current database.</span></span>|  
|<span data-ttu-id="43f27-115">**CurrentConnection**</span><span class="sxs-lookup"><span data-stu-id="43f27-115">**CurrentConnection**</span></span>|<span data-ttu-id="43f27-116">连接</span><span class="sxs-lookup"><span data-stu-id="43f27-116">Connection</span></span>|<span data-ttu-id="43f27-117">对当前上下文中连接对象的引用。</span><span class="sxs-lookup"><span data-stu-id="43f27-117">A reference to the connection object in the current context.</span></span>|  
|<span data-ttu-id="43f27-118">**通过**</span><span class="sxs-lookup"><span data-stu-id="43f27-118">**Pass**</span></span>|<span data-ttu-id="43f27-119">Integer</span><span class="sxs-lookup"><span data-stu-id="43f27-119">Integer</span></span>|<span data-ttu-id="43f27-120">当前上下文的传递号。</span><span class="sxs-lookup"><span data-stu-id="43f27-120">The pass number for the current context.</span></span>|  
  
 <span data-ttu-id="43f27-121">在存储过程中使用多维表达式 (MDX) 对象模型时，将会存在 `Context` 对象。</span><span class="sxs-lookup"><span data-stu-id="43f27-121">The `Context` object exists when the Multidimensional Expressions (MDX) object model is used in a stored procedure.</span></span> <span data-ttu-id="43f27-122">而在客户端上使用 MDX 对象模型时，该对象不可用。</span><span class="sxs-lookup"><span data-stu-id="43f27-122">It is not available when the MDX object model is used on a client.</span></span> <span data-ttu-id="43f27-123">`Context` 对象不会显式传递给存储过程，也不会被存储过程返回。</span><span class="sxs-lookup"><span data-stu-id="43f27-123">The `Context` object is not explicitly passed to or returned by the stored procedure.</span></span> <span data-ttu-id="43f27-124">它只在存储过程的执行期间可用。</span><span class="sxs-lookup"><span data-stu-id="43f27-124">It is available during the execution of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f27-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43f27-125">See Also</span></span>  
 <span data-ttu-id="43f27-126">[多维模型程序集管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="43f27-126">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="43f27-127">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="43f27-127">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
