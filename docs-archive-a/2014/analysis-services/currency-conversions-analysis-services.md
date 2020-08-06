---
title: Analysis Services) 的货币换算 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple currency conversions
- monetary data [SQL Server]
- currency [Analysis Services]
- converting currency
- one-to-many currency conversions
- many-to-many currency conversions [Analysis Services]
- many-to-one currency conversions [Analysis Services]
ms.assetid: e03f491c-7df8-46a0-ade9-f2e55b68db85
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4fee100dea2b3aff99516175bf688337a33592e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589983"
---
# <a name="currency-conversions-analysis-services"></a><span data-ttu-id="912ef-102">货币换算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="912ef-102">Currency Conversions (Analysis Services)</span></span>
  <span data-ttu-id="912ef-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 仅多维</span><span class="sxs-lookup"><span data-stu-id="912ef-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="912ef-104">使用一组由多维表达式 (MDX) 脚本引导的功能组合，在支持多种货币的多维数据集中提供货币换算支持。</span><span class="sxs-lookup"><span data-stu-id="912ef-104">uses a combination of features, guided by Multidimensional Expressions (MDX) scripts, to provide currency conversion support in cubes supporting multiple currencies.</span></span>  
  
## <a name="currency-conversion-terminology"></a><span data-ttu-id="912ef-105">货币换算术语</span><span class="sxs-lookup"><span data-stu-id="912ef-105">Currency Conversion Terminology</span></span>  
 <span data-ttu-id="912ef-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中使用下列术语来说明货币换算功能：</span><span class="sxs-lookup"><span data-stu-id="912ef-106">The following terminology is used in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to describe currency conversion functionality:</span></span>  
  
 <span data-ttu-id="912ef-107">先导货币</span><span class="sxs-lookup"><span data-stu-id="912ef-107">Pivot currency</span></span>  
 <span data-ttu-id="912ef-108">在比率度量值组中为其输入汇率的货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-108">The currency against which exchange rates are entered in the rate measure group.</span></span>  
  
 <span data-ttu-id="912ef-109">本地货币</span><span class="sxs-lookup"><span data-stu-id="912ef-109">Local currency</span></span>  
 <span data-ttu-id="912ef-110">用于存储待换算度量值所基于的交易的货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-110">The currency used to store transactions on which measures to be converted are based.</span></span>  
  
 <span data-ttu-id="912ef-111">本地货币可由下面的两者之一标识：</span><span class="sxs-lookup"><span data-stu-id="912ef-111">The local currency can be identified by either:</span></span>  
  
-   <span data-ttu-id="912ef-112">事实数据表中与交易存储在一起的货币标识符，对于使用交易本身来标识用于该交易的货币的银行应用程序来说，通常是这种情况。</span><span class="sxs-lookup"><span data-stu-id="912ef-112">A currency identifier in the fact table stored with the transaction, as is commonly the case with banking applications where the transaction itself identifies the currency used for that transaction.</span></span>  
  
-   <span data-ttu-id="912ef-113">与维度表中的一个属性相关联然后又与事实数据表中的一个交易相关联的货币标识符，对于使用位置或其他标识符（例如子公司）来标识用于相关交易的货币的财务应用程序来说，通常是这种情况。</span><span class="sxs-lookup"><span data-stu-id="912ef-113">A currency identifier associated with an attribute in a dimension table that is then associated with a transaction in the fact table, as is commonly the case in financial applications where a location or other identifier, such as a subsidiary, identifies the currency used for an associated transaction.</span></span>  
  
 <span data-ttu-id="912ef-114">报表货币</span><span class="sxs-lookup"><span data-stu-id="912ef-114">Reporting currency</span></span>  
 <span data-ttu-id="912ef-115">交易要从先导货币换算到的货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-115">The currency to which transactions are converted from the pivot currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="912ef-116">对多对一货币换算来说，先导货币和报表货币是相同的。</span><span class="sxs-lookup"><span data-stu-id="912ef-116">For many-to-one currency conversions, the pivot currency and reporting currency are the same.</span></span>  
  
 <span data-ttu-id="912ef-117">货币维度</span><span class="sxs-lookup"><span data-stu-id="912ef-117">Currency dimension</span></span>  
 <span data-ttu-id="912ef-118">一个为之定义了以下设置的数据库维度：</span><span class="sxs-lookup"><span data-stu-id="912ef-118">A database dimension defined with the following settings:</span></span>  
  
