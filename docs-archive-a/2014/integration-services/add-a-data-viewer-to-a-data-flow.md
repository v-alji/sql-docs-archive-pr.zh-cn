---
title: 向数据流添加数据查看器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data viewers [Integration Services]
- data flow [Integration Services], data viewers
- adding data viewers
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7abd76417552ec50da736afe024a5ae36ee6a2ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577786"
---
# <a name="add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="01963-102">将数据查看器添加到数据流</span><span class="sxs-lookup"><span data-stu-id="01963-102">Add a Data Viewer to a Data Flow</span></span>
  <span data-ttu-id="01963-103">本主题介绍如何在数据流中添加和配置数据查看器。</span><span class="sxs-lookup"><span data-stu-id="01963-103">This topic describes how to add and configure a data viewer in a data flow.</span></span> <span data-ttu-id="01963-104">数据查看器可以显示在两个数据流组件之间移动的数据。</span><span class="sxs-lookup"><span data-stu-id="01963-104">A data viewer displays data that is moving between two data flow components.</span></span> <span data-ttu-id="01963-105">例如，数据查看器可以显示在数据流中的转换修改数据之前从数据源中提取的数据。</span><span class="sxs-lookup"><span data-stu-id="01963-105">For example, a data viewer can display the data that is extracted from a data source before a transformation in the data flow modifies the data.</span></span>  
  
 <span data-ttu-id="01963-106">路径将一个数据流组件的输出连接到另一个组件的输入，以此连接数据流中的组件。</span><span class="sxs-lookup"><span data-stu-id="01963-106">A path connects components in a data flow by connecting the output of one data flow component to the input of another component.</span></span>  
  
 <span data-ttu-id="01963-107">在可以将数据查看器添加到包之前，包必须包括一个数据流任务和至少两个已连接在一起的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="01963-107">Before you can add data viewers to a package, the package must include a Data Flow task and at least two data flow components that are connected.</span></span>  
  
### <a name="to-add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="01963-108">将数据查看器添加到数据流</span><span class="sxs-lookup"><span data-stu-id="01963-108">To add a data viewer to a data flow</span></span>  
  
1.  <span data-ttu-id="01963-109">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="01963-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="01963-110">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="01963-110">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="01963-111">如果 **“控制流”** 选项卡尚未处于活动状态，请单击该选项卡。</span><span class="sxs-lookup"><span data-stu-id="01963-111">Click the **Control Flow** tab, if it is not already active.</span></span>  
  
4.  <span data-ttu-id="01963-112">单击要将数据查看器附加到其数据流的数据流任务，然后单击 **“数据流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="01963-112">Click the Data Flow task to whose data flow you want to attach a data viewer and then click the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="01963-113">右键单击两个数据流组件之间的路径，然后单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="01963-113">Right-click a path between two data flow components, and click **Edit**.</span></span>  
  
6.  <span data-ttu-id="01963-114">在 **“常规”** 页上，可以查看和编辑路径属性。</span><span class="sxs-lookup"><span data-stu-id="01963-114">On the **General** page, you can view and edit path properties.</span></span> <span data-ttu-id="01963-115">例如，从“路径批注”下拉列表中，你可以选择要在路径旁边显示的批注。</span><span class="sxs-lookup"><span data-stu-id="01963-115">For example, from the **PathAnnotation** drop-down list you can select the annotation that appears next to the path.</span></span>  
  
7.  <span data-ttu-id="01963-116">在 **“元数据”** 页上，您可以查看列元数据并将元数据复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="01963-116">On the **Metadata** page, you can view the column metadata and copy the metadata to the Clipboard.</span></span>  
  
8.  <span data-ttu-id="01963-117">在 **“数据查看器”** 页上，单击 **“启用数据查看器”** 。</span><span class="sxs-lookup"><span data-stu-id="01963-117">On the **Data Viewer** page, click **Enable data viewer**.</span></span>  
  
9. <span data-ttu-id="01963-118">在“要显示的列”区域中，选择要在数据查看器中显示的列。</span><span class="sxs-lookup"><span data-stu-id="01963-118">In the Columns to display area, select the columns you want to display in the data viewer.</span></span> <span data-ttu-id="01963-119">默认情况下，所有可用列都处于选定状态并在 **“已显示的列”** 列表中列出。</span><span class="sxs-lookup"><span data-stu-id="01963-119">By default, all the available columns are selected and listed in the **Displayed Columns** list.</span></span> <span data-ttu-id="01963-120">选择不希望使用的列，然后单击向左键，将它们移到 **“未使用的列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="01963-120">Move columns that you do not want to use to the **Unused Column** list by selecting them and then clicking the left arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01963-121">在网格中，表示 DT_DATE、DT_DBTIME2、DT_FILETIME、DT_DBTIMESTAMP、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 数据类型的值显示为 ISO 8601 格式字符串，空间分隔符将替代 `T` 分隔符。</span><span class="sxs-lookup"><span data-stu-id="01963-121">In the grid, values that represent the DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types appear as ISO 8601 formatted strings and a space separator replaces the `T` separator.</span></span> <span data-ttu-id="01963-122">表示 DT_DATE 和 DT_FILETIME 数据类型的值包括七位秒小数。</span><span class="sxs-lookup"><span data-stu-id="01963-122">Values that represent the DT_DATE and DT_FILETIME data types include seven digits for fractional seconds.</span></span> <span data-ttu-id="01963-123">因为 DT_FILETIME 数据类型仅存储三位秒小数，网格会将其余四位显示为零。</span><span class="sxs-lookup"><span data-stu-id="01963-123">Because the DT_FILETIME data type stores only three digits of fractional seconds, the grid displays zeros for the remaining four digits.</span></span> <span data-ttu-id="01963-124">表示 DT_DBTIMESTAMP 数据类型的值包含三位秒小数。</span><span class="sxs-lookup"><span data-stu-id="01963-124">Values that represent the DT_DBTIMESTAMP data type include three digits for fractional seconds.</span></span> <span data-ttu-id="01963-125">对于表示 DT_DBTIME2、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 数据类型的值，秒小数的数字位数与为列数据类型指定的小数位数对应。</span><span class="sxs-lookup"><span data-stu-id="01963-125">For values that represent the DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types, the number of digits for fractional seconds corresponds to the scale specified for the column's data type.</span></span> <span data-ttu-id="01963-126">有关 ISO 8601 格式的详细信息，请参阅 [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="01963-126">For more information about ISO 8601 formats, see [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span> <span data-ttu-id="01963-127">有关数据类型的详细信息，请参阅 [Integration Services Data Types](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="01963-127">For more information about data types, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
10. <span data-ttu-id="01963-128">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="01963-128">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01963-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01963-129">See Also</span></span>  
 <span data-ttu-id="01963-130">[Integration Services 转换](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="01963-130">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="01963-131">[Integration Services 路径](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="01963-131">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="01963-132">[数据流](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="01963-132">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="01963-133">调试数据流</span><span class="sxs-lookup"><span data-stu-id="01963-133">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
  
