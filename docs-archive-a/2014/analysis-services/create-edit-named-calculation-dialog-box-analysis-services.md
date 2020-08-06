---
title: "\"创建-编辑命名计算\" 对话框 (Analysis Services) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b6777feb47a1ce6b601d0190e413b4baae35f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577099"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a><span data-ttu-id="7f9d8-102">"创建-编辑命名计算" 对话框 (Analysis Services) </span><span class="sxs-lookup"><span data-stu-id="7f9d8-102">Create-Edit Named Calculation Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="7f9d8-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“创建/编辑命名计算”\*\*\*\* 对话框，为数据源视图中的表定义或修改命名计算。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-103">Use the **Create/Edit Named Calculation** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a named calculation for a table in a data source view.</span></span> <span data-ttu-id="7f9d8-104">通过执行以下操作之一，可以显示“创建/编辑命名计算”\*\*\*\* 对话框：</span><span class="sxs-lookup"><span data-stu-id="7f9d8-104">You can display the **Create/Edit Named Calculation** dialog box by:</span></span>  
  
-   <span data-ttu-id="7f9d8-105">在“数据源视图设计器”\*\*\*\* 的“工具栏”\*\*\*\* 窗格中，单击“新建命名计算”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-105">Clicking **New Named Calculation** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="7f9d8-106">右键单击“数据源视图设计器”\*\*\*\* 的“表”\*\*\*\* 窗格或“关系图”\*\*\*\* 窗格中的表，再选择“新建命名计算”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Named Calculation**.</span></span>  
  
-   <span data-ttu-id="7f9d8-107">右键单击“数据源视图设计器”\*\*\*\* 的“关系图”\*\*\*\* 窗格中某命名计算的名称，再选择“编辑命名计算”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-107">Right-clicking the name of a named calculation in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Named Calculation**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f9d8-108">选项</span><span class="sxs-lookup"><span data-stu-id="7f9d8-108">Options</span></span>  
 <span data-ttu-id="7f9d8-109">**列名**</span><span class="sxs-lookup"><span data-stu-id="7f9d8-109">**Column Name**</span></span>  
 <span data-ttu-id="7f9d8-110">键入命名计算的名称。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-110">Type the name of the named calculation.</span></span>  
  
 <span data-ttu-id="7f9d8-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="7f9d8-111">**Description**</span></span>  
 <span data-ttu-id="7f9d8-112">键入命名计算的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-112">Type the optional description of the named calculation.</span></span>  
  
 <span data-ttu-id="7f9d8-113">**表达式**</span><span class="sxs-lookup"><span data-stu-id="7f9d8-113">**Expression**</span></span>  
 <span data-ttu-id="7f9d8-114">键入将返回标量值的有效的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="7f9d8-114">Type a valid SQL expression that returns a scalar value.</span></span> <span data-ttu-id="7f9d8-115">The expression is sent to the provider, and validated in the following expression:</span><span class="sxs-lookup"><span data-stu-id="7f9d8-115">The expression is sent to the provider, and validated in the following expression:</span></span>  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 <span data-ttu-id="7f9d8-116">The expression can contain references to other tables, by means of a sub-select statement.</span><span class="sxs-lookup"><span data-stu-id="7f9d8-116">The expression can contain references to other tables, by means of a sub-select statement.</span></span> <span data-ttu-id="7f9d8-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span><span class="sxs-lookup"><span data-stu-id="7f9d8-117">If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9d8-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f9d8-118">See Also</span></span>  
 <span data-ttu-id="7f9d8-119">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7f9d8-119">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7f9d8-120">数据源视图设计器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="7f9d8-120">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
