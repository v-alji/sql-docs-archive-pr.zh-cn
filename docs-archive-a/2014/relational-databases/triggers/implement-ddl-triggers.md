---
title: 实现 DDL 触发器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, implementing
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
author: rothja
ms.author: jroth
ms.openlocfilehash: 110e69aca31df75d4b4d7a732de5c58556bd3e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590620"
---
# <a name="implement-ddl-triggers"></a><span data-ttu-id="1a334-102">实现 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="1a334-102">Implement DDL Triggers</span></span>
  <span data-ttu-id="1a334-103">本主题介绍了有助于创建 DDL 触发器，修改 DDL 触发器以及禁用或删除 DDL 触发器的信息。</span><span class="sxs-lookup"><span data-stu-id="1a334-103">This topic provides information to help you create DDL triggers, modify DDL triggers, and disable or drop DDL triggers.</span></span>  
  
## <a name="creating-ddl-triggers"></a><span data-ttu-id="1a334-104">创建 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="1a334-104">Creating DDL Triggers</span></span>  
 <span data-ttu-id="1a334-105">DDL 触发器是使用 DDL 触发器的 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER 语句创建的。</span><span class="sxs-lookup"><span data-stu-id="1a334-105">DDL triggers are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement for DDL triggers.</span></span>  
  
 <span data-ttu-id="1a334-106">**创建 DDL 触发器**</span><span class="sxs-lookup"><span data-stu-id="1a334-106">**To create a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-107">CREATE TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a334-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的未来版本中将删除从触发器返回结果集的功能。</span><span class="sxs-lookup"><span data-stu-id="1a334-108">The ability to return result sets from triggers will be removed in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1a334-109">返回结果集的触发器可能会导致应用程序出现意外的行为，而这些行为并不符合它们的设计意图。</span><span class="sxs-lookup"><span data-stu-id="1a334-109">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span> <span data-ttu-id="1a334-110">避免在新的开发工作中从触发器返回结果集，并计划修改当前执行此操作的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1a334-110">Avoid returning result sets from triggers in new development work, and plan to modify applications that currently do this.</span></span> <span data-ttu-id="1a334-111">若要防止触发器在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中返回结果集，请将 [disallow results from triggers 选项](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="1a334-111">To prevent triggers from returning result sets in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], set the [disallow results from triggers Option](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) to 1.</span></span> <span data-ttu-id="1a334-112">在后续版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，此选项的默认设置为 1。</span><span class="sxs-lookup"><span data-stu-id="1a334-112">The default setting of this option will be 1 in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="modifying-ddl-triggers"></a><span data-ttu-id="1a334-113">修改 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="1a334-113">Modifying DDL Triggers</span></span>  
 <span data-ttu-id="1a334-114">如果必须修改 DDL 触发器的定义，只需一个操作即可删除并重新创建触发器，或重新定义现有触发器。</span><span class="sxs-lookup"><span data-stu-id="1a334-114">If you have to modify the definition of a DDL trigger, you can either drop and re-create the trigger or redefine the existing trigger in a single step.</span></span>  
  
 <span data-ttu-id="1a334-115">如果更改了由 DDL 触发器引用的对象的名称，则必须修改触发器，以使其文本反映新的名称。</span><span class="sxs-lookup"><span data-stu-id="1a334-115">If you change the name of an object that is referenced by a DDL trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="1a334-116">因此，在重命名对象之前，需要先显示该对象的依赖关系，以确定所建议的更改是否会影响任何触发器。</span><span class="sxs-lookup"><span data-stu-id="1a334-116">Therefore, before renaming an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="1a334-117">也可将修改触发器，对其定义进行加密。</span><span class="sxs-lookup"><span data-stu-id="1a334-117">A trigger can also be modified to encrypt its definition.</span></span>  
  
 <span data-ttu-id="1a334-118">**修改触发器**</span><span class="sxs-lookup"><span data-stu-id="1a334-118">**To modify a trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-119">ALTER TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-trigger-transact-sql)  
  
 <span data-ttu-id="1a334-120">**查看触发器的依赖关系**</span><span class="sxs-lookup"><span data-stu-id="1a334-120">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-121">sys.sql_expression_dependencies (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="1a334-122">sys.dm_sql_referenced_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="1a334-123">sys.dm_sql_referencing_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="disabling-and-dropping-ddl-triggers"></a><span data-ttu-id="1a334-124">禁用和删除 DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="1a334-124">Disabling and Dropping DDL Triggers</span></span>  
 <span data-ttu-id="1a334-125">当不再需要某个 DDL 触发器时，可以禁用或删除该触发器。</span><span class="sxs-lookup"><span data-stu-id="1a334-125">When a DDL trigger is no longer needed, you can disable it or delete it.</span></span>  
  
 <span data-ttu-id="1a334-126">禁用 DDL 触发器不会将其删除。</span><span class="sxs-lookup"><span data-stu-id="1a334-126">Disabling a DDL trigger does not drop it.</span></span> <span data-ttu-id="1a334-127">该触发器仍然作为对象存在于当前数据库中。</span><span class="sxs-lookup"><span data-stu-id="1a334-127">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="1a334-128">但是，当运行编写触发器程序所用的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时，不会激发触发器。</span><span class="sxs-lookup"><span data-stu-id="1a334-128">However, the trigger will not fire when any [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on which it was programmed are run.</span></span> <span data-ttu-id="1a334-129">可以重新启用禁用的 DDL 触发器。</span><span class="sxs-lookup"><span data-stu-id="1a334-129">DDL triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="1a334-130">在启用 DDL 触发器后，该触发器的激发方式与其最初创建时的激发方式相同。</span><span class="sxs-lookup"><span data-stu-id="1a334-130">Enabling a DDL trigger causes it to fire in the same way the trigger did when it was originally created.</span></span> <span data-ttu-id="1a334-131">创建的 DDL 触发器默认处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="1a334-131">When DDL triggers are created, they are enabled by default.</span></span>  
  
 <span data-ttu-id="1a334-132">删除 DDL 触发器时，该触发器将从当前数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="1a334-132">When a DDL trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="1a334-133">DDL 触发器范围内的任何对象或数据均不受影响。</span><span class="sxs-lookup"><span data-stu-id="1a334-133">Any objects or data upon which the DDL trigger is scoped are not affected.</span></span>  
  
 <span data-ttu-id="1a334-134">**禁用 DDL 触发器**</span><span class="sxs-lookup"><span data-stu-id="1a334-134">**To disable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-135">DISABLE TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/disable-trigger-transact-sql)  
  
-   [<span data-ttu-id="1a334-136">ALTER TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-136">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="1a334-137">**启用 DDL 触发器**</span><span class="sxs-lookup"><span data-stu-id="1a334-137">**To enable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-138">ENABLE TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/enable-trigger-transact-sql)  
  
-   [<span data-ttu-id="1a334-139">ALTER TABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-139">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="1a334-140">**删除 DDL 触发器**</span><span class="sxs-lookup"><span data-stu-id="1a334-140">**To delete a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="1a334-141">DROP TRIGGER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a334-141">DROP TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-trigger-transact-sql)  
  
  
