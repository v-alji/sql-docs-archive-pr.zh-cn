---
title: 分类的 Web 服务操作 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e3f346b5-7e26-481d-9821-1846e2e91289
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f7dd682f55c16c6dcbff9f0f669593a10486da6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589195"
---
# <a name="categorized-web-service-operations-master-data-services"></a><span data-ttu-id="539da-102">分类的 Web 服务操作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="539da-102">Categorized Web Service Operations (Master Data Services)</span></span>
  <span data-ttu-id="539da-103"> Web 服务包含一组完整的操作，可让您通过编写代码以控制  通过其用户界面所执行的所有功能。</span><span class="sxs-lookup"><span data-stu-id="539da-103">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service contains a complete set of operations that let you write code to control all of the features that [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] does through its user interface.</span></span> <span data-ttu-id="539da-104">Web 服务操作由 <xref:Microsoft.MasterDataServices.IService> 接口定义，并在 <xref:Microsoft.MasterDataServices.ServiceClient> 类中作为方法实现。</span><span class="sxs-lookup"><span data-stu-id="539da-104">The web service operations are defined by the <xref:Microsoft.MasterDataServices.IService> interface and are implemented as methods in the <xref:Microsoft.MasterDataServices.ServiceClient> class.</span></span> <span data-ttu-id="539da-105">本主题将 Web 服务操作分组为概念性类别，以帮助您了解如何使用 Web 服务 API。</span><span class="sxs-lookup"><span data-stu-id="539da-105">This topic groups the web service operations into conceptual categories to help you understand how to use the web service API.</span></span>  
  
