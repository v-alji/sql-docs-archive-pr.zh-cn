---
title: 导出基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15f554aeeebfd47c3fa1ea13b100fbe6bcfcc055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587366"
---
# <a name="export-a-policy-based-management-policy"></a><span data-ttu-id="779a2-102">导出基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="779a2-102">Export a Policy-Based Management Policy</span></span>
  <span data-ttu-id="779a2-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中导出基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="779a2-103">This topic describes how to export a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="779a2-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="779a2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="779a2-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="779a2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="779a2-106">安全性</span><span class="sxs-lookup"><span data-stu-id="779a2-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="779a2-107">**若要导出策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="779a2-107">**To export a policy, using:**</span></span>  
  
     [<span data-ttu-id="779a2-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="779a2-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="779a2-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="779a2-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="779a2-110">Security</span><span class="sxs-lookup"><span data-stu-id="779a2-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="779a2-111">权限</span><span class="sxs-lookup"><span data-stu-id="779a2-111">Permissions</span></span>  
 <span data-ttu-id="779a2-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="779a2-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="779a2-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="779a2-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-export-a-policy"></a><span data-ttu-id="779a2-114">导出策略</span><span class="sxs-lookup"><span data-stu-id="779a2-114">To export a policy</span></span>  
  
1.  <span data-ttu-id="779a2-115">在对象资源管理器中，单击加号以便展开包含您要导出的基于策略的管理策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="779a2-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to export.</span></span>  
  
2.  <span data-ttu-id="779a2-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="779a2-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="779a2-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="779a2-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="779a2-118">单击加号以便展开 **“策略”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="779a2-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="779a2-119">右键单击要导出的策略，然后选择“导出策略”  。</span><span class="sxs-lookup"><span data-stu-id="779a2-119">Right-click the policy that you want to export and select **Export Policy**.</span></span>  
  
6.  <span data-ttu-id="779a2-120">在 **“导出策略”** 对话框中，在地址栏中键入文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="779a2-120">In the **Export Policy** dialog box, type the path and name of the file in the address bar.</span></span> <span data-ttu-id="779a2-121">或者，在对话框的导航窗格中找到文件的合适位置，然后在 **“文件名”** 框中键入 XML 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="779a2-121">Alternately, find a suitable location for the file in the dialog box's navigation pane, and then type the name of the XML file in the **File Name** box.</span></span>  
  
7.  <span data-ttu-id="779a2-122">完成后，单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="779a2-122">When finished, click **Save**.</span></span>  
  
  
