---
title: 在 Reporting Services 数据源中存储凭据 | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fccf8669d1f39d19a26b443ffcead8e86db66a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588924"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a><span data-ttu-id="3b6e7-102">在 Reporting Services 数据源中存储凭据</span><span class="sxs-lookup"><span data-stu-id="3b6e7-102">Store Credentials in a Reporting Services Data Source</span></span>
  <span data-ttu-id="3b6e7-103">可以配置存储的凭据， [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 报表服务器可使用这些凭据来访问报表的外部数据。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-103">You can configure stored credentials that a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server uses to access external data for a report.</span></span> <span data-ttu-id="3b6e7-104">如果报表在无人参与的状态下运行，则使用存储凭据，例如将报表作为电子邮件发布的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 订阅。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-104">Stored credentials are used if the report runs unattended, for example a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription that publishes a report as an e-mail.</span></span> <span data-ttu-id="3b6e7-105">计划或触发报表处理时，报表服务器将检索和使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-105">The report server retrieves and uses the credentials when report processing is scheduled or triggered.</span></span> <span data-ttu-id="3b6e7-106">本主题向你说明了为本机模式下和 SharePoint 模式下的报表服务器配置存储凭据的过程。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-106">This topic walks you through configuring stored credentials for both Native mode and SharePoint mode report servers.</span></span>

||
|-|
|<span data-ttu-id="3b6e7-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="3b6e7-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="3b6e7-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="3b6e7-108">**In this topic:**</span></span>

-   [<span data-ttu-id="3b6e7-109">为特定于报表的数据源配置存储的凭据 (纯模式) </span><span class="sxs-lookup"><span data-stu-id="3b6e7-109">Configure stored credentials for a report-specific data source (Native mode)</span></span>](#bkmk_stored_credentials_data_source_native)

-   [<span data-ttu-id="3b6e7-110">为特定于报表的数据源配置存储的凭据（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="3b6e7-110">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_data_source_sharepoint)

-   [<span data-ttu-id="3b6e7-111">为共享数据源配置存储的凭据 (纯模式) </span><span class="sxs-lookup"><span data-stu-id="3b6e7-111">Configure stored credentials for a shared data source (Native mode)</span></span>](#bkmk_stored_credentials_shared_data_source_native)

-   [<span data-ttu-id="3b6e7-112">为共享数据源配置存储凭据（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="3b6e7-112">Configure stored credentials for a shared data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="security-policy-requirements-for-stored-credentials"></a><a name="bkmk_top"></a> <span data-ttu-id="3b6e7-113">存储凭据的安全策略要求</span><span class="sxs-lookup"><span data-stu-id="3b6e7-113">Security policy requirements for stored credentials</span></span>
 <span data-ttu-id="3b6e7-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") 要求为报表服务器上的以下其中一项安全策略配置用于存储凭据的帐户。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") It is required that the account you use for stored credentials, is configured for one of the following security policies on the report server.</span></span> <span data-ttu-id="3b6e7-115">建议使用环境要求的最低级别权限来选择策略。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-115">It is recommended you select the policy with the minimum level of permissions you require for your environment.</span></span>

1.  <span data-ttu-id="3b6e7-116">**允许本地登录**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-116">**Allow log on locally**.</span></span> <span data-ttu-id="3b6e7-117">有关详细信息，请参阅 [允许在本地登录](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-117">For more information, see [Allow log on locally](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).</span></span>

2.  <span data-ttu-id="3b6e7-118">**作为批处理作业登录**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-118">**Log on as a batch job**.</span></span> <span data-ttu-id="3b6e7-119">有关详细信息，请参阅 [作为批处理作业登录](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-119">For more information, see [Log on as a batch job](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).</span></span>

3.  <span data-ttu-id="3b6e7-120">有关策略的一般信息，请参阅 [在组策略对象上编辑安全设置](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-120">For general information on policies, see [Edit security settings on a Group Policy object](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-native-mode"></a><a name="bkmk_stored_credentials_data_source_native"></a> <span data-ttu-id="3b6e7-121">为特定于报表的数据源配置存储的凭据（本机模式）</span><span class="sxs-lookup"><span data-stu-id="3b6e7-121">Configure stored credentials for a report-specific data source (Native mode)</span></span>

1.  <span data-ttu-id="3b6e7-122">在本机模式下的报表管理器中，浏览至包含该报表的文件夹。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-122">In Native mode Report Manager, browse to the folder that contains the report.</span></span> <span data-ttu-id="3b6e7-123">单击![报表管理器中 ssrs 项](../media/ssrs-report-manager-item-context-menu.png "ssrs 项目报表管理器中的上下文菜单")的上下文菜单上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-123">Click the item context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items").</span></span>

2.  <span data-ttu-id="3b6e7-124">单击“管理” \*\*\*\* ，然后单击“数据源” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-124">Click **Manage** and then click **Data Sources**.</span></span>

3.  <span data-ttu-id="3b6e7-125">选择 **“自定义数据源”**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-125">Select **A custom data source**.</span></span>

4.  <span data-ttu-id="3b6e7-126">在“数据源类型” \*\*\*\* 列表中，选择处理数据源的数据所用的数据处理扩展。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-126">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="3b6e7-127">对于 "**连接字符串**"，指定 Report Server 用于连接到数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-127">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="3b6e7-128">下面的示例说明了用于连接到数据库的连接字符串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="3b6e7-128">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="3b6e7-129">对于“连接方法” \*\*\*\*，选择“安全存储在报表服务器中的凭据” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-129">For **Connect Using**, select **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="3b6e7-130">键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-130">Type a user name and password.</span></span>

    -   <span data-ttu-id="3b6e7-131">如果帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "在与**数据源建立连接时用作 Windows 凭据"。**</span><span class="sxs-lookup"><span data-stu-id="3b6e7-131">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="3b6e7-132">如果用户名和密码是数据库凭据，请不要选择 **“在与数据源建立连接时用作 Windows 凭据”**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-132">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="3b6e7-133">如果数据库服务器支持模拟或委托，则可以选择 **“与数据源建立连接之后模拟经过身份验证的用户”**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-133">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

8.  <span data-ttu-id="3b6e7-134">单击“**应用**”。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-134">Click **Apply**.</span></span>

     <span data-ttu-id="3b6e7-135">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [适用于存储凭据的安全策略要求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="3b6e7-135">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_data_source_sharepoint"></a><span data-ttu-id="3b6e7-136">在 SharePoint 模式 (为特定于报表的数据源配置存储的凭据) </span><span class="sxs-lookup"><span data-stu-id="3b6e7-136">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="3b6e7-137">浏览到包含该报表的文档库，然后单击打开菜单 ![ssrs 项的文档库上下文菜单](../media/ssrs-sharepoint-item-context-menu.png "ssrs 项的文档库上下文菜单")。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-137">Browse to the document library that contains the report and then click the open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

2.  <span data-ttu-id="3b6e7-138">单击第二个打开菜单 ![ssrs 项的文档库上下文菜单](../media/ssrs-sharepoint-item-context-menu.png "ssrs 项的文档库上下文菜单")，然后单击“管理数据源”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-138">Click second open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click **Manage Data Sources**.</span></span>

3.  <span data-ttu-id="3b6e7-139">单击想要使用存储的凭据进行配置的“自定义” \*\*\*\* 数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-139">Click the name of the **Custom** data source you want to configure with stored credentials.</span></span>

4.  <span data-ttu-id="3b6e7-140">在“数据源类型” \*\*\*\* 列表中，选择处理数据源的数据所用的数据处理扩展。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-140">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="3b6e7-141">对于 "**连接字符串**"，指定 Report Server 用于连接到数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-141">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="3b6e7-142">下面的示例说明了用于连接到数据库的连接字符串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="3b6e7-142">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="3b6e7-143">对于“凭据” \*\*\*\*，选择“存储的凭据” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-143">For **Credentials**, select **Stored Credentials**.</span></span>

7.  <span data-ttu-id="3b6e7-144">键入**用户名**和**密码**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-144">Type a **user name** and **password**.</span></span>

    -   <span data-ttu-id="3b6e7-145">如果帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "在与**数据源建立连接时用作 Windows 凭据"。**</span><span class="sxs-lookup"><span data-stu-id="3b6e7-145">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="3b6e7-146">如果用户名和密码是数据库凭据，请勿选择“用作 Windows 凭据” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-146">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="3b6e7-147">如果数据库服务器支持模拟或委托，则可以选择 "**设置此帐户的执行上下文**"。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-147">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>

8.  <span data-ttu-id="3b6e7-148">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-148">Click **ok**.</span></span>

     <span data-ttu-id="3b6e7-149">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [适用于存储凭据的安全策略要求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="3b6e7-149">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-native-mode"></a><a name="bkmk_stored_credentials_shared_data_source_native"></a> <span data-ttu-id="3b6e7-150">为共享数据源配置存储凭据（本机模式）</span><span class="sxs-lookup"><span data-stu-id="3b6e7-150">Configure stored credentials for a shared data source (Native mode)</span></span>

1.  <span data-ttu-id="3b6e7-151">在本机模式下的报表管理器中，浏览至共享数据源项。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-151">In Native mode Report Manager, browse to the shared data source item.</span></span> <span data-ttu-id="3b6e7-152">![共享数据源图标](../media/hlp-16datasource.png "共享数据源图标")</span><span class="sxs-lookup"><span data-stu-id="3b6e7-152">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="3b6e7-153">单击![报表管理器中 ssrs 项](../media/ssrs-report-manager-item-context-menu.png "ssrs 项目报表管理器中的上下文菜单")的上下文菜单上下文菜单，然后单击 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-153">Click the context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items") and then click **Manage**.</span></span>

3.  <span data-ttu-id="3b6e7-154">在 "**数据源类型**" 列表中，指定用于处理数据源中数据的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-154">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

4.  <span data-ttu-id="3b6e7-155">对于 "**连接字符串**"，指定 Report Server 用于连接到数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-155">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="3b6e7-156">建议您不要在连接字符串中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-156">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="3b6e7-157">下面的示例演示用于连接到本地数据库的连接字符串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="3b6e7-157">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  <span data-ttu-id="3b6e7-158">键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-158">Type a user name and password.</span></span>

    -   <span data-ttu-id="3b6e7-159">如果帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "在与**数据源建立连接时用作 Windows 凭据"。**</span><span class="sxs-lookup"><span data-stu-id="3b6e7-159">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="3b6e7-160">如果用户名和密码是数据库凭据，请不要选择 **“在与数据源建立连接时用作 Windows 凭据”**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-160">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="3b6e7-161">如果数据库服务器支持模拟或委托，则可以选择 **“与数据源建立连接之后模拟经过身份验证的用户”**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-161">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

6.  <span data-ttu-id="3b6e7-162">单击“**应用**”。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-162">Click **Apply**.</span></span>

     <span data-ttu-id="3b6e7-163">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [适用于存储凭据的安全策略要求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="3b6e7-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a><span data-ttu-id="3b6e7-164">在 SharePoint 模式 (为共享数据源配置存储的凭据) </span><span class="sxs-lookup"><span data-stu-id="3b6e7-164">Configure stored credentials for a shared data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="3b6e7-165">在文档库中，浏览到共享数据源项。![共享数据源图标](../media/hlp-16datasource.png "共享数据源图标")</span><span class="sxs-lookup"><span data-stu-id="3b6e7-165">In the document library, browse to the shared data source item.![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="3b6e7-166">单击上下文菜单 ![ssrs 项的文档库上下文菜单](../media/ssrs-sharepoint-item-context-menu.png "ssrs 项的文档库上下文菜单")，然后单击第二个上下文菜单 ![ssrs 项的文档库上下文菜单](../media/ssrs-sharepoint-item-context-menu.png "ssrs 项的文档库上下文菜单")。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-166">Click the context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click the second context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

3.  <span data-ttu-id="3b6e7-167">单击“编辑数据源定义” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-167">Click **Edit Data Source Definition**.</span></span>

4.  <span data-ttu-id="3b6e7-168">在 "**数据源类型**" 列表中，指定用于处理数据源中数据的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-168">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="3b6e7-169">对于 "**连接字符串**"，指定 Report Server 用于连接到数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-169">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="3b6e7-170">建议您不要在连接字符串中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-170">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="3b6e7-171">下面的示例演示用于连接到本地数据库的连接字符串 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="3b6e7-171">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="3b6e7-172">键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-172">Type a user name and password.</span></span>

    -   <span data-ttu-id="3b6e7-173">如果该帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "用作**Windows 凭据"。**</span><span class="sxs-lookup"><span data-stu-id="3b6e7-173">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials.**</span></span>

    -   <span data-ttu-id="3b6e7-174">如果用户名和密码是数据库凭据，请勿选择“用作 Windows 凭据” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-174">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="3b6e7-175">如果数据库服务器支持模拟或委托，则可选择 **Set Execution context to this account**。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-175">If the database server supports impersonation or delegation, you can select **Set Execution context to this account**.</span></span>

7.  <span data-ttu-id="3b6e7-176">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="3b6e7-176">Click **Ok**.</span></span>

     <span data-ttu-id="3b6e7-177">![用于“返回页首”链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [适用于存储凭据的安全策略要求](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="3b6e7-177">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

## <a name="see-also"></a><span data-ttu-id="3b6e7-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b6e7-178">See Also</span></span>
 <span data-ttu-id="3b6e7-179">[为报表数据源指定凭据和连接信息](../../integration-services/connection-manager/data-sources.md) [&#40;报表管理器&#41;](configure-data-source-properties-for-a-report-report-manager.md) [创建、删除或修改共享数据源 &#40;报表管理器](../create-delete-or-modify-a-shared-data-source-report-manager.md) [&#41;&#40;报表管理器](../data-sources-properties-page-report-manager.md)[新建数据源 "页](../new-data-source-page-report-manager.md)&#41;&#40;报表管理器</span><span class="sxs-lookup"><span data-stu-id="3b6e7-179">[Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md) [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [Data Sources Properties Page &#40;Report Manager&#41;](../data-sources-properties-page-report-manager.md) [New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md)</span></span>


