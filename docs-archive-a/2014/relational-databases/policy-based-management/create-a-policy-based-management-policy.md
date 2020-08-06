---
title: 创建基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e76b4dce17e00bae5e8ca4fcf071868c0641c786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587368"
---
# <a name="create-a-policy-based-management-policy"></a><span data-ttu-id="d5581-102">创建基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="d5581-102">Create a Policy-Based Management Policy</span></span>
  <span data-ttu-id="d5581-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中创建基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="d5581-103">This topic describes how to create a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d5581-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d5581-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d5581-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d5581-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d5581-106">安全性</span><span class="sxs-lookup"><span data-stu-id="d5581-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d5581-107">**若要创建策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d5581-107">**To create a policy, using:**</span></span>  
  
     [<span data-ttu-id="d5581-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d5581-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d5581-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="d5581-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d5581-110">Security</span><span class="sxs-lookup"><span data-stu-id="d5581-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d5581-111">权限</span><span class="sxs-lookup"><span data-stu-id="d5581-111">Permissions</span></span>  
 <span data-ttu-id="d5581-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="d5581-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d5581-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d5581-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-policy"></a><span data-ttu-id="d5581-114">创建策略</span><span class="sxs-lookup"><span data-stu-id="d5581-114">To create a policy</span></span>  
  
1.  <span data-ttu-id="d5581-115">在“对象资源管理器”  中，单击加号以展开你要在其中创建新的基于策略的管理策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="d5581-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a new a Policy-Based Management policy.</span></span>  
  
2.  <span data-ttu-id="d5581-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d5581-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="d5581-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="d5581-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="d5581-118">右键单击“策略”  文件夹，然后选择“新建策略”  。</span><span class="sxs-lookup"><span data-stu-id="d5581-118">Right-click the **Policies** folder and select **New Policy**.</span></span>  
  
5.  <span data-ttu-id="d5581-119">在 **“创建新策略”** 对话框的 **“名称”** 框中，键入新策略的名称。</span><span class="sxs-lookup"><span data-stu-id="d5581-119">In the **Create New Policy** dialog box, in the **Name** box, type the name of the new policy.</span></span>  
  
6.  <span data-ttu-id="d5581-120">如果希望在创建策略后立即启用该策略，请选中 **“已启用”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="d5581-120">If you want the policy to be enabled as soon as it is created, select the **Enabled** check box.</span></span> <span data-ttu-id="d5581-121">如果评估模式为 **“按需”** ，则 **“已启用”** 复选框不可用。</span><span class="sxs-lookup"><span data-stu-id="d5581-121">If the evaluation mode is **On demand**, the **Enabled** check box is not available.</span></span>  
  
7.  <span data-ttu-id="d5581-122">在 **“检查条件”** 列表中，选择现有条件之一，或者选择 **“新建条件”** 。</span><span class="sxs-lookup"><span data-stu-id="d5581-122">In the **Check condition** list, select one of the existing conditions, or select **New Condition**.</span></span> <span data-ttu-id="d5581-123">若要编辑某个条件，请选择该条件，然后单击省略号 ( **...** )。有关详细信息，请参阅 [创建新的基于策略的管理条件](create-a-new-policy-based-management-condition.md) 或 [查看或修改基于策略的管理条件的属性](view-or-modify-the-properties-of-a-policy-based-management-condition.md)。</span><span class="sxs-lookup"><span data-stu-id="d5581-123">To edit a condition, select the condition and then click the ellipsis (**...**). For more information, see [Create a New Policy-Based Management Condition](create-a-new-policy-based-management-condition.md) or [View or Modify the Properties of a Policy-Based Management Condition](view-or-modify-the-properties-of-a-policy-based-management-condition.md).</span></span>  
  
8.  <span data-ttu-id="d5581-124">在 **“针对目标”** 框中，为此策略选择一种或多种目标类型。</span><span class="sxs-lookup"><span data-stu-id="d5581-124">In the **Against targets** box, select one or more target types for this policy.</span></span> <span data-ttu-id="d5581-125">有些条件和方面只能应用于某些类型的目标。</span><span class="sxs-lookup"><span data-stu-id="d5581-125">Some conditions and facets can only be applied to certain types of targets.</span></span> <span data-ttu-id="d5581-126">可用目标集显示在关联的框中。</span><span class="sxs-lookup"><span data-stu-id="d5581-126">The available target sets appear in the associated box.</span></span> <span data-ttu-id="d5581-127">展开 **“每个”** 可为某些类型的目标选择筛选条件。</span><span class="sxs-lookup"><span data-stu-id="d5581-127">Expand **Every** to select a filtering condition for some types of the targets.</span></span> <span data-ttu-id="d5581-128">如果此框中没有出现目标，则检查条件的作用域为服务器级别。</span><span class="sxs-lookup"><span data-stu-id="d5581-128">If no targets appear in this box, the check condition is scoped at the server level.</span></span>  
  
9. <span data-ttu-id="d5581-129">在 **“评估模式”** 框中，选择此策略的工作方式。</span><span class="sxs-lookup"><span data-stu-id="d5581-129">In the **Evaluation Mode** box, select how this policy will behave.</span></span> <span data-ttu-id="d5581-130">不同的条件可具有不同的有效评估模式。</span><span class="sxs-lookup"><span data-stu-id="d5581-130">Different conditions can have different valid evaluation modes.</span></span> <span data-ttu-id="d5581-131">有关有效评估模式的详细信息，请参阅 [使用基于策略的管理来管理服务器](administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="d5581-131">For more information about which evaluation modes are valid, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
10. <span data-ttu-id="d5581-132">如果要按计划评估策略，请将评估模式设置为 **“按计划”** ，然后单击 **“选取”** 选择一个计划，或者单击 **“新建”** 创建一个新计划。</span><span class="sxs-lookup"><span data-stu-id="d5581-132">If the policy will be evaluated on a schedule, set the evaluation mode to **On schedule**, and then click **Pick** to select a schedule, or click **New** to create a new schedule.</span></span>  
  
11. <span data-ttu-id="d5581-133">若要将策略限制为目标类型的子集，请在 **“服务器限制”** 框中选择限制条件，或者创建一个新条件。</span><span class="sxs-lookup"><span data-stu-id="d5581-133">To limit the policy to subset of the target types, in the **Server restriction** box, select from limiting conditions or create a new condition.</span></span>  
  
     <span data-ttu-id="d5581-134">有关 **“创建新策略”** 对话框中的可用选项的详细信息，请参阅 [“创建新策略”或“打开策略”对话框，“常规”页](../../integration-services/general-page-of-integration-services-designers-options.md) 或 [“创建新策略”或“打开策略”对话框，“说明”页](create-new-policy-or-open-policy-dialog-box-description-page.md)。</span><span class="sxs-lookup"><span data-stu-id="d5581-134">For more information on the available options in the **Create New Policy** dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) or [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
12. <span data-ttu-id="d5581-135">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d5581-135">When finished click **OK**.</span></span>  
  
  
