---
title: 第 4 课：定义用于子报表的数据连接和数据表 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d9144d960ad933afa65f9d4483e96b5f732d944
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578706"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a><span data-ttu-id="2358f-102">第 4 课：定义用于子报表的数据连接和数据表</span><span class="sxs-lookup"><span data-stu-id="2358f-102">Lesson 4: Define a Data Connection and Data Table for Child Report</span></span>
  <span data-ttu-id="2358f-103">设计父报表后，接下来要创建用于子报表的数据连接和数据表。</span><span class="sxs-lookup"><span data-stu-id="2358f-103">After you design the parent report, you next step is to create a data connection and a data table for the child report.</span></span> <span data-ttu-id="2358f-104">在本教程中，数据连接指向 AdventureWorks2008 数据库。</span><span class="sxs-lookup"><span data-stu-id="2358f-104">In this tutorial the data connection is to the AdventureWorks2008 database.</span></span> <span data-ttu-id="2358f-105">也可选择连接到 AdventureWorks2012 数据库。</span><span class="sxs-lookup"><span data-stu-id="2358f-105">You also have the option of connecting to the AdventureWorks2012 database.</span></span>  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a><span data-ttu-id="2358f-106">通过添加 DataSet 定义数据连接和 DataTable（用于子报表）</span><span class="sxs-lookup"><span data-stu-id="2358f-106">To define a data connection and DataTable by adding a DataSet (for child report)</span></span>  
  
1.  <span data-ttu-id="2358f-107">在 "**网站**" 菜单上，单击 "**添加新项**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-107">On the **Website** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="2358f-108">在 "**添加新项**" 对话框中，单击 "**数据集**"，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-108">In the **Add New Item** dialog box, click **DataSet** and then click **Add**.</span></span> <span data-ttu-id="2358f-109">出现提示时，应通过单击 **"是"** 将该项添加到**App_Code**文件夹。</span><span class="sxs-lookup"><span data-stu-id="2358f-109">When prompted, you should add the item to the **App_Code** folder by clicking **Yes**.</span></span>  
  
     <span data-ttu-id="2358f-110">此操作将一个新的 XSD 文件 **DataSet2.xsd** 添加到项目，并打开数据集设计器。</span><span class="sxs-lookup"><span data-stu-id="2358f-110">This adds a new XSD file **DataSet2.xsd** to the project and opens the DataSet Designer.</span></span>  
  
3.  <span data-ttu-id="2358f-111">从“工具箱”窗口中，将一个 **TableAdapter** 控件拖到设计图面上。</span><span class="sxs-lookup"><span data-stu-id="2358f-111">From the Toolbox window, drag a **TableAdapter** control to the design surface.</span></span> <span data-ttu-id="2358f-112">随后将启动 **TableAdapter** 配置向导。</span><span class="sxs-lookup"><span data-stu-id="2358f-112">This launches the **TableAdapter** Configuration Wizard.</span></span>  
  
4.  <span data-ttu-id="2358f-113">在 "**选择你的数据连接**" 页上，单击 "**新建连接**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-113">On the **Choose Your Data Connection** page, click **New Connection**.</span></span>  
  
5.  <span data-ttu-id="2358f-114">在“添加连接”对话框中，执行以下步骤\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="2358f-114">In the **Add Connection** dialog box, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="2358f-115">在 "**服务器名称**" 框中，输入**AdventureWorks2008**数据库所在的服务器。</span><span class="sxs-lookup"><span data-stu-id="2358f-115">In the **Server name** box, enter the server where the **AdventureWorks2008** database is located.</span></span>  
  
         <span data-ttu-id="2358f-116">默认的 SQL Server Express 实例为 **(local)\sqlexpress**。</span><span class="sxs-lookup"><span data-stu-id="2358f-116">The default SQL Server Express instance is **(local)\sqlexpress**.</span></span>  
  
    2.  <span data-ttu-id="2358f-117">在“登录到服务器”部分中，选择使你可访问数据的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2358f-117">In the **Log on to the server** section, select the option that provides you access to the data.</span></span> <span data-ttu-id="2358f-118">“使用 Windows 身份验证”为默认选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2358f-118">**Use Windows Authentication** is the default.</span></span>  
  
    3.  <span data-ttu-id="2358f-119">在 "**选择或输入数据库名称**" 下拉列表中，单击 " **AdventureWorks2008**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-119">From the **Select or enter a database name** drop-down list, click **AdventureWorks2008**.</span></span>  
  
    4.  <span data-ttu-id="2358f-120">单击 **“确定”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2358f-120">Click **OK**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="2358f-121">如果在步骤 5 (b) 中选择了“使用 SQL Server 身份验证”，则选择一个选项，决定是在字符串中加入敏感数据还是在应用程序代码中设置该信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2358f-121">If you selected **Use SQL Server Authentication** in Step 5 (b), select the option whether to include the sensitive data in the string or set the information in your application code.</span></span>  
  
