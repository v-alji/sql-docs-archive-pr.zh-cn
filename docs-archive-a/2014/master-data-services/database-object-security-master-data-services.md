---
title: 数据库对象安全性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682922"
---
# <a name="database-object-security-master-data-services"></a><span data-ttu-id="70ad7-102">数据库对象安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="70ad7-102">Database Object Security (Master Data Services)</span></span>
  <span data-ttu-id="70ad7-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中，数据存储在多个数据库表中并可以通过视图查看。</span><span class="sxs-lookup"><span data-stu-id="70ad7-103">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, data is stored in multiple database tables and is visible in views.</span></span> <span data-ttu-id="70ad7-104">您在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中受保护的信息对于具有 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库访问权限的用户是可见的。</span><span class="sxs-lookup"><span data-stu-id="70ad7-104">Information that you might have secured in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="70ad7-105">例如，雇员薪金信息可能包含在 Employee 模型中，或公司财务信息可能包含在 Account 模型中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-105">Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model.</span></span> <span data-ttu-id="70ad7-106">您可以拒绝用户在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户界面中访问这些模型，但是具有数据库访问权限的用户可以查看此数据。</span><span class="sxs-lookup"><span data-stu-id="70ad7-106">You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface, but users with access to the database can view this data.</span></span>  
  
 <span data-ttu-id="70ad7-107">您可以授予对数据库对象的权限以使特定数据对用户可用。</span><span class="sxs-lookup"><span data-stu-id="70ad7-107">You can grant permissions to database objects to make specific data available to users.</span></span> <span data-ttu-id="70ad7-108">有关授予权限的详细信息，请参阅 [GRANT 对象权限 (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-108">For more information on granting permissions, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span> <span data-ttu-id="70ad7-109">有关保护 SQL Server 的详细信息，请参阅 [Securing SQL Server](../relational-databases/security/securing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-109">For more information about securing SQL server, see [Securing SQL Server](../relational-databases/security/securing-sql-server.md).</span></span>  
  
 <span data-ttu-id="70ad7-110">以下任务需要访问 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库：</span><span class="sxs-lookup"><span data-stu-id="70ad7-110">The following tasks require access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   [<span data-ttu-id="70ad7-111">暂存数据</span><span class="sxs-lookup"><span data-stu-id="70ad7-111">Staging Data</span></span>](#Staging)  
  
-   [<span data-ttu-id="70ad7-112">根据业务规则验证数据</span><span class="sxs-lookup"><span data-stu-id="70ad7-112">Validating Data Against Business Rules</span></span>](#rules)  
  
-   [<span data-ttu-id="70ad7-113">删除版本</span><span class="sxs-lookup"><span data-stu-id="70ad7-113">Deleting Versions</span></span>](#Versions)  
  
-   [<span data-ttu-id="70ad7-114">立即应用层次结构成员权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-114">Immediately Applying Hierarchy Member Permissions</span></span>](#Hierarchy)  
  
-   [<span data-ttu-id="70ad7-115">更改系统管理员帐户</span><span class="sxs-lookup"><span data-stu-id="70ad7-115">Changing the System Administrator Account</span></span>](#SysAdmin)  
  
-   [<span data-ttu-id="70ad7-116">配置系统设置</span><span class="sxs-lookup"><span data-stu-id="70ad7-116">Configuring System Settings</span></span>](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> <span data-ttu-id="70ad7-117">临时处理数据</span><span class="sxs-lookup"><span data-stu-id="70ad7-117">Staging Data</span></span>  
 <span data-ttu-id="70ad7-118">在下表中，每个安全对象都将“name”作为名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="70ad7-118">In the following table, each securable has "name" as part of the name.</span></span> <span data-ttu-id="70ad7-119">这指示在创建实体时指定的临时表的名称。</span><span class="sxs-lookup"><span data-stu-id="70ad7-119">This indicates the name of the staging table that is specified when an entity is created.</span></span> <span data-ttu-id="70ad7-120">有关详细信息，请参阅[数据导入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="70ad7-120">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span></span>  
  
|<span data-ttu-id="70ad7-121">操作</span><span class="sxs-lookup"><span data-stu-id="70ad7-121">Action</span></span>|<span data-ttu-id="70ad7-122">安全对象</span><span class="sxs-lookup"><span data-stu-id="70ad7-122">Securables</span></span>|<span data-ttu-id="70ad7-123">权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-123">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="70ad7-124">将叶成员及其属性加载到临时表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-124">Load leaf members and their attributes into the staging table.</span></span>|<span data-ttu-id="70ad7-125">stg.name_Leaf</span><span class="sxs-lookup"><span data-stu-id="70ad7-125">stg.name_Leaf</span></span>|<span data-ttu-id="70ad7-126">必需：INSERT</span><span class="sxs-lookup"><span data-stu-id="70ad7-126">Required: INSERT</span></span><br /><br /> <span data-ttu-id="70ad7-127">可选：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="70ad7-127">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="70ad7-128">将数据从叶临时表加载到相应的 MDS 数据库表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-128">Load the data from the Leaf staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="70ad7-129">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="70ad7-129">stg.udp_name_Leaf</span></span>|<span data-ttu-id="70ad7-130">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-130">EXECUTE</span></span>|  
|<span data-ttu-id="70ad7-131">将合并成员及其属性加载到临时表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-131">Load consolidated members and their attributes into the staging table.</span></span>|<span data-ttu-id="70ad7-132">stg.name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="70ad7-132">stg.name_Consolidated</span></span>|<span data-ttu-id="70ad7-133">必需：INSERT</span><span class="sxs-lookup"><span data-stu-id="70ad7-133">Required: INSERT</span></span><br /><br /> <span data-ttu-id="70ad7-134">可选：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="70ad7-134">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="70ad7-135">将数据从合并临时表加载到相应的 MDS 数据库表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-135">Load the data from the Consolidated staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="70ad7-136">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="70ad7-136">stg.udp_name_Consolidated</span></span>|<span data-ttu-id="70ad7-137">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-137">EXECUTE</span></span>|  
|<span data-ttu-id="70ad7-138">在显式层次结构中将叶成员和合并成员的关系加载到临时表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-138">Load leaf and consolidated members' relationships to each other in an explicit hierarchy into the staging table.</span></span>|<span data-ttu-id="70ad7-139">stg.name_Relationship</span><span class="sxs-lookup"><span data-stu-id="70ad7-139">stg.name_Relationship</span></span>|<span data-ttu-id="70ad7-140">必需：INSERT</span><span class="sxs-lookup"><span data-stu-id="70ad7-140">Required: INSERT</span></span><br /><br /> <span data-ttu-id="70ad7-141">可选：SELECT 和 UPDATE</span><span class="sxs-lookup"><span data-stu-id="70ad7-141">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="70ad7-142">将数据从关系临时表加载到相应的 MDS 表中。</span><span class="sxs-lookup"><span data-stu-id="70ad7-142">Load the data from the Relationship staging table into the appropriate MDS tables.</span></span>|<span data-ttu-id="70ad7-143">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="70ad7-143">stg.udp_name_Relationship</span></span>|<span data-ttu-id="70ad7-144">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-144">EXECUTE</span></span>|  
|<span data-ttu-id="70ad7-145">查看在数据从临时表插入到 MDS 数据库表时发生的错误。</span><span class="sxs-lookup"><span data-stu-id="70ad7-145">View errors that occurred when data from the staging tables was being inserted into the MDS database tables.</span></span>|<span data-ttu-id="70ad7-146">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="70ad7-146">stg.udp_name_Relationship</span></span>|<span data-ttu-id="70ad7-147">SELECT</span><span class="sxs-lookup"><span data-stu-id="70ad7-147">SELECT</span></span>|  
  
 <span data-ttu-id="70ad7-148">有关详细信息，请参阅[数据导入 (Master Data Services)](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-148">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a> <span data-ttu-id="70ad7-149">根据业务规则对数据进行验证</span><span class="sxs-lookup"><span data-stu-id="70ad7-149">Validating Data Against Business Rules</span></span>  
  
|<span data-ttu-id="70ad7-150">操作</span><span class="sxs-lookup"><span data-stu-id="70ad7-150">Action</span></span>|<span data-ttu-id="70ad7-151">安全对象</span><span class="sxs-lookup"><span data-stu-id="70ad7-151">Securable</span></span>|<span data-ttu-id="70ad7-152">权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-152">Permissions</span></span>|  
|------------|---------------|-----------------|  
|<span data-ttu-id="70ad7-153">根据业务规则验证数据版本</span><span class="sxs-lookup"><span data-stu-id="70ad7-153">Validate a version of data against business rules</span></span>|<span data-ttu-id="70ad7-154">mdm.udpValidateModel</span><span class="sxs-lookup"><span data-stu-id="70ad7-154">mdm.udpValidateModel</span></span>|<span data-ttu-id="70ad7-155">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-155">EXECUTE</span></span>|  
  
 <span data-ttu-id="70ad7-156">有关详细信息，请参阅 [验证存储过程 (Master Data Services)](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-156">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).</span></span>  
  
##  <a name="deleting-versions"></a><a name="Versions"></a> <span data-ttu-id="70ad7-157">删除版本</span><span class="sxs-lookup"><span data-stu-id="70ad7-157">Deleting Versions</span></span>  
  
|<span data-ttu-id="70ad7-158">操作</span><span class="sxs-lookup"><span data-stu-id="70ad7-158">Action</span></span>|<span data-ttu-id="70ad7-159">安全对象</span><span class="sxs-lookup"><span data-stu-id="70ad7-159">Securables</span></span>|<span data-ttu-id="70ad7-160">权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-160">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="70ad7-161">确定要删除的版本的 ID</span><span class="sxs-lookup"><span data-stu-id="70ad7-161">Determine the ID of the version you want to delete</span></span>|<span data-ttu-id="70ad7-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span><span class="sxs-lookup"><span data-stu-id="70ad7-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span></span>|<span data-ttu-id="70ad7-163">SELECT</span><span class="sxs-lookup"><span data-stu-id="70ad7-163">SELECT</span></span>|  
|<span data-ttu-id="70ad7-164">删除模型的版本</span><span class="sxs-lookup"><span data-stu-id="70ad7-164">Delete a version of a model</span></span>|<span data-ttu-id="70ad7-165">mdm.udpVersionDelete</span><span class="sxs-lookup"><span data-stu-id="70ad7-165">mdm.udpVersionDelete</span></span>|<span data-ttu-id="70ad7-166">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-166">EXECUTE</span></span>|  
  
 <span data-ttu-id="70ad7-167">有关详细信息，请参阅[删除版本 (Master Data Services)](../../2014/master-data-services/delete-a-version-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-167">For more information, see [Delete a Version &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).</span></span>  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a><span data-ttu-id="70ad7-168">立即应用层次结构成员权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-168">Immediately Applying Hierarchy Member Permissions</span></span>  
  
|<span data-ttu-id="70ad7-169">操作</span><span class="sxs-lookup"><span data-stu-id="70ad7-169">Action</span></span>|<span data-ttu-id="70ad7-170">安全对象</span><span class="sxs-lookup"><span data-stu-id="70ad7-170">Securables</span></span>|<span data-ttu-id="70ad7-171">权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-171">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="70ad7-172">立即应用成员权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-172">Immediately apply member permissions</span></span>|<span data-ttu-id="70ad7-173">mdm.udpSecurityMemberProcessRebuildModel</span><span class="sxs-lookup"><span data-stu-id="70ad7-173">mdm.udpSecurityMemberProcessRebuildModel</span></span>|<span data-ttu-id="70ad7-174">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-174">EXECUTE</span></span>|  
  
 <span data-ttu-id="70ad7-175">有关详细信息，请参阅[立即应用成员权限 (Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-175">For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a><span data-ttu-id="70ad7-176">更改系统管理员帐户</span><span class="sxs-lookup"><span data-stu-id="70ad7-176">Changing the System Administrator Account</span></span>  
  
|<span data-ttu-id="70ad7-177">操作</span><span class="sxs-lookup"><span data-stu-id="70ad7-177">Action</span></span>|<span data-ttu-id="70ad7-178">安全对象</span><span class="sxs-lookup"><span data-stu-id="70ad7-178">Securables</span></span>|<span data-ttu-id="70ad7-179">权限</span><span class="sxs-lookup"><span data-stu-id="70ad7-179">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="70ad7-180">确定新管理员的 SID</span><span class="sxs-lookup"><span data-stu-id="70ad7-180">Determine the SID of the new administrator</span></span>|<span data-ttu-id="70ad7-181">mdm.tblUser</span><span class="sxs-lookup"><span data-stu-id="70ad7-181">mdm.tblUser</span></span>|<span data-ttu-id="70ad7-182">SELECT</span><span class="sxs-lookup"><span data-stu-id="70ad7-182">SELECT</span></span>|  
|<span data-ttu-id="70ad7-183">更改系统管理员帐户</span><span class="sxs-lookup"><span data-stu-id="70ad7-183">Change the system administrator account</span></span>|<span data-ttu-id="70ad7-184">udpSecuritySetAdministrator</span><span class="sxs-lookup"><span data-stu-id="70ad7-184">mdm.udpSecuritySetAdministrator</span></span>|<span data-ttu-id="70ad7-185">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="70ad7-185">EXECUTE</span></span>|  
  
 <span data-ttu-id="70ad7-186">有关详细信息，请参阅[&#40;Master Data Services&#41;更改系统管理员帐户](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-186">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a><span data-ttu-id="70ad7-187">配置系统设置</span><span class="sxs-lookup"><span data-stu-id="70ad7-187">Configuring System Settings</span></span>  
 <span data-ttu-id="70ad7-188">可以配置系统设置来控制 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中的行为。</span><span class="sxs-lookup"><span data-stu-id="70ad7-188">There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="70ad7-189">可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中调整这些设置，或者如果具有 UPDATE 访问权限，可以直接在 mdm.tblSystemSetting 数据库表中调整这些设置。</span><span class="sxs-lookup"><span data-stu-id="70ad7-189">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table.</span></span> <span data-ttu-id="70ad7-190">有关详细信息，请参阅[系统设置 (Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="70ad7-190">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ad7-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70ad7-191">See Also</span></span>  
 [<span data-ttu-id="70ad7-192">安全性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="70ad7-192">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
