---
title: HTTP 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10c9f0778faa25aff8db4ad54ecaa8d3ccc5b359
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693012"
---
# <a name="http-connection-manager"></a><span data-ttu-id="c004c-102">HTTP 连接管理器</span><span class="sxs-lookup"><span data-stu-id="c004c-102">HTTP Connection Manager</span></span>
  <span data-ttu-id="c004c-103">利用 HTTP 连接，包可以使用 HTTP 访问 Web 服务器以发送或接收文件。</span><span class="sxs-lookup"><span data-stu-id="c004c-103">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="c004c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的 Web 服务任务使用此连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c004c-104">The Web Service task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="c004c-105">将 HTTP 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定 HTTP 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="c004c-105">When you add an HTTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an HTTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="c004c-106">`ConnectionManagerType`连接管理器的属性设置为`HTTP.`</span><span class="sxs-lookup"><span data-stu-id="c004c-106">The `ConnectionManagerType` property of the connection manager is set to `HTTP.`</span></span>  
  
 <span data-ttu-id="c004c-107">可以通过下列方式配置 HTTP 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="c004c-107">You can configure the HTTP connection manager the following ways:</span></span>  
  
-   <span data-ttu-id="c004c-108">使用凭据。</span><span class="sxs-lookup"><span data-stu-id="c004c-108">Use credentials.</span></span> <span data-ttu-id="c004c-109">如果连接管理器使用凭据，则其属性包含用户名、密码和域。</span><span class="sxs-lookup"><span data-stu-id="c004c-109">If the connection manager uses credentials, its properties include the user name, password, and domain.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c004c-110">HTTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="c004c-110">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="c004c-111">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c004c-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="c004c-112">使用客户端证书。</span><span class="sxs-lookup"><span data-stu-id="c004c-112">Use a client certificate.</span></span> <span data-ttu-id="c004c-113">如果连接管理器使用客户端证书，则其属性包含证书名称。</span><span class="sxs-lookup"><span data-stu-id="c004c-113">If the connection manager uses a client certificate, its properties include the certificate name.</span></span>  
  
-   <span data-ttu-id="c004c-114">提供连接到服务器的超时值和写入数据的块区大小。</span><span class="sxs-lookup"><span data-stu-id="c004c-114">Provide a time-out for connecting to the server and a chunk size for writing data.</span></span>  
  
-   <span data-ttu-id="c004c-115">使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="c004c-115">Use a proxy server.</span></span> <span data-ttu-id="c004c-116">也可以将代理服务器配置为使用凭据，并跳过代理服务器而使用本地地址。</span><span class="sxs-lookup"><span data-stu-id="c004c-116">The proxy server can also be configured to use credentials and to bypass the proxy server and use local addresses instead.</span></span>  
  
## <a name="configuration-of-the-http-connection-manager"></a><span data-ttu-id="c004c-117">HTTP 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="c004c-117">Configuration of the HTTP Connection Manager</span></span>  
 <span data-ttu-id="c004c-118">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="c004c-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c004c-119">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="c004c-119">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c004c-120">HTTP 连接管理器编辑器（“服务器”页）</span><span class="sxs-lookup"><span data-stu-id="c004c-120">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../http-connection-manager-editor-server-page.md)  
  
-   [<span data-ttu-id="c004c-121">HTTP 连接管理器编辑器（“代理”页）</span><span class="sxs-lookup"><span data-stu-id="c004c-121">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../http-connection-manager-editor-proxy-page.md)  
  
 <span data-ttu-id="c004c-122">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>。</span><span class="sxs-lookup"><span data-stu-id="c004c-122">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c004c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c004c-123">See Also</span></span>  
 <span data-ttu-id="c004c-124">[Web 服务任务](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="c004c-124">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="c004c-125">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="c004c-125">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