-   <span data-ttu-id="912ef-119">维度的 `Type` 属性设置为 Currency。</span><span class="sxs-lookup"><span data-stu-id="912ef-119">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="912ef-120">该维度的一个特性的 `Type` 属性被设置为 CurrencyName。</span><span class="sxs-lookup"><span data-stu-id="912ef-120">The `Type` property of one attribute for the dimension is set to CurrencyName.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="912ef-121">该特性的值必须用于应当包含货币标识符的所有列中。</span><span class="sxs-lookup"><span data-stu-id="912ef-121">The values of this attribute must be used in all columns that should contain a currency identifier.</span></span>  
  
 <span data-ttu-id="912ef-122">比率度量值组</span><span class="sxs-lookup"><span data-stu-id="912ef-122">Rate measure group</span></span>  
 <span data-ttu-id="912ef-123">多维数据集中的一个度量值组，为其定义了以下设置：</span><span class="sxs-lookup"><span data-stu-id="912ef-123">A measure group in a cube, defined with the following settings:</span></span>  
  
-   <span data-ttu-id="912ef-124">货币维度和比率度量值组之间的常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-124">A regular dimension relationship exists between a currency dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="912ef-125">时间维度和比率度量值组之间的常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-125">A regular dimension relationship exists between a time dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="912ef-126">作为一个可选项，还可以将 `Type` 属性设置为 ExchangeRate。</span><span class="sxs-lookup"><span data-stu-id="912ef-126">Optionally, the `Type` property is set to ExchangeRate.</span></span> <span data-ttu-id="912ef-127">当商业智能向导将这些关系和货币与时间维度一起使用来标识可能的比率度量值组时，将 `Type` 属性设置为 ExchangeRate 可使得客户端应用程序能够更轻松地标识比率度量值组。</span><span class="sxs-lookup"><span data-stu-id="912ef-127">While the Business Intelligence Wizard uses the relationships with the currency and time dimensions to identify likely rate measure groups, setting the `Type` property to ExchangeRate allows client applications to more easily identify rate measure groups.</span></span>  
  
-   <span data-ttu-id="912ef-128">一个或多个度量值，用来代表比率度量值组中包含的汇率。</span><span class="sxs-lookup"><span data-stu-id="912ef-128">One or more measures, representing the exchange rates contained by the rate measure group.</span></span>  
  
 <span data-ttu-id="912ef-129">报表货币维度</span><span class="sxs-lookup"><span data-stu-id="912ef-129">Reporting currency dimension</span></span>  
 <span data-ttu-id="912ef-130">由商业智能向导在定义了货币换算后定义的维度，它包含用于货币换算的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-130">The dimension, defined by the Business Intelligence Wizard after a currency conversion is defined, that contains the reporting currencies for that currency conversion.</span></span> <span data-ttu-id="912ef-131">报表货币维度基于一个命名查询，此命名查询定义于和比率度量值组相关联的货币维度所基于的数据源视图中，来自货币维度的维度主表。</span><span class="sxs-lookup"><span data-stu-id="912ef-131">The reporting currency dimension is based on a named query, defined in the data source view on which the currency dimension associated with the rate measure group is based, from the dimension main table of the currency dimension.</span></span> <span data-ttu-id="912ef-132">该维度被定义了以下设置：</span><span class="sxs-lookup"><span data-stu-id="912ef-132">The dimension is defined with the following settings:</span></span>  
  
