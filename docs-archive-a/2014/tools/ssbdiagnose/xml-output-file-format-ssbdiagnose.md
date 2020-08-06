---
title: " (ssbdiagnose) 的 XML 输出文件格式 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 612b317f7220f502faf1adc82cf9c1dcc8bc20a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691424"
---
# <a name="xml-output-file-format-ssbdiagnose"></a><span data-ttu-id="b2360-102">XML 输出文件格式 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="b2360-102">XML Output File Format (ssbdiagnose)</span></span>
  <span data-ttu-id="b2360-103">通过 **-XML** 开关运行 **ssbdiagnose** 实用工具时，该实用工具会将其结果输出为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="b2360-103">The **ssbdiagnose** utility delivers its output as an XML file when you run it with the **-XML** switch.</span></span> <span data-ttu-id="b2360-104">XML 输出文件将列出在分析 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 配置或会话时发现的标头信息和错误。</span><span class="sxs-lookup"><span data-stu-id="b2360-104">The XML output file lists header information and the errors that it found in the [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration or conversation that was analyzed.</span></span> <span data-ttu-id="b2360-105">您可以编写应用程序分析或报告文件中列出的错误。</span><span class="sxs-lookup"><span data-stu-id="b2360-105">You can write an application to analyze or report on the errors listed in the file.</span></span> <span data-ttu-id="b2360-106">或者，您还可以在常规 XML 编辑器（如 XML Notepad）中查看该 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="b2360-106">Or, you can view the XML file in a general XML editor, such as XML Notepad.</span></span>  
  
 <span data-ttu-id="b2360-107">**ssbdiangose** 输出文件包含具有两种子类型的 DiagnosticInformation 根元素：</span><span class="sxs-lookup"><span data-stu-id="b2360-107">An **ssbdiangose** output file contains a DiagnosticInformation root element with two child types:</span></span>  
  
-   <span data-ttu-id="b2360-108">带有标头信息的 Banner 元素。</span><span class="sxs-lookup"><span data-stu-id="b2360-108">A Banner element with header information.</span></span>  
  
-   <span data-ttu-id="b2360-109">**ssbdiagnose**报告的每个问题对应的 Issue 元素。</span><span class="sxs-lookup"><span data-stu-id="b2360-109">An Issue element for each issue that is reported by **ssbdiagnose**.</span></span>  
  
## <a name="diagnosticinformation-root-element"></a><span data-ttu-id="b2360-110">DiagnosticInformation 根元素</span><span class="sxs-lookup"><span data-stu-id="b2360-110">DiagnosticInformation Root Element</span></span>  
  
-   [<span data-ttu-id="b2360-111">DiagnosticInformation 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="b2360-111">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a><span data-ttu-id="b2360-112">Banner 元素</span><span class="sxs-lookup"><span data-stu-id="b2360-112">Banner Element</span></span>  
  
-   [<span data-ttu-id="b2360-113">Banner 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="b2360-113">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a><span data-ttu-id="b2360-114">Issue 元素</span><span class="sxs-lookup"><span data-stu-id="b2360-114">Issue Element</span></span>  
  
-   [<span data-ttu-id="b2360-115">Issue 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="b2360-115">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2360-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2360-116">See Also</span></span>  
 [<span data-ttu-id="b2360-117">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="b2360-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
