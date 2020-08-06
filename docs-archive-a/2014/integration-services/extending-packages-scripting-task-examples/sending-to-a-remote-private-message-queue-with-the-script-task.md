---
title: 使用脚本任务向远程私有消息队列发送消息 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 308815293dfc41f0a0ac60c21ce7f561a5e7f660
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689942"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a><span data-ttu-id="6daa3-102">使用脚本任务向远程私有消息队列发送消息</span><span class="sxs-lookup"><span data-stu-id="6daa3-102">Sending to a Remote Private Message Queue with the Script Task</span></span>
  <span data-ttu-id="6daa3-103">消息队列（又称为 MSMQ）使开发人员可以通过发送和接收消息，轻松实现与应用程序之间的快速可靠通信。</span><span class="sxs-lookup"><span data-stu-id="6daa3-103">Message Queuing (also known as MSMQ) makes it easy for developers to communicate with application programs quickly and reliably by sending and receiving messages.</span></span> <span data-ttu-id="6daa3-104">消息队列既可位于本地计算机，也可位于远程计算机；既可以是公共的，也可以是私有的。</span><span class="sxs-lookup"><span data-stu-id="6daa3-104">A message queue may be located on the local computer or a remote computer, and may be public or private.</span></span> <span data-ttu-id="6daa3-105">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，MSMQ 连接管理器和消息队列任务不支持向远程计算机上的私有队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="6daa3-105">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the MSMQ connection manager and Message Queue task do not support sending to a private queue on a remote computer.</span></span> <span data-ttu-id="6daa3-106">但通过使用脚本任务，可轻松地向远程私有队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="6daa3-106">However, by using the Script task, it is easy to send a message to a remote private queue.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6daa3-107">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="6daa3-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="6daa3-108">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="6daa3-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="6daa3-109">说明</span><span class="sxs-lookup"><span data-stu-id="6daa3-109">Description</span></span>  
 <span data-ttu-id="6daa3-110">下面的示例使用一个现有 MSMQ 连接管理器以及 System.Messaging 命名空间的对象和方法，向远程私有消息队列发送包含在包变量中的文本。</span><span class="sxs-lookup"><span data-stu-id="6daa3-110">The following example uses an existing MSMQ connection manager, together with objects and methods from the System.Messaging namespace, to send the text contained in a package variable to a remote private message queue.</span></span> <span data-ttu-id="6daa3-111">对 MSMQ 连接管理器的 M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection (System.object) 方法的调用将返回一个**MessageQueue**对象，其 `Send` 方法完成此任务。</span><span class="sxs-lookup"><span data-stu-id="6daa3-111">The call to the M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) method of the MSMQ connection manager returns a **MessageQueue** object whose `Send` method accomplishes this task.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6daa3-112">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="6daa3-112">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6daa3-113">使用默认名称创建一个 MSMQ 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="6daa3-113">Create an MSMQ connection manager with the default name.</span></span> <span data-ttu-id="6daa3-114">设置有效远程私有队列的路径，格式如下：</span><span class="sxs-lookup"><span data-stu-id="6daa3-114">Set the path of a valid remote private queue, in the following format:</span></span>  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  <span data-ttu-id="6daa3-115">创建一个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 名为**MessageText**的变量 `String` ，以将消息文本传递到脚本。</span><span class="sxs-lookup"><span data-stu-id="6daa3-115">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable named **MessageText** of type `String` to pass the message text into the script.</span></span> <span data-ttu-id="6daa3-116">输入默认消息作为该变量的值。</span><span class="sxs-lookup"><span data-stu-id="6daa3-116">Enter a default message as the value of the variable.</span></span>  
  
3.  <span data-ttu-id="6daa3-117">向设计图面添加一个脚本任务，并对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="6daa3-117">Add a Script Task to the design surface and edit it.</span></span> <span data-ttu-id="6daa3-118">在“脚本任务编辑器”的“脚本”选项卡中，将 `MessageText` 变量添加到 ReadOnlyVariables 属性中，使该变量在脚本内可用。</span><span class="sxs-lookup"><span data-stu-id="6daa3-118">On the **Script** tab of the **Script Task Editor**, add the `MessageText` variable to the **ReadOnlyVariables** property to make the variable available inside the script.</span></span>  
  
4.  <span data-ttu-id="6daa3-119">单击“编辑脚本”，打开   Tools for Applications (VSTA) 脚本编辑器[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6daa3-119">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) script editor.</span></span>  
  
5.  <span data-ttu-id="6daa3-120">在脚本项目中添加对 `System.Messaging` 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="6daa3-120">Add a reference in the script project to the `System.Messaging` namespace.</span></span>  
  
6.  <span data-ttu-id="6daa3-121">用下面部分中的代码替换脚本窗口中的内容。</span><span class="sxs-lookup"><span data-stu-id="6daa3-121">Replace the contents of the script window with the code in the following section.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6daa3-122">代码</span><span class="sxs-lookup"><span data-stu-id="6daa3-122">Code</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
<span data-ttu-id="6daa3-123">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6daa3-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6daa3-124">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6daa3-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6daa3-125">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6daa3-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6daa3-126">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6daa3-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6daa3-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6daa3-127">See Also</span></span>  
 [<span data-ttu-id="6daa3-128">消息队列任务</span><span class="sxs-lookup"><span data-stu-id="6daa3-128">Message Queue Task</span></span>](../control-flow/message-queue-task.md)  
  
  
