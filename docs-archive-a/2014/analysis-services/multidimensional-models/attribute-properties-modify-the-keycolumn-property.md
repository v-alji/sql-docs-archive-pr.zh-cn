---
title: 修改特性的 KeyColumn 属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3367a7aec84ba59efd118a56745bb76fc5266061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693554"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a><span data-ttu-id="bb524-102">修改某个特性的 KeyColumn 属性</span><span class="sxs-lookup"><span data-stu-id="bb524-102">Modify the KeyColumn Property of an Attribute</span></span>
  <span data-ttu-id="bb524-103">可以修改特性的 **KeyColumns** 属性。</span><span class="sxs-lookup"><span data-stu-id="bb524-103">You can modify the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="bb524-104">例如，您可能需要指定组合键以作为该特性的键，而不是指定单个键。</span><span class="sxs-lookup"><span data-stu-id="bb524-104">For example, you might want to specify a composite key instead of a single key as the key for the attribute.</span></span>  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a><span data-ttu-id="bb524-105">修改某个特性的 KeyColumns 属性</span><span class="sxs-lookup"><span data-stu-id="bb524-105">To modify the KeyColumns property of an attribute</span></span>  
  
1.  <span data-ttu-id="bb524-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开要修改其中 **KeyColumns** 属性的项目。</span><span class="sxs-lookup"><span data-stu-id="bb524-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project in which you want to modify the **KeyColumns** property.</span></span>  
  
2.  <span data-ttu-id="bb524-107">通过执行下列过程之一打开维度设计器：</span><span class="sxs-lookup"><span data-stu-id="bb524-107">Open Dimension Designer by doing one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="bb524-108">在**解决方案资源管理器**中，右键单击“维度”文件夹中的维度，然后单击“打开”或“视图设计器”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb524-108">In **Solution Explorer**, right-click the dimension in the **Dimensions** folder, and then either click **Open** or **View Designer**.</span></span>  
  
         <span data-ttu-id="bb524-109">- 或 -</span><span class="sxs-lookup"><span data-stu-id="bb524-109">-or-</span></span>  
  
    -   <span data-ttu-id="bb524-110">在多维数据集设计器的 "**多维数据集结构**" 选项卡上，展开 "**维度**" 窗格中的多维数据集维度，然后单击\*\*编辑 \<dimension> \*\*</span><span class="sxs-lookup"><span data-stu-id="bb524-110">In Cube Designer, on the **Cube Structure** tab, expand the cube dimension in the **Dimensions** pane and click **Edit \<dimension>**.</span></span>  
  
3.  <span data-ttu-id="bb524-111">在 **“维度结构”** 选项卡的 **“属性”** 窗格中，单击要修改其 **KeyColumns** 属性的特性。</span><span class="sxs-lookup"><span data-stu-id="bb524-111">On the **Dimension Structure** tab, in the **Attributes** pane, click the attribute whose **KeyColumns** property you want to modify.</span></span>  
  
4.  <span data-ttu-id="bb524-112">在 **“属性”** 窗口中，单击 **KeyColumns** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="bb524-112">In the **Properties** window, click the value for the **KeyColumns** property.</span></span>  
  
5.  <span data-ttu-id="bb524-113">单击在属性框的值单元中出现的浏览按钮 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="bb524-113">Click the browse **(...)** button that appears in the value cell of the property box.</span></span>  
  
     <span data-ttu-id="bb524-114">**“键列”** 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="bb524-114">The **Key Columns** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="bb524-115">若要删除现有键列，请在“键列”\*\*\*\* 列表中选择相应的列，然后单击“\<”按钮\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb524-115">To remove an existing key column, in the **Key Columns** list, select the column, and then click the **\<** button.</span></span>  
  
7.  <span data-ttu-id="bb524-116">若要添加键列，请在“可用列”\*\*\*\* 列表中选择相应的列，然后单击“>”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="bb524-116">To add a key column, in the **Available Columns** list, select the column, and then click the **>** button.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb524-117">如果定义多个键列，则这些列在 **“键列”** 列表中的排序将影响键列的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="bb524-117">If you define multiple key columns, the order in which those columns appear in the **Key Columns** list affects the display order.</span></span> <span data-ttu-id="bb524-118">例如，月特性有两个键列：月和年。</span><span class="sxs-lookup"><span data-stu-id="bb524-118">For example, a month attribute has two key columns: month and year.</span></span> <span data-ttu-id="bb524-119">如果列表中年列显示在月列前，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将先按年进行排序，再按月进行排序。</span><span class="sxs-lookup"><span data-stu-id="bb524-119">If the year column appears in the list before the month column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by year and then by month.</span></span> <span data-ttu-id="bb524-120">如果月列显示在年列前，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将先按月进行排序，再按年进行排序。</span><span class="sxs-lookup"><span data-stu-id="bb524-120">If the month column appears before the year column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by month and then by year.</span></span>  
  
8.  <span data-ttu-id="bb524-121">若要更改键列的顺序，请选择一列，然后单击 **“向上”** 或 **“向下”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="bb524-121">To change the order of key columns, select a column, and then click the **Up** or **Down** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb524-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb524-122">See Also</span></span>  
 [<span data-ttu-id="bb524-123">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="bb524-123">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
