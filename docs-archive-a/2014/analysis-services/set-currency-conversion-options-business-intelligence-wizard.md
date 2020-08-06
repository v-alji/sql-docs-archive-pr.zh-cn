---
title: " (商业智能向导) 设置货币换算选项 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.calculationsettings.f1
ms.assetid: a49d4e1f-bdda-4a83-ab4f-ce8c500e1d6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61877deb0bc422d65f977e3fc9de3e678f7d8477
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691915"
---
# <a name="set-currency-conversion-options-business-intelligence-wizard"></a><span data-ttu-id="c5f4b-102">设置货币换算选项（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="c5f4b-102">Set Currency Conversion Options (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="c5f4b-103">可以使用 **“设置货币换算选项”** 页，为包含汇率的度量值组定义货币换算计算。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-103">Use the **Set Currency Conversion** page to define currency conversion calculations for a measure group that contains exchange rates.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5f4b-104">如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，则将不会显示此页。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5f4b-105">选项</span><span class="sxs-lookup"><span data-stu-id="c5f4b-105">Options</span></span>  
 <span data-ttu-id="c5f4b-106">**选择包含汇率的度量值组**</span><span class="sxs-lookup"><span data-stu-id="c5f4b-106">**Select the measure group that contains exchange rates**</span></span>  
 <span data-ttu-id="c5f4b-107">选择包含货币换算计算要引用的汇率的度量值组。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-107">Select the measure group that contains the exchange rates that the currency conversion calculations should reference.</span></span>  
  
 <span data-ttu-id="c5f4b-108">**指定先导货币**</span><span class="sxs-lookup"><span data-stu-id="c5f4b-108">**Specify the pivot currency**</span></span>  
 <span data-ttu-id="c5f4b-109">选择作为度量值组的先导货币的成员。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-109">Select the member that serves as the pivot currency for the measure group.</span></span>  
  
 <span data-ttu-id="c5f4b-110">**选择如何输入了汇率(选择示例货币)**</span><span class="sxs-lookup"><span data-stu-id="c5f4b-110">**Select how you entered your exchange rates (select a sample currency)**</span></span>  
 <span data-ttu-id="c5f4b-111">从货币维度中选择代表示例货币的成员，以便更改“每 1 示例货币折合 X 先导货币”和“每 1 先导货币折合 X 示例货币”选项的文本，使其更好地显示汇率方向。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-111">Select a member representing a sample currency from the currency dimension to change the text for the X pivot currency per 1 sample currency and X sample currency per 1 pivot currency options to better display the exchange rate direction.</span></span>  
  
 <span data-ttu-id="c5f4b-112">**每 1 示例货币折合 X 先导货币**</span><span class="sxs-lookup"><span data-stu-id="c5f4b-112">**X pivot currency per 1 sample currency**</span></span>  
 <span data-ttu-id="c5f4b-113">选择此选项可以指示比率度量值组中的汇率代表指定先导货币的换算比例。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-113">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified pivot currency.</span></span>  
  
 <span data-ttu-id="c5f4b-114">**每 1 先导货币折合 X 示例货币**</span><span class="sxs-lookup"><span data-stu-id="c5f4b-114">**X sample currency per 1 pivot currency**</span></span>  
 <span data-ttu-id="c5f4b-115">选择此选项可以指示比率度量值组中的汇率代表指定示例货币的换算比例。</span><span class="sxs-lookup"><span data-stu-id="c5f4b-115">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified sample currency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f4b-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5f4b-116">See Also</span></span>  
 <span data-ttu-id="c5f4b-117">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c5f4b-117">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="c5f4b-118">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5f4b-118">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c5f4b-119">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="c5f4b-119">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
