---
title: 设置报表或文本框的区域设置 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb2b0cbd6e4216138520834216358ee455729386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578631"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a><span data-ttu-id="da04b-102">设置报表或文本框的区域设置 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="da04b-102">Set the Locale for a Report or Text Box (Reporting Services)</span></span>
  <span data-ttu-id="da04b-103">报表或文本框的 **“语言”** 属性包含区域设置，该区域设置确定因语言和区域而异的默认报表数据显示格式，例如日期、货币或数值。</span><span class="sxs-lookup"><span data-stu-id="da04b-103">The **Language** property on a report or a text box contains the locale setting, which determines the default formats for displaying report data that differ by language and region, for example, date, currency, or number values.</span></span> <span data-ttu-id="da04b-104">文本框的 **“语言”** 属性会覆盖报表的 **“语言”** 属性。</span><span class="sxs-lookup"><span data-stu-id="da04b-104">The **Language** property on a text box overrides the **Language** property on the report.</span></span> <span data-ttu-id="da04b-105">如果不为 **“语言”** 指定值，则 Reporting Services 将使用报表服务器所用操作系统的区域设置来发布报表，或使用报表创作计算机的区域设置来预览报表。</span><span class="sxs-lookup"><span data-stu-id="da04b-105">If no value is specified for **Language**, Reporting Services uses the locale of the operating system on the report server for published reports or of the report authoring computer for report preview.</span></span>  
  
 <span data-ttu-id="da04b-106">对于 HTML 报表，您可以覆盖默认 **“语言”** 值，而使用浏览器客户端的 HTTP 标头所指定的语言，方法是对报表或文本框的 **“语言”** 属性使用包含内置字段 User!Language 的表达式。</span><span class="sxs-lookup"><span data-stu-id="da04b-106">For HTML reports, you can override the default **Language** value and use the language specified by the HTTP header of the browser client by using the built-in field User!Language in an expression for the **Language** property of a report or a text box.</span></span>  
  
 <span data-ttu-id="da04b-107">您还可以在 URL 中指定报表的 **“语言”** 属性。</span><span class="sxs-lookup"><span data-stu-id="da04b-107">You can also specify the **Language** property for a report in a URL.</span></span> <span data-ttu-id="da04b-108">有关详细信息，请参阅 [设置 URL 中的报表语言参数](../set-the-language-for-report-parameters-in-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="da04b-108">For more information, see [Set the Language for Report Parameters in a URL](../set-the-language-for-report-parameters-in-a-url.md).</span></span>  
  
### <a name="to-set-the-locale-for-a-report"></a><span data-ttu-id="da04b-109">设置报表的区域设置</span><span class="sxs-lookup"><span data-stu-id="da04b-109">To set the locale for a report</span></span>  
  
1.  <span data-ttu-id="da04b-110">在“设计”视图中，单击报表设计图面的外部以选中该报表。</span><span class="sxs-lookup"><span data-stu-id="da04b-110">In Design view, click outside the report design surface to select the report.</span></span>  
  
2.  <span data-ttu-id="da04b-111">在“属性”窗格中，对于 **“语言”** 属性，键入或选择希望报表使用的语言。</span><span class="sxs-lookup"><span data-stu-id="da04b-111">In the Properties pane, for the **Language** property, type or select the language that you want to use for the report.</span></span>  
  
### <a name="to-set-the-locale-for-a-text-box"></a><span data-ttu-id="da04b-112">设置文本框的区域设置</span><span class="sxs-lookup"><span data-stu-id="da04b-112">To set the locale for a text box</span></span>  
  
1.  <span data-ttu-id="da04b-113">在“设计”视图中，选择要对其应用区域设置的文本框。</span><span class="sxs-lookup"><span data-stu-id="da04b-113">In Design view, select the text box to which you want to apply the locale settings.</span></span>  
  
2.  <span data-ttu-id="da04b-114">在“属性”窗格中，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="da04b-114">In the Properties pane, do the following:</span></span>  
  
    -   <span data-ttu-id="da04b-115">对于 **“日历”** 属性，键入或选择希望日期所要使用的日历。</span><span class="sxs-lookup"><span data-stu-id="da04b-115">For the **Calendar** property, type or select the calendar that you want to use for dates.</span></span>  
  
    -   <span data-ttu-id="da04b-116">对于 **“方向”** 属性，键入或选择写入文本的方向。</span><span class="sxs-lookup"><span data-stu-id="da04b-116">For the **Direction** property, type or select the direction in which the text is written.</span></span>  
  
    -   <span data-ttu-id="da04b-117">对于 **“语言”** 属性，键入或选择希望文本框所要使用的语言。</span><span class="sxs-lookup"><span data-stu-id="da04b-117">For the **Language** property, type or select the language that you want to use for the text box.</span></span> <span data-ttu-id="da04b-118">此值将覆盖报表的 **“语言”** 属性。</span><span class="sxs-lookup"><span data-stu-id="da04b-118">This value overrides the **Language** property for the Report.</span></span>  
  
    -   <span data-ttu-id="da04b-119">对于 **NumeralLanguage** 属性，键入或选择文本框中的数字所要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="da04b-119">For the **NumeralLanguage** property, type or select the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="da04b-120">对于 **NumeralVariant** 属性，键入或选择要用于文本框中的数字的格式变量。</span><span class="sxs-lookup"><span data-stu-id="da04b-120">For the **NumeralVariant** property, type or select the variant of the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="da04b-121">对于 **UnicodeBiDi** 属性，选择要在文本框中使用的双向嵌入级别。</span><span class="sxs-lookup"><span data-stu-id="da04b-121">For the **UnicodeBiDi** property, select the level of bidirectional embedding to use in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da04b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da04b-122">See Also</span></span>  
 [<span data-ttu-id="da04b-123">在报表中使用表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="da04b-123">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
