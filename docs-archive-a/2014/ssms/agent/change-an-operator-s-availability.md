---
title: 更改操作员的可用性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- reactivating operators
- removing operators
- deleting operators
- available operators [SQL Server]
- dropping operators
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- disabling operators
- operators (users) [Database Engine], changing availability with Management Studio
ms.assetid: 10d58b92-b67b-47e2-af9c-9f9fd6968bba
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb369ea6a2d1edf1ed8f4377b627fb1ba7339a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591087"
---
# <a name="change-an-operator39s-availability"></a><span data-ttu-id="ad9fe-102">更改操作员的可用性</span><span class="sxs-lookup"><span data-stu-id="ad9fe-102">Change an Operator&#39;s Availability</span></span>
  <span data-ttu-id="ad9fe-103">本主题介绍了如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中更改操作员接收警报通知的计划。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-103">This topic describes how to change an operator's schedule for receiving alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ad9fe-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad9fe-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad9fe-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ad9fe-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad9fe-107">**若要更改操作员的可用性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="ad9fe-107">**To change an operator's availability, using:**</span></span>  
  
     [<span data-ttu-id="ad9fe-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad9fe-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad9fe-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad9fe-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad9fe-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="ad9fe-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad9fe-111">Security</span><span class="sxs-lookup"><span data-stu-id="ad9fe-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad9fe-112">权限</span><span class="sxs-lookup"><span data-stu-id="ad9fe-112">Permissions</span></span>  
 <span data-ttu-id="ad9fe-113">只有 **sysadmin** 固定服务器角色的成员才能编辑操作员。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-113">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad9fe-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad9fe-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="ad9fe-115">更改操作员的可用性</span><span class="sxs-lookup"><span data-stu-id="ad9fe-115">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="ad9fe-116">在 **“对象资源管理器”** 中，单击加号以展开包含要启用或禁用的操作员的服务器。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-116">In **Object Explorer**, click the plus sign to expand server that contains the operator that you want to enable or disable.</span></span>  
  
2.  <span data-ttu-id="ad9fe-117">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-117">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="ad9fe-118">单击加号以展开 **“操作员”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-118">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="ad9fe-119">右键单击要启用或禁用的操作员，选择“属性”\*\*\*\*，然后单击“常规”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-119">Right-click the operator that you want to enable or disable and select **Properties**, then click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="ad9fe-120">在“operator_name 属性”__\*\*\*\* 对话框中，选中或清除“启用”\*\*\*\* 复选框。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-120">In the _operator_name_**Properties** dialog box, select or clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="ad9fe-121">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-121">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad9fe-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad9fe-122">Using Transact-SQL</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="ad9fe-123">更改操作员的可用性</span><span class="sxs-lookup"><span data-stu-id="ad9fe-123">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="ad9fe-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad9fe-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad9fe-126">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- disables the 'Fran??ois Ajenstat' operator  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="ad9fe-127">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_operator ](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ad9fe-127">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
