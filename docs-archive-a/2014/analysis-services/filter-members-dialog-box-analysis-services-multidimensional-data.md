---
title: "\"筛选成员\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.filtermembers.f1
helpviewer_keywords:
- Filter Members dialog box
ms.assetid: 52c6da1d-9fb5-4dbc-bffa-248d11cd337c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66980b1afe9d4eed353ae18c37ed1fdd052e62b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577051"
---
# <a name="filter-members-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="18dc5-102">“筛选成员”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="18dc5-102">Filter Members Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="18dc5-103">可以使用 **中的** “筛选成员” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，在 **“维度设计器”** 的 **“浏览器”** 选项卡中浏览维度的同时，按当前级别的成员标题、成员名称、成员唯一名称、键列值或值列值对维度成员进行筛选。</span><span class="sxs-lookup"><span data-stu-id="18dc5-103">Use the **Filter Members** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to filter dimension members by member caption, member name, member unique name, key column value, or value column value for the current level while browsing a dimension in the **Browser** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="18dc5-104">选项</span><span class="sxs-lookup"><span data-stu-id="18dc5-104">Options</span></span>  
  
|<span data-ttu-id="18dc5-105">术语</span><span class="sxs-lookup"><span data-stu-id="18dc5-105">Term</span></span>|<span data-ttu-id="18dc5-106">定义</span><span class="sxs-lookup"><span data-stu-id="18dc5-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="18dc5-107">**筛选器表达式**</span><span class="sxs-lookup"><span data-stu-id="18dc5-107">**Filter expression**</span></span>|<span data-ttu-id="18dc5-108">显示一个网格，其中包含用于构造筛选表达式的属性、运算符和值。</span><span class="sxs-lookup"><span data-stu-id="18dc5-108">Displays a grid of properties, operators, and values used to construct a filter expression.</span></span> <span data-ttu-id="18dc5-109">请注意，添加一行之后，无法删除该行。</span><span class="sxs-lookup"><span data-stu-id="18dc5-109">Note that after a row is added, it cannot be removed.</span></span> <span data-ttu-id="18dc5-110">必须关闭并重新打开该对话框，才可指定新的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="18dc5-110">You must close and reopen the dialog box to specify a new filter expression.</span></span> <span data-ttu-id="18dc5-111">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="18dc5-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="18dc5-112">**属性**：选择要用于筛选表达式的成员的属性。</span><span class="sxs-lookup"><span data-stu-id="18dc5-112">**Property**: Select the property of the member to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="18dc5-113">**运算符**：选择要用于筛选表达式的运算符。</span><span class="sxs-lookup"><span data-stu-id="18dc5-113">**Operator**: Select the operator to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="18dc5-114">**值**：键入在**属性**中选择的属性的值，以使用**运算符**中指定的运算符进行计算。</span><span class="sxs-lookup"><span data-stu-id="18dc5-114">**Value**: Type the value of the property selected in **Property** to evaluate using the operator specified in **Operator**.</span></span>|  
|<span data-ttu-id="18dc5-115">**“测试”窗格**</span><span class="sxs-lookup"><span data-stu-id="18dc5-115">**Test pane**</span></span>|<span data-ttu-id="18dc5-116">单击 **“测试”** 时，此窗格将显示筛选表达式所返回的成员。</span><span class="sxs-lookup"><span data-stu-id="18dc5-116">When **Test** is clicked, this pane displays the members returned by the filter expression.</span></span> <span data-ttu-id="18dc5-117">如果使用在 **“筛选表达式”** 中指定的条件没有返回任何成员，则会显示警告。</span><span class="sxs-lookup"><span data-stu-id="18dc5-117">If no members are returned using the criteria specified in **Filter expression**, a warning is displayed.</span></span>|  
|<span data-ttu-id="18dc5-118">**Test**</span><span class="sxs-lookup"><span data-stu-id="18dc5-118">**Test**</span></span>|<span data-ttu-id="18dc5-119">单击此项可以测试在 **“筛选表达式”** 中指定的条件。</span><span class="sxs-lookup"><span data-stu-id="18dc5-119">Click to test the criteria specified in **Filter expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18dc5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18dc5-120">See Also</span></span>  
 <span data-ttu-id="18dc5-121">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="18dc5-121">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="18dc5-122">&#41; &#40;Analysis Services 多维&#41;数据的浏览器 &#40;维度设计器</span><span class="sxs-lookup"><span data-stu-id="18dc5-122">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
