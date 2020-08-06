---
title: 第2课：添加 Web 引用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 02ca614cb042211ac468246c3003efaa5f2e8fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690266"
---
# <a name="lesson-2-adding-a-web-reference"></a><span data-ttu-id="6990e-102">第 2 课：添加 Web 引用</span><span class="sxs-lookup"><span data-stu-id="6990e-102">Lesson 2: Adding a Web Reference</span></span>
  <span data-ttu-id="6990e-103">Web 服务发现是客户端查找 Web 服务并获取其服务说明的过程。</span><span class="sxs-lookup"><span data-stu-id="6990e-103">Web service discovery is the process by which a client locates a Web service and obtains its service description.</span></span> <span data-ttu-id="6990e-104">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的 Web 服务发现过程涉及询问网站是否遵循预定算法。</span><span class="sxs-lookup"><span data-stu-id="6990e-104">The process of Web service discovery in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] involves interrogating a Web site following a predetermined algorithm.</span></span> <span data-ttu-id="6990e-105">此过程的目的是查找服务说明，它是使用 Web 服务描述语言 (WSDL) 的一个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="6990e-105">The goal of the process is to locate the service description, which is an XML document that uses the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="6990e-106">服务说明介绍了哪些服务可用，以及如何与这些服务进行交互。</span><span class="sxs-lookup"><span data-stu-id="6990e-106">The service description describes what services are available and how to interact with those services.</span></span> <span data-ttu-id="6990e-107">没有服务说明，就不可能通过编程方式与 Web 服务进行交互。</span><span class="sxs-lookup"><span data-stu-id="6990e-107">Without a service description, it is impossible to programmatically interact with a Web service.</span></span>  
  
 <span data-ttu-id="6990e-108">您的应用程序必须能够通过某种方式与 Web 服务通信并在运行时找到该服务。</span><span class="sxs-lookup"><span data-stu-id="6990e-108">Your application must have a means to communicate with the Web service and to locate it at run time.</span></span> <span data-ttu-id="6990e-109">添加对 Web 服务项目的 Web 引用可以做到这点，这种方法将生成与 Web 服务连接并提供 Web 服务的本地表示形式的代理类。</span><span class="sxs-lookup"><span data-stu-id="6990e-109">Adding a Web reference to your project for the Web service does this by generating a proxy class that interfaces with the Web service and provides a local representation of the Web service.</span></span> <span data-ttu-id="6990e-110">有关详细信息，请参阅 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 文档中的“如何生成 XML Web 服务代理”。</span><span class="sxs-lookup"><span data-stu-id="6990e-110">For more information, see "How to: Generate an XML Web Service Proxy" in your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] documentation.</span></span>  
  
### <a name="to-add-a-web-reference"></a><span data-ttu-id="6990e-111">添加 Web 引用</span><span class="sxs-lookup"><span data-stu-id="6990e-111">To add a Web reference</span></span>  
  
1.  <span data-ttu-id="6990e-112">在 "**项目**" 菜单上，单击**添加服务引用**。</span><span class="sxs-lookup"><span data-stu-id="6990e-112">On the **Project** menu, click **Add Service Reference**.</span></span>  
  
2.  <span data-ttu-id="6990e-113">在 "**添加服务引用**" 对话框中，单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="6990e-113">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
3.  <span data-ttu-id="6990e-114">在 "**服务引用设置**" 对话框中，单击 "**添加 Web 引用**"。</span><span class="sxs-lookup"><span data-stu-id="6990e-114">In the **Service Reference Settings** dialog box, click **Add Web Reference**.</span></span>  
  
4.  <span data-ttu-id="6990e-115">在 "**添加 Web 引用**" 对话框的 " **url** " 框中，键入 Url 以获取报表服务器 Web 服务的服务说明，例如 http://localhost/reportserver/reportservice2010.asmx 。</span><span class="sxs-lookup"><span data-stu-id="6990e-115">In the **URL** box of the **Add Web Reference** dialog box, type the URL to obtain the service description of the Report Server Web service, such as http://localhost/reportserver/reportservice2010.asmx.</span></span> <span data-ttu-id="6990e-116">然后单击 "**开始**" 按钮以检索有关该 Web 服务的信息。</span><span class="sxs-lookup"><span data-stu-id="6990e-116">Then click the **Go** button to retrieve information about the Web service.</span></span>  
  
     <span data-ttu-id="6990e-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="6990e-117">\- or -</span></span>  
  
     <span data-ttu-id="6990e-118">如果本地计算机上存在报表服务器 Web 服务，请在 "浏览器" 窗格中单击 "本地计算机" 链接上的 " **Web 服务**"。</span><span class="sxs-lookup"><span data-stu-id="6990e-118">If the Report Server Web service exists on the local machine, click the **Web services on the local machine** link in the browser pane.</span></span> <span data-ttu-id="6990e-119">然后在提供的列表中单击 ReportService2010 Web 服务的链接。</span><span class="sxs-lookup"><span data-stu-id="6990e-119">Then click the link for the ReportService2010 Web service from the list provided.</span></span>  
  
5.  <span data-ttu-id="6990e-120">在 " **web 引用名称**" 框中，将 web 引用重命名为 ReportService2010，这是将用于该 web 引用的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6990e-120">In the **Web reference name** box, rename the Web reference to ReportService2010, which is the namespace you will use for this Web reference.</span></span>  
  
6.  <span data-ttu-id="6990e-121">单击 "**添加引用**" 以添加目标 web 服务的 web 引用。</span><span class="sxs-lookup"><span data-stu-id="6990e-121">Click **Add Reference** to add a Web reference for the target Web service.</span></span>  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="6990e-122">将下载服务说明并生成一个代理类，以在您的应用程序和报表服务器 Web 服务之间进行连接。</span><span class="sxs-lookup"><span data-stu-id="6990e-122">downloads the service description and generates a proxy class to interface between your application and the Report Server Web service.</span></span> <span data-ttu-id="6990e-123">您还需要添加对 <xref:System.Web.Services> 命名空间的引用，Web 引用才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="6990e-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
7.  <span data-ttu-id="6990e-124">在 "项目" 菜单上，单击 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="6990e-124">On the Project menu, click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="6990e-125">在 "**添加引用**" 对话框的 " **.net** " 选项卡中，选择 " **System.web**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6990e-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
 <span data-ttu-id="6990e-126">有关详细信息，请参阅[访问 SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="6990e-126">For more information, see [Accessing the SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6990e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6990e-127">See Also</span></span>  
 <span data-ttu-id="6990e-128">[报表服务器 Web 服务](../reporting-services/report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="6990e-128">[Report Server Web Service](../reporting-services/report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="6990e-129">[第3课：访问 Web 服务](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="6990e-129">[Lesson 3: Accessing the Web Service](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span></span>  
 [<span data-ttu-id="6990e-130">使用 Visual Basic 或 Visual C&#35; &#40;SSRS 教程访问报表服务器 Web 服务&#41;</span><span class="sxs-lookup"><span data-stu-id="6990e-130">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
