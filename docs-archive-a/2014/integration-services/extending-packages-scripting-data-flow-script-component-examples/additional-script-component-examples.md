---
title: 其他脚本组件示例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 897ca075674f5c3dbaf355390fe8346580bf638a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587921"
---
# <a name="additional-script-component-examples"></a><span data-ttu-id="bc7e2-102">其他脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="bc7e2-102">Additional Script Component Examples</span></span>
  <span data-ttu-id="bc7e2-103">脚本组件是一个可配置的工具，您可以在包的数据流中使用，它可以满足几乎所有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 附带的源、转换和目标所无法满足的要求。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-103">The Script component is a configurable tool that you can use in the data flow of a package to fill almost any requirement that is not met by the sources, transformations, and destinations that are included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="bc7e2-104">本节包含一些脚本组件代码示例，这些示例演示了各种类型的可用功能。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-104">This section contains Script component code samples that demonstrate the various types of functionality that are available.</span></span>  
  
 <span data-ttu-id="bc7e2-105">若要查看演示将脚本组件配置为基本的源、转换或目标的示例，请参阅[开发特定类型的脚本组件](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-105">For samples that demonstrate how to configure the Script component as a basic source, transformation, or destination, see [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc7e2-106">如果希望创建可更方便地重用于多个数据流文件和多个包的组件，请考虑以这些脚本组件示例中的代码为基础，创建自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-106">If you want to create components that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in these Script component samples as the starting point for custom data flow components.</span></span> <span data-ttu-id="bc7e2-107">有关详细信息，请参阅 [开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc7e2-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="bc7e2-108">In This Section</span></span>  
 [<span data-ttu-id="bc7e2-109">模拟脚本组件的错误输出</span><span class="sxs-lookup"><span data-stu-id="bc7e2-109">Simulating an Error Output for the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 <span data-ttu-id="bc7e2-110">脚本组件不支持标准错误输出，但您可以通过少量的其他配置和编码来模拟标准错误输出。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-110">The Script component does not support a standard error output, but you can simulate a standard error output with very little additional configuration and coding.</span></span>  
  
 [<span data-ttu-id="bc7e2-111">使用脚本组件增强错误输出</span><span class="sxs-lookup"><span data-stu-id="bc7e2-111">Enhancing an Error Output with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 <span data-ttu-id="bc7e2-112">说明并演示如何使用脚本组件来向标准错误输出添加其他信息。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-112">Explains and demonstrates how to add additional information to a standard error output by using the Script component.</span></span>  
  
 [<span data-ttu-id="bc7e2-113">使用脚本组件创建 ODBC 目标</span><span class="sxs-lookup"><span data-stu-id="bc7e2-113">Creating an ODBC Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 <span data-ttu-id="bc7e2-114">说明并演示如何使用脚本组件来创建 ODBC 数据流目标。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-114">Explains and demonstrates how to create an ODBC data flow destination by using the Script component.</span></span>  
  
 [<span data-ttu-id="bc7e2-115">使用脚本组件分析非标准文本文件格式</span><span class="sxs-lookup"><span data-stu-id="bc7e2-115">Parsing Non-Standard Text File Formats with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 <span data-ttu-id="bc7e2-116">说明并演示如何分析两种不同的非标准文本文件格式并将分析结果保存到目标表中。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-116">Explains and demonstrates how to parse two different non-standard text file formats into destination tables.</span></span>  
  
<span data-ttu-id="bc7e2-117">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="bc7e2-117">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bc7e2-118">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="bc7e2-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bc7e2-119">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="bc7e2-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bc7e2-120">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="bc7e2-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
