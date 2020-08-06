---
title: 使用模糊分组转换标识相似数据行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4e6d49548c211b38a35d6f5f7efc3d50fec93588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589804"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a><span data-ttu-id="e5aa4-102">使用模糊分组转换标识相似数据行</span><span class="sxs-lookup"><span data-stu-id="e5aa4-102">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="e5aa4-103">若要添加和配置模糊分组转换，包必须已包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-103">To add and configure a Fuzzy Grouping transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a><span data-ttu-id="e5aa4-104">在数据流中实现模糊分组转换</span><span class="sxs-lookup"><span data-stu-id="e5aa4-104">To implement Fuzzy Grouping transformation in a data flow</span></span>  
  
1.  <span data-ttu-id="e5aa4-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e5aa4-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e5aa4-107">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将模糊分组转换拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Fuzzy Grouping transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="e5aa4-108">将连接线从数据源或前一个转换拖到模糊分组转换，从而将模糊分组转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-108">Connect the Fuzzy Grouping transformation to the data flow by dragging the connector from the data source or a previous transformation to the Fuzzy Grouping transformation.</span></span>  
  
5.  <span data-ttu-id="e5aa4-109">双击模糊分组转换。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-109">Double-click the Fuzzy Grouping transformation.</span></span>  
  
6.  <span data-ttu-id="e5aa4-110">在 **“模糊分组转换编辑器”** 对话框中的 **“连接管理器”** 选项卡上，选择连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-110">In the **Fuzzy Grouping Transformation Editor** dialog box, on the **Connection Manager** tab, select an OLE DB connection manager that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5aa4-111">转换要求连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库，以创建临时表和索引。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-111">The transformation requires a connection to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database to create temporary tables and indexes.</span></span>  
  
7.  <span data-ttu-id="e5aa4-112">单击 **“列”** 选项卡，在 **“可用输入列”** 列表中，选中要使用的输入列的复选框，以标识数据集中的相似行。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-112">Click the **Columns** tab and, in the **Available Input Columns** list, select the check box of the input columns to use to identify similar rows in the dataset.</span></span>  
  
8.  <span data-ttu-id="e5aa4-113">选中 **“传递”** 列中的复选框，以标识要传递到转换输出的输入列。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-113">Select the check box in the **Pass Through** column to identify the input columns to pass through to the transformation output.</span></span> <span data-ttu-id="e5aa4-114">在重复行的标识过程中不包含传递列。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-114">Pass-through columns are not included in the process of identification of duplicate rows.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5aa4-115">用于分组的输入列自动被选为传递列，所以当用于分组时无法取消选择这些输入列。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-115">Input columns that are used for grouping are automatically selected as pass-through columns, and they cannot be unselected while used for grouping.</span></span>  
  
9. <span data-ttu-id="e5aa4-116">还可以更新 **“输出别名”** 列中的输出列名称。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-116">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="e5aa4-117">还可以更新“组输出别名”  列中清除的列的名称。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-117">Optionally, update the names of cleaned columns in the **Group OutputAlias** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5aa4-118">列的默认名称为输入列名称加“_clean”后缀。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-118">The default names of columns are the names of the input columns with a "_clean" suffix.</span></span>  
  
11. <span data-ttu-id="e5aa4-119">还可以更新 **“匹配类型”** 列中所使用的匹配类型。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-119">Optionally, update the type of match to use in the **Match Type** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e5aa4-120">至少有一列必须使用模糊匹配。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-120">At least one column must use fuzzy matching.</span></span>  
  
12. <span data-ttu-id="e5aa4-121">指定 **“最低相似性”** 列中的最低相似性级别列。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-121">Specify the minimum similarity level columns in the **Minimum Similarity** column.</span></span> <span data-ttu-id="e5aa4-122">该值必须介于 0 和 1 之间。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-122">The value must be between 0 and 1.</span></span> <span data-ttu-id="e5aa4-123">值越接近 1，则输入列中的值必然越接近于组成一组。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-123">The closer the value is to 1, the more similar the values in the input columns must be to form a group.</span></span> <span data-ttu-id="e5aa4-124">最低相似性为 1，则指示完全匹配。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-124">A minimum similarity of 1 indicates an exact match.</span></span>  
  
13. <span data-ttu-id="e5aa4-125">还可以更新 **“相似性输出别名”** 列中的相似性列的名称。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-125">Optionally, update the names of similarity columns in the **Similarity Output Alias** column.</span></span>  
  
14. <span data-ttu-id="e5aa4-126">指定数据值中数字的处理方式，更新 **“数字”** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-126">To specify the handling of numbers in data values, update the values in the **Numerals** column.</span></span>  
  
15. <span data-ttu-id="e5aa4-127">若要指定转换如何比较列中的字符串数据，请修改 **“比较标志”** 列中比较选项的默认选择。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-127">To specify how the transformation compares the string data in a column, modify the default selection of comparison options in the **Comparison Flags** column.</span></span>  
  
16. <span data-ttu-id="e5aa4-128">单击“高级”  选项卡，修改该转换为唯一行标识符 (_key_in)、重复行标识符 (_key_out) 和相似性值 (_score) 添加到输出的列的名称。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-128">Click the **Advanced** tab to modify the names of the columns that the transformation adds to the output for the unique row identifier (_key_in), the duplicate row identifier (_key_out), and the similarity value (_score).</span></span>  
  
17. <span data-ttu-id="e5aa4-129">还可以通过移动滑块来调节相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-129">Optionally, adjust the similarity threshold by moving the slider bar.</span></span>  
  
18. <span data-ttu-id="e5aa4-130">还可以清除标记分隔符复选框以忽略数据中的分隔符。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-130">Optionally, clear the token delimiter check boxes to ignore delimiters in the data.</span></span>  
  
19. <span data-ttu-id="e5aa4-131">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="e5aa4-131">Click **OK**.</span></span>  
  
20. <span data-ttu-id="e5aa4-132">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="e5aa4-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5aa4-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5aa4-133">See Also</span></span>  
 <span data-ttu-id="e5aa4-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="e5aa4-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span></span>  
 <span data-ttu-id="e5aa4-135">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="e5aa4-135">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="e5aa4-136">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="e5aa4-136">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="e5aa4-137">数据流任务</span><span class="sxs-lookup"><span data-stu-id="e5aa4-137">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
