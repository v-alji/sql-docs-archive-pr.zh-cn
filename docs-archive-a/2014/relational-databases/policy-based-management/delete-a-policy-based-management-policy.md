---
title: 删除基于策略的管理策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policies
ms.assetid: 488f0305-190c-4223-aa5c-e9bd43b520eb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c43bc3cdf4a7a5b5d9268bbd7e68506616d1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682815"
---
# <a name="delete-a-policy-based-management-policy"></a><span data-ttu-id="fb24e-102">删除基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="fb24e-102">Delete a Policy-Based Management Policy</span></span>
  <span data-ttu-id="fb24e-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中删除基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="fb24e-103">This topic describes how to delete a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fb24e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fb24e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fb24e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fb24e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fb24e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="fb24e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fb24e-107">**若要删除策略，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fb24e-107">**To delete a policy, using:**</span></span>  
  
     [<span data-ttu-id="fb24e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fb24e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb24e-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="fb24e-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb24e-110">Security</span><span class="sxs-lookup"><span data-stu-id="fb24e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb24e-111">权限</span><span class="sxs-lookup"><span data-stu-id="fb24e-111">Permissions</span></span>  
 <span data-ttu-id="fb24e-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="fb24e-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb24e-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fb24e-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-policy"></a><span data-ttu-id="fb24e-114">删除策略</span><span class="sxs-lookup"><span data-stu-id="fb24e-114">To delete a policy</span></span>  
  
1.  <span data-ttu-id="fb24e-115">在对象资源管理器中，单击加号以便展开包含您要删除的基于策略的管理策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="fb24e-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to delete.</span></span>  
  
2.  <span data-ttu-id="fb24e-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fb24e-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="fb24e-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="fb24e-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="fb24e-118">单击加号以便展开 **“策略”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fb24e-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="fb24e-119">右键单击要删除的策略，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="fb24e-119">Right-click the policy that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="fb24e-120">在 **“删除对象”** 对话框中，确保已选择正确的条件，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="fb24e-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
