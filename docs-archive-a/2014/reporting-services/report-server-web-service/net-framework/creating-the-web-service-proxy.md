---
title: 创建 Web 服务代理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d080b96fa29e906c044561a684d58275af9f61e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688540"
---
# <a name="creating-the-web-service-proxy"></a><span data-ttu-id="5df49-102">创建 Web 服务代理</span><span class="sxs-lookup"><span data-stu-id="5df49-102">Creating the Web Service Proxy</span></span>
  <span data-ttu-id="5df49-103">客户端和 Web 服务可以通过 SOAP 消息进行通信，这些消息将输入参数和输出参数封装为 XML。</span><span class="sxs-lookup"><span data-stu-id="5df49-103">A client and a Web service can communicate using SOAP messages, which encapsulate the input and output parameters as XML.</span></span> <span data-ttu-id="5df49-104">代理类将参数映射到 XML 元素，然后通过网络发送 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="5df49-104">A proxy class maps parameters to XML elements and then sends the SOAP messages over a network.</span></span> <span data-ttu-id="5df49-105">通过这种方法，代理类使您不必在 SOAP 级别与 Web 服务通信，并允许您在支持 SOAP 和 Web 服务代理的任何开发环境中调用 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="5df49-105">In this way, the proxy class frees you from having to communicate with the Web service at the SOAP level and allows you to invoke Web service methods in any development environment that supports SOAP and Web service proxies.</span></span>  
  
 <span data-ttu-id="5df49-106">可以通过两种方法使用将代理类添加到开发项目中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ：使用中的 WSDL 工具 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 和在中添加 Web 引用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5df49-106">There are two ways to add a proxy class to your development project using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: with the WSDL tool in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], and by adding a Web reference in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="5df49-107">下列各节更为详细地讨论这一主题。</span><span class="sxs-lookup"><span data-stu-id="5df49-107">The following sections discuss this subject in further detail.</span></span>  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a><span data-ttu-id="5df49-108">使用 WSDL 工具添加代理</span><span class="sxs-lookup"><span data-stu-id="5df49-108">Adding the Proxy Using the WSDL Tool</span></span>  
 <span data-ttu-id="5df49-109">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 包括 Web 服务描述语言工具 (Wsdl.exe)，它使得您能够生成 Web 服务代理以用于 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 开发环境中。</span><span class="sxs-lookup"><span data-stu-id="5df49-109">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK includes the Web Services Description Language tool (Wsdl.exe), which enables you to generate a Web service proxy for use in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] development environment.</span></span> <span data-ttu-id="5df49-110">在当前 c # 和)  (支持 Web 服务的语言中创建客户端代理的最常用方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 是使用 WSDL 工具。</span><span class="sxs-lookup"><span data-stu-id="5df49-110">The most common way to create a client proxy in languages that support Web services (currently C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) is to use the WSDL tool.</span></span>  
  
 <span data-ttu-id="5df49-111">**使用 Wsdl.exe 将代理类添加到项目中**</span><span class="sxs-lookup"><span data-stu-id="5df49-111">**To add a proxy class to your project using Wsdl.exe**</span></span>  
  
1.  <span data-ttu-id="5df49-112">从命令提示符下，使用 Wsdl.exe 创建代理类，同时指定（至少）指向报表服务器 Web 服务的 URL。</span><span class="sxs-lookup"><span data-stu-id="5df49-112">From a command prompt, use Wsdl.exe to create a proxy class, specifying (at a minimum) the URL to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="5df49-113">例如，下面的命令提示符语句为报表服务器 Web 服务的管理端点指定 URL。</span><span class="sxs-lookup"><span data-stu-id="5df49-113">For example, the following command prompt statement specifies a URL for the management endpoint of the Report Server Web service:</span></span>  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="5df49-114">WSDL 工具接受多种用于生成代理的命令提示符参数。</span><span class="sxs-lookup"><span data-stu-id="5df49-114">The WSDL tool accepts a number of command-prompt arguments for generating a proxy.</span></span> <span data-ttu-id="5df49-115">前一示例指定语言 C# 和建议在代理中使用的一个命名空间（以防止在使用多个 Web 服务端点时出现名称冲突），并生成一个名为 ReportingService2010.cs 的 C# 文件。</span><span class="sxs-lookup"><span data-stu-id="5df49-115">The preceding example specifies the language C#, a suggested namespace to use in the proxy (to prevent name collision if using more than one Web service endpoint), and generates a C# file called ReportingService2010.cs.</span></span> <span data-ttu-id="5df49-116">如果本示例已指定 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]，则该示例应已生成名为 ReportingService2010.vb 的代理文件。</span><span class="sxs-lookup"><span data-stu-id="5df49-116">If the example had specified [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], the example would have generated a proxy file with the name ReportingService2010.vb.</span></span> <span data-ttu-id="5df49-117">将在您运行此命令的目录中创建此文件。</span><span class="sxs-lookup"><span data-stu-id="5df49-117">This file is created in the directory from which you run the command.</span></span>  
  
