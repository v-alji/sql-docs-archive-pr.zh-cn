---
title: 第 8 课：创建数据筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c11d4cf83619e53cd7e8f00091c66cc8e50ad76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578698"
---
# <a name="lesson-8-create-a-data-filter"></a><span data-ttu-id="69d29-102">第 8 课：创建数据筛选器</span><span class="sxs-lookup"><span data-stu-id="69d29-102">Lesson 8: Create a Data Filter</span></span>
  <span data-ttu-id="69d29-103">在父报表上添加钻取操作后，接下来将创建一个数据筛选器，用于为子报表定义的数据表。</span><span class="sxs-lookup"><span data-stu-id="69d29-103">After you add a drillthrough action on the parent report, your next step is to create a data filter for the data table that you defined for the child report.</span></span>  
  
 <span data-ttu-id="69d29-104">可创建基于表的筛选器 **或** 查询筛选器用于钻取报表。</span><span class="sxs-lookup"><span data-stu-id="69d29-104">You can create a table-based filter **or** a query filter for the drillthrough report.</span></span> <span data-ttu-id="69d29-105">本课对这两种选择均加以说明。</span><span class="sxs-lookup"><span data-stu-id="69d29-105">This lesson provides instructions for both options.</span></span>  
  
## <a name="table-based-filter"></a><span data-ttu-id="69d29-106">基于表的筛选器</span><span class="sxs-lookup"><span data-stu-id="69d29-106">Table-Based Filter</span></span>  
 <span data-ttu-id="69d29-107">需要完成以下任务才能实现基于表的筛选器。</span><span class="sxs-lookup"><span data-stu-id="69d29-107">You need to complete the following tasks to implement a table-based filter.</span></span>  
  
-   <span data-ttu-id="69d29-108">向子报表中的 tablix 添加一个筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="69d29-108">Add a filter expression to the tablix in the child report.</span></span>  
  
