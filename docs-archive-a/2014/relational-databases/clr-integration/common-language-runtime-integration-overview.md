---
title: 公共语言运行时 (CLR) 集成概述 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 25345fd39fb8a77f62e4e352b75629a98cb9d7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581313"
---
# <a name="common-language-runtime-clr-integration-overview"></a><span data-ttu-id="1797c-102">公共语言运行时 (CLR) 集成概述</span><span class="sxs-lookup"><span data-stu-id="1797c-102">Common Language Runtime (CLR) Integration Overview</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="1797c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]现在提供了公共语言运行时与 .NET Framework 的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (CLR) 组件的集成的功能Windows.</span><span class="sxs-lookup"><span data-stu-id="1797c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] now features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="1797c-104">CLR 为托管代码提供服务，例如跨语言集成、代码访问安全性、对象生存期管理以及调试和分析支持。</span><span class="sxs-lookup"><span data-stu-id="1797c-104">The CLR supplies managed code with services such as cross-language integration, code access security, object lifetime management, and debugging and profiling support.</span></span> <span data-ttu-id="1797c-105">对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用户和应用程序开发人员来说，CLR 集成意味着您现在可以使用任何 .NET Framework 语言（包括 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#）编写存储过程、触发器、用户定义类型、用户定义函数（标量函数和表值函数）以及用户定义的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="1797c-105">For [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users and application developers, CLR integration means that you can now write stored procedures, triggers, user-defined types, user-defined functions (scalar and table-valued), and user-defined aggregate functions using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1797c-106">包括预安装的 .NET Framework 版本 4。</span><span class="sxs-lookup"><span data-stu-id="1797c-106">includes the .NET Framework version 4 pre-installed.</span></span>  
  
 <span data-ttu-id="1797c-107">下面列出了这一集成的其中一些主要优点：</span><span class="sxs-lookup"><span data-stu-id="1797c-107">Among the major benefits of this integration are:</span></span>  
  
-   <span data-ttu-id="1797c-108">**更好的编程模型。**</span><span class="sxs-lookup"><span data-stu-id="1797c-108">**A better programming model.**</span></span> <span data-ttu-id="1797c-109">.NET Framework 语言在许多方面都比 Transact-SQL 丰富，它为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 开发人员提供了以前没有的构造和功能。</span><span class="sxs-lookup"><span data-stu-id="1797c-109">The .NET Framework languages are in many respects richer than Transact-SQL, offering constructs and capabilities previously not available to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developers.</span></span> <span data-ttu-id="1797c-110">开发人员还可以利用 .NET Framework 库的功能，它提供了大量可用于快速有效地解决编程问题的类。</span><span class="sxs-lookup"><span data-stu-id="1797c-110">Developers may also leverage the power of the .NET Framework Library, which provides an extensive set of classes that can be used to quickly and efficiently solve programming problems.</span></span>  
  
-   <span data-ttu-id="1797c-111">**改进了安全和安全性。**</span><span class="sxs-lookup"><span data-stu-id="1797c-111">**Improved safety and security.**</span></span> <span data-ttu-id="1797c-112">托管代码在数据库引擎承载的公共语言运行时环境中运行。</span><span class="sxs-lookup"><span data-stu-id="1797c-112">Managed code runs in a common language run-time environment, hosted by the Database Engine.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1797c-113">利用这一特点为在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 早期版本中提供的扩展存储过程提供更安全更可靠的替代方法。</span><span class="sxs-lookup"><span data-stu-id="1797c-113">leverages this to provide a safer and more secure alternative to the extended stored procedures available in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1797c-114">**能够定义数据类型和聚合函数。**</span><span class="sxs-lookup"><span data-stu-id="1797c-114">**Ability to define data types and aggregate functions.**</span></span> <span data-ttu-id="1797c-115">用户定义类型和用户定义聚合是两个新的托管数据库对象，这两个对象扩展了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的存储和查询功能。</span><span class="sxs-lookup"><span data-stu-id="1797c-115">User defined types and user defined aggregates are two new managed database objects which expand the storage and querying capabilities of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1797c-116">**通过标准化环境简化了开发。**</span><span class="sxs-lookup"><span data-stu-id="1797c-116">**Streamlined development through a standardized environment.**</span></span> <span data-ttu-id="1797c-117">数据库开发集成到将来版本的  Visual Studio .NET 开发环境中。</span><span class="sxs-lookup"><span data-stu-id="1797c-117">Database development is integrated into future releases of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET development environment.</span></span> <span data-ttu-id="1797c-118">开发人员在开发和调试数据库对象和脚本时所使用的工具与他们编写中间层或客户端层的 .NET Framework 组件和服务时所使用的工具相同。</span><span class="sxs-lookup"><span data-stu-id="1797c-118">Developers use the same tools for developing and debugging database objects and scripts as they use to write middle-tier or client-tier .NET Framework components and services.</span></span>  
  
-   <span data-ttu-id="1797c-119">**具备改善性能和可伸缩性的潜力。**</span><span class="sxs-lookup"><span data-stu-id="1797c-119">**Potential for improved performance and scalability.**</span></span> <span data-ttu-id="1797c-120">在多数情况下，.NET Framework 语言编译和执行模型通过 Transact-SQL 提高性能。</span><span class="sxs-lookup"><span data-stu-id="1797c-120">In many situations, the .NET Framework language compilation and execution models deliver improved performance over Transact-SQL.</span></span>  
  
 <span data-ttu-id="1797c-121">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="1797c-121">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="1797c-122">CLR 集成的概述</span><span class="sxs-lookup"><span data-stu-id="1797c-122">Overview of CLR Integration</span></span>](clr-integration-overview.md)  
 <span data-ttu-id="1797c-123">说明可使用 CLR 集成生成的对象类型，并介绍使用 CLR 集成生成数据库对象的要求。</span><span class="sxs-lookup"><span data-stu-id="1797c-123">Describes the kinds of objects that can be built using CLR integration, and reviews the requirements for building database objects using CLR integration.</span></span>  
  
 [<span data-ttu-id="1797c-124">CLR 集成中的新增功能</span><span class="sxs-lookup"><span data-stu-id="1797c-124">What's New in CLR Integration</span></span>](clr-integration-what-s-new.md)  
 <span data-ttu-id="1797c-125">介绍此发行版的新功能。</span><span class="sxs-lookup"><span data-stu-id="1797c-125">Describes the new features in this release.</span></span>  
  
 [<span data-ttu-id="1797c-126">CLR 集成体系结构</span><span class="sxs-lookup"><span data-stu-id="1797c-126">Architecture of CLR Integration</span></span>](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 <span data-ttu-id="1797c-127">介绍 CLR 集成的设计目标。</span><span class="sxs-lookup"><span data-stu-id="1797c-127">Describes the design goals of CLR integration.</span></span>  
  
 [<span data-ttu-id="1797c-128">启用 CLR 集成</span><span class="sxs-lookup"><span data-stu-id="1797c-128">Enabling CLR Integration</span></span>](clr-integration-enabling.md)  
 <span data-ttu-id="1797c-129">介绍如何启用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="1797c-129">Describes how to enable CLR integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1797c-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1797c-130">See Also</span></span>  
 <span data-ttu-id="1797c-131">[安装 .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span><span class="sxs-lookup"><span data-stu-id="1797c-131">[Installing the .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span></span>  
 [<span data-ttu-id="1797c-132">CLR 集成的性能</span><span class="sxs-lookup"><span data-stu-id="1797c-132">Performance of CLR Integration</span></span>](clr-integration-architecture-performance.md)  
  
  