-   <span data-ttu-id="912ef-133">维度的 `Type` 属性设置为 Currency。</span><span class="sxs-lookup"><span data-stu-id="912ef-133">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="912ef-134">该维度的键特性的 `Type` 属性被设置为 CurrencyName。</span><span class="sxs-lookup"><span data-stu-id="912ef-134">The `Type` property of the key attribute for the dimension is set to CurrencyName.</span></span>  
  
-   <span data-ttu-id="912ef-135">该维度的一个特性的 `Type` 属性被设置为 CurrencyDestination，并且绑定到该特性的列包含代表用于货币换算的报表货币的货币标识符。</span><span class="sxs-lookup"><span data-stu-id="912ef-135">The `Type` property of one attribute within the dimension is set to CurrencyDestination, and the column bound to the attribute contains the currency identifiers that represent the reporting currencies for the currency conversion.</span></span>  
  
## <a name="defining-currency-conversions"></a><span data-ttu-id="912ef-136">定义货币换算</span><span class="sxs-lookup"><span data-stu-id="912ef-136">Defining Currency Conversions</span></span>  
 <span data-ttu-id="912ef-137">您可以使用商业智能向导来为多维数据集定义货币换算功能，也可以使用 MDX 脚本来手动定义货币换算。</span><span class="sxs-lookup"><span data-stu-id="912ef-137">You can use the Business Intelligence Wizard to define currency conversion functionality for a cube, or you can manually define currency conversions using MDX scripts.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="912ef-138">先决条件</span><span class="sxs-lookup"><span data-stu-id="912ef-138">Prerequisites</span></span>  
 <span data-ttu-id="912ef-139">您必须首先定义至少一个货币维度、至少一个时间维度和至少一个比率度量值组，然后才能使用商业智能向导在多维数据集中定义货币换算。</span><span class="sxs-lookup"><span data-stu-id="912ef-139">Before you can define a currency conversion in a cube using the Business Intelligence Wizard, you must first define at least one currency dimension, at least one time dimension, and at least one rate measure group.</span></span> <span data-ttu-id="912ef-140">商业智能向导可以从这些对象中检索相应的数据和元数据，以用于构造提供货币换算功能所需的报表货币维度和 MDX 脚本。</span><span class="sxs-lookup"><span data-stu-id="912ef-140">From these objects, the Business Intelligence Wizard can retrieve the data and metadata used to construct the reporting currency dimension and MDX script needed to provide currency conversion functionality.</span></span>  
  
### <a name="decisions"></a><span data-ttu-id="912ef-141">决策</span><span class="sxs-lookup"><span data-stu-id="912ef-141">Decisions</span></span>  
 <span data-ttu-id="912ef-142">您需要作出下列决策，商业智能向导才能构造提供货币换算功能所需的报表货币维度和 MDX 脚本：</span><span class="sxs-lookup"><span data-stu-id="912ef-142">You need to make the following decisions before the Business Intelligence Wizard can construct the reporting currency dimension and MDX script needed to provide currency conversion functionality:</span></span>  
  
-   <span data-ttu-id="912ef-143">汇率方向</span><span class="sxs-lookup"><span data-stu-id="912ef-143">Exchange rate direction</span></span>  
  
-   <span data-ttu-id="912ef-144">待换算成员</span><span class="sxs-lookup"><span data-stu-id="912ef-144">Converted members</span></span>  
  
-   <span data-ttu-id="912ef-145">换算类型</span><span class="sxs-lookup"><span data-stu-id="912ef-145">Conversion type</span></span>  
  
-   <span data-ttu-id="912ef-146">本地货币</span><span class="sxs-lookup"><span data-stu-id="912ef-146">Local currencies</span></span>  
  
-   <span data-ttu-id="912ef-147">报表货币</span><span class="sxs-lookup"><span data-stu-id="912ef-147">Reporting currencies</span></span>  
  
