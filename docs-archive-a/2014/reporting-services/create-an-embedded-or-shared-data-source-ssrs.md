---
title: " (SSRS) 创建嵌入数据源或共享数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], creating
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52c5263859ad16ed725065bce4998d08bddaf5f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691124"
---
# <a name="create-an-embedded-or-shared-data-source-ssrs"></a><span data-ttu-id="a0068-102">创建嵌入数据源或共享数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a0068-102">Create an Embedded or Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="a0068-103">报表数据源指定名称和连接信息。</span><span class="sxs-lookup"><span data-stu-id="a0068-103">A report data source specifies a name and connection information.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="a0068-104">支持两种类型的数据源，分别是嵌入数据源和共享数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-104">supports two types of data sources: embedded and shared.</span></span> <span data-ttu-id="a0068-105">嵌入数据源在报表定义中定义并只由该报表使用。</span><span class="sxs-lookup"><span data-stu-id="a0068-105">An embedded data source is defined in a report definition and used only by that report.</span></span> <span data-ttu-id="a0068-106">共享数据源被定义为一个单独项并可由多个报表使用。</span><span class="sxs-lookup"><span data-stu-id="a0068-106">A shared data source is defined as a separate item and can be used by multiple reports.</span></span> <span data-ttu-id="a0068-107">有关详细信息，请参阅[嵌入和共享的数据连接或数据源 &#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a0068-107">For more information, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="a0068-108">在报表生成器中，浏览到报表服务器或 SharePoint 站点并选择数据源，或者创建嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-108">In Report Builder, you browse to the report server or SharePoint site and select data sources or create embedded data sources.</span></span> <span data-ttu-id="a0068-109">不能在报表生成器中创建共享数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-109">You cannot create shared data sources in Report Builder.</span></span>  
  
 <span data-ttu-id="a0068-110">在报表设计器中，可以创建共享数据源或嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-110">In Report Designer, you can create shared or embedded data sources.</span></span> <span data-ttu-id="a0068-111">从 "报表数据" 窗格中，开始创建数据源引用，然后选择**新**选项。</span><span class="sxs-lookup"><span data-stu-id="a0068-111">From the Report Data pane, begin to create a data source reference, and then select the **New** option.</span></span> <span data-ttu-id="a0068-112">在您创建数据源引用后，新的共享数据源将自动添加到解决方案资源管理器中的“共享数据源”文件夹下。</span><span class="sxs-lookup"><span data-stu-id="a0068-112">After you create the data source reference, a new shared data source will automatically be added to Solution Explorer under the Shared Data Sources folder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="a0068-113">您还可以直接在报表服务器或 SharePoint 站点上创建共享数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-113">You can also create shared data sources directly on a report server or SharePoint site.</span></span> <span data-ttu-id="a0068-114">有关详细信息，请参阅[创建、删除或修改共享数据源 &#40;报表管理器&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)或[&#40;Reporting Services&#41;SharePoint 集成模式下创建和管理共享数据](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)源。</span><span class="sxs-lookup"><span data-stu-id="a0068-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) or [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-an-embedded-or-shared-data-source"></a><span data-ttu-id="a0068-115">创建嵌入数据源或共享数据源</span><span class="sxs-lookup"><span data-stu-id="a0068-115">To create an embedded or shared data source</span></span>  
  
1.  <span data-ttu-id="a0068-116">在 "报表数据" 窗格的工具栏上，单击 "**新建**"，然后单击 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="a0068-116">On the toolbar in the Report Data pane, click **New** and then click **Data Source**.</span></span> <span data-ttu-id="a0068-117">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0068-117">The **Data Source Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0068-118"> 如果“报表数据”窗格不可见，请单击 **“视图”** 菜单上的 **“报表数据”** 。</span><span class="sxs-lookup"><span data-stu-id="a0068-118">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="a0068-119">在 **“名称”** 文本框中，键入数据源的名称，或接受默认值。</span><span class="sxs-lookup"><span data-stu-id="a0068-119">In the **Name** text box, type a name for the data source or accept the default.</span></span> <span data-ttu-id="a0068-120">此数据源名称在报表内部使用。</span><span class="sxs-lookup"><span data-stu-id="a0068-120">The data source name is used internally within the report.</span></span> <span data-ttu-id="a0068-121">为便于识别，建议数据源名称包含在连接字符串中指定的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="a0068-121">For clarity, we recommend that the name of the data source contain the name of the database specified in the connection string.</span></span>  
  
3.  <span data-ttu-id="a0068-122">对于嵌入数据源，请验证是否已选中 "**嵌入连接**"。</span><span class="sxs-lookup"><span data-stu-id="a0068-122">For an embedded data source, verify that **Embedded connection** is selected.</span></span>  
  
    1.  <span data-ttu-id="a0068-123">从“类型”下拉列表中，选择一个数据源类型，例如“Microsoft SQL Server”或“OLE DB”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0068-123">From the **Type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="a0068-124">采用以下备选方案之一指定连接字符串：</span><span class="sxs-lookup"><span data-stu-id="a0068-124">Specify a connection string using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="a0068-125">直接在 **“连接字符串”** 文本框中键入连接字符串。</span><span class="sxs-lookup"><span data-stu-id="a0068-125">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="a0068-126">有关示例连接字符串的列表，请参阅[数据连接、数据源和连接字符串（在](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)Reporting Services 中报表生成器或[数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)中）。</span><span class="sxs-lookup"><span data-stu-id="a0068-126">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
    -   <span data-ttu-id="a0068-127">单击表达式 (**fx** ) 按钮创建计算结果为连接字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="a0068-127">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="a0068-128">在 **“表达式”** 对话框的“表达式”窗格中，键入该表达式。</span><span class="sxs-lookup"><span data-stu-id="a0068-128">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="a0068-129">单击 **“编辑”** 打开在步骤 2 中选择的数据源类型的 **“连接属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0068-129">Click **Edit** to open the **Connection Properties** dialog box for the data source type you chose in step 2.</span></span>  
  
         <span data-ttu-id="a0068-130">根据需要，在 **“连接属性”** 对话框中为该数据源类型填写字段。</span><span class="sxs-lookup"><span data-stu-id="a0068-130">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="a0068-131">连接属性包括数据源的类型、名称以及要使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="a0068-131">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="a0068-132">在此对话框中指定值之后，单击 **“测试连接”** 以确保该数据源可用并且指定的凭据是正确的。</span><span class="sxs-lookup"><span data-stu-id="a0068-132">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span> <span data-ttu-id="a0068-133">有关特定数据源类型的详细信息，请参阅[从外部数据源中添加数据 (SSRS)](report-data/add-data-from-external-data-sources-ssrs.md) 中的主题。</span><span class="sxs-lookup"><span data-stu-id="a0068-133">For more information about specific data source types, see topics in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="a0068-134">对于共享数据源，验证是否选择了 "**使用共享数据源引用**"。</span><span class="sxs-lookup"><span data-stu-id="a0068-134">For a shared data source, verify that **Use shared data source reference** is selected.</span></span>  
  
    1.  <span data-ttu-id="a0068-135">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="a0068-135">Click **New**.</span></span> <span data-ttu-id="a0068-136">在 **“共享数据源属性”** 对话框中，执行步骤 2 和 3 创建新数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-136">In the **Shared Data Source** properties dialog box, follow steps 2 and 3 to create a new data source.</span></span>  
  
    2.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
         <span data-ttu-id="a0068-137">解决方案资源管理器的“共享数据源”文件夹中将显示新的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-137">The new shared data source appears in the Shared Data Sources folder in Solution Explorer.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="a0068-138">数据源将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="a0068-138">The data source appears in the Report Data pane.</span></span> <span data-ttu-id="a0068-139">在“报表数据”窗格中，一个共享数据源将指向数据源定义。</span><span class="sxs-lookup"><span data-stu-id="a0068-139">In the Report Data pane, a shared data source points to the data source definition.</span></span> <span data-ttu-id="a0068-140">在报表生成器中，数据源定义位于报表服务器或 SharePoint 站点上。</span><span class="sxs-lookup"><span data-stu-id="a0068-140">In Report Builder, the data source definition is on a report server or SharePoint site.</span></span> <span data-ttu-id="a0068-141">在报表设计器中，数据源定义是解决方案资源管理器中“共享数据源”文件夹下的一个文件。</span><span class="sxs-lookup"><span data-stu-id="a0068-141">In Report Designer, the data source definition is a file in Solution Explorer under the Shared Data Sources folder.</span></span>  
  
### <a name="to-import-an-existing-data-source-in-report-designer"></a><span data-ttu-id="a0068-142">在报表设计器中导入现有数据源</span><span class="sxs-lookup"><span data-stu-id="a0068-142">To import an existing data source in Report Designer</span></span>  
  
1.  <span data-ttu-id="a0068-143">在解决方案资源管理器中，右键单击报表服务器项目中的“共享数据源”\*\*\*\* 文件夹，然后单击“添加现有项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0068-143">In Solution Explorer, right-click the **Shared Data Sources** folder in the report server project, and then click **Add Existing Item**.</span></span> <span data-ttu-id="a0068-144">此时将打开 **“添加现有项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0068-144">The **Add Existing Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a0068-145">导航到一个现有报表定义共享数据源 (rds) 文件，然后单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a0068-145">Navigate to an existing Report Definition Shared data source (rds) file and then click **Open**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-convert-an-embedded-data-source-to-a-shared-data-source-in-report-designer"></a><span data-ttu-id="a0068-146">在报表设计器中将嵌入数据源转换为共享数据源</span><span class="sxs-lookup"><span data-stu-id="a0068-146">To convert an embedded data source to a shared data source in Report Designer</span></span>  
  
-   <span data-ttu-id="a0068-147">在 "报表数据" 窗格中，右键单击数据源，然后单击 "**转换为共享数据源**"。</span><span class="sxs-lookup"><span data-stu-id="a0068-147">In the Report Data pane, right-click the data source and then click **Convert to Shared Data Source**.</span></span>  
  
### <a name="to-convert-a-shared-data-source-to-an-embedded-data-source-in-report-builder"></a><span data-ttu-id="a0068-148">在报表生成器中将共享数据源转换为嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="a0068-148">To convert a shared data source to an embedded data source in Report Builder</span></span>  
  
-   <span data-ttu-id="a0068-149">在 "报表数据" 窗格中，右键单击数据源并打开 "**数据源属性**"。</span><span class="sxs-lookup"><span data-stu-id="a0068-149">In the Report Data pane, right-click the data source and open **Data Source Properties**.</span></span>  
  
-   <span data-ttu-id="a0068-150">单击 "**嵌入连接**"，然后按照前面的过程中所述完成创建嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="a0068-150">Click **Embedded Connection** and finish creating the embedded data source as described in an earlier procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0068-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0068-151">See Also</span></span>  
 <span data-ttu-id="a0068-152">[在 Reporting Services 数据源中存储凭据](report-data/store-credentials-in-a-reporting-services-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="a0068-152">[Store Credentials in a Reporting Services Data Source](report-data/store-credentials-in-a-reporting-services-data-source.md) </span></span>  
 <span data-ttu-id="a0068-153">[嵌入和共享的数据连接或数据源 &#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a0068-153">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a0068-154">[将嵌入数据源转换为共享 &#40;报表生成器和 SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a0068-154">[Convert a Data Source from Embedded to Shared &#40;Report Builder and SSRS&#41;](report-data/convert-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a0068-155">[将报表或模型绑定到共享数据源 &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a0068-155">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="a0068-156">[配置报表的数据源属性 &#40;报表管理器&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a0068-156">[Configure Data Source Properties for a Report  &#40;Report Manager&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md) </span></span>  
 [<span data-ttu-id="a0068-157">Reporting Services 支持的数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a0068-157">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
