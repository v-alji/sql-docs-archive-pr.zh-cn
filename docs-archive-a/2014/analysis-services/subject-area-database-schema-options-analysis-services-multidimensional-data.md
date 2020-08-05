---
title: 主题区域数据库架构选项 (架构生成向导)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98460332478d02de823addcd113fb9c1e87d6958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580910"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="aa530-102">主题区域数据库架构选项（架构生成向导）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="aa530-102">Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="aa530-103">可以使用 **“主题区域数据库架构选项”** 页，控制如何生成架构以及定义如何保留数据。</span><span class="sxs-lookup"><span data-stu-id="aa530-103">Use the **Subject Area Database Schema Options** page to control how the schema is generated, as well as to define how data is preserved.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aa530-104">选项</span><span class="sxs-lookup"><span data-stu-id="aa530-104">Options</span></span>  
 <span data-ttu-id="aa530-105">**所属架构**</span><span class="sxs-lookup"><span data-stu-id="aa530-105">**Owning schema**</span></span>  
 <span data-ttu-id="aa530-106">指定新主题区域数据库中的架构的名称。</span><span class="sxs-lookup"><span data-stu-id="aa530-106">Specifies the name of the schema within the new subject area database.</span></span>  
  
 <span data-ttu-id="aa530-107">**创建维度表的主键**</span><span class="sxs-lookup"><span data-stu-id="aa530-107">**Create primary keys on dimension tables**</span></span>  
 <span data-ttu-id="aa530-108">在生成的架构中为维度表创建主键。</span><span class="sxs-lookup"><span data-stu-id="aa530-108">Creates primary keys on the dimension tables in the generated schema.</span></span> <span data-ttu-id="aa530-109">如果不选择此选项，则不会生成任何索引。</span><span class="sxs-lookup"><span data-stu-id="aa530-109">No index is generated if you do not select this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa530-110">如果不选择此选项，将强制引用完整性。</span><span class="sxs-lookup"><span data-stu-id="aa530-110">If you do not select this option, referential integrity is enforced.</span></span>  
  
 <span data-ttu-id="aa530-111">**创建索引**</span><span class="sxs-lookup"><span data-stu-id="aa530-111">**Create indexes**</span></span>  
 <span data-ttu-id="aa530-112">在生成的架构中为外键列创建索引。</span><span class="sxs-lookup"><span data-stu-id="aa530-112">Creates indexes on foreign key columns in the generated schema.</span></span>  
  
 <span data-ttu-id="aa530-113">**强制引用完整性**</span><span class="sxs-lookup"><span data-stu-id="aa530-113">**Enforce referential integrity**</span></span>  
 <span data-ttu-id="aa530-114">在生成的架构中强制引用完整性。</span><span class="sxs-lookup"><span data-stu-id="aa530-114">Enforces referential integrity within the generated schema.</span></span> <span data-ttu-id="aa530-115">如果不选择此选项，将创建关系但不会强制执行。</span><span class="sxs-lookup"><span data-stu-id="aa530-115">If you do not select this option, relationships are created but not enforced.</span></span>  
  
 <span data-ttu-id="aa530-116">**重新生成时保留数据**</span><span class="sxs-lookup"><span data-stu-id="aa530-116">**Preserve data on regeneration**</span></span>  
 <span data-ttu-id="aa530-117">向导完成时，在主题区域数据库中保留数据。</span><span class="sxs-lookup"><span data-stu-id="aa530-117">Retains data in the subject area database when the wizard finishes.</span></span> <span data-ttu-id="aa530-118">如果不选择此选项，则可能在无警告的情况下清除主题区域数据库中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="aa530-118">If you do not select this option, all the data in the subject area database may be erased without warning.</span></span>  
  
 <span data-ttu-id="aa530-119">**填充时间表**</span><span class="sxs-lookup"><span data-stu-id="aa530-119">**Populate time table(s)**</span></span>  
 <span data-ttu-id="aa530-120">指定向导如何填充时间表。</span><span class="sxs-lookup"><span data-stu-id="aa530-120">Specifies how the wizard populates the time tables.</span></span> <span data-ttu-id="aa530-121">下表对此选项的可能值进行了说明：</span><span class="sxs-lookup"><span data-stu-id="aa530-121">The following table describes the possible values for this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa530-122">只有在项目模式下使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 从 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 项目调用架构生成向导时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="aa530-122">This option is enabled only if Schema Generation Wizard is called from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in project mode.</span></span>  
  
|<span data-ttu-id="aa530-123">值</span><span class="sxs-lookup"><span data-stu-id="aa530-123">Value</span></span>|<span data-ttu-id="aa530-124">说明</span><span class="sxs-lookup"><span data-stu-id="aa530-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa530-125">填充</span><span class="sxs-lookup"><span data-stu-id="aa530-125">Populate</span></span>|<span data-ttu-id="aa530-126">填充主题区域时间表。</span><span class="sxs-lookup"><span data-stu-id="aa530-126">The subject area time tables are populated.</span></span>|  
|<span data-ttu-id="aa530-127">不填充</span><span class="sxs-lookup"><span data-stu-id="aa530-127">Do not populate</span></span>|<span data-ttu-id="aa530-128">不填充主题区域时间表。</span><span class="sxs-lookup"><span data-stu-id="aa530-128">The subject area time tables are not populated.</span></span>|  
|<span data-ttu-id="aa530-129">为空时才填充</span><span class="sxs-lookup"><span data-stu-id="aa530-129">Populate only if empty</span></span>|<span data-ttu-id="aa530-130">只有当主题区域时间表为空时才进行填充。</span><span class="sxs-lookup"><span data-stu-id="aa530-130">The subject area time tables are populated only if they are empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa530-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa530-131">See Also</span></span>  
 [<span data-ttu-id="aa530-132">架构生成向导的 F1 帮助 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="aa530-132">Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;</span></span>](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
