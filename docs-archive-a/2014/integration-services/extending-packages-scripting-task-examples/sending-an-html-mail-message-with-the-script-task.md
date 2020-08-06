---
title: 使用脚本任务发送 HTML 邮件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c1a967b52a84e1ff9c2e54c48e40f4d149b2dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682960"
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a><span data-ttu-id="6cd80-102">使用脚本任务发送 HTML 邮件消息</span><span class="sxs-lookup"><span data-stu-id="6cd80-102">Sending an HTML Mail Message with the Script Task</span></span>
  <span data-ttu-id="6cd80-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail 任务仅支持纯文本格式的邮件消息。</span><span class="sxs-lookup"><span data-stu-id="6cd80-103">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail task only supports mail messages in plain text format.</span></span> <span data-ttu-id="6cd80-104">但是，您可以使用脚本任务以及 .NET Framework 的邮件功能轻松发送 HTML 邮件消息。</span><span class="sxs-lookup"><span data-stu-id="6cd80-104">However you can easily send HTML mail messages by using the Script task and the mail capabilities of the .NET Framework.</span></span>

> [!NOTE]
>  <span data-ttu-id="6cd80-105">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="6cd80-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="6cd80-106">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="6cd80-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="6cd80-107">说明</span><span class="sxs-lookup"><span data-stu-id="6cd80-107">Description</span></span>
 <span data-ttu-id="6cd80-108">下面的示例使用 `System.Net.Mail` 命名空间配置和发送 HTML 邮件消息。</span><span class="sxs-lookup"><span data-stu-id="6cd80-108">The following example uses the `System.Net.Mail` namespace to configure and send an HTML mail message.</span></span> <span data-ttu-id="6cd80-109">该脚本从包变量获取电子邮件的收件人、发件人、主题和正文，然后使用它们创建新 `MailMessag`e，并将其 `IsBodyHtml` 属性设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="6cd80-109">The script obtains the To, From, Subject, and body of the e-mail from package variables, uses them to create a new `MailMessag`e, and sets its `IsBodyHtml` property to `True`.</span></span> <span data-ttu-id="6cd80-110">接着，该脚本从另一个包变量获取 SMTP 服务器名称，然后初始化 `System.Net.Mail.SmtpClient` 实例，并调用其 `Send` 方法发送 HTML 消息。</span><span class="sxs-lookup"><span data-stu-id="6cd80-110">Then it obtains the SMTP server name from another package variable, initializes an instance of `System.Net.Mail.SmtpClient`, and calls its `Send` method to send the HTML message.</span></span> <span data-ttu-id="6cd80-111">该示例将消息发送功能封装到一个可在其他脚本中重用的子例程中。</span><span class="sxs-lookup"><span data-stu-id="6cd80-111">The sample encapsulates the message sending functionality in a subroutine that could be reused in other scripts.</span></span>

#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a><span data-ttu-id="6cd80-112">不使用 SMTP 连接管理器配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="6cd80-112">To configure this Script Task example without an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="6cd80-113">创建名为 `HtmlEmailTo`、`HtmlEmailFrom` 和 `HtmlEmailSubject` 的字符串变量，并向它们分配相应的值，以用于有效的测试消息。</span><span class="sxs-lookup"><span data-stu-id="6cd80-113">Create string variables named `HtmlEmailTo`, `HtmlEmailFrom`, and `HtmlEmailSubject` and assign appropriate values to them for a valid test message.</span></span>

2.  <span data-ttu-id="6cd80-114">创建一个名为 `HtmlEmailBody` 的字符串变量，并向其分配 HTML 标记字符串。</span><span class="sxs-lookup"><span data-stu-id="6cd80-114">Create a string variable named `HtmlEmailBody` and assign a string of HTML markup to it.</span></span> <span data-ttu-id="6cd80-115">例如：</span><span class="sxs-lookup"><span data-stu-id="6cd80-115">For example:</span></span>

    ```
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>
    ```

3.  <span data-ttu-id="6cd80-116">创建一个名为 `HtmlEmailServer` 的字符串变量，并向其分配一个可接收匿名传出消息的可用 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6cd80-116">Create a string variable named `HtmlEmailServer` and assign the name of an available SMTP server that accepts anonymous outgoing messages.</span></span>

4.  <span data-ttu-id="6cd80-117">将这五个变量全部分配到新脚本任务的 ReadOnlyVariables 属性  。</span><span class="sxs-lookup"><span data-stu-id="6cd80-117">Assign all five of these variables to the **ReadOnlyVariables** property of a new Script task.</span></span>

