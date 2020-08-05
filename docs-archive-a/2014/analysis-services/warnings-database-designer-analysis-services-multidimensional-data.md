---
title: 数据库设计器)  ( (Analysis Services 多维数据) 的警告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf635460187fe56f4811de5090cada002ea8ca3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580385"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="cac00-102">警告（数据库设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="cac00-102">Warnings (Database Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="cac00-103">使用“警告”\*\*\*\* 选项卡可以全局查看和解除规则，并可以查看和重新启用已解除的警告的特定实例。</span><span class="sxs-lookup"><span data-stu-id="cac00-103">Use the **Warnings** tab to view and dismiss rules globally, and to view and re-enable specific instances of dismissed warnings.</span></span> <span data-ttu-id="cac00-104">**“警告”** 选项卡显示两个网格： **“设计警告规则”** 和 **“解除的警告”**。</span><span class="sxs-lookup"><span data-stu-id="cac00-104">The **Warnings** tab displays two grids: **Design Warning Rules** and **Dismissed Warnings**.</span></span>  
  
 <span data-ttu-id="cac00-105">**显示“警告”选项卡**</span><span class="sxs-lookup"><span data-stu-id="cac00-105">**To display the Warnings tab**</span></span>  
  
1.  <span data-ttu-id="cac00-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="cac00-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="cac00-107">在**解决方案资源管理器**中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目，单击“编辑数据库”\*\*\*\*，然后单击“警告”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="cac00-107">In **Solution Explorer**, right-click the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, click **Edit Database**, and then click the **Warnings** tab.</span></span>  
  
## <a name="design-warning-rules-grid"></a><span data-ttu-id="cac00-108">“设计警告规则”网格</span><span class="sxs-lookup"><span data-stu-id="cac00-108">Design Warning Rules Grid</span></span>  
 <span data-ttu-id="cac00-109">**“设计警告规则”** 网格显示所有设计警告规则。</span><span class="sxs-lookup"><span data-stu-id="cac00-109">The **Design Warning Rules** grid displays all the design warning rules.</span></span> <span data-ttu-id="cac00-110">此网格还控制对数据库所启用的规则。</span><span class="sxs-lookup"><span data-stu-id="cac00-110">This grid also controls which rules are enabled for the database.</span></span> <span data-ttu-id="cac00-111">若要启用或禁用某个警告规则，请选中或清除其复选框。</span><span class="sxs-lookup"><span data-stu-id="cac00-111">To enable or disable a warning rule, select or clear its check box.</span></span>  
  
 <span data-ttu-id="cac00-112">**“设计警告规则”** 网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="cac00-112">The **Design Warning Rules** grid has the following columns:</span></span>  
  
 <span data-ttu-id="cac00-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="cac00-113">**Description**</span></span>  
 <span data-ttu-id="cac00-114">显示规则的名称。</span><span class="sxs-lookup"><span data-stu-id="cac00-114">Displays the name of the rule.</span></span> <span data-ttu-id="cac00-115">规则会按类别分组。</span><span class="sxs-lookup"><span data-stu-id="cac00-115">Rules are grouped by category.</span></span>  
  
 <span data-ttu-id="cac00-116">**重要性**</span><span class="sxs-lookup"><span data-stu-id="cac00-116">**Importance**</span></span>  
 <span data-ttu-id="cac00-117">显示分配给规则的重要性。</span><span class="sxs-lookup"><span data-stu-id="cac00-117">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="cac00-118">**注释**</span><span class="sxs-lookup"><span data-stu-id="cac00-118">**Comments**</span></span>  
 <span data-ttu-id="cac00-119">（可选）允许用户键入注释，对解除警告的原因进行解释。</span><span class="sxs-lookup"><span data-stu-id="cac00-119">(Optional) Allows the user to type a comment that explains why you are dismissing the warning.</span></span>  
  
## <a name="dismissed-warnings-grid"></a><span data-ttu-id="cac00-120">“解除的警告”网格</span><span class="sxs-lookup"><span data-stu-id="cac00-120">Dismissed Warnings Grid</span></span>  
 <span data-ttu-id="cac00-121">**“解除的警告”** 网格显示所有已从 **“错误列表”** 解除的特定警告。</span><span class="sxs-lookup"><span data-stu-id="cac00-121">The **Dismissed Warnings** grid displays all specific warning occurrences that have been dismissed from the **Error List**.</span></span> <span data-ttu-id="cac00-122">若要重新启用某个警告，请在网格中选择该警告，然后单击“重新启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cac00-122">To re-enable a warning, select it in the grid, and then click **Re-enable**.</span></span>  
  
 <span data-ttu-id="cac00-123">**“解除的警告”** 网格包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="cac00-123">The **Dismissed Warnings** grid has the following :</span></span>  
  
 <span data-ttu-id="cac00-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="cac00-124">**Object**</span></span>  
 <span data-ttu-id="cac00-125">显示代表对象类型和对象名称的图标。</span><span class="sxs-lookup"><span data-stu-id="cac00-125">Displays an icon that represents the object type and the object name.</span></span>  
  
 <span data-ttu-id="cac00-126">**Type**</span><span class="sxs-lookup"><span data-stu-id="cac00-126">**Type**</span></span>  
 <span data-ttu-id="cac00-127">显示对象类型。</span><span class="sxs-lookup"><span data-stu-id="cac00-127">Displays the object type.</span></span>  
  
 <span data-ttu-id="cac00-128">**说明**</span><span class="sxs-lookup"><span data-stu-id="cac00-128">**Description**</span></span>  
 <span data-ttu-id="cac00-129">显示规则的名称。</span><span class="sxs-lookup"><span data-stu-id="cac00-129">Displays the name of the rule.</span></span>  
  
 <span data-ttu-id="cac00-130">**重要性**</span><span class="sxs-lookup"><span data-stu-id="cac00-130">**Importance**</span></span>  
 <span data-ttu-id="cac00-131">显示分配给规则的重要性。</span><span class="sxs-lookup"><span data-stu-id="cac00-131">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="cac00-132">**注释**</span><span class="sxs-lookup"><span data-stu-id="cac00-132">**Comments**</span></span>  
 <span data-ttu-id="cac00-133">显示解除该警告时输入的注释。</span><span class="sxs-lookup"><span data-stu-id="cac00-133">Displays the comment that was entered when the warning was dismissed.</span></span> <span data-ttu-id="cac00-134">可在此添加或修改注释。</span><span class="sxs-lookup"><span data-stu-id="cac00-134">You can add or modify a comment here.</span></span>  
  
 <span data-ttu-id="cac00-135">**重新启用**</span><span class="sxs-lookup"><span data-stu-id="cac00-135">**Re-enable**</span></span>  
 <span data-ttu-id="cac00-136">重新启用选定的警告。</span><span class="sxs-lookup"><span data-stu-id="cac00-136">Re-enables the selected warnings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cac00-137">如果对象包含警告，但是该对象处于无效状态或已从项目中手动删除，则列表中该警告的旁边会出现错误图标。</span><span class="sxs-lookup"><span data-stu-id="cac00-137">If an object has a warning, but the object is in an invalid state or was manually removed from the project, an error icon appears next to the warning in the list.</span></span> <span data-ttu-id="cac00-138">若要解除该警告，请选择它，然后单击“重新启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cac00-138">To dismiss the warning, select it and then click **Re-enable**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac00-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cac00-139">See Also</span></span>  
 <span data-ttu-id="cac00-140">["解除警告" 对话框 &#40;Analysis Services 多维数据&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="cac00-140">[Dismiss Warning Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="cac00-141">Analysis Services 多维&#41;数据&#41; &#40;的常规 &#40;数据库设计器</span><span class="sxs-lookup"><span data-stu-id="cac00-141">General &#40;Database Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
