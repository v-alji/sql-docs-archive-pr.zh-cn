---
title: 数据导入 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 403eca212611397fb3ba30f8fe12a2aa8b5e83ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577747"
---
# <a name="data-import-master-data-services"></a><span data-ttu-id="daf74-102">数据导入 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-102">Data Import (Master Data Services)</span></span>
  <span data-ttu-id="daf74-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中为数据创建模型后，你可以开始添加数据并在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中对数据进行更改。</span><span class="sxs-lookup"><span data-stu-id="daf74-103">Once you've created a model for your data in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can start adding data and make changes to data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>   <span data-ttu-id="daf74-104">你使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 临时表、存储过程和主数据管理器。</span><span class="sxs-lookup"><span data-stu-id="daf74-104">You use [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] staging tables, stored procedures and Master Data Manager .</span></span>

 <span data-ttu-id="daf74-105">你还可以使用将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 数据添加到 MDS 存储库 ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库) 。</span><span class="sxs-lookup"><span data-stu-id="daf74-105">You can also use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], to add data to the MDS repository ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database).</span></span> <span data-ttu-id="daf74-106">有关详细信息，请参阅[发布数据 &#40;MDS Add-in for Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="daf74-106">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>

 <span data-ttu-id="daf74-107">在添加和更新数据时，你可以执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="daf74-107">When you add and update data, you can do the following.</span></span>

-   <span data-ttu-id="daf74-108">加载和更新成员，并更新属性值</span><span class="sxs-lookup"><span data-stu-id="daf74-108">Load and update members, and update attribute values</span></span>

-   <span data-ttu-id="daf74-109">停用和删除成员</span><span class="sxs-lookup"><span data-stu-id="daf74-109">Deactivate and delete members</span></span>

-   <span data-ttu-id="daf74-110">移动显式层次结构成员</span><span class="sxs-lookup"><span data-stu-id="daf74-110">Move explicit hierarchy members</span></span>

 <span data-ttu-id="daf74-111">添加和更新数据包括以下主要任务。</span><span class="sxs-lookup"><span data-stu-id="daf74-111">Adding and updating data  includes the following main tasks.</span></span>

1.  <span data-ttu-id="daf74-112">将数据加载到 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中的临时表中。</span><span class="sxs-lookup"><span data-stu-id="daf74-112">Load data into the staging tables in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>

2.  <span data-ttu-id="daf74-113">将数据从临时表加载到相应的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="daf74-113">Load the data from the staging tables into the appropriate [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tables.</span></span>

     <span data-ttu-id="daf74-114">你使用临时存储过程或 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 来加载数据。</span><span class="sxs-lookup"><span data-stu-id="daf74-114">You use staging stored procedures or [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to load the data.</span></span>

> [!NOTE]
>  <span data-ttu-id="daf74-115">在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]中，已停止提供对 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 临时过程的支持。</span><span class="sxs-lookup"><span data-stu-id="daf74-115">In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], support for the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging processes is deprecated.</span></span>

## <a name="deactivating-and-deleting-members"></a><span data-ttu-id="daf74-116">停用和删除成员</span><span class="sxs-lookup"><span data-stu-id="daf74-116">Deactivating and Deleting Members</span></span>
 <span data-ttu-id="daf74-117">停用意味着可以重新激活成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-117">Deactivating means the member can be reactivated.</span></span> <span data-ttu-id="daf74-118">如果您重新激活某成员，可还原成员的属性以及成员在层次结构和集合中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="daf74-118">If you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span> <span data-ttu-id="daf74-119">以前的所有事务都将保持不变。</span><span class="sxs-lookup"><span data-stu-id="daf74-119">All previous transactions are intact.</span></span> <span data-ttu-id="daf74-120">管理员可以在主数据管理器的“版本管理” \*\*\*\* 功能区域中查看停用事务。</span><span class="sxs-lookup"><span data-stu-id="daf74-120">Deactivation transactions are visible to administrators in the **Version Management** functional area of the Master Data Manager.</span></span>

 <span data-ttu-id="daf74-121">删除意味着从系统中永久清除成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-121">Deleting means purging the member from the system permanently.</span></span> <span data-ttu-id="daf74-122">将永久删除该成员的所有事务、所有关系和所有属性。</span><span class="sxs-lookup"><span data-stu-id="daf74-122">All transactions for the member, all relationships, and all attributes are permanently deleted.</span></span>

> [!NOTE]
>  <span data-ttu-id="daf74-123">不能使用临时过程来重新激活成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-123">You cannot use staging to reactivate members.</span></span> <span data-ttu-id="daf74-124">你必须在主数据管理器中手动执行此操作。</span><span class="sxs-lookup"><span data-stu-id="daf74-124">You must do it manually in the Master Data Manager.</span></span> <span data-ttu-id="daf74-125">有关详细信息，请参阅[重新激活成员或集合 (Master Data Services)](reactivate-a-member-or-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="daf74-125">For more information, see [Reactivate a Member or Collection &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md).</span></span>
> 
>  <span data-ttu-id="daf74-126">不能使用临时过程来删除或停用集合。</span><span class="sxs-lookup"><span data-stu-id="daf74-126">You cannot use staging to delete or deactivate collections.</span></span> <span data-ttu-id="daf74-127">有关手动停用集合的详细信息，请参阅[删除成员或集合 (Master Data Services)](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="daf74-127">For more information on manually deactivating collections, see [Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).</span></span>

## <a name="moving-explicit-hierarchy-members"></a><span data-ttu-id="daf74-128">移动显式层次结构成员</span><span class="sxs-lookup"><span data-stu-id="daf74-128">Moving explicit hierarchy members</span></span>
 <span data-ttu-id="daf74-129">当你批量移动成员在显式层次结构中的位置时，你可以指定以下内容。</span><span class="sxs-lookup"><span data-stu-id="daf74-129">When you move the location of members in explicit hierarchies in bulk, you can designate the following.</span></span>

-   <span data-ttu-id="daf74-130">作为合并成员的父级的合并成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-130">A consolidated member as a parent of a consolidated member.</span></span>

-   <span data-ttu-id="daf74-131">作为叶成员的父级的合并成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-131">A consolidated member as a parent of a leaf member.</span></span>

-   <span data-ttu-id="daf74-132">作为叶成员或合并成员的同级的叶成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-132">A leaf member as a sibling of a leaf or consolidated member.</span></span>

-   <span data-ttu-id="daf74-133">作为叶成员或合并成员的同级的合并成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-133">A consolidated member as a sibling of a leaf or consolidated member.</span></span>

## <a name="staging-tables-and-stored-procedures"></a><span data-ttu-id="daf74-134">临时表和存储过程</span><span class="sxs-lookup"><span data-stu-id="daf74-134">Staging Tables and Stored Procedures</span></span>
 <span data-ttu-id="daf74-135">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库包含以下类型的临时表，你可以使用你的数据填充它们。</span><span class="sxs-lookup"><span data-stu-id="daf74-135">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database includes the following types of staging tables that you can populate with your  data.</span></span>

-   [<span data-ttu-id="daf74-136">叶成员临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-136">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="daf74-137">合并成员临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-137">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [<span data-ttu-id="daf74-138">关系临时表 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-138">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 <span data-ttu-id="daf74-139">模型中的每个实体都有一个临时表。</span><span class="sxs-lookup"><span data-stu-id="daf74-139">For each entity in the model, there is a staging table.</span></span> <span data-ttu-id="daf74-140">表名称指示相应的实体以及实体类型，如叶成员。</span><span class="sxs-lookup"><span data-stu-id="daf74-140">The table name indicates the corresponding entity, and the entity type such as leaf member.</span></span> <span data-ttu-id="daf74-141">下图显示货币、客户和产品实体的临时表。</span><span class="sxs-lookup"><span data-stu-id="daf74-141">The following image shows the staging tables for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="daf74-142">![MDS 数据库中的临时表](../../2014/master-data-services/media/mds-stagingtables.png "MDS 数据库中的临时表")</span><span class="sxs-lookup"><span data-stu-id="daf74-142">![Staging Tables in MDS database](../../2014/master-data-services/media/mds-stagingtables.png "Staging Tables in MDS database")</span></span>

 <span data-ttu-id="daf74-143">该表的名称在创建实体时指定，且不可更改。</span><span class="sxs-lookup"><span data-stu-id="daf74-143">The name of the  table is specified when an entity is created and cannot be changed.</span></span> <span data-ttu-id="daf74-144">如果临时表的名称包含 _1 或其他数字，则在创建实体时已存在带此名称的其他表。</span><span class="sxs-lookup"><span data-stu-id="daf74-144">If the staging table name contains a _1 or other number, another table of that name already existed when the entity was created.</span></span>

 <span data-ttu-id="daf74-145">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 包括以下类型的临时存储过程。</span><span class="sxs-lookup"><span data-stu-id="daf74-145">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] includes the following types of staging stored procedures.</span></span>

-   <span data-ttu-id="daf74-146">stg.<name _Leaf udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="daf74-146">stg.udp_\<name>_Leaf</span></span>

-   <span data-ttu-id="daf74-147">stg.<name _Consolidated udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="daf74-147">stg.udp_\<name>_Consolidated</span></span>

-   <span data-ttu-id="daf74-148">stg.<name _Relationship udp_ \<name></span><span class="sxs-lookup"><span data-stu-id="daf74-148">stg.udp_\<name>_Relationship</span></span>

 <span data-ttu-id="daf74-149">对于模型中的每个实体，有三个对应于叶成员、合并成员和关系临时表的存储过程。</span><span class="sxs-lookup"><span data-stu-id="daf74-149">For each entity in the model, there are three stored procedures that correspond to the leaf member, consolidated member, and relationship staging tables.</span></span>  <span data-ttu-id="daf74-150">下图显示货币、客户和产品实体的临时存储过程。</span><span class="sxs-lookup"><span data-stu-id="daf74-150">The following image shows the staging stored procedures for the currency, customer, and product entities.</span></span>

 <span data-ttu-id="daf74-151">![MDS 数据库中的临时存储过程](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "MDS 数据库中的临时存储过程")</span><span class="sxs-lookup"><span data-stu-id="daf74-151">![Staging Stored Procedures in MDS database](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Staging Stored Procedures in MDS database")</span></span>

 <span data-ttu-id="daf74-152">有关存储过程的详细信息，请参阅[临时存储过程 (Master Data Services)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="daf74-152">For more information on the stored procedures, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>

## <a name="logging-transactions"></a><span data-ttu-id="daf74-153">记录事务</span><span class="sxs-lookup"><span data-stu-id="daf74-153">Logging Transactions</span></span>
 <span data-ttu-id="daf74-154">导入或更新数据或关系时，可以记录发生的所有事务。</span><span class="sxs-lookup"><span data-stu-id="daf74-154">All transactions that occur when data or relationships are imported or updated can be logged.</span></span> <span data-ttu-id="daf74-155">存储过程中的选项允许进行此日志记录。</span><span class="sxs-lookup"><span data-stu-id="daf74-155">An option in the stored procedure allows this logging.</span></span> <span data-ttu-id="daf74-156">如果使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]启动临时过程，则不进行日志记录。</span><span class="sxs-lookup"><span data-stu-id="daf74-156">If you initiate the staging process using [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], no logging occurs.</span></span>

 <span data-ttu-id="daf74-157">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中， **“记录临时事务”** 设置不应用于暂存数据的此方法。</span><span class="sxs-lookup"><span data-stu-id="daf74-157">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], the **Log staging transactions** setting does not apply to this method of staging data.</span></span>

## <a name="related-content"></a><span data-ttu-id="daf74-158">相关内容</span><span class="sxs-lookup"><span data-stu-id="daf74-158">Related Content</span></span>

-   [<span data-ttu-id="daf74-159">验证 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-159">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)

-   [<span data-ttu-id="daf74-160">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="daf74-160">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)


