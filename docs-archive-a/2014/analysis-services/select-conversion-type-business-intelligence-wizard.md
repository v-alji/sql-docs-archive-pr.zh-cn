---
title: " (商业智能向导) 选择 \"转换类型\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f83fdf566b52a5fe79bea7a4a676274423d1091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579083"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a><span data-ttu-id="f4b47-102">选择换算类型（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="f4b47-102">Select Conversion Type (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="f4b47-103">可以使用 **“选择换算类型”** 页，为使用多种货币存储的事务定义本地货币和报表货币之间的关系。</span><span class="sxs-lookup"><span data-stu-id="f4b47-103">Use the **Select Conversion Type** page to define the relationship between local currencies and reporting currencies for transactions stored in multiple currencies.</span></span> <span data-ttu-id="f4b47-104">本地货币是存储 **“选择度量值”** 页中所选度量值的事务时使用的货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span> <span data-ttu-id="f4b47-105">报表货币是转换 **“选择度量值”** 页中所选事务时使用的货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-105">A reporting currency is the currency in which the transactions selected in the **Select Measures** page are translated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b47-106">如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，则将不会显示此页。</span><span class="sxs-lookup"><span data-stu-id="f4b47-106">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4b47-107">选项</span><span class="sxs-lookup"><span data-stu-id="f4b47-107">Options</span></span>  
 <span data-ttu-id="f4b47-108">**多对多**</span><span class="sxs-lookup"><span data-stu-id="f4b47-108">**Many-to-many**</span></span>  
 <span data-ttu-id="f4b47-109">使用本地货币存储事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-109">Stores transactions using local currencies.</span></span> <span data-ttu-id="f4b47-110">货币换算功能将此类事务换算成 **“设置货币换算选项”** 页中指定的先导货币，然后换算成一个或多个其他报表货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-110">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
 <span data-ttu-id="f4b47-111">例如，先导货币可以设置为美元 (USD)，而事实数据表使用欧元 (EUR)、澳大利亚元 (AUD) 和墨西哥比索 (MXN) 来存储交易。</span><span class="sxs-lookup"><span data-stu-id="f4b47-111">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="f4b47-112">选择此选项可以将这些事务从其指定的本地货币换算成先导货币，然后再次将换算的事务从先导货币换算成指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-112">Selecting this option converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="f4b47-113">结果是可以使用指定的本地货币存储事务，并使用指定的先导货币或 **“指定报表货币”** 页中指定的任一报表货币来查看事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-113">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
 <span data-ttu-id="f4b47-114">**多对一**</span><span class="sxs-lookup"><span data-stu-id="f4b47-114">**Many-to-one**</span></span>  
 <span data-ttu-id="f4b47-115">使用本地货币存储事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-115">Stores transactions using local currencies.</span></span> <span data-ttu-id="f4b47-116">货币换算功能将此类事务换算成 **“设置货币换算选项”** 页中指定的先导货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-116">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page.</span></span> <span data-ttu-id="f4b47-117">该先导货币用作唯一指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-117">The pivot currency serves as the only specified reporting currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b47-118">如果选择此选项，则不显示“指定报表货币”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="f4b47-118">If this option is selected, the **Specify Reporting Currencies** page does not appear.</span></span>  
  
 <span data-ttu-id="f4b47-119">例如，先导货币可以设置为美元 (USD)，而事实数据表使用欧元 (EUR)、澳大利亚元 (AUD) 和墨西哥比索 (MXN) 来存储交易。</span><span class="sxs-lookup"><span data-stu-id="f4b47-119">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="f4b47-120">选择此选项可以将这些事务从其指定的本地货币换算成先导货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-120">Selecting this option converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="f4b47-121">结果是可以使用指定的本地货币存储事务，并使用指定的先导货币来查看事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-121">The result is that transactions can be stored in the specified local currencies and viewed in the specified pivot currency.</span></span>  
  
 <span data-ttu-id="f4b47-122">**一对多**</span><span class="sxs-lookup"><span data-stu-id="f4b47-122">**One-to-many**</span></span>  
 <span data-ttu-id="f4b47-123">使用“设置货币换算选项”\*\*\*\* 页中指定的先导货币存储事务，然后换算成一种或多种其他报表货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-123">Store transactions using the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4b47-124">如果选择此选项，则不显示“定义本地货币引用”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="f4b47-124">If this option is selected, the **Define Local Currency Reference** page does not appear.</span></span>  
  
 <span data-ttu-id="f4b47-125">例如，先导货币可以设置为美元 (USD)，而事实数据表使用 USD 来存储事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-125">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="f4b47-126">选择此选项可以将这些事务从先导货币换算成指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="f4b47-126">Selecting this option converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="f4b47-127">结果是可以使用指定的先导货币存储事务，并使用指定的先导货币或 **“指定报表货币”** 页中指定的任一报表货币来查看事务。</span><span class="sxs-lookup"><span data-stu-id="f4b47-127">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b47-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4b47-128">See Also</span></span>  
 <span data-ttu-id="f4b47-129">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="f4b47-129">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="f4b47-130">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f4b47-130">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f4b47-131">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f4b47-131">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
