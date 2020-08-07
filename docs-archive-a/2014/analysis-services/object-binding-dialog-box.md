---
title: "\"对象绑定\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
ms.openlocfilehash: a10c91e0222b826066aeede96aa665cc22540637
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588088"
---
# <a name="object-binding-dialog-box"></a><span data-ttu-id="34e93-102">“对象绑定”对话框</span><span class="sxs-lookup"><span data-stu-id="34e93-102">Object Binding Dialog Box</span></span>
  <span data-ttu-id="34e93-103">使用 **中的** “对象绑定” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，可以定义 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的属性与数据源视图中的表或列之间的绑定。</span><span class="sxs-lookup"><span data-stu-id="34e93-103">Use the **Object Binding** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define bindings between the property of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object and a table or column in a data source view.</span></span> <span data-ttu-id="34e93-104">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“属性”\*\*\*\* 窗口中，通过从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的下列属性值的下拉列表中选择“(新建)”\*\*\*\*，可以显示“对象绑定”\*\*\*\* 对话框：</span><span class="sxs-lookup"><span data-stu-id="34e93-104">You can display the **Object Binding** dialog box by selecting **(new)** from the drop-down list for the value of the following properties of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   <span data-ttu-id="34e93-105">NameColumn</span><span class="sxs-lookup"><span data-stu-id="34e93-105">NameColumn</span></span>  
  
-   <span data-ttu-id="34e93-106">ValueColumn</span><span class="sxs-lookup"><span data-stu-id="34e93-106">ValueColumn</span></span>  
  
-   <span data-ttu-id="34e93-107">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="34e93-107">CustomRollupColumn</span></span>  
  
-   <span data-ttu-id="34e93-108">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="34e93-108">CustomRollupPropertiesColumn</span></span>  
  
-   <span data-ttu-id="34e93-109">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="34e93-109">UnaryOperatorColumn</span></span>  
  
## <a name="options"></a><span data-ttu-id="34e93-110">选项</span><span class="sxs-lookup"><span data-stu-id="34e93-110">Options</span></span>  
 <span data-ttu-id="34e93-111">**绑定类型**</span><span class="sxs-lookup"><span data-stu-id="34e93-111">**Binding type**</span></span>  
 <span data-ttu-id="34e93-112">选择要为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象使用的绑定。</span><span class="sxs-lookup"><span data-stu-id="34e93-112">Select the binding to use for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="34e93-113">可以使用以下类型的绑定：</span><span class="sxs-lookup"><span data-stu-id="34e93-113">The following types of binding can be used:</span></span>  
  
 <span data-ttu-id="34e93-114">列绑定</span><span class="sxs-lookup"><span data-stu-id="34e93-114">Column binding</span></span>  
 <span data-ttu-id="34e93-115">将对象绑定到数据源视图中的现有表和列。</span><span class="sxs-lookup"><span data-stu-id="34e93-115">Binds the object to an existing table and column within a data source view.</span></span>  
  
 <span data-ttu-id="34e93-116">生成列</span><span class="sxs-lookup"><span data-stu-id="34e93-116">Generate column</span></span>  
 <span data-ttu-id="34e93-117">指示将在数据源视图中定义新列，然后将列绑定与其相关联。</span><span class="sxs-lookup"><span data-stu-id="34e93-117">Indicates that a new column is to be defined in the data source view, and a column binding is then associated with it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34e93-118">如果选中此选项，则必须在部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象之前运行“架构生成向导”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="34e93-118">If this option is selected, you must run the **Schema Generation Wizard** before deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="34e93-119">行绑定</span><span class="sxs-lookup"><span data-stu-id="34e93-119">Row binding</span></span>  
 <span data-ttu-id="34e93-120">将对象绑定到事实数据表中的行，用于支持基于事实数据表中已处理行数的计数度量值。</span><span class="sxs-lookup"><span data-stu-id="34e93-120">Binds the object to a row in a fact table and is used to facilitate count measures based on the number of rows processed in the fact table.</span></span>  
  
 <span data-ttu-id="34e93-121">**源表**</span><span class="sxs-lookup"><span data-stu-id="34e93-121">**Source table**</span></span>  
 <span data-ttu-id="34e93-122">显示数据源视图中与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象关联的表的列表。</span><span class="sxs-lookup"><span data-stu-id="34e93-122">Displays a list of tables in the data source view associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="34e93-123">**源列**</span><span class="sxs-lookup"><span data-stu-id="34e93-123">**Source column**</span></span>  
 <span data-ttu-id="34e93-124">显示在“源表”\*\*\*\* 中选择的表中列的列表。</span><span class="sxs-lookup"><span data-stu-id="34e93-124">Displays a list of columns in the table selected in **Source table**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e93-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34e93-125">See Also</span></span>  
 [<span data-ttu-id="34e93-126">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="34e93-126">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
