---
title: 删除对不推荐使用的系统存储过程的引用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691510"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a><span data-ttu-id="24df6-102">删除对不推荐使用的系统存储过程的引用</span><span class="sxs-lookup"><span data-stu-id="24df6-102">Remove references to deprecated system stored procedures</span></span>
  <span data-ttu-id="24df6-103">升级顾问检测到一些语句引用了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不再可用的未记录的系统存储过程和扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="24df6-103">Upgrade Advisor detected statements that reference undocumented system stored procedures and extended stored procedures that are no longer available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24df6-104">引用这些对象的语句将失败。</span><span class="sxs-lookup"><span data-stu-id="24df6-104">Statements that reference these objects will fail.</span></span> <span data-ttu-id="24df6-105">请勿使用未记录的系统对象或 API，因为在将来的版本中该功能可能会更改或删除，且不会给出相关通知。</span><span class="sxs-lookup"><span data-stu-id="24df6-105">Do not use undocumented system objects or APIs as the functionality might change or be removed without notification in a future release.</span></span>  
  
## <a name="component"></a><span data-ttu-id="24df6-106">组件</span><span class="sxs-lookup"><span data-stu-id="24df6-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="24df6-107">说明</span><span class="sxs-lookup"><span data-stu-id="24df6-107">Description</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="24df6-108">已记录的系统存储过程</span><span class="sxs-lookup"><span data-stu-id="24df6-108">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="24df6-109">以下已记录的系统存储过程已被删除：</span><span class="sxs-lookup"><span data-stu-id="24df6-109">The following documented system stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="24df6-110">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="24df6-110">sp_addalias</span></span>  
  
-   <span data-ttu-id="24df6-111">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="24df6-111">sp_addgroup</span></span>  
  
-   <span data-ttu-id="24df6-112">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="24df6-112">sp_changegroup</span></span>  
  
-   <span data-ttu-id="24df6-113">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="24df6-113">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="24df6-114">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="24df6-114">sp_helpgroup</span></span>  
  
### <a name="undocumented-system-stored-procedures"></a><span data-ttu-id="24df6-115">未记录的系统存储过程</span><span class="sxs-lookup"><span data-stu-id="24df6-115">Undocumented System Stored Procedures</span></span>  
 <span data-ttu-id="24df6-116">以下未记录的系统存储过程和扩展存储过程已被删除：</span><span class="sxs-lookup"><span data-stu-id="24df6-116">The following undocumented system stored procedures and extended stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="24df6-117">sp_articlesynctranprocs</span><span class="sxs-lookup"><span data-stu-id="24df6-117">sp_articlesynctranprocs</span></span>  
  
-   <span data-ttu-id="24df6-118">sp_diskdefault</span><span class="sxs-lookup"><span data-stu-id="24df6-118">sp_diskdefault</span></span>  
  
-   <span data-ttu-id="24df6-119">sp_EventLog</span><span class="sxs-lookup"><span data-stu-id="24df6-119">sp_EventLog</span></span>  
  
-   <span data-ttu-id="24df6-120">sp_GetMBCSCharLen</span><span class="sxs-lookup"><span data-stu-id="24df6-120">sp_GetMBCSCharLen</span></span>  
  
-   <span data-ttu-id="24df6-121">sp_helplog</span><span class="sxs-lookup"><span data-stu-id="24df6-121">sp_helplog</span></span>  
  
-   <span data-ttu-id="24df6-122">sp_helpsql</span><span class="sxs-lookup"><span data-stu-id="24df6-122">sp_helpsql</span></span>  
  
-   <span data-ttu-id="24df6-123">sp_IsMBCSLeadByte</span><span class="sxs-lookup"><span data-stu-id="24df6-123">sp_IsMBCSLeadByte</span></span>  
  
-   <span data-ttu-id="24df6-124">sp_lock2</span><span class="sxs-lookup"><span data-stu-id="24df6-124">sp_lock2</span></span>  
  
-   <span data-ttu-id="24df6-125">sp_MSget_current_activity</span><span class="sxs-lookup"><span data-stu-id="24df6-125">sp_MSget_current_activity</span></span>  
  
-   <span data-ttu-id="24df6-126">sp_MSset_current_activity</span><span class="sxs-lookup"><span data-stu-id="24df6-126">sp_MSset_current_activity</span></span>  
  
-   <span data-ttu-id="24df6-127">sp_MSobjessearch</span><span class="sxs-lookup"><span data-stu-id="24df6-127">sp_MSobjessearch</span></span>  
  
-   <span data-ttu-id="24df6-128">xp_enum_ActiveScriptEngines</span><span class="sxs-lookup"><span data-stu-id="24df6-128">xp_enum_ActiveScriptEngines</span></span>  
  
-   <span data-ttu-id="24df6-129">xp_eventlog</span><span class="sxs-lookup"><span data-stu-id="24df6-129">xp_eventlog</span></span>  
  
