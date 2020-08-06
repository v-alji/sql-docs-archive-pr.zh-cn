---
title: )  (商业智能向导定义帐户智能Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17b8136e79097cd502d6b239ba6867c4e678c70f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687363"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a><span data-ttu-id="8c6e5-102">定义帐户智能（商业智能向导）</span><span class="sxs-lookup"><span data-stu-id="8c6e5-102">Define Account Intelligence (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="8c6e5-103">可以使用 **“定义帐户智能”** 页，将 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例上定义的帐户类型映射到特定数据源（提供帐户维度数据）中的源表所定义的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined by a source table in the data source that supplies the data for the account dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c6e5-104">如果将维度属性映射到“配置维度属性”页上的“帐户类型”属性时，将显示此页\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-104">This page will appear if a dimension attribute was mapped to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c6e5-105">选项</span><span class="sxs-lookup"><span data-stu-id="8c6e5-105">Options</span></span>  
 <span data-ttu-id="8c6e5-106">**源表帐户类型**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="8c6e5-107">显示的值包含在分配给“配置维度属性”页上的“帐户类型”属性类型的维度属性中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-107">Displays the values that are contained in the dimension attribute assigned to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
 <span data-ttu-id="8c6e5-108">**内置帐户类型**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="8c6e5-109">选择在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中定义的帐户类型，该帐户类型将映射到源表中的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="8c6e5-110">下表列出了在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中定义的帐户类型：</span><span class="sxs-lookup"><span data-stu-id="8c6e5-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="8c6e5-111">值</span><span class="sxs-lookup"><span data-stu-id="8c6e5-111">Value</span></span>|<span data-ttu-id="8c6e5-112">说明</span><span class="sxs-lookup"><span data-stu-id="8c6e5-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8c6e5-113">**资产**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-113">**Asset**</span></span>|<span data-ttu-id="8c6e5-114">在特定时间拥有的物品的价值。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="8c6e5-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-115">**Balance**</span></span>|<span data-ttu-id="8c6e5-116">在特定时间某物的计数。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="8c6e5-117">**费用**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-117">**Expense**</span></span>|<span data-ttu-id="8c6e5-118">所花费的价值。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-118">Value of things spent.</span></span>|  
|<span data-ttu-id="8c6e5-119">**流向**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-119">**Flow**</span></span>|<span data-ttu-id="8c6e5-120">事物的增量计数。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="8c6e5-121">**收入**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-121">**Income**</span></span>|<span data-ttu-id="8c6e5-122">收到的价值。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-122">Value of things received.</span></span>|  
|<span data-ttu-id="8c6e5-123">**负债**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-123">**Liability**</span></span>|<span data-ttu-id="8c6e5-124">在特定时间所拖欠的价值。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="8c6e5-125">**统计**</span><span class="sxs-lookup"><span data-stu-id="8c6e5-125">**Statistical**</span></span>|<span data-ttu-id="8c6e5-126">某事物的计算比率，或者未聚合的某事物的计数。</span><span class="sxs-lookup"><span data-stu-id="8c6e5-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c6e5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c6e5-127">See Also</span></span>  
 <span data-ttu-id="8c6e5-128">[商业智能向导的 F1 帮助](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8c6e5-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="8c6e5-129">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c6e5-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8c6e5-130">维度设计器 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="8c6e5-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
