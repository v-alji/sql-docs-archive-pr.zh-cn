---
title: 使用消息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53b2e0fa4be2dfd53cdd8f4f0cacb7ae0bd79edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590136"
---
# <a name="using-messages"></a><span data-ttu-id="04083-102">使用消息</span><span class="sxs-lookup"><span data-stu-id="04083-102">Using Messages</span></span>
  <span data-ttu-id="04083-103">在 SMO 中，系统消息由属于 `Server` 对象的 <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="04083-103">In SMO, system messages are represented by the <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> object that belongs to the `Server` object.</span></span> <span data-ttu-id="04083-104">因为无法修改系统消息，所以 `SystemMessage` 对象属性为只读属性。</span><span class="sxs-lookup"><span data-stu-id="04083-104">Because the system messages cannot be modified, `SystemMessage` object properties are read-only.</span></span>  
  
 <span data-ttu-id="04083-105">用户定义的消息在 SMO 中由 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> 对象以编程方式表示。</span><span class="sxs-lookup"><span data-stu-id="04083-105">User-defined messages are represented programmatically in SMO by the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> object.</span></span> <span data-ttu-id="04083-106">可通过循环访问该集合来发现现有的用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="04083-106">Existing user-defined messages can be discovered by iterating through the collection.</span></span> <span data-ttu-id="04083-107">可以通过实例化新的 `UserDefinedMessage` 对象并设置其相应的属性来创建新的用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="04083-107">New user-defined messages can be created by instantiating a new `UserDefinedMessage` object and setting the appropriate properties.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="04083-108">示例</span><span class="sxs-lookup"><span data-stu-id="04083-108">Examples</span></span>  
 <span data-ttu-id="04083-109">对于下列代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="04083-109">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="04083-110">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="04083-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a><span data-ttu-id="04083-111">在 Visual Basic 中查找特殊系统消息</span><span class="sxs-lookup"><span data-stu-id="04083-111">Finding a Particular System Message in Visual Basic</span></span>  
 <span data-ttu-id="04083-112">此代码示例说明如何通过 ID 号标识系统消息并显示该消息。</span><span class="sxs-lookup"><span data-stu-id="04083-112">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a><span data-ttu-id="04083-113">在 Visual C# 中查找特殊系统消息</span><span class="sxs-lookup"><span data-stu-id="04083-113">Finding a Particular System Message in Visual C#</span></span>  
 <span data-ttu-id="04083-114">此代码示例说明如何通过 ID 号标识系统消息并显示该消息。</span><span class="sxs-lookup"><span data-stu-id="04083-114">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a><span data-ttu-id="04083-115">在 PowerShell 中查找特殊系统消息</span><span class="sxs-lookup"><span data-stu-id="04083-115">Finding a Particular System Message in PowerShell</span></span>  
 <span data-ttu-id="04083-116">此代码示例说明如何通过 ID 号标识系统消息并显示该消息。</span><span class="sxs-lookup"><span data-stu-id="04083-116">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a><span data-ttu-id="04083-117">在 Visual Basic 中添加新的用户定义的消息</span><span class="sxs-lookup"><span data-stu-id="04083-117">Adding a New User-Defined Message in Visual Basic</span></span>  
 <span data-ttu-id="04083-118">此代码示例说明如何使用大于 50000 的 ID 创建用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="04083-118">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```vb
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a><span data-ttu-id="04083-119">在 Visual C# 中添加新的用户定义的消息</span><span class="sxs-lookup"><span data-stu-id="04083-119">Adding a New User-Defined Message in Visual C#</span></span>  
 <span data-ttu-id="04083-120">此代码示例说明如何使用大于 50000 的 ID 创建用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="04083-120">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```csharp
{
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a><span data-ttu-id="04083-121">在 PowerShell 中添加新的用户定义的消息</span><span class="sxs-lookup"><span data-stu-id="04083-121">Adding a New User-Defined Message in PowerShell</span></span>
 <span data-ttu-id="04083-122">此代码示例说明如何使用大于 50000 的 ID 创建用户定义的消息。</span><span class="sxs-lookup"><span data-stu-id="04083-122">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -ArgumentList `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
