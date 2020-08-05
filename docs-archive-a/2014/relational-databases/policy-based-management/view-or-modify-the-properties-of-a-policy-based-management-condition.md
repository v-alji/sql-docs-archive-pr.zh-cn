---
title: 查看或修改基于策略的管理条件的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08baec48bd13445ef56ea6a29520d23ebaf683b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580175"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a><span data-ttu-id="cc7fe-102">查看或修改基于策略的管理条件的属性</span><span class="sxs-lookup"><span data-stu-id="cc7fe-102">View or Modify the Properties of a Policy-Based Management Condition</span></span>
  <span data-ttu-id="cc7fe-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看或修改基于策略的管理条件的属性。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-103">This topic describes how to view or modify the properties of a Policy-Based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cc7fe-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="cc7fe-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cc7fe-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="cc7fe-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cc7fe-106">安全性</span><span class="sxs-lookup"><span data-stu-id="cc7fe-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cc7fe-107">**若要查看或修改条件的属性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="cc7fe-107">**To view or modify a condition's properties, using:**</span></span>  
  
     [<span data-ttu-id="cc7fe-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc7fe-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cc7fe-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc7fe-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cc7fe-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="cc7fe-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cc7fe-111">Security</span><span class="sxs-lookup"><span data-stu-id="cc7fe-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cc7fe-112">权限</span><span class="sxs-lookup"><span data-stu-id="cc7fe-112">Permissions</span></span>  
 <span data-ttu-id="cc7fe-113">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cc7fe-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cc7fe-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a><span data-ttu-id="cc7fe-115">查看或修改条件的属性</span><span class="sxs-lookup"><span data-stu-id="cc7fe-115">To view or modify a condition's properties</span></span>  
  
1.  <span data-ttu-id="cc7fe-116">在 **“对象资源管理器”** 中，单击加号以展开包含要查看或修改的条件的服务器。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-116">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="cc7fe-117">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="cc7fe-118">单击加号以便展开 **“策略管理”**。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-118">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="cc7fe-119">单击加号以便展开 **“条件”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-119">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="cc7fe-120">右键单击要查看或编辑的条件，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-120">Right-click the condition that you want to view or edit and select **Properties**.</span></span> <span data-ttu-id="cc7fe-121">若要深入了解“打开条件 - condition_name”对话框中的可用选项，请参阅[“创建新条件”或“打开条件”对话框，“常规”页](../../integration-services/general-page-of-integration-services-designers-options.md)、[“打开条件”对话框，“依赖策略”页](open-condition-dialog-box-dependent-policies-page.md)、[“创建新条件”或“打开条件”对话框，“说明”页](create-new-condition-or-open-condition-dialog-box-description-page.md)和[“高级编辑”（条件）对话框](advanced-edit-condition-dialog-box.md)\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-121">For more information on the available options in the **Open Condition -**_condition_name_ dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Open Condition Dialog Box, Dependent Policies Page](open-condition-dialog-box-dependent-policies-page.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="cc7fe-122">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cc7fe-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cc7fe-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-conditions-properties"></a><span data-ttu-id="cc7fe-124">查看条件的属性</span><span class="sxs-lookup"><span data-stu-id="cc7fe-124">To view a condition's properties</span></span>  
  
1.  <span data-ttu-id="cc7fe-125">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cc7fe-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cc7fe-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 <span data-ttu-id="cc7fe-128">有关详细信息，请参阅 [syspolicy_conditions (Transact-SQL)](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc7fe-128">For more information, see [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).</span></span>  
  
  
