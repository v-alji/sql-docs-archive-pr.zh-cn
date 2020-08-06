---
title: SSAS 表格)  (属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a59d3448-8619-4044-923b-8effba926dfa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d8c77ffbe8e185e15b716819498fe48295348e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683084"
---
# <a name="properties-ssas-tabular"></a><span data-ttu-id="5af4a-102">属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-102">Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="5af4a-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的表格模型项目具有不同的属性，这些属性定义项目、模型、报告和部署的行为。</span><span class="sxs-lookup"><span data-stu-id="5af4a-103">Tabular model projects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] have various properties that define behaviors for the project, model, reporting, and deployment.</span></span> <span data-ttu-id="5af4a-104">属性设置以 XML 格式存储于 Model.bim 文件中，但是，本节中描述的所有属性都可以在 **的** “属性” [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]窗口中配置。</span><span class="sxs-lookup"><span data-stu-id="5af4a-104">Property settings are stored in XML format in the Model.bim file, however, all of the properties described in this section can be configured in the **Properties** windows in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5af4a-105">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5af4a-105">Related Tasks</span></span>  
  
|<span data-ttu-id="5af4a-106">主题</span><span class="sxs-lookup"><span data-stu-id="5af4a-106">Topic</span></span>|<span data-ttu-id="5af4a-107">说明</span><span class="sxs-lookup"><span data-stu-id="5af4a-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5af4a-108">Power View 报表属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-108">Power View Reporting Properties &#40;SSAS Tabular&#41;</span></span>](power-view-reporting-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-109">本节中的主题提供用于将连接到 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]和从其进行浏览的表格模型的说明和配置选项。</span><span class="sxs-lookup"><span data-stu-id="5af4a-109">Topics in this section provide descriptions and configuration options for tabular models that will be connected to and browsed from [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>|  
|[<span data-ttu-id="5af4a-110">项目属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-110">Project Properties &#40;SSAS Tabular&#41;</span></span>](project-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-111">提供有关项目属性的说明。</span><span class="sxs-lookup"><span data-stu-id="5af4a-111">Provides descriptions for project properties.</span></span> <span data-ttu-id="5af4a-112">项目属性包括项目文件和部署选项设置。</span><span class="sxs-lookup"><span data-stu-id="5af4a-112">Project properties include project file and deployment options settings.</span></span>|  
|[<span data-ttu-id="5af4a-113">模型属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-113">Model Properties &#40;SSAS Tabular&#41;</span></span>](model-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-114">提供有关模型属性的说明。</span><span class="sxs-lookup"><span data-stu-id="5af4a-114">Provides descriptions for model properties.</span></span> <span data-ttu-id="5af4a-115">模型属性将会在模型创作过程中影响模型项目的生成操作、备份和工作区数据库。</span><span class="sxs-lookup"><span data-stu-id="5af4a-115">Model properties affect the model project's build actions, backup, and workspace database during model authoring.</span></span>|  
|[<span data-ttu-id="5af4a-116">表属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-116">Table Properties &#40;SSAS Tabular&#41;</span></span>](table-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-117">提供有关基本表属性的说明。</span><span class="sxs-lookup"><span data-stu-id="5af4a-117">Provides descriptions for basic table properties.</span></span> <span data-ttu-id="5af4a-118">此处所述的表属性不同于“编辑表属性”对话框中的那些属性，后者可以显示并允许从源选择和筛选列。</span><span class="sxs-lookup"><span data-stu-id="5af4a-118">Table properties described here are different from those in the Edit Table Properties dialog box, which display and allow selection and filtering of columns from the source,</span></span>|  
|[<span data-ttu-id="5af4a-119">列属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-119">Column Properties &#40;SSAS Tabular&#41;</span></span>](column-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-120">提供有关列属性的说明。</span><span class="sxs-lookup"><span data-stu-id="5af4a-120">Provides descriptions for column properties.</span></span> <span data-ttu-id="5af4a-121">列属性定义了列的数据类型、格式和隐藏设置。</span><span class="sxs-lookup"><span data-stu-id="5af4a-121">Column properties define a column's data type, format, and hiding settings.</span></span>|  
|[<span data-ttu-id="5af4a-122">配置默认数据建模和部署属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="5af4a-122">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)|<span data-ttu-id="5af4a-123">提供有关默认建模和部署属性的说明和配置步骤。</span><span class="sxs-lookup"><span data-stu-id="5af4a-123">Provides descriptions and configuration steps for default modeling and deployment properties.</span></span> <span data-ttu-id="5af4a-124">默认属性将应用于新的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="5af4a-124">Default properties apply to new tabular model projects.</span></span> <span data-ttu-id="5af4a-125">在创建新项目之后，根据您的需求，可为特定模型项目更改这些属性。</span><span class="sxs-lookup"><span data-stu-id="5af4a-125">After a project is created, these properties can be changed for a particular model project depending on your requirements.</span></span>|  
  
  
