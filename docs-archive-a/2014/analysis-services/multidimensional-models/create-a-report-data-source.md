---
title: 创建报表数据源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd6662c7-ffbe-479d-8944-3dc858340998
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9205eac497fc047b471f5b80becec36495474d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691961"
---
# <a name="create-a-report-data-source"></a><span data-ttu-id="64bdd-102">创建报表数据源</span><span class="sxs-lookup"><span data-stu-id="64bdd-102">Create a Report Data Source</span></span>
  <span data-ttu-id="64bdd-103">为了 Power View 可连接到多维模型，您必须在 SharePoint 库中创建一个共享的报表数据源定义（也称为 .rsds 文件）。</span><span class="sxs-lookup"><span data-stu-id="64bdd-103">In order for Power View to connect to a multidimensional model, you must create a shared report data source definition, also known as an .rsds file, in a SharePoint library.</span></span> <span data-ttu-id="64bdd-104">该 .rsds 文件指定用于连接到多维模型的 Analysis Services 服务器实例、连接类型、连接字符串以及凭据的名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-104">The .rsds file specifies the name of an Analysis Services server instance, connection type, connection string, and credentials used to connect to the multidimensional model.</span></span> <span data-ttu-id="64bdd-105">当用户单击 .rsds 时，将在浏览器中打开新的空白 Power View 报表（.rdlx 文件）。</span><span class="sxs-lookup"><span data-stu-id="64bdd-105">When a user clicks on the .rsds, a new blank Power View report (an .rdlx file) opens in the browser.</span></span>  
  
 <span data-ttu-id="64bdd-106">为了创建 .rsds 连接，您必须安装了 SQL Server 2012（或更高版本）Reporting Services 和用于 SharePoint 2010 或 SharePoint 2013 的 Reporting Services 外接程序。</span><span class="sxs-lookup"><span data-stu-id="64bdd-106">In order to create an .rsds connection, you must have SQL Server 2012 (or later) Reporting Services and the Reporting Services add-in for SharePoint 2010 or SharePoint 2013 installed.</span></span>  
  
## <a name="create-a-report-data-source-rsds-connection-to-a-multidimensional-model"></a><span data-ttu-id="64bdd-107">创建到多维模型的报表数据源 (.rsds) 连接</span><span class="sxs-lookup"><span data-stu-id="64bdd-107">Create a Report Data Source (.rsds) connection to a multidimensional model</span></span>  
 <span data-ttu-id="64bdd-108">在开始之前，您需要知道：</span><span class="sxs-lookup"><span data-stu-id="64bdd-108">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="64bdd-109">在多维模式下运行的 Analysis Services 服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-109">The name of the Analysis Services server instance running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="64bdd-110">要连接到的多维数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-110">The name of the multidimensional database you want to connect to.</span></span>  
  
-   <span data-ttu-id="64bdd-111">多维数据集的名称（如果存在多个多维数据集）。</span><span class="sxs-lookup"><span data-stu-id="64bdd-111">The name of the cube, if there is more than one.</span></span>  
  
-   <span data-ttu-id="64bdd-112">（可选）透视名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-112">(Optional) Perspective name.</span></span>  
  
-   <span data-ttu-id="64bdd-113">（可选）区域设置标识符。</span><span class="sxs-lookup"><span data-stu-id="64bdd-113">(Optional) Locale Identifier.</span></span>  
  
#### <a name="to-create-a-shared-report-data-source-rsds-file-sharepoint-2010"></a><span data-ttu-id="64bdd-114">创建共享报表数据源 (.rsds) 文件 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="64bdd-114">To create a shared Report Data Source (.rsds) file (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="64bdd-115">在库功能区上单击 **“文档”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="64bdd-115">Click the **Documents** tab on the library ribbon.</span></span>  
  
