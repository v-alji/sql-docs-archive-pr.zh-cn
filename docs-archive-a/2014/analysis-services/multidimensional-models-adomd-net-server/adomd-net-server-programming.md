---
title: ADOMD.NET 服务器编程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 7f7ff5be-3826-43a5-b94d-ddeec5ddb2eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 522478af0b19f1745d80f167e40345d4751136b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682429"
---
# <a name="adomdnet-server-programming"></a><span data-ttu-id="2d48a-102">ADOMD.NET 服务器编程</span><span class="sxs-lookup"><span data-stu-id="2d48a-102">ADOMD.NET Server Programming</span></span>
  <span data-ttu-id="2d48a-103">ADOMD.NET 的 ADOMD.NET 服务器组件位于 `Microsoft.AnalysisServices.AdomdServer` 命名空间中（在 msmgdsrv.dll 中）。</span><span class="sxs-lookup"><span data-stu-id="2d48a-103">The ADOMD.NET server components of ADOMD.NET reside within the `Microsoft.AnalysisServices.AdomdServer` namespace (in msmgdsrv.dll).</span></span> <span data-ttu-id="2d48a-104">您可以使用这些服务器组件来创建自定义多维表达式 (MDX) 函数和在的实例上运行的存储过程 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2d48a-104">You use these server components to create custom Multidimensional Expressions (MDX) functions and stored procedures that are run on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="2d48a-105">服务器对象可提供查询多维数据集和挖掘模型以及在给定上下文计算表达式的功能。</span><span class="sxs-lookup"><span data-stu-id="2d48a-105">The server objects provide the capabilities for querying cubes and mining models, and for evaluating expressions in a given context.</span></span> <span data-ttu-id="2d48a-106">创建自定义函数和存储过程的优点包括执行速度快、部署集中且可维护性得以改进。</span><span class="sxs-lookup"><span data-stu-id="2d48a-106">The benefits for creating custom functions and stored procedures include fast execution, centralized deployment, and improved maintainability.</span></span>  
  
 <span data-ttu-id="2d48a-107">下表中的主题将有助于您开发 ADOMD.NET 服务器应用程序。</span><span class="sxs-lookup"><span data-stu-id="2d48a-107">The topics in the following table will help you develop ADOMD.NET server applications.</span></span>  
  
|<span data-ttu-id="2d48a-108">主题</span><span class="sxs-lookup"><span data-stu-id="2d48a-108">Topic</span></span>|<span data-ttu-id="2d48a-109">说明</span><span class="sxs-lookup"><span data-stu-id="2d48a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2d48a-110">ADOMD.NET 服务器功能</span><span class="sxs-lookup"><span data-stu-id="2d48a-110">ADOMD.NET Server Functionality</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-functionality)|<span data-ttu-id="2d48a-111">介绍 ADOMD.NET 服务器对象的用途</span><span class="sxs-lookup"><span data-stu-id="2d48a-111">Describes the uses for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="2d48a-112">ADOMD.NET 服务器对象体系结构</span><span class="sxs-lookup"><span data-stu-id="2d48a-112">ADOMD.NET Server Object Architecture</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-object-architecture)|<span data-ttu-id="2d48a-113">介绍 ADOMD.NET 服务器对象的对象体系结构。</span><span class="sxs-lookup"><span data-stu-id="2d48a-113">Describes the object architecture for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="2d48a-114">用户定义函数和存储过程</span><span class="sxs-lookup"><span data-stu-id="2d48a-114">User Defined Functions and Stored Procedures</span></span>](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures)|<span data-ttu-id="2d48a-115">引导您完成创建用户定义函数或存储过程的步骤。</span><span class="sxs-lookup"><span data-stu-id="2d48a-115">Walks you through the process of creating a user defined function or stored Procedure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d48a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d48a-116">See Also</span></span>  
 <span data-ttu-id="2d48a-117">[ADOMD.NET 客户端编程](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span><span class="sxs-lookup"><span data-stu-id="2d48a-117">[ADOMD.NET Client Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span></span>  
 [<span data-ttu-id="2d48a-118">使用 ADOMD.NET 进行开发</span><span class="sxs-lookup"><span data-stu-id="2d48a-118">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
  