2.  <span data-ttu-id="5df49-118">将代理类编译为程序集文件（具有扩展名 .dll）并在项目中引用它，或者将该类添加为一个项目项。</span><span class="sxs-lookup"><span data-stu-id="5df49-118">Compile the proxy class into an assembly file (with the extension .dll) and reference it in your project, or add the class as a project item.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5df49-119">当您手动将代理类添加到项目时，您需要添加对于 System.Web.Services.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="5df49-119">When you add a proxy class to your project manually, you need to add a reference to System.Web.Services.dll.</span></span> <span data-ttu-id="5df49-120">如果您在 Visual Studio .NET 中使用 Web 引用添加代理，则将自动为您创建引用。</span><span class="sxs-lookup"><span data-stu-id="5df49-120">If you add the proxy using a Web reference in Visual Studio .NET, the reference is automatically created for you.</span></span> <span data-ttu-id="5df49-121">有关详细信息，请参阅本主题后面的“在 Visual Studio 中使用 Web 引用添加代理”。</span><span class="sxs-lookup"><span data-stu-id="5df49-121">For more information, see "Adding the Proxy Using a Web Reference in Visual Studio" later in this topic.</span></span>  
  
     <span data-ttu-id="5df49-122">在将代理类作为项添加到项目后，关联的文件将出现在解决方案资源管理器中。</span><span class="sxs-lookup"><span data-stu-id="5df49-122">After you add the proxy class as an item to your project, the associated file appears in Solution Explorer.</span></span>  
  
3.  <span data-ttu-id="5df49-123">若要以编程方式调用此服务，应创建代理类的实例。</span><span class="sxs-lookup"><span data-stu-id="5df49-123">To call the service programmatically, create an instance of the proxy class.</span></span>  
  
     <span data-ttu-id="5df49-124">以下代码示例显示在项目中创建 <xref:ReportService2010.ReportingService2010> 代理类的实例的语法：</span><span class="sxs-lookup"><span data-stu-id="5df49-124">The following code example shows the syntax for creating an instance of the <xref:ReportService2010.ReportingService2010> proxy class in a project:</span></span>  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 <span data-ttu-id="5df49-125">有关 Wsdl.exe 工具的详细信息（包括其完整语法），请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文档中的“Web 服务描述语言工具”。</span><span class="sxs-lookup"><span data-stu-id="5df49-125">For more information about the Wsdl.exe tool, including its full syntax, see "Web Services Description Language Tool" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span> <span data-ttu-id="5df49-126">有关 Web 服务代理的完整解释，请参阅 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文档中的“创建 XML Web 服务代理”。</span><span class="sxs-lookup"><span data-stu-id="5df49-126">For a full explanation of Web service proxies, see "Creating an XML Web Service Proxy" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a><span data-ttu-id="5df49-127">在 Visual Studio 中使用 Web 引用添加代理</span><span class="sxs-lookup"><span data-stu-id="5df49-127">Adding the Proxy Using a Web Reference in Visual Studio</span></span>  
 <span data-ttu-id="5df49-128">Web 引用使一个项目可以使用一个或多个 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="5df49-128">A Web reference enables a project to consume one or more Web services.</span></span> [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] <span data-ttu-id="5df49-129">使用户可以通过以下几个简单步骤向项目添加 Web 服务引用。</span><span class="sxs-lookup"><span data-stu-id="5df49-129">enables users to add Web service references to projects by following a few simple steps.</span></span>  
  
 <span data-ttu-id="5df49-130">**将 Web 引用添加到项目**</span><span class="sxs-lookup"><span data-stu-id="5df49-130">**To add a Web reference to a project**</span></span>  
  
1.  <span data-ttu-id="5df49-131">在“解决方案资源管理器”\*\*\*\* 中，选择要使用 Web 服务的项目。</span><span class="sxs-lookup"><span data-stu-id="5df49-131">In **Solution Explorer**, select the project that will consume the Web service.</span></span>  
  
