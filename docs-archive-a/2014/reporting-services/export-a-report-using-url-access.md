---
title: 使用 URL 访问导出报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69f340855e37ffde49aec0af096c094a142659d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682747"
---
# <a name="export-a-report-using-url-access"></a><span data-ttu-id="18dc6-102">使用 URL 访问导出报表</span><span class="sxs-lookup"><span data-stu-id="18dc6-102">Export a Report Using URL Access</span></span>
  <span data-ttu-id="18dc6-103">您可以选择使用*rs： format*参数指定呈现报表的格式。</span><span class="sxs-lookup"><span data-stu-id="18dc6-103">You can optionally specify the format in which to render a report by using the *rs:Format* parameter.</span></span> <span data-ttu-id="18dc6-104">例如，若要直接从本机模式报表服务器获取报表的 PDF 副本：</span><span class="sxs-lookup"><span data-stu-id="18dc6-104">For example, to get a PDF copy of a report directly from a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 <span data-ttu-id="18dc6-105">此外，若要从 SharePoint 集成模式的报表服务器获取：</span><span class="sxs-lookup"><span data-stu-id="18dc6-105">And, from a SharePoint integrated mode report server:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 <span data-ttu-id="18dc6-106">对于此参数，有效值为何随要访问的报表服务器上所安装的报表呈现扩展插件而异。</span><span class="sxs-lookup"><span data-stu-id="18dc6-106">Valid values for this parameter are based on the report rendering extensions that are installed on the report server being accessed.</span></span> <span data-ttu-id="18dc6-107">常见的扩展插件有 HTML4.0、MHTML、IMAGE、EXCEL、WORD、CSV、PDF、XML 和 NULL。</span><span class="sxs-lookup"><span data-stu-id="18dc6-107">Common extensions are HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML, and NULL.</span></span> <span data-ttu-id="18dc6-108">如果指定的呈现扩展插件未安装在相应的报表服务器上，则相应报表将不能呈现，并将生成错误，同时通过浏览器来显示该错误。</span><span class="sxs-lookup"><span data-stu-id="18dc6-108">If a specified rendering extension is not installed on the report server, the report is not rendered and an error is generated and displayed in the browser.</span></span>  
  
 <span data-ttu-id="18dc6-109">如果未在 URL 中纳入 *Format* 参数，则报表服务器将检测浏览器，并将相应报表呈现为合适的 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="18dc6-109">If you do not include the *Format* parameter as part of the URL, the report server detects the browser and renders the report in the appropriate HTML format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18dc6-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18dc6-110">See Also</span></span>  
 <span data-ttu-id="18dc6-111">[&#40;SSRS&#41;的 URL 访问](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="18dc6-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="18dc6-112">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="18dc6-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
