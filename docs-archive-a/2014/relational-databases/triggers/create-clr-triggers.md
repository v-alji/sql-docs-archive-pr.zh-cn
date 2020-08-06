---
title: 创建 CLR 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 3afd841b4f1f9ca567a93c0a20c0a7609a5b45e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590648"
---
# <a name="create-clr-triggers"></a><span data-ttu-id="aea87-102">创建 CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="aea87-102">Create CLR Triggers</span></span>
  <span data-ttu-id="aea87-103">可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建可在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 公共语言运行时 (CLR) 中创建的程序集中进行编程的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="aea87-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR).</span></span> <span data-ttu-id="aea87-104">可以利用由 CLR 提供的大量编程模型的数据库对象包括 DML 触发器、DDL 触发器、存储过程、函数、聚合函数和类型。</span><span class="sxs-lookup"><span data-stu-id="aea87-104">Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="aea87-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建 CLR 触发器（DML 或 DDL）包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="aea87-105">Creating a CLR trigger (DML or DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="aea87-106">使用 .NET Framework 支持的语言将触发器定义为类。</span><span class="sxs-lookup"><span data-stu-id="aea87-106">Define the trigger as a class in a .NET Framework-supported language.</span></span> <span data-ttu-id="aea87-107">有关如何在 CLR 中对触发器进行编程的详细信息，请参阅 [CLR 触发器](../../database-engine/dev-guide/clr-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="aea87-107">For more information about how to program triggers in the CLR, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span> <span data-ttu-id="aea87-108">然后，使用相应的语言编译器编译该类，在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中生成程序集。</span><span class="sxs-lookup"><span data-stu-id="aea87-108">Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="aea87-109">使用 CREATE ASSEMBLY 语句在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="aea87-109">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="aea87-110">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的程序集的详细信息，请参阅[程序集（数据库引擎）](../clr-integration/assemblies-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="aea87-110">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="aea87-111">创建用于引用已注册的程序集的触发器。</span><span class="sxs-lookup"><span data-stu-id="aea87-111">Create the trigger that references the registered assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aea87-112">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中部署 SQL Server 项目将在为该项目指定的数据库中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="aea87-112">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="aea87-113">部署项目也还会在数据库中为所有使用 `SqlTrigger` 属性批注的方法创建 CLR 触发器。</span><span class="sxs-lookup"><span data-stu-id="aea87-113">Deploying the project also creates CLR triggers in the database for all methods annotated with the `SqlTrigger` attribute.</span></span> <span data-ttu-id="aea87-114">有关详细信息，请参阅 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="aea87-114">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aea87-115">默认情况下，关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行 CLR 代码的功能。</span><span class="sxs-lookup"><span data-stu-id="aea87-115">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="aea87-116">可以创建、更改和删除引用托管代码模块的数据库对象，但是只有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure (Transact-SQL) [启用了](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled 选项 [，才能在](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)中执行这些引用。</span><span class="sxs-lookup"><span data-stu-id="aea87-116">You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="aea87-117">**创建、修改或删除程序集**</span><span class="sxs-lookup"><span data-stu-id="aea87-117">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="aea87-118">CREATE ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aea87-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="aea87-119">ALTER ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aea87-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="aea87-120">DROP ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aea87-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="aea87-121">**创建 CLR 触发器**</span><span class="sxs-lookup"><span data-stu-id="aea87-121">**To create a CLR trigger**</span></span>  
  
-   [<span data-ttu-id="aea87-122">CREATE TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="aea87-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="aea87-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aea87-123">See Also</span></span>  
 <span data-ttu-id="aea87-124">[DML 触发器](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="aea87-124">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="aea87-125">[公共语言运行时 (CLR) 集成编程概念](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="aea87-125">[Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span></span>  
 [<span data-ttu-id="aea87-126">从 CLR 数据库对象进行数据访问</span><span class="sxs-lookup"><span data-stu-id="aea87-126">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
