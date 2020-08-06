---
title: 启动或停止收集组 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e37d4b2edcd7a6e048c405b072bcbf9b1fef78c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589719"
---
# <a name="start-or-stop-a-collection-set"></a><span data-ttu-id="0d0f4-102">启动或停止收集组</span><span class="sxs-lookup"><span data-stu-id="0d0f4-102">Start or Stop a Collection Set</span></span>
  <span data-ttu-id="0d0f4-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中启动或停止收集组。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-103">This topic describes how to start or stop a collection set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0d0f4-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0d0f4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d0f4-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0d0f4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d0f4-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0d0f4-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0d0f4-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="0d0f4-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="0d0f4-108">建议</span><span class="sxs-lookup"><span data-stu-id="0d0f4-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="0d0f4-109">安全性</span><span class="sxs-lookup"><span data-stu-id="0d0f4-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d0f4-110">**若要启动或停止收集组，请使用：**</span><span class="sxs-lookup"><span data-stu-id="0d0f4-110">**To start or stop a collection set, using:**</span></span>  
  
     [<span data-ttu-id="0d0f4-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d0f4-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0d0f4-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d0f4-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d0f4-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="0d0f4-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0d0f4-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0d0f4-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0d0f4-115">数据收集器存储过程和目录视图存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-115">Data Collector stored procedures and catalog views are stored in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="0d0f4-116">与常规存储过程不同的是，数据收集器存储过程的参数已严格类型化，不支持自动的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-116">Unlike regular stored procedures, the parameters for data collector stored procedures are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="0d0f4-117">如果这些参数不是使用正确的输入参数数据类型（正如参数说明中指定的一样）调用的，则存储过程会返回错误。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-117">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="0d0f4-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="0d0f4-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="0d0f4-119">必须启动 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-119">SQL Server Agent must be started.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0d0f4-120">建议</span><span class="sxs-lookup"><span data-stu-id="0d0f4-120">Recommendations</span></span>  
  
-   <span data-ttu-id="0d0f4-121">若要获取有关收集组的信息，请查询 [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-121">To obtain information about collection sets, query the [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) catalog view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d0f4-122">Security</span><span class="sxs-lookup"><span data-stu-id="0d0f4-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d0f4-123">权限</span><span class="sxs-lookup"><span data-stu-id="0d0f4-123">Permissions</span></span>  
 <span data-ttu-id="0d0f4-124">要求具有 **dc_operator** 固定数据库角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-124">Requires membership in the **dc_operator** fixed database role.</span></span> <span data-ttu-id="0d0f4-125">如果收集组没有代理帐户，则需要具有 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-125">If the collection set does not have a proxy account, membership in the **sysadmin** fixed server role is required.Examples</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d0f4-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d0f4-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="0d0f4-127">启动收集组</span><span class="sxs-lookup"><span data-stu-id="0d0f4-127">To start a collection set</span></span>  
  
1.  <span data-ttu-id="0d0f4-128">在对象资源管理器中，依次展开 **“管理”** 节点、 **“数据收集”** 和 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-128">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="0d0f4-129">右键单击要启动的收集组，然后单击“启动数据收集组”  。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-129">Right-click the collection set that you want to start, and then click **Start Data Collection Set**.</span></span>  
  
     <span data-ttu-id="0d0f4-130">将出现一个消息框，显示此操作的结果，收集组图标上的绿色箭头指示收集组已经启动。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-130">A message box displays the results of this action, and a green arrow on the icon for the collection set indicates that the collection set has started.</span></span>  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="0d0f4-131">停止收集组</span><span class="sxs-lookup"><span data-stu-id="0d0f4-131">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="0d0f4-132">在对象资源管理器中，依次展开 **“管理”** 节点、 **“数据收集”** 和 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-132">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="0d0f4-133">右键单击要停止的收集组，然后单击 **“停止数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-133">Right-click the collection set that you want to stop, and then click **Stop Data Collection Set**.</span></span>  
  
     <span data-ttu-id="0d0f4-134">将出现一个消息框，显示此操作的结果，收集组图标上的红色圆圈指示收集组已经停止。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-134">A message box displays the results of this action, and a red circle on the icon for the collection set indicates that the collection set has stopped.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0d0f4-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d0f4-135">Using Transact-SQL</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="0d0f4-136">启动收集组</span><span class="sxs-lookup"><span data-stu-id="0d0f4-136">To start a collection set</span></span>  
  
1.  <span data-ttu-id="0d0f4-137">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d0f4-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d0f4-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0d0f4-140">此示例使用 [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) 启动 ID 为 `1`的收集组。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-140">This example uses [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) to start the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="0d0f4-141">停止收集组</span><span class="sxs-lookup"><span data-stu-id="0d0f4-141">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="0d0f4-142">连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-142">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d0f4-143">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d0f4-144">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0d0f4-145">此示例使用 [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) 停止 ID 为 `1`的收集组。</span><span class="sxs-lookup"><span data-stu-id="0d0f4-145">This example uses [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) to stop the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d0f4-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d0f4-146">See Also</span></span>  
 <span data-ttu-id="0d0f4-147">[数据收集器视图 (Transact-SQL)](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0d0f4-147">[Data Collector Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span></span>  
 [<span data-ttu-id="0d0f4-148">“数据收集”</span><span class="sxs-lookup"><span data-stu-id="0d0f4-148">Data Collection</span></span>](data-collection.md)  
  
  
