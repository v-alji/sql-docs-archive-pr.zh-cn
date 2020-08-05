---
title: 内联工作负荷的 XML 输入文件示例 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93b2ab4279378b4cd392d97a9b65f299d0e9c6dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580485"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a><span data-ttu-id="2b593-102">内联工作负荷的 XML 输入文件示例 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2b593-102">XML Input File Sample with Inline Workload (DTA)</span></span>
  <span data-ttu-id="2b593-103">复制以下 XML 输入文件的示例（其中使用 **EventString** 元素指定了一个工作负荷），并将其粘贴到常用的 XML 编辑器或文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="2b593-103">Copy and paste this sample of an XML input file that specifies a workload with the **EventString** element into your favorite XML editor or text editor.</span></span> <span data-ttu-id="2b593-104">您可以在 XML 输入文件中使用 **EventString** 元素指定一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本工作负荷，而不必使用单独的工作负荷文件。</span><span class="sxs-lookup"><span data-stu-id="2b593-104">You can use the **EventString** element to specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload in the XML input file instead of using a separate workload file.</span></span> <span data-ttu-id="2b593-105">将此示例复制到编辑工具中后，将为 **服务器**、 **数据库**、 **架构**、 **表**、 **工作负荷**、 **EventString**和 **TuningOptions** 元素指定的值，替换为具体的优化会话所用的值。</span><span class="sxs-lookup"><span data-stu-id="2b593-105">After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**, and **TuningOptions** elements with those for your specific tuning session.</span></span> <span data-ttu-id="2b593-106">有关可以与这些元素一起使用的所有属性和子元素的详细信息，请参阅 [XML 输入文件引用（数据库引擎优化顾问）](xml-input-file-reference-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="2b593-106">For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="2b593-107">以下示例只使用了部分可用属性和子元素选项。</span><span class="sxs-lookup"><span data-stu-id="2b593-107">The following sample uses only a subset of available attribute and child element options.</span></span>  
  
## <a name="code"></a><span data-ttu-id="2b593-108">代码</span><span class="sxs-lookup"><span data-stu-id="2b593-108">Code</span></span>  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#inlineworkloadinputfile)]  
  
## <a name="comments"></a><span data-ttu-id="2b593-109">注释</span><span class="sxs-lookup"><span data-stu-id="2b593-109">Comments</span></span>  
 <span data-ttu-id="2b593-110">`USE database_name` EventString **EventString** 语句。</span><span class="sxs-lookup"><span data-stu-id="2b593-110">`USE database_name` statements can be specified in the inline workload that is contained in the **EventString** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b593-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b593-111">See Also</span></span>  
 <span data-ttu-id="2b593-112">[启动并使用数据库引擎优化顾问](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="2b593-112">[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="2b593-113">[查看和使用数据库引擎优化顾问的输出](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="2b593-113">[View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="2b593-114">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="2b593-114">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
