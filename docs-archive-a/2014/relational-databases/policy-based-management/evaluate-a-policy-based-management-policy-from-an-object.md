---
title: 评估来自对象的基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f0de02092c87a727b723a5940805f34a75052e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588472"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a><span data-ttu-id="13b27-102">评估来自对象的基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="13b27-102">Evaluate a Policy-Based Management Policy from an Object</span></span>
  <span data-ttu-id="13b27-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中评估来自服务器实例、数据库或数据库对象的策略。</span><span class="sxs-lookup"><span data-stu-id="13b27-103">This topic describes how to evaluate a policy from a server instance, database, or database object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="13b27-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="13b27-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="13b27-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="13b27-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="13b27-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="13b27-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="13b27-107">安全性</span><span class="sxs-lookup"><span data-stu-id="13b27-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="13b27-108">**若要从对象评估策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="13b27-108">**To evaluate a policy from an object, using:**</span></span>  
  
     [<span data-ttu-id="13b27-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13b27-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="13b27-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="13b27-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="13b27-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="13b27-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="13b27-112">执行模式定义为策略的一部分，无法在 **“评估策略”** 对话框中更改。</span><span class="sxs-lookup"><span data-stu-id="13b27-112">The execution mode is defined as part of the policy and cannot be changed in the **Evaluate Policies** dialog box.</span></span>  
  
-   <span data-ttu-id="13b27-113">**“评估策略”** 对话框仅显示适用于数据库对象的策略。</span><span class="sxs-lookup"><span data-stu-id="13b27-113">The **Evaluate Policies** dialog box only shows policies appropriate for the database object.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="13b27-114">Security</span><span class="sxs-lookup"><span data-stu-id="13b27-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="13b27-115">权限</span><span class="sxs-lookup"><span data-stu-id="13b27-115">Permissions</span></span>  
 <span data-ttu-id="13b27-116">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="13b27-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="13b27-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13b27-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a><span data-ttu-id="13b27-118">从对象评估策略</span><span class="sxs-lookup"><span data-stu-id="13b27-118">To evaluate a policy from an object</span></span>  
  
1.  <span data-ttu-id="13b27-119">在对象资源管理器中，右键单击某个服务器实例、数据库或数据库对象，指向“策略”，然后选择“评估”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="13b27-119">In Object Explorer, right-click a server instance, a database, or a database object, point to **Policies**, and select **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="13b27-120">在 **“评估策略”** 对话框中，选择一个或多个策略，然后单击 **“评估”** 以在评估模式下运行策略。</span><span class="sxs-lookup"><span data-stu-id="13b27-120">In the **Evaluate Policies** dialog box, select one or more policies and click **Evaluate** to run the policy in evaluation mode.</span></span> <span data-ttu-id="13b27-121">这会为目标集生成符合报告，但不会重新配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或强制要求以后符合策略。</span><span class="sxs-lookup"><span data-stu-id="13b27-121">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span> <span data-ttu-id="13b27-122">对于不符合所选策略且具有可通过基于策略的管理进行重新配置的属性的目标，可以通过单击“应用”\*\*\*\* 强制符合策略。</span><span class="sxs-lookup"><span data-stu-id="13b27-122">For targets that do not comply with the selected policies and have properties that can be reconfigured by Policy-Based Management, you can enforce policy compliance by clicking **Apply**.</span></span> <span data-ttu-id="13b27-123">有关 **“评估策略** 对话框中的可用选项的详细信息，请参阅 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md)、 [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)和 [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="13b27-123">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md), and [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="13b27-124">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="13b27-124">When finished, click **Close**.</span></span>  
  
  
