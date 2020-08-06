---
title: 配置报表的数据源属性（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42969b4667dd71e4c6413f38e4deadb96491169c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578652"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a><span data-ttu-id="d8ee9-102">配置报表的数据源属性（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="d8ee9-102">Configure Data Source Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="d8ee9-103">在运行报表时，报表服务器检索属性信息以确定如何连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-103">When you run a report, the report server retrieves property information to determine how to connect to a data source.</span></span> <span data-ttu-id="d8ee9-104">数据源类型、连接字符串和凭据信息在已发布报表的“数据源”属性页中指定。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-104">The data source type, connection string, and credential information are specified in the Data Source property pages of the published report.</span></span> <span data-ttu-id="d8ee9-105">可以设置这些属性以使数据源连接信息与创建报表时指定的原始值不同。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-105">You can set the properties to vary the data source connection information from the original values that were specified when the report was created.</span></span>  
  
 <span data-ttu-id="d8ee9-106">另外，如果具有已指定了要使用的连接信息的预定义共享数据源，则可以改为指定共享数据源。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-106">Alternatively, if you have a predefined shared data source that already specifies the connection information you want to use, you can specify a shared data source instead.</span></span> <span data-ttu-id="d8ee9-107">若要使用共享数据源，请单击报表的“数据源属性”页上的 **“共享数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-107">To use a shared data source, click **A shared data source** on the Data Source properties page of the report.</span></span>  
  
### <a name="to-configure-an-embedded-data-source"></a><span data-ttu-id="d8ee9-108">配置嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="d8ee9-108">To configure an embedded data source</span></span>  
  
1.  <span data-ttu-id="d8ee9-109">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="d8ee9-110">在报表管理器中，导航到 "**内容**" 页。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-110">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="d8ee9-111">导航到要配置报表特定数据源的报表，然后打开该报表。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-111">Navigate to the report that you want to configure a report-specific data source for, and open the report.</span></span>  
  
3.  <span data-ttu-id="d8ee9-112">单击 "**属性**" 选项卡。此时将打开 "**常规**属性" 页。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-112">Click the **Properties** tab. The **General** properties page opens.</span></span>  
  
4.  <span data-ttu-id="d8ee9-113">单击 "**数据源**" 选项卡。这会打开报表的 "数据源属性" 页。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-113">Click the **Data Sources** tab. This opens the Data Source properties page of the report.</span></span>  
  
5.  <span data-ttu-id="d8ee9-114">单击 **“自定义数据源”** 以指定报表内的数据源连接信息。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-114">Click **A custom data source** to specify data source connection information within the report.</span></span>  
  
6.  <span data-ttu-id="d8ee9-115">在 **“连接类型”** 列表中，指定用于处理来自数据源的数据的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-115">In the **Connection Type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="d8ee9-116">对于 "**连接字符串**"，指定 Report Server 用于连接到数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-116">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="d8ee9-117">建议您不要在连接字符串中指定凭据。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-117">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="d8ee9-118">下面的示例演示用于连接到本地数据库的连接字符串 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="d8ee9-118">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="d8ee9-119">对于 **“连接方式”**，请指定在报表运行时获取凭据的方式：</span><span class="sxs-lookup"><span data-stu-id="d8ee9-119">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="d8ee9-120">如果希望提示用户输入登录名和密码，请单击 **“运行该报表的用户提供的凭据”**。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-120">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span>  
  
    -   <span data-ttu-id="d8ee9-121">如果希望将数据源与支持订阅或其他计划操作（如自动生成报表历史记录）的报表一起使用，请单击“安全存储在报表服务器中的凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-121">If you intend to use the data source with reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span>  
  
    -   <span data-ttu-id="d8ee9-122">如果希望报表服务器将访问报表的用户的凭据传递给承载外部数据源的服务器，请单击 **“Windows 集成安全性”**。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-122">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="d8ee9-123">在这种情况下，系统不会提示用户键入用户名或密码。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-123">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="d8ee9-124">如果数据源不使用凭据（例如，如果数据源是通过文件系统访问的 XML 文件），请单击“不需要凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-124">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="d8ee9-125">仅当此凭据类型对于相应数据源有效时，才能指定它。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-125">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="d8ee9-126">如果为要求身份验证的数据源选择此选项，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-126">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="d8ee9-127">如果选择此选项，请确保配置无人参与的执行帐户，以便在用户凭据不可用时，报表服务器可连接到其他计算机以检索数据或文件。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-127">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
 <span data-ttu-id="d8ee9-128">有关配置凭据的详细信息，请参阅 [指定报表数据源的凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-128">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="d8ee9-129">有关无人参与的执行帐户的详细信息，请参阅[配置无人参与的执行帐户（SSRS 配置管理器）](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ee9-129">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ee9-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8ee9-130">See Also</span></span>  
 <span data-ttu-id="d8ee9-131">["内容" 页 &#40;报表管理器&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8ee9-131">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="d8ee9-132">[新数据源页 &#40;报表管理器&#41;](../new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8ee9-132">[New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md) </span></span>  
 <span data-ttu-id="d8ee9-133">[创建、修改和删除共享数据源 &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8ee9-133">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="d8ee9-134">[管理报表数据源](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="d8ee9-134">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="d8ee9-135">[创建、删除或修改共享数据源 &#40;报表管理器&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8ee9-135">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 [<span data-ttu-id="d8ee9-136">“数据源”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="d8ee9-136">Data Sources Properties Page &#40;Report Manager&#41;</span></span>](../data-sources-properties-page-report-manager.md)  
  
  
