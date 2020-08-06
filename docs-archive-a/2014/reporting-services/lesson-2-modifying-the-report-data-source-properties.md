---
title: 第 2 课：修改报表数据源属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c962b0ff-ce8a-4742-8262-dc730901afcf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05e56a58ce28ee1e1e450d3af012cbd1ffe668ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578719"
---
# <a name="lesson-2-modifying-the-report-data-source-properties"></a><span data-ttu-id="87f9c-102">Lesson 2: Modifying the Report Data Source Properties</span><span class="sxs-lookup"><span data-stu-id="87f9c-102">Lesson 2: Modifying the Report Data Source Properties</span></span>
  <span data-ttu-id="87f9c-103">在本课中，您将使用报表管理器来选择要传递给收件人的报表。</span><span class="sxs-lookup"><span data-stu-id="87f9c-103">In this lesson, you will use Report Manager to select a report that will be delivered to recipients.</span></span> <span data-ttu-id="87f9c-104">你将定义的数据驱动订阅将分发在 **创建基本表报表（SSRS 教程）** 教程中创建的 [创建基本表报表（SSRS 教程）](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)报表。</span><span class="sxs-lookup"><span data-stu-id="87f9c-104">The data-driven subscription that you will define will distribute the **Sales Order** report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="87f9c-105">在接下来的步骤中，将修改此报表使用的数据源连接信息，以获取数据。</span><span class="sxs-lookup"><span data-stu-id="87f9c-105">In the steps that follow, you will modify the data source connection information used by the report to get data.</span></span> <span data-ttu-id="87f9c-106">只有使用 **已存储凭据** 访问报表数据源的报表才能通过数据驱动订阅进行分发。</span><span class="sxs-lookup"><span data-stu-id="87f9c-106">Only reports that use **stored credentials** to access a report data source can be distributed through a data-driven subscription.</span></span> <span data-ttu-id="87f9c-107">已存储凭据是处理无人参与的报表所必需的。</span><span class="sxs-lookup"><span data-stu-id="87f9c-107">Stored credentials are necessary for unattended report processing.</span></span>

 <span data-ttu-id="87f9c-108">您还将修改数据集和报表以便使用参数来筛选 `[Order]` 上的报表，这样，订阅可为特定的顺序和呈现格式输出不同的报表实例。</span><span class="sxs-lookup"><span data-stu-id="87f9c-108">You will also modify the dataset and report to use a parameter to filter the report on the `[Order]` so the subscription can output different instances of the report for specific orders and rendering formats.</span></span>

 <span data-ttu-id="87f9c-109">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="87f9c-109">**In this topic:**</span></span>

