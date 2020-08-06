---
title: 教程：创建钻取报表和主报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7168c8d3-cef5-4c4a-a0bf-fff1ac5b8b71
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7d30b59a0c5523ed50df06f8587bbd701ae4c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692215"
---
# <a name="tutorial-creating-drillthrough-and-main-reports-report-builder"></a><span data-ttu-id="ba903-102">教程：创建钻取报表和主报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="ba903-102">Tutorial: Creating Drillthrough and Main Reports (Report Builder)</span></span>
  <span data-ttu-id="ba903-103">本教程教您如何创建两种报表：钻取报表和主报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-103">This tutorial teaches you how to create two kinds of reports: a drillthrough report and a main report.</span></span> <span data-ttu-id="ba903-104">这些报表中使用的示例销售数据可从 Analysis Services 多维数据集检索。</span><span class="sxs-lookup"><span data-stu-id="ba903-104">The sample sales data used in these reports is retrieved from an Analysis Services cube.</span></span> <span data-ttu-id="ba903-105">下图显示了将创建的报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-105">The following illustration shows the reports you will create.</span></span>  
  
 <span data-ttu-id="ba903-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span><span class="sxs-lookup"><span data-stu-id="ba903-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span></span>  
  
 <span data-ttu-id="ba903-107">下图显示了主报表中的字段值 "游戏和玩具" 如何在钻取报表的标题中显示。</span><span class="sxs-lookup"><span data-stu-id="ba903-107">The following illustration shows how the field value, Games and Toys, in the main report displays in the drillthrough report's title.</span></span> <span data-ttu-id="ba903-108">钻取报表中的数据与“游戏和玩具”产品类别有关。</span><span class="sxs-lookup"><span data-stu-id="ba903-108">The data in the drillthrough pertains to the Games and Toys product category.</span></span>  
  
 <span data-ttu-id="ba903-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span><span class="sxs-lookup"><span data-stu-id="ba903-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="ba903-110">学习内容</span><span class="sxs-lookup"><span data-stu-id="ba903-110">What You Will Learn</span></span>  
 <span data-ttu-id="ba903-111">**在钻取报表中，您将学习如何：**</span><span class="sxs-lookup"><span data-stu-id="ba903-111">**In the drillthrough report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="ba903-112">使用表或矩阵向导创建钻取矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="ba903-112">Create a Drillthrough Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#DMatrixAndDataset)  
  
    1.  [<span data-ttu-id="ba903-113">指定数据连接</span><span class="sxs-lookup"><span data-stu-id="ba903-113">Specify a Data Connection</span></span>](#DConnection)  
  
    2.  [<span data-ttu-id="ba903-114">创建 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="ba903-114">Create an MDX Query</span></span>](#DMDXQuery)  
  
    3.  [<span data-ttu-id="ba903-115">按组样式组织数据</span><span class="sxs-lookup"><span data-stu-id="ba903-115">Organize Data into Groups Style</span></span>](#DLayout)  
  
    4.  [<span data-ttu-id="ba903-116">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-116">Add Subtotals and Totals</span></span>](#DTotals)  
  
    5.  [<span data-ttu-id="ba903-117">选择样式</span><span class="sxs-lookup"><span data-stu-id="ba903-117">Choose a Style</span></span>](#DStyle)  
  
2.  [<span data-ttu-id="ba903-118">将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="ba903-118">Format Data as Currency</span></span>](#DFormat)  
  
3.  [<span data-ttu-id="ba903-119">添加用于在迷你图中显示销售值的列</span><span class="sxs-lookup"><span data-stu-id="ba903-119">Add columns to Show Sales Values in Sparklines</span></span>](#DSparkline)  
  
4.  [<span data-ttu-id="ba903-120">添加包含产品类别名称的报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-120">Add Report Title with Product Category Name</span></span>](#DReportTitle)  
  
5.  [<span data-ttu-id="ba903-121">更新参数属性</span><span class="sxs-lookup"><span data-stu-id="ba903-121">Update Parameter Properties</span></span>](#DParameter)  
  
6.  [<span data-ttu-id="ba903-122">将报表保存到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="ba903-122">Save the Report to a SharePoint Library</span></span>](#DSave)  
  
 <span data-ttu-id="ba903-123">**在主报表中，您将学习如何：**</span><span class="sxs-lookup"><span data-stu-id="ba903-123">**In the main report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="ba903-124">使用表或矩阵向导创建主矩阵报表和数据集</span><span class="sxs-lookup"><span data-stu-id="ba903-124">Create the Main Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#MMatrixAndDataset)  
  
    1.  [<span data-ttu-id="ba903-125">指定数据连接</span><span class="sxs-lookup"><span data-stu-id="ba903-125">Specify a Data Connection</span></span>](#MConnection)  
  
    2.  [<span data-ttu-id="ba903-126">创建 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="ba903-126">Create an MDX Query</span></span>](#MMDXQuery)  
  
    3.  [<span data-ttu-id="ba903-127">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="ba903-127">Organize Data into Groups</span></span>](#MLayout)  
  
    4.  [<span data-ttu-id="ba903-128">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-128">Add Subtotals and Totals</span></span>](#MTotals)  
  
    5.  [<span data-ttu-id="ba903-129">选择样式</span><span class="sxs-lookup"><span data-stu-id="ba903-129">Choose a Style</span></span>](#MStyle)  
  
2.  [<span data-ttu-id="ba903-130">删除总计行</span><span class="sxs-lookup"><span data-stu-id="ba903-130">Remove the Grand Total Row</span></span>](#MGrandTotal)  
  
3.  [<span data-ttu-id="ba903-131">配置用于钻取的文本框操作</span><span class="sxs-lookup"><span data-stu-id="ba903-131">Configure Text Box Action for Drillthrough</span></span>](#MDrillthrough)  
  
4.  [<span data-ttu-id="ba903-132">使用指示器替换数值</span><span class="sxs-lookup"><span data-stu-id="ba903-132">Replace Numeric Values with Indicators</span></span>](#MIndicators)  
  
5.  [<span data-ttu-id="ba903-133">更新参数属性</span><span class="sxs-lookup"><span data-stu-id="ba903-133">Update Parameter Properties</span></span>](#MParameter)  
  
6.  [<span data-ttu-id="ba903-134">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-134">Add a Report Title</span></span>](#MTitle)  
  
7.  [<span data-ttu-id="ba903-135">将报表保存到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="ba903-135">Save the Report to a SharePoint Library</span></span>](#MSave)  
  
8.  [<span data-ttu-id="ba903-136">运行主报表和钻取报表</span><span class="sxs-lookup"><span data-stu-id="ba903-136">Run the Main and Drillthrough Reports</span></span>](#MRunReports)  
  
 <span data-ttu-id="ba903-137">本教程的预计学时：30 分钟。</span><span class="sxs-lookup"><span data-stu-id="ba903-137">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba903-138">要求</span><span class="sxs-lookup"><span data-stu-id="ba903-138">Requirements</span></span>  
 <span data-ttu-id="ba903-139">本教程需要访问 Contoso Sales 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-139">This tutorial requires access to the Contoso Sales cube.</span></span> <span data-ttu-id="ba903-140">此要求同样适用于钻取报表和主报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-140">This requirement applies to both the drillthrough and the main reports.</span></span> <span data-ttu-id="ba903-141">有关要求的详细信息，请参阅[教程先决条件（报表生成器）](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="ba903-141">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-drillthrough-report-from-the-table-or-matrix-wizard"></a><a name="DMatrixAndDataset"></a><span data-ttu-id="ba903-142">1. 使用表或矩阵向导创建钻取报表</span><span class="sxs-lookup"><span data-stu-id="ba903-142">1. Create a Drillthrough Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="ba903-143">使用“表或矩阵向导”从“入门”对话框创建一个矩阵报表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-143">From the Getting Started dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span> <span data-ttu-id="ba903-144">该向导提供两种模式：报表设计模式和共享数据集设计模式。</span><span class="sxs-lookup"><span data-stu-id="ba903-144">There are two modes available in the wizard: report design and shared dataset design.</span></span> <span data-ttu-id="ba903-145">在本教程中，您将使用报表设计模式。</span><span class="sxs-lookup"><span data-stu-id="ba903-145">In this tutorial, you will use the report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="ba903-146">创建新的报表</span><span class="sxs-lookup"><span data-stu-id="ba903-146">To create a new report</span></span>  
  
1.  <span data-ttu-id="ba903-147">单击 "**开始**"，指向 "**程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] "**报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="ba903-147">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="ba903-148">随即将打开“入门”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="ba903-148">The **Getting Started** dialog box opens.</span></span> <span data-ttu-id="ba903-149">如果未显示，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="ba903-149">If it does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="ba903-150">在左窗格中，确认已选中 **“新建报表”** 。</span><span class="sxs-lookup"><span data-stu-id="ba903-150">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="ba903-151">在右窗格中，确认已选中“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-151">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="DConnection"></a><span data-ttu-id="ba903-152">1a.</span><span class="sxs-lookup"><span data-stu-id="ba903-152">1a.</span></span> <span data-ttu-id="ba903-153">指定数据连接</span><span class="sxs-lookup"><span data-stu-id="ba903-153">Specify a Data Connection</span></span>  
 <span data-ttu-id="ba903-154">数据连接包含连接到外部数据源（如 Analysis Services 多维数据集或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库）所需的信息。</span><span class="sxs-lookup"><span data-stu-id="ba903-154">A data connection contains the information necessary to connect to an external data source such as an Analysis Services cube or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="ba903-155">若要指定数据连接，可以从报表服务器使用共享数据源或创建仅在此报表中使用的嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="ba903-155">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span> <span data-ttu-id="ba903-156">在本教程中，您将使用嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="ba903-156">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="ba903-157">若要了解有关使用共享数据源的详细信息，请参阅[获取数据连接的备选方式（报表生成器）](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ba903-157">To learn more about using a shared data source, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="ba903-158">创建嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="ba903-158">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="ba903-159">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-159">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="ba903-160">将打开“选择数据源的连接”\*\*\*\* 页面。</span><span class="sxs-lookup"><span data-stu-id="ba903-160">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="ba903-161">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="ba903-161">Click **New**.</span></span> <span data-ttu-id="ba903-162">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ba903-162">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ba903-163">在“名称”中，键入“Online and Reseller Sales Detail”作为数据源的名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-163">In **Name**, type **Online and Reseller Sales Detail** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="ba903-164">在“选择连接类型”中，选择“Microsoft SQL Server Analysis Services”，然后单击“生成”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-164">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="ba903-165">在“数据源”\*\*\*\* 中，确认数据源是“Microsoft SQL Server Analysis Services (AdomdClient)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-165">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="ba903-166">在“服务器名称”中，键入安装 Analysis Services 实例所在服务器的名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-166">In **Server name**, type the name of a server where an instance of Analysis Services is installed.</span></span>  
  
7.  <span data-ttu-id="ba903-167">在“选择或输入数据库名称”\*\*\*\* 中，选择 Contoso 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-167">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="ba903-168">确认“连接字符串”包含以下语法\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="ba903-168">Verify that **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
     <span data-ttu-id="ba903-169">`<servername>` 是安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services 的实例名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-169">The `<servername>` is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with Analysis Services installed.</span></span>  
  
10. <span data-ttu-id="ba903-170">单击“凭据类型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-170">Click **Credentials type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-171">您可能需要更改默认身份验证选项，具体取决于在数据源上配置权限的方式。</span><span class="sxs-lookup"><span data-stu-id="ba903-171">Depending on how permissions are configured on the data source, you might need to change the default authentication options.</span></span> <span data-ttu-id="ba903-172">有关详细信息，请参阅 [安全性（报表生成器）](report-builder/security-report-builder.md)中所创建的移动报表中使用。</span><span class="sxs-lookup"><span data-stu-id="ba903-172">For more information, see [Security &#40;Report Builder&#41;](report-builder/security-report-builder.md).</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="ba903-173">将显示“选择数据源的连接”\*\*\*\* 页面。</span><span class="sxs-lookup"><span data-stu-id="ba903-173">The **Choose a connection to a data source** page appears.</span></span>  
  
12. <span data-ttu-id="ba903-174">若要验证是否能连接到数据源，请单击“测试连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-174">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="ba903-175">将显示消息“已成功地创建连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-175">The message **Connection created successfully** appears.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="ba903-176">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-176">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="DMDXQuery"></a><span data-ttu-id="ba903-177">1b.</span><span class="sxs-lookup"><span data-stu-id="ba903-177">1b.</span></span> <span data-ttu-id="ba903-178">创建 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="ba903-178">Create an MDX Query</span></span>  
 <span data-ttu-id="ba903-179">在报表中，可以使用具有预定义查询的共享数据集，也可以创建仅在报表中使用的嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-179">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="ba903-180">在本教程中，将创建一个嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-180">In this tutorial, you will create an embedded dataset.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="ba903-181">创建查询筛选器</span><span class="sxs-lookup"><span data-stu-id="ba903-181">To create query filters</span></span>  
  
1.  <span data-ttu-id="ba903-182">在 "**设计查询**" 页上的 "元数据" 窗格中，单击按钮 " \*\* ( ..." ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-182">On the **Design a query** page, in the Metadata pane, click the button **(...)**.</span></span>  
  
2.  <span data-ttu-id="ba903-183">在“选择多维数据集”\*\*\*\* 对话框中，依次单击“Sales”和“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-183">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ba903-184">如果不想手动生成 MDX 查询，请单击 ![切换到设计模式](media/rsqdicon-designmode.gif "切换到设计模式") 图标，将查询设计器切换到“查询”模式，将已完成的 MDX 粘贴到查询设计器，然后继续执行 [创建数据集](#DSkip)中的步骤 6。</span><span class="sxs-lookup"><span data-stu-id="ba903-184">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 6 in [To create the dataset](#DSkip).</span></span>  
  
    ```  
    SELECT NON EMPTY { [Measures].[Sales Amount], [Measures].[Sales Return Amount] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS * [Product].[Product Subcategory Name].[Product Subcategory Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
    ```  
  
3.  <span data-ttu-id="ba903-185">在“度量值组”窗格中，展开“Channel”，然后将“Channel Name”拖到筛选器窗格中的“层次结构”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="ba903-185">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="ba903-186">维度名称“Channel”会自动添加到“维度”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-186">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="ba903-187">不要更改“维度”或“运算符”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-187">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="ba903-188">若要打开“筛选表达式”列表，请单击“筛选表达式”列中的向下箭头\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-188">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="ba903-189">在筛选表达式列表中，展开“所有渠道”，依次单击“在线”、“分销商”和“确定”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-189">In the filter expression list, expand **All Channel**, click **Online**, click **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-190">查询现在包含一个筛选器以只包括这些渠道：“在线”和“分销商”。</span><span class="sxs-lookup"><span data-stu-id="ba903-190">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="ba903-191">展开“Sales Territory”维度，然后将“Sales Territory Group”拖到“层次结构”列（在“Channel Name”下面）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-191">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column (below **Channel Name**).</span></span>  
  
7.  <span data-ttu-id="ba903-192">打开“筛选表达式”列表，展开“所有销售区域”，单击“北美洲”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-192">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-193">查询现在具有一个筛选器以只包括北美洲的销售额。</span><span class="sxs-lookup"><span data-stu-id="ba903-193">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="ba903-194">在“度量值组”窗格中，展开“Date”，然后将“Calendar Year”拖到筛选器窗格中的“层次结构”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-194">In the Measure Group pane, expand Date, and then drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="ba903-195">维度名称“Date”会自动添加到“维度”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-195">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="ba903-196">不要更改“维度”或“运算符”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-196">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="ba903-197">若要打开“筛选表达式”列表，请单击“筛选表达式”列中的向下箭头\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-197">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="ba903-198">在筛选表达式列表中，展开“所有日期”，单击“2009 年”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-198">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-199">查询现在具有一个筛选器以只包括日历 2009 年的销售额。</span><span class="sxs-lookup"><span data-stu-id="ba903-199">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="ba903-200">创建参数</span><span class="sxs-lookup"><span data-stu-id="ba903-200">To create the parameter</span></span>  
  
1.  <span data-ttu-id="ba903-201">展开“Product”维度，然后将“Product Category Name”成员拖到“Calendar Year”下面的“层次结构”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-201">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Calendar Year**.</span></span>  
  
2.  <span data-ttu-id="ba903-202">打开“筛选表达式”列表，单击“所有产品”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-202">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ba903-203">单击“参数”复选框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-203">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="ba903-204">查询现在包含参数 ProductProductCategoryName。</span><span class="sxs-lookup"><span data-stu-id="ba903-204">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-205">该参数包含产品类别的名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-205">The parameter contains the names of product categories.</span></span> <span data-ttu-id="ba903-206">单击主报表中的产品类别名称时，通过使用此参数将它的名称传递给钻取报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-206">When you click a product category name in the main report, its name is passed to the drillthrough report by using this parameter.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="DSkip"></a><span data-ttu-id="ba903-207">创建数据集</span><span class="sxs-lookup"><span data-stu-id="ba903-207">To create the dataset</span></span>  
  
1.  <span data-ttu-id="ba903-208">从“Channel”维度将“Channel Name”拖到数据窗格。</span><span class="sxs-lookup"><span data-stu-id="ba903-208">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="ba903-209">从“Product”维度将“Product Category Name”拖到数据窗格，然后将它放到“Channel Name”的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-209">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="ba903-210">从“Product”维度将“Product Subcategory Name”拖到数据窗格，然后将它放到“Product Category Name”的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-210">From the Product dimension, drag Product Subcategory Name to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="ba903-211">在“元数据”窗格中，展开“度量值”，然后展开“Sales”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-211">In the Metadata pane, expand **Measure**, and then expand Sales.</span></span>  
  
5.  <span data-ttu-id="ba903-212">将“Sales Amount”度量值拖到数据窗格，然后将它放到“Product Subcategory Name”的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-212">Drag the Sales Amount measure to the data pane, and then place it to the right of Product Subcategory Name.</span></span>  
  
6.  <span data-ttu-id="ba903-213">在查询设计器工具栏上，单击 "\*\*运行 (！ ) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="ba903-213">On the query designer toolbar, click **Run (!)**.</span></span>  
  
7.  <span data-ttu-id="ba903-214">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-214">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="DLayout"></a><span data-ttu-id="ba903-215">1c.</span><span class="sxs-lookup"><span data-stu-id="ba903-215">1c.</span></span> <span data-ttu-id="ba903-216">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="ba903-216">Organize Data into Groups</span></span>  
 <span data-ttu-id="ba903-217">在选择要对数据分组的字段时，可以设计一个矩阵，其中的行和列显示了详细数据和聚合数据。</span><span class="sxs-lookup"><span data-stu-id="ba903-217">When you select the fields on which to group the data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="ba903-218">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="ba903-218">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="ba903-219">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-219">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-220">在“排列字段”页上，将“Product_Subcategory_Name”拖到“行组”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-220">On the **Arrange fields** page, drag Product_Subcategory_Name to **Row groups**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-221">用下划线 (_) 来替代名称中的空格。</span><span class="sxs-lookup"><span data-stu-id="ba903-221">The spaces in the names are replaced with underscores (_).</span></span> <span data-ttu-id="ba903-222">例如，“Product Category Name”为“Product_Category_Name”。</span><span class="sxs-lookup"><span data-stu-id="ba903-222">For example Product Category Name is Product_Category_Name.</span></span>  
  
3.  <span data-ttu-id="ba903-223">将 Channel_Name 拖到“列组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-223">Drag Channel_Name to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="ba903-224">将“Sales_Amount”拖到“值”中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-224">Drag Sales_Amount to **Values**.</span></span>  
  
     <span data-ttu-id="ba903-225">“Sales_Amount”由 Sum 函数（即数值字段的默认聚合函数）自动聚合。</span><span class="sxs-lookup"><span data-stu-id="ba903-225">Sales_Amount is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="ba903-226">值为 `[Sum(Sales_Amount)]`。</span><span class="sxs-lookup"><span data-stu-id="ba903-226">The value is `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="ba903-227">若要查看其他可用聚合函数，请打开下拉列表（不要更改聚合函数）。</span><span class="sxs-lookup"><span data-stu-id="ba903-227">To view the other aggregate functions available, open the drop-down list (do not change the aggregate function).</span></span>  
  
5.  <span data-ttu-id="ba903-228">将“Sales_Return_Amount”拖到“值”中，然后将它放到“`[Sum(Sales_Amount)]`”下面\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-228">Drag Sales_Return_Amount to **Values**, and then place it below `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="ba903-229">步骤 4 和 5 指定要在矩阵中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ba903-229">Steps 4 and 5 specify the data to display in the matrix.</span></span>  
  
6.  <span data-ttu-id="ba903-230">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-230">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="DTotals"></a><span data-ttu-id="ba903-231">1d.</span><span class="sxs-lookup"><span data-stu-id="ba903-231">1d.</span></span> <span data-ttu-id="ba903-232">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-232">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="ba903-233">创建组后，可以添加用于显示字段的聚合值的行并设置其格式。</span><span class="sxs-lookup"><span data-stu-id="ba903-233">After you create groups, you can add and format rows where the aggregate values for the fields will display.</span></span> <span data-ttu-id="ba903-234">还可以选择是显示所有数据还是允许用户以交互方式展开和折叠已分组数据。</span><span class="sxs-lookup"><span data-stu-id="ba903-234">You can also choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="ba903-235">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-235">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="ba903-236">在“选择布局”页的“选项”下，确认已选择“显示小计和总计”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-236">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="ba903-237">向导的“预览”窗格将显示包含四行的矩阵。</span><span class="sxs-lookup"><span data-stu-id="ba903-237">The wizard Preview pane displays a matrix with four rows.</span></span>  
  
2.  <span data-ttu-id="ba903-238">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-238">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="DStyle"></a><span data-ttu-id="ba903-239">1e.</span><span class="sxs-lookup"><span data-stu-id="ba903-239">1e.</span></span> <span data-ttu-id="ba903-240">选择样式</span><span class="sxs-lookup"><span data-stu-id="ba903-240">Choose a Style</span></span>  
 <span data-ttu-id="ba903-241">样式指定字形、颜色集和边框样式。</span><span class="sxs-lookup"><span data-stu-id="ba903-241">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="ba903-242">指定样式</span><span class="sxs-lookup"><span data-stu-id="ba903-242">To specify a style</span></span>  
  
1.  <span data-ttu-id="ba903-243">在 "**选择样式**" 页的 "样式" 窗格中，选择 "石板"。</span><span class="sxs-lookup"><span data-stu-id="ba903-243">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="ba903-244">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="ba903-244">Click **Finish**.</span></span>  
  
     <span data-ttu-id="ba903-245">表将添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="ba903-245">The table is added to the design surface.</span></span>  
  
3.  <span data-ttu-id="ba903-246">若要预览报表，请单击“运行 (!)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-246">To preview the report, click **Run (!)**.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="DFormat"></a><span data-ttu-id="ba903-247">2. 将数据格式设置为货币</span><span class="sxs-lookup"><span data-stu-id="ba903-247">2. Format Data as Currency</span></span>  
 <span data-ttu-id="ba903-248">将货币格式应用到钻取报表中的销售额字段。</span><span class="sxs-lookup"><span data-stu-id="ba903-248">Apply currency formatting to the sales amount fields in the drillthrough report.</span></span>  
  
#### <a name="to-format-data-as-currency"></a><span data-ttu-id="ba903-249">将数据格式设置为货币格式</span><span class="sxs-lookup"><span data-stu-id="ba903-249">To format data as currency</span></span>  
  
1.  <span data-ttu-id="ba903-250">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-250">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-251">若要同时选择多个单元并设置其格式，请按 Ctrl 键，然后选择包含数值销售数据的单元。</span><span class="sxs-lookup"><span data-stu-id="ba903-251">To select and format multiple cells at one time, press the Ctrl key, and then select the cells that contain the numeric sales data.</span></span>  
  
3.  <span data-ttu-id="ba903-252">在“主文件夹”\*\*\*\* 选项卡上的“数字”\*\*\*\* 组中，单击“货币”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-252">On the **Home** tab, in the **Number** group, click **Currency**.</span></span>  
  
##  <a name="3-add-columns-to-show-sales-values-in-sparklines"></a><a name="DSparkline"></a><span data-ttu-id="ba903-253">3. 添加要在迷你图中显示销售值的列</span><span class="sxs-lookup"><span data-stu-id="ba903-253">3. Add Columns to Show Sales Values in Sparklines</span></span>  
 <span data-ttu-id="ba903-254">报表不将销售额和销售退货额显示为货币值，而是在迷你图中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="ba903-254">Instead of showing sales and sales returns as currency values, the report shows the values in a sparkline.</span></span>  
  
#### <a name="to-add-sparklines-to-columns"></a><span data-ttu-id="ba903-255">将迷你图添加到列</span><span class="sxs-lookup"><span data-stu-id="ba903-255">To add sparklines to columns</span></span>  
  
1.  <span data-ttu-id="ba903-256">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-256">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-257">在矩阵的“总计”组中，右键单击“销售额”列，单击“插入列”，然后单击“右侧”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-257">In the Total group of the matrix, right-click the **Sales Amount** column, click **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="ba903-258">一个空列会添加到“销售额”的右侧\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-258">An empty column is added to the right of **Sales Amount**.</span></span>  
  
3.  <span data-ttu-id="ba903-259">在功能区上，单击“矩形”，然后单击 [Product_Subcategory] 行组中 `[Sum(Sales_Amount)]` 单元右侧的空单元\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-259">On the ribbon, click **Rectangle**, and then click the empty cell to the right of the `[Sum(Sales_Amount)]` cell in the [Product_Subcategory] row group.</span></span>  
  
4.  <span data-ttu-id="ba903-260">在功能区上单击“迷你图”图标，然后单击添加了矩形的单元\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-260">On the ribbon, click the **Sparkline** icon, and then click the cell where the rectangle was added.</span></span>  
  
5.  <span data-ttu-id="ba903-261">在“选择迷你图类型”对话框中，确认已选中“列”类型\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-261">In the **Select Sparkline Type** dialog box, verify that **Column** type is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="ba903-262">右键单击该迷你图。</span><span class="sxs-lookup"><span data-stu-id="ba903-262">Right-click the sparkline.</span></span>  
  
8.  <span data-ttu-id="ba903-263">在“图表数据”窗格中，单击“添加字段”图标，然后单击“Sales_Amount”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-263">In the Chart Data pane, click the **Add field** icon, and then click Sales_Amount.</span></span>  
  
9. <span data-ttu-id="ba903-264">右键单击 `Sales_Return_Amount` 列，然后将一个列添加到它的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-264">Right-click the `Sales_Return_Amount` column, and then add a column to the right of it.</span></span>  
  
10. <span data-ttu-id="ba903-265">重复步骤 2 到步骤 6。</span><span class="sxs-lookup"><span data-stu-id="ba903-265">Repeat steps 2 through 6.</span></span>  
  
11. <span data-ttu-id="ba903-266">右键单击该迷你图。</span><span class="sxs-lookup"><span data-stu-id="ba903-266">Right-click the sparkline.</span></span>  
  
12. <span data-ttu-id="ba903-267">在“图表数据”窗格中，单击“添加字段”图标，然后单击“Sales_Return_Amount”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-267">In the Chart Data pane, click the **Add field** icon, and then click Sales_Return_Amount.</span></span>  
  
13. <span data-ttu-id="ba903-268">若要预览报表，请单击“运行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-268">To preview the report, click **Run**.</span></span>  
  
##  <a name="4-add-report-title-with-product-category-name"></a><a name="DReportTitle"></a><span data-ttu-id="ba903-269">4. 添加包含产品类别名称的报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-269">4. Add Report Title with Product Category Name</span></span>  
 <span data-ttu-id="ba903-270">报表标题将出现在报表的顶部。</span><span class="sxs-lookup"><span data-stu-id="ba903-270">A report title appears at the top of the report.</span></span> <span data-ttu-id="ba903-271">可以将报表标题置于报表表头中或置于表体顶部的文本框中（如果报表未使用表头）。</span><span class="sxs-lookup"><span data-stu-id="ba903-271">You can place the report title in a report header or, if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="ba903-272">在本教程中，您将使用自动放置在表体顶部的文本框。</span><span class="sxs-lookup"><span data-stu-id="ba903-272">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="ba903-273">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-273">To add a report title</span></span>  
  
1.  <span data-ttu-id="ba903-274">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-274">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-275">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-275">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="ba903-276">键入 **Sales and Returns for Category:**。</span><span class="sxs-lookup"><span data-stu-id="ba903-276">Type **Sales and Returns for Category:**.</span></span>  
  
4.  <span data-ttu-id="ba903-277">右键单击，然后单击“创建占位符”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-277">Right-click, and then click **Create Placeholder**.</span></span>  
  
5.  <span data-ttu-id="ba903-278">单击“值”列表右侧的“(fx)”按钮\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-278">Click the **(fx)** button to the right of the **Value** list.</span></span>  
  
6.  <span data-ttu-id="ba903-279">在“表达式”对话框的“类别”窗格中，单击“数据集”，然后在“值”列表中双击 `First(Product_Category_Name)`\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-279">In the **Expression** dialog box, in the Category pane, click **Dataset**, and then in the **Values** list double-click `First(Product_Category_Name)`.</span></span>  
  
     <span data-ttu-id="ba903-280">“表达式”框包含以下表达式\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="ba903-280">The **Expression** box contains the following expression:</span></span>  
  
    ```  
    =First(Fields!Product_Category_Name.Value, "DataSet1")  
    ```  
  
7.  <span data-ttu-id="ba903-281">若要预览报表，请单击“运行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-281">To preview the report, click **Run**.</span></span>  
  
 <span data-ttu-id="ba903-282">报表标题包含第一个产品类别的名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-282">The report title includes the name of the first product category.</span></span> <span data-ttu-id="ba903-283">以后，在您将此报表作为钻取报表运行时，产品类别名称将动态更改，以反映在主报表中单击的产品类别的名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-283">Later, after you run this report as a drillthrough report, the product category name will dynamically change to reflect the name of the product category that was clicked in the main report.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="DParameter"></a><span data-ttu-id="ba903-284">5. 更新参数属性</span><span class="sxs-lookup"><span data-stu-id="ba903-284">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="ba903-285">默认情况下，参数是可见的，但是这对此报表不合适。</span><span class="sxs-lookup"><span data-stu-id="ba903-285">By default parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="ba903-286">您将更新钻取报表的参数属性。</span><span class="sxs-lookup"><span data-stu-id="ba903-286">You will update the parameter properties for the drillthrough report.</span></span>  
  
#### <a name="to-hide-a-parameter"></a><span data-ttu-id="ba903-287">隐藏参数</span><span class="sxs-lookup"><span data-stu-id="ba903-287">To hide a parameter</span></span>  
  
1.  <span data-ttu-id="ba903-288">在“报表数据”窗格中，展开“参数”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-288">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="ba903-289">右键单击“\@ProductProductCategoryName”，再单击“参数属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-289">Right-click \@ProductProductCategoryName, and then click **Parameter Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-290">名称旁边的 \@ 字符指明这是参数。</span><span class="sxs-lookup"><span data-stu-id="ba903-290">The \@ character next to the name indicates that this is a parameter.</span></span>  
  
3.  <span data-ttu-id="ba903-291">在“常规”选项卡中，单击“隐藏”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-291">On the **General** tab, click **Hidden**.</span></span>  
  
4.  <span data-ttu-id="ba903-292">在“提示”框中，键入“Product Category”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-292">In the **Prompt** box, type **Product Category**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-293">因为参数是隐藏的，所以从不使用此提示。</span><span class="sxs-lookup"><span data-stu-id="ba903-293">Because the parameter is hidden, this prompt is never used.</span></span>  
  
5.  <span data-ttu-id="ba903-294">或者，可以单击“可用值”和“默认值”，然后查看它们的选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-294">Optionally, click **Available Values** and **Default Values** and review their options.</span></span> <span data-ttu-id="ba903-295">不更改这些选项卡上的任何选项。</span><span class="sxs-lookup"><span data-stu-id="ba903-295">Do not change any options on these tabs.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report-to-a-sharepoint-library"></a><a name="DSave"></a><span data-ttu-id="ba903-296">6. 将报表保存到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="ba903-296">6. Save the Report to a SharePoint Library</span></span>  
 <span data-ttu-id="ba903-297">可以将报表保存到 SharePoint 库、报表服务器或您的计算机。</span><span class="sxs-lookup"><span data-stu-id="ba903-297">You can save the report to a SharePoint library, report server, or your computer.</span></span> <span data-ttu-id="ba903-298">如果将报表保存到您的计算机，则许多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能（如报表部件和子报表）将不可用。</span><span class="sxs-lookup"><span data-stu-id="ba903-298">If you save the report to your computer, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span> <span data-ttu-id="ba903-299">在本教程中，您将把报表保存到 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="ba903-299">In this tutorial, you will save the report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="ba903-300">保存报表</span><span class="sxs-lookup"><span data-stu-id="ba903-300">To save the report</span></span>  
  
1.  <span data-ttu-id="ba903-301">从“报表生成器”按钮，单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ba903-301">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="ba903-302">“另存为报表”对话框将打开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-302">The **Save As Report** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-303">如果正在重新保存报表，会自动将其重新保存到以前的位置。</span><span class="sxs-lookup"><span data-stu-id="ba903-303">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="ba903-304">若要更改位置，请使用“另存为”选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-304">To change the location, use the **Save As** option.</span></span>  
  
2.  <span data-ttu-id="ba903-305">若要显示最近使用的报表服务器和 SharePoint 站点的列表，请单击“最近使用的站点和服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-305">To show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="ba903-306">选择或键入您拥有保存报表权限的 SharePoint 站点的名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-306">Select or type the name of the SharePoint site where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="ba903-307">SharePoint 库的 URL 具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="ba903-307">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
4.  <span data-ttu-id="ba903-308">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="ba903-308">Click **Save**.</span></span>  
  
     <span data-ttu-id="ba903-309">“最近使用的站点和服务器”列出 SharePoint 站点上的库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-309">**Recent Sites and Servers** lists the libraries on the SharePoint site.</span></span>  
  
5.  <span data-ttu-id="ba903-310">导航到您将保存报表的库。</span><span class="sxs-lookup"><span data-stu-id="ba903-310">Navigate to the library where you will save the report.</span></span>  
  
6.  <span data-ttu-id="ba903-311">在“名称”框中，用 ResellerVSOnlineDrillthrough 替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-311">In the **Name** box, replace the default name with **ResellerVSOnlineDrillthrough**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ba903-312">您将主报表保存到同一位置。</span><span class="sxs-lookup"><span data-stu-id="ba903-312">You will save the main report to the same location.</span></span> <span data-ttu-id="ba903-313">如果要将主报表和钻取报表保存到不同的站点或库，必须在主报表中更新“转到报表”操作的路径\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-313">If you want to save the main and drillthrough reports to different sites or libraries, you must update the path of the **Go to report** action in the main report.</span></span>  
  
7.  <span data-ttu-id="ba903-314">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="ba903-314">Click **Save**.</span></span>  
  
##  <a name="1-create-a-new-report-from-the-table-or-matrix-wizard"></a><a name="MMatrixAndDataset"></a><span data-ttu-id="ba903-315">1. 使用表或矩阵向导创建新报表</span><span class="sxs-lookup"><span data-stu-id="ba903-315">1. Create a New Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="ba903-316">使用“表或矩阵向导”从“入门”对话框创建一个矩阵报表\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-316">From the **Getting Started** dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="ba903-317">创建新的报表</span><span class="sxs-lookup"><span data-stu-id="ba903-317">To create a new report</span></span>  
  
1.  <span data-ttu-id="ba903-318">单击 "**开始**"，指向 "**程序**"，指向 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] "**报表生成器**"，然后单击 "**报表生成器**"。</span><span class="sxs-lookup"><span data-stu-id="ba903-318">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="ba903-319">在“入门”\*\*\*\* 对话框中，确认已选中“新建报表”\*\*\*\*，然后单击“表或矩阵向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-319">In the **Getting Started** dialog box, verify that **New Report** is selected, and then click **Table or Matrix Wizard**.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="MConnection"></a><span data-ttu-id="ba903-320">1a.</span><span class="sxs-lookup"><span data-stu-id="ba903-320">1a.</span></span> <span data-ttu-id="ba903-321">指定数据连接</span><span class="sxs-lookup"><span data-stu-id="ba903-321">Specify a Data Connection</span></span>  
 <span data-ttu-id="ba903-322">您将嵌入数据源添加到主报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-322">You will add an embedded data source to the main report.</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="ba903-323">创建嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="ba903-323">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="ba903-324">在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-324">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="ba903-325">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="ba903-325">Click **New**.</span></span>  
  
3.  <span data-ttu-id="ba903-326">在“名称”中，键入“Online and Reseller Sales Main”作为数据源名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-326">In **Name**, type **Online and Reseller Sales Main** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="ba903-327">在“选择连接类型”中，选择“Microsoft SQL Server Analysis Services”，然后单击“生成”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-327">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="ba903-328">在“数据源”\*\*\*\* 中，确认数据源是“Microsoft SQL Server Analysis Services (AdomdClient)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-328">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="ba903-329">在 "**服务器名称**" 中，键入安装了实例的服务器的名称 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ba903-329">In **Server name**, type the name of a server where an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is installed.</span></span>  
  
7.  <span data-ttu-id="ba903-330">在“选择或输入数据库名称”\*\*\*\* 中，选择 Contoso 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-330">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="ba903-331">确认“连接字符串”包含以下语法\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="ba903-331">Verify that the **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
10. <span data-ttu-id="ba903-332">单击“凭据类型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-332">Click **Credentials type**.</span></span>  
  
     <span data-ttu-id="ba903-333">您可能需要更改默认身份验证，具体取决于在数据源上配置权限的方式。</span><span class="sxs-lookup"><span data-stu-id="ba903-333">Depending on how permissions are configured on the data source, you might need to change the default authentication.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="ba903-334">若要验证是否能连接到数据源，请单击“测试连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-334">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="ba903-335">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-335">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="MMDXQuery"></a><span data-ttu-id="ba903-336">1b.</span><span class="sxs-lookup"><span data-stu-id="ba903-336">1b.</span></span> <span data-ttu-id="ba903-337">创建 MDX 查询</span><span class="sxs-lookup"><span data-stu-id="ba903-337">Create an MDX Query</span></span>  
 <span data-ttu-id="ba903-338">接下来将创建嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="ba903-338">Next, create an embedded dataset.</span></span> <span data-ttu-id="ba903-339">为此，您将使用查询设计器来创建筛选器、参数和计算成员以及数据集本身。</span><span class="sxs-lookup"><span data-stu-id="ba903-339">To do so, you will use the query designer to create filters, parameters, and calculated members as well as the dataset itself.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="ba903-340">创建查询筛选器</span><span class="sxs-lookup"><span data-stu-id="ba903-340">To create query filters</span></span>  
  
1.  <span data-ttu-id="ba903-341">在 "**设计查询**" 页上的 "元数据" 窗格的 "多维数据集" 部分中，单击省略号\*\* ( ") \*\*"。</span><span class="sxs-lookup"><span data-stu-id="ba903-341">On the **Design a query** page, in the Metadata pane, in the cube section, click the ellipsis **(...)**.</span></span>  
  
2.  <span data-ttu-id="ba903-342">在“选择多维数据集”\*\*\*\* 对话框中，依次单击“Sales”和“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-342">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ba903-343">如果不想手动生成 MDX 查询，请单击 ![切换到设计模式](media/rsqdicon-designmode.gif "切换到设计模式") 图标，将查询设计器切换到“查询”模式，将已完成的 MDX 粘贴到查询设计器，然后继续执行 [创建数据集](#MSkip)中的步骤 5。</span><span class="sxs-lookup"><span data-stu-id="ba903-343">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 5 in [To create the dataset](#MSkip).</span></span>  
  
    ```  
    WITH MEMBER [Measures].[Net QTY] AS [Measures].[Sales Quantity] -[Measures].[Sales Return Quantity] MEMBER [Measures].[Net Sales] AS [Measures].[Sales Amount] - [Measures].[Sales Return Amount] SELECT NON EMPTY { [Measures].[Net QTY], [Measures].[Net Sales] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGSQuery text: Code.  
    ```  
  
3.  <span data-ttu-id="ba903-344">在“度量值组”窗格中，展开“Channel”，然后将“Channel Name”拖到筛选器窗格中的“层次结构”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="ba903-344">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="ba903-345">维度名称“Channel”会自动添加到“维度”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-345">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="ba903-346">不要更改“维度”或“运算符”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-346">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="ba903-347">若要打开“筛选表达式”列表，请单击“筛选表达式”列中的向下箭头\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-347">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="ba903-348">在筛选表达式列表中，展开“所有渠道”，依次单击“在线”、“分销商”和“确定”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-348">In the filter expression list, expand **All Channel**, click **Online** and **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-349">查询现在包含一个筛选器以只包括这些渠道：“在线”和“分销商”。</span><span class="sxs-lookup"><span data-stu-id="ba903-349">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="ba903-350">展开 "销售区域" 维度，然后将 "销售区域" 组拖动到 "**通道名称**" 下方的 "**层次结构**" 列。</span><span class="sxs-lookup"><span data-stu-id="ba903-350">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column, below **Channel Name**.</span></span>  
  
7.  <span data-ttu-id="ba903-351">打开“筛选表达式”列表，展开“所有销售区域”，单击“北美洲”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-351">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-352">查询现在具有一个筛选器以只包括北美洲的销售额。</span><span class="sxs-lookup"><span data-stu-id="ba903-352">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="ba903-353">在“度量值组”窗格中，展开“Date”，然后将“Calendar Year”拖到筛选器窗格中的“层次结构”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-353">In the Measure Group pane, expand Date, and drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="ba903-354">维度名称“Date”会自动添加到“维度”列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-354">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="ba903-355">不要更改“维度”或“运算符”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-355">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="ba903-356">若要打开“筛选表达式”列表，请单击“筛选表达式”列中的向下箭头\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-356">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="ba903-357">在筛选表达式列表中，展开“所有日期”，单击“2009 年”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-357">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-358">查询现在具有一个筛选器以只包括日历 2009 年的销售额。</span><span class="sxs-lookup"><span data-stu-id="ba903-358">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="ba903-359">创建参数</span><span class="sxs-lookup"><span data-stu-id="ba903-359">To create the parameter</span></span>  
  
1.  <span data-ttu-id="ba903-360">展开“Product”维度，然后将“Product Category Name”成员拖到“Sales Territory Group”下面的“层次结构”列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-360">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Sales Territory Group**.</span></span>  
  
2.  <span data-ttu-id="ba903-361">打开“筛选表达式”列表，单击“所有产品”，然后单击“确定”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-361">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="ba903-362">单击“参数”复选框\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-362">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="ba903-363">查询现在包含参数 ProductProductCategoryName。</span><span class="sxs-lookup"><span data-stu-id="ba903-363">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
#### <a name="to-create-calculated-members"></a><span data-ttu-id="ba903-364">创建计算成员</span><span class="sxs-lookup"><span data-stu-id="ba903-364">To create calculated members</span></span>  
  
1.  <span data-ttu-id="ba903-365">将光标置于“计算成员”窗格内，右键单击，然后单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-365">Place the cursor inside the Calculated Members pane, right-click, and then click **New Calculated Member**.</span></span>  
  
2.  <span data-ttu-id="ba903-366">在 "元数据" 窗格中，展开 "**度量值**"，然后展开 "销售额"。</span><span class="sxs-lookup"><span data-stu-id="ba903-366">In the Metadata pane, expand **Measures** and then expand Sales.</span></span>  
  
3.  <span data-ttu-id="ba903-367">将“Sales Quantity”度量值拖到“表达式”框，键入减号字符 (-)，然后将“Sales Return Quantity”度量值拖到“表达式”框；将它放到减号字符后面\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-367">Drag the Sales Quantity measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Quantity measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="ba903-368">以下代码显示了该表达式：</span><span class="sxs-lookup"><span data-stu-id="ba903-368">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Quantity] - [Measures].[Sales Return Quantity]  
    ```  
  
4.  <span data-ttu-id="ba903-369">在“名称”框中，键入 Net QTY，然后单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-369">In the Name box, type **Net QTY**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba903-370">“计算成员”窗格将列出“Net QTY”计算成员\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-370">The Calculated Members pane lists the **Net QTY** calculated member.</span></span>  
  
5.  <span data-ttu-id="ba903-371">右键单击“计算成员”，然后单击“新建计算成员”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-371">Right-click **Calculated Members**, and then click **New Calculated Member**.</span></span>  
  
6.  <span data-ttu-id="ba903-372">在“元数据”窗格中，依次展开“度量值”和“Sales”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-372">In the Metadata pane, expand **Measures**, and then expand Sales.</span></span>  
  
7.  <span data-ttu-id="ba903-373">将“Sales Amount”度量值拖到“表达式”框，键入减号字符 (-)，然后将“Sales Return Amount”度量值拖到“表达式”框；将它放到减号字符后面\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-373">Drag the Sales Amount measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Amount measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="ba903-374">以下代码显示了该表达式：</span><span class="sxs-lookup"><span data-stu-id="ba903-374">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Amount] - [Measures].[Sales Return Amount]  
    ```  
  
8.  <span data-ttu-id="ba903-375">在“名称”\*\*\*\* 框中，键入 **Net Sales**，然后单击“确定”\*\*\*\*。“计算成员”窗格将列出“Net Sales”\*\*\*\* 计算成员。</span><span class="sxs-lookup"><span data-stu-id="ba903-375">In the **Name** box, type  **Net Sales**, and then click **OK**.The Calculated Members pane lists the **Net Sales** calculated member.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="MSkip"></a><span data-ttu-id="ba903-376">创建数据集</span><span class="sxs-lookup"><span data-stu-id="ba903-376">To create the dataset</span></span>  
  
1.  <span data-ttu-id="ba903-377">从“Channel”维度将“Channel Name”拖到数据窗格。</span><span class="sxs-lookup"><span data-stu-id="ba903-377">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="ba903-378">从“Product”维度将“Product Category Name”拖到数据窗格，然后将它放到“Channel Name”的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-378">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="ba903-379">从“计算成员”，将“`Net QTY`”拖到数据窗格，然后将它放到“Product Category Name”的右侧\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-379">From **Calculated Members**, drag `Net QTY` to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="ba903-380">从“计算成员”，将“Net Sales”拖到数据窗格，然后将它放到“ `Net QTY`”的右侧。</span><span class="sxs-lookup"><span data-stu-id="ba903-380">From Calculated Members, drag Net Sales to the data pane, and then place it to the right of `Net QTY`.</span></span>  
  
5.  <span data-ttu-id="ba903-381">在查询设计器工具栏上，单击 "\*\*运行 (！ ) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="ba903-381">On the query designer toolbar, click **Run (!)**.</span></span>  
  
     <span data-ttu-id="ba903-382">查看查询结果集。</span><span class="sxs-lookup"><span data-stu-id="ba903-382">Review the query result set.</span></span>  
  
6.  <span data-ttu-id="ba903-383">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-383">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="MLayout"></a><span data-ttu-id="ba903-384">1c.</span><span class="sxs-lookup"><span data-stu-id="ba903-384">1c.</span></span> <span data-ttu-id="ba903-385">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="ba903-385">Organize Data into Groups</span></span>  
 <span data-ttu-id="ba903-386">在选择要对数据分组的字段时，可以设计一个矩阵，其中的行和列显示了详细数据和聚合数据。</span><span class="sxs-lookup"><span data-stu-id="ba903-386">When you select the fields on which to group data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="ba903-387">将数据组织到组中</span><span class="sxs-lookup"><span data-stu-id="ba903-387">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="ba903-388">在“排列字段”页上，将“Product_Category_Name”拖到“行组”中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-388">On the **Arrange fields** page, drag Product_Category_Name to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="ba903-389">将 Channel_Name 拖到“列组”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-389">Drag Channel_Name to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="ba903-390">将“`Net_QTY`”拖到“值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-390">Drag `Net_QTY` to **Values**.</span></span>  
  
     <span data-ttu-id="ba903-391">`Net_QTY` 由 Sum 函数（即数值字段的默认聚合函数）自动聚合。</span><span class="sxs-lookup"><span data-stu-id="ba903-391">`Net_QTY` is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="ba903-392">值为 `[Sum(Net_QTY)]`。</span><span class="sxs-lookup"><span data-stu-id="ba903-392">The value is `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="ba903-393">若要查看其他可用聚合函数，请打开下拉列表。</span><span class="sxs-lookup"><span data-stu-id="ba903-393">To view the other aggregate functions available, open the drop-down list.</span></span> <span data-ttu-id="ba903-394">不要更改聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ba903-394">Do not change the aggregate function.</span></span>  
  
4.  <span data-ttu-id="ba903-395">将“`Net_Sales_Return`”拖到“值”，然后将它放在“`[Sum(Net_QTY)]`”下面\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-395">Drag `Net_Sales_Return` to **Values** and then place it below `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="ba903-396">步骤 3 和 4 指定要在矩阵中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="ba903-396">Steps 3 and 4 specify the data to display in the matrix.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="MTotals"></a><span data-ttu-id="ba903-397">1d.</span><span class="sxs-lookup"><span data-stu-id="ba903-397">1d.</span></span> <span data-ttu-id="ba903-398">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-398">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="ba903-399">可以在报表中显示小计和总计。</span><span class="sxs-lookup"><span data-stu-id="ba903-399">You can show subtotals and grand totals in reports.</span></span> <span data-ttu-id="ba903-400">主报表中的数据作为指示器显示；在完成向导后将删除总计。</span><span class="sxs-lookup"><span data-stu-id="ba903-400">The data in the main report displays as an indicator; you will remove the grand total after you complete the wizard.</span></span>  
  
#### <a name="to-add-subtotals-and-grand-totals"></a><span data-ttu-id="ba903-401">添加小计和总计</span><span class="sxs-lookup"><span data-stu-id="ba903-401">To add subtotals and grand totals</span></span>  
  
1.  <span data-ttu-id="ba903-402">在“选择布局”页的“选项”下，确认已选择“显示小计和总计”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-402">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="ba903-403">向导的“预览”窗格将显示包含四行的矩阵。</span><span class="sxs-lookup"><span data-stu-id="ba903-403">The wizard Preview pane displays a matrix with four rows.</span></span>  <span data-ttu-id="ba903-404">运行报表时，将通过以下方式显示每个行：第一行为列组，第二行包含列标题，第三行包含产品类别数据（`[Sum(Net_ QTY)]` 和 `[Sum(Net_Sales)]`），第四行包含总计。</span><span class="sxs-lookup"><span data-stu-id="ba903-404">When you run the report, each row will display in the following way: The first row is the column group, the second row contains the column headings, the third row contains the product category data (`[Sum(Net_ QTY)]` and `[Sum(Net_Sales)]`, and the fourth row contains the totals.</span></span>  
  
2.  <span data-ttu-id="ba903-405">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ba903-405">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="MStyle"></a><span data-ttu-id="ba903-406">1e.</span><span class="sxs-lookup"><span data-stu-id="ba903-406">1e.</span></span> <span data-ttu-id="ba903-407">选择样式</span><span class="sxs-lookup"><span data-stu-id="ba903-407">Choose a Style</span></span>  
 <span data-ttu-id="ba903-408">将“石板”样式应用到报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-408">Apply the Slate style to the report.</span></span> <span data-ttu-id="ba903-409">钻取报表也使用此样式。</span><span class="sxs-lookup"><span data-stu-id="ba903-409">This is the same style that the drillthrough report uses.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="ba903-410">指定样式</span><span class="sxs-lookup"><span data-stu-id="ba903-410">To specify a style</span></span>  
  
1.  <span data-ttu-id="ba903-411">在 "**选择样式**" 页的 "样式" 窗格中，选择 "石板"。</span><span class="sxs-lookup"><span data-stu-id="ba903-411">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="ba903-412">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="ba903-412">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="ba903-413">若要预览报表，请单击“运行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-413">To preview the report, click **Run**.</span></span>  
  
##  <a name="2-remove-the-grand-total-row"></a><a name="MGrandTotal"></a><span data-ttu-id="ba903-414">2. 删除总计行</span><span class="sxs-lookup"><span data-stu-id="ba903-414">2. Remove the Grand Total Row</span></span>  
 <span data-ttu-id="ba903-415">数据值作为指示器状态显示，包括列组总计。</span><span class="sxs-lookup"><span data-stu-id="ba903-415">The data values are shown as indictor states, including the column group totals.</span></span> <span data-ttu-id="ba903-416">删除显示总计的行。</span><span class="sxs-lookup"><span data-stu-id="ba903-416">Remove the row that displays the grand total.</span></span>  
  
#### <a name="to-remove-the-grand-total-row"></a><span data-ttu-id="ba903-417">删除总计行</span><span class="sxs-lookup"><span data-stu-id="ba903-417">To remove the grand total row</span></span>  
  
1.  <span data-ttu-id="ba903-418">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-418">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-419">单击“总计”行（矩阵中的最后一行），右键单击，然后单击“删除行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-419">Click the Total row (the last row in the matrix), right-click, and then click **Delete Rows**.</span></span>  
  
3.  <span data-ttu-id="ba903-420">若要预览报表，请单击“运行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-420">To preview the report, click **Run**.</span></span>  
  
##  <a name="3-configure-text-box-action-for-drillthrough"></a><a name="MDrillthrough"></a><span data-ttu-id="ba903-421">3. 配置用于钻取的文本框操作</span><span class="sxs-lookup"><span data-stu-id="ba903-421">3. Configure Text Box Action for Drillthrough</span></span>  
 <span data-ttu-id="ba903-422">若要启用钻取，请在主报表中指定文本框的操作。</span><span class="sxs-lookup"><span data-stu-id="ba903-422">To enable the drillthrough, specify an action on a text box in the main report.</span></span>  
  
#### <a name="to-enable-an-action"></a><span data-ttu-id="ba903-423">启用操作</span><span class="sxs-lookup"><span data-stu-id="ba903-423">To enable an action</span></span>  
  
1.  <span data-ttu-id="ba903-424">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-424">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-425">右键单击包含 Product_Category_Name 单元，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-425">Right-click the cell that contains Product_Category_Name, and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="ba903-426">单击“操作”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ba903-426">Click the **Action** tab.</span></span>  
  
4.  <span data-ttu-id="ba903-427">选择 "**转向报表"。**</span><span class="sxs-lookup"><span data-stu-id="ba903-427">Select **Go to report.**</span></span>  
  
5.  <span data-ttu-id="ba903-428">在“指定报表”中，单击“浏览”，然后查找名为 ResellerVSOnlineDrillthrough 的钻取报表\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-428">In **Specify a report**, click **Browse**, and then locate the drillthrough report named ResellerVSOnlineDrillthrough.</span></span>  
  
6.  <span data-ttu-id="ba903-429">若要添加用于运行钻取报表的参数，请单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-429">To add a parameter to run the drillthrough report, click **Add**.</span></span>  
  
7.  <span data-ttu-id="ba903-430">在“名称”列表中，选择“ProductProductCategoryName”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-430">In the **Name** list, select ProductProductCategoryName.</span></span>  
  
8.  <span data-ttu-id="ba903-431">在“值”中键入 `[Product_Category_Name.UniqueName]`。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ba903-431">In **Value**, type `[Product_Category_Name.UniqueName]`.</span></span>  
  
     <span data-ttu-id="ba903-432">“Product_Category_Name”是数据集中的字段。</span><span class="sxs-lookup"><span data-stu-id="ba903-432">Product_Category_Name is a field in the dataset.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ba903-433">必须包含 `UniqueName` 属性，因为钻取操作需要唯一值。</span><span class="sxs-lookup"><span data-stu-id="ba903-433">You must include the `UniqueName` property because the drillthrough action requires a unique value.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-format-the-drillthrough-field"></a><span data-ttu-id="ba903-434">设置钻取字段的格式</span><span class="sxs-lookup"><span data-stu-id="ba903-434">To format the drillthrough field</span></span>  
  
1.  <span data-ttu-id="ba903-435">右键单击包含 `Product_Category_Name` 的单元，然后单击“文本框属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-435">Right-click the cell that contains the `Product_Category_Name`, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="ba903-436">单击 **“字体”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ba903-436">Click the **Font** tab.</span></span>  
  
3.  <span data-ttu-id="ba903-437">在“效果”列表中，选择“下划线”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-437">In the **Effects** list, select **Underline**.</span></span>  
  
4.  <span data-ttu-id="ba903-438">在“颜色”列表中，选择“蓝色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-438">In the **Color** list, select **Blue**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="ba903-439">若要预览报表，请单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="ba903-439">To preview your report, click **Run**.</span></span>  
  
 <span data-ttu-id="ba903-440">这些产品类别名称采用常见的链接格式（蓝色带下划线）。</span><span class="sxs-lookup"><span data-stu-id="ba903-440">The product category names are in the common link format (blue and underlined).</span></span>  
  
##  <a name="4-replace-numeric-values-with-indicators"></a><a name="MIndicators"></a><span data-ttu-id="ba903-441">4. 将数值替换为指示器</span><span class="sxs-lookup"><span data-stu-id="ba903-441">4. Replace Numeric Values with Indicators</span></span>  
 <span data-ttu-id="ba903-442">使用指示器显示“在线”和“分销商”渠道的数量和销售额的情况。</span><span class="sxs-lookup"><span data-stu-id="ba903-442">Use indicators to show the state of quantities and sales for Online and Reseller channels.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-qty-values"></a><span data-ttu-id="ba903-443">添加 Net QTY 值的指示器</span><span class="sxs-lookup"><span data-stu-id="ba903-443">To add an indicator for Net QTY values</span></span>  
  
1.  <span data-ttu-id="ba903-444">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-444">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-445">在功能区上，单击“矩形”图标，然后在 `Channel_Name` 列组的 `[Product_Category_Name]` 行组中的 `[Sum(Net QTY)]` 单元内单击\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-445">On the ribbon, click the **Rectangle** icon, and then click in the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
3.  <span data-ttu-id="ba903-446">在功能区上，单击“指示器”图标，然后在矩形内单击\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-446">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span> <span data-ttu-id="ba903-447">“选择指示器类型”对话框将打开，其中选择了“方向”指示器\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-447">The **Select Indicator Type** dialog box opens with the **Directional** indicator selected.</span></span>  
  
4.  <span data-ttu-id="ba903-448">单击“3 个符号”类型，然后单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-448">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ba903-449">右键单击该指示器，然后在“仪表数据”窗格中单击“(未指定)”旁边的向下箭头\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-449">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="ba903-450">选择 `Net_QTY`。</span><span class="sxs-lookup"><span data-stu-id="ba903-450">Select `Net_QTY`.</span></span>  
  
6.  <span data-ttu-id="ba903-451">对“总计”内 `[Product_Category_Name]` 行组中的 `[Sum(Net QTY)]` 单元重复步骤 2 到 5\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-451">Repeat steps 2 through 5 for the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-sales-values"></a><span data-ttu-id="ba903-452">添加 Net Sales 值的指示器</span><span class="sxs-lookup"><span data-stu-id="ba903-452">To add an indicator for Net Sales values</span></span>  
  
1.  <span data-ttu-id="ba903-453">在功能区上，单击“矩形”图标，然后在 `Channel_Name` 列组的 `[Product_Category_Name]` 行组中的 `[Sum(Net_Sales)]` 单元内单击\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-453">On the ribbon, click the **Rectangle** icon, and then click inside the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
2.  <span data-ttu-id="ba903-454">在功能区上，单击“指示器”图标，然后在矩形内单击\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-454">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span>  
  
3.  <span data-ttu-id="ba903-455">单击“3 个符号”类型，然后单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-455">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="ba903-456">右键单击该指示器，然后在“仪表数据”窗格中单击“(未指定)”旁边的向下箭头\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-456">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="ba903-457">选择 `Net_Sales`。</span><span class="sxs-lookup"><span data-stu-id="ba903-457">Select `Net_Sales`.</span></span>  
  
5.  <span data-ttu-id="ba903-458">对“总计”内 `[Product_Category_Name]` 行组中的 `[Sum(Net_Sales)]` 单元重复步骤 1 到 4\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-458">Repeat steps 1 through 4 for the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
6.  <span data-ttu-id="ba903-459">若要预览报表，请单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="ba903-459">To preview your report, click **Run**.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="MParameter"></a><span data-ttu-id="ba903-460">5. 更新参数属性</span><span class="sxs-lookup"><span data-stu-id="ba903-460">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="ba903-461">默认情况下，参数是可见的，但是这对此报表不合适。</span><span class="sxs-lookup"><span data-stu-id="ba903-461">By default, parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="ba903-462">您将更新参数属性以便使参数为内部参数。</span><span class="sxs-lookup"><span data-stu-id="ba903-462">You will update the parameter properties to make the parameter internal.</span></span>  
  
#### <a name="to-make-the-parameter-internal"></a><span data-ttu-id="ba903-463">使参数为内部参数</span><span class="sxs-lookup"><span data-stu-id="ba903-463">To make the parameter internal</span></span>  
  
1.  <span data-ttu-id="ba903-464">在“报表数据”窗格中，展开“参数”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-464">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="ba903-465">右键单击“`@ProductProductCategoryName,`”，然后单击“参数属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-465">Right-click `@ProductProductCategoryName,` and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="ba903-466">在“常规”选项卡中，单击“内部”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-466">On the **General** tab, click **Internal**.</span></span>  
  
4.  <span data-ttu-id="ba903-467">或者，可以单击“可用值”和“默认值”选项卡，然后查看它们的选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-467">Optionally, click the **Available Values** and **Default Values** tabs and review their options.</span></span> <span data-ttu-id="ba903-468">不更改这些选项卡上的任何选项。</span><span class="sxs-lookup"><span data-stu-id="ba903-468">Do not change any options on these tabs.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-add-a-report-title"></a><a name="MTitle"></a><span data-ttu-id="ba903-469">6. 添加报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-469">6. Add a Report Title</span></span>  
 <span data-ttu-id="ba903-470">将标题添加到主报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-470">Add a title to the main report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="ba903-471">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="ba903-471">To add a report title</span></span>  
  
1.  <span data-ttu-id="ba903-472">在设计图面上，单击“单击以添加标题”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-472">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="ba903-473">键入 **2009 Product Category Sales: Online and Reseller Category:**。</span><span class="sxs-lookup"><span data-stu-id="ba903-473">Type **2009 Product Category Sales: Online and Reseller Category:**.</span></span>  
  
3.  <span data-ttu-id="ba903-474">选择键入的文本。</span><span class="sxs-lookup"><span data-stu-id="ba903-474">Select the text you typed.</span></span>  
  
4.  <span data-ttu-id="ba903-475">在功能区的“主文件夹”选项卡上，在“字体”组中选择“Times New Roman”字体、“16pt”字号以及“加粗”和“倾斜”样式\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-475">On the **Home** tab of the ribbon, in the Font group, select the **Times New Roman** font, **16pt** size, and the **Bold** and **Italic** styles.</span></span>  
  
5.  <span data-ttu-id="ba903-476">若要预览报表，请单击 **“运行”**。</span><span class="sxs-lookup"><span data-stu-id="ba903-476">To preview your report, click **Run**.</span></span>  
  
##  <a name="7-save-the-main-report-to-a-sharepoint-library"></a><a name="MSave"></a><span data-ttu-id="ba903-477">7. 将主报表保存到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="ba903-477">7. Save the Main Report to a SharePoint Library</span></span>  
 <span data-ttu-id="ba903-478">将主报表保存到 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="ba903-478">Save the main report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="ba903-479">保存报表</span><span class="sxs-lookup"><span data-stu-id="ba903-479">To save the report</span></span>  
  
1.  <span data-ttu-id="ba903-480">若要切换到设计视图，请单击“设计”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-480">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="ba903-481">从“报表生成器”按钮，单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ba903-481">From the Report Builder button, click **Save**.</span></span>  
  
3.  <span data-ttu-id="ba903-482">或者，单击“最近使用的站点和服务器”以显示最近使用的报表服务器和 SharePoint 站点的列表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-482">Optionally, to show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
4.  <span data-ttu-id="ba903-483">选择或键入您拥有保存报表权限的 SharePoint 站点的名称。</span><span class="sxs-lookup"><span data-stu-id="ba903-483">Select or type the name of the SharePoint site where you have permission to save reports.</span></span> <span data-ttu-id="ba903-484">SharePoint 库的 URL 具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="ba903-484">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
5.  <span data-ttu-id="ba903-485">导航到您要保存报表的库。</span><span class="sxs-lookup"><span data-stu-id="ba903-485">Navigate to the library where you want to save the report.</span></span>  
  
6.  <span data-ttu-id="ba903-486">在“名称”中，用 ResellerVSOnlineMain 替换默认名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-486">In **Name**, replace the default name with **ResellerVSOnlineMain**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ba903-487">将主报表保存到保存钻取报表的同一位置。</span><span class="sxs-lookup"><span data-stu-id="ba903-487">Save the main report to the same location where you saved the drillthrough report.</span></span> <span data-ttu-id="ba903-488">若要将主报表和钻取报表保存到不同的站点或库，请确保主报表中的“转到报表”操作指向正确的钻取报表位置\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-488">To save the main and drillthrough reports to different sites or libraries, confirm that the **Go to report** action in the main report, points to the correct location of the drillthrough report.</span></span>  
  
7.  <span data-ttu-id="ba903-489">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="ba903-489">Click **Save**.</span></span>  
  
##  <a name="8-run-the-main-and-drillthrough-reports"></a><a name="MRunReports"></a><span data-ttu-id="ba903-490">8. 运行主报表和钻取报表</span><span class="sxs-lookup"><span data-stu-id="ba903-490">8. Run the Main and Drillthrough Reports</span></span>  
 <span data-ttu-id="ba903-491">运行主报表，然后单击产品类别列中的值以运行钻取报表。</span><span class="sxs-lookup"><span data-stu-id="ba903-491">Run the main report, and then click values in the product category column to run the drillthrough report.</span></span>  
  
#### <a name="to-run-the-reports"></a><span data-ttu-id="ba903-492">运行报表</span><span class="sxs-lookup"><span data-stu-id="ba903-492">To run the reports</span></span>  
  
1.  <span data-ttu-id="ba903-493">打开保存报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="ba903-493">Open the SharePoint library where the reports are saved.</span></span>  
  
2.  <span data-ttu-id="ba903-494">双击 ResellerVSOnlineMain。</span><span class="sxs-lookup"><span data-stu-id="ba903-494">Double-click ResellerVSOnlineMain.</span></span>  
  
     <span data-ttu-id="ba903-495">将运行该报表并显示产品类别销售信息。</span><span class="sxs-lookup"><span data-stu-id="ba903-495">The report runs and displays product category sales information.</span></span>  
  
3.  <span data-ttu-id="ba903-496">单击包含产品类别名称的列中的“游戏和玩具”链接\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba903-496">Click the **Games and Toys** link in the column that contains product category names.</span></span>  
  
     <span data-ttu-id="ba903-497">将运行钻取报表，并只显示“游戏和玩具”产品类别的值。</span><span class="sxs-lookup"><span data-stu-id="ba903-497">The drillthrough report runs, displaying only the values for the Games and Toys product category.</span></span>  
  
4.  <span data-ttu-id="ba903-498">若要返回到主报表，请单击 Internet Explorer 返回按钮。</span><span class="sxs-lookup"><span data-stu-id="ba903-498">To return to the main report, click the Internet Explorer back button.</span></span>  
  
5.  <span data-ttu-id="ba903-499">也可以通过单击其名称来浏览其他产品类别（可选）。</span><span class="sxs-lookup"><span data-stu-id="ba903-499">Optionally, explore other product categories by clicking their names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba903-500">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba903-500">See Also</span></span>  
 [<span data-ttu-id="ba903-501">教程 &#40;报表生成器&#41;</span><span class="sxs-lookup"><span data-stu-id="ba903-501">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
