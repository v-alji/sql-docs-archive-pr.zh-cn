---
title: " (维度向导) 选择创建方法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensiondefinition.f1
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6338a0bde7865482fb7a98d7ec36ba5a71feb806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687255"
---
# <a name="select-creation-method-dimension-wizard"></a><span data-ttu-id="f6a04-102">选择创建方法（维度向导）</span><span class="sxs-lookup"><span data-stu-id="f6a04-102">Select Creation Method (Dimension Wizard)</span></span>
  <span data-ttu-id="f6a04-103">可以使用 **“选择创建方法”** 页选择如何创建维度。</span><span class="sxs-lookup"><span data-stu-id="f6a04-103">Use the **Select Creation Method** page to select how to create the dimension.</span></span>  
  
 <span data-ttu-id="f6a04-104">**打开维度向导**</span><span class="sxs-lookup"><span data-stu-id="f6a04-104">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="f6a04-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的**解决方案资源管理器**中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目的“维度”文件夹，然后单击“新建维度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6a04-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f6a04-106">选项</span><span class="sxs-lookup"><span data-stu-id="f6a04-106">Options</span></span>  
 <span data-ttu-id="f6a04-107">**使用现有表**</span><span class="sxs-lookup"><span data-stu-id="f6a04-107">**Use an existing table**</span></span>  
 <span data-ttu-id="f6a04-108">从数据源中的一个或多个表创建维度。</span><span class="sxs-lookup"><span data-stu-id="f6a04-108">Create a dimension from one or more tables in a data source.</span></span> <span data-ttu-id="f6a04-109">可用于该维度的属性取决于表中数据的结构。</span><span class="sxs-lookup"><span data-stu-id="f6a04-109">The attributes that are available for the dimension will depend on the structure of the data in the table.</span></span>  
  
 <span data-ttu-id="f6a04-110">有关详细信息，请参阅 [使用现有表创建维度](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a04-110">For more information, see [Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md).</span></span>  
  
 <span data-ttu-id="f6a04-111">**在数据源中生成时间表**</span><span class="sxs-lookup"><span data-stu-id="f6a04-111">**Generate a time table in the data source**</span></span>  
 <span data-ttu-id="f6a04-112">在基础数据源中创建时间表，然后使用该表创建时间维度。</span><span class="sxs-lookup"><span data-stu-id="f6a04-112">Create a time table in the underlying data source and then use that table to create a time dimension.</span></span> <span data-ttu-id="f6a04-113">不存在这类表，并且不想使用脚本创建表时，可使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f6a04-113">Use this option when no such table exists and you do not want to use a script to create one.</span></span> <span data-ttu-id="f6a04-114">新的时间表将包含日期范围数据、属性和在向导中指定的日历。</span><span class="sxs-lookup"><span data-stu-id="f6a04-114">The new time table will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6a04-115">若要使用此选项，则您必须拥有在基础数据源中创建对象的权限。</span><span class="sxs-lookup"><span data-stu-id="f6a04-115">To use this option, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="f6a04-116">如果没有在数据源中创建对象的权限，可以尝试改用 **“在服务器上生成时间表”** 选项。</span><span class="sxs-lookup"><span data-stu-id="f6a04-116">If you do not have permission to create objects on the data source, try to use the **Generate a time table on the server** option instead.</span></span>  
  
 <span data-ttu-id="f6a04-117">有关详细信息，请参阅 [通过生成时间表来创建时间维度](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a04-117">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="f6a04-118">**“在服务器上生成时间表”**</span><span class="sxs-lookup"><span data-stu-id="f6a04-118">**Generate a time table on the server**</span></span>  
 <span data-ttu-id="f6a04-119">在服务器上直接创建时间表，然后使用该表创建时间维度。</span><span class="sxs-lookup"><span data-stu-id="f6a04-119">Create a time table directly on the server and then use that table to create a time dimension.</span></span> <span data-ttu-id="f6a04-120">如果没有在基础源数据中创建对象的权限，可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="f6a04-120">Use this option if you do not have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="f6a04-121">新的时间维度将包含日期范围数据、属性和在向导中指定的日历。</span><span class="sxs-lookup"><span data-stu-id="f6a04-121">The new time dimension will contain data for the date range, attributes, and calendars that you specify in the wizard.</span></span>  
  
 <span data-ttu-id="f6a04-122">有关详细信息，请参阅 [通过生成时间表来创建时间维度](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a04-122">For more information, see [Create a Time Dimension by Generating a Time Table](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
 <span data-ttu-id="f6a04-123">**在数据源中生成非时间表**</span><span class="sxs-lookup"><span data-stu-id="f6a04-123">**Generate a non-time table in the data source**</span></span>  
 <span data-ttu-id="f6a04-124">在没有基础关系数据源的情况下设计维度，然后为数据源生成必要的架构。</span><span class="sxs-lookup"><span data-stu-id="f6a04-124">Design the dimension without an underlying relational data source, and then generate the necessary schema for the data source.</span></span> <span data-ttu-id="f6a04-125">这种方法称为自上而下的建模。</span><span class="sxs-lookup"><span data-stu-id="f6a04-125">This approach is known as top-down modeling.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6a04-126">若要使用此选项，则您必须拥有在基础数据源中创建对象的权限。</span><span class="sxs-lookup"><span data-stu-id="f6a04-126">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="f6a04-127">生成维度可以使用模板，也可以不使用模板。</span><span class="sxs-lookup"><span data-stu-id="f6a04-127">You can build the dimension with or without a template.</span></span> <span data-ttu-id="f6a04-128">若要使用模板生成维度，请从 **“模板”** 列表中选择模板。</span><span class="sxs-lookup"><span data-stu-id="f6a04-128">To build the dimension with a template, select the template from the **Template** list.</span></span>  
  
 <span data-ttu-id="f6a04-129">有关详细信息，请参阅 [通过在数据源中生成非时间表来创建维度](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a04-129">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md).</span></span>  
  
 <span data-ttu-id="f6a04-130">**模板**</span><span class="sxs-lookup"><span data-stu-id="f6a04-130">**Template**</span></span>  
 <span data-ttu-id="f6a04-131">选择要用于创建维度的模板。</span><span class="sxs-lookup"><span data-stu-id="f6a04-131">Select the template that you want to use to create the dimension.</span></span> <span data-ttu-id="f6a04-132">模板提供面向特定商业用途的一组完整的属性和层次结构定义。</span><span class="sxs-lookup"><span data-stu-id="f6a04-132">Templates provide a complete set of attribute and hierarchy definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6a04-133">仅当选择了“在数据源中生成非时间表”\*\*\*\* 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="f6a04-133">This option is only available when the **Generate a non-time table in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a04-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6a04-134">See Also</span></span>  
 <span data-ttu-id="f6a04-135">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f6a04-135">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="f6a04-136">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f6a04-136">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f6a04-137">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="f6a04-137">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
