---
title: 定义 (商业智能向导) 的本地货币引用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: bcd5c01839ecc7ae120089f17a1b909f18464e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690864"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a><span data-ttu-id="0b5bb-102">定义本地货币引用（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="0b5bb-102">Define Local Currency Reference (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="0b5bb-103">可以使用“定义本地货币引用”\*\*\*\* 页，为涉及“选择换算类型”\*\*\*\* 页中指定的多对多或多对一换算类型的货币换算功能定义本地货币。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-103">Use the **Define Local Currency Reference** page to define the local currencies for currency conversion functionality that covers the many-to-many or many-to-one conversion types specified on the **Select Conversion Type** page.</span></span> <span data-ttu-id="0b5bb-104">本地货币是存储 **“选择度量值”** 页中所选度量值的事务时使用的货币。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b5bb-105">如果从维度设计器或者通过在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中右键单击维度启动了商业智能向导，则将不会显示此页。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-105">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0b5bb-106">如果在“选择换算类型”\*\*\*\* 页中选择了“一对多”\*\*\*\*，则不会显示此页。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-106">This page also does not appear if **One-to-Many** was selected on the **Select Conversion Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b5bb-107">选项</span><span class="sxs-lookup"><span data-stu-id="0b5bb-107">Options</span></span>  
 <span data-ttu-id="0b5bb-108">**事实数据表中的标识符**</span><span class="sxs-lookup"><span data-stu-id="0b5bb-108">**Identifiers in the fact table**</span></span>  
 <span data-ttu-id="0b5bb-109">对于包含“选择度量值”\*\*\*\* 页中所选度量值的事实数据表所引用的货币维度，选择此选项可指定为该货币维度中的本地货币提供货币标识符的属性。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-109">Select to specify an attribute that provides currency identifiers for local currencies in a currency dimension referenced by the fact table that contains the measures selected on the **Select Measures** page.</span></span> <span data-ttu-id="0b5bb-110"> (一个 "货币" 维度，其 `Type` 属性设置为 "*货币*"。 ) </span><span class="sxs-lookup"><span data-stu-id="0b5bb-110">(A currency dimension in one whose `Type` property is set to *Currency*.)</span></span>  
  
 <span data-ttu-id="0b5bb-111">在由事务本身确定事务的本地货币时使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-111">Use this option when the transaction itself determines the local currency for that transaction.</span></span> <span data-ttu-id="0b5bb-112">例如，在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 示例数据库中 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ，"Internet 销售" 度量值组具有与货币维度的常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-112">For example, in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="0b5bb-113">该度量值组的事实数据表包含一个外键列，该外键列引用该维度的维度表中的货币标识符。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-113">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span>  
  
 <span data-ttu-id="0b5bb-114">**事实数据引用的货币维度和属性**</span><span class="sxs-lookup"><span data-stu-id="0b5bb-114">**Currency dimension and attribute referenced by the fact data**</span></span>  
 <span data-ttu-id="0b5bb-115">在成员表示本地货币的货币标识符的货币维度中选择货币属性。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-115">Select the currency attribute within a currency dimension whose members represent currency identifiers for local currencies.</span></span> <span data-ttu-id="0b5bb-116"> (货币属性是其 `Type` 属性设置为 "*货币*" 的属性。 ) </span><span class="sxs-lookup"><span data-stu-id="0b5bb-116">(A currency attribute is one whose `Type` property is set to *Currency*.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b5bb-117"> 如果未选择 **“事实数据表中的标识符”** 选项，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-117">This option is not available if the **Identifiers in the fact table** option is not selected.</span></span>  
  
 <span data-ttu-id="0b5bb-118">**维度表中的属性**</span><span class="sxs-lookup"><span data-stu-id="0b5bb-118">**Attributes in the dimension table**</span></span>  
 <span data-ttu-id="0b5bb-119">选择此选项可从与包含本地货币货币标识符的度量值组相关的维度中指定属性。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-119">Select to specify an attribute from a dimension related to the measure group that contains currency identifiers for local currencies.</span></span>  
  
 <span data-ttu-id="0b5bb-120">在由事务和另一个业务实体（如位置）之间的关系确定该事务的本地货币时使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-120">Use this option when the relationship between a transaction and another business entity, such as a location, determines the local currency for that transaction.</span></span> <span data-ttu-id="0b5bb-121">例如，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 示例数据库-中 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ，"财务报表" 度量值组与 "货币" 维度之间通过 "单位" 维度的引用维度关系。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-121">For example, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="0b5bb-122">也就是说，“财务报表”度量值组的事实数据表包含一个外键列，该外键列引用了“单位”维度的维度表中的成员。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-122">That is, the fact table for the Financial Reporting measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="0b5bb-123">反过来，“单位”维度的维度表也包含一个外键列，该外键列引用“货币”维度的维度表中的货币标识符。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-123">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span>  
  
 <span data-ttu-id="0b5bb-124">**引用货币的维度属性**</span><span class="sxs-lookup"><span data-stu-id="0b5bb-124">**Dimension attribute that references currency**</span></span>  
 <span data-ttu-id="0b5bb-125">在成员引用本地货币的货币标识符的维度中选择属性。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-125">Select the attribute within a dimension whose members reference the currency identifiers for local currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b5bb-126"> 如果未选择 **“维度表中的属性”** 选项，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="0b5bb-126">This option is not available if the **Attributes in the dimension table** option is not selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5bb-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b5bb-127">See Also</span></span>  
 <span data-ttu-id="0b5bb-128">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="0b5bb-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="0b5bb-129">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0b5bb-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="0b5bb-130">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="0b5bb-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
