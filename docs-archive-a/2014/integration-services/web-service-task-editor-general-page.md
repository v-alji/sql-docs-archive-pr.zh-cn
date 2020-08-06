---
title: Web 服务任务编辑器 ("常规" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dbacf2a2a867ab01039678ff4f43eebac839c11a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590267"
---
# <a name="web-service-task-editor-general-page"></a><span data-ttu-id="df1e2-102">Web 服务任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="df1e2-102">Web Service Task Editor (General Page)</span></span>
  <span data-ttu-id="df1e2-103">使用“Web 服务任务编辑器”  对话框的“常规”  页，可以指定 HTTP 连接管理器，指定 Web 服务任务所使用的 Web 服务描述语言 (WSDL) 文件的位置，对 Web 服务任务进行说明，以及下载 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-103">Use the **General** page of the **Web Services Task Editor** dialog box to specify an HTTP connection manager, specify the location of the Web Services Description Language (WSDL) file the Web Service task uses, describe the Web Services task, and download the WSDL file.</span></span>  
  
 <span data-ttu-id="df1e2-104">有关此任务的详细信息，请参阅 [Web 服务任务](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="df1e2-104">For more information about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="df1e2-105">选项</span><span class="sxs-lookup"><span data-stu-id="df1e2-105">Options</span></span>  
 <span data-ttu-id="df1e2-106">**HTTPConnection**</span><span class="sxs-lookup"><span data-stu-id="df1e2-106">**HTTPConnection**</span></span>  
 <span data-ttu-id="df1e2-107">从列表中选择连接管理器，或单击“\<**New connection...**>”以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="df1e2-107">Select a connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df1e2-108">HTTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="df1e2-108">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="df1e2-109">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="df1e2-109">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="df1e2-110">**相关主题：** [HTTP 连接管理器](connection-manager/http-connection-manager.md)、[HTTP 连接管理器编辑器（“服务器”页）](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="df1e2-110">**Related Topics:**  [HTTP Connection Manager](connection-manager/http-connection-manager.md), [HTTP Connection Manager Editor &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span></span>  
  
 <span data-ttu-id="df1e2-111">**WSDLFile**</span><span class="sxs-lookup"><span data-stu-id="df1e2-111">**WSDLFile**</span></span>  
 <span data-ttu-id="df1e2-112">键入计算机本地上 WSDL 文件的完全限定路径，或单击浏览按钮 (…) 并定位到该文件  。</span><span class="sxs-lookup"><span data-stu-id="df1e2-112">Type the fully qualified path of a WSDL file that is local to the computer, or click the browse button **(...)** and locate this file.</span></span>  
  
 <span data-ttu-id="df1e2-113">如果您已经将该 WSDL 文件手动下载到计算机，请选择此文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-113">If you have already manually downloaded the WSDL file to the computer, select this file.</span></span> <span data-ttu-id="df1e2-114">但是，如果尚未下载该 WSDL 文件，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="df1e2-114">However, if the WSDL file has not yet been downloaded, follow these steps:</span></span>  
  
-   <span data-ttu-id="df1e2-115">创建文件扩展名为“.wsdl”的空文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-115">Create an empty file that has the ".wsdl" file name extension.</span></span>  
  
-   <span data-ttu-id="df1e2-116">为 **WSDLFile** 选项选择此空文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-116">Select this empty file for the **WSDLFile** option.</span></span>  
  
-   <span data-ttu-id="df1e2-117">将**OverwriteWSDLFile**的值设置为 `True` ，以允许使用实际的 WSDL 文件覆盖空文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-117">Set the value of **OverwriteWSDLFile** to `True` to enable the empty file to be overwritten with the actual WSDL file.</span></span>  
  
-   <span data-ttu-id="df1e2-118">单击 **“下载 WSDL”** 下载实际 WSDL 文件，并覆盖空文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-118">Click **Download WSDL** to download the actual WSDL file and overwrite the empty file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df1e2-119">在“WSDLFile”  框中提供现有本地文件的名称后，才会启用“下载 WSDL”  选项。</span><span class="sxs-lookup"><span data-stu-id="df1e2-119">The **Download WSDL** option is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
 <span data-ttu-id="df1e2-120">**OverwriteWSDLFile**</span><span class="sxs-lookup"><span data-stu-id="df1e2-120">**OverwriteWSDLFile**</span></span>  
 <span data-ttu-id="df1e2-121">指示是否可以覆盖 Web 服务任务的 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-121">Indicate whether the WSDL file for the Web Service task can be overwritten.</span></span>  
  
 <span data-ttu-id="df1e2-122">如果要使用 "**下载 wsdl** " 按钮下载 WSDL 文件，请将此值设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="df1e2-122">If you intend to download the WSDL file by using the **Download WSDL** button, set this value to `True`.</span></span>  
  
 <span data-ttu-id="df1e2-123">**名称**</span><span class="sxs-lookup"><span data-stu-id="df1e2-123">**Name**</span></span>  
 <span data-ttu-id="df1e2-124">为 Web 服务任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="df1e2-124">Provide a unique name for the Web Service task.</span></span> <span data-ttu-id="df1e2-125">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="df1e2-125">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df1e2-126">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="df1e2-126">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="df1e2-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="df1e2-127">**Description**</span></span>  
 <span data-ttu-id="df1e2-128">键入 Web 服务任务的说明。</span><span class="sxs-lookup"><span data-stu-id="df1e2-128">Type a description of the Web Service task.</span></span>  
  
 <span data-ttu-id="df1e2-129">**“下载 WSDL”**</span><span class="sxs-lookup"><span data-stu-id="df1e2-129">**Download WSDL**</span></span>  
 <span data-ttu-id="df1e2-130">下载 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="df1e2-130">Download the WSDL file.</span></span>  
  
 <span data-ttu-id="df1e2-131">当您在 **WSDLFile** 框中提供现有本地文件的名称后，该按钮才会启用。</span><span class="sxs-lookup"><span data-stu-id="df1e2-131">This button is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1e2-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df1e2-132">See Also</span></span>  
 <span data-ttu-id="df1e2-133">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="df1e2-133">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="df1e2-134">[Web 服务任务编辑器 &#40;输入页&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="df1e2-134">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 <span data-ttu-id="df1e2-135">[Web 服务任务编辑器 &#40;输出页&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="df1e2-135">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="df1e2-136">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="df1e2-136">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
