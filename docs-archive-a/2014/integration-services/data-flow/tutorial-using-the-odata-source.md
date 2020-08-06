---
title: 教程：使用 OData 源 [SSIS] |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2c64cf8b-5edb-48df-8ffe-697096258f71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a13b04494ed00251774b490b1cc929769a869acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589775"
---
# <a name="tutorial-using-the-odata-source-ssis"></a><span data-ttu-id="c451b-102">教程：使用 OData 源 [SSIS]</span><span class="sxs-lookup"><span data-stu-id="c451b-102">Tutorial: Using the OData Source [SSIS]</span></span>
  <span data-ttu-id="c451b-103">本教程介绍了从示例 Northwind OData 服务 (http://services.odata.org/V3/Northwind/Northwind.svc/) ) 提取 Employees 集合，然后将它加载到某一平面文件中的过程   。</span><span class="sxs-lookup"><span data-stu-id="c451b-103">This tutorial walks you through the process to extract the **Employees** collection from the sample **Northwind** OData service (http://services.odata.org/V3/Northwind/Northwind.svc/), and then load it into a flat file.</span></span>  
  
## <a name="1-create-an-integration-services-project"></a><span data-ttu-id="c451b-104">1.创建 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="c451b-104">1. Create an Integration Services Project</span></span>  
  
1.  <span data-ttu-id="c451b-105">启动 **SQL Server Data Tools** 或 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c451b-105">Launch **SQL Server Data Tools** or [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="c451b-106">单击“文件”，指向“新建”并单击“项目”。   </span><span class="sxs-lookup"><span data-stu-id="c451b-106">Click **File**, point to **New**, and click **Project**.</span></span>  
  
3.  <span data-ttu-id="c451b-107">在“新建项目”  对话框中，依次展开“已安装”  、“模板”  “商业智能”  ，然后单击“Integration Services”  。</span><span class="sxs-lookup"><span data-stu-id="c451b-107">In the **New Project** dialog box, expand **Installed**, expand **Templates**, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
4.  <span data-ttu-id="c451b-108">对于项目类型，选择 **“Integration Services 项目”** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-108">Select **Integration Services Project** for the type of project.</span></span>  
  
5.  <span data-ttu-id="c451b-109">为项目输入 **“名称”** 并且选择 **“位置”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-109">Enter a **name** and select a **location** for the project, and click **OK**.</span></span>  
  
## <a name="2-add-and-configure-odata-source-to-the-ssis-package"></a><span data-ttu-id="c451b-110">2.配置 OData 源并将其添加到 SSIS 包</span><span class="sxs-lookup"><span data-stu-id="c451b-110">2. Add and Configure OData Source to the SSIS Package</span></span>  
  
1.  <span data-ttu-id="c451b-111">将“数据流任务”  从“SSIS 工具箱”  拖放到 SSIS 包的控制流设计图面上。</span><span class="sxs-lookup"><span data-stu-id="c451b-111">Drag-drop a **Data Flow Task** from the **SSIS Toolbox** on to the control flow design surface of your SSIS package.</span></span>  
  
2.  <span data-ttu-id="c451b-112">单击 **“数据流”** 选项卡或者双击新添加的 **“数据流任务”** ，以便启动 **“数据流”** 设计图面。</span><span class="sxs-lookup"><span data-stu-id="c451b-112">Click the **Data Flow** tab, or double click on the newly added **Data Flow Task** to launch the **Data Flow design surface**.</span></span>  
  
3.  <span data-ttu-id="c451b-113">从“SSIS 工具箱”  的“公共”  组中拖放“OData 源”  。</span><span class="sxs-lookup"><span data-stu-id="c451b-113">Drag-drop **OData Source** from the **Common** group in the **SSIS Toolbox**.</span></span> <span data-ttu-id="c451b-114">首次安装 **“OData 源”** 时，它将出现在 **“SSIS 工具箱”** 中的 **“公共”** 组下。</span><span class="sxs-lookup"><span data-stu-id="c451b-114">When the **OData Source** is first installed, it will appear under the **Common** group in the **SSIS Toolbox**.</span></span>  
  
4.  <span data-ttu-id="c451b-115">双击 **“OData 源”** 组件可启动 **“OData 源编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-115">Double click the **OData Source** component to launch the **OData Source Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="c451b-116">单击“新建…”可添加新的 OData 连接管理器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c451b-116">Click **New...** to add a new OData Connection Manager.</span></span>  
  
6.  <span data-ttu-id="c451b-117">为 **“服务文档位置”** 输入 OData 服务 URL。</span><span class="sxs-lookup"><span data-stu-id="c451b-117">Enter the OData service URL for **Service document location**.</span></span> <span data-ttu-id="c451b-118">它可以是指向服务文档的 URL，也可以是指向特定馈送或实体的 URL。</span><span class="sxs-lookup"><span data-stu-id="c451b-118">This can be the URL to the service document, or to a specific feed or entity.</span></span> <span data-ttu-id="c451b-119">对于本教程，请键入 [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/) 。</span><span class="sxs-lookup"><span data-stu-id="c451b-119">For the purpose of this tutorial, type [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/).</span></span>  
  
7.  <span data-ttu-id="c451b-120">确认为 **“身份验证”** 选择了 **“Windows 身份验证”** ，以便用于访问 OData 服务。</span><span class="sxs-lookup"><span data-stu-id="c451b-120">Confirm that **Windows Authentication** is selected for the **authentication** to use to access the OData Service.</span></span> <span data-ttu-id="c451b-121">默认情况下将选择 **“Windows 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-121">**Windows Authentication** is selected by default.</span></span> <span data-ttu-id="c451b-122">若要使用基本身份验证，请选择 **“使用此用户名和密码”**。</span><span class="sxs-lookup"><span data-stu-id="c451b-122">To use basic authentication, select **Use this user name and password**.</span></span>  
  
8.  <span data-ttu-id="c451b-123">对于连接单击 **“测试连接”** ，然后单击 **“确定”** 以便创建 OData 连接管理器的实例。</span><span class="sxs-lookup"><span data-stu-id="c451b-123">Click **Test Connection** to the connection, and click **OK** to create an instance of OData Connection Manager.</span></span>  
  
9. <span data-ttu-id="c451b-124">在 **“OData 源编辑器”** 对话框中，确认为 **“对资源路径使用集合”** 选项选择了 **“集合”** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-124">In the **OData Source Editor** Dialog Box, confirm that **Collection** is selected for **Use collection on resource path** option.</span></span>  
  
10. <span data-ttu-id="c451b-125">从 **“集合”** 下拉列表中，选择 **Employees**。</span><span class="sxs-lookup"><span data-stu-id="c451b-125">From the **Collection** drop down list, select **Employees**.</span></span>  
  
11. <span data-ttu-id="c451b-126">为 **“查询选项”** 输入任何其他 OData 查询选项或筛选器。</span><span class="sxs-lookup"><span data-stu-id="c451b-126">Enter any additional OData query options or filters for **Query Options**.</span></span> <span data-ttu-id="c451b-127">例如：</span><span class="sxs-lookup"><span data-stu-id="c451b-127">Ex.</span></span> <span data-ttu-id="c451b-128">$orderby=CompanyName&$top=100。</span><span class="sxs-lookup"><span data-stu-id="c451b-128">$orderby=CompanyName&$top=100.</span></span> <span data-ttu-id="c451b-129">为了实现本教程教学目的，请输入 **$top=5**。</span><span class="sxs-lookup"><span data-stu-id="c451b-129">For the purpose of this tutorial, enter **$top=5**.</span></span>  
  
12. <span data-ttu-id="c451b-130">单击 **“预览”** 可预览数据。</span><span class="sxs-lookup"><span data-stu-id="c451b-130">Click **Preview** to preview the data.</span></span>  
  
13. <span data-ttu-id="c451b-131">在左导航窗格中单击 **“列”** 可切换到 **“列”** 页。</span><span class="sxs-lookup"><span data-stu-id="c451b-131">Click **Columns** in the left navigation pane to switch to the **Columns** page.</span></span>  
  
14. <span data-ttu-id="c451b-132">通过选中相应复选框，从 **“可用外部列”** 中选择 **EmployeeID**、 **FirstName** 和 **LastName** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-132">Select **EmployeeID**, **FirstName**, and **LastName** from **Available External Columns** by checking the check boxes.</span></span>  
  
15. <span data-ttu-id="c451b-133">单击 **“确定”** 关闭 **“OData 源编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-133">Click **OK** to close the **OData Source Editor** dialog box.</span></span>  
  
## <a name="3-add-flat-file-destination-and-test-the-solution"></a><span data-ttu-id="c451b-134">3.添加平面文件目标并且测试解决方案</span><span class="sxs-lookup"><span data-stu-id="c451b-134">3. Add Flat File Destination and Test the Solution</span></span>  
  
1.  <span data-ttu-id="c451b-135">现在，将“平面文件目标”\*\*\*\* 从“SSIS 工具箱”\*\*\*\* 拖放到“OData 源”\*\*\*\* 组件下的数据流设计图面上。</span><span class="sxs-lookup"><span data-stu-id="c451b-135">Now, drag-drop a **Flat File Destination** from **SSIS Toolbox** to the Data Flow design surface below the **OData Source** component.</span></span>  
  
2.  <span data-ttu-id="c451b-136">使用蓝色箭头将 **“OData 源”** 组件与 **“平面文件目标”** 组件连接起来。</span><span class="sxs-lookup"><span data-stu-id="c451b-136">Connect **OData Source** component with the **Flat File Destination** component using blue arrow.</span></span>  
  
3.  <span data-ttu-id="c451b-137">双击“平面文件目标”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c451b-137">Double-click on **Flat File Destination**.</span></span> <span data-ttu-id="c451b-138">您应该会看到 **“平面文件目标编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-138">You should see the **Flat File Destination Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="c451b-139">在 **“平面文件目标编辑器”** 对话框中，单击 **“新建”** 创建新的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c451b-139">In the **Flat File Destination Editor** dialog box, click **New** to create a new flat file connection manager.</span></span>  
  
5.  <span data-ttu-id="c451b-140">在 **“平面文件格式”** 对话框中，选择 **“带分隔符”**。</span><span class="sxs-lookup"><span data-stu-id="c451b-140">In the **Flat File Format** dialog box, select **Delimited**.</span></span> <span data-ttu-id="c451b-141">您应该会看到 **“平面文件连接管理器编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-141">You should see the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
6.  <span data-ttu-id="c451b-142">在“平面文件连接管理器编辑器”\*\*\*\* 对话框中，为“文件名”\*\*\*\* 输入 **c:\Employees.txt**。</span><span class="sxs-lookup"><span data-stu-id="c451b-142">In the **Flat File Connection Manager Editor** dialog box, for the **File name**, enter **c:\Employees.txt**.</span></span>  
  
7.  <span data-ttu-id="c451b-143">在左侧导航窗格中，单击 **“列”**。</span><span class="sxs-lookup"><span data-stu-id="c451b-143">In the left navigation pane, click **Columns**.</span></span> <span data-ttu-id="c451b-144">您可以预览此页上的数据。</span><span class="sxs-lookup"><span data-stu-id="c451b-144">You can preview the data on this page.</span></span>  
  
8.  <span data-ttu-id="c451b-145">单击“确定”关闭 **“平面文件连接管理器编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-145">Click OK to close the **Flat File Connection Manager** Editor dialog box.</span></span>  
  
9. <span data-ttu-id="c451b-146">在 **“平面文件目标编辑器”** 对话框中，在左侧导航窗格中单击 **“映射”** 。</span><span class="sxs-lookup"><span data-stu-id="c451b-146">In the **Flat File Destination Editor** dialog box, click **Mappings** in the left navigation pane.</span></span> <span data-ttu-id="c451b-147">查看映射。</span><span class="sxs-lookup"><span data-stu-id="c451b-147">Review the mappings.</span></span>  
  
10. <span data-ttu-id="c451b-148">单击“确定” **关闭“平面文件目标编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c451b-148">Click OK to close the **Flat File Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="c451b-149">编译并执行该 SSIS 包。</span><span class="sxs-lookup"><span data-stu-id="c451b-149">Compile and execute the SSIS package.</span></span> <span data-ttu-id="c451b-150">验证为来自 OData 馈送的 5 名员工使用 ID、名字和姓氏创建了输出文件。</span><span class="sxs-lookup"><span data-stu-id="c451b-150">Verify that the output file is created with ID, First Name, and Last Name for 5 employees from the OData feed.</span></span>  
  
  
