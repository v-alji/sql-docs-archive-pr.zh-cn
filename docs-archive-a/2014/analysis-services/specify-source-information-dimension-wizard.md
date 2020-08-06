---
title: " (维度向导) 指定源信息 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 99bbaac0bdf24a18dcde455e779f056b98106dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589247"
---
# <a name="specify-source-information-dimension-wizard"></a><span data-ttu-id="7fb9d-102">指定源信息（维度向导）</span><span class="sxs-lookup"><span data-stu-id="7fb9d-102">Specify Source Information (Dimension Wizard)</span></span>
  <span data-ttu-id="7fb9d-103">可以使用 **“选择主维度表”** 页，为要创建的维度选择数据源视图、主维度表、键列和成员名列。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-103">Use the **Select the Main Dimension Table** page to select the data source view, main dimension table, key columns, and member name column for the dimension to be created.</span></span>  
  
 <span data-ttu-id="7fb9d-104">**打开维度向导**</span><span class="sxs-lookup"><span data-stu-id="7fb9d-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="7fb9d-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的**解决方案资源管理器**中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目的“维度”文件夹，然后单击“新建维度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7fb9d-106">选项</span><span class="sxs-lookup"><span data-stu-id="7fb9d-106">Options</span></span>  
 <span data-ttu-id="7fb9d-107">**数据源视图**</span><span class="sxs-lookup"><span data-stu-id="7fb9d-107">**Data source view**</span></span>  
 <span data-ttu-id="7fb9d-108">选择数据源视图。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-108">Select a data source view.</span></span>  
  
 <span data-ttu-id="7fb9d-109">**主表**</span><span class="sxs-lookup"><span data-stu-id="7fb9d-109">**Main table**</span></span>  
 <span data-ttu-id="7fb9d-110">从所选数据源视图中选择一个表，用作维度的主表。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-110">Select a table from the selected data source view to use as the main table for the dimension.</span></span>  
  
 <span data-ttu-id="7fb9d-111">**键列**</span><span class="sxs-lookup"><span data-stu-id="7fb9d-111">**Key columns**</span></span>  
 <span data-ttu-id="7fb9d-112">从维度的键属性的“主表”指定的表中选择键列。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7fb9d-112">Select the key columns from the table specified in **Main table** for the key attribute of the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fb9d-113">您可以选择多列。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-113">More than one column can be selected.</span></span> <span data-ttu-id="7fb9d-114">如果该表包含组合主键，则选择组合主键中包含的所有列。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-114">If the table contains a composite primary key, select all the columns included in the composite primary key.</span></span> <span data-ttu-id="7fb9d-115">键列的顺序很重要。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-115">The order of the key columns is important.</span></span>  
  
 <span data-ttu-id="7fb9d-116">**名称列**</span><span class="sxs-lookup"><span data-stu-id="7fb9d-116">**Name column**</span></span>  
 <span data-ttu-id="7fb9d-117">从提供维度成员名称的“主表”指定的表中选择列。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7fb9d-117">Select the column from the table specified in **Main table** that provides the member names for the dimension.</span></span> <span data-ttu-id="7fb9d-118">使用组合键时，必须指定名称列。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-118">A name column must be specified when a composite key is used.</span></span> <span data-ttu-id="7fb9d-119">若要创建组合键的名称列，建议您在数据源视图中创建串联指定键列的命名计算。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-119">To create a name column for a composite key, we recommend that you create a named calculation in the data source view that concatenates the specified key columns.</span></span> <span data-ttu-id="7fb9d-120">使用单个键时，名称列是可选的。</span><span class="sxs-lookup"><span data-stu-id="7fb9d-120">When a single key is used, the name column is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb9d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fb9d-121">See Also</span></span>  
 <span data-ttu-id="7fb9d-122">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7fb9d-122">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="7fb9d-123">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7fb9d-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7fb9d-124">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="7fb9d-124">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
