---
title: Analysis Services 多维数据)  (的 "影响分析" 对话框 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e47ab806b9bd10afc812113b69fe0849437068b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687331"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="7f59e-102">“影响分析”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="7f59e-102">Impact Analysis Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7f59e-103">如果 **“处理”** 对话框中列出的对象已处理，则使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 **“影响分析”** 对话框来标识和处理受影响的依赖对象。</span><span class="sxs-lookup"><span data-stu-id="7f59e-103">Use the **Impact Analysis** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to identify and optionally process dependent objects that are affected if the objects listed in the **Process** dialog box are processed.</span></span> <span data-ttu-id="7f59e-104">通过在 **“处理”** 对话框中单击 **“影响分析”** ，可以显示 **“影响分析”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="7f59e-104">You can display the **Impact Analysis** dialog box by clicking **Impact Analysis** from the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f59e-105">如果某个对象在多个方面受到影响，则该对象将显示多次。</span><span class="sxs-lookup"><span data-stu-id="7f59e-105">An object appears more than once if it is affected in more than one way.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f59e-106">选项</span><span class="sxs-lookup"><span data-stu-id="7f59e-106">Options</span></span>  
 <span data-ttu-id="7f59e-107">**对象列表**</span><span class="sxs-lookup"><span data-stu-id="7f59e-107">**Object list**</span></span>  
 <span data-ttu-id="7f59e-108">在网格中显示依赖对象的列表。</span><span class="sxs-lookup"><span data-stu-id="7f59e-108">Displays a list of dependent objects in a grid.</span></span> <span data-ttu-id="7f59e-109">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="7f59e-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="7f59e-110">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="7f59e-110">**Object Name**</span></span>  
 <span data-ttu-id="7f59e-111">显示可能需要处理的依赖对象的名称。</span><span class="sxs-lookup"><span data-stu-id="7f59e-111">Displays the name of the dependent object that may need to be processed.</span></span> <span data-ttu-id="7f59e-112">名称左侧的图标指示对象类型。</span><span class="sxs-lookup"><span data-stu-id="7f59e-112">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="7f59e-113">**Type**</span><span class="sxs-lookup"><span data-stu-id="7f59e-113">**Type**</span></span>  
 <span data-ttu-id="7f59e-114">显示可能需要处理的依赖对象的类型。</span><span class="sxs-lookup"><span data-stu-id="7f59e-114">Displays the type of dependent object that may need to be processed.</span></span>  
  
 <span data-ttu-id="7f59e-115">**影响类型**</span><span class="sxs-lookup"><span data-stu-id="7f59e-115">**Impact Type**</span></span>  
 <span data-ttu-id="7f59e-116">显示处理“处理”\*\*\*\* 对话框中的对象对依赖对象的影响。</span><span class="sxs-lookup"><span data-stu-id="7f59e-116">Displays the effect that processing the objects in the **Process** dialog box has on the dependent object.</span></span> <span data-ttu-id="7f59e-117">下表列出了处理的可能影响，并说明每种影响将导致警告还是错误：</span><span class="sxs-lookup"><span data-stu-id="7f59e-117">The following table lists the possible effects of processing and notes whether each one results in a warning or an error.</span></span>  
  
|<span data-ttu-id="7f59e-118">影响</span><span class="sxs-lookup"><span data-stu-id="7f59e-118">Impact</span></span>|<span data-ttu-id="7f59e-119">Message</span><span class="sxs-lookup"><span data-stu-id="7f59e-119">Message</span></span>|  
|------------|-------------|  
|<span data-ttu-id="7f59e-120">将清除对象（不处理）</span><span class="sxs-lookup"><span data-stu-id="7f59e-120">Object will be cleared (unprocessed)</span></span>|<span data-ttu-id="7f59e-121">警告</span><span class="sxs-lookup"><span data-stu-id="7f59e-121">Warning</span></span>|  
|<span data-ttu-id="7f59e-122">对象将无效</span><span class="sxs-lookup"><span data-stu-id="7f59e-122">Object would be invalid</span></span>|<span data-ttu-id="7f59e-123">错误</span><span class="sxs-lookup"><span data-stu-id="7f59e-123">Error</span></span>|  
|<span data-ttu-id="7f59e-124">将删除聚合</span><span class="sxs-lookup"><span data-stu-id="7f59e-124">Aggregation would be dropped</span></span>|<span data-ttu-id="7f59e-125">警告</span><span class="sxs-lookup"><span data-stu-id="7f59e-125">Warning</span></span>|  
|<span data-ttu-id="7f59e-126">将删除灵活的聚合</span><span class="sxs-lookup"><span data-stu-id="7f59e-126">Flexible aggregation would be dropped</span></span>|<span data-ttu-id="7f59e-127">警告</span><span class="sxs-lookup"><span data-stu-id="7f59e-127">Warning</span></span>|  
|<span data-ttu-id="7f59e-128">将删除索引</span><span class="sxs-lookup"><span data-stu-id="7f59e-128">Indexes will be dropped</span></span>|<span data-ttu-id="7f59e-129">警告</span><span class="sxs-lookup"><span data-stu-id="7f59e-129">Warning</span></span>|  
|<span data-ttu-id="7f59e-130">将处理非子对象</span><span class="sxs-lookup"><span data-stu-id="7f59e-130">Non-child object will be processed</span></span>|<span data-ttu-id="7f59e-131">警告</span><span class="sxs-lookup"><span data-stu-id="7f59e-131">Warning</span></span>|  
  
 <span data-ttu-id="7f59e-132">**处理对象**</span><span class="sxs-lookup"><span data-stu-id="7f59e-132">**Process Object**</span></span>  
 <span data-ttu-id="7f59e-133">选择要使用处理操作处理的依赖对象。</span><span class="sxs-lookup"><span data-stu-id="7f59e-133">Select the dependent objects that you want to process with the processing operation.</span></span> <span data-ttu-id="7f59e-134">必须在处理操作完成后处理未选中的依赖对象。</span><span class="sxs-lookup"><span data-stu-id="7f59e-134">Dependent objects that are not selected must be processed after the processing operation is finished.</span></span> <span data-ttu-id="7f59e-135">否则，将无法使用这些对象。</span><span class="sxs-lookup"><span data-stu-id="7f59e-135">Otherwise, they cannot be used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f59e-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f59e-136">See Also</span></span>  
 <span data-ttu-id="7f59e-137">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7f59e-137">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7f59e-138">"处理" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="7f59e-138">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
