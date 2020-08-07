---
title: 教程：脱机生成快速图表报表（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51a9e648550a0108f47e3d93d75267ab0c1c24f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580015"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a><span data-ttu-id="0f5f6-102">教程：脱机创建快速图表报表（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="0f5f6-102">Tutorial: Create a Quick Chart Report Offline (Report Builder)</span></span>
  <span data-ttu-id="0f5f6-103">在本教程中，将使用向导创建饼图，然后将对其稍作修改以了解都能执行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-103">In this tutorial, you'll create a pie chart by using a wizard, and then you'll modify it a little, just to get an idea of what's possible.</span></span> <span data-ttu-id="0f5f6-104">您可以通过两种不同的方式学习本教程。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-104">You can do this tutorial two different ways.</span></span> <span data-ttu-id="0f5f6-105">这两种方法具有相同的结果：如下图所示的饼图：</span><span class="sxs-lookup"><span data-stu-id="0f5f6-105">Both methods have the same outcome-a pie chart like the one in the following illustration:</span></span>

 <span data-ttu-id="0f5f6-106">![“运行”视图中的“我的第一个饼图”](../media/rs-my1stpierunview.gif ""运行" 视图中的第一个饼图")</span><span class="sxs-lookup"><span data-stu-id="0f5f6-106">!["My First Pie Chart" in Run view](../media/rs-my1stpierunview.gif "My First Pie Chart in Run view")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f5f6-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="0f5f6-107">Prerequisites</span></span>
 <span data-ttu-id="0f5f6-108">无论您是使用 XML 数据还是 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询，都需要有权访问 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 报表生成器。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-108">Whether you use XML data or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, you need to have access to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder.</span></span> <span data-ttu-id="0f5f6-109">可以运行独立版本，也可以运行 ClickOnce 版本（可从报表管理器或 SharePoint 站点获取）。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-109">You can run the stand-alone version or the ClickOnce version available from Report Manager or a SharePoint site.</span></span> <span data-ttu-id="0f5f6-110">ClickOnce 版本只有第一步（如何打开报表生成器）不同。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-110">Only the first step, how to open Report Builder, is different for ClickOnce versions.</span></span> <span data-ttu-id="0f5f6-111">有关详细信息，请参阅[安装、卸载和报表生成器支持](../install-uninstall-and-report-builder-support.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-111">For more information, see [Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md).</span></span>

##  <a name="two-ways-to-do-this-tutorial"></a><a name="TwoWays"></a><span data-ttu-id="0f5f6-112">完成本教程的两种方法</span><span class="sxs-lookup"><span data-stu-id="0f5f6-112">Two Ways To Do This Tutorial</span></span>

