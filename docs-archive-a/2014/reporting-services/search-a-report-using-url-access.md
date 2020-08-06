---
title: 使用 URL 访问搜索报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b45f3fabf58a0980d41ee7b4b89a771655477d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692676"
---
# <a name="search-a-report-using-url-access"></a><span data-ttu-id="e8716-102">使用 URL 访问搜索报表</span><span class="sxs-lookup"><span data-stu-id="e8716-102">Search a Report Using URL Access</span></span>
  <span data-ttu-id="e8716-103">可以使用 URL 访问在报表中搜索一组特定的文本。</span><span class="sxs-lookup"><span data-stu-id="e8716-103">You can search a report for a specific set of text using URL access.</span></span> <span data-ttu-id="e8716-104">若要在报表中搜索，请将 URL 中的 *rc:FindString* 参数的值设置为等于所要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="e8716-104">To search a report, set the value of the *rc:FindString* parameter on the URL equal to the text for which you want to search.</span></span> <span data-ttu-id="e8716-105">另外，可以使用 *rc:StartFind* 和 *rc:EndFind* 参数将搜索范围缩小到相应报表中的特定页。</span><span class="sxs-lookup"><span data-stu-id="e8716-105">Additionally, use the *rc:StartFind* and *rc:EndFind* parameters to narrow your search to specific pages within the report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8716-106">示例</span><span class="sxs-lookup"><span data-stu-id="e8716-106">Example</span></span>  
 <span data-ttu-id="e8716-107">下面的 URL 访问示例在 Product Catalog 示例报表的第 1 页到第 5 页之间搜索第一条“Mountain-400”文本：</span><span class="sxs-lookup"><span data-stu-id="e8716-107">The following URL access example searches for the first occurrence of the text "Mountain-400" in the Product Catalog sample report starting with page one and ending with page five:</span></span>  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8716-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8716-108">See Also</span></span>  
 <span data-ttu-id="e8716-109">[URL 访问 (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e8716-109">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="e8716-110">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="e8716-110">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
