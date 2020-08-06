---
title: "\"数据集属性\" 对话框-> \"查询\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bffb14155d37e67333eb626747e1fcc54e618bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591139"
---
# <a name="dataset-properties-dialog-box-query"></a><span data-ttu-id="d69ad-102">“数据集属性”对话框 -&gt;“查询”</span><span class="sxs-lookup"><span data-stu-id="d69ad-102">Dataset Properties Dialog Box, Query</span></span>
  <span data-ttu-id="d69ad-103">在 "**数据集属性**" 对话框中选择 "**查询**" 可以选择数据源并创建查询。</span><span class="sxs-lookup"><span data-stu-id="d69ad-103">Select **Query** on the **Dataset Properties** dialog box to choose a data source and create a query.</span></span>  
  
 <span data-ttu-id="d69ad-104">与 **“数据集属性”** 对话框相关的主题还有：</span><span class="sxs-lookup"><span data-stu-id="d69ad-104">The **Dataset Properties** dialog box includes the following:</span></span>  
  
-   [<span data-ttu-id="d69ad-105">“数据集属性”对话框 -&gt;“参数”</span><span class="sxs-lookup"><span data-stu-id="d69ad-105">Dataset Properties Dialog Box, Parameters</span></span>](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [<span data-ttu-id="d69ad-106">“数据集属性”对话框 -&amp;gt;“字段”</span><span class="sxs-lookup"><span data-stu-id="d69ad-106">Dataset Properties Dialog Box, Fields</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [<span data-ttu-id="d69ad-107">“数据集属性”对话框 -&amp;gt;“选项”</span><span class="sxs-lookup"><span data-stu-id="d69ad-107">Dataset Properties Dialog Box, Options</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [<span data-ttu-id="d69ad-108">“数据集属性”对话框 -&amp;gt;“筛选器”</span><span class="sxs-lookup"><span data-stu-id="d69ad-108">Dataset Properties Dialog Box, Filters</span></span>](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a><span data-ttu-id="d69ad-109">选项</span><span class="sxs-lookup"><span data-stu-id="d69ad-109">Options</span></span>  
 <span data-ttu-id="d69ad-110">**名称**</span><span class="sxs-lookup"><span data-stu-id="d69ad-110">**Name**</span></span>  
 <span data-ttu-id="d69ad-111">为数据集键入名称。</span><span class="sxs-lookup"><span data-stu-id="d69ad-111">Type a name for the dataset.</span></span> <span data-ttu-id="d69ad-112">该名称不能与报表中的任何数据区域或组的名称相同。</span><span class="sxs-lookup"><span data-stu-id="d69ad-112">The name cannot be the same as a name for any data region or group in the report.</span></span>  
  
 <span data-ttu-id="d69ad-113">**数据源**</span><span class="sxs-lookup"><span data-stu-id="d69ad-113">**Data Source**</span></span>  
 <span data-ttu-id="d69ad-114">选择数据集要基于的数据源。</span><span class="sxs-lookup"><span data-stu-id="d69ad-114">Select the data source on which to base the dataset.</span></span> <span data-ttu-id="d69ad-115">若要创建新的数据源，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="d69ad-115">To create a new data source, click **New**.</span></span>  
  
 <span data-ttu-id="d69ad-116">**查询类型**</span><span class="sxs-lookup"><span data-stu-id="d69ad-116">**Query type**</span></span>  
 <span data-ttu-id="d69ad-117">选择要用于数据集的命令或查询的类型。</span><span class="sxs-lookup"><span data-stu-id="d69ad-117">Select the type of command or query to use for the dataset.</span></span> <span data-ttu-id="d69ad-118">选择 **Text** 可运行从数据库中检索数据的查询。</span><span class="sxs-lookup"><span data-stu-id="d69ad-118">Select **Text** to run a query to retrieve data from the database.</span></span> <span data-ttu-id="d69ad-119">选择 **Table** 可使用 **的** TableDirect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能选择表内的所有字段。</span><span class="sxs-lookup"><span data-stu-id="d69ad-119">Select **Table** to use the **TableDirect** feature of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to select all the fields within a table.</span></span> <span data-ttu-id="d69ad-120">选择 **Stored Procedure** 可按名称运行存储过程。</span><span class="sxs-lookup"><span data-stu-id="d69ad-120">Select **Stored Procedure** to run a stored procedure by name.</span></span> <span data-ttu-id="d69ad-121">默认情况下将选择**Text** ，该类型适用于大多数查询。</span><span class="sxs-lookup"><span data-stu-id="d69ad-121">**Text** is selected by default and is used for most queries.</span></span> <span data-ttu-id="d69ad-122">若要编辑选中的数据源查询，单击 **“查询设计器”**。</span><span class="sxs-lookup"><span data-stu-id="d69ad-122">To edit the selected data source query, click **Query Designer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d69ad-123">不是任何数据源都支持所有查询类型。</span><span class="sxs-lookup"><span data-stu-id="d69ad-123">Not all query types are supported by all data sources.</span></span> <span data-ttu-id="d69ad-124">例如，仅数据源类型 **OLE DB** 和 **ODBC** 支持 **Table**。</span><span class="sxs-lookup"><span data-stu-id="d69ad-124">For example, **Table** is supported only by data source types **OLE DB** and **ODBC**.</span></span>  
  
 <span data-ttu-id="d69ad-125">**查询**</span><span class="sxs-lookup"><span data-stu-id="d69ad-125">**Query**</span></span>  
 <span data-ttu-id="d69ad-126">选中 **Text** 命令类型选项后将显示此选项。</span><span class="sxs-lookup"><span data-stu-id="d69ad-126">This option appears when you choose the **Text** command type option.</span></span> <span data-ttu-id="d69ad-127">需键入一个查询或通过单击“导入”来导入一个预先存在的查询\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d69ad-127">Type a query or import a pre-existing query by clicking **Import**.</span></span> <span data-ttu-id="d69ad-128">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="d69ad-128">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d69ad-129">如果您已使用查询设计器生成了一个查询，则此对话框中将显示该查询的文本。</span><span class="sxs-lookup"><span data-stu-id="d69ad-129">If you used a query designer to build a query, the text of the query appears in this box.</span></span>  
  
 <span data-ttu-id="d69ad-130">**表名称**</span><span class="sxs-lookup"><span data-stu-id="d69ad-130">**Table name**</span></span>  
 <span data-ttu-id="d69ad-131">需输入要用作数据集的表的名称。</span><span class="sxs-lookup"><span data-stu-id="d69ad-131">Enter the name of the table that you want to use as a dataset.</span></span> <span data-ttu-id="d69ad-132">选中 **“表”** 后会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="d69ad-132">This option appears when you select **Table**.</span></span>  
  
 <span data-ttu-id="d69ad-133">**选择或输入存储过程名称**</span><span class="sxs-lookup"><span data-stu-id="d69ad-133">**Select or enter stored procedure name**</span></span>  
 <span data-ttu-id="d69ad-134">需键入或选择要使用的存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="d69ad-134">Type or choose the name of the stored procedure that you want to use.</span></span> <span data-ttu-id="d69ad-135">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="d69ad-135">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="d69ad-136">选中“存储过程”命令类型选项后会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="d69ad-136">This option appears when you choose the Stored Procedure command type option.</span></span>  
  
 <span data-ttu-id="d69ad-137">**超时（以秒为单位）**</span><span class="sxs-lookup"><span data-stu-id="d69ad-137">**Time out (in seconds)**</span></span>  
 <span data-ttu-id="d69ad-138">键入查询超时前等待的秒数。默认值为30秒。</span><span class="sxs-lookup"><span data-stu-id="d69ad-138">Type the number of seconds until the query times out. The default is 30 seconds.</span></span> <span data-ttu-id="d69ad-139">**“超时值”** 的值必须为空或大于零。</span><span class="sxs-lookup"><span data-stu-id="d69ad-139">The value for **Time out** must be empty or greater than zero.</span></span> <span data-ttu-id="d69ad-140">如果该值为空，则查询将不会超时。</span><span class="sxs-lookup"><span data-stu-id="d69ad-140">If it is empty, the query does not time out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69ad-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d69ad-141">See Also</span></span>  
 <span data-ttu-id="d69ad-142">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d69ad-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="d69ad-143">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d69ad-143">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="d69ad-144">[查询设计器 &#40;报表生成器&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="d69ad-144">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 [<span data-ttu-id="d69ad-145">Reporting Services 查询设计器</span><span class="sxs-lookup"><span data-stu-id="d69ad-145">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