-   <span data-ttu-id="24df6-130">xp_GetAdminGroupName</span><span class="sxs-lookup"><span data-stu-id="24df6-130">xp_GetAdminGroupName</span></span>  
  
-   <span data-ttu-id="24df6-131">xp_GetFileDetails</span><span class="sxs-lookup"><span data-stu-id="24df6-131">xp_GetFileDetails</span></span>  
  
-   <span data-ttu-id="24df6-132">xp_GetLocalSystemAccountName</span><span class="sxs-lookup"><span data-stu-id="24df6-132">xp_GetLocalSystemAccountName</span></span>  
  
-   <span data-ttu-id="24df6-133">xp_IsNTAdmin</span><span class="sxs-lookup"><span data-stu-id="24df6-133">xp_IsNTAdmin</span></span>  
  
-   <span data-ttu-id="24df6-134">xp_MSLocalSystem</span><span class="sxs-lookup"><span data-stu-id="24df6-134">xp_MSLocalSystem</span></span>  
  
-   <span data-ttu-id="24df6-135">xp_MSnt2000</span><span class="sxs-lookup"><span data-stu-id="24df6-135">xp_MSnt2000</span></span>  
  
-   <span data-ttu-id="24df6-136">xp_MSplatform</span><span class="sxs-lookup"><span data-stu-id="24df6-136">xp_MSplatform</span></span>  
  
-   <span data-ttu-id="24df6-137">xp_SetSecurity</span><span class="sxs-lookup"><span data-stu-id="24df6-137">xp_SetSecurity</span></span>  
  
-   <span data-ttu-id="24df6-138">xp_varbintohexstr</span><span class="sxs-lookup"><span data-stu-id="24df6-138">xp_varbintohexstr</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="24df6-139">纠正措施</span><span class="sxs-lookup"><span data-stu-id="24df6-139">Corrective Action</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="24df6-140">已记录的系统存储过程</span><span class="sxs-lookup"><span data-stu-id="24df6-140">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="24df6-141">按照下表修改应用程序。</span><span class="sxs-lookup"><span data-stu-id="24df6-141">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="24df6-142">不再使用</span><span class="sxs-lookup"><span data-stu-id="24df6-142">Instead of</span></span>|<span data-ttu-id="24df6-143">操作</span><span class="sxs-lookup"><span data-stu-id="24df6-143">Do this</span></span>|  
|----------------|-------------|  
|<span data-ttu-id="24df6-144">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="24df6-144">sp_addalias</span></span>|<span data-ttu-id="24df6-145">请将别名替换为用户帐户和数据库角色的组合。</span><span class="sxs-lookup"><span data-stu-id="24df6-145">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="24df6-146">有关详细信息，请参阅 SQL Server 联机丛书中的“CREATE USER (Transact-SQL)”和“CREATE ROLE (Transact-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="24df6-146">For more information, see "CREATE USER (Transact-SQL)" and "CREATE ROLE (Transact-SQL)" in SQL Server Books Online.</span></span> <span data-ttu-id="24df6-147">使用 sp_dropalias 删除已升级数据库中的别名。</span><span class="sxs-lookup"><span data-stu-id="24df6-147">Remove aliases in upgraded databases by using sp_dropalias.</span></span>|  
|<span data-ttu-id="24df6-148">sp_addgroupsp_changegroup</span><span class="sxs-lookup"><span data-stu-id="24df6-148">sp_addgroupsp_changegroup</span></span><br /><br /> <span data-ttu-id="24df6-149">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="24df6-149">sp_dropgroup</span></span><br /><br /> <span data-ttu-id="24df6-150">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="24df6-150">sp_helpgroup</span></span>|<span data-ttu-id="24df6-151">使用角色。</span><span class="sxs-lookup"><span data-stu-id="24df6-151">Use roles.</span></span> <span data-ttu-id="24df6-152">有关详细信息，请参阅 SQL Server 联机丛书中的“服务器级别角色”和“数据库级别角色”。</span><span class="sxs-lookup"><span data-stu-id="24df6-152">For more information, see "Server-Level Roles" and "Database-Level Roles" in SQL Server Books Online.</span></span>|  
  
### <a name="undocmented-system-stored-procedures"></a><span data-ttu-id="24df6-153">Undocmented 系统存储过程</span><span class="sxs-lookup"><span data-stu-id="24df6-153">Undocmented System Stored Procedures</span></span>  
 <span data-ttu-id="24df6-154">可创建具有等效功能的 CLR 存储过程来替换未记录的系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="24df6-154">You can create CLR stored procedures with equivalent functionality to replace the undocumented system stored procedures.</span></span> <span data-ttu-id="24df6-155">有关详细信息，请参阅 SQL Server 联机丛书中的“CLR 存储过程”。</span><span class="sxs-lookup"><span data-stu-id="24df6-155">For more information, see the topic "CLR Stored Procedures" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24df6-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24df6-156">See Also</span></span>  
 <span data-ttu-id="24df6-157">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="24df6-157">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="24df6-158">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="24df6-158">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
