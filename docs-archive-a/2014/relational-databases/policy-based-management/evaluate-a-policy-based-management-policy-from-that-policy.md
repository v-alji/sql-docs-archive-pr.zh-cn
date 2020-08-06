---
title: 从基于策略的管理策略评估该策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 207c86f1465c49238fc9b50ee75489b43d956caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588474"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a><span data-ttu-id="181ed-102">从基于策略的管理策略评估该策略</span><span class="sxs-lookup"><span data-stu-id="181ed-102">Evaluate a Policy-Based Management Policy from That Policy</span></span>
  <span data-ttu-id="181ed-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用策略来评估该策略。</span><span class="sxs-lookup"><span data-stu-id="181ed-103">This topic describes how to evaluate a policy using that policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="181ed-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="181ed-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="181ed-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="181ed-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="181ed-106">安全性</span><span class="sxs-lookup"><span data-stu-id="181ed-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="181ed-107">**若要评估某个策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="181ed-107">**To evaluate a policy, using:**</span></span>  
  
     [<span data-ttu-id="181ed-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="181ed-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="181ed-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="181ed-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="181ed-110">Security</span><span class="sxs-lookup"><span data-stu-id="181ed-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="181ed-111">权限</span><span class="sxs-lookup"><span data-stu-id="181ed-111">Permissions</span></span>  
 <span data-ttu-id="181ed-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="181ed-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="181ed-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="181ed-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy"></a><span data-ttu-id="181ed-114">评估策略</span><span class="sxs-lookup"><span data-stu-id="181ed-114">To evaluate a policy</span></span>  
  
1.  <span data-ttu-id="181ed-115">在 **“对象资源管理器”** 中，单击加号以展开包含要评估的策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="181ed-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="181ed-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="181ed-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="181ed-117">单击加号以便展开 **“策略管理”**。</span><span class="sxs-lookup"><span data-stu-id="181ed-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="181ed-118">单击加号以便展开 **“策略”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="181ed-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="181ed-119">右键单击要评估的策略，然后选择“评估”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="181ed-119">Right-click the policy that you want to evaluate and select **Evaluate**.</span></span>  
  
6.  <span data-ttu-id="181ed-120">在 **“评估结果”**  对话框中，可查看策略评估的结果。</span><span class="sxs-lookup"><span data-stu-id="181ed-120">In the **Evaluate Results**  dialog box, you see the results of the policy evaluation.</span></span> <span data-ttu-id="181ed-121">对于不符合策略且具有可通过基于策略的管理进行重新配置的属性的目标，可以通过单击“应用”\*\*\*\* 强制符合策略。</span><span class="sxs-lookup"><span data-stu-id="181ed-121">For targets that do not comply with the policy and have properties that can be reconfigured by Policy-Based Management, you can enforce compliance by clicking **Apply**.</span></span> <span data-ttu-id="181ed-122">有关 **“评估策略** 对话框中的可用选项的详细信息，请参阅 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) 和 [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)。</span><span class="sxs-lookup"><span data-stu-id="181ed-122">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) and [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).</span></span>  
  
7.  <span data-ttu-id="181ed-123">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="181ed-123">When finished, click **Close**.</span></span>  
  
  
