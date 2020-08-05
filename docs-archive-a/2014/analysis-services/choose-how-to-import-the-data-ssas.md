---
title: 选择如何 (SSAS) 导入数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.choosehowtoimpdata.f1
ms.assetid: 17dc6903-c239-46aa-a3b0-6e3156accacc
author: minewiskan
ms.author: owend
ms.openlocfilehash: fba1d5801f325400b228920fffa06512f4db8de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579894"
---
# <a name="choose-how-to-import-the-data-ssas"></a><span data-ttu-id="a2bb4-102">选择如何导入数据 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="a2bb4-102">Choose How to Import the Data (SSAS)</span></span>
  <span data-ttu-id="a2bb4-103">**“表导入向导”** 的这一页可用于选择从所选数据源导入数据的方式。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-103">This page of the **Table Import Wizard** enables you to choose how to import data from the selected data source.</span></span> <span data-ttu-id="a2bb4-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a2bb4-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a2bb4-105">UI element list</span></span>  
 <span data-ttu-id="a2bb4-106">**从表和视图的列表中进行选择，以便选择要导入的数据**</span><span class="sxs-lookup"><span data-stu-id="a2bb4-106">**Select from a list of tables and views to choose the data to import**</span></span>  
 <span data-ttu-id="a2bb4-107">如果要通过从列表中选择来导入数据，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-107">Select this option if you want to import data by selecting from a list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2bb4-108">仅当所选数据源公开“表导入向导”\*\*\*\* 支持的架构信息后，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-108">This option is available only when the selected data source exposes schema information that the **Table Import Wizard** supports.</span></span>  
  
 <span data-ttu-id="a2bb4-109">**编写一个查询以便指定要导入的数据**</span><span class="sxs-lookup"><span data-stu-id="a2bb4-109">**Write a query to specify the data to import**</span></span>  
 <span data-ttu-id="a2bb4-110">如果要使用 SQL 查询来导入数据，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-110">Select this option if you want to import data by using a SQL query.</span></span> <span data-ttu-id="a2bb4-111">SQL 查询可以处理导入的数据。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-111">The SQL query can manipulate the data that is imported.</span></span> <span data-ttu-id="a2bb4-112">例如，您可以联接来自不同表的数据，或仅选择符合特定条件的行。</span><span class="sxs-lookup"><span data-stu-id="a2bb4-112">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
  
