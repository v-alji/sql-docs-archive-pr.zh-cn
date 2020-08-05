---
title: " (商业智能向导) 中选择成员 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd5f184e0d9670725609531b6d0a101f8e7f8647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579821"
---
# <a name="select-members-business-intelligence-wizard"></a><span data-ttu-id="25f2f-102">选择成员（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="25f2f-102">Select Members (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="25f2f-103">可以使用 **“选择成员”** 页，确定商业智能向导应对哪些成员应用 **“设置货币换算选项”** 页上指定的货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-103">Use the **Select Members** page to determine to which members the Business Intelligence Wizard should apply the currency conversion functionality specified on the **Set Currency Conversion Options** page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25f2f-104">如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，则将不会显示此页。</span><span class="sxs-lookup"><span data-stu-id="25f2f-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="25f2f-105">选项</span><span class="sxs-lookup"><span data-stu-id="25f2f-105">Options</span></span>  
 <span data-ttu-id="25f2f-106">**度量值维度**</span><span class="sxs-lookup"><span data-stu-id="25f2f-106">**Measures dimension**</span></span>  
 <span data-ttu-id="25f2f-107">选择此选项可以对多维数据集中的一个或多个度量值应用货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-107">Select to apply the currency conversion functionality to one or more measures in the cube.</span></span>  
  
 <span data-ttu-id="25f2f-108">如果选择此选项，网格中将显示下表中所列出的选项：</span><span class="sxs-lookup"><span data-stu-id="25f2f-108">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="25f2f-109">选项</span><span class="sxs-lookup"><span data-stu-id="25f2f-109">Option</span></span>|<span data-ttu-id="25f2f-110">说明</span><span class="sxs-lookup"><span data-stu-id="25f2f-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25f2f-111">**内置度量值类型**</span><span class="sxs-lookup"><span data-stu-id="25f2f-111">**Built-in Measure Types**</span></span>|<span data-ttu-id="25f2f-112">选择此选项可为指定的度量值包括货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-112">Select to include currency conversion functionality for the specified measure.</span></span>|  
|<span data-ttu-id="25f2f-113">**措施**</span><span class="sxs-lookup"><span data-stu-id="25f2f-113">**Measures**</span></span>|<span data-ttu-id="25f2f-114">从包含汇率的比率度量值组中，选择在换算从“内置度量值类型”\*\*\*\* 中选择的度量值时要使用的度量值。</span><span class="sxs-lookup"><span data-stu-id="25f2f-114">Select the measure from the rate measure group that contains the exchange rate to use when the measure selected in **Built-in Measure Types** is converted.</span></span>|  
  
 <span data-ttu-id="25f2f-115">**帐户层次结构**</span><span class="sxs-lookup"><span data-stu-id="25f2f-115">**Account hierarchy**</span></span>  
 <span data-ttu-id="25f2f-116">选择此选项可以对多维数据集中所包括帐户维度的帐户层次结构中的一个或多个成员应用货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-116">Select to apply the currency conversion functionality to one or more members in the account hierarchy of the account dimension included in the cube.</span></span> <span data-ttu-id="25f2f-117">帐户层次结构是帐户维度中的层次结构，其 `Type` 属性设置为 "*帐户*"。</span><span class="sxs-lookup"><span data-stu-id="25f2f-117">The account hierarchy is the hierarchy within the account dimension whose `Type` property is set to *Account*.</span></span>  
  
 <span data-ttu-id="25f2f-118">如果选择此选项，网格中将显示下表中所列出的选项：</span><span class="sxs-lookup"><span data-stu-id="25f2f-118">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="25f2f-119">选项</span><span class="sxs-lookup"><span data-stu-id="25f2f-119">Option</span></span>|<span data-ttu-id="25f2f-120">说明</span><span class="sxs-lookup"><span data-stu-id="25f2f-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25f2f-121">**帐户成员**</span><span class="sxs-lookup"><span data-stu-id="25f2f-121">**Account Member**</span></span>|<span data-ttu-id="25f2f-122">选择此选项可为帐户层次结构中指定的成员包括货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-122">Select to include currency conversion functionality for the specified member of the account hierarchy.</span></span>|  
|<span data-ttu-id="25f2f-123">**措施**</span><span class="sxs-lookup"><span data-stu-id="25f2f-123">**Measures**</span></span>|<span data-ttu-id="25f2f-124">从包含汇率的比率度量值组中，选择在换算 **“帐户成员”** 中所选成员的度量值时要使用的度量值。</span><span class="sxs-lookup"><span data-stu-id="25f2f-124">Select the measure from the rate measure group that contains the exchange rate to use when the measures for the member selected in **Account Member** are converted.</span></span>|  
  
 <span data-ttu-id="25f2f-125">**基于类型的帐户层次结构**</span><span class="sxs-lookup"><span data-stu-id="25f2f-125">**Account hierarchy based on type**</span></span>  
 <span data-ttu-id="25f2f-126">选择此选项可以向以下成员应用货币换算功能：帐户层次结构中 `Type` 属性设置为指定帐户类型的特性的所有成员。</span><span class="sxs-lookup"><span data-stu-id="25f2f-126">Select to apply the currency conversion functionality to all members of attributes in the account hierarchy whose `Type` property is set to a specified account type.</span></span>  
  
 <span data-ttu-id="25f2f-127">如果选择此选项，网格中将显示下表中所列出的选项：</span><span class="sxs-lookup"><span data-stu-id="25f2f-127">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="25f2f-128">选项</span><span class="sxs-lookup"><span data-stu-id="25f2f-128">Option</span></span>|<span data-ttu-id="25f2f-129">说明</span><span class="sxs-lookup"><span data-stu-id="25f2f-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25f2f-130">**帐户类型**</span><span class="sxs-lookup"><span data-stu-id="25f2f-130">**Account Type**</span></span>|<span data-ttu-id="25f2f-131">选择此选项可为指定的帐户类型包括货币换算功能。</span><span class="sxs-lookup"><span data-stu-id="25f2f-131">Select to include currency conversion functionality for the specified account type.</span></span>|  
|<span data-ttu-id="25f2f-132">**措施**</span><span class="sxs-lookup"><span data-stu-id="25f2f-132">**Measures**</span></span>|<span data-ttu-id="25f2f-133">对于使用 **“帐户类型”** 中所选择的帐户类型的属性，从包含汇率的比率度量值组中，选择在换算这些属性的成员的度量值时要使用的度量值。</span><span class="sxs-lookup"><span data-stu-id="25f2f-133">Select the measure from the rate measure group that contains the exchange rate to use when measures for the members of attributes using the account type selected in **Account Type** are converted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25f2f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25f2f-134">See Also</span></span>  
 <span data-ttu-id="25f2f-135">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="25f2f-135">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="25f2f-136">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="25f2f-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="25f2f-137">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="25f2f-137">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