-   [<span data-ttu-id="0f5f6-113">使用 XML 数据创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-113">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

-   [<span data-ttu-id="0f5f6-114">使用包含数据的 Transact-SQL 查询创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-114">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

### <a name="using-xml-data-for-this-tutorial"></a><span data-ttu-id="0f5f6-115">使用本教程的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0f5f6-115">Using XML data for this tutorial</span></span>
 <span data-ttu-id="0f5f6-116">通过复制本主题中的 XML 数据并粘贴到向导中，可以使用本主题中的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-116">You can use XML data that you copy from this topic and paste into the wizard.</span></span> <span data-ttu-id="0f5f6-117">不需要连接到报表服务器或处于 SharePoint 集成模式下的报表服务器，也不需要访问 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-117">You don't need to be connected to a report server or a report server in SharePoint integrated mode, and you don't need access to an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>

 [<span data-ttu-id="0f5f6-118">使用 XML 数据创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-118">Create the pie chart with XML data</span></span>](#CreatePieChartXML)

### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a><span data-ttu-id="0f5f6-119">使用包含本教程数据的 Transact-SQL 查询</span><span class="sxs-lookup"><span data-stu-id="0f5f6-119">Using a Transact-SQL query that contains data for this tutorial</span></span>
 <span data-ttu-id="0f5f6-120">可以复制本主题中包含数据的查询，并将其粘贴到向导中。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-120">You can copy a query with data included in it from this topic and paste it into the wizard.</span></span> <span data-ttu-id="0f5f6-121">将需要 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 实例的名称以及足以对任何数据库进行只读访问的凭据。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-121">You will need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="0f5f6-122">本教程中的数据集查询使用文字数据，但必须由 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 实例处理查询以返回报表数据集所必需的元数据。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-122">The dataset query in the tutorial uses literal data, but the query must be processed by an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] to return the metadata that is required for a report dataset.</span></span>

 <span data-ttu-id="0f5f6-123">使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询的优势在于，其他所有报表生成器教程均使用相同的方法，这样，在您学习其他教程时，您已经提前知道了该做什么。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-123">The advantage of using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query is that all the other Report Builder tutorials use the same method, so when you do the other tutorials, you will already know what to do.</span></span>

 <span data-ttu-id="0f5f6-124">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询要求满足一些其他前提条件。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-124">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] query does require a few other prerequisites.</span></span> <span data-ttu-id="0f5f6-125">有关详细信息，请参阅[教程先决条件&#40;报表生成器&#41;](../report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-125">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

 [<span data-ttu-id="0f5f6-126">使用包含数据的 Transact-SQL 查询创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-126">Create the pie chart with a Transact-SQL query that contains data</span></span>](#CreatePieQueryData)

## <a name="also-in-this-article"></a><span data-ttu-id="0f5f6-127">本文还介绍了</span><span class="sxs-lookup"><span data-stu-id="0f5f6-127">Also in This Article</span></span>
 [<span data-ttu-id="0f5f6-128">运行向导之后</span><span class="sxs-lookup"><span data-stu-id="0f5f6-128">After You Run the Wizard</span></span>](#AfterWizard)

 [<span data-ttu-id="0f5f6-129">后续操作</span><span class="sxs-lookup"><span data-stu-id="0f5f6-129">What's Next</span></span>](#WhatsNext)

##  <a name="creating-the-pie-chart-with-xml-data"></a><a name="CreatePieChartXML"></a><span data-ttu-id="0f5f6-130">用 XML 数据创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-130">Creating the pie chart with XML data</span></span>

#### <a name="to-create-the-pie-chart-with-xml-data"></a><span data-ttu-id="0f5f6-131">用 XML 数据创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-131">To create the pie chart with XML data</span></span>

1.  <span data-ttu-id="0f5f6-132">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

     <span data-ttu-id="0f5f6-133">此时将显示 "**入门**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-133">The **Getting Started** dialog box appears.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="0f5f6-134">如果未显示 "**入门**" 对话框，请在 "**报表生成器**" 按钮中单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-134">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>

2.  <span data-ttu-id="0f5f6-135">在左窗格中，验证是否选择了 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-135">In the left pane, verify that **Report** is selected.</span></span>

3.  <span data-ttu-id="0f5f6-136">在右窗格中，单击 **“图表向导”** ，然后单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-136">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="0f5f6-137">在 **“选择数据集”** 页中，单击 **“创建数据集”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-137">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="0f5f6-138">在 **“选择数据源的连接”** 页中，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-138">In the **Choose a connection to a data source** page, click **New**.</span></span>

     <span data-ttu-id="0f5f6-139">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-139">The **Data Source Properties** dialog box opens.</span></span>

6.  <span data-ttu-id="0f5f6-140">可以将数据源命名为任何名称。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-140">You can name a data source anything you want.</span></span> <span data-ttu-id="0f5f6-141">在 **“名称”** 框中，键入 **MyPieChart**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-141">In the **Name** box, type **MyPieChart**.</span></span>

7.  <span data-ttu-id="0f5f6-142">在 "**选择连接类型**" 框中，单击 " **XML"。**</span><span class="sxs-lookup"><span data-stu-id="0f5f6-142">In the **Select connection type** box, click **XML.**</span></span>

8.  <span data-ttu-id="0f5f6-143">单击 "**凭据**" 选项卡，选择 "**使用当前 Windows 用户"。可能需要 Kerberos 委托**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-143">Click the **Credentials** tab, select **Use current Windows user. Kerberos delegation may be required**, and then click **OK**.</span></span>

9. <span data-ttu-id="0f5f6-144">在 **“选择数据源的连接”** 页中，单击 **MyPieChart**，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-144">In the **Choose a connection to a data source** page, click **MyPieChart**, and then click **Next**.</span></span>

10. <span data-ttu-id="0f5f6-145">复制以下文本，并将其粘贴到 "**设计查询**" 页中心的大框中。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-145">Copy the following text and paste it in the large box in the center of the **Design a query** page.</span></span>

    ```
    <Query>
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>
    <XmlData>
    <Root>
    <S Sales="150">
      <C FullName="Jae Pak" />
    </S>
    <S Sales="350">
      <C FullName="Jillian  Carson" />
    </S>
    <S Sales="250">
      <C FullName="Linda C Mitchell" />
    </S>
    <S Sales="500">
      <C FullName="Michael Blythe" />
    </S>
    <S Sales="450">
      <C FullName="Ranjit Varkey" />
    </S>
    </Root>
    </XmlData>
    </Query>
    ```

11. <span data-ttu-id="0f5f6-146">（可选）单击“运行”按钮 (!)，查看要用于图表的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

12. <span data-ttu-id="0f5f6-147">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-147">Click **Next**.</span></span>

13. <span data-ttu-id="0f5f6-148">在 **“选择图表类型”** 页中，单击 **“饼图”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-148">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

14. <span data-ttu-id="0f5f6-149">在“排列图表字段”页中，在“可用字段”框中双击“Sales”字段\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-149">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="0f5f6-150">注意，它将自动移动到 **“值”** 框，因为它是数字值。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-150">Note that it automatically moves to the **Values** box, because it is a numerical value.</span></span>

15. <span data-ttu-id="0f5f6-151">将“FullName”字段从“可用字段”框拖到“类别”框（或双击它，它将转到“类别”框），然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-151">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

16. <span data-ttu-id="0f5f6-152">默认情况下，在 "**选择样式**" 页中选择 "**海运**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-152">In the **Choose a style** page, **Ocean** is selected by default.</span></span> <span data-ttu-id="0f5f6-153">单击其他样式查看其外观。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-153">Click the other styles to see what they look like.</span></span>

17. <span data-ttu-id="0f5f6-154">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-154">Click **Finish**.</span></span>

     <span data-ttu-id="0f5f6-155">现在，将在设计图面上看到新饼图报表。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-155">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="0f5f6-156">看到的内容很有代表性。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-156">What you see is representational.</span></span> <span data-ttu-id="0f5f6-157">图例读取 Full Name 1、Full Name 2 等，而不是销售人员的名字，并且饼图切片的大小不准确。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-157">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="0f5f6-158">这只用于展示报表的外观。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-158">This is just to give you an idea of what your report will look like.</span></span>

18. <span data-ttu-id="0f5f6-159">若要看见实际的饼图，请在功能区的 **“主文件夹”** 选项卡上单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-159">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="0f5f6-160">![用于 "返回页首" 链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标")[返回页首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-160">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="creating-the-pie-chart-with-a-tsql-query"></a><a name="CreatePieQueryData"></a> <span data-ttu-id="0f5f6-161">使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-161">Creating the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query</span></span>

#### <a name="to-create-the-pie-chart-with-a-tsql-query-that-contains-data"></a><span data-ttu-id="0f5f6-162">使用包含数据的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查询创建饼图</span><span class="sxs-lookup"><span data-stu-id="0f5f6-162">To create the pie chart with a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query that contains data</span></span>

1.  <span data-ttu-id="0f5f6-163">单击 **“开始”**，依次指向 **“程序”**、 **Microsoft SQL Server 2012 Report Builder**，再单击 **“报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-163">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

2.  <span data-ttu-id="0f5f6-164">在 "**新建报表或数据集**" 对话框中，验证是否已在左窗格中选择 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-164">In the **New report or dataset** dialog box, verify that **Report** is selected in the left pane.</span></span>

3.  <span data-ttu-id="0f5f6-165">在右窗格中，单击 **“图表向导”**，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-165">In the right pane, click **Chart Wizard**, and then click **Create**.</span></span>

4.  <span data-ttu-id="0f5f6-166">在 **“选择数据集”** 页中，单击 **“创建数据集”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-166">In the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>

5.  <span data-ttu-id="0f5f6-167">在 **“选择数据源的连接”** 页中，选择现有数据源或浏览到报表服务器并选择一个数据源，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-167">In the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="0f5f6-168">您可能需要输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-168">You may need to enter a user name and password.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="0f5f6-169">只要您具有足够的权限，则选择哪一个数据源并不重要。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-169">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="0f5f6-170">您将不会从数据源中获取数据。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-170">You will not be getting data from the data source.</span></span> <span data-ttu-id="0f5f6-171">有关详细信息，请参阅[教程先决条件&#40;报表生成器&#41;](../report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-171">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md).</span></span>

6.  <span data-ttu-id="0f5f6-172">在 "**设计查询**" 页上，单击 "**编辑为文本**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-172">On the **Design a Query** page, click **Edit as Text**.</span></span>

7.  <span data-ttu-id="0f5f6-173">将以下查询粘贴到查询窗格中：</span><span class="sxs-lookup"><span data-stu-id="0f5f6-173">Paste the following query into the query pane:</span></span>

    ```
    SELECT 150 AS Sales, 'Jae Pak' AS FullName 
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName 
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName 
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName 
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName 
    ```

8.  <span data-ttu-id="0f5f6-174">（可选）单击“运行”按钮 (!)，查看要用于图表的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-174">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>

9. <span data-ttu-id="0f5f6-175">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-175">Click **Next**.</span></span>

10. <span data-ttu-id="0f5f6-176">在 **“选择图表类型”** 页中，单击 **“饼图”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-176">In the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span>

11. <span data-ttu-id="0f5f6-177">在“排列图表字段”页中，在“可用字段”框中双击“Sales”字段\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-177">In the **Arrange chart fields** page, double-click the **Sales** field in the **Available fields** box.</span></span>

     <span data-ttu-id="0f5f6-178">注意，它将自动移动到 **“值”** 框，因为它是数字值。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-178">Note that it automatically moves to the **Values** box, because it's a numerical value.</span></span>

12. <span data-ttu-id="0f5f6-179">将“FullName”字段从“可用字段”框拖到“类别”框（或双击它，它将转到“类别”框），然后单击“下一步”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-179">Drag the **FullName** field from the **Available fields** box to the **Categories** box (or double-click it; it will go to the **Categories** box), and then click **Next**.</span></span>

13. <span data-ttu-id="0f5f6-180">在 **“选择样式”** 页中，默认情况下“海洋”为选中状态。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-180">In the **Choose a style** page, Ocean is selected by default.</span></span> <span data-ttu-id="0f5f6-181">单击其他样式查看其外观。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-181">Click the other styles to see what they look like.</span></span>

14. <span data-ttu-id="0f5f6-182">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-182">Click **Finish**.</span></span>

     <span data-ttu-id="0f5f6-183">现在，将在设计图面上看到新饼图报表。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-183">You're now looking at your new pie chart report on the design surface.</span></span> <span data-ttu-id="0f5f6-184">看到的内容很有代表性。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-184">What you see is representational.</span></span> <span data-ttu-id="0f5f6-185">图例读取 Full Name 1、Full Name 2 等，而不是销售人员的名字，并且饼图切片的大小不准确。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-185">The legend reads Full Name 1, Full Name 2, etc., rather than the salespeople's names, and the size of the slices of pie are not accurate.</span></span> <span data-ttu-id="0f5f6-186">这只用于展示报表的外观。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-186">This is just to give you an idea of what your report will look like.</span></span>

15. <span data-ttu-id="0f5f6-187">若要看见实际的饼图，请在功能区的 **“主文件夹”** 选项卡上单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-187">To see your actual pie chart, click **Run** on the **Home** tab of the Ribbon.</span></span>

 <span data-ttu-id="0f5f6-188">![用于 "返回页首" 链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标")[返回页首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-188">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="after-you-run-the-wizard"></a><a name="AfterWizard"></a> <span data-ttu-id="0f5f6-189">运行向导之后</span><span class="sxs-lookup"><span data-stu-id="0f5f6-189">After You Run the Wizard</span></span>
 <span data-ttu-id="0f5f6-190">现在您便拥有了饼图报表，从而可以对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-190">Now that you have your pie chart report, you can play with it.</span></span> <span data-ttu-id="0f5f6-191">在功能区的 **“运行”** 选项卡上，单击 **“设计”**，这样可以继续修改它。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-191">On the **Run** tab of the Ribbon, click **Design**, so you can continue modifying it.</span></span>

### <a name="make-the-chart-bigger"></a><span data-ttu-id="0f5f6-192">放大图表</span><span class="sxs-lookup"><span data-stu-id="0f5f6-192">Make the chart bigger</span></span>
 <span data-ttu-id="0f5f6-193">您可能希望放大饼图。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-193">You may want the pie chart to be bigger.</span></span> <span data-ttu-id="0f5f6-194">单击图表（但不要单击图表中的任何元素）以选择它，并拖动右下角以调整它的大小。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-194">Click the chart, but not on any element in the chart, to select it and drag the lower-right corner to resize it.</span></span>

### <a name="add-a-report-title"></a><span data-ttu-id="0f5f6-195">添加报表标题</span><span class="sxs-lookup"><span data-stu-id="0f5f6-195">Add a report title</span></span>
 <span data-ttu-id="0f5f6-196">选择图表顶部的词语 **“图表标题”** ，然后键入标题，例如 **Sales Pie Chart**。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-196">Select the words **Chart title** at the top of the chart, and then type a title, such as **Sales Pie Chart**.</span></span>

### <a name="add-percentages"></a><span data-ttu-id="0f5f6-197">添加百分比</span><span class="sxs-lookup"><span data-stu-id="0f5f6-197">Add percentages</span></span>

##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="0f5f6-198">在饼图上显示百分比值</span><span class="sxs-lookup"><span data-stu-id="0f5f6-198">To display percentage values as labels on a pie chart</span></span>

1.  <span data-ttu-id="0f5f6-199">右键单击饼图并选择 "**显示数据标签**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-199">Right-click on the pie chart and select **Show Data Labels**.</span></span> <span data-ttu-id="0f5f6-200">数据标签应显示在饼图上的每个切片上。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-200">The data labels should appear within each slice on the pie chart.</span></span>

2.  <span data-ttu-id="0f5f6-201">右键单击标签并选择 "**序列标签属性**"。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-201">Right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="0f5f6-202">此时将显示 **“序列标签属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-202">The **Series Label Properties** dialog box appears.</span></span>

3.  <span data-ttu-id="0f5f6-203">`#PERCENT{P0}`"**标签数据**" 选项的类型。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-203">Type `#PERCENT{P0}` for the **Label data** option.</span></span>

     <span data-ttu-id="0f5f6-204">`{P0}` 提供没有小数位的百分比。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-204">The `{P0}` gives you the percentage without decimal places.</span></span> <span data-ttu-id="0f5f6-205">如果只是键入 `#PERCENT`，则数字将有两位小数。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-205">If you type just `#PERCENT`, your numbers will have two decimal places.</span></span> <span data-ttu-id="0f5f6-206">`#PERCENT` 是执行计算或函数的关键字，还有很多这样的关键字。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-206">`#PERCENT` is a keyword that performs a calculation or function for you; there are many others.</span></span>

 <span data-ttu-id="0f5f6-207">有关自定义饼图标签和图例的详细信息，请参阅[在饼图上显示百分比值&#40;报表生成器和 SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) 和 [更改图例项文本&#40;报表生成器和 SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-207">For more information about customizing chart labels and legends, see [Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) and [Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](../report-design/chart-legend-change-item-text-report-builder.md).</span></span>

 <span data-ttu-id="0f5f6-208">![用于 "返回页首" 链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标")[返回页首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-208">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

##  <a name="whats-next"></a><a name="WhatsNext"></a><span data-ttu-id="0f5f6-209">下一步是什么？</span><span class="sxs-lookup"><span data-stu-id="0f5f6-209">What's Next?</span></span>
 <span data-ttu-id="0f5f6-210">现在，你已在报表生成器中创建了第一个报表，接下来可以尝试其他教程并开始从你自己的数据创建报表。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-210">Now that you have created your first report in Report Builder, you are ready to try the other tutorials and to start creating reports from your own data.</span></span> <span data-ttu-id="0f5f6-211">若要运行报表生成器，你需要有权使用*连接字符串*访问数据源（如数据库），这会将你实际连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-211">To run Report Builder, you need permission to access your data sources, such as databases, with a *connection string*, which actually connects you to the data source.</span></span> <span data-ttu-id="0f5f6-212">系统管理员拥有此信息，并且可以为您设置相应的权限。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-212">Your system administrator will have this information and can set you up.</span></span>

 <span data-ttu-id="0f5f6-213">若要完成其他教程，需要 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 实例的名称以及足以对任何数据库进行只读访问的凭据。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-213">To work through the other tutorials, you need the name of an instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] and credentials sufficient for read-only access to any database.</span></span> <span data-ttu-id="0f5f6-214">系统管理员也可以为您设置该权限。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-214">Your system administrator can also set that up for you.</span></span>

 <span data-ttu-id="0f5f6-215">最后，若要将报表保存到报表服务器或与报表服务器集成的 SharePoint 站点，需要具有 URL 和相应权限。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-215">Finally, to save your reports to a report server or a SharePoint site that is integrated with a report server, you need the URL and permissions.</span></span> <span data-ttu-id="0f5f6-216">可以直接从您的计算机运行您创建的任何报表，但如果从报表服务器或 SharePoint 站点运行报表，则报表会有更多功能。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-216">You can run any report you create directly from your computer, but reports have more functionality when run from the report server or SharePoint site.</span></span> <span data-ttu-id="0f5f6-217">您需要有一定权限才能运行您的报表或报表服务器或 SharePoint 站点上发布的其他报表。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-217">You need permissions to run your reports or others from the report server or SharePoint site where they are published.</span></span> <span data-ttu-id="0f5f6-218">请与系统管理员联系以获取访问权限。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-218">Talk to your system administrator to obtain access.</span></span>

 <span data-ttu-id="0f5f6-219">在入门之前，可能有必要了解一些概念和术语。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-219">It may help to read about some of the concepts and terms before you get started.</span></span> <span data-ttu-id="0f5f6-220">有关详细信息，请参阅[报表创作概念 &#40;报表生成器和 SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-220">For more information, see [Report Authoring Concepts &#40;Report Builder and SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="0f5f6-221">而且，在创建第一个报表之前，应当花一些时间进行规划。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-221">Also, spend some time planning, before you create your first report.</span></span> <span data-ttu-id="0f5f6-222">这将需要较长时间。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-222">It will be time well spent.</span></span> <span data-ttu-id="0f5f6-223">有关详细信息，请参阅[规划报表 &#40;报表生成器&#41;](../report-design/planning-a-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="0f5f6-223">For more information, see [Planning a Report &#40;Report Builder&#41;](../report-design/planning-a-report-report-builder.md).</span></span>

 <span data-ttu-id="0f5f6-224">![用于 "返回页首" 链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标")[返回页首](#TwoWays)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-224">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#TwoWays)</span></span>

## <a name="see-also"></a><span data-ttu-id="0f5f6-225">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f5f6-225">See Also</span></span>
 <span data-ttu-id="0f5f6-226">[SQL Server 2014 中](report-builder-in-sql-server-2016.md)[报表生成器&#41;报表生成器教程 &#40;](../report-builder-tutorials.md)</span><span class="sxs-lookup"><span data-stu-id="0f5f6-226">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder-in-sql-server-2016.md)</span></span>


