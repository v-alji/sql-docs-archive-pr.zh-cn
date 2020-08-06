---
title: CLR 例程的自定义属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: 058bbec7f0f1f63fbd96258a0abe7a6c3d543d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576829"
---
# <a name="custom-attributes-for-clr-routines"></a><span data-ttu-id="ff0bd-102">CLR 例程的自定义属性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-102">Custom Attributes for CLR Routines</span></span>
  <span data-ttu-id="ff0bd-103">列出的属性可应用于公共语言运行时 (CLR) 例程、用户定义类型和在中注册的用户定义聚合 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-103">The attributes listed can be applied to common language runtime (CLR) routines, user-defined types, and user-defined aggregates that are registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ff0bd-104">如果未应用此属性，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将采用默认值。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-104">If the attribute is not applied, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assumes the default value.</span></span> <span data-ttu-id="ff0bd-105">列出的属性在 `Microsoft.SqlServer.Server` 命名空间中定义。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-105">The attributes listed are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a><span data-ttu-id="ff0bd-106">SqlUserDefinedAggregate 特性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-106">The SqlUserDefinedAggregate Attribute</span></span>  
 <span data-ttu-id="ff0bd-107">`SqlUserDefinedAggregate` 属性指示方法应注册为用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-107">The `SqlUserDefinedAggregate` attribute indicates that the method should be registered as a user-defined aggregate.</span></span> <span data-ttu-id="ff0bd-108">必须使用此属性注释每个用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-108">Every user-defined aggregate must be annotated with this attribute.</span></span>  
  
 <span data-ttu-id="ff0bd-109">有关详细信息，请参阅[SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-109">For more information, see [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).</span></span>  
  
## <a name="the-sqlfunction-attribute"></a><span data-ttu-id="ff0bd-110">SqlFunction 属性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-110">The SqlFunction Attribute</span></span>  
 <span data-ttu-id="ff0bd-111">`SqlFunction` 属性指示方法应注册为包含相应函数属性集的函数。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-111">The `SqlFunction` attribute indicates the method should be registered as a function, with the appropriate function attributes set.</span></span>  
  
 <span data-ttu-id="ff0bd-112">有关详细信息，请参阅[SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-112">For more information, see [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).</span></span>  
  
## <a name="the-sqlfacet-attribute"></a><span data-ttu-id="ff0bd-113">SqlFacet 特性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-113">The SqlFacet Attribute</span></span>  
 <span data-ttu-id="ff0bd-114">`SqlFacet` 属性用于返回有关用户定义类型 (UDT) 表达式的返回类型的信息。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-114">The `SqlFacet` attribute is used to return information about the return type of a user-defined type (UDT) expression.</span></span>  
  
 <span data-ttu-id="ff0bd-115">有关详细信息，请参阅[SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-115">For more information, see [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).</span></span>  
  
## <a name="the-sqlprocedure-attribute"></a><span data-ttu-id="ff0bd-116">SqlProcedure 属性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-116">The SqlProcedure Attribute</span></span>  
 <span data-ttu-id="ff0bd-117">`SqlProcedure` 属性指示方法应注册为存储过程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-117">The `SqlProcedure` attribute indicates the method should be registered as a stored procedure.</span></span> <span data-ttu-id="ff0bd-118">此属性仅由 Visual Studio 用于将指定的方法自动注册为存储过程；[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不使用此属性。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-118">This attribute is used only by Visual Studio to register the specified method as a stored procedure automatically; it is not used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ff0bd-119">有关详细信息，请参阅[SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-119">For more information, see [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).</span></span>  
  
## <a name="the-sqltrigger-attribute"></a><span data-ttu-id="ff0bd-120">SqlTrigger 特性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-120">The SqlTrigger Attribute</span></span>  
 <span data-ttu-id="ff0bd-121">`SqlTrigger` 属性指示方法应注册为触发器。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-121">The `SqlTrigger` attribute indicates the method should be registered as a trigger.</span></span>  
  
 <span data-ttu-id="ff0bd-122">有关详细信息，请参阅[SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022)和[SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-122">For more information, see [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) and [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).</span></span>  
  
## <a name="the-sqluserdefinedtypeattribute"></a><span data-ttu-id="ff0bd-123">SqlUserDefinedTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ff0bd-123">The SqlUserDefinedTypeAttribute</span></span>  
 <span data-ttu-id="ff0bd-124">可将 SqlUserDefinedTypeAttribute 应用于程序集中的类定义。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-124">You can apply the SqlUserDefinedTypeAttribute to a class definition in the assembly.</span></span> <span data-ttu-id="ff0bd-125">此属性会使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 创建绑定到具有此自定义属性的类定义的用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-125">It causes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create a user-defined type that is bound to the class definition which has this custom attribute.</span></span>  
  
 <span data-ttu-id="ff0bd-126">有关详细信息，请参阅[SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-126">For more information, see [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).</span></span>  
  
## <a name="the-sqlmethod-attribute"></a><span data-ttu-id="ff0bd-127">SqlMethod 属性</span><span class="sxs-lookup"><span data-stu-id="ff0bd-127">The SqlMethod Attribute</span></span>  
 <span data-ttu-id="ff0bd-128">`SqlMethod` 特性用于指示 UDT 的某方法或属性的确定性和数据访问属性。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-128">The `SqlMethod` attribute is used to indicate the determinism and data access properties of a method or a property on a UDT.</span></span>  
  
 <span data-ttu-id="ff0bd-129">有关详细信息，请参阅[SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-129">For more information, see [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0bd-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff0bd-130">See Also</span></span>  
 <span data-ttu-id="ff0bd-131">[CLR 用户定义聚合](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span><span class="sxs-lookup"><span data-stu-id="ff0bd-131">[CLR User-Defined Aggregates](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span></span>  
 <span data-ttu-id="ff0bd-132">[CLR 用户定义函数](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="ff0bd-132">[CLR User-Defined Functions](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="ff0bd-133">[CLR 用户定义类型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="ff0bd-133">[CLR User-Defined Types](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 <span data-ttu-id="ff0bd-134">[CLR 存储过程](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ff0bd-134">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="ff0bd-135">CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="ff0bd-135">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