### <a name="exchange-rate-directions"></a><span data-ttu-id="912ef-148">汇率方向</span><span class="sxs-lookup"><span data-stu-id="912ef-148">Exchange Rate Directions</span></span>  
 <span data-ttu-id="912ef-149">比率度量值组中包含代表本地货币和先导货币（通常称为公司货币）之间的关系的度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-149">The rate measure group contains measures representing exchange rates between local currencies and the pivot currency (commonly referred to as the corporate currency).</span></span> <span data-ttu-id="912ef-150">汇率方向和换算类型的组合决定了使用商业智能向导生成的 MDX 脚本对待换算度量值所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="912ef-150">The combination of exchange rate direction and conversion type determines the operation performed on measures to be converted by the MDX script generated using the Business Intelligence Wizard.</span></span> <span data-ttu-id="912ef-151">下表说明了基于商业智能向导中可用的汇率方向选项和换算方向时，根据不同的汇率方向和换算类型执行的操作。</span><span class="sxs-lookup"><span data-stu-id="912ef-151">The following table describes the operations performed depending on the exchange rate direction and conversion type, based on the exchange rate direction options and conversion directions available in the Business Intelligence Wizard.</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="912ef-152">汇率方向</span><span class="sxs-lookup"><span data-stu-id="912ef-152">Exchange rate direction</span></span>|<span data-ttu-id="912ef-153">**多对一**</span><span class="sxs-lookup"><span data-stu-id="912ef-153">**Many-to-one**</span></span>|<span data-ttu-id="912ef-154">**一对多**</span><span class="sxs-lookup"><span data-stu-id="912ef-154">**One-to-many**</span></span>|<span data-ttu-id="912ef-155">**多对多**</span><span class="sxs-lookup"><span data-stu-id="912ef-155">**Many-to-many**</span></span>|  
