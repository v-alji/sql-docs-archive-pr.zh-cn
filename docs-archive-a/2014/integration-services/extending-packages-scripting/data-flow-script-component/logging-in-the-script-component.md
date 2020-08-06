---
title: 脚本组件中的日志记录 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c29dfffee6cacb39272aef07caa5539555cdd4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587906"
---
# <a name="logging-in-the-script-component"></a><span data-ttu-id="1a57b-102">脚本组件中的日志记录</span><span class="sxs-lookup"><span data-stu-id="1a57b-102">Logging in the Script Component</span></span>
  <span data-ttu-id="1a57b-103">使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包中的日志记录可以记录预定义的事件或用户定义的消息，从而将有关执行进度、结果和问题的详细信息保存下来，以供日后分析。</span><span class="sxs-lookup"><span data-stu-id="1a57b-103">Logging in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages lets you save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="1a57b-104">脚本组件可以使用 `ScriptMain` 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法记录用户定义的数据。</span><span class="sxs-lookup"><span data-stu-id="1a57b-104">The Script component can use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class to log user-defined data.</span></span> <span data-ttu-id="1a57b-105">如果启用了日志记录，并且已选择 ScriptComponentLogEntry 事件登录“配置 SSIS 日志”对话框的“详细信息”选项卡，调用一次 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法会将事件信息存储在为数据流任务配置的所有日志提供程序中。</span><span class="sxs-lookup"><span data-stu-id="1a57b-105">If logging is enabled, and the **ScriptComponentLogEntry** event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box, a single call to the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method stores the event information in all the log providers that have been configured for the data flow task.</span></span>  
  
 <span data-ttu-id="1a57b-106">下面是一个简单的日志记录示例：</span><span class="sxs-lookup"><span data-stu-id="1a57b-106">Here is a simple example of logging:</span></span>  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  <span data-ttu-id="1a57b-107">尽管可以直接从脚本组件执行日志记录，但是您可能希望考虑实现事件，而不是日志记录。</span><span class="sxs-lookup"><span data-stu-id="1a57b-107">Although you can perform logging directly from your Script component, you may want to consider implementing events rather than logging.</span></span> <span data-ttu-id="1a57b-108">如果使用事件，不仅能够启用事件消息的日志记录，而且能够通过默认的或用户定义的事件处理程序响应事件。</span><span class="sxs-lookup"><span data-stu-id="1a57b-108">When using events, not only can you enable the logging of event messages, but you can respond to the event with default or user-defined event handlers.</span></span>  
  
 <span data-ttu-id="1a57b-109">有关日志记录的详细信息，请参阅 [Integration Services (SSIS) 日志记录](../../performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="1a57b-109">For more information about logging, see [Integration Services &#40;SSIS&#41; Logging](../../performance/integration-services-ssis-logging.md).</span></span>  
  
<span data-ttu-id="1a57b-110">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1a57b-110">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1a57b-111">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1a57b-111">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1a57b-112">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1a57b-112">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1a57b-113">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1a57b-113">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a57b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a57b-114">See Also</span></span>  
 [<span data-ttu-id="1a57b-115">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="1a57b-115">Integration Services &#40;SSIS&#41; Logging</span></span>](../../performance/integration-services-ssis-logging.md)  
  
  
