---
title: 删除基于策略的管理条件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policy conditions
ms.assetid: e04148b8-f6dd-4c50-a5ef-c650b71dbf4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02a5294ecb53db4d8baa4f3dae0a232d9551a13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577586"
---
# <a name="delete-a-policy-based-management-condition"></a><span data-ttu-id="ab8cb-102">删除基于策略的管理条件</span><span class="sxs-lookup"><span data-stu-id="ab8cb-102">Delete a Policy-Based Management Condition</span></span>
  <span data-ttu-id="ab8cb-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中删除基于策略的管理条件。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-103">This topic describes how to delete a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ab8cb-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ab8cb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab8cb-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ab8cb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab8cb-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ab8cb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab8cb-107">**若要删除条件，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ab8cb-107">**To delete a condition, using:**</span></span>  
  
     [<span data-ttu-id="ab8cb-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab8cb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab8cb-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="ab8cb-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab8cb-110">Security</span><span class="sxs-lookup"><span data-stu-id="ab8cb-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab8cb-111">权限</span><span class="sxs-lookup"><span data-stu-id="ab8cb-111">Permissions</span></span>  
 <span data-ttu-id="ab8cb-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab8cb-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab8cb-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-condition"></a><span data-ttu-id="ab8cb-114">删除条件</span><span class="sxs-lookup"><span data-stu-id="ab8cb-114">To delete a condition</span></span>  
  
1.  <span data-ttu-id="ab8cb-115">在 **“对象资源管理器”** 中，单击加号以展开包含要删除的条件的服务器。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-115">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to delete.</span></span>  
  
2.  <span data-ttu-id="ab8cb-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ab8cb-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="ab8cb-118">单击加号以便展开 **“条件”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-118">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="ab8cb-119">右键单击要删除的条件，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-119">Right-click the condition that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="ab8cb-120">在 **“删除对象”** 对话框中，确保已选择正确的条件，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ab8cb-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
