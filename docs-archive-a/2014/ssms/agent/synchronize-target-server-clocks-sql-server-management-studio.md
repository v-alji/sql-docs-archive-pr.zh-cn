---
title: 同步目标服务器时钟 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e7150cd42699503ab22cdd89fb6206194bd64e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682652"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a><span data-ttu-id="b6d0d-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b6d0d-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b6d0d-103">本主题介绍了如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使目标服务器时钟与主服务器时钟同步。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-103">This topic describes how to synchronize target server clocks in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] with the master server clock by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b6d0d-104">同步这些系统时钟可以为实现您的作业计划提供支持。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-104">Synchronizing these system clocks supports your job schedules.</span></span>  
  
 <span data-ttu-id="b6d0d-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b6d0d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6d0d-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6d0d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6d0d-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b6d0d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6d0d-108">**若要同步目标服务器的时钟，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b6d0d-108">**To synchronize target server clocks, using:**</span></span>  
  
     [<span data-ttu-id="b6d0d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6d0d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b6d0d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6d0d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6d0d-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b6d0d-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6d0d-112">Security</span><span class="sxs-lookup"><span data-stu-id="b6d0d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6d0d-113">权限</span><span class="sxs-lookup"><span data-stu-id="b6d0d-113">Permissions</span></span>  
 <span data-ttu-id="b6d0d-114">要求具有 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6d0d-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6d0d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="b6d0d-116">同步目标服务器的时钟</span><span class="sxs-lookup"><span data-stu-id="b6d0d-116">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="b6d0d-117">在 **“对象资源管理器”** 中，单击加号以展开要使目标服务器时钟与主服务器时钟同步的服务器。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-117">In **Object Explorer,** click the plus sign to expand the server where you want to synchronize the target server clocks with the master server clock.</span></span>  
  
2.  <span data-ttu-id="b6d0d-118">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，然后选择“管理目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="b6d0d-119">在 **“管理目标服务器”** 对话框中，单击 **“发布指令”**。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-119">In the **Manage Target Servers** dialog box, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="b6d0d-120">在 **“指令类型”** 列表中，选择 **“同步时钟”**。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-120">In the **Instruction type** list, select **Synchronize clocks**.</span></span>  
  
5.  <span data-ttu-id="b6d0d-121">在 **“收件人”** 下，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="b6d0d-121">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="b6d0d-122">单击 **“所有目标服务器”** 使所有目标服务器时钟与主服务器时钟同步。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-122">Click **All target servers** to synchronize all target server clocks with the master server clock.</span></span>  
  
    -   <span data-ttu-id="b6d0d-123">单击 **“以下目标服务器”** 同步某些特定的服务器时钟，然后选择要使其时钟与主服务器时钟同步的每台目标服务器。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-123">Click **These target servers** to synchronize certain server clocks, and then select each target server whose clock you want to synchronize with the master server clock.</span></span>  
  
6.  <span data-ttu-id="b6d0d-124">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-124">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b6d0d-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6d0d-125">Using Transact-SQL</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="b6d0d-126">同步目标服务器的时钟</span><span class="sxs-lookup"><span data-stu-id="b6d0d-126">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="b6d0d-127">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6d0d-128">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b6d0d-129">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 <span data-ttu-id="b6d0d-130">有关详细信息，请参阅[&#40;transact-sql&#41;sp_resync_targetserver ](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b6d0d-130">For more information, see [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).</span></span>  
  
  
