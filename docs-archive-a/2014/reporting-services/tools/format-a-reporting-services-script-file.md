---
title: 设置 Reporting Services 脚本文件的格式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c98a2f6561c3242fec34f7ca11c8304286ccebae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689753"
---
# <a name="format-a-reporting-services-script-file"></a><span data-ttu-id="cc1dc-102">设置 Reporting Services 脚本文件的格式</span><span class="sxs-lookup"><span data-stu-id="cc1dc-102">Format a Reporting Services Script File</span></span>
  <span data-ttu-id="cc1dc-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 脚本是用来定义 Reporting Services SOAP API 的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET 代码文件，该文件是针对基于 Web 服务描述语言 (WSDL) 构建的代理编写的。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET code file, written against a proxy that is built on Web Service Description Language (WSDL), which defines the Reporting Services SOAP API.</span></span> <span data-ttu-id="cc1dc-104">脚本文件以 Unicode 或 UTF-8 文本文件形式存储，扩展名为 .rss。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-104">A script file is stored as a Unicode or UTF-8 text file with the extension .rss.</span></span>  
  
 <span data-ttu-id="cc1dc-105">脚本文件充当 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 模块，以包含用户定义的过程和模块级变量。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-105">The script file acts as a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] module and can contain user-defined procedures and module-level variables.</span></span> <span data-ttu-id="cc1dc-106">为了使脚本文件成功运行，其中必须包含 Main 过程。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-106">For the script file to run successfully, it must contain a Main procedure.</span></span> <span data-ttu-id="cc1dc-107">Main 过程是脚本文件运行时访问的第一个过程。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-107">The Main procedure is the first procedure that is accessed when your script file runs.</span></span> <span data-ttu-id="cc1dc-108">在 Main 过程中，可以添加您的 Web 服务操作并运行您的用户定义子过程。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-108">Main is where you can add your Web service operations and run your user defined subprocedures.</span></span> <span data-ttu-id="cc1dc-109">下面的代码将创建一个 Main 过程：</span><span class="sxs-lookup"><span data-stu-id="cc1dc-109">The following code creates a Main procedure:</span></span>  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 <span data-ttu-id="cc1dc-110">脚本环境会自动连接到报表服务器，创建 Web 代理类，并生成一个指向 Web 服务代理对象的引用变量 (*rs*)。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-110">The script environment automatically connects to the report server, creates the Web proxy class, and generates a reference variable (*rs*) to the Web service proxy object.</span></span> <span data-ttu-id="cc1dc-111">所创建的各个语句只需引用 *rs* 模块级变量即可执行 Web 服务库中所提供的任何 Web 服务操作。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-111">Individual statements that you create need only refer to the *rs* module-level variable to perform any of the Web service operations that are available in the Web service library.</span></span> <span data-ttu-id="cc1dc-112">下面的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 代码从脚本文件中调用 Web 服务 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="cc1dc-112">The following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code calls the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method from within a script file:</span></span>  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cc1dc-113">用户凭据由脚本环境管理，并通过使用 RS.exe 来传递命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-113">User credentials are managed by the script environment and passed through command prompt arguments through the use of RS.exe.</span></span> <span data-ttu-id="cc1dc-114">尽管可以使用 *rs* 变量来设置对 Web 服务的身份验证，但是仍建议您使用脚本环境。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-114">Although you can use the *rs* variable to set the authentication of the Web service, it is recommended that you use the script environment.</span></span> <span data-ttu-id="cc1dc-115">不必在脚本文件本身中对 Web 服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-115">You do not need to authenticate the Web service in the script file itself.</span></span> <span data-ttu-id="cc1dc-116">有关对脚本环境进行身份验证的详细信息，请参阅 [RS.exe 实用工具 (SSRS)](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-116">For more information about authenticating the script environment, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
 <span data-ttu-id="cc1dc-117">在脚本文件中不必声明命名空间。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-117">You do not declare namespaces within the script file.</span></span> <span data-ttu-id="cc1dc-118">脚本环境提供了几个有用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空间：System.Web.Services  、System.Web.Services.Protocols  、System.Xml  和 System.IO  。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-118">The scripting environment makes several useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces available to you: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**, and **System.IO**.</span></span>  
  
 <span data-ttu-id="cc1dc-119">有关脚本示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="cc1dc-119">For script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1dc-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc1dc-120">See Also</span></span>  
 <span data-ttu-id="cc1dc-121">[报表服务器 Web 服务](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="cc1dc-121">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="cc1dc-122">[技术参考 (SSRS)](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cc1dc-122">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="cc1dc-123">RS.exe 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="cc1dc-123">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
