---
title: "\"键列\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a72a9e137700ddee822e68901bfde971637d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579148"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6df93-102">“键列”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="6df93-102">Key Columns Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6df93-103">可以使用 **“键列”** 对话框更改特性的 **KeyColumns** 属性。</span><span class="sxs-lookup"><span data-stu-id="6df93-103">Use the **Key Columns** dialog box to change the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="6df93-104">有关详细信息，请参阅 [修改特性的 KeyColumn 属性](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)。</span><span class="sxs-lookup"><span data-stu-id="6df93-104">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
 <span data-ttu-id="6df93-105">**显示“键列”对话框**</span><span class="sxs-lookup"><span data-stu-id="6df93-105">**To display the Key Columns dialog box**</span></span>  
  
-   <span data-ttu-id="6df93-106">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，选择一个特性，然后在“属性”\*\*\*\* 窗口中单击与该特性的 **KeyColumns** 属性关联的省略号按钮 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="6df93-106">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select an attribute, and in the **Properties** window, click the ellipsis button (**...**) associated with the **KeyColumns** property of that attribute.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6df93-107">选项</span><span class="sxs-lookup"><span data-stu-id="6df93-107">Options</span></span>  
 <span data-ttu-id="6df93-108">**源表**</span><span class="sxs-lookup"><span data-stu-id="6df93-108">**Source table**</span></span>  
 <span data-ttu-id="6df93-109">选择要选择其键列的源表。</span><span class="sxs-lookup"><span data-stu-id="6df93-109">Select the source table for which you want to select its key columns.</span></span> <span data-ttu-id="6df93-110">可以从数据源视图的所有表列表中选择源表。</span><span class="sxs-lookup"><span data-stu-id="6df93-110">You can select the source table from a list of all tables in the Data Source View.</span></span>  
  
 <span data-ttu-id="6df93-111">**可用列**</span><span class="sxs-lookup"><span data-stu-id="6df93-111">**Available Columns**</span></span>  
 <span data-ttu-id="6df93-112">选择要用作键列的列。</span><span class="sxs-lookup"><span data-stu-id="6df93-112">Select the columns that you want to use as key columns.</span></span> <span data-ttu-id="6df93-113">可以从指定的 **“源表”** 的列列表中选择尚未选为键列的列。</span><span class="sxs-lookup"><span data-stu-id="6df93-113">You can select the columns from a list of columns in the specified **Source table** that have not yet been selected as key columns.</span></span>  
  
 <span data-ttu-id="6df93-114">若要将所选列添加到“键列”列表，请单击 **“键列”** 按钮 **>** 。</span><span class="sxs-lookup"><span data-stu-id="6df93-114">To add the selected columns to the **Key Columns** list, click the **>** button.</span></span>  
  
 <span data-ttu-id="6df93-115">**键列**</span><span class="sxs-lookup"><span data-stu-id="6df93-115">**Key Columns**</span></span>  
 <span data-ttu-id="6df93-116">定义所选键列的顺序。</span><span class="sxs-lookup"><span data-stu-id="6df93-116">Define the order of the selected key columns.</span></span> <span data-ttu-id="6df93-117">键列的顺序对于定义正确的组合键非常重要。</span><span class="sxs-lookup"><span data-stu-id="6df93-117">The order of the key columns is important in defining the correct composite key.</span></span> <span data-ttu-id="6df93-118">若要排序或重新排序键列列表，请选择列，然后单击 **“向上”** 或 **“向下”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="6df93-118">To order or reorder the list of key columns, select a column, and then click the **Up** or **Down** buttons.</span></span>  
  
 <span data-ttu-id="6df93-119">若要从“键列”列表中删除列，请选择列，然后单击 **“键列”** 按钮 **\<** 。</span><span class="sxs-lookup"><span data-stu-id="6df93-119">To remove a column from the **Key Columns** list, select the column and click the **\<** button.</span></span>  
  
 <span data-ttu-id="6df93-120">**Up**</span><span class="sxs-lookup"><span data-stu-id="6df93-120">**Up**</span></span>  
 <span data-ttu-id="6df93-121">单击此项可在\*\*\*\*“键列”中将所选列上移一个位置。</span><span class="sxs-lookup"><span data-stu-id="6df93-121">Click to move the column selected in **Key Columns** up one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6df93-122">仅当列表中包含一个以上列并且选定某列时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="6df93-122">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 <span data-ttu-id="6df93-123">**向下**</span><span class="sxs-lookup"><span data-stu-id="6df93-123">**Down**</span></span>  
 <span data-ttu-id="6df93-124">单击此项可在“键列”\*\*\*\* 中将所选列下移一个位置。</span><span class="sxs-lookup"><span data-stu-id="6df93-124">Click to move the column selected in **Key Columns** down one position.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6df93-125">仅当列表中包含一个以上列并且选定某列时，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="6df93-125">This option is enabled only if the list contains more than one column and a column is selected.</span></span>  
  
 **>**  
 <span data-ttu-id="6df93-126"> 单击此项可将新列添加到 **“键列”** 中列出的列的末尾。</span><span class="sxs-lookup"><span data-stu-id="6df93-126">Click to add a new column to the end of the columns listed in **Key Columns**.</span></span>  
  
 **<**  
 <span data-ttu-id="6df93-127"> 单击此项可将所选列从 **“键列”** 中列出的列中删除。</span><span class="sxs-lookup"><span data-stu-id="6df93-127">Click to remove the selected column from the columns listed in **Key Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df93-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6df93-128">See Also</span></span>  
 [<span data-ttu-id="6df93-129">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="6df93-129">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
