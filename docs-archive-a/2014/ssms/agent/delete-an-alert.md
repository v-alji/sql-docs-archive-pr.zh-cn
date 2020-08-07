---
title: 删除警报 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], deleting
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- removing alerts
ms.assetid: c982b208-e2d1-4d34-8cee-940b9baf6586
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15fdae19b150a5a06a32e91ec1947a0acfa5f900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588807"
---
# <a name="delete-an-alert"></a><span data-ttu-id="67c57-102">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="67c57-102">Delete an Alert</span></span>
  <span data-ttu-id="67c57-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中删除代理警报 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67c57-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="67c57-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="67c57-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="67c57-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="67c57-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="67c57-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="67c57-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="67c57-107">安全性</span><span class="sxs-lookup"><span data-stu-id="67c57-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="67c57-108">**若要删除警报，可使用：**</span><span class="sxs-lookup"><span data-stu-id="67c57-108">**To delete an alert, using:**</span></span>  
  
     [<span data-ttu-id="67c57-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="67c57-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="67c57-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="67c57-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="67c57-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="67c57-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="67c57-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="67c57-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="67c57-113">删除警报时，将同时删除与警报相关的所有通知。</span><span class="sxs-lookup"><span data-stu-id="67c57-113">Removing an alert also removes any notifications associated with the alert.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="67c57-114">Security</span><span class="sxs-lookup"><span data-stu-id="67c57-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="67c57-115">权限</span><span class="sxs-lookup"><span data-stu-id="67c57-115">Permissions</span></span>  
 <span data-ttu-id="67c57-116">默认情况下，只有 **sysadmin** 固定服务器角色的成员才能删除警报。</span><span class="sxs-lookup"><span data-stu-id="67c57-116">By default, only members of the **sysadmin** fixed server role can delete alerts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="67c57-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="67c57-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="67c57-118">删除警报</span><span class="sxs-lookup"><span data-stu-id="67c57-118">To delete an alert</span></span>  
  
1.  <span data-ttu-id="67c57-119">在 **“对象资源管理器”** 中，单击加号以展开包含要删除的 SQL Server 代理警报的服务器。</span><span class="sxs-lookup"><span data-stu-id="67c57-119">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent alert that you want to delete.</span></span>  
  
2.  <span data-ttu-id="67c57-120">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="67c57-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="67c57-121">单击加号以展开 **“警报”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="67c57-121">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="67c57-122">右键单击要删除的警报，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="67c57-122">Right-click the alert you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="67c57-123">在 **“删除对象”** 对话框中，确认已选择正确的警报，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="67c57-123">In the **Delete Object** dialog box, confirm that the correct alert is selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="67c57-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="67c57-124">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="67c57-125">删除警报</span><span class="sxs-lookup"><span data-stu-id="67c57-125">To delete an alert</span></span>  
  
1.  <span data-ttu-id="67c57-126">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="67c57-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="67c57-127">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="67c57-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="67c57-128">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="67c57-128">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the SQL Server Agent alert called 'Test Alert.'  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_alert  
       @name = N'Test Alert' ;  
    GO  
    ```  
  
 <span data-ttu-id="67c57-129">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_alert ](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="67c57-129">For more information, see s[sp_delete_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql).</span></span>  
  
  