2.  <span data-ttu-id="64bdd-116">单击 "**新建文档**" "  >  **报表数据源**"。</span><span class="sxs-lookup"><span data-stu-id="64bdd-116">Click **New Document** > **Report Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64bdd-117">如果在菜单上没有看到 **“报表数据源”** 项，说明尚未启用此库的报表数据源内容类型。</span><span class="sxs-lookup"><span data-stu-id="64bdd-117">If you do not see the **Report Data Source** item on the menu, the report data source content type has not been enabled for this library.</span></span> <span data-ttu-id="64bdd-118">有关详细信息，请参阅[将报表服务器内容类型添加到库 &#40;Reporting Services 在 SharePoint 集成模式下&#41;" ](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="64bdd-118">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
3.  <span data-ttu-id="64bdd-119">在 **“数据源属性”** 页上，在 **“名称”** 中键入连接 .rsds 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-119">On the **Data Source Properties** page, in **Name**, type a name for the connection .rsds file.</span></span>  
  
4.  <span data-ttu-id="64bdd-120">在 **“数据源类型”** 中，选择 **“Power View 的 Microsoft BI 语义模型”**。</span><span class="sxs-lookup"><span data-stu-id="64bdd-120">In **Data Source Type**, select **Microsoft BI Semantic Model for Power View**.</span></span>  
  
5.  <span data-ttu-id="64bdd-121">在 **“连接字符串”** 中，指定 Analysis Services 服务器名称、数据库名称、多维数据集名称和所有可选设置。</span><span class="sxs-lookup"><span data-stu-id="64bdd-121">In **Connection String**, specify the Analysis Services server name, database name, cube name, and any optional settings.</span></span>  
  
     <span data-ttu-id="64bdd-122">连接字符串： `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span><span class="sxs-lookup"><span data-stu-id="64bdd-122">Connection String: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64bdd-123">如果有多个多维数据集，必须指定多维数据集名称。</span><span class="sxs-lookup"><span data-stu-id="64bdd-123">If there is more than one cube, you must specify a cube name.</span></span>  
  
     <span data-ttu-id="64bdd-124">（可选）多维数据集可以有透视，这些透视为用户提供一个选择视图，其中在客户端上只能看到某些维度和/或度量值组。</span><span class="sxs-lookup"><span data-stu-id="64bdd-124">(Optional) Cubes can have perspectives that provide users a select view where only certain dimensions and/or measure groups are visible in the client.</span></span> <span data-ttu-id="64bdd-125">若要指定透视，请输入透视名称作为 Cube 属性的值： `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span><span class="sxs-lookup"><span data-stu-id="64bdd-125">To specify a perspective, enter the perspective name as a value to the Cube property: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span></span>  
  
     <span data-ttu-id="64bdd-126">（可选）多维数据集可以具有为模型内各种语言指定的元数据和数据翻译。</span><span class="sxs-lookup"><span data-stu-id="64bdd-126">(Optional) Cubes can have metadata and data translations specified for various languages within the model.</span></span> <span data-ttu-id="64bdd-127">若要查看 (数据和元数据的翻译) 需要将 "区域设置标识符" 属性添加到连接字符串：`Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span><span class="sxs-lookup"><span data-stu-id="64bdd-127">In order to see the translations (data and metadata) you need to add the "Locale Identifier" property to the connection string: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span></span>  
  
6.  <span data-ttu-id="64bdd-128">在 **“凭据”** 中，指定报表服务器如何获取访问外部数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="64bdd-128">In **Credentials**, specify how the report server obtains credentials to access the external data source.</span></span>  
  
    -   <span data-ttu-id="64bdd-129">若要使用打开报表的用户凭据访问数据，请选择“Windows 身份验证(集成)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64bdd-129">Select **Windows authentication (integrated)** if you want to access the data using the credentials of the user who opened the report.</span></span> <span data-ttu-id="64bdd-130">如果 SharePoint 站点或场使用窗体身份验证或通过可信帐户连接至报表服务器，请不要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="64bdd-130">Do not select this option if the SharePoint site or farm uses forms authentication or connects to the report server through a trusted account.</span></span> <span data-ttu-id="64bdd-131">若要为此报表计划订阅或数据处理，请不要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="64bdd-131">Do not select this option if you want to schedule subscription or data processing for this report.</span></span> <span data-ttu-id="64bdd-132">如果您的域启用了 Kerberos 身份验证或者数据源与报表服务器位于同一台计算机上，则此选项最为有效。</span><span class="sxs-lookup"><span data-stu-id="64bdd-132">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="64bdd-133">如果未启用 Kerberos 身份验证，则只能将 Windows 凭据传递到另一台计算机。</span><span class="sxs-lookup"><span data-stu-id="64bdd-133">If Kerberos authentication is not enabled, Windows credentials can only be passed to one other computer.</span></span> <span data-ttu-id="64bdd-134">也就是说，如果外部数据源位于需要另行连接的其他计算机上，则会出现错误而不会获得期望的数据。</span><span class="sxs-lookup"><span data-stu-id="64bdd-134">This means that if the external data source is on another computer, requiring an additional connection, you will get an error instead of the data you expect.</span></span>  
  
    -   <span data-ttu-id="64bdd-135">若要使用户在每次运行报表时都输入其凭据，请选择 **“凭据提示”** 。</span><span class="sxs-lookup"><span data-stu-id="64bdd-135">Select **Prompt for credentials** if you want the user to enter his or her credentials each time he or she runs the report.</span></span> <span data-ttu-id="64bdd-136">若要为此报表计划订阅或数据处理，请不要选择此选项。</span><span class="sxs-lookup"><span data-stu-id="64bdd-136">Do not select this option if you want to schedule subscription or data processing for this report.</span></span>  
  
    -   <span data-ttu-id="64bdd-137">若要使用一组凭据访问数据，请选择 **“已存储凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="64bdd-137">Select **Stored credentials** if you want to access the data using a single set of credentials.</span></span> <span data-ttu-id="64bdd-138">凭据在存储之前是加密的。</span><span class="sxs-lookup"><span data-stu-id="64bdd-138">The credentials are encrypted before they are stored.</span></span> <span data-ttu-id="64bdd-139">您可以选择用于确定如何对已存储凭据进行身份验证的选项。</span><span class="sxs-lookup"><span data-stu-id="64bdd-139">You can select options that determine how the stored credentials are authenticated.</span></span> <span data-ttu-id="64bdd-140">如果已存储的凭据属于 Windows 用户帐户，请选择“用作 Windows 凭据”。</span><span class="sxs-lookup"><span data-stu-id="64bdd-140">Select Use as Windows credentials if the stored credentials belong to a Windows user account.</span></span> <span data-ttu-id="64bdd-141">如果要设置数据库服务器的执行上下文，请选择 **“设置此帐户的执行上下文”** 。</span><span class="sxs-lookup"><span data-stu-id="64bdd-141">Select **Set execution context to this account** if you want to set the execution context on the database server.</span></span>  
  
    -   <span data-ttu-id="64bdd-142">如果在连接字符串中指定凭据，或者如果要使用最低特权帐户运行报表，请选择“不需要提供凭据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64bdd-142">Select **Credentials are not required** if you specify credentials in the connection string, or if you want to run the report using a least-privilege account.</span></span>  
  
7.  <span data-ttu-id="64bdd-143">单击 **“测试连接”** 以进行验证。</span><span class="sxs-lookup"><span data-stu-id="64bdd-143">Click **Test Connection** to validate.</span></span>  
  
8.  <span data-ttu-id="64bdd-144">如果您想要数据源处于活动状态，则选择 **“启用此数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="64bdd-144">Select **Enable this data source** if you want the data source to be active.</span></span> <span data-ttu-id="64bdd-145">如果配置了数据源但该数据源未处于活动状态，则在用户尝试创建报表时，将会收到错误消息。</span><span class="sxs-lookup"><span data-stu-id="64bdd-145">If the data source is configured but not active, users will receive an error message when they attempt to create a report.</span></span>  
  
  
