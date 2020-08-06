---
title: 删除操作员 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75bea1c5c5fabff7ce55fe07a5181baa8f99e0fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578007"
---
# <a name="delete-an-operator"></a><span data-ttu-id="a6d4b-102">Delete an Operator</span><span class="sxs-lookup"><span data-stu-id="a6d4b-102">Delete an Operator</span></span>
  <span data-ttu-id="a6d4b-103">本主题介绍如何使用或在中删除操作员，使其不再接收 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-103">This topic describes how to remove an operator so they no longer receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a6d4b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a6d4b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a6d4b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a6d4b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a6d4b-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a6d4b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a6d4b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a6d4b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a6d4b-108">**若要删除操作员，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a6d4b-108">**To delete an operator, using:**</span></span>  
  
     [<span data-ttu-id="a6d4b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6d4b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a6d4b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6d4b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a6d4b-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="a6d4b-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a6d4b-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a6d4b-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a6d4b-113">删除操作员时，将同时删除与此操作员关联的所有通知。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-113">When an operator is removed, all the notifications associated with the operator are also removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a6d4b-114">Security</span><span class="sxs-lookup"><span data-stu-id="a6d4b-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a6d4b-115">权限</span><span class="sxs-lookup"><span data-stu-id="a6d4b-115">Permissions</span></span>  
 <span data-ttu-id="a6d4b-116">**sysadmin** 固定服务器角色的成员可以删除操作员。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-116">Members of the **sysadmin** fixed server role can delete operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a6d4b-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6d4b-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="a6d4b-118">删除操作员</span><span class="sxs-lookup"><span data-stu-id="a6d4b-118">To delete an operator</span></span>  
  
1.  <span data-ttu-id="a6d4b-119">在 **“对象资源管理器”** 中，单击加号以展开包含要删除的操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-119">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to delete.</span></span>  
  
2.  <span data-ttu-id="a6d4b-120">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="a6d4b-121">单击加号以展开 **“操作员”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-121">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="a6d4b-122">右键单击要删除的操作员，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-122">Right-click the operator that you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="a6d4b-123">在 **“删除对象”** 对话框中，确保已选择正确的操作员，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-123">In the **Delete Object** dialog box, make sure that the correct operator is selected, and then click **OK**.</span></span> <span data-ttu-id="a6d4b-124">如果希望其他操作员收到发送给已删除操作员的警报和作业，请选择 **“重新分配给”** ，然后在列表中选择一个操作员。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-124">If you want another operator to receive the alerts and jobs sent to the deleted operator, check **Reassign to** and select an operator in the list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a6d4b-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6d4b-125">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="a6d4b-126">删除操作员</span><span class="sxs-lookup"><span data-stu-id="a6d4b-126">To delete an operator</span></span>  
  
1.  <span data-ttu-id="a6d4b-127">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6d4b-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a6d4b-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'Fran??ois Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'Fran??ois Ajenstat';  
    GO  
    ```  
  
 <span data-ttu-id="a6d4b-130">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_operator ](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a6d4b-130">For more information, see [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span></span>  
  
  
