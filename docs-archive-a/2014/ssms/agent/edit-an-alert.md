---
title: 编辑警报 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], modifying
- modifying alerts
ms.assetid: f518e528-cc8f-446a-b37d-98505b86e430
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1eae606b3c2ca4c18d088e650e774986d4e31387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587694"
---
# <a name="edit-an-alert"></a><span data-ttu-id="ad4cd-102">Edit an Alert</span><span class="sxs-lookup"><span data-stu-id="ad4cd-102">Edit an Alert</span></span>
  <span data-ttu-id="ad4cd-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中编辑代理警报 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-103">This topic describes how to edit a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ad4cd-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ad4cd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad4cd-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ad4cd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad4cd-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ad4cd-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad4cd-107">**若要编辑警报，可使用：**</span><span class="sxs-lookup"><span data-stu-id="ad4cd-107">**To edit an alert, using:**</span></span>  
  
     [<span data-ttu-id="ad4cd-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad4cd-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad4cd-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad4cd-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad4cd-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="ad4cd-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad4cd-111">Security</span><span class="sxs-lookup"><span data-stu-id="ad4cd-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad4cd-112">权限</span><span class="sxs-lookup"><span data-stu-id="ad4cd-112">Permissions</span></span>  
 <span data-ttu-id="ad4cd-113">默认情况下， **sysadmin** 固定服务器角色的成员可以编辑警报中的信息。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="ad4cd-114">其他用户必须被授予 **msdb** 数据库中的 **SQLAgentOperatorRole** 固定数据库角色的权限。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad4cd-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad4cd-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="ad4cd-116">编辑警报</span><span class="sxs-lookup"><span data-stu-id="ad4cd-116">To edit an alert</span></span>  
  
1.  <span data-ttu-id="ad4cd-117">在 **“对象资源管理器”** 中，单击加号以展开包含要编辑的警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-117">In **Object Explorer,** click the plus sign to expand the server containing the alert you want to edit.</span></span>  
  
2.  <span data-ttu-id="ad4cd-118">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="ad4cd-119">单击加号以展开 **“警报”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="ad4cd-120">右键单击要编辑的警报，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-120">Right-click the alert you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="ad4cd-121">在 **“常规”**、 **“响应”** 和 **“选项”** 页上更新警报属性。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-121">Update the alert properties on the **General**, **Response**, and **Options** pages.</span></span>  
  
6.  <span data-ttu-id="ad4cd-122">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad4cd-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad4cd-123">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="ad4cd-124">编辑警报</span><span class="sxs-lookup"><span data-stu-id="ad4cd-124">To edit an alert</span></span>  
  
1.  <span data-ttu-id="ad4cd-125">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad4cd-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad4cd-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="ad4cd-128">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_alert ](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ad4cd-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
