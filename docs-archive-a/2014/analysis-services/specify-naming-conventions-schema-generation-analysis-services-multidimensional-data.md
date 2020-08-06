---
title: 指定命名约定 (架构生成向导)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.namingconventions.f1
ms.assetid: 02d830ea-5b1f-4485-9f94-d64b8bea592b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e9588b49331934041cad888142d29d189fc1a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589255"
---
# <a name="specify-naming-conventions-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="39277-102">指定命名约定（架构生成向导）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="39277-102">Specify Naming Conventions (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="39277-103">可以使用 **“指定命名约定”** 页，定义在创建架构对象时架构生成向导使用的命名约定。</span><span class="sxs-lookup"><span data-stu-id="39277-103">Use the **Specify Naming Conventions** page to define the naming conventions that the Schema Generation Wizard uses when creating schema objects.</span></span>  
  
## <a name="options"></a><span data-ttu-id="39277-104">选项</span><span class="sxs-lookup"><span data-stu-id="39277-104">Options</span></span>  
 <span data-ttu-id="39277-105">**选项**</span><span class="sxs-lookup"><span data-stu-id="39277-105">**Option**</span></span>  
 <span data-ttu-id="39277-106">指定向导所使用的命名约定。</span><span class="sxs-lookup"><span data-stu-id="39277-106">Specify the naming conventions for the wizard to use.</span></span> <span data-ttu-id="39277-107">下表对您可以指定的选项进行了说明：</span><span class="sxs-lookup"><span data-stu-id="39277-107">The following table describes the options you can specify.</span></span>  
  
|<span data-ttu-id="39277-108">选项</span><span class="sxs-lookup"><span data-stu-id="39277-108">Option</span></span>|<span data-ttu-id="39277-109">说明</span><span class="sxs-lookup"><span data-stu-id="39277-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="39277-110">**Separator**</span><span class="sxs-lookup"><span data-stu-id="39277-110">**Separator**</span></span>|<span data-ttu-id="39277-111">指定用于分隔对象名称中的字词的字符。</span><span class="sxs-lookup"><span data-stu-id="39277-111">Specifies the character that separates words in an object name.</span></span> <span data-ttu-id="39277-112">在 **“值”** 列中，选择 **“下划线”**、 **“空格”** 或 **“无”**。</span><span class="sxs-lookup"><span data-stu-id="39277-112">In the **Value** column, select **Underscore**, **Space**, or **None**.</span></span> <span data-ttu-id="39277-113">默认值为 **“下划线”**。</span><span class="sxs-lookup"><span data-stu-id="39277-113">The default is **Underscore**.</span></span>|  
|<span data-ttu-id="39277-114">**主键列前缀**</span><span class="sxs-lookup"><span data-stu-id="39277-114">**Primary key column prefix**</span></span>|<span data-ttu-id="39277-115">指定每个主键列名称的前缀字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-115">Specifies the string to prefix the name of each primary key column.</span></span> <span data-ttu-id="39277-116">默认值为 **PK**。</span><span class="sxs-lookup"><span data-stu-id="39277-116">The default is **PK**.</span></span>|  
|<span data-ttu-id="39277-117">**外键列前缀**</span><span class="sxs-lookup"><span data-stu-id="39277-117">**Foreign key column prefix**</span></span>|<span data-ttu-id="39277-118">指定每个外键列名称的前缀字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-118">Specifies the string to prefix the name of each foreign key column.</span></span> <span data-ttu-id="39277-119">默认值为 **FK**。</span><span class="sxs-lookup"><span data-stu-id="39277-119">The default is **FK**.</span></span>|  
|<span data-ttu-id="39277-120">**属性名称后缀**</span><span class="sxs-lookup"><span data-stu-id="39277-120">**Attribute name suffix**</span></span>|<span data-ttu-id="39277-121">指定追加到每个属性列名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-121">Specifies the string to be appended to the name of each attribute column.</span></span> <span data-ttu-id="39277-122">默认值为 **Name**。</span><span class="sxs-lookup"><span data-stu-id="39277-122">The default is **Name**.</span></span>|  
|<span data-ttu-id="39277-123">**自定义汇总后缀**</span><span class="sxs-lookup"><span data-stu-id="39277-123">**Custom rollup suffix**</span></span>|<span data-ttu-id="39277-124">指定追加到每个汇总列名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-124">Specifies the string to be appended to the name of each rollup column.</span></span> <span data-ttu-id="39277-125">默认值为 **CustomRollup**。</span><span class="sxs-lookup"><span data-stu-id="39277-125">The default is **CustomRollup**.</span></span>|  
|<span data-ttu-id="39277-126">**自定义汇总属性后缀**</span><span class="sxs-lookup"><span data-stu-id="39277-126">**Custom rollup Properties suffix**</span></span>|<span data-ttu-id="39277-127">指定追加到每个汇总属性列名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-127">Specifies the string to be appended to the name of each rollup property column.</span></span> <span data-ttu-id="39277-128">默认值为 **CustomRollupProperties**。</span><span class="sxs-lookup"><span data-stu-id="39277-128">The default is **CustomRollupProperties**.</span></span>|  
|<span data-ttu-id="39277-129">**一元运算符后缀**</span><span class="sxs-lookup"><span data-stu-id="39277-129">**Unary operator suffix**</span></span>|<span data-ttu-id="39277-130">指定追加到每个一元运算符列名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="39277-130">Specifies the string to be appended to the name of each unary operator column.</span></span> <span data-ttu-id="39277-131">默认值为 **UnaryOperator**。</span><span class="sxs-lookup"><span data-stu-id="39277-131">The default is **UnaryOperator**.</span></span>|  
  
 <span data-ttu-id="39277-132">**值**</span><span class="sxs-lookup"><span data-stu-id="39277-132">**Value**</span></span>  
 <span data-ttu-id="39277-133">为“选项”\*\*\*\* 中指定的选项指定在生成架构时要使用的值。</span><span class="sxs-lookup"><span data-stu-id="39277-133">Specify a value for the option specified in **Option** that you want to use when the schema is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39277-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39277-134">See Also</span></span>  
 <span data-ttu-id="39277-135">[架构生成向导的 F1 帮助 &#40;Analysis Services 多维数据&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="39277-135">[Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="39277-136">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="39277-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
