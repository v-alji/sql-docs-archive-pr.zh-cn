---
title: 从 SharePoint 站点更新报表数据源的凭据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 923fee5656ed6032201fb4276fcca75be799e42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577303"
---
# <a name="update-credentials-in-report-data-sources-from-a-sharepoint-site"></a><span data-ttu-id="4b98f-102">从 SharePoint 站点更新报表数据源的凭据</span><span class="sxs-lookup"><span data-stu-id="4b98f-102">Update Credentials in Report Data Sources from a SharePoint Site</span></span>
  <span data-ttu-id="4b98f-103">本主题介绍如何更新报表中嵌入的数据源和保存在 SharePoint 文档库中的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="4b98f-103">This topic describes how to update data sources embedded in reports and shared data sources that are saved in a SharePoint document library.</span></span>  
  
 <span data-ttu-id="4b98f-104">许多报表可能包含数据源或使用配置为使用 Windows 身份验证的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="4b98f-104">Many of your reports might include data sources or use shared data sources that are configured to use Windows Authentication.</span></span> <span data-ttu-id="4b98f-105">在某些情况下（如在保存到 SharePoint 文档库的报表上创建数据警报），您需要将数据源凭据更新到存储的凭据或不需要凭据。</span><span class="sxs-lookup"><span data-stu-id="4b98f-105">Under some circumstances, such as creating data alerts on reports saved to a SharePoint document library, you need to update the data source credentials to stored credentials or require no credentials.</span></span>  
  
 <span data-ttu-id="4b98f-106">若要在报表中使用存储的凭据，您可能会决定创建并使用一个新的 SQL Server 登录名。</span><span class="sxs-lookup"><span data-stu-id="4b98f-106">To use stored credentials in reports, you might decide to create and use a new SQL Server login.</span></span> <span data-ttu-id="4b98f-107">有关详细信息，请参阅 [创建登录名](../../relational-databases/security/authentication-access/create-a-login.md)。</span><span class="sxs-lookup"><span data-stu-id="4b98f-107">For more information, see [Create a Login](../../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
### <a name="to-update-an-embedded-data-source-to-use-stored-credentials"></a><span data-ttu-id="4b98f-108">更新嵌入的数据源以使用存储的凭据</span><span class="sxs-lookup"><span data-stu-id="4b98f-108">To update an embedded data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="4b98f-109">转到保存该报表的 SharePoint 文档库。</span><span class="sxs-lookup"><span data-stu-id="4b98f-109">Go to the SharePoint document library where you saved the report.</span></span>  
  
2.  <span data-ttu-id="4b98f-110">单击针对该报表展开下拉菜单的图标，然后单击“管理数据源”  。</span><span class="sxs-lookup"><span data-stu-id="4b98f-110">Click the icon for the expand drop-down menu on the report and then click **Manage Data Sources**.</span></span>  
  
     <span data-ttu-id="4b98f-111">此时将打开“管理数据源”页。</span><span class="sxs-lookup"><span data-stu-id="4b98f-111">The Manage Data Sources page opens.</span></span>  
  
3.  <span data-ttu-id="4b98f-112">在 **“名称”** 列中，单击该数据源。</span><span class="sxs-lookup"><span data-stu-id="4b98f-112">In the **Name** column, click the data source.</span></span>  
  
4.  <span data-ttu-id="4b98f-113">针对 **“连接类型”** ，确认已选中 **“自定义数据源”** 选项。</span><span class="sxs-lookup"><span data-stu-id="4b98f-113">For **Connection Type** verify that the **Custom data source** option is selected.</span></span>  
  
     <span data-ttu-id="4b98f-114">此选项指示数据源嵌入在报表中。</span><span class="sxs-lookup"><span data-stu-id="4b98f-114">This option indicates that the data source is embedded in the report.</span></span>  
  
5.  <span data-ttu-id="4b98f-115">保留 **“数据源类型”** 和 **“连接字符串”** 选项不变，除非您要将报表连接到其他类型的数据源、其他服务器或数据存储区。</span><span class="sxs-lookup"><span data-stu-id="4b98f-115">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the report to connect to different type of data source, a different server, or data store.</span></span>  
  
6.  <span data-ttu-id="4b98f-116">对于 **“凭据”** ，请选择 **“存储的凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-116">For **Credentials**, select **Stored credentials**.</span></span> <span data-ttu-id="4b98f-117">仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="4b98f-117">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="4b98f-118">**“不需要凭据”** 选项也可以在某些情况下使用。</span><span class="sxs-lookup"><span data-stu-id="4b98f-118">The **Credentials are not required** option can also be used under some circumstances.</span></span>  
  
     <span data-ttu-id="4b98f-119">对于某些数据源类型，必须在报表服务器上配置无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="4b98f-119">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="4b98f-120">有关详细信息，请参阅[从外部数据源中添加数据 (SSRS)](add-data-from-external-data-sources-ssrs.md)和[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)中相应的数据源类型的主题。</span><span class="sxs-lookup"><span data-stu-id="4b98f-120">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
7.  <span data-ttu-id="4b98f-121">键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4b98f-121">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="4b98f-122">如果帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "在与**数据源建立连接时用作 Windows 凭据**"。</span><span class="sxs-lookup"><span data-stu-id="4b98f-122">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source**.</span></span>  
  
    -   <span data-ttu-id="4b98f-123">如果用户名和密码是数据库凭据，请不要选择 **“在与数据源建立连接时用作 Windows 凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-123">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="4b98f-124">如果数据库服务器支持模拟或委托，则可选择 **“设置此帐户的执行上下文”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-124">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
8.  <span data-ttu-id="4b98f-125">若要验证数据源是否可以使用更新的凭据进行连接，请单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-125">To verify the data source can connect by using the updated credentials, click **Test connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-update-a-shared-data-source-to-use-stored-credentials"></a><span data-ttu-id="4b98f-126">更新共享的数据源以使用存储的凭据</span><span class="sxs-lookup"><span data-stu-id="4b98f-126">To update a shared data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="4b98f-127">转到保存共享数据源的 SharePoint 文档库。</span><span class="sxs-lookup"><span data-stu-id="4b98f-127">Go to the SharePoint document library where you saved the shared data source.</span></span>  
  
2.  <span data-ttu-id="4b98f-128">单击针对共享数据源展开下拉菜单的图标，然后单击“编辑数据源定义”  。</span><span class="sxs-lookup"><span data-stu-id="4b98f-128">Click the icon for the expand drop-down menu on shared data source, and then click **Edit Data Source Definition**.</span></span>  
  
     <span data-ttu-id="4b98f-129">将打开“数据源”页。</span><span class="sxs-lookup"><span data-stu-id="4b98f-129">The Data Source page opens.</span></span>  
  
3.  <span data-ttu-id="4b98f-130">保留 **“数据源类型”** 和 **“连接字符串”** 选项不变，除非您要将共享数据源连接到其他类型的数据源、其他服务器或数据存储区。</span><span class="sxs-lookup"><span data-stu-id="4b98f-130">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the shared data source to connect to different type of data source, a different server, or data store.</span></span>  
  
4.  <span data-ttu-id="4b98f-131">对于 **“凭据”** ，请选择 **“存储的凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-131">For **Credentials**, select **Stored credentials**.</span></span>  
  
     <span data-ttu-id="4b98f-132">**“不需要凭据”** 选项也可以在某些情况下使用。</span><span class="sxs-lookup"><span data-stu-id="4b98f-132">The **Credentials are not required** option can also be used under some circumstances.</span></span> <span data-ttu-id="4b98f-133">仅当数据源不接受凭据，或者要通过其他方式传递凭据时，才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="4b98f-133">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="4b98f-134">对于某些数据源类型，必须在报表服务器上配置无人参与的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="4b98f-134">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="4b98f-135">有关详细信息，请参阅[从外部数据源中添加数据 (SSRS)](add-data-from-external-data-sources-ssrs.md)和[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)中相应的数据源类型的主题。</span><span class="sxs-lookup"><span data-stu-id="4b98f-135">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="4b98f-136">键入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4b98f-136">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="4b98f-137">如果帐户是 Windows 域用户帐户，请按以下格式指定该帐户： \<domain> \\<帐户 \> ，然后选择 "在与**数据源建立连接时用作 Windows 凭据"。**</span><span class="sxs-lookup"><span data-stu-id="4b98f-137">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>  
  
    -   <span data-ttu-id="4b98f-138">如果用户名和密码是数据库凭据，请不要选择 **“在与数据源建立连接时用作 Windows 凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-138">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="4b98f-139">如果数据库服务器支持模拟或委托，则可选择 **“设置此帐户的执行上下文”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-139">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
6.  <span data-ttu-id="4b98f-140">若要验证数据源是否可以使用更新的凭据进行连接，请单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="4b98f-140">To verify the data source can connect using the updated credentials, **Test connection**.</span></span>  
  
7.  <span data-ttu-id="4b98f-141">验证是否选择了启用此数据源。</span><span class="sxs-lookup"><span data-stu-id="4b98f-141">Verify that Enable this data source is selected.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b98f-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b98f-142">See Also</span></span>  
 [<span data-ttu-id="4b98f-143">将文档上传到 SharePoint 库（SharePoint 模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="4b98f-143">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
  
