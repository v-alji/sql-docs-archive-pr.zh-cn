---
title: " (商业智能向导) 配置维度属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d2e9bc83b7a6d83b6d2808b472d67169266ff07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579238"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a><span data-ttu-id="f08b3-102">配置维度属性（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="f08b3-102">Configure Dimension Attributes (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="f08b3-103">可以使用 **“配置维度属性”** 页，将维度属性映射到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用于标识帐户维度属性的属性类型。</span><span class="sxs-lookup"><span data-stu-id="f08b3-103">Use the **Configure Dimension Attributes** page to map the dimension attributes to the attribute types that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to identify attributes for account dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f08b3-104">选项</span><span class="sxs-lookup"><span data-stu-id="f08b3-104">Options</span></span>  
 <span data-ttu-id="f08b3-105">**维度类型**</span><span class="sxs-lookup"><span data-stu-id="f08b3-105">**Dimension type**</span></span>  
 <span data-ttu-id="f08b3-106">显示所选维度类型。</span><span class="sxs-lookup"><span data-stu-id="f08b3-106">Displays the selected dimension type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f08b3-107">此选项不可用，因为 `Type` 维度的属性不能更改为帐户维度的*帐户*之外的值。</span><span class="sxs-lookup"><span data-stu-id="f08b3-107">This option is not available because the `Type` property of the dimension cannot be changed to a value other than *Account* for account dimensions.</span></span>  
  
 <span data-ttu-id="f08b3-108">**“维度属性”**</span><span class="sxs-lookup"><span data-stu-id="f08b3-108">**Dimension attributes**</span></span>  
 <span data-ttu-id="f08b3-109">显示可以映射到维度中现有维度属性的有效属性类型。</span><span class="sxs-lookup"><span data-stu-id="f08b3-109">Displays the valid attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="f08b3-110">**包括**</span><span class="sxs-lookup"><span data-stu-id="f08b3-110">**Include**</span></span>  
 <span data-ttu-id="f08b3-111">选中复选框，将维度中相应的属性类型包括在内。</span><span class="sxs-lookup"><span data-stu-id="f08b3-111">Select a check box to include the corresponding attribute type in the dimension.</span></span>  
  
 <span data-ttu-id="f08b3-112">**特性类型**</span><span class="sxs-lookup"><span data-stu-id="f08b3-112">**Attribute Type**</span></span>  
 <span data-ttu-id="f08b3-113">列出可以映射到维度中现有维度属性的属性类型。</span><span class="sxs-lookup"><span data-stu-id="f08b3-113">Lists the attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="f08b3-114">**维度属性**</span><span class="sxs-lookup"><span data-stu-id="f08b3-114">**Dimension Attribute**</span></span>  
 <span data-ttu-id="f08b3-115">选择应该映射到相应属性类型的维度属性。</span><span class="sxs-lookup"><span data-stu-id="f08b3-115">Select the dimension attribute that should be mapped to the corresponding attribute type.</span></span>  
  
 <span data-ttu-id="f08b3-116">**基于帐户类型将度量值设置为半累加性**</span><span class="sxs-lookup"><span data-stu-id="f08b3-116">**Set measures to be semiadditive based on account type**</span></span>  
 <span data-ttu-id="f08b3-117">选中此选项，可以将与此维度相关联的每个度量值更改为按帐户类型聚合。</span><span class="sxs-lookup"><span data-stu-id="f08b3-117">Select to change every measure associated with this dimension to be aggregated by account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f08b3-118">如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，则将不会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="f08b3-118">This option does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08b3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f08b3-119">See Also</span></span>  
 <span data-ttu-id="f08b3-120">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f08b3-120">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="f08b3-121">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f08b3-121">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f08b3-122">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f08b3-122">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
