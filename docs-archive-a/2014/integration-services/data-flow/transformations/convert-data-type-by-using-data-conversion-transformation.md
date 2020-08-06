---
title: 使用 "数据转换" 转换将数据转换为其他数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 878741717c36c18e9a069c62e86be0148272239f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587939"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a><span data-ttu-id="e0676-102">使用数据转换将数据转换为其他数据类型</span><span class="sxs-lookup"><span data-stu-id="e0676-102">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>
  <span data-ttu-id="e0676-103">若要添加并配置数据转换，包必须已经包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="e0676-103">To add and configure a Data Conversion transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-convert-data-to-a-different-data-type"></a><span data-ttu-id="e0676-104">将数据转换为其他数据类型</span><span class="sxs-lookup"><span data-stu-id="e0676-104">To convert data to a different data type</span></span>  
  
1.  <span data-ttu-id="e0676-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="e0676-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e0676-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="e0676-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e0676-107">单击 **“数据流”** 选项卡，再从 **“工具箱”** 中将数据转换拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="e0676-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Data Conversion transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="e0676-108">将连接线从源或前一转换拖到数据转换，从而将数据转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="e0676-108">Connect the Data Conversion transformation to the data flow by dragging a connector from the source or the previous transformation to the Data Conversion transformation.</span></span>  
  
5.  <span data-ttu-id="e0676-109">双击此数据转换。</span><span class="sxs-lookup"><span data-stu-id="e0676-109">Double-click the Data Conversion transformation.</span></span>  
  
6.  <span data-ttu-id="e0676-110">在“数据转换编辑器”对话框的“可用输入列”表中，选中位于要转换其数据类型的列旁边的复选框   。</span><span class="sxs-lookup"><span data-stu-id="e0676-110">In the **Data ConversionTransformation Editor** dialog box, in the **Available Input Columns** table, select the check box next to the columns whose data type you want to convert.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0676-111">可以将多个数据转换应用到一个输入列。</span><span class="sxs-lookup"><span data-stu-id="e0676-111">You can apply multiple data conversions to an input column.</span></span>  
  
7.  <span data-ttu-id="e0676-112">也可以在 **“输出别名”** 列中修改默认值。</span><span class="sxs-lookup"><span data-stu-id="e0676-112">Optionally, modify the default values in the **Output Alias** column.</span></span>  
  
8.  <span data-ttu-id="e0676-113">在 **“数据类型”** 列表中，选择列的新数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0676-113">In the **Data Type** list, select the new data type for the column.</span></span> <span data-ttu-id="e0676-114">默认数据类型为输入列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e0676-114">The default data type is the data type of the input column.</span></span>  
  
9. <span data-ttu-id="e0676-115">也可以根据所选数据类型更新 **“长度”** 、 **“精度”** 、 **“小数位数”** 和 **“代码页”** 列的值。</span><span class="sxs-lookup"><span data-stu-id="e0676-115">Optionally, depending on the selected data type, update the values in the **Length**, the **Precision**, the **Scale**, and the **Code Page** columns.</span></span>  
  
10. <span data-ttu-id="e0676-116">若要配置错误输出，请单击 **“配置错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="e0676-116">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="e0676-117">有关详细信息，请参阅 [在数据流组件中配置错误输出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e0676-117">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="e0676-118">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="e0676-118">Click **OK**.</span></span>  
  
12. <span data-ttu-id="e0676-119">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="e0676-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0676-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0676-120">See Also</span></span>  
 <span data-ttu-id="e0676-121">[Data Conversion Transformation](data-conversion-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="e0676-121">[Data Conversion Transformation](data-conversion-transformation.md) </span></span>  
 <span data-ttu-id="e0676-122">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="e0676-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="e0676-123">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="e0676-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="e0676-124">[Integration Services 数据类型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="e0676-124">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 [<span data-ttu-id="e0676-125">数据流任务</span><span class="sxs-lookup"><span data-stu-id="e0676-125">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
