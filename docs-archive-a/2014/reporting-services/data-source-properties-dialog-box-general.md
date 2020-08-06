---
title: "\"数据源属性\" 对话框-\"常规\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c79ad70cdd4dcb10e1abce1102fa39eef4c67461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577395"
---
# <a name="data-source-properties-dialog-box-general"></a><span data-ttu-id="e315d-102">“数据源属性”对话框 ->“常规”</span><span class="sxs-lookup"><span data-stu-id="e315d-102">Data Source Properties Dialog Box, General</span></span>
  <span data-ttu-id="e315d-103">在 **“数据源属性”** 对话框中选择 **“常规”** 可以显示和修改报表中数据源的连接信息。</span><span class="sxs-lookup"><span data-stu-id="e315d-103">Select **General** on the **Data Source Properties** dialog box to display and modify connection information for a data source in the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e315d-104">选项</span><span class="sxs-lookup"><span data-stu-id="e315d-104">Options</span></span>  
 <span data-ttu-id="e315d-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="e315d-105">**Name**</span></span>  
 <span data-ttu-id="e315d-106">键入数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="e315d-106">Type the name of the data source.</span></span> <span data-ttu-id="e315d-107">数据源名称在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e315d-107">The data source name must be unique within the report.</span></span> <span data-ttu-id="e315d-108">默认情况下，会为数据源分配一个常规名称，如 DataSource1 或 DataSource2。</span><span class="sxs-lookup"><span data-stu-id="e315d-108">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="e315d-109">**嵌入连接**</span><span class="sxs-lookup"><span data-stu-id="e315d-109">**Embedded connection**</span></span>  
 <span data-ttu-id="e315d-110">如果不想使用共享数据源，则请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="e315d-110">Select this option when you do not want to use a shared data source.</span></span>  
  
 <span data-ttu-id="e315d-111">**Type**</span><span class="sxs-lookup"><span data-stu-id="e315d-111">**Type**</span></span>  
 <span data-ttu-id="e315d-112">选择数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e315d-112">Select a data processing extension.</span></span> <span data-ttu-id="e315d-113">该列表显示所有已注册的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e315d-113">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="e315d-114">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="e315d-114">**Connection string**</span></span>  
 <span data-ttu-id="e315d-115">输入数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e315d-115">Enter a connection string for the data source.</span></span> <span data-ttu-id="e315d-116">单击 **“编辑”** 可以使用 **“连接属性”** 对话框生成连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e315d-116">Click **Edit** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="e315d-117">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="e315d-117">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="e315d-118">**使用共享数据源引用**</span><span class="sxs-lookup"><span data-stu-id="e315d-118">**Use shared data source reference**</span></span>  
 <span data-ttu-id="e315d-119">选择此选项可以链接到共享数据源。</span><span class="sxs-lookup"><span data-stu-id="e315d-119">Select this option to link to a shared data source.</span></span> <span data-ttu-id="e315d-120">请从下拉列表中选择共享数据源。</span><span class="sxs-lookup"><span data-stu-id="e315d-120">Select a shared data source from the drop-down list.</span></span> <span data-ttu-id="e315d-121">若要编辑所选的数据源，请单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="e315d-121">To edit the selected data source, click **Edit**.</span></span> <span data-ttu-id="e315d-122">如果选择了 **“使用共享数据源引用”** ，则会禁用 **“类型”** 和 **“连接字符串”** 。</span><span class="sxs-lookup"><span data-stu-id="e315d-122">If **Use shared data source reference** is selected, **Type** and **Connection string** are disabled.</span></span>  
  
 <span data-ttu-id="e315d-123">**处理查询时使用单个事务**</span><span class="sxs-lookup"><span data-stu-id="e315d-123">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="e315d-124">选择此选项可指示使用此数据源的数据集在针对数据库的单个事务中运行。</span><span class="sxs-lookup"><span data-stu-id="e315d-124">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="e315d-125">若要将使用同一数据源的子报表的事务包含在内，请在 **“属性”** 窗格中相应子报表的 **“其他”** 属性部分中将 **MergeTransactions** 设置为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="e315d-125">To include transactions for subreports that use the same data source, set **MergeTransactions** to **True** in the subreport's **Other** properties section of the **Properties** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e315d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e315d-126">See Also</span></span>  
 <span data-ttu-id="e315d-127">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e315d-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="e315d-128">[&#40;SSRS 创建嵌入数据源或共享数据源&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e315d-128">[Create an Embedded or Shared Data Source &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="e315d-129">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="e315d-129">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="e315d-130">“数据源属性”对话框 -&gt;“凭据”</span><span class="sxs-lookup"><span data-stu-id="e315d-130">Data Source Properties Dialog Box, Credentials</span></span>](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
