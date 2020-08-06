---
title: 通过使用 Union All 转换来合并数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e782a5770ab9936e4c5cc84da706a5472ecd4d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589791"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a><span data-ttu-id="de7e1-102">通过使用 Union All 转换来合并数据</span><span class="sxs-lookup"><span data-stu-id="de7e1-102">Merge Data by Using the Union All Transformation</span></span>
  <span data-ttu-id="de7e1-103">若要添加和配置 Union All 转换，包必须至少已包含一个数据流任务和两个数据源。</span><span class="sxs-lookup"><span data-stu-id="de7e1-103">To add and configure a Union All transformation, the package must already include at least one Data Flow task and two data sources.</span></span>  
  
 <span data-ttu-id="de7e1-104">Union All 转换组合多个输入。</span><span class="sxs-lookup"><span data-stu-id="de7e1-104">The Union All transformation combines multiple inputs.</span></span> <span data-ttu-id="de7e1-105">连接到转换的第一个输入是引用输入，以后连接的输入是辅助输入。</span><span class="sxs-lookup"><span data-stu-id="de7e1-105">The first input that is connected to the transformation is the reference input, and the inputs connected subsequently are the secondary inputs.</span></span> <span data-ttu-id="de7e1-106">输出包含引用输入中的列。</span><span class="sxs-lookup"><span data-stu-id="de7e1-106">The output includes the columns in the reference input.</span></span>  
  
### <a name="to-combine-inputs-in-a-data-flow"></a><span data-ttu-id="de7e1-107">组合数据流中的输入</span><span class="sxs-lookup"><span data-stu-id="de7e1-107">To combine inputs in a data flow</span></span>  
  
1.  <span data-ttu-id="de7e1-108">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中，双击解决方案资源管理器中的包将其在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中打开，然后单击“数据流”选项卡。</span><span class="sxs-lookup"><span data-stu-id="de7e1-108">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], double-click the package in Solution Explorer to open the package in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and then click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="de7e1-109">将 Union All 转换从 **“工具箱”** 拖动到 **“数据流”** 选项卡的设计图面。</span><span class="sxs-lookup"><span data-stu-id="de7e1-109">From the **Toolbox**, drag the Union All transformation to the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="de7e1-110">将连接线从数据源或前一个转换拖到 Union All 转换，从而将 Union All 转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="de7e1-110">Connect the Union All transformation to the data flow by dragging a connector from the data source or a previous transformation to the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="de7e1-111">双击 Union All 转换。</span><span class="sxs-lookup"><span data-stu-id="de7e1-111">Double-click the Union All transformation.</span></span>  
  
5.  <span data-ttu-id="de7e1-112">在 **“Union All 转换编辑器”** 中，通过单击行然后在输入列表中选择列，将输入中的列映射到 **“输出列的名称”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="de7e1-112">In the **Union All Transformation Editor**, map a column from an input to a column in the **Output Column Name** list by clicking a row and then selecting a column in the input list.</span></span> <span data-ttu-id="de7e1-113">在输入列表中选择 \<ignore> 以跳过对该列的映射。</span><span class="sxs-lookup"><span data-stu-id="de7e1-113">Select **\<ignore>** in the input list to skip mapping the column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de7e1-114">两列间的映射要求各列的元数据相匹配。</span><span class="sxs-lookup"><span data-stu-id="de7e1-114">The mapping between two columns requires that the metadata of the columns match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de7e1-115">辅助输入中未映射到引用列的列在输出中设置为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="de7e1-115">Columns in a secondary input that are not mapped to reference columns are set to null values in the output.</span></span>  
  
6.  <span data-ttu-id="de7e1-116">根据需要，也可以在 **“输出列的名称”** 列中修改列的名称。</span><span class="sxs-lookup"><span data-stu-id="de7e1-116">Optionally, modify the names of columns in the **Output Column Name** column.</span></span>  
  
7.  <span data-ttu-id="de7e1-117">对每个输入中的每一列重复第 5 和第 6 步。</span><span class="sxs-lookup"><span data-stu-id="de7e1-117">Repeat steps 5 and 6 for each column in each input.</span></span>  
  
8.  <span data-ttu-id="de7e1-118">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="de7e1-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="de7e1-119">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="de7e1-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7e1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de7e1-120">See Also</span></span>  
 <span data-ttu-id="de7e1-121">[Union All 转换](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="de7e1-121">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="de7e1-122">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="de7e1-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="de7e1-123">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="de7e1-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="de7e1-124">数据流任务</span><span class="sxs-lookup"><span data-stu-id="de7e1-124">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
