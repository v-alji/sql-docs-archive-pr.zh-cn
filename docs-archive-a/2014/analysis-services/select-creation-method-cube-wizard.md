---
title: " (多维数据集向导) 选择创建方法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
author: minewiskan
ms.author: owend
ms.openlocfilehash: c8c4d611e00a2b3f5d115ea5749b1e494a44bf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589891"
---
# <a name="select-creation-method-cube-wizard"></a><span data-ttu-id="bb7b5-102">选择创建方法（多维数据集向导）</span><span class="sxs-lookup"><span data-stu-id="bb7b5-102">Select Creation Method (Cube Wizard)</span></span>
  <span data-ttu-id="bb7b5-103">可以使用 **“选择创建方法”** 页指定创建多维数据集的方式。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-103">Use the **Select Creation Method** page to specify how to create the cube.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bb7b5-104">选项</span><span class="sxs-lookup"><span data-stu-id="bb7b5-104">Options</span></span>  
 <span data-ttu-id="bb7b5-105">**使用现有表**</span><span class="sxs-lookup"><span data-stu-id="bb7b5-105">**Use existing tables**</span></span>  
 <span data-ttu-id="bb7b5-106">选择此选项可以通过使用数据源中的现有表创建多维数据集。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-106">Select to create a cube by using existing tables in a data source.</span></span> <span data-ttu-id="bb7b5-107">该向导将引导您完成基于现有表选择和定义度量值组和维度的整个过程，从而生成新多维数据集。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-107">The wizard will guide you through the process of selecting and defining measure groups and dimensions based on existing tables to build your new cube.</span></span>  
  
 <span data-ttu-id="bb7b5-108">**创建空的多维数据集**</span><span class="sxs-lookup"><span data-stu-id="bb7b5-108">**Create an empty cube**</span></span>  
 <span data-ttu-id="bb7b5-109">选择此选项可以创建空的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-109">Select to create an empty cube.</span></span> <span data-ttu-id="bb7b5-110">当要手动创建所有内容或者多维数据集中的所有度量值组都是链接度量值组时，此选项将非常有用。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-110">This option is useful when you want to create everything manually, or when all measure groups in the cube are linked measure groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb7b5-111">仅当您正处理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目时，此选项才可用；如果您直接连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-111">This option is only available when you are working with an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and not when you are connected directly to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="bb7b5-112">**在数据源中生成表**</span><span class="sxs-lookup"><span data-stu-id="bb7b5-112">**Generate tables in the data source**</span></span>  
 <span data-ttu-id="bb7b5-113">选择此选项可以首先创建一个多维数据集，然后可基于多维数据集定义在数据源中生成新表。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-113">Select to create a cube first and then generate new tables in the data source based on the cube definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb7b5-114">若要使用此选项，则您必须拥有在基础数据源中创建对象的权限。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-114">To use this option, you must have permission to create objects in the underlying data source.</span></span>  
  
 <span data-ttu-id="bb7b5-115">选择此选项后， **“模板”** 选项将可用。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-115">Selecting this option will make the **Template** option available.</span></span>  
  
 <span data-ttu-id="bb7b5-116">**模板**</span><span class="sxs-lookup"><span data-stu-id="bb7b5-116">**Template**</span></span>  
 <span data-ttu-id="bb7b5-117">选择要用于创建多维数据集的模板。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-117">Select the template that you want to use to create the cube.</span></span> <span data-ttu-id="bb7b5-118">模板可以提供一组面向特定业务用途的定义。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-118">Templates provide a set of definitions oriented towards a specific business purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb7b5-119">仅当选择了“在数据源中生成表”\*\*\*\* 选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bb7b5-119">This option is only available when the **Generate tables in the data source** option has been selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7b5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb7b5-120">See Also</span></span>  
 <span data-ttu-id="bb7b5-121">[多维数据集对象 &#40;Analysis Services 多维数据&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="bb7b5-121">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="bb7b5-122">[多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="bb7b5-122">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="bb7b5-123">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="bb7b5-123">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
