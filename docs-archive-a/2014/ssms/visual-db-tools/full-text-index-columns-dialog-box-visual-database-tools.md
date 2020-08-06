---
title: “全文索引列”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f1cd2c94739a13e1820d8c05b338abd91d8a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693603"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="e575e-102">“全文本索引列”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e575e-102">Full-Text Index Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="e575e-103">此对话框列出了参与表设计器中所打开表的全文本索引的列。</span><span class="sxs-lookup"><span data-stu-id="e575e-103">This dialog box lists the columns participating in the full-text index for the table open in Table Designer.</span></span> <span data-ttu-id="e575e-104">若要访问此对话框，请在表设计器中右键单击相应的表，选择“全文检索”，然后在“全文检索”对话框中，单击具有要查看或编辑的列的索引，单击右侧网格中的“列”字段，再单击省略号 (…)     。</span><span class="sxs-lookup"><span data-stu-id="e575e-104">To access this dialog box, right-click the table in Table Designer, choose **Full-Text Index**, and in the **Full-Text Index** dialog box, click the index with columns you want to view or edit, click the **Columns** field in the grid to the right, and click the ellipses (**...**).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e575e-105">选项</span><span class="sxs-lookup"><span data-stu-id="e575e-105">Options</span></span>  
 <span data-ttu-id="e575e-106">**列**</span><span class="sxs-lookup"><span data-stu-id="e575e-106">**Column**</span></span>  
 <span data-ttu-id="e575e-107">显示参与全文本索引的列的名称。</span><span class="sxs-lookup"><span data-stu-id="e575e-107">Shows the names of columns participating in the full-text index.</span></span> <span data-ttu-id="e575e-108">若要添加列，请单击第一个空单元格，再从下拉列表中选择列。</span><span class="sxs-lookup"><span data-stu-id="e575e-108">To add a column, click in the first empty cell and choose a column from the drop-down list.</span></span> <span data-ttu-id="e575e-109">只能基于文本的数据类型或 image 数据类型的列才可访问。</span><span class="sxs-lookup"><span data-stu-id="e575e-109">Only columns with either text-based or image data types will be accessible.</span></span>  
  
 <span data-ttu-id="e575e-110">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="e575e-110">**Data Type**</span></span>  
 <span data-ttu-id="e575e-111">显示每列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e575e-111">Shows the data type for each column.</span></span> <span data-ttu-id="e575e-112">这是只读属性。</span><span class="sxs-lookup"><span data-stu-id="e575e-112">This is a read-only property.</span></span> <span data-ttu-id="e575e-113">若要更改数据类型，请在表设计器中打开表，单击相应列，然后在“列属性”  选项卡中编辑数据类型。</span><span class="sxs-lookup"><span data-stu-id="e575e-113">To change a data type, open the table in Table Designer, click the column, and edit the data type in the **Column Properties** tab.</span></span>  
  
 <span data-ttu-id="e575e-114">**按列分类**</span><span class="sxs-lookup"><span data-stu-id="e575e-114">**Typed by Column**</span></span>  
 <span data-ttu-id="e575e-115">仅适用于数据类型为 `image` 的列。</span><span class="sxs-lookup"><span data-stu-id="e575e-115">Applies only to columns with the data type `image`.</span></span> <span data-ttu-id="e575e-116">提供一个下拉列表，可以从中选择其他列中哪一列代表此列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e575e-116">Provides a drop-down list from which you can choose which of the other columns represent the data type of this column.</span></span> <span data-ttu-id="e575e-117">如果此列的数据类型不是 `image`，则该值将为“无”。</span><span class="sxs-lookup"><span data-stu-id="e575e-117">If this column is not of the `image` data type the value will be None.</span></span>  
  
 <span data-ttu-id="e575e-118">数据类型为 `image` 的列可以包含 Microsoft Office 文件（.doc、.xls 和 .ppt 文件）、文本文件（.txt 文件）和 HTML 文件（.htm 文件），将该列的数据类型设置为 image 将允许进行全文搜索以搜索文件的内容。</span><span class="sxs-lookup"><span data-stu-id="e575e-118">Columns with the data type `image` can contain Microsoft Office files (.doc, .xls, and .ppt files), text files (.txt files), and HTML files (.htm files), and setting the data type of that column to image allows the full-text search to search the contents of the files.</span></span>  
  
 <span data-ttu-id="e575e-119">**语言**</span><span class="sxs-lookup"><span data-stu-id="e575e-119">**Language**</span></span>  
 <span data-ttu-id="e575e-120">列出可用语言。</span><span class="sxs-lookup"><span data-stu-id="e575e-120">Lists available languages.</span></span> <span data-ttu-id="e575e-121">从下拉列表中选择适合您的列数据的语言。</span><span class="sxs-lookup"><span data-stu-id="e575e-121">Choose the language from the drop-down list appropriate for your column data.</span></span> <span data-ttu-id="e575e-122">例如，如果您使用的是英语版本的操作系统，但希望对包含德文的列进行索引，请从下拉列表中选择“德语”以提高索引的性能。</span><span class="sxs-lookup"><span data-stu-id="e575e-122">For example, if you are using an English operating system, but you want to index a column that contains German text, choose German from the drop-down list to improve the index's performance.</span></span>  
  
 <span data-ttu-id="e575e-123">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="e575e-123">**Statistical Semantics**</span></span>  
 <span data-ttu-id="e575e-124">选择是否为所选列启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="e575e-124">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="e575e-125">有关详细信息，请参阅[语义搜索 (SQL Server)](../../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e575e-125">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="e575e-126">如果您在选择 **“统计语义”** 前选择某一 **“语言”** ，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将被禁用。</span><span class="sxs-lookup"><span data-stu-id="e575e-126">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="e575e-127">如果你在选择“语言”前选择“统计语义”，则下拉组合框中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="e575e-127">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e575e-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e575e-128">See Also</span></span>  
 [<span data-ttu-id="e575e-129">“全文检索”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e575e-129">Full-Text Index Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
