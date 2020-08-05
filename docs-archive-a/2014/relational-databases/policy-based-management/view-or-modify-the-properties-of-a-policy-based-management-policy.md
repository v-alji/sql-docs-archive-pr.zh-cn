---
title: 查看或修改基于策略的管理策略的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: da2226d3049a84098eb8e561635161f73b71ab10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580176"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a><span data-ttu-id="4096e-102">查看或修改基于策略的管理策略的属性</span><span class="sxs-lookup"><span data-stu-id="4096e-102">View or Modify the Properties of a Policy-Based Management Policy</span></span>
  <span data-ttu-id="4096e-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中查看或修改基于策略的管理策略的属性。</span><span class="sxs-lookup"><span data-stu-id="4096e-103">This topic describes how to view or modify a Policy-Based Management policy's properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4096e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="4096e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4096e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4096e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4096e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="4096e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4096e-107">**若要查看或修改策略的属性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="4096e-107">**To view or modify a policy's properties, using:**</span></span>  
  
     [<span data-ttu-id="4096e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4096e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4096e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4096e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4096e-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="4096e-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4096e-111">Security</span><span class="sxs-lookup"><span data-stu-id="4096e-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4096e-112">权限</span><span class="sxs-lookup"><span data-stu-id="4096e-112">Permissions</span></span>  
 <span data-ttu-id="4096e-113">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="4096e-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4096e-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4096e-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a><span data-ttu-id="4096e-115">查看对象的所有策略的属性</span><span class="sxs-lookup"><span data-stu-id="4096e-115">To view the properties of all policies on an object</span></span>  
  
1.  <span data-ttu-id="4096e-116">在对象资源管理器中，右键单击某个服务器、服务器对象、数据库或数据库对象，指向“策略”\*\*\*\*，然后选择“查看”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4096e-116">In Object Explorer, right-click a server, server object, database, or database object, point to **Policies** and select **View**.</span></span> <span data-ttu-id="4096e-117">若要深入了解“查看策略 - object_name”对话框中的可用选项息，请参阅[查看策略对话框](view-policies-dialog-box.md)\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="4096e-117">For more information on the available options in the **View Policies -**_object_name_ dialog box, see [View Policies Dialog Box](view-policies-dialog-box.md).</span></span>  
  
2.  <span data-ttu-id="4096e-118">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="4096e-118">When finished, click **Close**.</span></span>  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a><span data-ttu-id="4096e-119">查看或修改特定策略的属性</span><span class="sxs-lookup"><span data-stu-id="4096e-119">To view or modify a specific policy's properties</span></span>  
  
1.  <span data-ttu-id="4096e-120">在“对象资源管理器”\*\*\*\* 中，单击加号以便展开包含你要查看或修改的基于策略的管理策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="4096e-120">In **Object Explorer**, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="4096e-121">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4096e-121">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="4096e-122">单击加号以便展开 **“策略管理”**。</span><span class="sxs-lookup"><span data-stu-id="4096e-122">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="4096e-123">单击加号以便展开 **“策略”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4096e-123">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="4096e-124">右键单击要查看或修改的策略，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4096e-124">Right-click the policy that you want to view or modify and select **Properties**.</span></span> <span data-ttu-id="4096e-125">若要深入了解“打开策略 - policy_name”对话框中的可用选项，请参阅[创建新策略或打开策略对话框，“常规”页](../../integration-services/general-page-of-integration-services-designers-options.md)和[创建新策略或打开策略对话框，“说明”页](create-new-policy-or-open-policy-dialog-box-description-page.md)\*\*\*\*__。</span><span class="sxs-lookup"><span data-stu-id="4096e-125">For more information on the available options in the **Open Policy -**_policy_name_ dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) and [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
6.  <span data-ttu-id="4096e-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4096e-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4096e-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4096e-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-policys-properties"></a><span data-ttu-id="4096e-128">查看策略属性</span><span class="sxs-lookup"><span data-stu-id="4096e-128">To view a policy's properties</span></span>  
  
1.  <span data-ttu-id="4096e-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="4096e-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4096e-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="4096e-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4096e-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="4096e-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 <span data-ttu-id="4096e-132">有关详细信息，请参阅 [syspolicy_policies (Transact-SQL)](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4096e-132">For more information, see [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).</span></span>  
  
  
