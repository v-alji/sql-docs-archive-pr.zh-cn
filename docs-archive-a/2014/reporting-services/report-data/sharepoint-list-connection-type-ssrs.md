---
title: SharePoint 列表连接类型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2c4adf2f-e9c4-4fae-bd3c-97fe64436caf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dbe50adbf8d4daa7b616dad7f40d185a4c923d77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580002"
---
# <a name="sharepoint-list-connection-type-ssrs"></a><span data-ttu-id="7766d-102">SharePoint 列表连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7766d-102">SharePoint List Connection Type (SSRS)</span></span>
  <span data-ttu-id="7766d-103">若要在报表中包含来自 Microsoft SharePoint 列表的数据，您必须添加或创建一个基于 Microsoft SharePoint 列表类型的报表数据源的数据集。</span><span class="sxs-lookup"><span data-stu-id="7766d-103">To include data from a Microsoft SharePoint list in your report, you must add or create a dataset that is based on a report data source of type Microsoft SharePoint List.</span></span> <span data-ttu-id="7766d-104">此内置数据源类型是基于 Microsoft SQL Server Reporting Services SharePoint 列表数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="7766d-104">This is a built-in data source type based on the Microsoft SQL Server Reporting Services SharePoint List data extension.</span></span> <span data-ttu-id="7766d-105">使用此数据源类型可连接到 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 和 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 站点，并从中检索列表数据。</span><span class="sxs-lookup"><span data-stu-id="7766d-105">Use this data source type to connect to and retrieve list data from [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], [!INCLUDE[SPS2010](../../includes/sps2010-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0, and [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 sites.</span></span>  
  
 <span data-ttu-id="7766d-106">使用本主题中的信息来生成一个数据源。</span><span class="sxs-lookup"><span data-stu-id="7766d-106">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="7766d-107">有关分步说明，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-107">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="7766d-108">连接字符串</span><span class="sxs-lookup"><span data-stu-id="7766d-108">Connection String</span></span>  
 <span data-ttu-id="7766d-109">SharePoint 列表的连接字符串是指向 SharePoint 站点或子站点（例如， `http://MySharePointWeb/MySharePointSite` 或 `http://MySharePointWeb/MySharePointSite/Subsite`）的 URL。</span><span class="sxs-lookup"><span data-stu-id="7766d-109">The connection string to a SharePoint list is the URL to the SharePoint site or subsite, for example, `http://MySharePointWeb/MySharePointSite` or `http://MySharePointWeb/MySharePointSite/Subsite`.</span></span>  
  
 <span data-ttu-id="7766d-110">查询设计器会自动显示您拥有足够访问权限的 SharePoint 列表。</span><span class="sxs-lookup"><span data-stu-id="7766d-110">The query designer automatically displays the SharePoint lists that you have sufficient permissions to access.</span></span>  
  
 <span data-ttu-id="7766d-111">有关更多连接字符串的示例，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-111">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="7766d-112">凭据</span><span class="sxs-lookup"><span data-stu-id="7766d-112">Credentials</span></span>  
 <span data-ttu-id="7766d-113">执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。</span><span class="sxs-lookup"><span data-stu-id="7766d-113">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span> <span data-ttu-id="7766d-114">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="7766d-114">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span> <span data-ttu-id="7766d-115">可与此数据扩展插件一起使用的凭据类型取决于用作数据源的 SharePoint 列表的 SharePoint 技术配置。</span><span class="sxs-lookup"><span data-stu-id="7766d-115">The types of credentials that can be used with this data extension depend on the SharePoint technology configuration for the SharePoint list that you are using as a data source.</span></span>  
  
 <span data-ttu-id="7766d-116">下表概括了在连接到本地场 SharePoint 列表和远程 SharePoint 列表时，SharePoint 列表扩展的凭据检索行为。</span><span class="sxs-lookup"><span data-stu-id="7766d-116">The following tables outline credential retrieval behavior for the SharePoint list extension, when connecting to a local farm SharePoint list and to a remote SharePoint list.</span></span>  
  
 <span data-ttu-id="7766d-117">**表 1** 适用于部署到旧的 Windows SharePoint 站点的报表。</span><span class="sxs-lookup"><span data-stu-id="7766d-117">**Table 1** is for reports deployed to a legacy Windows SharePoint Site.</span></span> <span data-ttu-id="7766d-118">旧的 Windows 站点仅支持 Kerberos、NTLM 和基于窗体的身份验证 (FBA)。</span><span class="sxs-lookup"><span data-stu-id="7766d-118">A legacy Windows site supports only Kerberos, NTLM, and Forms Based Authentication (FBA).</span></span> <span data-ttu-id="7766d-119">**表 2** 适用于部署到基于声明的 SharePoint 站点的报表。</span><span class="sxs-lookup"><span data-stu-id="7766d-119">**Table 2** is for reports deployed to a Claims-based SharePoint site.</span></span>  
  
 <span data-ttu-id="7766d-120">**表1**</span><span class="sxs-lookup"><span data-stu-id="7766d-120">**Table 1**</span></span>  
  
||<span data-ttu-id="7766d-121">受支持的凭据</span><span class="sxs-lookup"><span data-stu-id="7766d-121">Supported Credentials</span></span>|<span data-ttu-id="7766d-122">经典模式 Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="7766d-122">Classic Mode Windows Authentication</span></span>|<span data-ttu-id="7766d-123"><sup>3</sup>声明身份验证</span><span class="sxs-lookup"><span data-stu-id="7766d-123"><sup>3</sup> Claims Authentication</span></span>|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|<span data-ttu-id="7766d-124">本地场 SharePoint 列表</span><span class="sxs-lookup"><span data-stu-id="7766d-124">Local farm SharePoint List</span></span>|<span data-ttu-id="7766d-125">Windows 身份验证（集成）或 SharePoint 用户标记</span><span class="sxs-lookup"><span data-stu-id="7766d-125">Windows Authentication (integrated) or SharePoint User Token</span></span>|<span data-ttu-id="7766d-126">是</span><span class="sxs-lookup"><span data-stu-id="7766d-126">Yes</span></span>|<span data-ttu-id="7766d-127">是</span><span class="sxs-lookup"><span data-stu-id="7766d-127">Yes</span></span>|  
||<span data-ttu-id="7766d-128">存储、提示、无（带有 Windows 凭据<sup>1</sup>）</span><span class="sxs-lookup"><span data-stu-id="7766d-128">Stored, Prompt, None (with Windows credentials<sup>1</sup>)</span></span>|<span data-ttu-id="7766d-129">是</span><span class="sxs-lookup"><span data-stu-id="7766d-129">Yes</span></span>|<span data-ttu-id="7766d-130">否</span><span class="sxs-lookup"><span data-stu-id="7766d-130">No</span></span>|  
|<span data-ttu-id="7766d-131">远程 SharePoint 列表</span><span class="sxs-lookup"><span data-stu-id="7766d-131">Remote SharePoint List</span></span>|<span data-ttu-id="7766d-132">Windows 身份验证（集成）或 SharePoint 用户标记</span><span class="sxs-lookup"><span data-stu-id="7766d-132">Windows Authentication (integrated) or SharePoint User Token</span></span>|<span data-ttu-id="7766d-133">是</span><span class="sxs-lookup"><span data-stu-id="7766d-133">Yes</span></span>|<span data-ttu-id="7766d-134">否<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7766d-134">No<sup>2</sup></span></span>|  
||<span data-ttu-id="7766d-135">存储、提示、无（带有 Windows 凭据<sup>1</sup>）</span><span class="sxs-lookup"><span data-stu-id="7766d-135">Stored, Prompt, None (with Windows credentials<sup>1</sup>)</span></span>|<span data-ttu-id="7766d-136">是</span><span class="sxs-lookup"><span data-stu-id="7766d-136">Yes</span></span>|<span data-ttu-id="7766d-137">否<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7766d-137">No<sup>2</sup></span></span>|  
  
 <span data-ttu-id="7766d-138">**表2**</span><span class="sxs-lookup"><span data-stu-id="7766d-138">**Table 2**</span></span>  
  
||<span data-ttu-id="7766d-139">受支持的凭据</span><span class="sxs-lookup"><span data-stu-id="7766d-139">Supported Credentials</span></span>|<span data-ttu-id="7766d-140">经典模式 Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="7766d-140">Classic Mode Windows Authentication</span></span>|<span data-ttu-id="7766d-141"><sup>3</sup>声明身份验证</span><span class="sxs-lookup"><span data-stu-id="7766d-141"><sup>3</sup> Claims Authentication</span></span>|  
|-|---------------------------|-----------------------------------------|----------------------------------------|  
|<span data-ttu-id="7766d-142">本地场 SharePoint 列表</span><span class="sxs-lookup"><span data-stu-id="7766d-142">Local Farm SharePoint List</span></span>|<span data-ttu-id="7766d-143">Windows 身份验证（集成）或 SharePoint 用户标记</span><span class="sxs-lookup"><span data-stu-id="7766d-143">Windows Authentication (integrated) or SharePoint User Token</span></span>|<span data-ttu-id="7766d-144">是</span><span class="sxs-lookup"><span data-stu-id="7766d-144">Yes</span></span>|<span data-ttu-id="7766d-145">是</span><span class="sxs-lookup"><span data-stu-id="7766d-145">Yes</span></span>|  
||<span data-ttu-id="7766d-146">存储、提示、无（带有 Windows 凭据<sup>1</sup>）</span><span class="sxs-lookup"><span data-stu-id="7766d-146">Stored, Prompt, None (with Windows credentials<sup>1</sup>)</span></span>|<span data-ttu-id="7766d-147">否</span><span class="sxs-lookup"><span data-stu-id="7766d-147">No</span></span>|<span data-ttu-id="7766d-148">否</span><span class="sxs-lookup"><span data-stu-id="7766d-148">No</span></span>|  
|<span data-ttu-id="7766d-149">远程 SharePoint 列表</span><span class="sxs-lookup"><span data-stu-id="7766d-149">Remote SharePoint List</span></span>|<span data-ttu-id="7766d-150">Windows 身份验证（集成）或 SharePoint 用户标记</span><span class="sxs-lookup"><span data-stu-id="7766d-150">Windows Authentication (integrated) or SharePoint User Token</span></span>|<span data-ttu-id="7766d-151">是</span><span class="sxs-lookup"><span data-stu-id="7766d-151">Yes</span></span>|<span data-ttu-id="7766d-152">否<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7766d-152">No<sup>2</sup></span></span>|  
||<span data-ttu-id="7766d-153">存储、提示、无（带有 Windows 凭据<sup>1</sup>）</span><span class="sxs-lookup"><span data-stu-id="7766d-153">Stored, Prompt, None (with Windows credentials<sup>1</sup>)</span></span>|<span data-ttu-id="7766d-154">否</span><span class="sxs-lookup"><span data-stu-id="7766d-154">No</span></span>|<span data-ttu-id="7766d-155">否<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7766d-155">No<sup>2</sup></span></span>|  
  
 <span data-ttu-id="7766d-156"><sup>1</sup>不支持带有非 Windows 凭据的存储和提示凭据。</span><span class="sxs-lookup"><span data-stu-id="7766d-156"><sup>1</sup> Stored and prompt credentials with non-Windows credentials is not supported.</span></span>  
  
 <span data-ttu-id="7766d-157"><sup>2</sup>远程 SharePoint 列表不支持基于窗体的身份验证和声明身份验证。</span><span class="sxs-lookup"><span data-stu-id="7766d-157"><sup>2</sup> Forms-based authentication and Claims authentication are not supported for remote SharePoint lists.</span></span>  
  
 <span data-ttu-id="7766d-158"><sup>3</sup> Windows 身份验证、基于窗体的身份验证 (FBA) 、安全应用程序标记语言 (SAML) 令牌、其他标识提供程序或以上提到的多个身份验证提供程序的组合。</span><span class="sxs-lookup"><span data-stu-id="7766d-158"><sup>3</sup> Windows authentication, Forms Based authentication (FBA), Secure Application Markup Language (SAML) tokens, other identity providers or a combination of more than one of the above mentioned authentication providers.</span></span>  
  
 <span data-ttu-id="7766d-159">**Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="7766d-159">**Windows Authentication**</span></span>  
 <span data-ttu-id="7766d-160">对于配置为在“可信帐户”模式下与报表服务器一起使用的 SharePoint 技术，不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="7766d-160">For a SharePoint technology that is configured to work with a report server in Trusted Account mode, this option is not supported.</span></span> <span data-ttu-id="7766d-161">仅适用于 SQL Server 2012 Reporting Services 之前的版本。</span><span class="sxs-lookup"><span data-stu-id="7766d-161">This applies only to releases prior to SQL Server 2012 Reporting Services.</span></span>  
  
 <span data-ttu-id="7766d-162">对于配置为在“Windows 集成”模式下与报表服务器一起使用的 SharePoint 技术，此选项既适用于当前 Windows 用户，也适用于当前 SharePoint 用户。</span><span class="sxs-lookup"><span data-stu-id="7766d-162">For a SharePoint technology that is configured to work with a report server in Windows Integrated mode, this option applies to both the current Windows user and the current SharePoint user.</span></span>  
  
 <span data-ttu-id="7766d-163">对于配置为不使用报表服务器的 SharePoint 技术（本地模式），不支持此选项。</span><span class="sxs-lookup"><span data-stu-id="7766d-163">For a SharePoint technology that is configured to work without a Report Server (local mode), this option is not supported.</span></span> <span data-ttu-id="7766d-164">有关本地模式的详细信息，请参阅["报表查看器" 中的 "本地模式" 与 "连接模式报表" &#40;Reporting Services 在 SharePoint 模式下&#41;" ](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-164">For more information on local mode, see [Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
 <span data-ttu-id="7766d-165">**不需要凭据（不使用凭据）：**</span><span class="sxs-lookup"><span data-stu-id="7766d-165">**Credentials are not required (Do not use credentials):**</span></span>  
 <span data-ttu-id="7766d-166">若要使用此选项，必须为报表服务器配置无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="7766d-166">To use this option, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="7766d-167">有关详细信息，请参阅[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-167">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="7766d-168">有关 Microsoft BI 堆栈中声明身份验证支持的信息，请参阅 [在 Microsoft BI 堆栈中使用声明身份验证](https://social.technet.microsoft.com/wiki/contents/articles/15274.using-claims-authentication-across-the-microsoft-bi-stack.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7766d-168">For information about Claims authentication support across the Microsoft BI stack, see [Using Claims Authentication across the Microsoft BI Stack](https://social.technet.microsoft.com/wiki/contents/articles/15274.using-claims-authentication-across-the-microsoft-bi-stack.aspx).</span></span>  
  
 <span data-ttu-id="7766d-169">有关详细信息，请参阅 Reporting Services 中的[数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)、[指定报表生成器中的凭据](../specify-credentials-in-report-builder.md)，以及[Reporting Services &#40;SSRS&#41;所支持的数据源](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-169">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md), [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md), and [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="7766d-170">请求</span><span class="sxs-lookup"><span data-stu-id="7766d-170">Queries</span></span>  
 <span data-ttu-id="7766d-171">若要设计一个查询，请基于数据源创建新数据集，然后打开关联的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="7766d-171">To design a query, create a new dataset based on the data source, and then open the associated query designer.</span></span> <span data-ttu-id="7766d-172">有关详细信息，请参阅 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-172">For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7766d-173">SharePoint 列表图形查询设计器中显示四个窗格：</span><span class="sxs-lookup"><span data-stu-id="7766d-173">The SharePoint List graphical query designer displays four panes:</span></span>  
  
 <span data-ttu-id="7766d-174">**SharePoint 列表**  ：显示该数据源在站点上的所有 SharePoint 列表的列表。</span><span class="sxs-lookup"><span data-stu-id="7766d-174">**SharePoint Lists**  Displays a list of all the SharePoint lists on the site for this data source.</span></span> <span data-ttu-id="7766d-175">选择某一列表，然后选择要位于查询中的字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-175">Select a list and then select the fields that you want in your query.</span></span> <span data-ttu-id="7766d-176">此窗格中字段的名称是 SharePoint 友好名称，也称为显示名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-176">The names of fields in this pane are the SharePoint friendly names, also known as display names.</span></span> <span data-ttu-id="7766d-177">将鼠标指针悬停在某一项上可在工具提示中显示以下属性：</span><span class="sxs-lookup"><span data-stu-id="7766d-177">Hover over an item to display the following properties in the tooltip:</span></span>  
  
-   <span data-ttu-id="7766d-178">**名称** ：字段的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-178">**Name** The unique name of the field.</span></span>  
  
-   <span data-ttu-id="7766d-179">**标识符** ：字段的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="7766d-179">**Identifier** The unique identifier of the field.</span></span>  
  
-   <span data-ttu-id="7766d-180">**字段类型** ：字段的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7766d-180">**Field Type** The data type of the field.</span></span>  
  
-   <span data-ttu-id="7766d-181">**隐藏** ：字段是否显示在 SharePoint 列表视图中。</span><span class="sxs-lookup"><span data-stu-id="7766d-181">**Hidden** Whether the field displays in the SharePoint list view.</span></span>  
  
 <span data-ttu-id="7766d-182">不支持从多个列表中选择字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-182">Selecting fields from multiple lists is not supported.</span></span> <span data-ttu-id="7766d-183">可以为每个列表创建一个数据集并从每个数据集中选择字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-183">You can create a dataset for each list and select fields from each dataset.</span></span> <span data-ttu-id="7766d-184">如果这些列表具有通用字段，则可以使用绑定到一个数据集的 Tablix 数据区域中的 Lookup 函数从另一个未绑定到数据区域的数据集中检索值。</span><span class="sxs-lookup"><span data-stu-id="7766d-184">If the lists have a common field, you can use the Lookup function in a tablix data region that is bound to one dataset to retrieve a value from the other dataset that is not bound to the data region.</span></span> <span data-ttu-id="7766d-185">有关详细信息，请参阅 [Lookup 函数（报表生成器和 SSRS）](../report-design/report-builder-functions-lookup-function.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-185">For more information, see [Lookup Function &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-lookup-function.md).</span></span>  
  
-   <span data-ttu-id="7766d-186">**所选字段**  ：显示所选的字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-186">**Selected Fields**  Displays the fields that you have selected.</span></span> <span data-ttu-id="7766d-187">此窗格中的字段名称是 SharePoint 用户指定的友好名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-187">The names of fields in this pane are friendly names that a SharePoint user has specified.</span></span> <span data-ttu-id="7766d-188">在您关闭查询设计器后，将会在“报表数据”窗格的数据集字段集合中看到这些名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-188">When you close the query designer, you see these names in the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="7766d-189">[“数据集属性”对话框 ->“字段”（报表生成器）](../dataset-properties-dialog-box-fields-report-builder.md)页介绍了唯一名称和友好名称的关系。</span><span class="sxs-lookup"><span data-stu-id="7766d-189">The relationship between unique names and friendly names is available in the [Dataset Properties Dialog Box, Fields &#40;Report Builder&#41;](../dataset-properties-dialog-box-fields-report-builder.md) page.</span></span>  
  
-   <span data-ttu-id="7766d-190">**应用的筛选器**  ：在数据返回到报表中之前，限制从 SharePoint 列表返回的数据。</span><span class="sxs-lookup"><span data-stu-id="7766d-190">**Applied Filters**  Limits the data that is returned from the SharePoint list, before the data is returned to the report.</span></span> <span data-ttu-id="7766d-191">选择用于限制在列表中检索的数据的字段名称、运算符和值。</span><span class="sxs-lookup"><span data-stu-id="7766d-191">Select the field name, operator, and value to use to limit the data that is retrieved in the list.</span></span> <span data-ttu-id="7766d-192">根据所选值的数据类型的不同，运算符也会有所不同。</span><span class="sxs-lookup"><span data-stu-id="7766d-192">The operators vary depending on the data type of the value that you select.</span></span>  
  
     <span data-ttu-id="7766d-193">您不能在图形查询设计器中更改排序顺序或指定组。</span><span class="sxs-lookup"><span data-stu-id="7766d-193">You cannot change the sort order or specify groups in the graphical query designer.</span></span> <span data-ttu-id="7766d-194">为了更改排序顺序或指定组，请对报表数据集设置排序表达式，并且对报表中数据区域上的表达式进行分组。</span><span class="sxs-lookup"><span data-stu-id="7766d-194">To do that, set sort expressions on the report dataset, and group expressions on the data regions in the report.</span></span> <span data-ttu-id="7766d-195">不支持查询参数。</span><span class="sxs-lookup"><span data-stu-id="7766d-195">Query parameters are not supported.</span></span> <span data-ttu-id="7766d-196">若要筛选报表中的数据，请使用您创建的报表筛选器或报表参数。</span><span class="sxs-lookup"><span data-stu-id="7766d-196">To filter data in the report, use report filters or report parameters that you create.</span></span> <span data-ttu-id="7766d-197">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) 和 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-197">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) and [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
-   <span data-ttu-id="7766d-198">**查询结果**  ：显示查询运行时返回的示例行。</span><span class="sxs-lookup"><span data-stu-id="7766d-198">**Query Results**  Displays example rows that are returned when the query runs.</span></span> <span data-ttu-id="7766d-199">如果 SharePoint 列表值在 SharePoint 站点上频繁更改，则您在查询结果窗格中看到的值可能不同于在报表中看到的值。</span><span class="sxs-lookup"><span data-stu-id="7766d-199">If the SharePoint list values change frequently on the SharePoint site, the values that you see in the query results pane might differ from the values that you see in the report.</span></span>  
  
-   <span data-ttu-id="7766d-200">**所选字段**  ：显示所选的字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-200">**Selected Fields**  Displays the fields that you have selected.</span></span> <span data-ttu-id="7766d-201">此窗格中的字段名称是 SharePoint 用户指定的友好名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-201">The names of fields in this pane are friendly names that a SharePoint user has specified.</span></span> <span data-ttu-id="7766d-202">在您关闭查询设计器后，将会在“报表数据”窗格的数据集字段集合中看到这些名称。</span><span class="sxs-lookup"><span data-stu-id="7766d-202">When you close the query designer, you see these names in the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="7766d-203">[“数据集属性”对话框 ->“字段”（报表生成器）](../dataset-properties-dialog-box-fields-report-builder.md)页介绍了唯一名称和友好名称的关系。</span><span class="sxs-lookup"><span data-stu-id="7766d-203">The relationship between unique names and friendly names is available in the [Dataset Properties Dialog Box, Fields &#40;Report Builder&#41;](../dataset-properties-dialog-box-fields-report-builder.md) page.</span></span>  
  
-   <span data-ttu-id="7766d-204">**应用的筛选器**  ：在数据返回到报表中之前，限制从 SharePoint 列表返回的数据。</span><span class="sxs-lookup"><span data-stu-id="7766d-204">**Applied Filters**  Limits the data that is returned from the SharePoint list, before the data is returned to the report.</span></span> <span data-ttu-id="7766d-205">选择用于限制在列表中检索的数据的字段名称、运算符和值。</span><span class="sxs-lookup"><span data-stu-id="7766d-205">Select the field name, operator, and value to use to limit the data that is retrieved in the list.</span></span> <span data-ttu-id="7766d-206">根据所选值的数据类型的不同，运算符也会有所不同。</span><span class="sxs-lookup"><span data-stu-id="7766d-206">The operators vary depending on the data type of the value that you select.</span></span>  
  
     <span data-ttu-id="7766d-207">您不能在图形查询设计器中更改排序顺序或指定组。</span><span class="sxs-lookup"><span data-stu-id="7766d-207">You cannot change the sort order or specify groups in the graphical query designer.</span></span> <span data-ttu-id="7766d-208">为了更改排序顺序或指定组，请对报表数据集设置排序表达式，并且对报表中数据区域上的表达式进行分组。</span><span class="sxs-lookup"><span data-stu-id="7766d-208">To do that, set sort expressions on the report dataset, and group expressions on the data regions in the report.</span></span> <span data-ttu-id="7766d-209">不支持查询参数。</span><span class="sxs-lookup"><span data-stu-id="7766d-209">Query parameters are not supported.</span></span> <span data-ttu-id="7766d-210">若要筛选报表中的数据，请使用您创建的报表筛选器或报表参数。</span><span class="sxs-lookup"><span data-stu-id="7766d-210">To filter data in the report, use report filters or report parameters that you create.</span></span> <span data-ttu-id="7766d-211">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) 和 [报表参数（报表生成器和报表设计器）](../report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-211">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) and [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
-   <span data-ttu-id="7766d-212">**查询结果**  ：显示查询运行时返回的示例行。</span><span class="sxs-lookup"><span data-stu-id="7766d-212">**Query Results**  Displays example rows that are returned when the query runs.</span></span> <span data-ttu-id="7766d-213">如果 SharePoint 列表值在 SharePoint 站点上频繁更改，则您在查询结果窗格中看到的值可能不同于在报表中看到的值。</span><span class="sxs-lookup"><span data-stu-id="7766d-213">If the SharePoint list values change frequently on the SharePoint site, the values that you see in the query results pane might differ from the values that you see in the report.</span></span>  
  
 <span data-ttu-id="7766d-214">有关详细信息，请参阅 [SharePoint 列表查询设计器（报表生成器）](sharepoint-list-query-designer-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-214">For more information, see [SharePoint List Query Designer &#40;Report Builder&#41;](sharepoint-list-query-designer-report-builder.md).</span></span>  
  
### <a name="query-text"></a><span data-ttu-id="7766d-215">查询文本</span><span class="sxs-lookup"><span data-stu-id="7766d-215">Query Text</span></span>  
 <span data-ttu-id="7766d-216">若要查看图形查询设计器生成的查询，请切换到基于文本的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="7766d-216">To view the query that is generated by the graphical query designer, switch to the text-based query designer.</span></span> <span data-ttu-id="7766d-217">在此视图中，您可以看到由图形查询设计器创建的 XML。</span><span class="sxs-lookup"><span data-stu-id="7766d-217">In this view, you can see the XML that is created by the graphical query designer.</span></span> <span data-ttu-id="7766d-218">该 XML 包括用于列表名称、字段集合和筛选器的元素。</span><span class="sxs-lookup"><span data-stu-id="7766d-218">The XML includes elements for the list name, the field collection, and the filter.</span></span>  
  
#### <a name="example-1-specified-fields-for-a-list"></a><span data-ttu-id="7766d-219">示例 1。</span><span class="sxs-lookup"><span data-stu-id="7766d-219">Example 1.</span></span> <span data-ttu-id="7766d-220">列表的指定字段</span><span class="sxs-lookup"><span data-stu-id="7766d-220">Specified fields for a list</span></span>  
 <span data-ttu-id="7766d-221">下面的示例演示一个格式正确的 SharePoint 查询：</span><span class="sxs-lookup"><span data-stu-id="7766d-221">The following example shows a well-formed SharePoint query:</span></span>  
  
```  
<RSSharePointList>  
<listName>MyList</listName>  
<viewFields>  
  <FieldRef Name="Field1"/>  
  <FieldRef Name="Field4"/>  
</viewFields>  
<Query>  
  <Where>  
    <And>  
      <Gt>  
        <FieldRef Name="Field1"/>  
        <Value Type="Integer">1</Value>  
      </Gt>  
      <IsNotNull>  
        <FieldRef Name="Field2"/>  
        <Value Type="string"/>  
      </IsNotNull>   
    </And>  
  </Where>  
</Query>  
</RSSharePointList>  
```  
  
 <span data-ttu-id="7766d-222">您可以编辑此查询的视图，只要它保持格式正确的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="7766d-222">You can edit this view of the query as long as it remains well-formed XML text.</span></span>  
  
#### <a name="example-2-all-fields-for-a-list"></a><span data-ttu-id="7766d-223">示例 2。</span><span class="sxs-lookup"><span data-stu-id="7766d-223">Example 2.</span></span> <span data-ttu-id="7766d-224">列表的所有字段</span><span class="sxs-lookup"><span data-stu-id="7766d-224">All fields for a list</span></span>  
 <span data-ttu-id="7766d-225">您还可以仅指定列表的名称，包括隐藏字段在内的所有字段都将返回。</span><span class="sxs-lookup"><span data-stu-id="7766d-225">You can also specify only the name of a list, and all fields, including hidden fields, are returned.</span></span> <span data-ttu-id="7766d-226">下面的示例从名为 Tasks 的列表中检索所有字段：</span><span class="sxs-lookup"><span data-stu-id="7766d-226">The following example retrieves all the fields from a list that is named Tasks:</span></span>  
  
```  
<RSSharePointList>  
<listName>Tasks</listName>  
</RSSharePointList>  
```  
  
 <span data-ttu-id="7766d-227">在查询结果中返回 Tasks 列表的所有字段。</span><span class="sxs-lookup"><span data-stu-id="7766d-227">All fields for the list Tasks are returned in the query results.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="7766d-228">Parameters</span><span class="sxs-lookup"><span data-stu-id="7766d-228">Parameters</span></span>  
 <span data-ttu-id="7766d-229">此数据扩展插件不支持参数。</span><span class="sxs-lookup"><span data-stu-id="7766d-229">Parameters are not supported by this data extension.</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="7766d-230">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="7766d-230">How-To Topics</span></span>  
 <span data-ttu-id="7766d-231">本节包含使用数据连接、数据源和数据集的分步说明。</span><span class="sxs-lookup"><span data-stu-id="7766d-231">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="7766d-232">添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7766d-232">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="7766d-233">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7766d-233">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="7766d-234">向数据集添加筛选器（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7766d-234">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a><span data-ttu-id="7766d-235">相关部分</span><span class="sxs-lookup"><span data-stu-id="7766d-235">Related Sections</span></span>  
 <span data-ttu-id="7766d-236">文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。</span><span class="sxs-lookup"><span data-stu-id="7766d-236">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="7766d-237">将数据添加到报表 &#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7766d-237">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="7766d-238">提供访问报表数据的概述。</span><span class="sxs-lookup"><span data-stu-id="7766d-238">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="7766d-239">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="7766d-239">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="7766d-240">提供有关数据连接和数据源的信息。</span><span class="sxs-lookup"><span data-stu-id="7766d-240">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="7766d-241">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7766d-241">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="7766d-242">提供有关嵌入数据集和共享数据集的信息。</span><span class="sxs-lookup"><span data-stu-id="7766d-242">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="7766d-243">数据集字段集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7766d-243">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="7766d-244">提供有关查询生成的数据集字段集合的信息。</span><span class="sxs-lookup"><span data-stu-id="7766d-244">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="7766d-245">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [联机丛书](https://go.microsoft.com/fwlink/?linkid=121312)中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 文档中的 [Reporting Services 支持的数据源 (SSRS) ](../create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="7766d-245">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="7766d-246">提供有关每个数据扩展插件的平台和版本支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7766d-246">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="7766d-247">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7766d-247">See Also</span></span>  
 <span data-ttu-id="7766d-248">[报表参数 &#40;报表生成器和报表设计器&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7766d-248">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="7766d-249">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7766d-249">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7766d-250">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="7766d-250">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
