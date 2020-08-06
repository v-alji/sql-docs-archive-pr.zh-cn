---
title: 创建用户定义聚合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: c91179cb194bbfb79e8e7a8476e9725877b88afa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693229"
---
# <a name="create-user-defined-aggregates"></a><span data-ttu-id="a30c9-102">创建用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="a30c9-102">Create User-defined Aggregates</span></span>
  <span data-ttu-id="a30c9-103">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建在 CLR 程序集中进行编程的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="a30c9-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in a CLR assembly.</span></span> <span data-ttu-id="a30c9-104">能够利用由 CLR 提供的众多编程模型的数据库对象包括触发器、存储过程、函数、聚合函数和类型。</span><span class="sxs-lookup"><span data-stu-id="a30c9-104">Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="a30c9-105">与 [!INCLUDE[tsql](../../includes/tsql-md.md)]中提供的内置聚合函数一样，用户定义聚合函数对一组值进行计算，然后返回单个值。</span><span class="sxs-lookup"><span data-stu-id="a30c9-105">Like the built-in aggregate functions provided in [!INCLUDE[tsql](../../includes/tsql-md.md)], user-defined aggregate functions perform a calculation on a set of values and return a single value.</span></span>  
  
 <span data-ttu-id="a30c9-106">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建用户定义聚合函数包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="a30c9-106">Creating a user-defined aggregate function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="a30c9-107">用一种 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 语言将用户定义聚合函数定义为类。</span><span class="sxs-lookup"><span data-stu-id="a30c9-107">Define the user-defined aggregate function as a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-supported language.</span></span> <span data-ttu-id="a30c9-108">有关如何在 CLR 中编写用户定义聚合函数的详细信息，请参阅 [CLR 用户定义聚合函数](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)。</span><span class="sxs-lookup"><span data-stu-id="a30c9-108">For more information about how to program user-defined aggregates in the CLR, see [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).</span></span> <span data-ttu-id="a30c9-109">使用适当的语言编译器编译此类，以生成 CLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="a30c9-109">Compile this class to build a CLR assembly using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="a30c9-110">使用 CREATE ASSEMBLY 语句在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="a30c9-110">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="a30c9-111">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的程序集的详细信息，请参阅[程序集（数据库引擎）](../clr-integration/assemblies-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="a30c9-111">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="a30c9-112">使用 CREATE AGGREGATE 语句创建引用已注册程序集的用户定义聚合函数。</span><span class="sxs-lookup"><span data-stu-id="a30c9-112">Create the user-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a30c9-113">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中部署 SQL Server 项目将在为该项目指定的数据库中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="a30c9-113">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="a30c9-114">部署项目还会在数据库中为使用 `SqlUserDefinedAggregate` 属性注释的所有类定义创建用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="a30c9-114">Deploying the project also creates a user-defined aggregate in the database for all class definitions annotated with the `SqlUserDefinedAggregate` attribute.</span></span> <span data-ttu-id="a30c9-115">有关详细信息，请参阅 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="a30c9-115">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a30c9-116">默认情况下，关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行 CLR 代码的功能。</span><span class="sxs-lookup"><span data-stu-id="a30c9-116">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="a30c9-117">可以创建、更改和删除将引用托管代码模块的数据库对象，但是不能在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中执行这些引用，除非使用 [sp_configure (Transact-SQL)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) 启用了 [clr enabled](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)选项。</span><span class="sxs-lookup"><span data-stu-id="a30c9-117">You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="a30c9-118">**创建、修改或删除程序集**</span><span class="sxs-lookup"><span data-stu-id="a30c9-118">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="a30c9-119">CREATE ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a30c9-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="a30c9-120">ALTER ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a30c9-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="a30c9-121">DROP ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a30c9-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="a30c9-122">**创建用户定义聚合函数**</span><span class="sxs-lookup"><span data-stu-id="a30c9-122">**To create a user-defined aggregate**</span></span>  
  
-   [<span data-ttu-id="a30c9-123">CREATE AGGREGATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a30c9-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a30c9-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a30c9-124">See Also</span></span>  
 [<span data-ttu-id="a30c9-125">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="a30c9-125">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