|<span data-ttu-id="912ef-156">**n 先导货币对 1 示例货币**</span><span class="sxs-lookup"><span data-stu-id="912ef-156">**n pivot currency to 1 sample currency**</span></span>|<span data-ttu-id="912ef-157">为将度量值换算为先导货币，需要将待换算度量值乘以本地货币的汇率度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-157">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="912ef-158">为将度量值换算为报表货币，需要将待换算度量值除以报表货币的汇率度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-158">Divide the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="912ef-159">将待换算度量值乘以本地货币的汇率度量值来将其换算为先导货币，然后将该换算后的度量值除以报表货币的汇率度量值来将其换算为报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-159">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then divide the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
|<span data-ttu-id="912ef-160">**n 示例货币对 1 先导货币**</span><span class="sxs-lookup"><span data-stu-id="912ef-160">**n sample currency to 1 pivot currency**</span></span>|<span data-ttu-id="912ef-161">为将度量值换算为先导货币，需要将待换算度量值除以本地货币的汇率度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-161">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="912ef-162">为将度量值换算为报表货币，需要将待换算度量值乘以报表货币的汇率度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-162">Multiply the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="912ef-163">将待换算度量值除以本地货币的汇率度量值来将其换算为先导货币，然后将该换算后的度量值乘以报表货币的汇率度量值来将其换算为报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-163">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then multiply the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
  
 <span data-ttu-id="912ef-164">您可以在商业智能向导的 **“设置货币换算选项”** 页上选择汇率方向。</span><span class="sxs-lookup"><span data-stu-id="912ef-164">You choose the exchange rate direction on the **Set currency conversion options** page of the Business Intelligence Wizard.</span></span> <span data-ttu-id="912ef-165">有关设置换算方向的详细信息，请参阅[设置货币换算选项（商业智能向导）](set-currency-conversion-options-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="912ef-165">For more information about setting conversion direction, see [Set Currency Conversion Options &#40;Business Intelligence Wizard&#41;](set-currency-conversion-options-business-intelligence-wizard.md).</span></span>  
  
### <a name="converted-members"></a><span data-ttu-id="912ef-166">待换算成员</span><span class="sxs-lookup"><span data-stu-id="912ef-166">Converted Members</span></span>  
 <span data-ttu-id="912ef-167">您可以使用商业智能向导来指定使用比率度量值组中的哪些度量值来为以下内容进行值换算：</span><span class="sxs-lookup"><span data-stu-id="912ef-167">You can use the Business Intelligence Wizard to specify which measures from the rate measure group are used to convert values for:</span></span>  
  
-   <span data-ttu-id="912ef-168">其他度量值组中的度量值。</span><span class="sxs-lookup"><span data-stu-id="912ef-168">Measures in other measure groups.</span></span>  
  
-   <span data-ttu-id="912ef-169">数据库维度中的帐户属性的属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="912ef-169">Members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
-   <span data-ttu-id="912ef-170">数据库维度中的帐户属性的属性层次结构的成员使用的帐户类型。</span><span class="sxs-lookup"><span data-stu-id="912ef-170">Account types, used by members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
 <span data-ttu-id="912ef-171">商业智能向导将此信息用于由向导生成的 MDX 脚本中来确定货币换算计算的作用域。</span><span class="sxs-lookup"><span data-stu-id="912ef-171">The Business Intelligence Wizard uses this information within the MDX script generated by the wizard to determine the scope of the currency conversion calculation.</span></span> <span data-ttu-id="912ef-172">有关为货币换算指定成员的详细信息，请参阅[选择成员（商业智能向导）](select-members-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="912ef-172">For more information about specifying members for currency conversion, see [Select Members &#40;Business Intelligence Wizard&#41;](select-members-business-intelligence-wizard.md).</span></span>  
  
### <a name="conversion-types"></a><span data-ttu-id="912ef-173">换算类型</span><span class="sxs-lookup"><span data-stu-id="912ef-173">Conversion Types</span></span>  
 <span data-ttu-id="912ef-174">商业智能向导支持三种不同类型的货币换算：</span><span class="sxs-lookup"><span data-stu-id="912ef-174">The Business Intelligence Wizard supports three different types of currency conversion:</span></span>  
  
-   <span data-ttu-id="912ef-175">**一对多**</span><span class="sxs-lookup"><span data-stu-id="912ef-175">**One-to-many**</span></span>  
  
     <span data-ttu-id="912ef-176">交易以先导货币存储在事实数据表中，然后换算为一种或多种其他报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-176">Transactions are stored in the fact table in the pivot currency, and then converted to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="912ef-177">例如，先导货币可以设置为美元 (USD)，而事实数据表使用 USD 来存储事务。</span><span class="sxs-lookup"><span data-stu-id="912ef-177">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="912ef-178">此换算类型将这些交易由先导货币换算为指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-178">This conversion type converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="912ef-179">因此，交易能够以指定的先导货币进行存储，并且能够以指定的先导货币或以在为货币换算定义的报表货币维度中指定的任意一种报表货币进行查看。</span><span class="sxs-lookup"><span data-stu-id="912ef-179">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any of the reporting currencies specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="912ef-180">**多对一**</span><span class="sxs-lookup"><span data-stu-id="912ef-180">**Many-to-one**</span></span>  
  
     <span data-ttu-id="912ef-181">交易以本地货币存储在事实数据表中，然后换算为先导货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-181">Transactions are stored in the fact table in local currencies, and then converted into the pivot currency.</span></span> <span data-ttu-id="912ef-182">先导货币充当报表货币维度中唯一指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-182">The pivot currency serves as the only specified reporting currency in the reporting currency dimension.</span></span>  
  
     <span data-ttu-id="912ef-183">例如，先导货币可以设置为美元 (USD)，而事实数据表使用欧元 (EUR)、澳大利亚元 (AUD) 和墨西哥比索 (MXN) 来存储交易。</span><span class="sxs-lookup"><span data-stu-id="912ef-183">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="912ef-184">此换算类型将这些交易由它们的指定本地货币换算为先导货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-184">This conversion type converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="912ef-185">因此，交易能够以指定的本地货币进行存储，并且能够以在为货币换算定义的报表货币维度中指定的先导货币进行查看。</span><span class="sxs-lookup"><span data-stu-id="912ef-185">The result is that transactions can be stored in the specified local currencies and viewed in the pivot currency, which is specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="912ef-186">**多对多**</span><span class="sxs-lookup"><span data-stu-id="912ef-186">**Many-to-many**</span></span>  
  
     <span data-ttu-id="912ef-187">交易以本地货币存储在事实数据表中。</span><span class="sxs-lookup"><span data-stu-id="912ef-187">Transactions are stored in the fact table in local currencies.</span></span> <span data-ttu-id="912ef-188">此种货币换算功能先将这类交易换算为先导货币，然后将其换算为一种或多种其他报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-188">The currency conversion functionality converts such transactions into the pivot currency, and then to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="912ef-189">例如，先导货币可以设置为美元 (USD)，而事实数据表使用欧元 (EUR)、澳大利亚元 (AUD) 和墨西哥比索 (MXN) 来存储交易。</span><span class="sxs-lookup"><span data-stu-id="912ef-189">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="912ef-190">此换算类型将这些交易由它们的指定本地货币换算为先导货币，然后再将这些已换算的交易由先导货币换算为指定的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-190">This conversion type converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="912ef-191">因此，交易能够以指定的本地货币进行存储，并且能够以指定的先导货币或以在为货币换算定义的报表货币维度中指定的任意一种报表货币进行查看。</span><span class="sxs-lookup"><span data-stu-id="912ef-191">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any of the reporting currencies that are specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
 <span data-ttu-id="912ef-192">指定换算类型将允许商业智能向导定义报表货币维度的命名查询和维度结构，还将允许其定义为货币换算定义的 MDX 脚本的结构。</span><span class="sxs-lookup"><span data-stu-id="912ef-192">Specifying the conversion type allows the Business Intelligence Wizard to define the named query and dimension structure of the reporting currency dimension, as well as the structure of the MDX script defined for the currency conversion.</span></span>  
  
### <a name="local-currencies"></a><span data-ttu-id="912ef-193">本地货币</span><span class="sxs-lookup"><span data-stu-id="912ef-193">Local Currencies</span></span>  
 <span data-ttu-id="912ef-194">如果您为自己的货币换算选择了多对多或多对一换算类型，则需要指定如何标识商业智能向导生成的 MDX 脚本执行货币换算计算时所使用的本地货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-194">If you choose a many-to-many or many-to-one conversion type for your currency conversion, you need to specify how to identify the local currencies from which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="912ef-195">可以用下面的两种方法之一来标识事实数据表中交易的本地货币：</span><span class="sxs-lookup"><span data-stu-id="912ef-195">The local currency for a transaction in a fact table can be identified in one of two ways:</span></span>  
  
-   <span data-ttu-id="912ef-196">度量值组包含一个到货币维度的常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-196">The measure group contains a regular dimension relationship to the currency dimension.</span></span> <span data-ttu-id="912ef-197">例如，在 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 示例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中，Internet Sales 度量值组有一个到 Currency 维度的常规维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-197">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="912ef-198">该度量值组的事实数据表包含一个外键列，该外键列引用该维度的维度表中的货币标识符。</span><span class="sxs-lookup"><span data-stu-id="912ef-198">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span> <span data-ttu-id="912ef-199">在这种情况下，您可以从由该度量值组引用的货币维度中选择此属性来为该度量值组标识事实数据表中交易的本地货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-199">In this case, you can select the attribute from the currency dimension that is referenced by the measure group to identify the local currency for transactions in the fact table for that measure group.</span></span> <span data-ttu-id="912ef-200">此种情况在银行应用程序中最常见，这类应用程序使用交易本身确定交易使用的货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-200">This situation most often occurs in banking applications, where the transaction itself determines the currency used within the transaction.</span></span>  
  
-   <span data-ttu-id="912ef-201">度量值组通过另一个直接引用货币维度的维度包含一个到货币维度的被引用维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-201">The measure group contains a referenced dimension relationship to the currency dimension, through another dimension that directly references the currency dimension.</span></span> <span data-ttu-id="912ef-202">例如，在 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 示例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中，“财务报表”度量值组与“货币”维度之间通过“单位”维度建立了引用维度关系。</span><span class="sxs-lookup"><span data-stu-id="912ef-202">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="912ef-203">该度量值组的事实数据表包含一个外键列，该列引用了 Organization 维度的维度表中的成员。</span><span class="sxs-lookup"><span data-stu-id="912ef-203">The fact table for that measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="912ef-204">反过来，“单位”维度的维度表也包含一个外键列，该外键列引用“货币”维度的维度表中的货币标识符。</span><span class="sxs-lookup"><span data-stu-id="912ef-204">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span> <span data-ttu-id="912ef-205">这种情况在财务报表应用程序中最常见，此类应用程序使用交易的位置或子公司来确定交易的货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-205">This situation most often occurs in financial reporting applications, where the location or subsidiary for a transaction determines the currency for the transaction.</span></span> <span data-ttu-id="912ef-206">在这种情况下，可以从业务实体的维度中选择引用货币维度的属性。</span><span class="sxs-lookup"><span data-stu-id="912ef-206">In this case, you can select the attribute that references the currency dimension from the dimension for the business entity.</span></span>  
  
### <a name="reporting-currencies"></a><span data-ttu-id="912ef-207">报表货币</span><span class="sxs-lookup"><span data-stu-id="912ef-207">Reporting Currencies</span></span>  
 <span data-ttu-id="912ef-208">如果您为自己的货币换算选择了多对多或一对多换算类型，则需要指定如何标识商业智能向导生成的 MDX 脚本执行货币换算计算时所使用的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-208">If you choose a many-to-many or one-to-many conversion type for your currency conversion, you need to specify the reporting currencies for which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="912ef-209">您可以指定与比率度量值组相关的货币维度的所有成员，也可以从该维度中选择单独的成员。</span><span class="sxs-lookup"><span data-stu-id="912ef-209">You can either specify all the members of the currency dimension related to the rate measure group, or select individual members from the dimension.</span></span>  
  
 <span data-ttu-id="912ef-210">商业智能向导将基于使用选定的报表货币从货币维度的维度表中构造的命名查询来创建一个报表货币维度。</span><span class="sxs-lookup"><span data-stu-id="912ef-210">The Business Intelligence Wizard creates a reporting currency dimension, based on a named query constructed from the dimension table for the currency dimension using the selected reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="912ef-211">如果您选择了一对多换算类型，则同时还创建一个报表货币维度。</span><span class="sxs-lookup"><span data-stu-id="912ef-211">If you select the one-to-many conversion type, a reporting currency dimension is also created.</span></span> <span data-ttu-id="912ef-212">该维度只包含一个代表先导货币的成员，这是因为先导货币也用作一对多货币换算的报表货币。</span><span class="sxs-lookup"><span data-stu-id="912ef-212">The dimension contains only one member representing the pivot currency, because the pivot currency is also used as the reporting currency for a one-to-many currency conversion.</span></span>  
  
 <span data-ttu-id="912ef-213">向导会为多维数据集中定义的每个货币换算分别定义一个报表货币维度。</span><span class="sxs-lookup"><span data-stu-id="912ef-213">A separate reporting currency dimension is defined for each currency conversion defined in a cube.</span></span> <span data-ttu-id="912ef-214">完成创建后，可以对报表货币维度的名称进行更改，但是如果这样做，您还必须更新为该货币换算生成的 MDX 脚本以确保脚本命令在引用报表货币维度时使用正确的名称。</span><span class="sxs-lookup"><span data-stu-id="912ef-214">You can change the name of the reporting currency dimensions after creation, but if you do so you must also update the MDX script generated for that currency conversion to ensure that the correct name is used by the script command when referencing the reporting currency dimension.</span></span>  
  
## <a name="defining-multiple-currency-conversions"></a><span data-ttu-id="912ef-215">定义多个货币换算</span><span class="sxs-lookup"><span data-stu-id="912ef-215">Defining Multiple Currency Conversions</span></span>  
 <span data-ttu-id="912ef-216">使用商业智能向导，您可以根据您的商业智能解决方案的需要定义尽可能多的货币换算。</span><span class="sxs-lookup"><span data-stu-id="912ef-216">Using the Business Intelligence Wizard, you can define as many currency conversions as needed for your business intelligence solution.</span></span> <span data-ttu-id="912ef-217">您可以覆盖一个现有的货币换算，也可以将一个新的货币换算追加到多维数据集的 MDX 脚本中。</span><span class="sxs-lookup"><span data-stu-id="912ef-217">You can either overwrite an existing currency conversion or append a new currency conversion to the MDX script for a cube.</span></span> <span data-ttu-id="912ef-218">在具有复杂的报表要求的商业智能应用程序（例如支持国际报表的多个独立换算要求的财务报表应用程序）中，定义于单个多维数据集中的多个货币换算提供了很大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="912ef-218">Multiple currency conversions defined in a single cube provide flexibility in business intelligence applications that have complex reporting requirements, such as financial reporting applications that support multiple, separate conversion requirements for international reporting.</span></span>  
  
### <a name="identifying-currency-conversions"></a><span data-ttu-id="912ef-219">标识货币换算</span><span class="sxs-lookup"><span data-stu-id="912ef-219">Identifying Currency Conversions</span></span>  
 <span data-ttu-id="912ef-220">商业智能向导通过将货币换算的脚本命令放置到下列注释框架中来标识各个货币换算。</span><span class="sxs-lookup"><span data-stu-id="912ef-220">The Business Intelligence Wizard identifies each currency conversion by framing the script commands for the currency conversion in the following comments:</span></span>  
  
 `//<Currency conversion>`  
  
 `...`  
  
 `[MDX statements for the currency conversion]`  
  
 `...`  
  
 `//</Currency conversion>`  
  
 <span data-ttu-id="912ef-221">如果您更改或删除了这些注释，则商业智能向导将不能检测到货币换算，因此您不应更改这些注释。</span><span class="sxs-lookup"><span data-stu-id="912ef-221">If you change or remove these comments, the Business Intelligence Wizard is unable to detect the currency conversion, so you should not change these comments.</span></span>  
  
 <span data-ttu-id="912ef-222">向导还将注释中的元数据存储在这些注释内，这包括创建日期和时间、用户及换算类型。</span><span class="sxs-lookup"><span data-stu-id="912ef-222">The wizard also stores metadata in comments within these comments, including the creation date and time, the user, and the conversion type.</span></span> <span data-ttu-id="912ef-223">您也不应当更改这些注释，因为在显示现有的货币换算时，商业智能向导使用此元数据。</span><span class="sxs-lookup"><span data-stu-id="912ef-223">These comments should also not be changed because the Business Intelligence Wizard uses this metadata when displaying existing currency conversions.</span></span>  
  
 <span data-ttu-id="912ef-224">若有必要，您可以更改包含在货币换算中的脚本命令。</span><span class="sxs-lookup"><span data-stu-id="912ef-224">You can change the script commands contained in a currency conversion as needed.</span></span> <span data-ttu-id="912ef-225">如果您覆盖了该货币换算，则您的更改将丢失。</span><span class="sxs-lookup"><span data-stu-id="912ef-225">If you overwrite the currency conversion, however, your changes will be lost.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ef-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="912ef-226">See Also</span></span>  
 [<span data-ttu-id="912ef-227">Analysis Services Multidimensional 的全球化方案</span><span class="sxs-lookup"><span data-stu-id="912ef-227">Globalization scenarios for Analysis Services Multiidimensional</span></span>](globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
  
