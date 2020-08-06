---
title: " (SSAS 表格) 创建计算列 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdb56ffb2b42aa8225b7eff76b11315ea511fd81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682387"
---
# <a name="create-a-calculated-column-ssas-tabular"></a><span data-ttu-id="30051-102">创建计算列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="30051-102">Create a Calculated Column (SSAS Tabular)</span></span>
  <span data-ttu-id="30051-103">通过计算列，可以将新数据添加到您的模型。</span><span class="sxs-lookup"><span data-stu-id="30051-103">Calculated columns allow you to add new data to your model.</span></span> <span data-ttu-id="30051-104">您可以创建定义列的行级值的 DAX 公式，而不是在列中粘贴或导入值。</span><span class="sxs-lookup"><span data-stu-id="30051-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="30051-105">计算列中每行的值在您创建有效公式并单击 Enter 后会进行计算和填充。</span><span class="sxs-lookup"><span data-stu-id="30051-105">The values in each row of a calculated column are calculated and populated when you create a valid formula and then click ENTER.</span></span> <span data-ttu-id="30051-106">然后可以将计算列添加到报告或分析应用程序中，就像添加任何其他数据列一样。</span><span class="sxs-lookup"><span data-stu-id="30051-106">The calculated column can then be added to a reporting or analysis application just as would any other column of data.</span></span> <span data-ttu-id="30051-107">本主题说明如何使用模型设计器中的 DAX 编辑栏创建新的计算列。</span><span class="sxs-lookup"><span data-stu-id="30051-107">This topic describes how to create a new calculated column by using the DAX formula bar in the model designer.</span></span>  
  
#### <a name="to-create-a-new-calculated-column"></a><span data-ttu-id="30051-108">创建新的计算列</span><span class="sxs-lookup"><span data-stu-id="30051-108">To create a new calculated column</span></span>  
  
1.  <span data-ttu-id="30051-109">在模型设计器的“数据视图”中，选择要添加计算列的表，单击 **“列”** 菜单，然后单击 **“添加列”**。</span><span class="sxs-lookup"><span data-stu-id="30051-109">In the model designer, in Data View, select the table to which you want to add a calculated column, then click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="30051-110">**“添加列”** 将在最右侧的空列之上突出显示，并且光标将移到公式栏。</span><span class="sxs-lookup"><span data-stu-id="30051-110">**Add Column** is highlighted over the empty rightmost column, and the cursor moves to the formula bar.</span></span>  
  
     <span data-ttu-id="30051-111">若要在两个现有列之间创建新列，请右键单击某个现有列，然后单击\*\*\*\*“插入列”。</span><span class="sxs-lookup"><span data-stu-id="30051-111">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="30051-112">在编辑栏中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="30051-112">In the formula bar, do one of the following:</span></span>  
  
    -   <span data-ttu-id="30051-113">键入等号，后跟公式。</span><span class="sxs-lookup"><span data-stu-id="30051-113">Type an equal sign followed by a formula.</span></span>  
  
    -   <span data-ttu-id="30051-114">键入等号，后跟 DAX 函数和该函数所需的参数。</span><span class="sxs-lookup"><span data-stu-id="30051-114">Type an equal sign, followed by a DAX function, followed by arguments and parameters as required by the function.</span></span>  
  
    -   <span data-ttu-id="30051-115">单击函数按钮 (**fx**)，在“插入函数”对话框中选择一个类别和函数，然后单击“确定”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30051-115">Click the function button (**fx**), then in the **Insert Function** dialog box, select a category and function, and then click **OK**.</span></span> <span data-ttu-id="30051-116">在编辑栏中键入该函数所需的其他参数。</span><span class="sxs-lookup"><span data-stu-id="30051-116">In the formula bar, type the remaining arguments and parameters as required by the function.</span></span>  
  
3.  <span data-ttu-id="30051-117">按 Enter 以接受该公式。</span><span class="sxs-lookup"><span data-stu-id="30051-117">Press ENTER to accept the formula.</span></span>  
  
     <span data-ttu-id="30051-118">整个列将用该公式填充，将为每一行计算值。</span><span class="sxs-lookup"><span data-stu-id="30051-118">The entire column is populated with the formula, and a value is calculated for each row.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="30051-119">可以在具有嵌套函数的现有公式中使用 DAX 公式记忆式键入功能。</span><span class="sxs-lookup"><span data-stu-id="30051-119">You can use DAX Formula AutoComplete in the middle of an existing formula with nested functions.</span></span> <span data-ttu-id="30051-120">刚好在插入点之前的文本将用于显示下拉列表中的值，并且插入点之后的所有文本都保持不变。</span><span class="sxs-lookup"><span data-stu-id="30051-120">The text immediately before the insertion point is used to display values in the drop-down list, and all of the text after the insertion point remains unchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30051-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30051-121">See Also</span></span>  
 <span data-ttu-id="30051-122">[&#40;SSAS 表格&#41;计算列](ssas-calculated-columns.md) </span><span class="sxs-lookup"><span data-stu-id="30051-122">[Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md) </span></span>  
 [<span data-ttu-id="30051-123">度量值（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="30051-123">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
