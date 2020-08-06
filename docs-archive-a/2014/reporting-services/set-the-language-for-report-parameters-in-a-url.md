---
title: 设置 URL 中的报表参数语言 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8087a181906517bb60d4cd6839eed0681f52a5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689764"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a><span data-ttu-id="d8736-102">设置 URL 中的报表语言参数</span><span class="sxs-lookup"><span data-stu-id="d8736-102">Set the Language for Report Parameters in a URL</span></span>
  <span data-ttu-id="d8736-103">*rs:ParameterLanguage* URL 访问参数可以缓解与使用浏览器语言解释区分区域性的报表参数（如日期、时间、货币和数字）相关的问题。</span><span class="sxs-lookup"><span data-stu-id="d8736-103">The *rs:ParameterLanguage* URL access parameter alleviates a problem in which culture-sensitive report parameters, such as dates, times, currency, and numbers, are interpreted using the browser language.</span></span> <span data-ttu-id="d8736-104">借助于 *rs:ParameterLanguage*，现在可以独立于浏览器解释 URL。</span><span class="sxs-lookup"><span data-stu-id="d8736-104">With *rs:ParameterLanguage*, the URL is now interpreted independently of the browser.</span></span> <span data-ttu-id="d8736-105">例如，如果报表服务器设置为区域设置“德语”，但用户正在使用设置为“英语-美国”的浏览器通过 URL 访问某个报表，则将以错误的方式解释传递到报表服务器的参数值。</span><span class="sxs-lookup"><span data-stu-id="d8736-105">For example, if the report server is set to a regional setting of German, but a user is accessing a report via a URL using a browser that is set to English-United States, parameter values that are passed to a report server will be misinterpreted.</span></span>  
  
 <span data-ttu-id="d8736-106">请看指向某个报表的以下 URL：</span><span class="sxs-lookup"><span data-stu-id="d8736-106">Consider the following URL to a report:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 <span data-ttu-id="d8736-107">在上述情况下，在区域性“de-de”下运行的服务器通过电子邮件订阅或超链接生成一个 URL。</span><span class="sxs-lookup"><span data-stu-id="d8736-107">In the above case, the server, running under a culture of "de-de", generates a URL either through an e-mail subscription or a hyperlink.</span></span> <span data-ttu-id="d8736-108">超链接指示应根据德语日期/时间标准，按照开始日期 2008 年 10 月 4 日和结束日期 2008 年 10 月 11 日对报表进行参数化。</span><span class="sxs-lookup"><span data-stu-id="d8736-108">The hyperlink indicates that the report should be parameterized by a start date of October 4, 2008 and an end date of October 11, 2008 according to German date/time standards.</span></span> <span data-ttu-id="d8736-109">然而，通过设置为“en-us”的浏览器访问此 URL 的用户会强制服务器按照美国英语日期/时间标准将值解释为 2008 年 4 月 10 日和 2008 年 11 月 10 日。</span><span class="sxs-lookup"><span data-stu-id="d8736-109">However, a user that is accessing the URL through a browser set to "en-us" forces the server to interpret the values as April 10, 2008 and November 10, 2008 under United States English date/time standards.</span></span> <span data-ttu-id="d8736-110">为了解决这一问题，可以使用 *rs:ParameterLanguage* 覆盖浏览器语言以进行参数解释。</span><span class="sxs-lookup"><span data-stu-id="d8736-110">To fix the problem, *rs:ParameterLanguage* can be used to override the browser language for parameter interpretation:</span></span>  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 <span data-ttu-id="d8736-111">除了 URL 访问参数 **rc:Parameters** 的值 **true** 和 *false*之外，您现在可以传递值 **Collapsed**。</span><span class="sxs-lookup"><span data-stu-id="d8736-111">In addition to a value of **true** and **false** for the URL access parameter *rc:Parameters*, you can now pass a value of **Collapsed**.</span></span> <span data-ttu-id="d8736-112">对于某个 URL 使用 *rc:Parameters*=**Collapsed** 时，HTML 查看器的参数提示区域将折叠到视线之外，但用户仍可以进行切换。</span><span class="sxs-lookup"><span data-stu-id="d8736-112">When using *rc:Parameters*=**Collapsed** on a URL, the parameter prompt area of the HTML viewer is collapsed out of sight, but can still be toggled by the user.</span></span> <span data-ttu-id="d8736-113">值为 **false** 时，将从 HTML 查看器工具栏删除参数提示区域并使其无法供最终用户使用。</span><span class="sxs-lookup"><span data-stu-id="d8736-113">A value of **false** removes the parameter prompt area from the HTML viewer toolbar and makes it unavailable to the end-user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8736-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8736-114">See Also</span></span>  
 <span data-ttu-id="d8736-115">[URL 访问 (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8736-115">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="d8736-116">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="d8736-116">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
