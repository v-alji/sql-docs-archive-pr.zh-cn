---
title: 在脚本任务中引发事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e20a276b91e434b6915cfb218eba17c07acd6544
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689521"
---
# <a name="raising-events-in-the-script-task"></a><span data-ttu-id="9e3bc-102">在脚本任务中引发事件</span><span class="sxs-lookup"><span data-stu-id="9e3bc-102">Raising Events in the Script Task</span></span>
  <span data-ttu-id="9e3bc-103">事件提供向包含包报告错误、警告和其他信息（如任务进度或状态）的方式。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="9e3bc-104">包为管理事件通知提供事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="9e3bc-105">脚本任务可以通过对 `Dts` 对象的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 属性调用方法来引发事件。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-105">The Script task can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="9e3bc-106">有关 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包如何处理事件的详细信息，请参阅 [Integration Services (SSIS) 事件处理程序](../../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="9e3bc-107">事件可以记录到包中已启用的任何日志提供程序中。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="9e3bc-108">日志提供程序在数据存储区中存储有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="9e3bc-109">脚本任务还可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法将信息记录到日志提供程序中而不引发事件。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-109">The Script task can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="9e3bc-110">有关如何使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法的详细信息，请参阅[脚本任务中的日志记录](logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method, see [Logging in the Script Task](logging-in-the-script-task.md).</span></span>  
  
 <span data-ttu-id="9e3bc-111">为了引发事件，脚本任务将调用由 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 属性公开的方法之一。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-111">To raise an event, the Script task calls one of the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span> <span data-ttu-id="9e3bc-112">下表列出了由 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 属性公开的方法。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-112">The following table lists the methods exposed by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
|<span data-ttu-id="9e3bc-113">事件</span><span class="sxs-lookup"><span data-stu-id="9e3bc-113">Event</span></span>|<span data-ttu-id="9e3bc-114">说明</span><span class="sxs-lookup"><span data-stu-id="9e3bc-114">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|<span data-ttu-id="9e3bc-115">引发包中用户定义的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-115">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|<span data-ttu-id="9e3bc-116">将错误情况通知包。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-116">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|<span data-ttu-id="9e3bc-117">为用户提供信息。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-117">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|<span data-ttu-id="9e3bc-118">将任务的进度通知包。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-118">Informs the package of the progress of the task.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|<span data-ttu-id="9e3bc-119">返回一个指示包是否需要提前关闭任务的值。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-119">Returns a value that indicates whether the package needs the task to shut down prematurely.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|<span data-ttu-id="9e3bc-120">向包发出通知：任务处于有必要发出用户通知，但不是错误条件的状态。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-120">Informs the package that the task is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
## <a name="events-example"></a><span data-ttu-id="9e3bc-121">事件示例</span><span class="sxs-lookup"><span data-stu-id="9e3bc-121">Events Example</span></span>  
 <span data-ttu-id="9e3bc-122">下面的示例演示如何从脚本任务内部引发事件。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-122">The following example demonstrates how to raise events from within the Script task.</span></span> <span data-ttu-id="9e3bc-123">该示例使用本机 Windows API 函数确定 Internet 连接是否可用。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-123">The example uses a native Windows API function to determine whether an Internet connection is available.</span></span> <span data-ttu-id="9e3bc-124">如果没有可用的连接，则引发错误。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-124">If no connection is available, it raises an error.</span></span> <span data-ttu-id="9e3bc-125">如果使用的调制解调器连接可能不稳定，则该示例将引发警告。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-125">If a potentially volatile modem connection is in use, the example raises a warning.</span></span> <span data-ttu-id="9e3bc-126">否则，返回已检测到 Internet 连接的信息性消息。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-126">Otherwise, it returns an informational message that an Internet connection has been detected.</span></span>  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
<span data-ttu-id="9e3bc-127">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9e3bc-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9e3bc-128">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="9e3bc-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9e3bc-129">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="9e3bc-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9e3bc-130">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="9e3bc-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3bc-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e3bc-131">See Also</span></span>  
 <span data-ttu-id="9e3bc-132">[Integration Services (SSIS) 事件处理程序](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="9e3bc-132">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="9e3bc-133">在包中添加事件处理程序</span><span class="sxs-lookup"><span data-stu-id="9e3bc-133">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
