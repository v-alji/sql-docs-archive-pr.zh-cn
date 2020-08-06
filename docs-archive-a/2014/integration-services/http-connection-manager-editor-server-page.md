---
title: HTTP 连接管理器编辑器 (服务器页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2349766b11b28ff258496dc966d554d49c7657b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578317"
---
# <a name="http-connection-manager-editor-server-page"></a><span data-ttu-id="8d564-102">HTTP 连接管理器编辑器（“服务器”页）</span><span class="sxs-lookup"><span data-stu-id="8d564-102">HTTP Connection Manager Editor (Server Page)</span></span>
  <span data-ttu-id="8d564-103">使用 **“HTTP 连接管理器编辑器”** 对话框的 **“服务器”** 选项卡，可以通过指定 URL 和安全凭据等属性来配置 HTTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="8d564-103">Use the **Server** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager by specifying properties such as the URL and security credentials.</span></span> <span data-ttu-id="8d564-104">利用 HTTP 连接，包可以使用 HTTP 访问 Web 服务器以发送或接收文件。</span><span class="sxs-lookup"><span data-stu-id="8d564-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="8d564-105">配置 HTTP 连接管理器后，还可以测试该连接。</span><span class="sxs-lookup"><span data-stu-id="8d564-105">After configuring the HTTP Connection Manager, you can also test the connection.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8d564-106">HTTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="8d564-106">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="8d564-107">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="8d564-107">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="8d564-108">若要了解有关 HTTP 连接管理器的详细信息，请参阅 [HTTP Connection Manager](connection-manager/http-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="8d564-108">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="8d564-109">若要了解有关 HTTP 连接管理器的常见使用方案的详细信息，请参阅 [Web Service Task](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="8d564-109">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8d564-110">选项</span><span class="sxs-lookup"><span data-stu-id="8d564-110">Options</span></span>  
 <span data-ttu-id="8d564-111">**服务器 URL**</span><span class="sxs-lookup"><span data-stu-id="8d564-111">**Server URL**</span></span>  
 <span data-ttu-id="8d564-112">键入服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="8d564-112">Type the URL for the server.</span></span>  
  
 <span data-ttu-id="8d564-113">如果您计划使用 **“Web 服务任务编辑器”** 的 **“常规”** 页上的 **“下载 WSDL”** 按钮来下载 WSDL 文件，请键入 WSDL 文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="8d564-113">If you plan to use the **Download WSDL** button on the **General** page of the **Web Service Task Editor** to download a WSDL file, type the URL for the WSDL file.</span></span> <span data-ttu-id="8d564-114">此 URL 要以“?wsdl”结尾。</span><span class="sxs-lookup"><span data-stu-id="8d564-114">This URL ends with "?wsdl".</span></span>  
  
 <span data-ttu-id="8d564-115">**使用凭据**</span><span class="sxs-lookup"><span data-stu-id="8d564-115">**Use credentials**</span></span>  
 <span data-ttu-id="8d564-116">指定是否希望 HTTP 连接管理器使用用户安全凭据进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="8d564-116">Specify whether you want the HTTP Connection Manager to use the user's security credentials for authentication.</span></span>  
  
 <span data-ttu-id="8d564-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="8d564-117">**User name**</span></span>  
 <span data-ttu-id="8d564-118">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="8d564-118">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="8d564-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="8d564-119">**Password**</span></span>  
 <span data-ttu-id="8d564-120">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="8d564-120">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="8d564-121">**Domain**</span><span class="sxs-lookup"><span data-stu-id="8d564-121">**Domain**</span></span>  
 <span data-ttu-id="8d564-122">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="8d564-122">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="8d564-123">**使用客户端证书**</span><span class="sxs-lookup"><span data-stu-id="8d564-123">**Use client certificate**</span></span>  
 <span data-ttu-id="8d564-124">指定是否希望 HTTP 连接管理器使用客户端证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="8d564-124">Specify whether you want the HTTP Connection Manager to use a client certificate for authentication.</span></span>  
  
 <span data-ttu-id="8d564-125">**证书**</span><span class="sxs-lookup"><span data-stu-id="8d564-125">**Certificate**</span></span>  
 <span data-ttu-id="8d564-126">使用“选择证书”对话框从列表中选择证书。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8d564-126">Select a certificate from the list by using the **Select Certificate** dialog box.</span></span> <span data-ttu-id="8d564-127">文本框显示与此证书关联的名称。</span><span class="sxs-lookup"><span data-stu-id="8d564-127">The text box displays the name associated with this certificate.</span></span>  
  
 <span data-ttu-id="8d564-128">**超时值(秒)**</span><span class="sxs-lookup"><span data-stu-id="8d564-128">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="8d564-129">提供连接 Web 服务器时允许的超时值。</span><span class="sxs-lookup"><span data-stu-id="8d564-129">Provide a time-out for connecting to the Web server.</span></span> <span data-ttu-id="8d564-130">此属性的默认值为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="8d564-130">The default value of this property is 30 seconds.</span></span>  
  
 <span data-ttu-id="8d564-131">**块区大小(KB)**</span><span class="sxs-lookup"><span data-stu-id="8d564-131">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="8d564-132">提供用于写入数据的块区大小。</span><span class="sxs-lookup"><span data-stu-id="8d564-132">Provide a chunk size for writing data.</span></span>  
  
 <span data-ttu-id="8d564-133">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="8d564-133">**Test Connection**</span></span>  
 <span data-ttu-id="8d564-134">在配置 HTTP 连接管理器后，请通过单击“测试连接”确认该连接是否正常。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8d564-134">After configuring the HTTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d564-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d564-135">See Also</span></span>  
 <span data-ttu-id="8d564-136">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8d564-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="8d564-137">HTTP 连接管理器编辑器（“代理”页）</span><span class="sxs-lookup"><span data-stu-id="8d564-137">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)  
  
  