-   <span data-ttu-id="69d29-109">创建一个函数，用于从 `PurchaseOrderDetail` 表选择未筛选的数据。</span><span class="sxs-lookup"><span data-stu-id="69d29-109">Create a function that selects unfiltered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="69d29-110">添加一个事件处理程序，用于将 `PurchaseOrderDetail` DataTable 绑定到子报表。</span><span class="sxs-lookup"><span data-stu-id="69d29-110">Add an event handler that binds the `PurchaseOrderDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a><span data-ttu-id="69d29-111">向子报表中的 tablix 添加一个筛选表达式</span><span class="sxs-lookup"><span data-stu-id="69d29-111">To add a filter expression to the tablix in the child report</span></span>  
  
1.  <span data-ttu-id="69d29-112">打开子报表。</span><span class="sxs-lookup"><span data-stu-id="69d29-112">Open the child report.</span></span>  
  
2.  <span data-ttu-id="69d29-113">选择 tablix 中的列标题，右键单击列标题上方显示的灰色单元，然后单击 " **Tablix 属性**"。</span><span class="sxs-lookup"><span data-stu-id="69d29-113">Select a column heading in the tablix, right-click the gray cell that appears above the column heading, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="69d29-114">单击 "**筛选器**" 页，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="69d29-114">Click on the **Filters** page, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="69d29-115">在 "**表达式**" 字段中，单击 `ProductID` 下拉列表中的。</span><span class="sxs-lookup"><span data-stu-id="69d29-115">In the **Expression** filed, click `ProductID` from the drop-down list.</span></span> <span data-ttu-id="69d29-116">筛选器即应用于此列。</span><span class="sxs-lookup"><span data-stu-id="69d29-116">This is the column to which you apply the filter.</span></span>  
  
5.  <span data-ttu-id="69d29-117">**=** 在 "**运算符**" 下拉列表中单击等于 () 运算符。</span><span class="sxs-lookup"><span data-stu-id="69d29-117">Click the equal (**=**) operator in the **Operator** drop-down list.</span></span>  
  
6.  <span data-ttu-id="69d29-118">单击 "**值**" 字段旁边的 "表达式" 按钮，在 "**类别**" 区域中单击 "**参数**"，然后 `productid` 在 "**值**" 区域中双击。</span><span class="sxs-lookup"><span data-stu-id="69d29-118">Click the expression button next to the **Value** field, click **Parameters** in the **Category** area, and then double-click `productid` in the **Values** area.</span></span> <span data-ttu-id="69d29-119">“为以下项设置表达式: 值”字段现在应包含类似于 =Parameters!productid.Value 的表达式   。</span><span class="sxs-lookup"><span data-stu-id="69d29-119">The **Set expression for: Value** field should now contain expression similar to **=Parameters!productid.Value**.</span></span>  
  
7.  <span data-ttu-id="69d29-120">单击 **"确定"，** 然后在 " **Tablix 属性**" 对话框中再次单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="69d29-120">Click **OK,** and **OK** again in the **Tablix Properties** dialog box.</span></span>  
  
8.  <span data-ttu-id="69d29-121">保存 .rdlc 文件。</span><span class="sxs-lookup"><span data-stu-id="69d29-121">Save the .rdlc file.</span></span>  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a><span data-ttu-id="69d29-122">创建一个函数，用于从 PurchaseOrdeDetail 表选择未筛选的数据</span><span class="sxs-lookup"><span data-stu-id="69d29-122">To create a function that selects unfiltered data from the PurchaseOrdeDetail table</span></span>  
  
1.  <span data-ttu-id="69d29-123">在解决方案资源管理器中，展开 Default.aspx，然后双击 Default.aspx.cs。</span><span class="sxs-lookup"><span data-stu-id="69d29-123">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="69d29-124">创建一个新函数，该函数接受 `productid` 类型为 Integer 的参数，并返回一个 `datatable` 对象，并执行以下。</span><span class="sxs-lookup"><span data-stu-id="69d29-124">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object, and does the following.</span></span>  
  
    1.  <span data-ttu-id="69d29-125">创建 `DataSet2` 在第[4 课：定义用于子报表的数据连接和](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)数据表的步骤2中创建的数据集的实例。</span><span class="sxs-lookup"><span data-stu-id="69d29-125">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="69d29-126">创建一个到 SqlServer 数据库的连接，以执行在 **第 4 课：定义用于子报表的数据连接和 DataTable**中定义的查询。</span><span class="sxs-lookup"><span data-stu-id="69d29-126">Create a connection to the SqlServer database to execute the query defined in **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="69d29-127">该查询将返回未筛选的数据。</span><span class="sxs-lookup"><span data-stu-id="69d29-127">The query will return unfiltered data.</span></span>  
  
    4.  <span data-ttu-id="69d29-128">通过执行该查询，用未筛选的数据填充 DataSet 实例。</span><span class="sxs-lookup"><span data-stu-id="69d29-128">Fill the DataSet instance with the unfiltered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="69d29-129">返回 `PurchaseOrderDetail` DataTable。</span><span class="sxs-lookup"><span data-stu-id="69d29-129">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="69d29-130">该函数将类似于下面这个函数（仅供参考。</span><span class="sxs-lookup"><span data-stu-id="69d29-130">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="69d29-131">可采用您所需的任意模式提取子报表所需的数据。）</span><span class="sxs-lookup"><span data-stu-id="69d29-131">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a><span data-ttu-id="69d29-132">添加一个事件处理程序，用于将 PurchaseOrderDetail DataTable 绑定到子报表</span><span class="sxs-lookup"><span data-stu-id="69d29-132">To add an event handler that binds the PurchaseOrderDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="69d29-133">打开 Default.aspx。</span><span class="sxs-lookup"><span data-stu-id="69d29-133">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="69d29-134">右键单击 ReportViewer 控件，然后单击 "**属性"。**</span><span class="sxs-lookup"><span data-stu-id="69d29-134">Right click the ReportViewer control, and then click **Properties.**</span></span>  
  
3.  <span data-ttu-id="69d29-135">在 "**属性**" 页上，单击 "**事件**" 图标。</span><span class="sxs-lookup"><span data-stu-id="69d29-135">On the **Properties** page, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="69d29-136">双击**钻取**事件。</span><span class="sxs-lookup"><span data-stu-id="69d29-136">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="69d29-137">随后将在代码中添加一个事件处理程序部分，类似于下面这个代码块。</span><span class="sxs-lookup"><span data-stu-id="69d29-137">This will add an event handler section in the code, which will look similar to the below block.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="69d29-138">将事件处理程序填写完整。</span><span class="sxs-lookup"><span data-stu-id="69d29-138">Complete the event handler.</span></span> <span data-ttu-id="69d29-139">它应包括以下功能。</span><span class="sxs-lookup"><span data-stu-id="69d29-139">It should include the following functionalty.</span></span>  
  
    1.  <span data-ttu-id="69d29-140">从 *DrillthroughEventArgs* 参数提取子报表对象引用。</span><span class="sxs-lookup"><span data-stu-id="69d29-140">Fetch the child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="69d29-141">调用函数，`GetPurchaseOrderDetail`</span><span class="sxs-lookup"><span data-stu-id="69d29-141">Call the function, `GetPurchaseOrderDetail`</span></span>  
  
    3.  <span data-ttu-id="69d29-142">将 `PurchaseOrderDetail` DataTable 与报表的相应数据源绑定。</span><span class="sxs-lookup"><span data-stu-id="69d29-142">Bind the `PurchaseOrderDetail` DataTable with the report's corresponding data source.</span></span>  
  
         <span data-ttu-id="69d29-143">填写完整的事件处理程序代码将类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="69d29-143">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="69d29-144">保存文件。</span><span class="sxs-lookup"><span data-stu-id="69d29-144">Save the file.</span></span>  
  
## <a name="query-filter"></a><span data-ttu-id="69d29-145">查询筛选器</span><span class="sxs-lookup"><span data-stu-id="69d29-145">Query Filter</span></span>  
 <span data-ttu-id="69d29-146">需要完成以下任务才能实现查询筛选器。</span><span class="sxs-lookup"><span data-stu-id="69d29-146">You need to complete the following tasks to implement a query filter.</span></span>  
  
-   <span data-ttu-id="69d29-147">创建一个函数，用于从 `PurchaseOrderDetail` 表选择经过筛选的数据。</span><span class="sxs-lookup"><span data-stu-id="69d29-147">Create a function that selected filtered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="69d29-148">添加一个事件处理程序，用于检索参数值并将 `PurchaseOrdeDetail` DataTable 绑定到子报表。</span><span class="sxs-lookup"><span data-stu-id="69d29-148">Add an event handler that retrieves parameter values and binds the `PurchaseOrdeDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a><span data-ttu-id="69d29-149">创建一个函数，用于从 PurchaseOrderDetail 表选择经过筛选的数据</span><span class="sxs-lookup"><span data-stu-id="69d29-149">To create a function that selects filtered data from the PurchaseOrderDetail table</span></span>  
  
