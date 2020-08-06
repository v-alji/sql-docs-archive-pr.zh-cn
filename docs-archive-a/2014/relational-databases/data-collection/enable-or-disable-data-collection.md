---
title: 启用或禁用数据收集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af5cc647a63d3a9451086fc9e2211dec809e88fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578898"
---
# <a name="enable-or-disable-data-collection"></a><span data-ttu-id="7f18c-102">启用或禁用数据收集</span><span class="sxs-lookup"><span data-stu-id="7f18c-102">Enable or Disable Data Collection</span></span>
  <span data-ttu-id="7f18c-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中启用或禁用数据收集。</span><span class="sxs-lookup"><span data-stu-id="7f18c-103">This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7f18c-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="7f18c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7f18c-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="7f18c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7f18c-106">安全性</span><span class="sxs-lookup"><span data-stu-id="7f18c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7f18c-107">**若要启用或禁用数据收集，请使用：**</span><span class="sxs-lookup"><span data-stu-id="7f18c-107">**To enable or disable data collection, using:**</span></span>  
  
     [<span data-ttu-id="7f18c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7f18c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7f18c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7f18c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7f18c-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="7f18c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7f18c-111">Security</span><span class="sxs-lookup"><span data-stu-id="7f18c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7f18c-112">权限</span><span class="sxs-lookup"><span data-stu-id="7f18c-112">Permissions</span></span>  
 <span data-ttu-id="7f18c-113">必须具有 **dc_admin** 或 **dc_operator** （拥有 EXECUTE 权限）固定数据库角色的成员身份才能执行此过程。</span><span class="sxs-lookup"><span data-stu-id="7f18c-113">Requires membership in the **dc_admin** or **dc_operator** (with EXECUTE permission) fixed database role to execute this procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7f18c-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7f18c-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="7f18c-115">启用数据收集器</span><span class="sxs-lookup"><span data-stu-id="7f18c-115">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="7f18c-116">在对象资源管理器中，展开 **“管理”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7f18c-116">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="7f18c-117">右键单击 **“数据收集”** ，然后单击 **“启用数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="7f18c-117">Right-click **Data Collection**, and then click **Enable Data Collection**.</span></span>  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="7f18c-118">禁用数据收集器</span><span class="sxs-lookup"><span data-stu-id="7f18c-118">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="7f18c-119">在对象资源管理器中，展开 **“管理”** 节点。</span><span class="sxs-lookup"><span data-stu-id="7f18c-119">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="7f18c-120">右键单击“数据收集”，然后单击“禁用数据收集”   。</span><span class="sxs-lookup"><span data-stu-id="7f18c-120">Right-click **Data Collection**, and then click **Disable Data Collection**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7f18c-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7f18c-121">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="7f18c-122">启用数据收集器</span><span class="sxs-lookup"><span data-stu-id="7f18c-122">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="7f18c-123">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7f18c-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7f18c-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7f18c-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7f18c-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="7f18c-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7f18c-126">此示例使用 [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) 启用数据收集器。</span><span class="sxs-lookup"><span data-stu-id="7f18c-126">This example uses [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) to enable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="7f18c-127">禁用数据收集器</span><span class="sxs-lookup"><span data-stu-id="7f18c-127">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="7f18c-128">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7f18c-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7f18c-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7f18c-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7f18c-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="7f18c-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7f18c-131">此示例使用 [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) 禁用数据收集器。</span><span class="sxs-lookup"><span data-stu-id="7f18c-131">This example uses [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) to disable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f18c-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f18c-132">See Also</span></span>  
 <span data-ttu-id="7f18c-133">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="7f18c-133">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="7f18c-134">系统存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7f18c-134">System Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
