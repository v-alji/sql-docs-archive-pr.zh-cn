---
title: 查看有关警报的信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580514"
---
# <a name="view-information-about-an-alert"></a><span data-ttu-id="7561a-102">View Information About an Alert</span><span class="sxs-lookup"><span data-stu-id="7561a-102">View Information About an Alert</span></span>
  <span data-ttu-id="7561a-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中查看有关代理警报 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 信息 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7561a-103">This topic describes how to view information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7561a-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7561a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7561a-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7561a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7561a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="7561a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7561a-107">**若要查看有关警报的信息，可使用：**</span><span class="sxs-lookup"><span data-stu-id="7561a-107">**To view information about an alert, using:**</span></span>  
  
     [<span data-ttu-id="7561a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7561a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7561a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7561a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7561a-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="7561a-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7561a-111">Security</span><span class="sxs-lookup"><span data-stu-id="7561a-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7561a-112">权限</span><span class="sxs-lookup"><span data-stu-id="7561a-112">Permissions</span></span>  
 <span data-ttu-id="7561a-113">默认情况下，只有 **sysadmin** 固定服务器角色的成员才能查看有关警报的信息。</span><span class="sxs-lookup"><span data-stu-id="7561a-113">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="7561a-114">其他用户必须被授予 **msdb** 数据库中的 **SQLAgentOperatorRole** 固定数据库角色的权限。</span><span class="sxs-lookup"><span data-stu-id="7561a-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7561a-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7561a-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="7561a-116">查看有关警报的信息</span><span class="sxs-lookup"><span data-stu-id="7561a-116">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="7561a-117">在 **“对象资源管理器”** 中，单击加号以展开要在其中查看有关警报的信息的服务器。</span><span class="sxs-lookup"><span data-stu-id="7561a-117">In **Object Explorer,** click the plus sign to expand the server where you want to view information about an alert.</span></span>  
  
2.  <span data-ttu-id="7561a-118">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="7561a-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7561a-119">单击加号以展开 **“警报”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7561a-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="7561a-120">右键单击包含要查看的信息的警报，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7561a-120">Right-click the alert that has the information you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="7561a-121">有关 alert_name__“警报属性”\*\*\*\* 对话框中包含的可用选项的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="7561a-121">For more information on the available options contained in the _alert_name_**alert properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="7561a-122">警报属性-新建警报 &#40;常规页&#41;</span><span class="sxs-lookup"><span data-stu-id="7561a-122">Alert Properties-New Alert &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="7561a-123">警报属性-新建警报 &#40;响应 "页面&#41;</span><span class="sxs-lookup"><span data-stu-id="7561a-123">Alert Properties-New Alert &#40;Response Page&#41;</span></span>](alert-properties-new-alert-response-page.md)  
  
    -   [<span data-ttu-id="7561a-124">警报属性： "新建警报 &#40;选项" 页面&#41;</span><span class="sxs-lookup"><span data-stu-id="7561a-124">Alert Properties: New Alert &#40;Options Page&#41;</span></span>](alert-properties-new-alert-options-page.md)  
  
    -   [<span data-ttu-id="7561a-125">警报属性（“历史记录”页）</span><span class="sxs-lookup"><span data-stu-id="7561a-125">Alert Properties &#40;History Page&#41;</span></span>](alert-properties-history-page.md)  
  
5.  <span data-ttu-id="7561a-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="7561a-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7561a-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7561a-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="7561a-128">查看有关警报的信息</span><span class="sxs-lookup"><span data-stu-id="7561a-128">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="7561a-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="7561a-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7561a-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7561a-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7561a-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="7561a-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 <span data-ttu-id="7561a-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_help_alert ](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7561a-132">For more information, see [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).</span></span>  
  
  
