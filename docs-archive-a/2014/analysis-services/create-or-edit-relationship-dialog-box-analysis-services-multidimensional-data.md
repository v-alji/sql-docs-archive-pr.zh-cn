---
title: "\"创建或编辑关系\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580471"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="74bf4-102">“创建或编辑关系”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="74bf4-102">Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="74bf4-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“创建/编辑关系”\*\*\*\* 对话框，定义或修改数据源视图中的关系。</span><span class="sxs-lookup"><span data-stu-id="74bf4-103">Use the **Create/Edit Relationship** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a relationship in a data source view.</span></span> <span data-ttu-id="74bf4-104">通过执行以下操作之一，可以显示“创建/编辑关系”对话框\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="74bf4-104">You can display the **Create/Edit Relationship** dialog box by:</span></span>  
  
-   <span data-ttu-id="74bf4-105">在 **数据源视图设计器** 的 **“工具栏”** 窗格中，单击 **“新建关系”**。</span><span class="sxs-lookup"><span data-stu-id="74bf4-105">Clicking **New Relationship** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="74bf4-106">右键单击**数据源视图设计器**的“表”\*\*\*\* 窗格或“关系图”\*\*\*\* 窗格中的表，再选择“新建关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74bf4-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Relationship**.</span></span>  
  
-   <span data-ttu-id="74bf4-107">右键单击**数据源视图设计器**的“关系图”\*\*\*\* 窗格中的关系，再选择“编辑关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74bf4-107">Right-clicking a relationship in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Relationship**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74bf4-108"> 可以在 **数据源视图设计器** 中创建基础数据源中不存在的关系，并从基础数据源中的现有外键关系中删除通过 **数据源视图设计器** 创建的关系。</span><span class="sxs-lookup"><span data-stu-id="74bf4-108">You can create relationships in **Data Source View Designer** that do not exist in the underlying data source, and remove relationships created by **Data Source View Designer** from existing foreign key relationships in the underlying data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="74bf4-109">选项</span><span class="sxs-lookup"><span data-stu-id="74bf4-109">Options</span></span>  
 <span data-ttu-id="74bf4-110">**源(外键)表**</span><span class="sxs-lookup"><span data-stu-id="74bf4-110">**Source (foreign key) table**</span></span>  
 <span data-ttu-id="74bf4-111">选择包含对目标表中一个或多个列的引用的表或命名查询。</span><span class="sxs-lookup"><span data-stu-id="74bf4-111">Select the table or named query that contains the reference to one or more columns in the destination table.</span></span>  
  
 <span data-ttu-id="74bf4-112">**目标(主键)表**</span><span class="sxs-lookup"><span data-stu-id="74bf4-112">**Destination (primary key) table**</span></span>  
 <span data-ttu-id="74bf4-113">选择包含源表所引用的一个或多个列的表。</span><span class="sxs-lookup"><span data-stu-id="74bf4-113">Select the table that contains one or more columns referenced by the source table.</span></span> <span data-ttu-id="74bf4-114">对于自联接，请选择在“源(外键)表”\*\*\*\* 中选择的同一个表。</span><span class="sxs-lookup"><span data-stu-id="74bf4-114">For self-joins, select the same table selected in **Source (foreign key) table**.</span></span>  
  
 <span data-ttu-id="74bf4-115">**源列**</span><span class="sxs-lookup"><span data-stu-id="74bf4-115">**Source columns**</span></span>  
 <span data-ttu-id="74bf4-116">选择引用目标表中的列的列。</span><span class="sxs-lookup"><span data-stu-id="74bf4-116">Select the columns that reference columns in the destination table.</span></span>  
  
 <span data-ttu-id="74bf4-117">**目标列**</span><span class="sxs-lookup"><span data-stu-id="74bf4-117">**Destination columns**</span></span>  
 <span data-ttu-id="74bf4-118">选择被源表中的列引用的列。</span><span class="sxs-lookup"><span data-stu-id="74bf4-118">Select the columns that are referenced by columns in the source table.</span></span>  
  
 <span data-ttu-id="74bf4-119">**反向**</span><span class="sxs-lookup"><span data-stu-id="74bf4-119">**Reverse**</span></span>  
 <span data-ttu-id="74bf4-120">单击此项可以使关系方向变为相反方向。</span><span class="sxs-lookup"><span data-stu-id="74bf4-120">Click to reverse the direction of the relationship.</span></span>  
  
 <span data-ttu-id="74bf4-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="74bf4-121">**Description**</span></span>  
 <span data-ttu-id="74bf4-122">键入关系的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="74bf4-122">Type an optional description for the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bf4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74bf4-123">See Also</span></span>  
 <span data-ttu-id="74bf4-124">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="74bf4-124">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="74bf4-125">数据源视图设计器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="74bf4-125">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
