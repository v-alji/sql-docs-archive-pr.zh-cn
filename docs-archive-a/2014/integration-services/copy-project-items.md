---
title: 复制项目项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587534"
---
# <a name="copy-project-items"></a><span data-ttu-id="87cdd-102">复制项目项</span><span class="sxs-lookup"><span data-stu-id="87cdd-102">Copy Project Items</span></span>
  <span data-ttu-id="87cdd-103">本主题说明如何在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目内或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目之间复制对象。</span><span class="sxs-lookup"><span data-stu-id="87cdd-103">This topic describes how to copy objects within an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="87cdd-104">您还可以在其他类型的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 项目（ [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]）之间复制对象。</span><span class="sxs-lookup"><span data-stu-id="87cdd-104">You can also copy objects between the other types of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] projects, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="87cdd-105">若要在项目之间进行复制，则项目必须是同一个 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 解决方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="87cdd-105">To copy between projects, the project must be part of the same [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] solution.</span></span> <span data-ttu-id="87cdd-106">有关详细信息，请参阅 [Integration Services (SSIS) 项目](integration-services-ssis-projects-and-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="87cdd-106">For more information, see [Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md).</span></span>  
  
### <a name="to-copy-project-level-items"></a><span data-ttu-id="87cdd-107">复制项目级别的项</span><span class="sxs-lookup"><span data-stu-id="87cdd-107">To copy project level items</span></span>  
  
1.  <span data-ttu-id="87cdd-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开希望处理的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目或解决方案。</span><span class="sxs-lookup"><span data-stu-id="87cdd-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or solution that you want to work with.</span></span>  
  
2.  <span data-ttu-id="87cdd-109">展开要从中复制对象的项目和项文件夹。</span><span class="sxs-lookup"><span data-stu-id="87cdd-109">Expand the project and item folder to copy from.</span></span>  
  
3.  <span data-ttu-id="87cdd-110">右键单击该项，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87cdd-110">Right-click the item and click **Copy**.</span></span>  
  
4.  <span data-ttu-id="87cdd-111">右键单击要复制到其中的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，然后单击“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87cdd-111">Right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to copy to and click **Paste**.</span></span>  
  
     <span data-ttu-id="87cdd-112">这些项会自动复制到正确的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="87cdd-112">The items are automatically copied to the correct folder.</span></span> <span data-ttu-id="87cdd-113">如果将项复制到不是包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中，则该项将复制到 **“杂项”** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="87cdd-113">If you copy items to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that are not packages, the items are copied to the **Miscellaneous** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cdd-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87cdd-114">See Also</span></span>  
 <span data-ttu-id="87cdd-115">[Integration Services &#40;SSIS&#41; 包](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="87cdd-115">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="87cdd-116">复制包对象</span><span class="sxs-lookup"><span data-stu-id="87cdd-116">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
  
