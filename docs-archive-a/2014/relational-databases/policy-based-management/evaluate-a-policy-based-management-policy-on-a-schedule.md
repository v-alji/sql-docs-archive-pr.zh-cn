---
title: 定期评估基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f1c6b1a7d13d14c02f4b4e537c2dbdb2df39d02c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689331"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a><span data-ttu-id="dc811-102">定期评估基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="dc811-102">Evaluate a Policy-Based Management Policy on a Schedule</span></span>
  <span data-ttu-id="dc811-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中按计划评估基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="dc811-103">This topic describes how to evaluate a Policy-Based Management policy on a schedule in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="dc811-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="dc811-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dc811-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="dc811-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dc811-106">安全性</span><span class="sxs-lookup"><span data-stu-id="dc811-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dc811-107">**若要按计划评估策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="dc811-107">**To evaluate a policy on a schedule, using:**</span></span>  
  
     [<span data-ttu-id="dc811-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dc811-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dc811-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="dc811-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dc811-110">Security</span><span class="sxs-lookup"><span data-stu-id="dc811-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dc811-111">权限</span><span class="sxs-lookup"><span data-stu-id="dc811-111">Permissions</span></span>  
 <span data-ttu-id="dc811-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="dc811-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dc811-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dc811-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a><span data-ttu-id="dc811-114">按计划评估策略</span><span class="sxs-lookup"><span data-stu-id="dc811-114">To evaluate a policy on a schedule</span></span>  
  
1.  <span data-ttu-id="dc811-115">在 **“对象资源管理器”** 中，单击加号以展开包含要评估的策略计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="dc811-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy schedule that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="dc811-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="dc811-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="dc811-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="dc811-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="dc811-118">单击加号以便展开 **“策略”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="dc811-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="dc811-119">右键单击要评估其计划的策略，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="dc811-119">Right-click the policy whose schedule you what to evaluate and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="dc811-120">在“打开策略 - policy_name”对话框的“评估模式”列表中，选择“按计划”     。</span><span class="sxs-lookup"><span data-stu-id="dc811-120">On the **Open Policy -**_policy_name_ dialog box, in the **Evaluation Mode** list, select **On schedule**.</span></span>  
  
7.  <span data-ttu-id="dc811-121">在 **“计划”** 中，单击 **“选取”** 指定现有的计划，或 **“新建”** 创建新的计划。</span><span class="sxs-lookup"><span data-stu-id="dc811-121">Under **Schedule**, click either **Pick** to specify an existing schedule or **New** to create a new schedule.</span></span>  
  
8.  <span data-ttu-id="dc811-122">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="dc811-122">When finished, click **OK**.</span></span>  
  
  
