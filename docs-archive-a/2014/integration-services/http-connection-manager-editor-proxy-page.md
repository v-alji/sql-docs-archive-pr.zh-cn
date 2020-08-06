---
title: HTTP 连接管理器编辑器 (Proxy Page) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8269dbbeb226ffa3f56c226e1a416d99c1e3f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578322"
---
# <a name="http-connection-manager-editor-proxy-page"></a><span data-ttu-id="30382-102">HTTP 连接管理器编辑器（“代理”页）</span><span class="sxs-lookup"><span data-stu-id="30382-102">HTTP Connection Manager Editor (Proxy Page)</span></span>
  <span data-ttu-id="30382-103">可以使用 **“HTTP 连接管理器编辑器”** 对话框的 **“代理”** 选项卡配置 HTTP 连接管理器以使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="30382-103">Use the **Proxy** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager to use a proxy server.</span></span> <span data-ttu-id="30382-104">利用 HTTP 连接，包可以使用 HTTP 访问 Web 服务器以发送或接收文件。</span><span class="sxs-lookup"><span data-stu-id="30382-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span>  
  
 <span data-ttu-id="30382-105">若要了解有关 HTTP 连接管理器的详细信息，请参阅 [HTTP Connection Manager](connection-manager/http-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="30382-105">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="30382-106">若要了解有关 HTTP 连接管理器的常见使用方案的详细信息，请参阅 [Web Service Task](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="30382-106">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="30382-107">选项</span><span class="sxs-lookup"><span data-stu-id="30382-107">Options</span></span>  
 <span data-ttu-id="30382-108">**使用代理**</span><span class="sxs-lookup"><span data-stu-id="30382-108">**Use proxy**</span></span>  
 <span data-ttu-id="30382-109">指定是否希望通过代理服务器连接 HTTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="30382-109">Specify whether you want the HTTP Connection Manager to connect through a proxy server.</span></span>  
  
 <span data-ttu-id="30382-110">**代理 URL**</span><span class="sxs-lookup"><span data-stu-id="30382-110">**Proxy URL**</span></span>  
 <span data-ttu-id="30382-111">键入代理服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="30382-111">Type the URL for the proxy server.</span></span>  
  
 <span data-ttu-id="30382-112">**跳过本地代理**</span><span class="sxs-lookup"><span data-stu-id="30382-112">**Bypass proxy on local**</span></span>  
 <span data-ttu-id="30382-113">指定是否希望 HTTP 连接管理器对于本地地址跳过代理服务器。</span><span class="sxs-lookup"><span data-stu-id="30382-113">Specify whether you want the HTTP Connection Manager to bypass the proxy server for local addresses.</span></span>  
  
 <span data-ttu-id="30382-114">**使用凭据**</span><span class="sxs-lookup"><span data-stu-id="30382-114">**Use credentials**</span></span>  
 <span data-ttu-id="30382-115">指定是否希望 HTTP 连接管理器对于代理服务器使用安全凭据。</span><span class="sxs-lookup"><span data-stu-id="30382-115">Specify whether you want the HTTP Connection Manager to use security credentials for the proxy server.</span></span>  
  
 <span data-ttu-id="30382-116">**用户名**</span><span class="sxs-lookup"><span data-stu-id="30382-116">**User name**</span></span>  
 <span data-ttu-id="30382-117">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="30382-117">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="30382-118">**密码**</span><span class="sxs-lookup"><span data-stu-id="30382-118">**Password**</span></span>  
 <span data-ttu-id="30382-119">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="30382-119">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="30382-120">**Domain**</span><span class="sxs-lookup"><span data-stu-id="30382-120">**Domain**</span></span>  
 <span data-ttu-id="30382-121">如果 HTTP 连接管理器使用凭据，则必须指定用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="30382-121">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="30382-122">**代理跳过列表**</span><span class="sxs-lookup"><span data-stu-id="30382-122">**Proxy bypass list**</span></span>  
 <span data-ttu-id="30382-123">要跳过代理服务器的地址的列表。</span><span class="sxs-lookup"><span data-stu-id="30382-123">The list of addresses for which  you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="30382-124">**添加**</span><span class="sxs-lookup"><span data-stu-id="30382-124">**Add**</span></span>  
 <span data-ttu-id="30382-125">键入要跳过代理服务器的地址。</span><span class="sxs-lookup"><span data-stu-id="30382-125">Type an address for which you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="30382-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="30382-126">**Remove**</span></span>  
 <span data-ttu-id="30382-127">选择某个地址，再单击“删除”\*\*\*\* 即可将其删除。</span><span class="sxs-lookup"><span data-stu-id="30382-127">Select an address, and then remove it by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30382-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30382-128">See Also</span></span>  
 <span data-ttu-id="30382-129">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="30382-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="30382-130">HTTP 连接管理器编辑器（“服务器”页）</span><span class="sxs-lookup"><span data-stu-id="30382-130">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
  