2.  <span data-ttu-id="5df49-132">在“项目”\*\*\*\* 菜单中，单击“添加 Web 引用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5df49-132">On the **Project** menu, click **Add Web Reference**.</span></span>  
  
     <span data-ttu-id="5df49-133">“添加 Web 引用”\*\*\*\* 对话框打开。</span><span class="sxs-lookup"><span data-stu-id="5df49-133">The **Add Web Reference** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="5df49-134">在“URL”\*\*\*\* 字段中，输入指向报表服务器 Web 服务的完整路径。</span><span class="sxs-lookup"><span data-stu-id="5df49-134">In the **URL** field, enter the complete path to the Report Server Web service.</span></span>  
  
     <span data-ttu-id="5df49-135">报表服务器 Web 服务的报表执行端点的简化 URL 可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="5df49-135">A simplified URL for the report execution endpoint of the Report Server Web service might look like this:</span></span>  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     <span data-ttu-id="5df49-136">此 URL 包含在其中部署报表服务器 Web 服务的域、包含该服务的文件夹的名称以及该服务的发现文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5df49-136">The URL contains the domain in which the Report Server Web service is deployed, the name of the folder containing the service, and the name of the discovery file for the service.</span></span> <span data-ttu-id="5df49-137">有关不同 URL 元素的完整说明，请参阅[访问 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="5df49-137">For a complete description of the different URL elements, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
     <span data-ttu-id="5df49-138">由 Web 服务提供的方法和属性的说明将出现在“浏览器”窗格的左侧。</span><span class="sxs-lookup"><span data-stu-id="5df49-138">A description of the methods and properties provided by the Web service appears in the Browser pane on the left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5df49-139">有关与报表服务器 Web 服务关联的项的详细信息，请参阅[报表服务器 Web 服务方法](../methods/report-server-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="5df49-139">For more information about the items associated with the Report Server Web service, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span>  
  
4.  <span data-ttu-id="5df49-140">验证项目是否可以使用报表服务器 Web 服务，以及您是否具有适当的权限访问报表服务器。</span><span class="sxs-lookup"><span data-stu-id="5df49-140">Verify that your project can use the Report Server Web service, and that you have appropriate permission to access the report server.</span></span>  
  
5.  <span data-ttu-id="5df49-141">在“Web 引用名”\*\*\*\* 字段中输入一个名称，将在代码中使用该名称以编程方式访问报表服务器 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="5df49-141">In the **Web reference name** field, enter a name that you will use in your code to access the Report Server Web service programmatically.</span></span>  
  
6.  <span data-ttu-id="5df49-142">选择“添加引用”\*\*\*\* 按钮，以在应用程序中创建对 Web 服务的引用。</span><span class="sxs-lookup"><span data-stu-id="5df49-142">Select the **Add Reference** button to create a reference in your application to the Web service.</span></span>  
  
     <span data-ttu-id="5df49-143">新引用将出现在“解决方案资源管理器”\*\*\*\* 中处于活动状态的项目的“Web 引用”节点下，其名称在“Web 引用名”\*\*\*\* 字段中指定。</span><span class="sxs-lookup"><span data-stu-id="5df49-143">The new reference appears in **Solution Explorer** under the Web References node for the active project, named as specified in the **Web reference name** field.</span></span>  
  
7.  <span data-ttu-id="5df49-144">在“解决方案资源管理器”\*\*\*\* 中，展开“Web 引用”文件夹，以记下与可用于项目中的项的 Web 引用类对应的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5df49-144">In **Solution Explorer**, expand the Web References folder to note the namespace for the Web reference classes that are available to the items in your project.</span></span>  
  
     <span data-ttu-id="5df49-145">在将 Web 引用添加到项目后，关联的文件将显示在“解决方案资源管理器”\*\*\*\* 的“Web 引用”文件夹内的某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5df49-145">After adding a Web reference to your project, the associated files are displayed in a folder within the Web References folder of **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="5df49-146">在添加 Web 引用之后，使用以下语法创建代理类的实例：</span><span class="sxs-lookup"><span data-stu-id="5df49-146">After you add the Web reference, use the following syntax to create an instance of the proxy class:</span></span>  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 <span data-ttu-id="5df49-147">还可以将“using”\*\*\*\*（在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中为“Import”\*\*\*\*）指令添加到报表服务器 Web 服务引用中。</span><span class="sxs-lookup"><span data-stu-id="5df49-147">You can also add a **using** (**Import** in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) directive to the Report Server Web service reference.</span></span> <span data-ttu-id="5df49-148">如果您使用该指令，则不必完全限定命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="5df49-148">If you use this directive, you do not need to fully qualify the types in the namespace.</span></span> <span data-ttu-id="5df49-149">为此，请在文件中添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="5df49-149">To do this, add the following code to your file:</span></span>  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a><span data-ttu-id="5df49-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5df49-150">See Also</span></span>  
 <span data-ttu-id="5df49-151">[报表服务器 Web 服务](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="5df49-151">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="5df49-152">[使用 Web 服务和 .NET Framework 生成应用程序](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="5df49-152">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="5df49-153">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5df49-153">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
