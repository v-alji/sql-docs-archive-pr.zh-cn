---
title: Integration Services)&#39;的新 (Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84f0b668407c89e1d6acc3c8cfbda73f129ca19a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590260"
---
# <a name="what39s-new-integration-services"></a><span data-ttu-id="53bc4-102">新增 (Integration Services&#39;) </span><span class="sxs-lookup"><span data-stu-id="53bc4-102">What&#39;s New (Integration Services)</span></span>
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="53bc4-103">与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 上一版本保持不变。</span><span class="sxs-lookup"><span data-stu-id="53bc4-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is unchanged from the previous release.</span></span>  
  
 <span data-ttu-id="53bc4-104">有关其他 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 产品和技术的信息，请参阅[SQL Server 2014 中的新增功能](../sql-server/what-s-new-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="53bc4-104">For information about other [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] products and technologies, see [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="53bc4-105">有关与商业智能相关的更改的详细信息 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅[Analysis Services 和商业智能中的新增功能](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="53bc4-105">For more information about changes related to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, see [What's New in Analysis Services and Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services).</span></span>  
  
##  <a name="rich-xml-validation-output-in-the-xml-task"></a><a name="ValidateXML"></a> <span data-ttu-id="53bc4-106">XML 任务中丰富的 XML 验证输出</span><span class="sxs-lookup"><span data-stu-id="53bc4-106">Rich XML validation output in the XML Task</span></span>  
 <span data-ttu-id="53bc4-107">通过启用 XML 任务的 `ValidationDetails` 属性，验证 XML 文档并获取丰富的错误输出。</span><span class="sxs-lookup"><span data-stu-id="53bc4-107">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span> <span data-ttu-id="53bc4-108">在可以使用 `ValidationDetails` 属性之前，XML 任务的 XML 验证仅返回 true 或 false 结果，而不包含关于错误或其位置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="53bc4-108">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="53bc4-109">现在，当你将 `ValidationDetails` 设置为 true 时，输出文件将包含关于每个错误的详细信息，包括行号和位置。</span><span class="sxs-lookup"><span data-stu-id="53bc4-109">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="53bc4-110">此信息可用于了解、查找和修复 XML 文档中的错误。</span><span class="sxs-lookup"><span data-stu-id="53bc4-110">You can use this information to understand, locate, and fix errors in XML documents.</span></span> <span data-ttu-id="53bc4-111">有关详细信息，请参阅 [Validate XML with the XML Task](control-flow/xml-task.md)。</span><span class="sxs-lookup"><span data-stu-id="53bc4-111">For more info, see [Validate XML with the XML Task](control-flow/xml-task.md).</span></span>  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="53bc4-112">介绍了 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2 中的 `ValidationDetails` 属性。</span><span class="sxs-lookup"><span data-stu-id="53bc4-112">introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="53bc4-113">此时尚未公布或记录这一新属性。</span><span class="sxs-lookup"><span data-stu-id="53bc4-113">This new property was not announced or documented at that time.</span></span> <span data-ttu-id="53bc4-114">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 和 SQL Server 2016 中也可使用 `ValidationDetails` 属性。</span><span class="sxs-lookup"><span data-stu-id="53bc4-114">The `ValidationDetails` property is also available in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bc4-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53bc4-115">See Also</span></span>  
 [<span data-ttu-id="53bc4-116">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="53bc4-116">Features Supported by the Editions of SQL Server 2014</span></span>](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
