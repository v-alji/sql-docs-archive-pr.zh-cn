---
title: 从数据挖掘模型检索数据 (DMX) (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a59184524967a9bfe772e41890afc3b900cc9e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692284"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a><span data-ttu-id="40e0d-102">从数据挖掘模型检索数据 (DMX) (SSRS)</span><span class="sxs-lookup"><span data-stu-id="40e0d-102">Retrieve Data from a Data Mining Model (DMX) (SSRS)</span></span>
  <span data-ttu-id="40e0d-103">必须定义 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源以及一个或多个报表数据集，才能在报表中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据挖掘模型中的数据。</span><span class="sxs-lookup"><span data-stu-id="40e0d-103">To use data from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data mining model in your report, you must define a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source and one or more report datasets.</span></span> <span data-ttu-id="40e0d-104">创建数据源定义时，必须指定连接字符串和凭据，以便能够从客户端计算机访问该数据源。</span><span class="sxs-lookup"><span data-stu-id="40e0d-104">When you create the data source definition, you must specify a connection string and credentials so that you can access the data source from your client computer.</span></span>  
  
 <span data-ttu-id="40e0d-105">可以创建供单个报表使用的嵌入数据源定义，也可以创建可由多个报表使用的共享数据源定义。</span><span class="sxs-lookup"><span data-stu-id="40e0d-105">You can create an embedded data source definition for use by a single report or a shared data source definition that can be used by multiple reports.</span></span> <span data-ttu-id="40e0d-106">本主题中的过程介绍如何创建嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="40e0d-106">The procedures in this topic describe how to create an embedded data source.</span></span> <span data-ttu-id="40e0d-107">有关共享数据源的详细信息，请参阅[嵌入和共享的数据连接或数据源（报表生成器和 SSRS）](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)和[创建、修改和删除共享数据源 (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40e0d-107">For more information about shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) and [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="40e0d-108">创建 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源后，可以创建一个或多个数据集。</span><span class="sxs-lookup"><span data-stu-id="40e0d-108">After you create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, you can create one or more datasets.</span></span> <span data-ttu-id="40e0d-109">对于每个数据集，您都可以使用数据挖掘预测表达式 (DMX) 查询设计器来创建指定字段集合的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="40e0d-109">For each dataset, you use a Data Mining Prediction Expression (DMX) query designer to create a DMX query that specifies the field collection.</span></span> <span data-ttu-id="40e0d-110">有关详细信息，请参阅 [Analysis Services DMX 查询设计器用户界面](analysis-services-dmx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="40e0d-110">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="40e0d-111">创建数据集后，数据集的名称将在“报表数据”窗格中该数据集的数据源节点下显示为节点。</span><span class="sxs-lookup"><span data-stu-id="40e0d-111">After you create a dataset, the name of the dataset appears in the Report Data pane as a node under its data source.</span></span>  
  
 <span data-ttu-id="40e0d-112">报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。</span><span class="sxs-lookup"><span data-stu-id="40e0d-112">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a><span data-ttu-id="40e0d-113">创建 Microsoft SQL Server Analysis Services 嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="40e0d-113">To create an embedded Microsoft SQL Server Analysis Services data source</span></span>  
  
1.  <span data-ttu-id="40e0d-114">在“报表数据”窗格的工具栏上，单击 **“新建”** ，然后单击 **“数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-114">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="40e0d-115">在 **“数据源属性”** 对话框的 **“名称”** 文本框中键入名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="40e0d-115">In the **Data Source Properties** dialog box, type a name in the **Name** text box, or accept the default name.</span></span>  
  
3.  <span data-ttu-id="40e0d-116">确保已选中 **“嵌入连接”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-116">Verify that **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="40e0d-117">从“类型”下拉列表中，选择“Microsoft SQL Server Analysis Services”   。</span><span class="sxs-lookup"><span data-stu-id="40e0d-117">From the **Type** drop-down list, select **Microsoft SQL Server Analysis Services**.</span></span>  
  
5.  <span data-ttu-id="40e0d-118">指定使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="40e0d-118">Specify a connection string that works with your [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
     <span data-ttu-id="40e0d-119">请联系数据库管理员，获取连接信息以及用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="40e0d-119">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="40e0d-120">下面的连接字符串示例指定本地客户端上的 [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="40e0d-120">The following connection string example specifies the sample [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] database on the local client.</span></span>  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  <span data-ttu-id="40e0d-121">单击 **“凭据”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-121">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="40e0d-122">设置用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="40e0d-122">Set the credentials to use to connect to the data source.</span></span> <span data-ttu-id="40e0d-123">有关详细信息，请参阅[为报表数据源指定凭据和连接信息](../../integration-services/connection-manager/data-sources.md)</span><span class="sxs-lookup"><span data-stu-id="40e0d-123">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40e0d-124">若要测试数据源连接，请单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-124">To test the data source connection, click **Edit**.</span></span> <span data-ttu-id="40e0d-125">单击 **“连接属性”** 对话框中的 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-125">In the **Connection Properties** dialog box, click **Test Connection**.</span></span> <span data-ttu-id="40e0d-126">如果测试成功，您将会看到信息性消息“连接测试成功”。</span><span class="sxs-lookup"><span data-stu-id="40e0d-126">If the test is successful, you will see the information message "Test connection succeeded."</span></span> <span data-ttu-id="40e0d-127">如果测试失败，您将会看到一条警告消息，其中包含有关测试失败原因的详细信息。</span><span class="sxs-lookup"><span data-stu-id="40e0d-127">If the test fails, you will see a warning message with more information about why the test was not successful.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="40e0d-128">数据源将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="40e0d-128">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a><span data-ttu-id="40e0d-129">创建 Microsoft SQL Server Analysis Services 的数据集</span><span class="sxs-lookup"><span data-stu-id="40e0d-129">To create a dataset for a Microsoft SQL Server Analysis Services</span></span>  
  
1.  <span data-ttu-id="40e0d-130">在“报表数据”  窗格中，右键单击连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源的数据源的名称，再单击“添加数据集”  。</span><span class="sxs-lookup"><span data-stu-id="40e0d-130">In the **Report Data** pane, right-click the name of the data source that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="40e0d-131">在 **“数据集属性”** 对话框的 **“名称”** 文本框中键入名称。</span><span class="sxs-lookup"><span data-stu-id="40e0d-131">In the **Dataset Properties** dialog box, type a name in the **Name** text box.</span></span>  
  
3.  <span data-ttu-id="40e0d-132">在 **“数据源”** 框中，验证名称是否为连接到 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="40e0d-132">In the **Data source box**, verify that the name is the name of a data source that connects to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span>  
  
4.  <span data-ttu-id="40e0d-133">单击 **“查询设计器”** 打开图形查询设计器，从而以交互方式生成查询。</span><span class="sxs-lookup"><span data-stu-id="40e0d-133">Click **Query Designer** to open the graphical query designer to build a query interactively.</span></span> <span data-ttu-id="40e0d-134">如果查询设计器以 MDX 模式打开，请单击工具栏上的“命令类型 DMX”  （![更改为 DMX 查询语言视图](../media/rsqdicon-commandtypedmx.gif "更改为 DMX 查询语言视图")），以切换到数据挖掘查询设计器。</span><span class="sxs-lookup"><span data-stu-id="40e0d-134">If the query designer opens in MDX mode, click **Command Type DMX** (![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) on the toolbar to switch to the data mining query designer.</span></span> <span data-ttu-id="40e0d-135">有关详细信息，请参阅 [Analysis Services DMX 查询设计器用户界面](analysis-services-dmx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="40e0d-135">For more information, see [Analysis Services DMX Query Designer User Interface](analysis-services-dmx-query-designer-user-interface.md).</span></span>  
  
     <span data-ttu-id="40e0d-136">或者，若要从另一个报表导入现有的 DMX 查询，请单击 **“导入”** ，然后导航到包含 DMX 查询的 .rdl 文件。</span><span class="sxs-lookup"><span data-stu-id="40e0d-136">Alternatively, to import an existing DMX query from another report, click **Import**, and then navigate to the .rdl file with the DMX query.</span></span> <span data-ttu-id="40e0d-137">不支持从 .dmx 文件导入查询。</span><span class="sxs-lookup"><span data-stu-id="40e0d-137">Importing a query from an .dmx file is not supported.</span></span>  
  
5.  <span data-ttu-id="40e0d-138">通过创建并运行查询查看示例结果后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="40e0d-138">After you create and run your query to see sample results, click **OK**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="40e0d-139">数据集及其字段集合显示在“报表数据”窗格的数据源节点下。</span><span class="sxs-lookup"><span data-stu-id="40e0d-139">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e0d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40e0d-140">See Also</span></span>  
 <span data-ttu-id="40e0d-141">[针对 DMX 的 Analysis Services 连接类型 (SSRS)](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40e0d-141">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="40e0d-142">[Reporting Services 中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="40e0d-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="40e0d-143">[数据集字段集合（报表生成器和 SSRS）](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40e0d-143">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="40e0d-144">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="40e0d-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
