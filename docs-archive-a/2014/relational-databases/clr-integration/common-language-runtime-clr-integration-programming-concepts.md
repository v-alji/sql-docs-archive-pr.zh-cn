---
title: 公共语言运行时 (CLR) 集成编程概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
author: rothja
ms.author: jroth
ms.openlocfilehash: 38323b0145132ad60d59c001d5147a7d19942462
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580780"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a><span data-ttu-id="21cfb-102">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="21cfb-102">Common Language Runtime (CLR) Integration Programming Concepts</span></span>
  <span data-ttu-id="21cfb-103">从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 开始，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 集成了用于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 的 .NET Framework 的公共语言运行时 (CLR) 组件。</span><span class="sxs-lookup"><span data-stu-id="21cfb-103">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="21cfb-104">这意味着现在可以使用任何 .NET Framework 语言（包括 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#）来编写存储过程、触发器、用户定义类型、用户定义函数、用户定义聚合和流式表值函数。</span><span class="sxs-lookup"><span data-stu-id="21cfb-104">This means that you can now write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="21cfb-105">Microsoft.SqlServer.Server 命名空间包括在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中进行 CLR 编程的核心功能。</span><span class="sxs-lookup"><span data-stu-id="21cfb-105">The Microsoft.SqlServer.Server namespace includes core functionality for CLR programming in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21cfb-106">但是，有关 Microsoft.SqlServer.Server 命名空间的文档位于 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="21cfb-106">However, the Microsoft.SqlServer.Server namespace is documented in the .NET Framework SDK.</span></span> <span data-ttu-id="21cfb-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书不包括该文档。</span><span class="sxs-lookup"><span data-stu-id="21cfb-107">This documentation is not included in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="21cfb-108">默认情况下，.NET Framework 随 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一起安装，但不安装 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="21cfb-108">By default, the .NET Framework is installed with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but the .NET Framework SDK is not.</span></span> <span data-ttu-id="21cfb-109">如果未在计算机上安装 SDK，并且未将其包括在联机丛书集中，则本节中指向 SDK 内容的链接无效。</span><span class="sxs-lookup"><span data-stu-id="21cfb-109">Without the SDK installed on your computer and included in the Books Online collection, links to SDK content in this section do not work.</span></span> <span data-ttu-id="21cfb-110">请安装 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="21cfb-110">Install the .NET Framework SDK.</span></span> <span data-ttu-id="21cfb-111">安装后，按照[安装 .NET FRAMEWORK sdk](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)中的说明，将 SDK 添加到联机丛书集合和目录。</span><span class="sxs-lookup"><span data-stu-id="21cfb-111">Once installed, add the SDK to the Books Online collection and table of contents by following the instructions in [Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).</span></span>  
  
 <span data-ttu-id="21cfb-112">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="21cfb-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="21cfb-113">公共语言运行时 &#40;CLR&#41; 集成概述</span><span class="sxs-lookup"><span data-stu-id="21cfb-113">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](common-language-runtime-integration-overview.md)  
 <span data-ttu-id="21cfb-114">提供 CLR 的简短概述，并说明如何以及为什么在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用该技术。</span><span class="sxs-lookup"><span data-stu-id="21cfb-114">Provides a brief overview of the CLR, and describes how and why this technology has been used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21cfb-115">描述使用 CLR 创建数据库对象的好处。</span><span class="sxs-lookup"><span data-stu-id="21cfb-115">Describes the benefits of using the CLR to create database objects.</span></span>  
  
 [<span data-ttu-id="21cfb-116">程序集（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="21cfb-116">Assemblies &#40;Database Engine&#41;</span></span>](assemblies-database-engine.md)  
 <span data-ttu-id="21cfb-117">介绍如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中使用程序集来部署用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 公共语言运行时 (CLR) 中驻留的一种托管代码语言（而非 [!INCLUDE[tsql](../../../includes/tsql-md.md)]）编写的函数、存储过程、触发器、用户定义聚合和用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="21cfb-117">Describes how assemblies are used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework common language runtime (CLR), and not written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 [<span data-ttu-id="21cfb-118">通过公共语言运行时 &#40;CLR&#41; 集成生成数据库对象</span><span class="sxs-lookup"><span data-stu-id="21cfb-118">Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration</span></span>](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="21cfb-119">描述可以使用 CLR 生成的对象种类，并说明生成 CLR 数据库对象时所要满足的要求。</span><span class="sxs-lookup"><span data-stu-id="21cfb-119">Describes the kinds of objects that can be built using the CLR, and reviews the requirements for building CLR database objects.</span></span>  
  
 [<span data-ttu-id="21cfb-120">从 CLR 数据库对象进行数据访问</span><span class="sxs-lookup"><span data-stu-id="21cfb-120">Data Access from CLR Database Objects</span></span>](data-access/data-access-from-clr-database-objects.md)  
 <span data-ttu-id="21cfb-121">描述 CLR 例程如何访问存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的数据。</span><span class="sxs-lookup"><span data-stu-id="21cfb-121">Describes how a CLR routine can access data stored in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="21cfb-122">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="21cfb-122">CLR Integration Security</span></span>](security/clr-integration-security.md)  
 <span data-ttu-id="21cfb-123">描述 CLR 集成安全模型。</span><span class="sxs-lookup"><span data-stu-id="21cfb-123">Describes the CLR integration security model.</span></span>  
  
 [<span data-ttu-id="21cfb-124">调试 CLR 数据库对象</span><span class="sxs-lookup"><span data-stu-id="21cfb-124">Debugging CLR Database Objects</span></span>](debugging-clr-database-objects.md)  
 <span data-ttu-id="21cfb-125">描述调试 CLR 数据库对象的限制和要求。</span><span class="sxs-lookup"><span data-stu-id="21cfb-125">Describes limitations of and requirements for debugging CLR database objects.</span></span>  
  
 [<span data-ttu-id="21cfb-126">部署 CLR 数据库对象</span><span class="sxs-lookup"><span data-stu-id="21cfb-126">Deploying CLR Database Objects</span></span>](deploying-clr-database-objects.md)  
 <span data-ttu-id="21cfb-127">描述如何将程序集部署到生产服务器。</span><span class="sxs-lookup"><span data-stu-id="21cfb-127">Describes deploying assemblies to production servers.</span></span>  
  
 [<span data-ttu-id="21cfb-128">管理 CLR 集成程序集</span><span class="sxs-lookup"><span data-stu-id="21cfb-128">Managing CLR Integration Assemblies</span></span>](assemblies/managing-clr-integration-assemblies.md)  
 <span data-ttu-id="21cfb-129">描述如何创建和删除 CLR 集成程序集。</span><span class="sxs-lookup"><span data-stu-id="21cfb-129">Describes how to create and drop CLR integration assemblies.</span></span>  
  
 [<span data-ttu-id="21cfb-130">托管数据库对象监视和故障排除</span><span class="sxs-lookup"><span data-stu-id="21cfb-130">Monitoring and Troubleshooting Managed Database Objects</span></span>](monitoring-and-troubleshooting-managed-database-objects.md)  
 <span data-ttu-id="21cfb-131">介绍用于对在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中运行的托管数据库对象和程序集进行监视和故障排除的工具的相关信息。</span><span class="sxs-lookup"><span data-stu-id="21cfb-131">Provides information about the tools that can be used to monitor and troubleshoot managed database objects and assemblies running in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="21cfb-132">公共语言运行时 (CLR) 集成的使用方案和示例</span><span class="sxs-lookup"><span data-stu-id="21cfb-132">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 <span data-ttu-id="21cfb-133">描述使用 CLR 对象的应用场景和代码示例。</span><span class="sxs-lookup"><span data-stu-id="21cfb-133">Describes usage scenarios and code samples using CLR objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cfb-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21cfb-134">See Also</span></span>  
 <span data-ttu-id="21cfb-135">[程序集 &#40;数据库引擎&#41;](assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="21cfb-135">[Assemblies &#40;Database Engine&#41;](assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="21cfb-136">[安装 .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="21cfb-136">[Installing the .NET Framework SDK](https://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)</span></span>  
  
  
