---
title: 使用 URL 访问呈现报表历史记录快照 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 67854a39ab7e38289627d03ac00cc4b2a6dca6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586488"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a><span data-ttu-id="53d0c-102">使用 URL 访问呈现报表历史记录快照</span><span class="sxs-lookup"><span data-stu-id="53d0c-102">Render a Report History Snapshot Using URL Access</span></span>
  <span data-ttu-id="53d0c-103">您可以通过提供 *rs:Snapshot* 参数并将其值设置为有效的快照 ID，基于报表历史记录快照呈现报表。</span><span class="sxs-lookup"><span data-stu-id="53d0c-103">You can render a report based on a report history snapshot by supplying the *rs:Snapshot* parameter and setting its value to a valid snapshot ID.</span></span> <span data-ttu-id="53d0c-104">参数值采用 YYYY-MM-DDTHH:MM:SS 格式，该格式基于国际标准化组织 (ISO) 8601 标准。</span><span class="sxs-lookup"><span data-stu-id="53d0c-104">The parameter value is in the format YYYY-MM-DDTHH:MM:SS, based on the International Organization for Standardization (ISO) 8601 standard.</span></span>  
  
 <span data-ttu-id="53d0c-105">如果省略此参数，则报表将根据报表服务器的报表执行和缓存管理选项设置呈现。</span><span class="sxs-lookup"><span data-stu-id="53d0c-105">If you omit this parameter, the report is rendered according to the report execution and cache management option settings of the report server.</span></span> <span data-ttu-id="53d0c-106">有关报表执行的详细信息，请参阅 [设置报表处理属性](report-server/set-report-processing-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="53d0c-106">For more information about report execution, see [Set Report Processing Properties](report-server/set-report-processing-properties.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53d0c-107">示例</span><span class="sxs-lookup"><span data-stu-id="53d0c-107">Example</span></span>  
 <span data-ttu-id="53d0c-108">下面的示例说明检索历史记录快照的 URL：</span><span class="sxs-lookup"><span data-stu-id="53d0c-108">The following example shows a URL that retrieves a report history snapshot:</span></span>  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a><span data-ttu-id="53d0c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53d0c-109">See Also</span></span>  
 <span data-ttu-id="53d0c-110">[URL 访问 (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="53d0c-110">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="53d0c-111">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="53d0c-111">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