## <a name="model-operations"></a><span data-ttu-id="539da-106">模型操作</span><span class="sxs-lookup"><span data-stu-id="539da-106">Model Operations</span></span>  
 <span data-ttu-id="539da-107">这些操作用于创建、更新和删除模型，以及对所有模型内容（如实体、层次结构和版本）执行操作。</span><span class="sxs-lookup"><span data-stu-id="539da-107">These operations are used to create, update, and delete models, as well as to operate on all the contents of a model, such as entities, hierarchies, and versions.</span></span> <span data-ttu-id="539da-108">有关详细信息，请参阅[模型 (Master Data Services)](../models-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-108">For more information, see [Models &#40;Master Data Services&#41;](../models-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>|  
  
## <a name="entity-operations"></a><span data-ttu-id="539da-109">实体操作</span><span class="sxs-lookup"><span data-stu-id="539da-109">Entity Operations</span></span>  
 <span data-ttu-id="539da-110">这些操作用于创建、更新和删除单个实体的成员。</span><span class="sxs-lookup"><span data-stu-id="539da-110">These operations are used to create, update, and delete the members of a single entity.</span></span> <span data-ttu-id="539da-111">有关详细信息，请参阅[实体 &#40;Master Data Services&#41;](../entities-master-data-services.md) 和[成员 &#40;Master Data Services&#41;](../members-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-111">For more information, see [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md) and [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberKeyLookup%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersUpdate%2A>|  
  
## <a name="member-operations"></a><span data-ttu-id="539da-112">成员操作</span><span class="sxs-lookup"><span data-stu-id="539da-112">Member Operations</span></span>  
 <span data-ttu-id="539da-113">这些操作用于获取、更新和删除成员。</span><span class="sxs-lookup"><span data-stu-id="539da-113">These operations are used to get, update, and delete members.</span></span> <span data-ttu-id="539da-114">这组操作的成员可能包含多个实体中的成员。</span><span class="sxs-lookup"><span data-stu-id="539da-114">The set of members operated on can contain members from multiple entities.</span></span> <span data-ttu-id="539da-115">有关详细信息，请参阅[成员 (Master Data Services)](../members-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-115">For more information, see [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersGet%2A>|  
  
## <a name="attribute-and-hierarchy-operations"></a><span data-ttu-id="539da-116">属性和层次结构操作</span><span class="sxs-lookup"><span data-stu-id="539da-116">Attribute and Hierarchy Operations</span></span>  
 <span data-ttu-id="539da-117">这些操作用于获取属性和层次结构信息。</span><span class="sxs-lookup"><span data-stu-id="539da-117">These operations are used to get attribute and hierarchy information.</span></span> <span data-ttu-id="539da-118">还可通过使用模型操作来修改属性和层次结构，如 <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>。</span><span class="sxs-lookup"><span data-stu-id="539da-118">Attributes and hierarchies can also be modified by using the model operations, such as <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>.</span></span> <span data-ttu-id="539da-119">有关详细信息，请参阅[属性 &#40;Master Data Services&#41;](../attributes-master-data-services.md) 和[层次结构 &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-119">For more information, see [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) and [Hierarchies &#40;Master Data Services&#41;](../hierarchies-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAttributesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.HierarchyMembersGet%2A>|  
  
## <a name="business-rule-operations"></a><span data-ttu-id="539da-120">业务规则操作</span><span class="sxs-lookup"><span data-stu-id="539da-120">Business Rule Operations</span></span>  
 <span data-ttu-id="539da-121">这些操作用于创建、更新、删除和发布业务规则。</span><span class="sxs-lookup"><span data-stu-id="539da-121">These operations are used to create, update, delete, and publish business rules.</span></span> <span data-ttu-id="539da-122">有关详细信息，请参阅[业务规则 (Master Data Services)](../business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-122">For more information, see [Business Rules &#40;Master Data Services&#41;](../business-rules-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPaletteGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPublish%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesUpdate%2A>|  
  
## <a name="annotation-operations"></a><span data-ttu-id="539da-123">批注操作</span><span class="sxs-lookup"><span data-stu-id="539da-123">Annotation Operations</span></span>  
 <span data-ttu-id="539da-124">这些操作用于创建、更新和删除批注。</span><span class="sxs-lookup"><span data-stu-id="539da-124">These operations are used to create, update, and delete annotations.</span></span> <span data-ttu-id="539da-125">有关详细信息，请参阅[批注 &#40;Master Data Services&#41;](../annotations-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-125">For more information, see [Annotations &#40;Master Data Services&#41;](../annotations-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsGet%2A>|  
  
## <a name="transaction-operations"></a><span data-ttu-id="539da-126">事务操作</span><span class="sxs-lookup"><span data-stu-id="539da-126">Transaction Operations</span></span>  
 <span data-ttu-id="539da-127">这些操作用于获取和撤消事务。</span><span class="sxs-lookup"><span data-stu-id="539da-127">These operations are used to get and reverse transactions.</span></span> <span data-ttu-id="539da-128">有关详细信息，请参阅[事务 (Master Data Services)](../transactions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-128">For more information, see [Transactions &#40;Master Data Services&#41;](../transactions-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsReverse%2A>|  
  
## <a name="version-and-validation-operations"></a><span data-ttu-id="539da-129">版本和验证操作</span><span class="sxs-lookup"><span data-stu-id="539da-129">Version and Validation Operations</span></span>  
 <span data-ttu-id="539da-130">这些操作用来复制和验证版本。</span><span class="sxs-lookup"><span data-stu-id="539da-130">These operations are used to copy and validate versions.</span></span> <span data-ttu-id="539da-131">有关详细信息，请参阅[版本 &#40;Master Data Services&#41;](../versions-master-data-services.md) 和[验证 &#40;Master Data Services&#41;](../validation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-131">For more information, see [Versions &#40;Master Data Services&#41;](../versions-master-data-services.md) and [Validation &#40;Master Data Services&#41;](../validation-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.VersionCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationProcess%2A>|  
  
## <a name="data-quality-operations"></a><span data-ttu-id="539da-132">数据质量操作</span><span class="sxs-lookup"><span data-stu-id="539da-132">Data Quality Operations</span></span>  
 <span data-ttu-id="539da-133">这些操作用于执行数据质量任务并检查其结果。</span><span class="sxs-lookup"><span data-stu-id="539da-133">These operations are used to perform data quality tasks and to examine their results.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityCleansingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityMatchingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStart%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityInstalledState%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityKnowledgeBasesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationResultsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStatus%2A>|  
  
## <a name="data-import-operations"></a><span data-ttu-id="539da-134">数据导入操作</span><span class="sxs-lookup"><span data-stu-id="539da-134">Data Import Operations</span></span>  
 <span data-ttu-id="539da-135">这些操作用于将数据导入到 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="539da-135">These operations are used to import data into a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="539da-136">有关详细信息，请参阅[数据导入 (Master Data Services)](../overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-136">For more information, see [Data Import &#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingLoad%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingProcess%2A>|  
  
 <span data-ttu-id="539da-137">以下操作用于通过使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中所包含的临时过程导入数据。</span><span class="sxs-lookup"><span data-stu-id="539da-137">The following operations are used to import data by using the staging process included in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="539da-138">这些操作应仅用于支持现有数据库。</span><span class="sxs-lookup"><span data-stu-id="539da-138">These operations should be used only to support existing databases.</span></span> <span data-ttu-id="539da-139">对于新的开发工作，请使用前面列出的操作。</span><span class="sxs-lookup"><span data-stu-id="539da-139">For new development, use the previously listed operations.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingNameCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingProcess%2A>|  
  
## <a name="data-export-operations"></a><span data-ttu-id="539da-140">数据导出操作</span><span class="sxs-lookup"><span data-stu-id="539da-140">Data Export Operations</span></span>  
 <span data-ttu-id="539da-141">这些操作可用于通过使用订阅视图导出数据。</span><span class="sxs-lookup"><span data-stu-id="539da-141">These operations are used to export data through the use of subscription views.</span></span> <span data-ttu-id="539da-142">有关详细信息，请参阅将[数据导出 &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="539da-142">For more information, see [Exporting Data &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewUpdate%2A>|  
  
## <a name="security-operations"></a><span data-ttu-id="539da-143">安全运营</span><span class="sxs-lookup"><span data-stu-id="539da-143">Security Operations</span></span>  
 <span data-ttu-id="539da-144">这些操作用于修改控制对 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库进行访问的安全设置。</span><span class="sxs-lookup"><span data-stu-id="539da-144">These operations are used to modify the security settings that control access to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="539da-145">有关详细信息，请参阅[安全性 (Master Data Services)](../security-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="539da-145">For more information, see [Security &#40;Master Data Services&#41;](../security-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesUpdate%2A>|  
  
## <a name="system-operations"></a><span data-ttu-id="539da-146">系统操作</span><span class="sxs-lookup"><span data-stu-id="539da-146">System Operations</span></span>  
 <span data-ttu-id="539da-147">这些操作用于获取和更新系统设置和用户首选项。</span><span class="sxs-lookup"><span data-stu-id="539da-147">These operations are used to get and update system settings and user preferences.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceVersionGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemDomainListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemPropertiesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesUpdate%2A>|  
  
  
