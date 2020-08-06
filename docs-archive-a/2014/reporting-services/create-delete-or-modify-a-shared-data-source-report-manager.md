---
title: 创建、删除或修改共享数据源 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6f4ff658e656b159995087df3121806b462e687
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587250"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a><span data-ttu-id="8feb3-102">创建、删除或修改共享数据源（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="8feb3-102">Create, Delete, or Modify a Shared Data Source (Report Manager)</span></span>
  <span data-ttu-id="8feb3-103">共享数据源指定数据源的连接属性。</span><span class="sxs-lookup"><span data-stu-id="8feb3-103">A shared data source specifies connection properties for a data source.</span></span> <span data-ttu-id="8feb3-104">如果数据源供大量的报表、模型或数据驱动订阅使用，则可考虑创建共享数据源，以消除必须在多个位置维护相同连接信息的开销。</span><span class="sxs-lookup"><span data-stu-id="8feb3-104">If you have a data source that is used by a large number of reports, models, or data-driven subscriptions, consider creating a shared data source to eliminate the overhead of having to maintain the same connection information in multiple places.</span></span>  
  
 <span data-ttu-id="8feb3-105">下面的图标表示报表管理器文件夹层次结构中的共享数据源：</span><span class="sxs-lookup"><span data-stu-id="8feb3-105">The following icon indicates a shared data source in the Report Manager folder hierarchy:</span></span>  
  
 <span data-ttu-id="8feb3-106">![共享数据源图标](media/hlp-16datasource.png "共享数据源图标")</span><span class="sxs-lookup"><span data-stu-id="8feb3-106">![Shared data source icon](media/hlp-16datasource.png "Shared data source icon")</span></span>  
<span data-ttu-id="8feb3-107">共享数据源图标</span><span class="sxs-lookup"><span data-stu-id="8feb3-107">shared data source icon</span></span>  
  
### <a name="to-create-a-shared-data-source"></a><span data-ttu-id="8feb3-108">创建共享数据源</span><span class="sxs-lookup"><span data-stu-id="8feb3-108">To create a shared data source</span></span>  
  
