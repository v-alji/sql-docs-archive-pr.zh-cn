---
title: 安全性（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ed38291a-6afe-449f-9f32-3ae04502bd6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d744d00068ebd51148aa71ccf5b9ad170ed2f077
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692755"
---
# <a name="security-report-builder"></a><span data-ttu-id="75324-102">安全性（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="75324-102">Security (Report Builder)</span></span>
  <span data-ttu-id="75324-103">报表生成器是一种设计用于处理 Report Server 的报表创作客户端应用程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75324-103">Report Builder is a report authoring client application that is designed to work with a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="75324-104">可以将报表服务器配置为在本机模式中作为独立服务器运行，也可以将报表服务器配置为在 SharePoint 集成模式中运行以支持 SharePoint 站点上的报表。</span><span class="sxs-lookup"><span data-stu-id="75324-104">The report server can be configured to work in native mode as a stand-alone server or in SharePoint integrated mode to support reports on a SharePoint site.</span></span>  
  
 <span data-ttu-id="75324-105">在报表生成器中，可以创作报表、共享数据集和可重用的报表部件。</span><span class="sxs-lookup"><span data-stu-id="75324-105">In Report Builder, you can author reports, shared datasets, and reusable report parts.</span></span> <span data-ttu-id="75324-106">可以从报表服务器或 SharePoint 站点中编辑报表和添加共享数据源、共享数据集和共享报表部件。</span><span class="sxs-lookup"><span data-stu-id="75324-106">From a report server or SharePoint site, you can edit reports and add shared data sources, shared datasets, and shared report parts.</span></span>  
  
 <span data-ttu-id="75324-107">若要创作、发布和使用报表以及与报表相关的项，则应了解安全性功能是如何与以下几个方面相关的：</span><span class="sxs-lookup"><span data-stu-id="75324-107">To author, publish, and use reports and report-related items, you should understand how security features relate to the following areas:</span></span>  
  
-   <span data-ttu-id="75324-108">**在其上发布报表的报表服务器或 SharePoint 站点** 这些功能由报表服务器管理员或 SharePoint 站点管理员管理。</span><span class="sxs-lookup"><span data-stu-id="75324-108">**The report server or SharePoint site where you publish reports** These features are managed by the report server administrator or SharePoint site administrator.</span></span>  
  
-   <span data-ttu-id="75324-109">**已发布的报表以及与报表相关的项** ：与报表相关的项包括嵌入数据源和共享数据源及其凭据、共享数据集、参数、报表部件和报表模型。</span><span class="sxs-lookup"><span data-stu-id="75324-109">**Published reports and report-related items** Report-related items include embedded and shared data sources and their credentials, shared datasets, parameters, report parts, and report models.</span></span> <span data-ttu-id="75324-110">应用于这些项的安全性功能由报表作者管理。</span><span class="sxs-lookup"><span data-stu-id="75324-110">Security features that apply to these items are managed by the report author.</span></span> <span data-ttu-id="75324-111">报表作者必须获得由报表服务器管理员或 SharePoint 站点管理员授予的足够权限，才能发布和共享项。</span><span class="sxs-lookup"><span data-stu-id="75324-111">The report author must be granted sufficient permissions by the report server administrator or SharePoint site administrator to publish and share the items.</span></span>  
  
-   <span data-ttu-id="75324-112">**报表使用的外部数据源** 这些功能由外部数据源的所有者管理。</span><span class="sxs-lookup"><span data-stu-id="75324-112">**External data sources that are used by a report** These features are managed by the owner of the external data source.</span></span>  
  
-   <span data-ttu-id="75324-113">**基于外部数据源的报表模型** 这些功能由模型设计器管理。</span><span class="sxs-lookup"><span data-stu-id="75324-113">**Report models that are based on external data sources** These features are managed by the model designer.</span></span>  
  
-   <span data-ttu-id="75324-114">**交互式报表功能（如参数）** 这些功能由报表作者管理。</span><span class="sxs-lookup"><span data-stu-id="75324-114">**Interactive report features such as parameters** These features are managed by the report author.</span></span>  
  
 <span data-ttu-id="75324-115">查看本主题中的信息，更好地了解如何使用安全性功能来帮助管理和保护报表以及与报表相关的项。</span><span class="sxs-lookup"><span data-stu-id="75324-115">Review the information in this topic to better understand how to use security features to help manage and secure reports and report-related items.</span></span>  
  
