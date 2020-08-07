---
title: 通过公共语言运行时 (CLR) 集成生成数据库对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c849c095a3be1c590e6fcb3ce87a0725eb795c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587859"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a><span data-ttu-id="f7d3b-102">使用公共语言运行时 (CLR) 集成生成数据库对象</span><span class="sxs-lookup"><span data-stu-id="f7d3b-102">Building Database Objects with Common Language Runtime (CLR) Integration</span></span>
  <span data-ttu-id="f7d3b-103">您可以使用生成数据库对象 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，称为 "CLR 例程"。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-103">You can build database objects using the [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is referred to as a "CLR routine."</span></span> <span data-ttu-id="f7d3b-104">这些例程包括：</span><span class="sxs-lookup"><span data-stu-id="f7d3b-104">These routines include:</span></span>  
  
-   <span data-ttu-id="f7d3b-105">标量值用户定义函数（标量 UDF）</span><span class="sxs-lookup"><span data-stu-id="f7d3b-105">Scalar-valued user-defined functions (scalar UDFs)</span></span>  
  
-   <span data-ttu-id="f7d3b-106">表值用户定义函数 (TVF)</span><span class="sxs-lookup"><span data-stu-id="f7d3b-106">Table-valued user-defined functions (TVFs)</span></span>  
  
-   <span data-ttu-id="f7d3b-107">用户定义的过程 (UDP)</span><span class="sxs-lookup"><span data-stu-id="f7d3b-107">User-defined procedures (UDPs)</span></span>  
  