1.  <span data-ttu-id="69d29-150">在解决方案资源管理器中，展开 Default.aspx，然后双击 Default.aspx.cs。</span><span class="sxs-lookup"><span data-stu-id="69d29-150">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="69d29-151">创建一个新函数，该函数接受类型为 Integer 的参数 `productid` 并返回 `datatable` 对象，然后执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="69d29-151">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object and does the following.</span></span>  
  
    1.  <span data-ttu-id="69d29-152">创建 `DataSet2` 在第[4 课：定义用于子报表的数据连接和](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)数据表的步骤2中创建的数据集的实例。</span><span class="sxs-lookup"><span data-stu-id="69d29-152">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="69d29-153">创建一个到 SqlServer 数据库的连接，以执行在 **第 4 课：定义用于子报表的数据连接和 DataTable**中定义的查询。</span><span class="sxs-lookup"><span data-stu-id="69d29-153">Create a connection to the SqlServer database to execute the query defined **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="69d29-154">该查询将包括参数 `productid` 以确保根据在父报表中选择的 `ProductID` 筛选所返回的数据。</span><span class="sxs-lookup"><span data-stu-id="69d29-154">The query will include a parameter, `productid`, to make sure the data returned is filtered based on the `ProductID` selected in the parent report.</span></span>  
  
    4.  <span data-ttu-id="69d29-155">通过执行该查询，用经过筛选的数据填充 DataSet 实例。</span><span class="sxs-lookup"><span data-stu-id="69d29-155">Fill the DataSet instance with the filtered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="69d29-156">返回 `PurchaseOrderDetail` DataTable。</span><span class="sxs-lookup"><span data-stu-id="69d29-156">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="69d29-157">该函数将类似于下面这个函数（仅供参考。</span><span class="sxs-lookup"><span data-stu-id="69d29-157">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="69d29-158">可采用您所需的任意模式提取子报表所需的数据。）</span><span class="sxs-lookup"><span data-stu-id="69d29-158">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a><span data-ttu-id="69d29-159">添加一个事件处理程序，用于检索参数值并将 PurchaseOrdeDetail DataTable 绑定到子报表</span><span class="sxs-lookup"><span data-stu-id="69d29-159">To add an event handler that retrieves parameter values and binds the PurchaseOrdeDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="69d29-160">打开 Default.aspx。</span><span class="sxs-lookup"><span data-stu-id="69d29-160">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="69d29-161">右键单击 ReportViewer 控件，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="69d29-161">Right-click the ReportViewer control, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="69d29-162">在 "**属性**" 窗格中，单击 "**事件**" 图标。</span><span class="sxs-lookup"><span data-stu-id="69d29-162">On the **Properties** pane, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="69d29-163">双击**钻取**事件。</span><span class="sxs-lookup"><span data-stu-id="69d29-163">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="69d29-164">随后将在代码中添加一个事件处理程序部分，类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="69d29-164">This will add an event handler section in the code that will look similar to the following.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="69d29-165">将事件处理程序填写完整。</span><span class="sxs-lookup"><span data-stu-id="69d29-165">Complete the event handler.</span></span> <span data-ttu-id="69d29-166">它应包括以下功能。</span><span class="sxs-lookup"><span data-stu-id="69d29-166">It should include the following functionality.</span></span>  
  
    1.  <span data-ttu-id="69d29-167">从 *DrillthroughEventArgs* 参数提取子报表对象引用。</span><span class="sxs-lookup"><span data-stu-id="69d29-167">Fetch the Child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="69d29-168">从所提取的子报表对象获取子报表参数列表。</span><span class="sxs-lookup"><span data-stu-id="69d29-168">Get the child report parameter list from the child report object fetched.</span></span>  
  
    3.  <span data-ttu-id="69d29-169">遍历参数集合并检索从父报表传递的参数 `ProductID` 的值。</span><span class="sxs-lookup"><span data-stu-id="69d29-169">Iterate through the parameter's collection and retrieve the value for the parameter, `ProductID`, passed from the parent report.</span></span>  
  
    4.  <span data-ttu-id="69d29-170">调用函数 `GetPurchaseOrderDetail` 并传递参数 `ProductID` 的值。</span><span class="sxs-lookup"><span data-stu-id="69d29-170">Call the function, `GetPurchaseOrderDetail`, and pass the value for parameter `ProductID`.</span></span>  
  
    5.  <span data-ttu-id="69d29-171">将 `PurchaseOrderDetail` DataTable 与报表的相应数据源绑定。</span><span class="sxs-lookup"><span data-stu-id="69d29-171">Bind the `PurchaseOrderDetail` DataTable with the Report's corresponding data source.</span></span>  
  
         <span data-ttu-id="69d29-172">填写完整的事件处理程序代码将类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="69d29-172">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="69d29-173">保存文件。</span><span class="sxs-lookup"><span data-stu-id="69d29-173">Save the file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="69d29-174">下一个任务</span><span class="sxs-lookup"><span data-stu-id="69d29-174">Next Task</span></span>  
 <span data-ttu-id="69d29-175">您已成功创建了一个数据筛选器，用于为子报表定义的数据表。</span><span class="sxs-lookup"><span data-stu-id="69d29-175">You have successfully created a data filter for the data table that you defined for the child report.</span></span> <span data-ttu-id="69d29-176">接下来，将生成并运行网站应用程序。</span><span class="sxs-lookup"><span data-stu-id="69d29-176">Next, you will build and run the website application.</span></span>  
  
  
