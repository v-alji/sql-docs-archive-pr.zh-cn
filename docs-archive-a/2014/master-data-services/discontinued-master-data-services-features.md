---
title: SQL Server 2014 中的废止 Master Data Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 595b8bf9829ee57ff0d3bee1a82e527876ecc4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591917"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="40c53-102">SQL Server 2014 中不再支持的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="40c53-102">Discontinued Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="40c53-103">此主题介绍 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中不再可用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="40c53-103">This topic describes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are no longer available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="40c53-104">废弃的功能</span><span class="sxs-lookup"><span data-stu-id="40c53-104">Discontinued Features</span></span>  
 <span data-ttu-id="40c53-105">此版本中没有废弃的功能。</span><span class="sxs-lookup"><span data-stu-id="40c53-105">There are no discontinued features in this release.</span></span>  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="40c53-106">废弃的功能</span><span class="sxs-lookup"><span data-stu-id="40c53-106">Discontinued Features</span></span>  
  
### <a name="security"></a><span data-ttu-id="40c53-107">安全性</span><span class="sxs-lookup"><span data-stu-id="40c53-107">Security</span></span>  
 <span data-ttu-id="40c53-108">为了简化安全权限的分配，您不能再向派生层次结构、显式层次结构和属性组等对象分配模型对象权限。</span><span class="sxs-lookup"><span data-stu-id="40c53-108">To make assigning security easier, you can no longer assign model object permissions to the Derived Hierarchy, Explicit Hierarchy, and Attribute Group objects.</span></span>  
  
-   <span data-ttu-id="40c53-109">派生层次结构权限现在基于模型。</span><span class="sxs-lookup"><span data-stu-id="40c53-109">Derived hierarchy permissions are now based on the model.</span></span> <span data-ttu-id="40c53-110">例如，如果希望用户对派生层次结构具有权限，则必须将**更新**分配给模型对象。</span><span class="sxs-lookup"><span data-stu-id="40c53-110">For example, if you want a user to have permission to a derived hierarchy, you must assign **Update** to the model object.</span></span> <span data-ttu-id="40c53-111">然后，可以将 "**拒绝**" 权限分配给不希望用户访问的任何实体。</span><span class="sxs-lookup"><span data-stu-id="40c53-111">Then you can assign **Deny** access to any entities you don't want the user to have access to.</span></span>  
  
-   <span data-ttu-id="40c53-112">显式层次结构权限现在基于实体。</span><span class="sxs-lookup"><span data-stu-id="40c53-112">Explicit hierarchy permissions are now based on the entity.</span></span> <span data-ttu-id="40c53-113">例如，如果用户对某个帐户实体具有 "**更新**" 权限，则该实体的所有显式层次结构都将可更新。</span><span class="sxs-lookup"><span data-stu-id="40c53-113">For example, if the user has **Update** permissions to an Account entity, then all explicit hierarchies for the entity will be updateable.</span></span>  
  
-   <span data-ttu-id="40c53-114">不能再在 "**用户和组权限**" 功能区域中分配属性组权限。</span><span class="sxs-lookup"><span data-stu-id="40c53-114">Attribute group permissions can no longer be assigned in the **User and Group Permissions** functional area.</span></span> <span data-ttu-id="40c53-115">相反，在创建属性组的 "**系统管理**" 功能区域中，可以为用户和组授予对属性组的 "**更新**" 权限。</span><span class="sxs-lookup"><span data-stu-id="40c53-115">Instead, in the **System Administration** functional area where attribute groups are created, users and groups can be given **Update** permission to attribute groups.</span></span> <span data-ttu-id="40c53-116">对属性组的**只读**权限不再可用。</span><span class="sxs-lookup"><span data-stu-id="40c53-116">**Read-only** permission to attribute groups is no longer available.</span></span>  
  
### <a name="staging-process"></a><span data-ttu-id="40c53-117">临时过程</span><span class="sxs-lookup"><span data-stu-id="40c53-117">Staging Process</span></span>  
 <span data-ttu-id="40c53-118">您不能使用新的临时过程来：</span><span class="sxs-lookup"><span data-stu-id="40c53-118">You cannot use the new staging process to:</span></span>  
  
-   <span data-ttu-id="40c53-119">创建或删除集合。</span><span class="sxs-lookup"><span data-stu-id="40c53-119">Create or delete collections.</span></span>  
  
-   <span data-ttu-id="40c53-120">在集合中添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="40c53-120">Add members to or remove members from collections.</span></span>  
  
-   <span data-ttu-id="40c53-121">重新激活成员和集合。</span><span class="sxs-lookup"><span data-stu-id="40c53-121">Reactivate members and collections.</span></span>  
  
 <span data-ttu-id="40c53-122">可以使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 临时过程来处理集合。</span><span class="sxs-lookup"><span data-stu-id="40c53-122">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process to work with collections.</span></span>  
  