##  <a name="understanding-security-for-report-servers"></a><a name="ReportServers"></a> <span data-ttu-id="75324-116">了解报表服务器的安全性</span><span class="sxs-lookup"><span data-stu-id="75324-116">Understanding Security for Report Servers</span></span>  
 <span data-ttu-id="75324-117">发布报表和查看报表是需要特权的操作。</span><span class="sxs-lookup"><span data-stu-id="75324-117">Publishing reports and viewing reports are privileged operations.</span></span> <span data-ttu-id="75324-118">报表服务器管理员授予权限以确保只有得到授权的用户才能在下列某个类型的报表服务器上发布和查看报表：</span><span class="sxs-lookup"><span data-stu-id="75324-118">A report server administrator grants permissions to ensure that only authorized users can publish and view reports on one of the following types of report servers:</span></span>  
  
-   <span data-ttu-id="75324-119">在本机模式中配置的报表服务器</span><span class="sxs-lookup"><span data-stu-id="75324-119">Report server configured in native mode</span></span>  
  
     <span data-ttu-id="75324-120">若要连接到或浏览到一个报表服务器，您必须具有有效的 URL，并且对该服务器具有足够的访问权限。</span><span class="sxs-lookup"><span data-stu-id="75324-120">To connect to or browse to a report server, you must have a valid URL and have sufficient permissions to access the server.</span></span>  
  
     <span data-ttu-id="75324-121">若要在报表服务器上查看或发布项，需将应用于与报表相关的项和操作的权限集组织到角色中。</span><span class="sxs-lookup"><span data-stu-id="75324-121">To view or publish items on a report server, sets of permissions that apply to report-related items and operations are organized into roles.</span></span> <span data-ttu-id="75324-122">报表服务器管理员为您分配了一个或多个角色。</span><span class="sxs-lookup"><span data-stu-id="75324-122">A report server administrator assigns you to one or more roles.</span></span> <span data-ttu-id="75324-123">例如，利用预定义的角色浏览器，可以查看报表、文件夹、模型和资源。</span><span class="sxs-lookup"><span data-stu-id="75324-123">For example, the predefined role Browser enables you to view reports, folders, models, and resources.</span></span>  
  
     <span data-ttu-id="75324-124">如果您无法连接到或浏览到报表服务器，请与报表服务器管理员联系。</span><span class="sxs-lookup"><span data-stu-id="75324-124">If you cannot connect to or browse to a report server, contact the report server administrator.</span></span> <span data-ttu-id="75324-125">有关详细信息，请参阅 [Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) 联机丛书 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="75324-125">For more information, see [Reporting Services Security and Protection](../security/reporting-services-security-and-protection.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
-   <span data-ttu-id="75324-126">在 SharePoint 集成模式中配置的报表服务器</span><span class="sxs-lookup"><span data-stu-id="75324-126">Report server configured in SharePoint integrated mode</span></span>  
  
     <span data-ttu-id="75324-127">若要连接到与报表服务器集成的 SharePoint 站点，您必须具有 SharePoint 站点或子站点的有效 URL，并且具有对其的足够访问权限。</span><span class="sxs-lookup"><span data-stu-id="75324-127">To connect to a SharePoint site that is integrated with a report server, you must have a valid URL to the SharePoint site or subsite and have sufficient permissions to access it.</span></span>  
  
     <span data-ttu-id="75324-128">通过 SharePoint 安全策略来授予与报表相关的项和操作的访问权限，这些策略可映射拥有与项相关的某个权限级别的用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="75324-128">Permission to access report-related items and operations is granted through SharePoint security policies that map a user or group account with a permission level, relative to an item.</span></span>  
  
     <span data-ttu-id="75324-129">如果您无法连接到或浏览到 SharePoint 站点或子站点，请与 SharePoint 站点管理员联系。</span><span class="sxs-lookup"><span data-stu-id="75324-129">If you cannot connect to or browse to a SharePoint site or subsite, contact the SharePoint site administrator.</span></span>  
  
=
  
##  <a name="understanding-security-for-published-reports-and-report-related-items"></a><a name="Reports"></a> <span data-ttu-id="75324-130">了解已发布的报表以及与报表相关的项的安全性</span><span class="sxs-lookup"><span data-stu-id="75324-130">Understanding Security for Published Reports and Report-related Items</span></span>  
 <span data-ttu-id="75324-131">报表以及与报表相关的项的安全性由报表服务器管理员管理。</span><span class="sxs-lookup"><span data-stu-id="75324-131">Security for reports and report-related items is managed by the report server administrator.</span></span> <span data-ttu-id="75324-132">与报表相关的项包括嵌入数据源和共享数据源（包括凭据、共享数据集、参数、报表部件和模型）。</span><span class="sxs-lookup"><span data-stu-id="75324-132">Report-related items include embedded and shared data sources including credentials, shared datasets, parameters, report parts, and models.</span></span>  
  
 <span data-ttu-id="75324-133">在报表服务器或 SharePoint 站点上，可以单独保护报表以及与报表相关的项和操作。</span><span class="sxs-lookup"><span data-stu-id="75324-133">On a report server or SharePoint site, reports and report-related items and operations are independently securable.</span></span> <span data-ttu-id="75324-134">通过安全策略来授予项和操作的访问权限，这些策略可映射拥有与项相关的某个权限级别的用户帐户或组帐户。</span><span class="sxs-lookup"><span data-stu-id="75324-134">Permission to access items and operations is granted through security policies that map a user or group account with a permission level, relative to an item.</span></span> <span data-ttu-id="75324-135">为了降低维护大量策略所带来的复杂性和管理负担，容器（如文件夹）的权限由容器中的项来继承。</span><span class="sxs-lookup"><span data-stu-id="75324-135">To reduce the complexity and overhead of maintaining a large number of policies, permissions on a container, such as a folder, are inherited by items in the container.</span></span> <span data-ttu-id="75324-136">例如，如果用户具有某个文件夹的特定“查看报表”权限，则用户具有该文件夹中的项的“查看报表”权限。</span><span class="sxs-lookup"><span data-stu-id="75324-136">For example, if a user has the specific View Reports permission on a folder, they have View Reports permission on the items in the folder.</span></span>  
  
 <span data-ttu-id="75324-137">可以使用项级别安全性来覆盖项或文件夹的权限。</span><span class="sxs-lookup"><span data-stu-id="75324-137">Permissions can be overridden on items or folders by using item level security.</span></span> <span data-ttu-id="75324-138">在应用项级别安全性时，从父容器进行的权限继承将不再适用于项。</span><span class="sxs-lookup"><span data-stu-id="75324-138">When item-level security is applied, permission inheritance from the parent container no longer applies to the item.</span></span> <span data-ttu-id="75324-139">如果对文件夹应用项级别安全性，则嵌套文件夹将继承相同的权限。</span><span class="sxs-lookup"><span data-stu-id="75324-139">If item-level security is applied to a folder, nested folders inherit the same permissions.</span></span>  
  
 <span data-ttu-id="75324-140">如果无法浏览并找到其他人已为您发布的项，则您对项或文件夹所具有的权限可能有问题。</span><span class="sxs-lookup"><span data-stu-id="75324-140">If you are not able to browse to and find items that someone else has published for you, you might have a permissions issue on the item or on the folder.</span></span>  
  
 <span data-ttu-id="75324-141">为了让其他人能够浏览并找到您已发布的共享项，您必须与报表服务器管理员协作，设置用于为您的用户提供访问权的文件夹组织。</span><span class="sxs-lookup"><span data-stu-id="75324-141">To enable others to browse to and find items that you published to be shared, you must work with the report server administrator to set up a folder organization that provides access to your users.</span></span> <span data-ttu-id="75324-142">创作报表和运行已发布的报表时必须具有访问权。</span><span class="sxs-lookup"><span data-stu-id="75324-142">Access must be available for authoring reports and for running published reports.</span></span>  
  
 <span data-ttu-id="75324-143">有关详细信息，请参阅 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span><span class="sxs-lookup"><span data-stu-id="75324-143">For more information, see the following topics in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span></span>  
  
-   [<span data-ttu-id="75324-144">角色和权限 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="75324-144">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
-   [<span data-ttu-id="75324-145">管理共享数据集</span><span class="sxs-lookup"><span data-stu-id="75324-145">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
### <a name="update-notifications-for-report-parts"></a><span data-ttu-id="75324-146">报表部件的更新通知</span><span class="sxs-lookup"><span data-stu-id="75324-146">Update Notifications for Report Parts</span></span>  
 <span data-ttu-id="75324-147">报表部件将发布到报表服务器以供其他人进行共享。</span><span class="sxs-lookup"><span data-stu-id="75324-147">Report parts are published to a report server so that others can share them.</span></span> <span data-ttu-id="75324-148">根据设计来指定将报表部件发布到的位置。</span><span class="sxs-lookup"><span data-stu-id="75324-148">By design, you specify the location to publish report parts to.</span></span>  
  
 <span data-ttu-id="75324-149">将报表部件包含在其报表中的用户可以启用更新功能。</span><span class="sxs-lookup"><span data-stu-id="75324-149">Users who include report parts in their reports can enable the update feature.</span></span> <span data-ttu-id="75324-150">在启用此功能后，当报表服务器上的报表部件发生更改时，用户会收到通知。</span><span class="sxs-lookup"><span data-stu-id="75324-150">When this feature is enabled, users receive notifications when report parts change on the report server.</span></span>  
  
 <span data-ttu-id="75324-151">如果报表部件是从原始位置移动的，则更新通知将包含报表部件的当前位置和先前位置。</span><span class="sxs-lookup"><span data-stu-id="75324-151">If report parts are moved from the original location, the update notice includes both the current location and the previous location of the report part.</span></span> <span data-ttu-id="75324-152">仅接受来自受信任位置的更新。</span><span class="sxs-lookup"><span data-stu-id="75324-152">Accept updates only from trusted locations.</span></span>  
  
 <span data-ttu-id="75324-153">有关详细信息，请参阅 [报表部件（报表生成器和 SSRS）](../report-parts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="75324-153">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
=  
  
##  <a name="understanding-security-for-report-data-and-external-data-sources"></a><a name="Data"></a> <span data-ttu-id="75324-154">了解报表数据和外部数据源的安全性</span><span class="sxs-lookup"><span data-stu-id="75324-154">Understanding Security for Report Data and External Data Sources</span></span>  
 <span data-ttu-id="75324-155">若要在报表中访问来自每个外部数据源的数据，请在报表中创建嵌入数据源或添加对共享数据源或共享数据集的引用。</span><span class="sxs-lookup"><span data-stu-id="75324-155">To access data from each external data source in a report, you create an embedded data source or add a reference to a shared data source or shared dataset in your report.</span></span>  
  
 <span data-ttu-id="75324-156">对于每个外部数据源，您必须提供足以用来访问源和基础数据的凭据。</span><span class="sxs-lookup"><span data-stu-id="75324-156">For each external data source, you must supply credentials that are sufficient to access the source and the underlying data.</span></span> <span data-ttu-id="75324-157">数据源所有者将指定用于提供此访问的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="75324-157">The data source owner specifies the type of credentials that provides this access.</span></span>  
  
 <span data-ttu-id="75324-158">凭据不保存在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="75324-158">Credentials are not saved in the report definition.</span></span> <span data-ttu-id="75324-159">将从报表服务器或 SharePoint 站点和报表创作客户端上的报表中独立管理这些凭据。</span><span class="sxs-lookup"><span data-stu-id="75324-159">They are managed independently from the report on the report server or SharePoint site and on the report authoring client.</span></span>  
  
 <span data-ttu-id="75324-160">在报表设计时，凭据用于运行数据集查询和预览报表。</span><span class="sxs-lookup"><span data-stu-id="75324-160">At report design time, credentials are used to run dataset queries and preview the report.</span></span> <span data-ttu-id="75324-161">在运行时，凭据用于运行报表和缓存查询结果。</span><span class="sxs-lookup"><span data-stu-id="75324-161">At run time, credentials are used to run the report and cache query results.</span></span> <span data-ttu-id="75324-162">也可以单独缓存数据集查询结果。</span><span class="sxs-lookup"><span data-stu-id="75324-162">You can also cache shared dataset query results independently.</span></span> <span data-ttu-id="75324-163">设计时凭据和运行时凭据可能不同。</span><span class="sxs-lookup"><span data-stu-id="75324-163">Design time and run time credentials might differ.</span></span> <span data-ttu-id="75324-164">有关详细信息，请参阅 [在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="75324-164">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="75324-165">有关保护数据的详细信息，请参阅 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span><span class="sxs-lookup"><span data-stu-id="75324-165">For more information about securing data, see the following topic in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312):</span></span>  
  
-   [<span data-ttu-id="75324-166">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="75324-166">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 <span data-ttu-id="75324-167">有关数据源的详细信息，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="75324-167">For more information about data sources, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
=
  
##  <a name="understanding-models-and-security-filters"></a><a name="Models"></a> <span data-ttu-id="75324-168">了解模型和安全筛选器</span><span class="sxs-lookup"><span data-stu-id="75324-168">Understanding Models and Security Filters</span></span>  
 <span data-ttu-id="75324-169">在从基于外部数据的报表模型中检索数据时，可以在该模型中应用安全筛选器。这是保护数据的好方法，使每个运行报表的用户只能看到其有权使用的数据。</span><span class="sxs-lookup"><span data-stu-id="75324-169">When data is retrieved from a report model that is based on external data, you can apply security filters in the model  This is a good way to secure data so that each user who runs a report can see only the data that they have permissions to.</span></span>  
  
 <span data-ttu-id="75324-170">报表参数不能提供行级安全性；它们并不防止用户或用户组查看特定的数据行。</span><span class="sxs-lookup"><span data-stu-id="75324-170">Report parameters are not used for row-level security; they do not prevent users or groups of users from seeing specific rows of data.</span></span> <span data-ttu-id="75324-171">若要对报表中显示的数据应用安全性，必须使用安全筛选器或模型项安全性。</span><span class="sxs-lookup"><span data-stu-id="75324-171">To apply security to the data displayed within a report, you must use security filters or model item security.</span></span>  
  
=
  
##  <a name="understanding-security-for-report-authoring-for-interactive-features"></a><a name="Interactive"></a> <span data-ttu-id="75324-172">了解为报表创作交互式功能的安全性</span><span class="sxs-lookup"><span data-stu-id="75324-172">Understanding Security for Report Authoring for Interactive Features</span></span>  
 <span data-ttu-id="75324-173">报表经常会使用参数，使用户能够以交互方式自定义其报表视图。</span><span class="sxs-lookup"><span data-stu-id="75324-173">Reports frequently use parameters to enable a user to interactively customize their view of a report.</span></span> <span data-ttu-id="75324-174">使用以下提示可帮助设计遵循良好实践的报表：</span><span class="sxs-lookup"><span data-stu-id="75324-174">Use the following tips to help design reports that follow good practices:</span></span>  
  
-   <span data-ttu-id="75324-175">除非您提供了有效的值，否则不要使用基于查询参数且类型为 **Text** 的参数。</span><span class="sxs-lookup"><span data-stu-id="75324-175">Do not use parameters that are based on query parameters and that are type **Text** unless you provide valid values.</span></span> <span data-ttu-id="75324-176">可用值列表可帮助用户只选择有效值。</span><span class="sxs-lookup"><span data-stu-id="75324-176">An available values list helps a user choose only valid values.</span></span> <span data-ttu-id="75324-177">如果不使用可用值列表，则无法限制用户可输入的值。</span><span class="sxs-lookup"><span data-stu-id="75324-177">Without an available values list, you cannot restrict which values a user can enter.</span></span>  
  
-   <span data-ttu-id="75324-178">不要使用全局 [&UserID] 来保护私有数据。</span><span class="sxs-lookup"><span data-stu-id="75324-178">Do not use the global [&UserID] to secure private data.</span></span> <span data-ttu-id="75324-179">当此值作为报表参数时，可以使用 URL 访问语法在报表 URL 中指定此值。</span><span class="sxs-lookup"><span data-stu-id="75324-179">As a report parameter, this value can be specified in a report URL by using URL access syntax.</span></span> <span data-ttu-id="75324-180">在共享数据集的表达式中使用此值可防止数据集被缓存。</span><span class="sxs-lookup"><span data-stu-id="75324-180">Using this value in an expression in a shared dataset prevents the dataset from being cached.</span></span> <span data-ttu-id="75324-181">有关详细信息，请参阅 [URL Access Parameter Reference](../url-access-parameter-reference.md) 联机丛书 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="75324-181">For more information, see [URL Access Parameter Reference](../url-access-parameter-reference.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="75324-182">在将项发布到报表服务器后，报表服务器管理员可通过分配基于角色的安全性或文件夹和项级别安全性来帮助保护这些项。</span><span class="sxs-lookup"><span data-stu-id="75324-182">After items are published to a report server, the report server administrator can help secure them by assigning role-based security or folder and item level security.</span></span> <span data-ttu-id="75324-183">有关详细信息，请参阅 [Secure Reports and Resources](../security/secure-reports-and-resources.md) 联机丛书 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span><span class="sxs-lookup"><span data-stu-id="75324-183">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="75324-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75324-184">See Also</span></span>  
 <span data-ttu-id="75324-185">[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="75324-185">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="75324-186">报表参数（报表生成器和报表设计器）</span><span class="sxs-lookup"><span data-stu-id="75324-186">Report Parameters &#40;Report Builder and Report Designer&#41;</span></span>](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
  
