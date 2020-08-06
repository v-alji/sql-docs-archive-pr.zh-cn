---
title: 使用数据库邮件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ceec7417638f53427ed5a62101f2fdb6d7440a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689817"
---
# <a name="using-database-mail"></a><span data-ttu-id="c8bb5-102">使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="c8bb5-102">Using Database Mail</span></span>
  <span data-ttu-id="c8bb5-103">在 SMO 中，数据库邮件子系统由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 属性引用的 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-103">In SMO, the Database Mail subsystem is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object that is referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property.</span></span> <span data-ttu-id="c8bb5-104">使用 SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 对象，可以配置数据库邮件子系统并管理配置文件和邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-104">By using the SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object, you can configure the Database Mail subsystem and manage profiles and mail accounts.</span></span> <span data-ttu-id="c8bb5-105">SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 对象属于 `Server` 对象，也就是说，邮件帐户的作用域处于服务器级别。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-105">The SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object belongs to the `Server` object, meaning that scope of the mail accounts is at the server level.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c8bb5-106">示例</span><span class="sxs-lookup"><span data-stu-id="c8bb5-106">Examples</span></span>  
 <span data-ttu-id="c8bb5-107">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="c8bb5-108">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="c8bb5-109">对于使用数据库邮件的程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，您必须包含 `Imports` 用于限定邮件命名空间的语句。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-109">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Database Mail, you must include the `Imports` statement to qualify the Mail namespace.</span></span> <span data-ttu-id="c8bb5-110">请在应用程序的其他 `Imports` 语句之后、任何声明之前插入该语句，例如：</span><span class="sxs-lookup"><span data-stu-id="c8bb5-110">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a><span data-ttu-id="c8bb5-111">使用 Visual Basic 创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="c8bb5-111">Creating a Database Mail Account by Using Visual Basic</span></span>  
 <span data-ttu-id="c8bb5-112">此代码示例说明如何在 SMO 中创建电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-112">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="c8bb5-113">数据库邮件由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 对象表示，并由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Server> 属性引用。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-113">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="c8bb5-114">SMO 可用于以编程方式配置数据库邮件，但它无法用于发送或处理收到的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-114">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
 <span data-ttu-id="c8bb5-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="c8bb5-115">VB.NET</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a><span data-ttu-id="c8bb5-116">使用 Visual C# 创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="c8bb5-116">Creating a Database Mail Account by Using Visual C#</span></span>  
 <span data-ttu-id="c8bb5-117">此代码示例说明如何在 SMO 中创建电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-117">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="c8bb5-118">数据库邮件由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 对象表示，并由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Server> 属性引用。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-118">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="c8bb5-119">SMO 可用于以编程方式配置数据库邮件，但它无法用于发送或处理收到的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-119">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a><span data-ttu-id="c8bb5-120">使用 PowerShell 创建数据库邮件帐户</span><span class="sxs-lookup"><span data-stu-id="c8bb5-120">Creating a Database Mail Account by Using PowerShell</span></span>  
 <span data-ttu-id="c8bb5-121">此代码示例说明如何在 SMO 中创建电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-121">This code example shows how to create an e-mail account in SMO.</span></span> <span data-ttu-id="c8bb5-122">数据库邮件由 <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> 对象表示，并由 <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Server> 属性引用。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-122">Database Mail is represented by the <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> object and referenced by the <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="c8bb5-123">SMO 可用于以编程方式配置数据库邮件，但它无法用于发送或处理收到的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c8bb5-123">SMO can be used to programmatically configure Database Mail, but it cannot be used to send or handle received e-mail.</span></span>
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -ArgumentList $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
