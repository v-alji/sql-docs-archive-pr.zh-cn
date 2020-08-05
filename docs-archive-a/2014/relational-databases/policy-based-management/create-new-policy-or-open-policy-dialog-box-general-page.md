---
title: “创建新策略”或“打开策略”对话框，“常规”页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.newgroup.f1
- sql12.swb.dmf.policy.f1
- sql12.swb.dmf.policy.filter.f1
ms.assetid: c00bebd0-d04b-4c64-840e-8b7a2c603436
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4b67cb8faf18001b841824b806e7befc0683d457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580212"
---
# <a name="create-new-policy-or-open-policy-dialog-box-general-page"></a><span data-ttu-id="bf434-102">“创建新策略”或“打开策略”对话框，“常规”页</span><span class="sxs-lookup"><span data-stu-id="bf434-102">Create New Policy or Open Policy Dialog Box, General Page</span></span>
  <span data-ttu-id="bf434-103">使用此对话框可创建新的基于策略的管理策略，或者修改现有策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-103">Use this dialog box to create a new Policy-Based Management policy or modify an existing policy.</span></span> <span data-ttu-id="bf434-104">可以将 **“针对目标”** 和 **“服务器限制”** 区域作为筛选器，将策略限制为所有可能的目标的子集。</span><span class="sxs-lookup"><span data-stu-id="bf434-104">Use the **Against targets** and **Server restriction** areas as a filter to limit policies to a subset of all possible targets.</span></span> <span data-ttu-id="bf434-105">对于要用作目标筛选器的条件，必须在物理方面中对其进行定义，并且不能包含函数和 LIKE 运算符。</span><span class="sxs-lookup"><span data-stu-id="bf434-105">For conditions to be used as target filters, they must be defined on a physical facet, must not contain functions, and must not contain the LIKE operator.</span></span> <span data-ttu-id="bf434-106">在系统计算某一策略的对象集时，默认情况下将排除系统对象。</span><span class="sxs-lookup"><span data-stu-id="bf434-106">When the system computes the object set for a policy, by default the system objects are excluded.</span></span>  <span data-ttu-id="bf434-107">例如，如果该策略的对象集引用所有表，则该策略将不适用于系统表。</span><span class="sxs-lookup"><span data-stu-id="bf434-107">For example, if the object set of the policy refers to all tables, the policy will not apply to system tables.</span></span> <span data-ttu-id="bf434-108">如果用户想要评估针对系统对象的策略，可以显式向对象集添加系统对象。</span><span class="sxs-lookup"><span data-stu-id="bf434-108">If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set.</span></span> <span data-ttu-id="bf434-109">但是，尽管 **“按计划检查”** 评估模式支持所有策略，但出于性能原因， **“更改时检查”** 并不支持具有任意对象集的所有策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-109">However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode.</span></span> <span data-ttu-id="bf434-110">有关详细信息，请参阅 [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf434-110">For more information, see [https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf434-111">选项</span><span class="sxs-lookup"><span data-stu-id="bf434-111">Options</span></span>  
 <span data-ttu-id="bf434-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="bf434-112">**Name**</span></span>  
 <span data-ttu-id="bf434-113">对于新策略，请键入新策略的名称。</span><span class="sxs-lookup"><span data-stu-id="bf434-113">For a new policy, type the new policy name.</span></span> <span data-ttu-id="bf434-114">对于现有策略，将显示其名称。</span><span class="sxs-lookup"><span data-stu-id="bf434-114">For an existing policy, the name is displayed.</span></span>  
  
 <span data-ttu-id="bf434-115">**已启用**</span><span class="sxs-lookup"><span data-stu-id="bf434-115">**Enabled**</span></span>  
 <span data-ttu-id="bf434-116">选中“已启用”  复选框可启用策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-116">Select the **Enabled** check box to enable the policy.</span></span> <span data-ttu-id="bf434-117">清除 **“已启用”** 复选框可禁用策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-117">Clear the **Enabled** check box to disable the policy.</span></span> <span data-ttu-id="bf434-118">**“已启用”** 框适用于策略自动化。</span><span class="sxs-lookup"><span data-stu-id="bf434-118">The **Enabled** box applies to policy automation.</span></span> <span data-ttu-id="bf434-119">它将创建或删除策略的自动化系统。</span><span class="sxs-lookup"><span data-stu-id="bf434-119">It creates or removes the automation system for the policy.</span></span> <span data-ttu-id="bf434-120">自动化使用以下机制：</span><span class="sxs-lookup"><span data-stu-id="bf434-120">Automation uses the following mechanisms:</span></span>  
  
 <span data-ttu-id="bf434-121">**更改时: 禁止**</span><span class="sxs-lookup"><span data-stu-id="bf434-121">**On change: prevent**</span></span>  
 <span data-ttu-id="bf434-122">数据库触发器强制要求符合策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-122">A database trigger enforces compliance.</span></span>  
  
 <span data-ttu-id="bf434-123">**更改时: 仅记录**</span><span class="sxs-lookup"><span data-stu-id="bf434-123">**On change: log only**</span></span>  
 <span data-ttu-id="bf434-124">通知服务事件检查是否符合策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-124">A notification services event checks for compliance.</span></span>  
  
 <span data-ttu-id="bf434-125">**按计划**</span><span class="sxs-lookup"><span data-stu-id="bf434-125">**On schedule**</span></span>  
 <span data-ttu-id="bf434-126">创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业以定期检查是否符合策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-126">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created to check for compliance on a schedule.</span></span>  
  
 <span data-ttu-id="bf434-127">使用 **“按需”** 评估模式运行的策略不使用此复选框。</span><span class="sxs-lookup"><span data-stu-id="bf434-127">Policies that are run using **On demand** evaluation mode do not use this check box.</span></span>  
  
 <span data-ttu-id="bf434-128">**检查条件**</span><span class="sxs-lookup"><span data-stu-id="bf434-128">**Check condition**</span></span>  
 <span data-ttu-id="bf434-129">选择此策略使用的基于策略的管理条件。</span><span class="sxs-lookup"><span data-stu-id="bf434-129">Select the Policy-Based Management condition that this policy uses.</span></span> <span data-ttu-id="bf434-130">将列出服务器上关联的基于策略的管理方面的所有条件。</span><span class="sxs-lookup"><span data-stu-id="bf434-130">All conditions on the server for the associated Policy-Based Management facet are listed.</span></span> <span data-ttu-id="bf434-131">单击 **“新建条件”** 可创建新的条件。</span><span class="sxs-lookup"><span data-stu-id="bf434-131">Click **New condition** to create a new condition.</span></span> <span data-ttu-id="bf434-132">单击省略号“(…)”按钮可修改条件  。</span><span class="sxs-lookup"><span data-stu-id="bf434-132">Click the ellipsis (**...**) button to modify the condition.</span></span>  
  
 <span data-ttu-id="bf434-133">**“针对目标”**</span><span class="sxs-lookup"><span data-stu-id="bf434-133">**Against targets**</span></span>  
 <span data-ttu-id="bf434-134">选择此方面完成筛选表达式时可使用的目标类型。</span><span class="sxs-lookup"><span data-stu-id="bf434-134">Select the target types that are available for this facet to complete a filter expression.</span></span>  
  
 <span data-ttu-id="bf434-135">**评估模式**</span><span class="sxs-lookup"><span data-stu-id="bf434-135">**Evaluation Mode**</span></span>  
 <span data-ttu-id="bf434-136">为策略选择评估模式。</span><span class="sxs-lookup"><span data-stu-id="bf434-136">Select the evaluation mode for the policy.</span></span> <span data-ttu-id="bf434-137">可以检查某些策略，但不能强制实施这些策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-137">Some policies can be checked but not enforced.</span></span> <span data-ttu-id="bf434-138">评估模式包括：</span><span class="sxs-lookup"><span data-stu-id="bf434-138">The evaluation modes are as follows:</span></span>  
  
 <span data-ttu-id="bf434-139">**“按需”**</span><span class="sxs-lookup"><span data-stu-id="bf434-139">**On demand**</span></span>  
 <span data-ttu-id="bf434-140">只能从“评估”  对话框中运行策略。</span><span class="sxs-lookup"><span data-stu-id="bf434-140">Policy will only be run when you run it from the **Evaluate** dialog box.</span></span>  
  
 <span data-ttu-id="bf434-141">**按计划**</span><span class="sxs-lookup"><span data-stu-id="bf434-141">**On schedule**</span></span>  
 <span data-ttu-id="bf434-142">定期评估策略、记录不符合要求的策略的日志条目并创建报告。</span><span class="sxs-lookup"><span data-stu-id="bf434-142">Periodically evaluates the policy, records a log entry for policies that have out-of-compliance, and creates a report.</span></span> <span data-ttu-id="bf434-143">启用 **“计划”** 框。</span><span class="sxs-lookup"><span data-stu-id="bf434-143">Enables the **Schedule** box.</span></span>  
  
 <span data-ttu-id="bf434-144">**更改时: 仅记录**</span><span class="sxs-lookup"><span data-stu-id="bf434-144">**On change: log only**</span></span>  
 <span data-ttu-id="bf434-145">当尝试进行更改时，此选项不会禁止不符合策略的更改，但会记录违反策略的情况。</span><span class="sxs-lookup"><span data-stu-id="bf434-145">When changes are tried, this option does not prevent out-of-compliance changes, but logs policy violations.</span></span>  
  
 <span data-ttu-id="bf434-146">**更改时: 禁止**</span><span class="sxs-lookup"><span data-stu-id="bf434-146">**On change: prevent**</span></span>  
 <span data-ttu-id="bf434-147">当尝试进行更改时，此选项禁止违反策略的更改。</span><span class="sxs-lookup"><span data-stu-id="bf434-147">When changes are tried, this option prevents changes that would violate the policy.</span></span>  
  
 <span data-ttu-id="bf434-148">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="bf434-148">**Schedule**</span></span>  
 <span data-ttu-id="bf434-149">此选项在选择了“按计划”  评估模式的情况下显示。</span><span class="sxs-lookup"><span data-stu-id="bf434-149">This option appears when **On schedule** evaluation mode is selected.</span></span> <span data-ttu-id="bf434-150">键入计划的名称，单击 **“选取”** ，从列表中选择一个计划，或者单击 **“新建”** 以创建新计划。</span><span class="sxs-lookup"><span data-stu-id="bf434-150">Type the name of the schedule, click **Pick** to select a schedule from a list, or click **New** to create a new schedule.</span></span> <span data-ttu-id="bf434-151">若要启用计划区域，必须选择 **“按计划”** 。</span><span class="sxs-lookup"><span data-stu-id="bf434-151">To enable the schedule area, **On schedule** must be selected.</span></span>  
  
 <span data-ttu-id="bf434-152">**“服务器限制”**</span><span class="sxs-lookup"><span data-stu-id="bf434-152">**Server restriction**</span></span>  
 <span data-ttu-id="bf434-153">选择适用于此策略的服务器类型。</span><span class="sxs-lookup"><span data-stu-id="bf434-153">Select the types of servers that are appropriate for this policy.</span></span> <span data-ttu-id="bf434-154">选项为 **“无”** ，或者选择一个条件以筛选可能的服务器。</span><span class="sxs-lookup"><span data-stu-id="bf434-154">Options are **None** or select a condition that filters the possible servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf434-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf434-155">See Also</span></span>  
 [<span data-ttu-id="bf434-156">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="bf434-156">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