-   [<span data-ttu-id="87f9c-110">修改数据源属性</span><span class="sxs-lookup"><span data-stu-id="87f9c-110">To Modify the Data Source Properties</span></span>](#bkmk_modify_datasource)

-   [<span data-ttu-id="87f9c-111">修改 AdventureWorksDataset</span><span class="sxs-lookup"><span data-stu-id="87f9c-111">To Modify the AdventureWorksDataset</span></span>](#bkmk_modify_dataset)

-   [<span data-ttu-id="87f9c-112">添加报表参数并重新发布报表</span><span class="sxs-lookup"><span data-stu-id="87f9c-112">To Add a Report Parameter and Republish the Report</span></span>](#bkmk_add_reportparameter)

-   [<span data-ttu-id="87f9c-113">重新部署报表</span><span class="sxs-lookup"><span data-stu-id="87f9c-113">To Re-deploy the Report</span></span>](#bkmk_redeploy)

##  <a name="to-modify-the-data-source-properties"></a><a name="bkmk_modify_datasource"></a><span data-ttu-id="87f9c-114">修改数据源属性</span><span class="sxs-lookup"><span data-stu-id="87f9c-114">To Modify the Data Source Properties</span></span>

1.  <span data-ttu-id="87f9c-115">启动[报表管理器 &#40;SSRS 本机模式下&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)具有管理员权限，例如，右键单击 Internet Explorer 图标，然后单击 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="87f9c-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>

2.  <span data-ttu-id="87f9c-116">浏览到包含 **Sales Orders** 报表的文件夹，在该报表的上下文菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-116">Browse to the folder containing the **Sales Orders** report and in the context menu of the report, click **Manage**.</span></span>

     <span data-ttu-id="87f9c-117">![打开报表上下文菜单并选择管理](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "打开报表上下文菜单并选择管理")</span><span class="sxs-lookup"><span data-stu-id="87f9c-117">![Open the report context menu and select manage](../../2014/tutorials/media/ssrs-tutorial-datadriven-manage-report.gif "Open the report context menu and select manage")</span></span>

3.  <span data-ttu-id="87f9c-118">单击 **“数据源”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="87f9c-118">Click the **Data Sources** tab.</span></span>

4.  <span data-ttu-id="87f9c-119">对于 **“连接类型”**，请选择 **Microsoft SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-119">For **Connection Type**, select **Microsoft SQL Server**.</span></span>

5.  <span data-ttu-id="87f9c-120">自定义数据源连接字符串如下并且它假定示例数据库位于本地数据库服务器上：</span><span class="sxs-lookup"><span data-stu-id="87f9c-120">The custom data source connection string will be the following and it assumes that the sample database is on a local database server:</span></span>

    ```
    Data source=localhost; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="87f9c-121">单击 **“安全存储在报表服务器中的凭据”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-121">Click **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="87f9c-122">输入用户名（使用 *domain\user* 格式）和密码。</span><span class="sxs-lookup"><span data-stu-id="87f9c-122">Type your user name (use the format *domain\user*) and password.</span></span> <span data-ttu-id="87f9c-123">如果您没有访问 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库的权限，请指定具有此权限的登录名。</span><span class="sxs-lookup"><span data-stu-id="87f9c-123">If you do not have permission to access the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database, specify a login that does.</span></span>

8.  <span data-ttu-id="87f9c-124">单击 **“在与数据源建立连接时用作 Windows 凭据”**，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-124">Click **Use as windows credentials when connecting to the data source**, and then click **OK**.</span></span> <span data-ttu-id="87f9c-125">如果没有使用域帐户（例如，如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录），请不要单击该复选框。</span><span class="sxs-lookup"><span data-stu-id="87f9c-125">If you are not using a domain account (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login), do not click this checkbox.</span></span>

9. <span data-ttu-id="87f9c-126">若要验证是否能连接到数据源，请单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="87f9c-126">Click **Test Connection** to verify you can connect to the data source.</span></span>

10. <span data-ttu-id="87f9c-127">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="87f9c-127">Click **Apply**.</span></span>

11. <span data-ttu-id="87f9c-128">查看报表以验证报表是否以指定的凭据运行。</span><span class="sxs-lookup"><span data-stu-id="87f9c-128">View the report to verify that the report runs with the credentials you specified.</span></span> <span data-ttu-id="87f9c-129">若要查看报表，请单击 "**视图**" 选项卡。请注意，在报表打开后，您必须选择一个雇员姓名，然后单击 "**查看报告**" 按钮以查看报表。</span><span class="sxs-lookup"><span data-stu-id="87f9c-129">To view the report, click the **View** tab. Note that once the report is open, you must select an Employee name and then click the **View Report** button to view the report.</span></span>

##  <a name="to-modify-the-adventureworksdataset"></a><a name="bkmk_modify_dataset"></a><span data-ttu-id="87f9c-130">修改 AdventureWorksDataset</span><span class="sxs-lookup"><span data-stu-id="87f9c-130">To Modify the AdventureWorksDataset</span></span>

1.  <span data-ttu-id="87f9c-131">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中打开 Sales Orders 报表。</span><span class="sxs-lookup"><span data-stu-id="87f9c-131">Open the Sales Orders report in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]</span></span>

2.  <span data-ttu-id="87f9c-132">右键单击数据集 `AdventureWorksDataset`，然后单击“数据集属性”  。</span><span class="sxs-lookup"><span data-stu-id="87f9c-132">Right-click the dataset `AdventureWorksDataset` and click **Dataset Properties**.</span></span>

3.  <span data-ttu-id="87f9c-133">将语句 `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` 添加到 `Group By` 语句之前。</span><span class="sxs-lookup"><span data-stu-id="87f9c-133">Add the statement `WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)` before the `Group By` statement.</span></span> <span data-ttu-id="87f9c-134">完整查询语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="87f9c-134">The full query syntax is the following:</span></span>

    ```
    SELECT soh.OrderDate AS Date, soh.SalesOrderNumber AS [Order], pps.Name AS Subcat, pp.Name AS Product, SUM(sd.OrderQty) AS Qty, SUM(sd.LineTotal)  AS LineTotal
    FROM Sales.SalesPerson AS sp INNER JOIN
      Sales.SalesOrderHeader AS soh ON sp.BusinessEntityID = soh.SalesPersonID INNER JOIN
       Sales.SalesOrderDetail AS sd ON sd.SalesOrderID = soh.SalesOrderID INNER JOIN
       Production.Product AS pp ON sd.ProductID = pp.ProductID
    INNER JOIN
       Production.ProductSubcategory AS pps ON pp.ProductSubcategoryID = pps.ProductSubcategoryID 
    INNER JOIN
        Production.ProductCategory AS ppc ON ppc.ProductCategoryID = pps.ProductCategoryID

    WHERE (UPPER(SalesOrderNumber) =UPPER(@OrderNumber) or  @OrderNumber IS NULL)

    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name, soh.SalesPersonID
    HAVING (ppc.Name = 'Clothing')
    ```

4.  <span data-ttu-id="87f9c-135">单击 **“确定”**</span><span class="sxs-lookup"><span data-stu-id="87f9c-135">Click **OK**</span></span>

##  <a name="to-add-a-report-parameter-and-republish-the-report"></a><a name="bkmk_add_reportparameter"></a><span data-ttu-id="87f9c-136">添加报表参数并重新发布报表</span><span class="sxs-lookup"><span data-stu-id="87f9c-136">To Add a Report Parameter and Republish the Report</span></span>

1.  <span data-ttu-id="87f9c-137">在 **“报表数据”** 窗格中，单击 **“新建”** ，然后单击 **“参数...”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-137">In the **Report Data** pane click **New** and then click **Parameter...**</span></span>

2.  <span data-ttu-id="87f9c-138">在 **“名称”** 中，键入 `OrderNumber`。</span><span class="sxs-lookup"><span data-stu-id="87f9c-138">In **Name**, type `OrderNumber`.</span></span>

3.  <span data-ttu-id="87f9c-139">在 **“提示”** 中，键入 `OrderNumber`。</span><span class="sxs-lookup"><span data-stu-id="87f9c-139">In **Prompt**, type `OrderNumber`.</span></span>

4.  <span data-ttu-id="87f9c-140">选择“允许空值("")”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87f9c-140">Select **Allow blank value ("")**.</span></span>

5.  <span data-ttu-id="87f9c-141">选择 **“允许 Null 值”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-141">Select **Allow null value**.</span></span>

6.  <span data-ttu-id="87f9c-142">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="87f9c-142">Click **OK**.</span></span> <span data-ttu-id="87f9c-143">该参数将添加到 **“报表数据窗格”** ，其外观如下图所示：</span><span class="sxs-lookup"><span data-stu-id="87f9c-143">The parameter will be added to the **Report Data pane** and it will look like the following image:</span></span>

     <span data-ttu-id="87f9c-144">![“报表数据”窗格中会添加新参数](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "“报表数据”窗格中会添加新参数")</span><span class="sxs-lookup"><span data-stu-id="87f9c-144">![The new parameter is added to the Report Data pane](../../2014/tutorials/media/ssrs-tutorial-datadriven-parameter.gif "The new parameter is added to the Report Data pane")</span></span>

7.  <span data-ttu-id="87f9c-145">单击 **“预览”** 选项卡，运行该报表。请注意报表顶部的参数输入框。</span><span class="sxs-lookup"><span data-stu-id="87f9c-145">Click the **Preview** tab to run the report.Note the parameter input box at the top of the report.</span></span> <span data-ttu-id="87f9c-146">可以：</span><span class="sxs-lookup"><span data-stu-id="87f9c-146">You can either:</span></span>

    -   <span data-ttu-id="87f9c-147">在不使用参数的情况下单击“查看报表”以便看到完整的报表。</span><span class="sxs-lookup"><span data-stu-id="87f9c-147">Click View Report to see the full report without using a parameter.</span></span>

    -   <span data-ttu-id="87f9c-148">取消选择 Null 选项，然后键入订单号，例如 so71949，以便只查看报表中的一个订单。</span><span class="sxs-lookup"><span data-stu-id="87f9c-148">Unselect the Null option and type an order number, for example so71949 to view only the one order in the report.</span></span>

         <span data-ttu-id="87f9c-149">![参数区可见的报表查看器](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "参数区可见的报表查看器")</span><span class="sxs-lookup"><span data-stu-id="87f9c-149">![Report viewer with parameter area visible](../../2014/tutorials/media/ssrs-tutorial-datadriven-reportviewer-parameter.gif "Report viewer with parameter area visible")</span></span>

8.  <span data-ttu-id="87f9c-150">重新部署报表，以便下一课程中的订阅配置可利用您在本课程中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="87f9c-150">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="87f9c-151">有关在表教程中使用的项目属性的详细信息，请参阅[第6课：添加分组和总计 &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)中的 "将报表发布到报表服务器 (可选的) " 部分。</span><span class="sxs-lookup"><span data-stu-id="87f9c-151">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

##  <a name="to-re-deploy-the-report"></a><a name="bkmk_redeploy"></a><span data-ttu-id="87f9c-152">重新部署报表</span><span class="sxs-lookup"><span data-stu-id="87f9c-152">To Re-deploy the Report</span></span>

1.  <span data-ttu-id="87f9c-153">重新部署报表，以便下一课程中的订阅配置可利用您在本课程中进行的更改。</span><span class="sxs-lookup"><span data-stu-id="87f9c-153">Re-deploy the report so the subscription configuration in the next lesson can utilize the changes you made in this lesson.</span></span> <span data-ttu-id="87f9c-154">有关在表教程中使用的项目属性的详细信息，请参阅[第6课：添加分组和总计 &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)中的 "将报表发布到报表服务器 (可选的) " 部分。</span><span class="sxs-lookup"><span data-stu-id="87f9c-154">For more information on the project properties used in the table tutorial, see section 'To Publish the Report to the Report Server (Optional)' of [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>

2.  <span data-ttu-id="87f9c-155">在工具栏上，单击 **“生成”** ，然后单击 **“部署教程”**。</span><span class="sxs-lookup"><span data-stu-id="87f9c-155">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87f9c-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="87f9c-156">Next Steps</span></span>
 <span data-ttu-id="87f9c-157">您已成功配置了报表，从而可使用已存储凭据获取数据。</span><span class="sxs-lookup"><span data-stu-id="87f9c-157">You successfully configured the report to get data using stored credentials.</span></span> <span data-ttu-id="87f9c-158">接下来，将使用报表管理器中的“数据驱动订阅”页来指定订阅。</span><span class="sxs-lookup"><span data-stu-id="87f9c-158">Next, you specify the subscription using the Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="87f9c-159">请参阅 [第 3 课：定义数据驱动订阅](../reporting-services/lesson-3-defining-a-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="87f9c-159">See [Lesson 3: Defining a Data-Driven Subscription](../reporting-services/lesson-3-defining-a-data-driven-subscription.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87f9c-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87f9c-160">See Also</span></span>
 <span data-ttu-id="87f9c-161">[管理报表数据源](report-data/manage-report-data-sources.md)[为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)[创建数据驱动订阅 &#40;Ssrs 教程&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [创建基本表报表 &#40;SSRS 教程&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="87f9c-161">[Manage Report Data Sources](report-data/manage-report-data-sources.md) [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)</span></span>