5.  <span data-ttu-id="6cd80-118">将 `System.Net` 和 `System.Net.Mail` 命名空间导入到代码中。</span><span class="sxs-lookup"><span data-stu-id="6cd80-118">Import the `System.Net` and `System.Net.Mail` namespaces into your code.</span></span>

 <span data-ttu-id="6cd80-119">本主题中的示例代码从包变量获取 SMTP 服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6cd80-119">The sample code in this topic obtains the SMTP server name from a package variable.</span></span> <span data-ttu-id="6cd80-120">当然，还可以利用 SMTP 连接管理器封装连接信息，并在代码中从连接管理器提取服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6cd80-120">However, you could also take advantage of an SMTP connection manager to encapsulate the connection information, and extract the server name from the connection manager in your code.</span></span> <span data-ttu-id="6cd80-121">SMTP 连接管理器的 <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> 方法以下列格式返回一个字符串：</span><span class="sxs-lookup"><span data-stu-id="6cd80-121">The <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> method of the SMTP connection manager returns a string in the following format:</span></span>

 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`

 <span data-ttu-id="6cd80-122">可以使用 `String.Split` 方法将此参数列表从每个分号 (;) 或等号 (=) 处分为一个单独的字符串数组，然后提取该数组的第二个参数 (subscript 1) 作为服务器名称。</span><span class="sxs-lookup"><span data-stu-id="6cd80-122">You can use the `String.Split` method to separate this argument list into an array of individual strings at each semicolon (;) or equal sign (=), and then extract the second argument (subscript 1) from the array as the server name.</span></span>

#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a><span data-ttu-id="6cd80-123">使用 SMTP 连接管理器配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="6cd80-123">To configure this Script Task example with an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="6cd80-124">通过从 ReadOnlyVariables 列表删除 `HtmlEmailServer` 变量修改先前配置的脚本任务  。</span><span class="sxs-lookup"><span data-stu-id="6cd80-124">Modify the Script task configured earlier by removing the `HtmlEmailServer` variable from the list of **ReadOnlyVariables**.</span></span>

2.  <span data-ttu-id="6cd80-125">将获取服务器名称的代码行：</span><span class="sxs-lookup"><span data-stu-id="6cd80-125">Replace the line of code that obtains the server name:</span></span>

    ```
    Dim smtpServer As String = _
      Dts.Variables("HtmlEmailServer").Value.ToString
    ```

     <span data-ttu-id="6cd80-126">替换为以下代码行：</span><span class="sxs-lookup"><span data-stu-id="6cd80-126">with the following lines:</span></span>

    ```
    Dim smtpConnectionString As String = _
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)
    Dim smtpServer As String = _
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)
    ```

## <a name="code"></a><span data-ttu-id="6cd80-127">代码</span><span class="sxs-lookup"><span data-stu-id="6cd80-127">Code</span></span>

```vb
Public Sub Main()

  Dim htmlMessageTo As String = _
    Dts.Variables("HtmlEmailTo").Value.ToString
  Dim htmlMessageFrom As String = _
    Dts.Variables("HtmlEmailFrom").Value.ToString
  Dim htmlMessageSubject As String = _
    Dts.Variables("HtmlEmailSubject").Value.ToString
  Dim htmlMessageBody As String = _
    Dts.Variables("HtmlEmailBody").Value.ToString
  Dim smtpServer As String = _
    Dts.Variables("HtmlEmailServer").Value.ToString

  SendMailMessage( _
      htmlMessageTo, htmlMessageFrom, _
      htmlMessageSubject, htmlMessageBody, _
      True, smtpServer)

  Dts.TaskResult = ScriptResults.Success

End Sub

Private Sub SendMailMessage( _
    ByVal SendTo As String, ByVal From As String, _
    ByVal Subject As String, ByVal Body As String, _
    ByVal IsBodyHtml As Boolean, ByVal Server As String)

  Dim htmlMessage As MailMessage
  Dim mySmtpClient As SmtpClient

  htmlMessage = New MailMessage( _
    SendTo, From, Subject, Body)
  htmlMessage.IsBodyHtml = IsBodyHtml

  mySmtpClient = New SmtpClient(Server)
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials
  mySmtpClient.Send(htmlMessage)

End Sub
```

```csharp
public void Main()
        {

            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();

            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)
        {

            MailMessage htmlMessage;
            SmtpClient mySmtpClient;

            htmlMessage = new MailMessage(SendTo, From, Subject, Body);
            htmlMessage.IsBodyHtml = IsBodyHtml;

            mySmtpClient = new SmtpClient(Server);
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;
            mySmtpClient.Send(htmlMessage);

        }
```

<span data-ttu-id="6cd80-128">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6cd80-128">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6cd80-129">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="6cd80-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6cd80-130">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="6cd80-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6cd80-131">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="6cd80-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd80-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cd80-132">See Also</span></span>
 [<span data-ttu-id="6cd80-133">发送邮件任务</span><span class="sxs-lookup"><span data-stu-id="6cd80-133">Send Mail Task</span></span>](../control-flow/send-mail-task.md)


