---
title: Web 服务任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2f719a6fb0076a3bb286865199a9cf6a008d32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578992"
---
# <a name="web-service-task"></a><span data-ttu-id="b58af-102">Web 服务任务</span><span class="sxs-lookup"><span data-stu-id="b58af-102">Web Service Task</span></span>
  <span data-ttu-id="b58af-103">Web 服务任务执行 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="b58af-103">The Web Service task executes a Web service method.</span></span> <span data-ttu-id="b58af-104">可以将 Web 服务任务用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="b58af-104">You can use the Web Service task for the following purposes:</span></span>  
  
-   <span data-ttu-id="b58af-105">将 Web 服务方法返回的值写入变量。</span><span class="sxs-lookup"><span data-stu-id="b58af-105">Writing to a variable the values that a Web service method returns.</span></span> <span data-ttu-id="b58af-106">例如，可以从 Web 服务方法获取某天的最高气温，然后使用此值更新设置列值的表达式中使用的变量。</span><span class="sxs-lookup"><span data-stu-id="b58af-106">For example, you could obtain the highest temperature of the day from a Web service method, and then use that value to update a variable that is used in an expression that sets a column value.</span></span>  
  
-   <span data-ttu-id="b58af-107">将 Web 服务方法返回的值写入文件。</span><span class="sxs-lookup"><span data-stu-id="b58af-107">Writing to a file the values that a Web service method returns.</span></span> <span data-ttu-id="b58af-108">例如，可以将潜在客户列表写入一个文件，然后将此文件用作在被写入数据库之前会清除数据的包中的数据源。</span><span class="sxs-lookup"><span data-stu-id="b58af-108">For example, a list of potential customers can be written to a file and the file then used as a data source in a package that cleans the data before it is written to a database.</span></span>  
  
