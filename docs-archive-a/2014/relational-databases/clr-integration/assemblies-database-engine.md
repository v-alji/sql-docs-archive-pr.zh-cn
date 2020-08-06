---
title: 程序集 (数据库引擎) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edb18ccfa9954fe52093f87948f956c2eacc1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691255"
---
# <a name="assemblies-database-engine"></a><span data-ttu-id="491cc-102">程序集（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="491cc-102">Assemblies (Database Engine)</span></span>
  <span data-ttu-id="491cc-103">本节中的主题旨在帮助您了解、设计和实现程序集。</span><span class="sxs-lookup"><span data-stu-id="491cc-103">The topics in this section provide information to help you understand, design, and implement assemblies.</span></span>  
  
 <span data-ttu-id="491cc-104">程序集是的实例中使用的 DLL 文件，用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 部署函数、存储过程、触发器、用户定义聚合和用户定义的类型，这些类型由 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 公共语言运行时 (CLR) 而不是中的托管代码语言之一来编写 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="491cc-104">Assemblies are DLL files used in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR), instead of in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="491cc-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的程序集对象引用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 公共语言运行时中创建的托管应用程序模块（.dll 文件）。</span><span class="sxs-lookup"><span data-stu-id="491cc-105">An assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is an object that references a managed application module (.dll file) that was created in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime.</span></span> <span data-ttu-id="491cc-106">程序集包含类元数据和托管代码。</span><span class="sxs-lookup"><span data-stu-id="491cc-106">An assembly contains class metadata and managed code.</span></span> <span data-ttu-id="491cc-107">将程序集上载到 SQL Server 实例是创建以下任何一个数据库对象的第一步：</span><span class="sxs-lookup"><span data-stu-id="491cc-107">Uploading an assembly to an instance of SQL Server is the first step toward creating any of the following database objects:</span></span>  
  
-   <span data-ttu-id="491cc-108">CLR 函数。</span><span class="sxs-lookup"><span data-stu-id="491cc-108">CLR functions.</span></span> <span data-ttu-id="491cc-109">有关详细信息，请参阅[创建 CLR 函数](../user-defined-functions/create-clr-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="491cc-109">For more information, see [Create CLR Functions](../user-defined-functions/create-clr-functions.md).</span></span>  
  
-   <span data-ttu-id="491cc-110">CLR 存储过程。</span><span class="sxs-lookup"><span data-stu-id="491cc-110">CLR stored procedures.</span></span> <span data-ttu-id="491cc-111">有关详细信息，请参阅[CLR 存储过程](../../database-engine/dev-guide/clr-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="491cc-111">For more information, see [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md).</span></span>  
  
-   <span data-ttu-id="491cc-112">CLR 触发器。</span><span class="sxs-lookup"><span data-stu-id="491cc-112">CLR triggers.</span></span> <span data-ttu-id="491cc-113">有关详细信息，请参阅[创建 CLR 触发器](../triggers/create-clr-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="491cc-113">For more information, see [Create CLR Triggers](../triggers/create-clr-triggers.md).</span></span>  
  
-   <span data-ttu-id="491cc-114">用户定义聚合函数。</span><span class="sxs-lookup"><span data-stu-id="491cc-114">User-defined aggregate functions.</span></span> <span data-ttu-id="491cc-115">有关详细信息，请参阅[创建用户定义聚合](../user-defined-functions/create-user-defined-aggregates.md)。</span><span class="sxs-lookup"><span data-stu-id="491cc-115">For more information, see [Create User-defined Aggregates](../user-defined-functions/create-user-defined-aggregates.md).</span></span>  
  
-   <span data-ttu-id="491cc-116">用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="491cc-116">User-defined types.</span></span> <span data-ttu-id="491cc-117">有关详细信息，请参阅[使用用户定义类型](../native-client/features/using-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="491cc-117">For more information, see [Using User-Defined Types](../native-client/features/using-user-defined-types.md).</span></span>  
  
 <span data-ttu-id="491cc-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中程序集可以执行下列功能：</span><span class="sxs-lookup"><span data-stu-id="491cc-118">Assemblies perform the following functions in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="491cc-119">包含可以实现已列出的一个或多个 CLR 数据库对象的功能的托管代码。</span><span class="sxs-lookup"><span data-stu-id="491cc-119">Contain the managed code that runs the functionality of one or more of the CLR database objects previously listed.</span></span>  
  
-   <span data-ttu-id="491cc-120">包含程序集以下方面的元数据：版本号和区域性、唯一标识类列表的可选公钥、定义的方法以及处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="491cc-120">Contain metadata that includes the version number and culture of the assembly, an optional public key that uniquely identifies the list of classes of the assembly, the methods that are defined in the assembly, and the processor architecture of the assembly.</span></span>  
  
-   <span data-ttu-id="491cc-121">通过控制代码访问权限，管理托管代码可以访问外部资源的等级。</span><span class="sxs-lookup"><span data-stu-id="491cc-121">Manage the degree to which managed code can access outside resources by regulating code access permissions.</span></span>  
  
-   <span data-ttu-id="491cc-122">包含有关程序集与所引用的其他程序集之间的依赖关系的元数据。</span><span class="sxs-lookup"><span data-stu-id="491cc-122">Contain metadata about dependencies on other assemblies that are referenced by the assembly.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="491cc-123">本节内容</span><span class="sxs-lookup"><span data-stu-id="491cc-123">In This Section</span></span>  
  
|<span data-ttu-id="491cc-124">主题</span><span class="sxs-lookup"><span data-stu-id="491cc-124">Topic</span></span>|<span data-ttu-id="491cc-125">说明</span><span class="sxs-lookup"><span data-stu-id="491cc-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="491cc-126">设计程序集</span><span class="sxs-lookup"><span data-stu-id="491cc-126">Designing Assemblies</span></span>](assemblies-designing.md)|<span data-ttu-id="491cc-127">说明创建程序集之前必须考虑的问题，</span><span class="sxs-lookup"><span data-stu-id="491cc-127">Explains what you have to consider before creating an assembly.</span></span> <span data-ttu-id="491cc-128">包括打包程序集、代码访问权限和其他限制。</span><span class="sxs-lookup"><span data-stu-id="491cc-128">This includes packaging assemblies, code access permissions, and other restrictions.</span></span>|  
|[<span data-ttu-id="491cc-129">实现程序集</span><span class="sxs-lookup"><span data-stu-id="491cc-129">Implementing Assemblies</span></span>](assemblies-implementing.md)|<span data-ttu-id="491cc-130">说明如何创建和删除程序集、如何以及何时修改程序集、如何检索程序集的有关元数据。</span><span class="sxs-lookup"><span data-stu-id="491cc-130">Explains how to create and drop assemblies, how and when to modify assemblies, and how to retrieve metadata about assemblies.</span></span>|  
|[<span data-ttu-id="491cc-131">获取有关程序集的信息</span><span class="sxs-lookup"><span data-stu-id="491cc-131">Getting Information About Assemblies</span></span>](assemblies-getting-information.md)|<span data-ttu-id="491cc-132">列出了可以查询程序集的有关元数据的目录视图和函数。</span><span class="sxs-lookup"><span data-stu-id="491cc-132">Lists the catalog views and functions that can be queried for metadata about assemblies.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="491cc-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="491cc-133">See Also</span></span>  
 [<span data-ttu-id="491cc-134">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="491cc-134">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
