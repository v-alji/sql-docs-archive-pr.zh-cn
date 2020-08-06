---
title: 浏览数据源视图中的数据 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591606"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a><span data-ttu-id="04e72-102">在数据源视图中浏览数据 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="04e72-102">Explore Data in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="04e72-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的数据源视图设计器中的“浏览数据”\*\*\*\* 对话框，在数据源视图 (DSV) 中浏览表、视图或命名查询的数据。</span><span class="sxs-lookup"><span data-stu-id="04e72-103">You can use the **Explore Data** dialog box in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to browse data for a table, view, or named query in a data source view (DSV).</span></span> <span data-ttu-id="04e72-104">在数据源视图设计器中浏览数据时，可以查看所选表、视图或命名查询中每个数据列的内容。</span><span class="sxs-lookup"><span data-stu-id="04e72-104">When you explore the data in Data Source View Designer, you can view the contents of each column of data in a selected table, view, or named query.</span></span> <span data-ttu-id="04e72-105">查看实际内容将帮助您确定是否需要所有列，是否需要命名计算来提高用户友好性和可用性，以及现有命名计算或命名查询是否返回预期值。</span><span class="sxs-lookup"><span data-stu-id="04e72-105">Viewing the actual contents assists you in determining whether all columns are needed, if named calculations are required to increase user friendliness and usability, and whether existing named calculations or named queries return the anticipated values.</span></span>  
  
 <span data-ttu-id="04e72-106">若要查看数据，必须与 DSV 中所选对象的一个或多个数据源建立活动连接。</span><span class="sxs-lookup"><span data-stu-id="04e72-106">To view data, you must have an active connection to the data source or sources for the selected object in the DSV.</span></span> <span data-ttu-id="04e72-107">此外，还在该查询中发送表中的任何命名计算。</span><span class="sxs-lookup"><span data-stu-id="04e72-107">Any named calculations in a table are also sent in the query.</span></span>  
  
 <span data-ttu-id="04e72-108">您可以对以表格格式返回的数据进行排序和复制。</span><span class="sxs-lookup"><span data-stu-id="04e72-108">The data returned in a tabular format that you can sort and copy.</span></span> <span data-ttu-id="04e72-109">单击列标题可以按该列对行进行重新排序。</span><span class="sxs-lookup"><span data-stu-id="04e72-109">Click on the column headers to re-sort the rows by that column.</span></span> <span data-ttu-id="04e72-110">也可以突出显示网格中的数据，然后按下 Ctrl-C 以便将选定内容复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="04e72-110">You can also highlight data in the grid and press Ctrl-C to copy the selection to the clipboard.</span></span>  
  
 <span data-ttu-id="04e72-111">还可以控制抽样方法和抽样计数。</span><span class="sxs-lookup"><span data-stu-id="04e72-111">You can also control the sample method and the sample count.</span></span> <span data-ttu-id="04e72-112">默认情况下，将返回前 5000 行。</span><span class="sxs-lookup"><span data-stu-id="04e72-112">By default, the top 5000 rows are returned.</span></span>  
  
## <a name="to-browse-data-or-change-sampling-options"></a><span data-ttu-id="04e72-113">浏览数据或更改抽样选项</span><span class="sxs-lookup"><span data-stu-id="04e72-113">To browse data or change sampling options</span></span>  
  
1.  <span data-ttu-id="04e72-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中浏览数据的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="04e72-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to browse data.</span></span>  
  
2.  <span data-ttu-id="04e72-115">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="04e72-115">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="04e72-116">右键单击包含要查看的数据的表、视图或命名查询，再单击“浏览数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04e72-116">Right-click the table, view, or named query that contains the data you want to view, and then click **Explore Data**.</span></span>  
  
     <span data-ttu-id="04e72-117">数据源视图中表、视图或命名查询的基础数据源是查询，结果显示在 "**浏览 \<object name> 表**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="04e72-117">The data source underlying the table, view, or named query in the data source view are queries, and the results appear in the **Explore \<object name> Table** tab.</span></span>  
  
4.  <span data-ttu-id="04e72-118">在 "**浏览 \<object name> 表**" 工具栏上，单击 "**抽样选项**" 图标。</span><span class="sxs-lookup"><span data-stu-id="04e72-118">On the **Explore \<object name> Table** toolbar, click the **Sampling options** icon.</span></span>  
  
     <span data-ttu-id="04e72-119">此时将打开 **“数据浏览选项”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="04e72-119">The **Data Exploration Options** dialog box opens.</span></span> <span data-ttu-id="04e72-120">在该对话框中可以指定抽样方法（记录少于或多于默认抽样大小 5000 行）或抽样计数。</span><span class="sxs-lookup"><span data-stu-id="04e72-120">In this dialog box you can specify the sampling method (fewer or more records than the default sampling size of 5000 rows), or sample count.</span></span>  
  
5.  <span data-ttu-id="04e72-121">根据需要单击 **“确定”** 或 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="04e72-121">Click **OK** or **Cancel** as appropriate.</span></span>  
  
6.  <span data-ttu-id="04e72-122">若要对数据重新抽样，请单击 "**浏览 \<object name> 表**" 工具栏上的 "对**数据重新取样**"</span><span class="sxs-lookup"><span data-stu-id="04e72-122">To resample the data, click **Resample Data** on the **Explore \<object name> Table** toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e72-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04e72-123">See Also</span></span>  
 [<span data-ttu-id="04e72-124">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="04e72-124">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