## <a name="wsdl-file"></a><span data-ttu-id="b58af-109">WSDL 文件</span><span class="sxs-lookup"><span data-stu-id="b58af-109">WSDL File</span></span>  
 <span data-ttu-id="b58af-110">Web 服务任务使用 HTTP 连接管理器连接到 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="b58af-110">The Web Service task uses an HTTP connection manager to connect to the Web service.</span></span> <span data-ttu-id="b58af-111">HTTP 连接管理器与 Web 服务任务是单独配置的，在 Web 服务任务中要引用它。</span><span class="sxs-lookup"><span data-stu-id="b58af-111">The HTTP connection manager is configured separately from the Web Service task, and is referenced in the task.</span></span> <span data-ttu-id="b58af-112">HTTP 连接管理器指定服务器代理设置，如服务器 URL、访问 Web 服务服务器的凭据以及超时长度。</span><span class="sxs-lookup"><span data-stu-id="b58af-112">The HTTP connection manager specifies the server proxy settings such as the server URL, credentials for accessing the Web services server, and time-out length.</span></span> <span data-ttu-id="b58af-113">有关详细信息，请参阅 [HTTP 连接管理器](../connection-manager/http-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b58af-113">For more information, see [HTTP Connection Manager](../connection-manager/http-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b58af-114">HTTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="b58af-114">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="b58af-115">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b58af-115">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="b58af-116">HTTP 连接管理器可以指向网站或 Web 服务描述语言 (WSDL) 文件。</span><span class="sxs-lookup"><span data-stu-id="b58af-116">The HTTP connection manager can point to a Web site or to a Web Service Description Language (WSDL) file.</span></span> <span data-ttu-id="b58af-117">指向 WSDL 文件的 HTTP 连接管理器的 URL 中包括 `?WSDL` 参数：例如， `http://MyServer/MyWebService/MyPage.asmx?WSDL`。</span><span class="sxs-lookup"><span data-stu-id="b58af-117">The URL of the HTTP connection manager that points to a WSDL file includes the `?WSDL` parameter: for example, `http://MyServer/MyWebService/MyPage.asmx?WSDL`.</span></span>  
  
 <span data-ttu-id="b58af-118">计算机本地必须有 WSDL 文件，以使用 **设计器提供的** “Web 服务任务编辑器” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 对话框配置 Web 服务任务。</span><span class="sxs-lookup"><span data-stu-id="b58af-118">The WSDL file must be available locally to configure the Web Service task using the **Web Service Task Editor** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span>  
  
-   <span data-ttu-id="b58af-119">如果 HTTP 连接管理器指向网站，则必须手动把 WSDL 文件复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b58af-119">If the HTTP connection manager points to a Web site, the WSDL file must be copied manually to a local computer.</span></span>  
  
-   <span data-ttu-id="b58af-120">如果 HTTP 连接管理器指向 WSDL 文件，那么此文件可以由 Web 服务任务从网站下载到本地文件。</span><span class="sxs-lookup"><span data-stu-id="b58af-120">If the HTTP connection manager points to a WSDL file, the file can be downloaded from the Web site to a local file by the Web Service task.</span></span>  
  
 <span data-ttu-id="b58af-121">WSDL 文件列出 Web 服务提供的方法、方法要求的输入参数、方法返回的响应以及如何与 Web 服务通信。</span><span class="sxs-lookup"><span data-stu-id="b58af-121">The WSDL file lists the methods that the Web service offers, the input parameters that the methods require, the responses that the methods return, and how to communicate with the Web service.</span></span>  
  
 <span data-ttu-id="b58af-122">如果方法使用输入参数，那么 Web 服务任务要求参数值。</span><span class="sxs-lookup"><span data-stu-id="b58af-122">If the method uses input parameters, the Web Service task requires parameter values.</span></span> <span data-ttu-id="b58af-123">例如，需要根据身高建议应该购买多长的滑雪板的 Web 服务方法，就要求在输入参数中提交您的身高。</span><span class="sxs-lookup"><span data-stu-id="b58af-123">For example, a Web service method that recommends the length of skis you should purchase based on your height requires that your height be submitted in an input parameter.</span></span> <span data-ttu-id="b58af-124">该参数值可以通过任务中定义的字符串来提供，也可以通过任务作用域或父级容器中定义的变量来提供。</span><span class="sxs-lookup"><span data-stu-id="b58af-124">The parameter values can be provided either by strings that are defined in the task, or by variables defined in the scope of the task or a parent container.</span></span> <span data-ttu-id="b58af-125">使用变量的优点在于可通过使用包配置或脚本来动态地更新参数值。</span><span class="sxs-lookup"><span data-stu-id="b58af-125">The advantage of using variables is that they let you dynamically update the parameter values by using package configurations or scripts.</span></span> <span data-ttu-id="b58af-126">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[包配置](../package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="b58af-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Package Configurations](../package-configurations.md).</span></span>  
  
 <span data-ttu-id="b58af-127">许多 Web 服务方法不使用输入参数。</span><span class="sxs-lookup"><span data-stu-id="b58af-127">Many Web service methods do not use input parameters.</span></span> <span data-ttu-id="b58af-128">例如，获取本月出生的总统姓名的 Web 服务方法就不需要输入参数，因为该 Web 服务可以在本地确定本月。</span><span class="sxs-lookup"><span data-stu-id="b58af-128">For example, a Web service method that gets the names of presidents who were born in the current month would not require an input parameter because the Web service can determine the current month locally.</span></span>  
  
 <span data-ttu-id="b58af-129">Web 服务方法的结果可以写入变量或文件。</span><span class="sxs-lookup"><span data-stu-id="b58af-129">The results of the Web service method can be written to a variable or to a file.</span></span> <span data-ttu-id="b58af-130">使用文件连接管理器可以指定文件，也可以提供将结果写入的变量名称。</span><span class="sxs-lookup"><span data-stu-id="b58af-130">You use the File connection manager either to specify the file or to provide the name of the variable to write the results to.</span></span> <span data-ttu-id="b58af-131">有关详细信息，请参阅[文件连接管理器](../connection-manager/file-connection-manager.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b58af-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a><span data-ttu-id="b58af-132">Web 服务任务可用的自定义日志记录消息</span><span class="sxs-lookup"><span data-stu-id="b58af-132">Custom Logging Messages Available on the Web Service Task</span></span>  
 <span data-ttu-id="b58af-133">下表列出了可以为 Web 服务任务启用的自定义日志项。</span><span class="sxs-lookup"><span data-stu-id="b58af-133">The following table lists the custom log entries that you can enable for the Web Service task.</span></span> <span data-ttu-id="b58af-134">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](../performance/integration-services-ssis-logging.md)和[日志记录的自定义消息](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="b58af-134">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="b58af-135">日志项</span><span class="sxs-lookup"><span data-stu-id="b58af-135">Log entry</span></span>|<span data-ttu-id="b58af-136">说明</span><span class="sxs-lookup"><span data-stu-id="b58af-136">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="b58af-137">任务已开始访问 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="b58af-137">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="b58af-138">任务已完成 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="b58af-138">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="b58af-139">有关任务的说明性信息。</span><span class="sxs-lookup"><span data-stu-id="b58af-139">Descriptive information about the task.</span></span>|  
  
## <a name="configuration-of-the-web-service-task"></a><span data-ttu-id="b58af-140">Web 服务任务的配置</span><span class="sxs-lookup"><span data-stu-id="b58af-140">Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="b58af-141">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="b58af-141">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b58af-142">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="b58af-142">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b58af-143">Web 服务任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="b58af-143">Web Service Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="b58af-144">Web 服务任务编辑器（“输入”页）</span><span class="sxs-lookup"><span data-stu-id="b58af-144">Web Service Task Editor &#40;Input Page&#41;</span></span>](../web-service-task-editor-input-page.md)  
  
-   [<span data-ttu-id="b58af-145">Web 服务任务编辑器（“输出”页）</span><span class="sxs-lookup"><span data-stu-id="b58af-145">Web Service Task Editor &#40;Output Page&#41;</span></span>](../web-service-task-editor-output-page.md)  
  
-   [<span data-ttu-id="b58af-146">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="b58af-146">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="b58af-147">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="b58af-147">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="b58af-148">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="b58af-148">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a><span data-ttu-id="b58af-149">Web 服务任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="b58af-149">Programmatic Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="b58af-150">有关以编程方式设置这些属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="b58af-150">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a><span data-ttu-id="b58af-151">相关内容</span><span class="sxs-lookup"><span data-stu-id="b58af-151">Related Content</span></span>  
 <span data-ttu-id="b58af-152">MSDN 库中的视频[操作说明：使用 Web 服务任务调用 Web 服务（SQL Server 视频）](https://go.microsoft.com/fwlink/?LinkId=259642)。</span><span class="sxs-lookup"><span data-stu-id="b58af-152">Video, [How to: Call a Web Service by Using the Web Service Task (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=259642), on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="b58af-153">[如何通过 SSIS 包使用 Web 服务](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/)。</span><span class="sxs-lookup"><span data-stu-id="b58af-153">[How To Consume Web Service Through SSIS Package](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/).</span></span>  
  
  