### <a name="model-deployment-wizard"></a><span data-ttu-id="40c53-123">模型部署向导</span><span class="sxs-lookup"><span data-stu-id="40c53-123">Model Deployment Wizard</span></span>  
 <span data-ttu-id="40c53-124">不能再使用[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中的向导创建和部署包含数据的包。</span><span class="sxs-lookup"><span data-stu-id="40c53-124">Packages that contain data can no longer be created and deployed by using the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="40c53-125">可改为使用新的命令行实用程序。</span><span class="sxs-lookup"><span data-stu-id="40c53-125">A new command line utility can be used instead.</span></span> <span data-ttu-id="40c53-126">有关详细信息，请参阅[部署模型 (Master Data Services)](deploying-models-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40c53-126">For more information, see [Deploying Models &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span></span>  
  
 <span data-ttu-id="40c53-127">仍可以使用该向导来创建和部署不包含数据的包。</span><span class="sxs-lookup"><span data-stu-id="40c53-127">The wizard can still be used to create and deploy packages that do not contain data.</span></span>  
  
 <span data-ttu-id="40c53-128">此外，包只能部署到创建它们的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本中。</span><span class="sxs-lookup"><span data-stu-id="40c53-128">In addition, packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="40c53-129">这意味着在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中创建的包不能部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="40c53-129">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="40c53-130">您必须将包部署到 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 环境中，然后将数据库升级到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="40c53-130">You must deploy the package to a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] environment and then upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="code-generation-business-rules"></a><span data-ttu-id="40c53-131">代码生成业务规则</span><span class="sxs-lookup"><span data-stu-id="40c53-131">Code Generation Business Rules</span></span>  
 <span data-ttu-id="40c53-132">自动生成 Code 属性值的业务规则现在以不同的方式进行管理。</span><span class="sxs-lookup"><span data-stu-id="40c53-132">Business rules that automatically generate values for the Code attribute are now administered differently.</span></span> <span data-ttu-id="40c53-133">以前，若要为 Code 属性生成值，请在 "**业务规则**" 下的 "**系统管理**" 功能区域中将 "**默认属性" 设置为 "生成的值**" 操作。</span><span class="sxs-lookup"><span data-stu-id="40c53-133">Previously, to generate values for the Code attribute, you used the **Default attribute to a generated value** action in the **System Administration** functional area under **Business Rules**.</span></span> <span data-ttu-id="40c53-134">现在，在 "**系统管理**" 中，您必须编辑该实体以启用自动生成的代码值。</span><span class="sxs-lookup"><span data-stu-id="40c53-134">Now, in **System Administration**, you must edit the entity to enable automatically-generated Code values.</span></span> <span data-ttu-id="40c53-135">有关详细信息，请参阅[&#41;&#40;Master Data Services 自动创建代码](automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40c53-135">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span></span>  
  
 <span data-ttu-id="40c53-136">如果具有包含此类规则的 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 模型部署包，当您将数据库升级到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 时，将排除该业务规则。</span><span class="sxs-lookup"><span data-stu-id="40c53-136">If you have a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] model deployment package that contains a rule of this type, when you upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the business rule will be excluded.</span></span>  
  
### <a name="bulk-updates-and-exporting"></a><span data-ttu-id="40c53-137">大容量更新和导出</span><span class="sxs-lookup"><span data-stu-id="40c53-137">Bulk Updates and Exporting</span></span>  
 <span data-ttu-id="40c53-138">在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中，不能再大容量更新多个成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="40c53-138">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer update attribute values for multiple members in bulk.</span></span> <span data-ttu-id="40c53-139">若要进行批量更新，请使用临时过程或 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="40c53-139">To do bulk updates, use the staging process or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="40c53-140">在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中，不能再将成员导出到 Excel。</span><span class="sxs-lookup"><span data-stu-id="40c53-140">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer export members to Excel.</span></span> <span data-ttu-id="40c53-141">若要使用 Excel 中的成员，请使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="40c53-141">To work with members in Excel, use the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="40c53-142">事务</span><span class="sxs-lookup"><span data-stu-id="40c53-142">Transactions</span></span>  
 <span data-ttu-id="40c53-143">在 "**资源管理器**" 功能区域中，用户不能再恢复其自己的事务。</span><span class="sxs-lookup"><span data-stu-id="40c53-143">In the **Explorer** functional area, users can no longer revert their own transactions.</span></span> <span data-ttu-id="40c53-144">之前，用户可以还原他们对**资源管理器**中的数据所做的更改。</span><span class="sxs-lookup"><span data-stu-id="40c53-144">Previously, users could revert changes they made to data in **Explorer**.</span></span> <span data-ttu-id="40c53-145">管理员仍可以为 "**版本管理**" 功能区域中的所有用户恢复事务。</span><span class="sxs-lookup"><span data-stu-id="40c53-145">Administrators can still revert transactions for all users in the **Version Management** functional area.</span></span>  
  
 <span data-ttu-id="40c53-146">批注现在是永久性的，且无法删除。</span><span class="sxs-lookup"><span data-stu-id="40c53-146">Annotations are now permanent and cannot be deleted.</span></span> <span data-ttu-id="40c53-147">以前，批注被视为事务，可以通过还原事务来删除批注。</span><span class="sxs-lookup"><span data-stu-id="40c53-147">Previously, annotations were considered transactions and could be deleted by reverting the transaction.</span></span>  
  
### <a name="web-service"></a><span data-ttu-id="40c53-148">Web 服务</span><span class="sxs-lookup"><span data-stu-id="40c53-148">Web Service</span></span>  
 <span data-ttu-id="40c53-149">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服务现在可应 Silverlight 的要求自动启用。</span><span class="sxs-lookup"><span data-stu-id="40c53-149">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] web service is now enabled automatically, as required by Silverlight.</span></span> <span data-ttu-id="40c53-150">以前必须手动启用该 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="40c53-150">Previously, the web service had to be enabled manually.</span></span>  
  
### <a name="powershell-cmdlets"></a><span data-ttu-id="40c53-151">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="40c53-151">PowerShell Cmdlets</span></span>  
 <span data-ttu-id="40c53-152">MDS 不再包括 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40c53-152">MDS no longer includes PowerShell cmdlets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c53-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40c53-153">See Also</span></span>  
 [<span data-ttu-id="40c53-154">SQL Server 2014 中不推荐使用的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="40c53-154">Deprecated Master Data Services Features in SQL Server 2014</span></span>](deprecated-master-data-services-features.md)  
  
  