7.  <span data-ttu-id="2358f-122">在 "将**连接字符串保存到应用程序配置文件**中" 页上，键入连接字符串的名称，或接受默认的**AdventureWorks2008ConnectionString**。</span><span class="sxs-lookup"><span data-stu-id="2358f-122">On the **Save the Connection String to the Application Configuration File** page, type in the name for the connection string or accept the default **AdventureWorks2008ConnectionString**.</span></span> <span data-ttu-id="2358f-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2358f-123">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="2358f-124">在 "**选择命令类型**" 页上，选择 "**使用 SQL 语句**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-124">On the **Choose a Command Type** page, select **Use SQL Statements**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="2358f-125">在 "**输入 SQL 语句**" 页上，输入以下 transact-sql 查询以从**AdventureWorks2008**数据库检索数据，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-125">On the **Enter a SQL Statement** page, enter the following Transact-SQL query to retrieve data from the **AdventureWorks2008** database, and then click **Next**.</span></span>  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     <span data-ttu-id="2358f-126">还可以通过单击 "**查询生成器**" 创建查询，然后通过单击 "**执行查询**" 按钮验证查询。</span><span class="sxs-lookup"><span data-stu-id="2358f-126">You can also create the query by clicking **Query Builder**, and then verify the query by clicking **Execute Query** button.</span></span> <span data-ttu-id="2358f-127">如果查询返回的数据不符合预期，则可能使用的 AdventureWorks 版本较低。</span><span class="sxs-lookup"><span data-stu-id="2358f-127">If the query does not return the expected data, you might be using an earlier version of AdventureWorks.</span></span> <span data-ttu-id="2358f-128">有关安装 AdventureWorks 的**AdventureWorks2008**版本的详细信息，请参阅[演练：安装 adventureworks 数据库](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="2358f-128">For more information about installing the **AdventureWorks2008** version of AdventureWorks, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).</span></span>  
  
10. <span data-ttu-id="2358f-129">在 "**选择要生成的方法**" 页上，取消选中 **"创建方法以将更新直接发送到数据库 (GenerateDBDirectMethods") **，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-129">On the **Choose Methods to Generate** page, uncheck **Create methods to send updates directly to the database (GenerateDBDirectMethods)**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="2358f-130">现在已完成将 ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx)配置为报表的数据源。</span><span class="sxs-lookup"><span data-stu-id="2358f-130">You have now completed configuring the ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) as data source for your report.</span></span> <span data-ttu-id="2358f-131">在 Visual Studio 中的“数据集设计器”页上，应看到所添加的 **DataTable** ，其中列出在查询中指定的列。</span><span class="sxs-lookup"><span data-stu-id="2358f-131">On the DataSet Designer page in Visual Studio, you should see the **DataTable** you added, listing the columns specified in the query.</span></span> <span data-ttu-id="2358f-132">DataSet2 由根据查询从 PurhcaseOrderDetail 表获得的数据组成。</span><span class="sxs-lookup"><span data-stu-id="2358f-132">DataSet2 contains the data from the PurhcaseOrderDetail table, based on the query.</span></span>  
  
11. <span data-ttu-id="2358f-133">保存文件。</span><span class="sxs-lookup"><span data-stu-id="2358f-133">Save the file.</span></span>  
  
12. <span data-ttu-id="2358f-134">若要预览数据，请在 "**数据**" 菜单上单击 "**预览数据**"，然后单击 "**预览**"。</span><span class="sxs-lookup"><span data-stu-id="2358f-134">To preview the data, click **Preview Data** on the **Data** menu, and then click **Preview**.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="2358f-135">下一个任务</span><span class="sxs-lookup"><span data-stu-id="2358f-135">Next Task</span></span>  
 <span data-ttu-id="2358f-136">您已成功创建了用于子报表的数据连接和数据表。</span><span class="sxs-lookup"><span data-stu-id="2358f-136">You have successfully created a data connection and data table for the child report.</span></span> <span data-ttu-id="2358f-137">接下来，将使用报表向导设计子报表。</span><span class="sxs-lookup"><span data-stu-id="2358f-137">Next, you will design the child report using the Report Wizard.</span></span>  
  
  
