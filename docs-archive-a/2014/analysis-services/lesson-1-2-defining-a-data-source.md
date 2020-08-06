---
title: 定义数据源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdf00b47360341e2b9a99654482d65be83b86503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577050"
---
# <a name="defining-a-data-source"></a><span data-ttu-id="b5e9d-102">定义数据源</span><span class="sxs-lookup"><span data-stu-id="b5e9d-102">Defining a Data Source</span></span>
  <span data-ttu-id="b5e9d-103">在创建 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目后，通常通过定义项目使用的一个或多个数据源来开始使用项目。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-103">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you generally start working with the project by defining one or more data sources that the project will use.</span></span> <span data-ttu-id="b5e9d-104">定义数据源时，将定义要用于连接此数据源的连接字符串信息。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-104">When you define a data source, you are defining the connection string information that will be used to connect to the data source.</span></span> <span data-ttu-id="b5e9d-105">有关详细信息，请参阅 [创建数据源（SSAS 多维）](multidimensional-models/create-a-data-source-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-105">For more information, see [Create a Data Source &#40;SSAS Multidimensional&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md).</span></span>  
  
 <span data-ttu-id="b5e9d-106">在以下任务中，您将把 AdventureWorksDWSQLServer2012 示例数据库定义为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目的数据源。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-106">In the following task, you define the AdventureWorksDWSQLServer2012 sample database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="b5e9d-107">为了实现本教程教学目的，此数据库位于您的本地计算机上，而源数据库通常驻留在一台或多台远程计算机中。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-107">While this database is located on your local computer for the purposes of this tutorial, source databases are frequently hosted on one or more remote computers.</span></span>  
  
### <a name="to-define-a-new-data-source"></a><span data-ttu-id="b5e9d-108">定义新的数据源</span><span class="sxs-lookup"><span data-stu-id="b5e9d-108">To define a new data source</span></span>  
  
1.  <span data-ttu-id="b5e9d-109">在解决方案资源管理器中（在 Microsoft Visual Studio 窗口的右侧），右键单击“数据源”\*\*\*\*，然后单击“新建数据源”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Sources**, and then click **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="b5e9d-110">在 "**数据源向导**" 的 "**欢迎使用数据源向导**" 页上，单击 "**下一步**" 打开 "**选择如何定义连接"** 页。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-110">On the **Welcome to the Data Source Wizard** page of the **Data Source Wizard**, click **Next** to open the **Select how to define the connection** page.</span></span>  
  
3.  <span data-ttu-id="b5e9d-111">在“选择如何定义连接”\*\*\*\* 页上，可以基于新连接、现有连接或以前定义的数据源对象来定义数据源。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-111">On the **Select how to define the connection** page, you can define a data source based on a new connection, based on an existing connection, or based on a previously defined data source object.</span></span> <span data-ttu-id="b5e9d-112">在本教程中，基于新连接定义数据源。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-112">In this tutorial, you define a data source based on a new connection.</span></span> <span data-ttu-id="b5e9d-113">确保已选中“基于现有连接或新连接创建数据源”\*\*\*\*，再单击“新建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-113">Verify that **Create a data source based on an existing or new connection** is selected, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="b5e9d-114">在“连接管理器”\*\*\*\* 对话框中，为数据源定义连接属性。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-114">In the **Connection Manager** dialog box, you define connection properties for the data source.</span></span> <span data-ttu-id="b5e9d-115">在“提供程序”\*\*\*\* 列表框中，确保已选中“本机 OLE DB\SQL Server Native Client 11.0”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-115">In the **Provider** list box, verify that **Native OLE DB\SQL Server Native Client 11.0** is selected.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="b5e9d-116">还支持其他提供程序，这些提供程序显示在**提供程序**列表中。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-116">also supports other providers, which are displayed in the **Provider** list.</span></span>  
  
5.  <span data-ttu-id="b5e9d-117">在 "**服务器名称**" 文本框中，键入 `localhost` 。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-117">In the **Server name** text box, type `localhost`.</span></span>  
  
     <span data-ttu-id="b5e9d-118">若要连接到本地计算机上的命名实例，请键入**localhost \\<实例 \> 名称**。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-118">To connect to a named instance on your local computer, type **localhost\\<instance name\>**.</span></span> <span data-ttu-id="b5e9d-119">若要连接到特定的计算机而不是本地计算机，请键入该计算机名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-119">To connect to the specific computer instead of the local computer, type the computer name or IP address.</span></span>  
  
6.  <span data-ttu-id="b5e9d-120">确保已选中“使用 Windows 身份验证”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-120">Verify that **Use Windows Authentication** is selected.</span></span> <span data-ttu-id="b5e9d-121">在“选择或输入数据库名称”\*\*\*\* 列表中，选择 **AdventureWorksDW2012**。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-121">In the **Select or enter a database name** list, select **AdventureWorksDW2012**.</span></span>  
  
7.  <span data-ttu-id="b5e9d-122">单击“测试连接”\*\*\*\* 以测试与数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-122">Click **Test Connection** to test the connection to the database.</span></span>  
  
8.  <span data-ttu-id="b5e9d-123">单击 **“确定”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-123">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="b5e9d-124">在该向导的“模拟信息”\*\*\*\* 页上，可以定义 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用于连接数据源的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-124">On the **Impersonation Information** page of the wizard, you define the security credentials for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use to connect to the data source.</span></span> <span data-ttu-id="b5e9d-125">在选中“Windows 身份验证”时，模拟会影响用于连接数据源的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-125">Impersonation affects the Windows account used to connect to the data source when Windows Authentication is selected.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="b5e9d-126">不支持模拟来处理 OLAP 对象。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-126">does not support impersonation for processing OLAP objects.</span></span> <span data-ttu-id="b5e9d-127">选择“使用服务帐户”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-127">Select **Use the service account**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="b5e9d-128">在“完成向导”\*\*\*\* 页上，接受默认名称 **Adventure Works DW 2012**，然后单击“完成”\*\*\*\* 以创建新数据源。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-128">On the **Completing the Wizard** page, accept the default name, **Adventure Works DW 2012**, and then click **Finish** to create the new data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5e9d-129">若要在创建数据源之后修改其属性，请在“数据源”\*\*\*\* 文件夹中双击该数据源，以在“数据源设计器”\*\*\*\* 中显示数据源属性。</span><span class="sxs-lookup"><span data-stu-id="b5e9d-129">To modify the properties of the data source after it has been created, double-click the data source in the **Data Sources** folder to display the data source properties in **Data Source Designer**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b5e9d-130">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="b5e9d-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b5e9d-131">定义数据源视图</span><span class="sxs-lookup"><span data-stu-id="b5e9d-131">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5e9d-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5e9d-132">See Also</span></span>  
 [<span data-ttu-id="b5e9d-133">创建数据源（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="b5e9d-133">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
  
