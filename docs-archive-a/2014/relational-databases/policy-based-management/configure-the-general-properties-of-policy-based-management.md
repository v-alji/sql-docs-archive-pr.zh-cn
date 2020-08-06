---
title: 配置基于策略的管理的常规属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2efb37fafa29bcb043dedbcfa8719d0092b1c77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689335"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a><span data-ttu-id="33867-102">配置基于策略的管理的常规属性</span><span class="sxs-lookup"><span data-stu-id="33867-102">Configure the General Properties of Policy-Based Management</span></span>
  <span data-ttu-id="33867-103">本主题说明如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中配置基于策略的管理的属性。</span><span class="sxs-lookup"><span data-stu-id="33867-103">This topic describes how to configure the properties for Policy-Based Management in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="33867-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="33867-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="33867-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="33867-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="33867-106">安全性</span><span class="sxs-lookup"><span data-stu-id="33867-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="33867-107">**配置基于策略的管理，使用：**</span><span class="sxs-lookup"><span data-stu-id="33867-107">**To configure Policy-Based Management, using:**</span></span>  
  
     [<span data-ttu-id="33867-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33867-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="33867-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33867-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="33867-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="33867-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="33867-111">Security</span><span class="sxs-lookup"><span data-stu-id="33867-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="33867-112">权限</span><span class="sxs-lookup"><span data-stu-id="33867-112">Permissions</span></span>  
 <span data-ttu-id="33867-113">要求具有 PolicyAdministratorRole 固定数据库角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="33867-113">Requires membership in the PolicyAdministratorRole fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33867-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33867-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="33867-115">配置基于策略的管理</span><span class="sxs-lookup"><span data-stu-id="33867-115">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="33867-116">在“对象资源管理器”\*\*\*\* 中，单击加号以展开你要在其中配置基于策略的管理属性的服务器。</span><span class="sxs-lookup"><span data-stu-id="33867-116">In **Object Explorer**, click the plus sign to expand the server where you want to configure Policy-Based Management properties.</span></span>  
  
2.  <span data-ttu-id="33867-117">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="33867-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="33867-118">右键单击“策略管理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33867-118">Right-click **Policy Management** and select **Properties**.</span></span>  
  
     <span data-ttu-id="33867-119">在 **“策略管理属性”** 对话框中提供以下选项。</span><span class="sxs-lookup"><span data-stu-id="33867-119">The following options are available in **Policy Management Properties** dialog box.</span></span>  
  
     <span data-ttu-id="33867-120">**已启用**</span><span class="sxs-lookup"><span data-stu-id="33867-120">**Enabled**</span></span>  
     <span data-ttu-id="33867-121">指定是否启用基于策略的管理。</span><span class="sxs-lookup"><span data-stu-id="33867-121">Specifies whether Policy-Based Management is enabled.</span></span>  
  
     <span data-ttu-id="33867-122">**HistoryRetentionInDays**</span><span class="sxs-lookup"><span data-stu-id="33867-122">**HistoryRetentionInDays**</span></span>  
     <span data-ttu-id="33867-123">指定策略评估历史纪录应保留的天数。</span><span class="sxs-lookup"><span data-stu-id="33867-123">Specifies the number of days that policy evaluation history should be retained.</span></span> <span data-ttu-id="33867-124">如果该值为 0（默认值），则不会自动删除历史纪录。</span><span class="sxs-lookup"><span data-stu-id="33867-124">If this value is 0 (the default), the history will not be automatically removed.</span></span>  
  
     <span data-ttu-id="33867-125">**LogOnSuccess**</span><span class="sxs-lookup"><span data-stu-id="33867-125">**LogOnSuccess**</span></span>  
     <span data-ttu-id="33867-126">指定基于策略的管理是否记录成功的策略评估。</span><span class="sxs-lookup"><span data-stu-id="33867-126">Specifies whether Policy-Based Management logs successful policy evaluations.</span></span>  
  
    -   <span data-ttu-id="33867-127">如果该值为 false（默认值），则仅记录失败的策略评估。</span><span class="sxs-lookup"><span data-stu-id="33867-127">When this value is false (the default), only failed policy evaluations are logged.</span></span>  
  
    -   <span data-ttu-id="33867-128">如果该值为 true，则成功和失败的策略评估都会记录。</span><span class="sxs-lookup"><span data-stu-id="33867-128">When this value is true, both successful and failed policy evaluations are logged.</span></span>  
  
4.  <span data-ttu-id="33867-129">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="33867-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33867-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33867-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="33867-131">配置基于策略的管理</span><span class="sxs-lookup"><span data-stu-id="33867-131">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="33867-132">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="33867-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="33867-133">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="33867-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="33867-134">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="33867-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 <span data-ttu-id="33867-135">有关详细信息，请参阅 [sp_syspolicy_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="33867-135">For more information, see [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).</span></span>  
  
  
