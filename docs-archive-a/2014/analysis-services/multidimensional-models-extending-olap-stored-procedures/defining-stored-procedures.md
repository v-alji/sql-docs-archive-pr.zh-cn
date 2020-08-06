---
title: 定义存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689653"
---
# <a name="defining-stored-procedures"></a><span data-ttu-id="fb1d4-102">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="fb1d4-102">Defining Stored Procedures</span></span>
  <span data-ttu-id="fb1d4-103">您可以使用存储过程从调用外部例程 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-103">You can use stored procedures to call external routines from [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fb1d4-104">您可以在任何公共语言运行时 (CLR) 语言（例如 C、C++、C#、Visual Basic 或 Visual Basic .NET）中编写由存储过程调用的外部例程。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-104">You can write an external routines called by a stored procedure in any common language runtime (CLR) language, such as C, C++, C#, Visual Basic, or Visual Basic .NET.</span></span> <span data-ttu-id="fb1d4-105">存储过程可以一次创建并从许多上下文中进行调用，例如其他存储过程、计算度量值或客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-105">A stored procedure can be created once and called from many contexts, such as other stored procedures, calculated measures, or client applications.</span></span> <span data-ttu-id="fb1d4-106">程序集通过使通用代码可以一次开发并存储在单个位置中，简化 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库开发和实现。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-106">Stored procedures simplify [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="fb1d4-107">存储过程可用来向应用程序中添加 MDX 的本机功能未提供的商业功能。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-107">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="fb1d4-108">本节提供了解、设计和实现存储过程所需的信息。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-108">This section provides the information necessary to understand, design, and implement stored procedures.</span></span>  
  
|<span data-ttu-id="fb1d4-109">主题</span><span class="sxs-lookup"><span data-stu-id="fb1d4-109">Topic</span></span>|<span data-ttu-id="fb1d4-110">说明</span><span class="sxs-lookup"><span data-stu-id="fb1d4-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fb1d4-111">设计存储过程</span><span class="sxs-lookup"><span data-stu-id="fb1d4-111">Designing Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|<span data-ttu-id="fb1d4-112">介绍如何设计用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的程序集。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-112">Describes how to design assemblies for use with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fb1d4-113">创建存储过程</span><span class="sxs-lookup"><span data-stu-id="fb1d4-113">Creating Stored Procedures</span></span>](creating-stored-procedures.md)|<span data-ttu-id="fb1d4-114">介绍如何为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 创建程序集。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-114">Describes how to create assemblies for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fb1d4-115">调用存储过程</span><span class="sxs-lookup"><span data-stu-id="fb1d4-115">Calling Stored Procedures</span></span>](calling-stored-procedures.md)|<span data-ttu-id="fb1d4-116">提供有关如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中使用程序集的信息。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-116">Provides information on how to use assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fb1d4-117">访问存储过程中的查询上下文</span><span class="sxs-lookup"><span data-stu-id="fb1d4-117">Accessing Query Context in Stored Procedures</span></span>](accessing-query-context-in-stored-procedures.md)|<span data-ttu-id="fb1d4-118">介绍如何使用程序集访问作用域和上下文信息。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-118">Describes how to access scope and context information with assemblies.</span></span>|  
|[<span data-ttu-id="fb1d4-119">设置存储过程的安全性</span><span class="sxs-lookup"><span data-stu-id="fb1d4-119">Setting Security for Stored Procedures</span></span>](setting-security-for-stored-procedures.md)|<span data-ttu-id="fb1d4-120">介绍如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中配置程序集的安全性。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-120">Describes how to configure security for assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fb1d4-121">调试存储过程</span><span class="sxs-lookup"><span data-stu-id="fb1d4-121">Debugging Stored Procedures</span></span>](debugging-stored-procedures.md)|<span data-ttu-id="fb1d4-122">介绍了如何在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中调试程序集。</span><span class="sxs-lookup"><span data-stu-id="fb1d4-122">Describes how to debug assemblies in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb1d4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb1d4-123">See Also</span></span>  
 [<span data-ttu-id="fb1d4-124">多维模型程序集管理</span><span class="sxs-lookup"><span data-stu-id="fb1d4-124">Multidimensional Model Assemblies Management</span></span>](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