1.  <span data-ttu-id="8feb3-109">启动 [报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8feb3-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="8feb3-110">在报表管理器中，导航到 "**内容**" 页。</span><span class="sxs-lookup"><span data-stu-id="8feb3-110">In Report Manager, navigate to the **Contents** page.</span></span>  
  
3.  <span data-ttu-id="8feb3-111">单击 **“新建数据源”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-111">Click **New Data Source**.</span></span> <span data-ttu-id="8feb3-112">此时，将打开 **“新建数据源”** 页。</span><span class="sxs-lookup"><span data-stu-id="8feb3-112">The **New Data Source** page opens.</span></span>  
  
4.  <span data-ttu-id="8feb3-113">为相应项键入一个名称。</span><span class="sxs-lookup"><span data-stu-id="8feb3-113">Type a name for the item.</span></span> <span data-ttu-id="8feb3-114">名称必须包含至少一个字符并且必须以字母开头。</span><span class="sxs-lookup"><span data-stu-id="8feb3-114">A name must contain at least one character and it must start with a letter.</span></span> <span data-ttu-id="8feb3-115">它也可以包括特定的一些符号，但不能包括空格或以下字符：; ?</span><span class="sxs-lookup"><span data-stu-id="8feb3-115">It can also include certain symbols, but not spaces or the characters ; ?</span></span> <span data-ttu-id="8feb3-116">： \@ & = +，$/\* \< > |" /.</span><span class="sxs-lookup"><span data-stu-id="8feb3-116">: \@ & = + , $ / \* \< > | " /.</span></span>  
  
5.  <span data-ttu-id="8feb3-117">根据需要，可以键入说明，向用户提供相关的连接信息。</span><span class="sxs-lookup"><span data-stu-id="8feb3-117">Optionally type a description to provide users with information about the connection.</span></span> <span data-ttu-id="8feb3-118">此说明将显示在报表管理器的 **“内容”** 页中。</span><span class="sxs-lookup"><span data-stu-id="8feb3-118">This description will appear on the **Contents** page in Report Manager.</span></span>  
  
6.  <span data-ttu-id="8feb3-119">在 **“数据源类型”** 列表中，指定用于处理来自数据源的数据的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="8feb3-119">In the **Data source type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="8feb3-120">对于 **“连接字符串”**，指定报表服务器用于连接数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="8feb3-120">For **Connection string**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="8feb3-121">建议您不要在连接字符串中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="8feb3-121">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="8feb3-122">下面的示例演示用于连接到本地数据库的连接字符串 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="8feb3-122">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="8feb3-123">对于 **“连接方式”**，请指定在报表运行时获取凭据的方式：</span><span class="sxs-lookup"><span data-stu-id="8feb3-123">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="8feb3-124">如果希望提示用户输入登录名和密码，请单击 **“运行该报表的用户提供的凭据”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-124">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span> <span data-ttu-id="8feb3-125">若要将用户输入的凭据作为 Windows 凭据，请单击 **“在与数据源建立连接时用作 Windows 凭据”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-125">To use the credentials that the user enters as Windows credentials, click **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="8feb3-126">如果用户名和密码是数据库凭据，则不选择此选项。</span><span class="sxs-lookup"><span data-stu-id="8feb3-126">If the user name and password are database credentials, do not select this option.</span></span>  
  
    -   <span data-ttu-id="8feb3-127">如果要将该数据源用作共享数据源以及使用由数据源所有者管理的已保存凭据，或者将该数据源用于支持订阅或其他计划操作（例如自动生成报表历史记录）的报表，请单击“安全存储在报表服务器中的凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8feb3-127">If you intend to use the data source as a shared data source with saved credentials that are managed by the owner of the data source, or for reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span> <span data-ttu-id="8feb3-128">如果数据库服务器支持模拟或委托，则可以选择 **“与数据源建立连接之后模拟经过身份验证的用户”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-128">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>  
  
    -   <span data-ttu-id="8feb3-129">如果希望报表服务器将访问报表的用户的凭据传递给承载外部数据源的服务器，请单击 **“Windows 集成安全性”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-129">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="8feb3-130">在这种情况下，系统不会提示用户键入用户名或密码。</span><span class="sxs-lookup"><span data-stu-id="8feb3-130">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="8feb3-131">如果数据源不使用凭据（例如，如果数据源是通过文件系统访问的 XML 文件），请单击“不需要凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8feb3-131">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="8feb3-132">仅当此凭据类型对于相应数据源有效时，才能指定它。</span><span class="sxs-lookup"><span data-stu-id="8feb3-132">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="8feb3-133">如果为要求身份验证的数据源选择此选项，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="8feb3-133">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="8feb3-134">如果选择此选项，请确保配置无人参与的执行帐户，以便在用户凭据不可用时，报表服务器可连接到其他计算机以检索数据或文件。</span><span class="sxs-lookup"><span data-stu-id="8feb3-134">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
     <span data-ttu-id="8feb3-135">有关配置凭据的详细信息，请参阅 [指定报表数据源的凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="8feb3-135">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="8feb3-136">有关无人参与的执行帐户的详细信息，请参阅[配置无人参与的执行帐户（SSRS 配置管理器）](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="8feb3-136">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
9. <span data-ttu-id="8feb3-137">单击 **“测试连接”** 按钮可验证数据源配置。</span><span class="sxs-lookup"><span data-stu-id="8feb3-137">Click the **Test Connection** button to validate the data source configuration.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8feb3-138">对于 XML 数据源类型，不支持“测试连接”按钮。</span><span class="sxs-lookup"><span data-stu-id="8feb3-138">The Test Connection button is not supported for the XML data source type.</span></span>  
  
10. <span data-ttu-id="8feb3-139">单击 **“确定”**</span><span class="sxs-lookup"><span data-stu-id="8feb3-139">Click **OK**</span></span>  
  
### <a name="to-modify-a-shared-data-source"></a><span data-ttu-id="8feb3-140">修改共享数据源</span><span class="sxs-lookup"><span data-stu-id="8feb3-140">To modify a shared data source</span></span>  
  
1.  <span data-ttu-id="8feb3-141">在报表管理器中，导航到“内容”页。</span><span class="sxs-lookup"><span data-stu-id="8feb3-141">In Report Manager, navigate to the Contents page.</span></span>  
  
2.  <span data-ttu-id="8feb3-142">导航到共享数据源项，悬停在该项上，单击下拉列表，然后从上下文菜单中单击“管理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8feb3-142">Navigate to the shared data source item, hover over the item, click the drop-down list, and from the context menu, click **Manage**.</span></span> <span data-ttu-id="8feb3-143">**“属性”** 页将打开。</span><span class="sxs-lookup"><span data-stu-id="8feb3-143">The **Properties** page opens.</span></span>  
  
3.  <span data-ttu-id="8feb3-144">修改数据源，再单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-144">Modify the data source, and then click **Apply**.</span></span>  
  
### <a name="to-delete-a-shared-data-source"></a><span data-ttu-id="8feb3-145">删除共享数据源</span><span class="sxs-lookup"><span data-stu-id="8feb3-145">To delete a shared data source</span></span>  
  
-   <span data-ttu-id="8feb3-146">在报表管理器中，导航到 **“内容”** 页，再执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="8feb3-146">In Report Manager, navigate to the **Contents** page and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8feb3-147">导航到共享数据源项。</span><span class="sxs-lookup"><span data-stu-id="8feb3-147">Navigate to the shared data source item.</span></span>  
  
         <span data-ttu-id="8feb3-148">单击该项将其打开。</span><span class="sxs-lookup"><span data-stu-id="8feb3-148">Click the item to open it.</span></span> <span data-ttu-id="8feb3-149">此时将打开“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="8feb3-149">The General Properties page opens.</span></span>  
  
         <span data-ttu-id="8feb3-150">单击 **“删除”**，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="8feb3-150">Click **Delete**, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="8feb3-151">在 **“内容”** 页中，导航到要删除的数据源所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8feb3-151">In the **Contents** page, navigate to the folder that contains the data source you want to delete.</span></span>  
  
         <span data-ttu-id="8feb3-152">悬停在该项上，单击下拉列表，然后从上下文菜单中单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8feb3-152">Hover over the item, click the drop-down list, and from the context menu, click **Delete**.</span></span>  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8feb3-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8feb3-153">See Also</span></span>  
 <span data-ttu-id="8feb3-154">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8feb3-154">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="8feb3-155">["内容" 页 &#40;报表管理器&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8feb3-155">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="8feb3-156">[创建、修改和删除共享数据源 &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8feb3-156">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="8feb3-157">[管理报表数据源](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="8feb3-157">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="8feb3-158">配置报表的数据源属性（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="8feb3-158">Configure Data Source Properties for a Report  &#40;Report Manager&#41;</span></span>](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
