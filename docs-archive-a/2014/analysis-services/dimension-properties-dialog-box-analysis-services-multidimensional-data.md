---
title: "\"维度属性\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.dimensionproperties.f1
helpviewer_keywords:
- Dimension Properties dialog box
ms.assetid: 7235d443-b2ce-4c53-b2eb-abceb28394bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0523220c76c11280165bc825c5c00c5eb9e23be6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591637"
---
# <a name="dimension-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="fd182-102">“维度属性”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fd182-102">Dimension Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fd182-103">可以使用 **中的** “维度属性” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的维度的属性。</span><span class="sxs-lookup"><span data-stu-id="fd182-103">Use the **Dimension Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a dimension in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="fd182-104">在对象资源管理器中右键单击某个维度，并选择“属性”，可以显示“维度属性”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd182-104">You can display the **Dimension Properties** dialog box by right-clicking a dimension in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fd182-105">选项</span><span class="sxs-lookup"><span data-stu-id="fd182-105">Options</span></span>  
  
|<span data-ttu-id="fd182-106">术语</span><span class="sxs-lookup"><span data-stu-id="fd182-106">Term</span></span>|<span data-ttu-id="fd182-107">定义</span><span class="sxs-lookup"><span data-stu-id="fd182-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="fd182-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="fd182-108">**Name**</span></span>|<span data-ttu-id="fd182-109">显示维度的名称。</span><span class="sxs-lookup"><span data-stu-id="fd182-109">Displays the name of the dimension.</span></span>|  
|<span data-ttu-id="fd182-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="fd182-110">**ID**</span></span>|<span data-ttu-id="fd182-111">显示维度的标识符。</span><span class="sxs-lookup"><span data-stu-id="fd182-111">Displays the identifier of the dimension.</span></span>|  
|<span data-ttu-id="fd182-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="fd182-112">**Description**</span></span>|<span data-ttu-id="fd182-113">显示维度的说明。</span><span class="sxs-lookup"><span data-stu-id="fd182-113">Displays the description of the dimension.</span></span>|  
|<span data-ttu-id="fd182-114">**创建时间戳**</span><span class="sxs-lookup"><span data-stu-id="fd182-114">**Create Timestamp**</span></span>|<span data-ttu-id="fd182-115">显示维度的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fd182-115">Displays the date and time the dimension was created.</span></span>|  
|<span data-ttu-id="fd182-116">**上次架构更新时间**</span><span class="sxs-lookup"><span data-stu-id="fd182-116">**Last Schema Update**</span></span>|<span data-ttu-id="fd182-117">显示上次更新维度元数据的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fd182-117">Displays the date and time the metadata for the dimension was last updated.</span></span>|  
|<span data-ttu-id="fd182-118">**处理模式**</span><span class="sxs-lookup"><span data-stu-id="fd182-118">**Processing Mode**</span></span>|<span data-ttu-id="fd182-119">选择维度要使用的处理模式。</span><span class="sxs-lookup"><span data-stu-id="fd182-119">Select the processing mode to use for the dimension.</span></span> <span data-ttu-id="fd182-120">有关此属性的值的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd182-120">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.ProcessingMode%2A>.</span></span>|  
|<span data-ttu-id="fd182-121">**State**</span><span class="sxs-lookup"><span data-stu-id="fd182-121">**State**</span></span>|<span data-ttu-id="fd182-122">显示维度的处理状态。</span><span class="sxs-lookup"><span data-stu-id="fd182-122">Displays the processing state of the dimension.</span></span> <span data-ttu-id="fd182-123">有关此属性的值的详细信息，请参阅 <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd182-123">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="fd182-124">**上次处理时间**</span><span class="sxs-lookup"><span data-stu-id="fd182-124">**Last Processed**</span></span>|<span data-ttu-id="fd182-125">显示上次处理维度的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fd182-125">Displays the date and time the dimension was last processed.</span></span>|  
|<span data-ttu-id="fd182-126">**当前存储模式**</span><span class="sxs-lookup"><span data-stu-id="fd182-126">**Current Storage Mode**</span></span>|<span data-ttu-id="fd182-127">显示维度的当前存储模式。</span><span class="sxs-lookup"><span data-stu-id="fd182-127">Displays the current storage mode for the dimension.</span></span> <span data-ttu-id="fd182-128">有关此属性的值的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd182-128">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.Dimension.CurrentStorageMode%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd182-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd182-129">See Also</span></span>  
 <span data-ttu-id="fd182-130">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fd182-130">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fd182-131">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="fd182-131">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