-   <span data-ttu-id="f7d3b-108">用户定义的触发器</span><span class="sxs-lookup"><span data-stu-id="f7d3b-108">User-defined triggers</span></span>  
  
 <span data-ttu-id="f7d3b-109">CLR 例程在托管代码中具有相同的结构。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-109">CLR routines have the same structure in managed code.</span></span> <span data-ttu-id="f7d3b-110">它们映射为某个类的公共静态（在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 中共享）方法。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-110">They are mapped to public, static (shared in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) methods of a class.</span></span> <span data-ttu-id="f7d3b-111">除了例程之外，还可以使用 .NET Framework 定义用户定义类型 (UDT) 和用户定义的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-111">In addition to routines, user-defined types (UDTs) and user-defined aggregate functions can also be defined using the .NET Framework.</span></span> <span data-ttu-id="f7d3b-112">将 UDT 和用户定义聚合映射为整个 .NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-112">UDTs and user-defined aggregates are mapped to entire .NET Framework classes.</span></span>  
  
 <span data-ttu-id="f7d3b-113">每种类型的 .NET Framework 例程都具有 [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可使用等效的。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-113">Each type of .NET Framework routine has a [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] that the [!INCLUDE[tsql](../../../includes/tsql-md.md)] equivalent can be used.</span></span> <span data-ttu-id="f7d3b-114">例如，标量 UDF 可以用于任意标量表达式中。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-114">For instance, scalar UDFs can be used in any scalar expression.</span></span> <span data-ttu-id="f7d3b-115">TVF 可以用于任意 FROM 子句中。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-115">A TVF can be used in any FROM clause.</span></span> <span data-ttu-id="f7d3b-116">可以在 EXEC 语句中调用过程或从客户端应用程序调用。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-116">A procedure can be invoked in an EXEC statement or invoked from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7d3b-117">如果查询优化器确定这样做有益处，则在公共语言运行时上执行 CLR 对象（用户定义函数、用户定义类型或触发器）可能在多个线程上发生（并行计划）。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-117">Execution of a CLR object (user-defined function, user-defined type, or trigger) on the common language runtime can take place on multiple threads (parallel plan), if the query optimizer decides it is beneficial.</span></span> <span data-ttu-id="f7d3b-118">但是，如果用户定义函数访问数据，则会在串行计划上执行。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-118">However, if a user-defined function accesses data, execution will be  on a serial plan.</span></span> <span data-ttu-id="f7d3b-119">当在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 之前的服务器版本上执行时，如果某一用户定义函数包含 LOB 参数或返回值，则也必须在串行计划上执行。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-119">When executed on a server version prior to [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], if a user-defined function contains LOB parameters or return values, execution also must be on a serial plan.</span></span>  
  
 <span data-ttu-id="f7d3b-120">下表列出了本节涵盖的主题。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-120">The following table lists the topics covered in this section.</span></span>  
  
 [<span data-ttu-id="f7d3b-121">CLR 集成入门</span><span class="sxs-lookup"><span data-stu-id="f7d3b-121">Getting Started with CLR Integration</span></span>](getting-started-with-clr-integration.md)  
 <span data-ttu-id="f7d3b-122">简要概括使用 CLR 与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 集成编译对象所需的库和命名空间。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-122">Provides a brief overview of the libraries and namespaces required to compile object using CLR integration with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f7d3b-123">提供一个“Hello World”CLR 存储过程示例。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-123">Includes an example "Hello World" CLR stored procedure.</span></span>  
  
 [<span data-ttu-id="f7d3b-124">支持的 .NET Framework 库</span><span class="sxs-lookup"><span data-stu-id="f7d3b-124">Supported .NET Framework Libraries</span></span>](supported-net-framework-libraries.md)  
 <span data-ttu-id="f7d3b-125">提供有关 CLR 集成支持的 .NET Framework 库的信息。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-125">Provides information on the .NET Framework libraries supported by CLR integration.</span></span>  
  
 [<span data-ttu-id="f7d3b-126">CLR 集成编程模型限制</span><span class="sxs-lookup"><span data-stu-id="f7d3b-126">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
 <span data-ttu-id="f7d3b-127">提供有关 CLR 集成编程模型限制的信息。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-127">Provides information about CLR integration programming model restrictions.</span></span>  
  
 [<span data-ttu-id="f7d3b-128">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="f7d3b-128">SQL Server Data Types in the .NET Framework</span></span>](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 <span data-ttu-id="f7d3b-129">提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型及其 .NET Framework 等效项的概览。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-129">An overview of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types and their .NET Framework equivalents.</span></span>  
  
 [<span data-ttu-id="f7d3b-130">CLR 集成自定义属性的概览</span><span class="sxs-lookup"><span data-stu-id="f7d3b-130">Overview of CLR Integration Custom Attributes</span></span>](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 <span data-ttu-id="f7d3b-131">提供有关 CLR 集成自定义属性的信息。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-131">Provides information about CLR integration custom attributes.</span></span>  
  
 [<span data-ttu-id="f7d3b-132">CLR 用户定义函数</span><span class="sxs-lookup"><span data-stu-id="f7d3b-132">CLR User-Defined Functions</span></span>](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 <span data-ttu-id="f7d3b-133">说明如何实现和使用各种类型的 CLR 函数：表值、标量和用户定义的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-133">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="f7d3b-134">CLR 用户定义类型</span><span class="sxs-lookup"><span data-stu-id="f7d3b-134">CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="f7d3b-135">说明如何实现和使用 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-135">Describes how to implement and use CLR user-defined types.</span></span>  
  
 [<span data-ttu-id="f7d3b-136">CLR 存储过程</span><span class="sxs-lookup"><span data-stu-id="f7d3b-136">CLR Stored Procedures</span></span>](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 <span data-ttu-id="f7d3b-137">说明如何实现和使用 CLR 存储过程。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-137">Describes how to implement and use CLR stored procedures.</span></span>  
  
 [<span data-ttu-id="f7d3b-138">CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="f7d3b-138">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
 <span data-ttu-id="f7d3b-139">说明如何实现和使用 CLR 触发器。</span><span class="sxs-lookup"><span data-stu-id="f7d3b-139">Describes how to implement and use CLR triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d3b-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7d3b-140">See Also</span></span>  
 [<span data-ttu-id="f7d3b-141">公共语言运行时 &#40;CLR&#41; 集成概述</span><span class="sxs-lookup"><span data-stu-id="f7d3b-141">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](../common-language-runtime-integration-overview.md)  
  
  
