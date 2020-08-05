---
title: " (XMLA) 管理连接和会话 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bfe876f6874193fd0885f16d91caa9f6fe8b172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580962"
---
# <a name="managing-connections-and-sessions-xmla"></a><span data-ttu-id="098ee-102">管理连接和会话 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="098ee-102">Managing Connections and Sessions (XMLA)</span></span>
  <span data-ttu-id="098ee-103">*有状态*是服务器在方法调用之间保留客户端的标识和上下文的条件。</span><span class="sxs-lookup"><span data-stu-id="098ee-103">*Statefulness* is a condition during which the server preserves the identity and context of a client between method calls.</span></span> <span data-ttu-id="098ee-104">*情形*是在方法调用完成后服务器不记得客户端的标识和上下文的情况。</span><span class="sxs-lookup"><span data-stu-id="098ee-104">*Statelessness* is a condition during which the server does not remember the identity and context of a client after a method call finishes.</span></span>  
  
 <span data-ttu-id="098ee-105">为了提供有状态，XML for Analysis (XMLA) 支持允许一系列语句一起执行的*会话*。</span><span class="sxs-lookup"><span data-stu-id="098ee-105">To provide statefulness, XML for Analysis (XMLA) supports *sessions* that allow a series of statements to be performed together.</span></span> <span data-ttu-id="098ee-106">例如，创建要在后续查询中使用的计算成员就是这样的一系列语句。</span><span class="sxs-lookup"><span data-stu-id="098ee-106">An example of such a series of statements would be the creation of a calculated member that is to be used in subsequent queries.</span></span>  
  
 <span data-ttu-id="098ee-107">通常，XMLA 中的会话遵循 OLE DB 2.6 规范中所述的以下行为：</span><span class="sxs-lookup"><span data-stu-id="098ee-107">In general, sessions in XMLA follow the following behavior outlined by the OLE DB 2.6 specification:</span></span>  
  
-   <span data-ttu-id="098ee-108">会话定义事务和命令上下文范围。</span><span class="sxs-lookup"><span data-stu-id="098ee-108">Sessions define transaction and command context scope.</span></span>  
  
-   <span data-ttu-id="098ee-109">可以在一个会话的上下文中运行多个命令。</span><span class="sxs-lookup"><span data-stu-id="098ee-109">Multiple commands can be run in the context of a single session.</span></span>  
  
-   <span data-ttu-id="098ee-110">XMLA 上下文中对事务的支持是使用[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法发送的特定于访问接口的命令。</span><span class="sxs-lookup"><span data-stu-id="098ee-110">Support for transactions in the XMLA context is through provider-specific commands sent with the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
 <span data-ttu-id="098ee-111">XMLA 定义了一种方法，用于在 Web 环境中以与分布式创作和版本管理 (DAV) 协议所使用的方法类似的模式支持会话，以便在松散耦合环境中实现锁定。</span><span class="sxs-lookup"><span data-stu-id="098ee-111">XMLA defines a way to support sessions in a Web environment in a mode similar to the approach used by the Distributed Authoring and Versioning (DAV) protocol to implement locking in a loosely coupled environment.</span></span> <span data-ttu-id="098ee-112">此实现遵循 DAV，允许访问接口由于各种原因而终止会话（例如超时或连接错误）。</span><span class="sxs-lookup"><span data-stu-id="098ee-112">This implementation parallels DAV in that the provider is allowed to expire sessions for various reasons (for example, a timeout or connection error).</span></span> <span data-ttu-id="098ee-113">支持会话时，Web 服务必须能够知道必须重新启动的已中断命令集，并准备好进行处理。</span><span class="sxs-lookup"><span data-stu-id="098ee-113">When sessions are supported, Web services must be aware and ready to handle interrupted sets of commands that must be restarted.</span></span>  
  
 <span data-ttu-id="098ee-114">万维网联盟 (W3C) 简单对象访问协议 (SOAP) 规范建议在 SOAP 消息的最前面使用 SOAP 标头以构建新协议。</span><span class="sxs-lookup"><span data-stu-id="098ee-114">The World Wide Web Consortium (W3C) Simple Object Access Protocol (SOAP) specification recommends using SOAP headers for building up new protocols on top of SOAP messages.</span></span> <span data-ttu-id="098ee-115">下表列出了 XMLA 定义的用于启动、维护和关闭会话的 SOAP 标头元素和属性。</span><span class="sxs-lookup"><span data-stu-id="098ee-115">The following table lists the SOAP header elements and attributes that XMLA defines for initiating, maintaining, and closing a session.</span></span>  
  
|<span data-ttu-id="098ee-116">SOAP Header — SOAP 标头</span><span class="sxs-lookup"><span data-stu-id="098ee-116">SOAP header</span></span>|<span data-ttu-id="098ee-117">说明</span><span class="sxs-lookup"><span data-stu-id="098ee-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="098ee-118">BeginSession</span><span class="sxs-lookup"><span data-stu-id="098ee-118">BeginSession</span></span>|<span data-ttu-id="098ee-119">此标头请求访问接口创建新会话。</span><span class="sxs-lookup"><span data-stu-id="098ee-119">This header requests the provider to create a new session.</span></span> <span data-ttu-id="098ee-120">访问接口应通过以下方式进行响应：构造新会话并将会话 ID 作为 SOAP 响应中 Session 标头的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="098ee-120">The provider should respond by constructing a new session and returning the session ID as part of the Session header in the SOAP response.</span></span>|  
|<span data-ttu-id="098ee-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="098ee-121">SessionId</span></span>|<span data-ttu-id="098ee-122">值区域包含会话 ID，在该会话此后的每个方法调用中都必须使用此 ID。</span><span class="sxs-lookup"><span data-stu-id="098ee-122">The value area contains the session ID that must be used in each method call for the rest of the session.</span></span> <span data-ttu-id="098ee-123">SOAP 响应中的访问接口会发送此标记，客户端也必须在每个 Session 标头元素中发送此属性。</span><span class="sxs-lookup"><span data-stu-id="098ee-123">The provider in the SOAP response sends this tag and the client must also send this attribute with each Session header element.</span></span>|  
|<span data-ttu-id="098ee-124">会话</span><span class="sxs-lookup"><span data-stu-id="098ee-124">Session</span></span>|<span data-ttu-id="098ee-125">对于会话中发生的每个方法调用，都必须使用此标头，此标头的值区域中必须包含会话 ID。</span><span class="sxs-lookup"><span data-stu-id="098ee-125">For every method call that occurs in the session, this header must be used, and the session ID must be included in the value area of the header.</span></span>|  
|<span data-ttu-id="098ee-126">EndSession</span><span class="sxs-lookup"><span data-stu-id="098ee-126">EndSession</span></span>|<span data-ttu-id="098ee-127">若要终止会话，请使用此标头。</span><span class="sxs-lookup"><span data-stu-id="098ee-127">To terminate the session, use this header.</span></span> <span data-ttu-id="098ee-128">值区域中必须包含会话 ID。</span><span class="sxs-lookup"><span data-stu-id="098ee-128">The session ID must be included with the value area.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="098ee-129">会话 ID 并不保证会话保持有效。</span><span class="sxs-lookup"><span data-stu-id="098ee-129">A session ID does not guarantee that a session stays valid.</span></span> <span data-ttu-id="098ee-130">如果会话过期 (例如，如果它超时或连接丢失) ，则提供程序可以选择结束和回滚该会话的操作。</span><span class="sxs-lookup"><span data-stu-id="098ee-130">If the session expires (for example, if it times out or the connection is lost), the provider can choose to end and roll back that session's actions.</span></span> <span data-ttu-id="098ee-131">因此，来自客户端的对会话 ID 的所有后续方法调用都将失败，返回错误以通知会话无效。</span><span class="sxs-lookup"><span data-stu-id="098ee-131">As a result, all subsequent method calls from the client on a session ID fail with an error signaling a session that is not valid.</span></span> <span data-ttu-id="098ee-132">客户端应处理此情况，并准备从头开始重新发送这些会话方法调用。</span><span class="sxs-lookup"><span data-stu-id="098ee-132">A client should handle this condition and be prepared to resend the session method calls from the beginning.</span></span>  
  
## <a name="legacy-code-example"></a><span data-ttu-id="098ee-133">旧代码示例</span><span class="sxs-lookup"><span data-stu-id="098ee-133">Legacy Code Example</span></span>  
 <span data-ttu-id="098ee-134">下面的示例演示如何支持会话。</span><span class="sxs-lookup"><span data-stu-id="098ee-134">The following example shows how sessions are supported.</span></span>  
  
1.  <span data-ttu-id="098ee-135">若要开始会话，请在 SOAP 中将 BeginSession 标头添加到来自客户端的出站 XMLA 方法调用中。</span><span class="sxs-lookup"><span data-stu-id="098ee-135">To begin the session, add a BeginSession header in SOAP to the outbound XMLA method call from the client.</span></span> <span data-ttu-id="098ee-136">值区域最初是空白的，因为会话 ID 还是未知的。</span><span class="sxs-lookup"><span data-stu-id="098ee-136">The value area is initially blank because the session ID is not yet known.</span></span>  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  <span data-ttu-id="098ee-137">提供程序中的 SOAP 响应消息使用 XMLA 标头标记在返回标头区域中包含会话 ID \<SessionId> 。</span><span class="sxs-lookup"><span data-stu-id="098ee-137">The SOAP response message from the provider includes the session ID in the return header area, using the XMLA header tag \<SessionId>.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  <span data-ttu-id="098ee-138">会话中的每个方法调用都必须添加 Session 标头，其中包含从访问接口返回的会话 ID。</span><span class="sxs-lookup"><span data-stu-id="098ee-138">For each method call in the session, the Session header must be added, containing the session ID returned from the provider.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  <span data-ttu-id="098ee-139">会话完成时，将 \<EndSession> 使用标记，其中包含相关的会话 ID 值。</span><span class="sxs-lookup"><span data-stu-id="098ee-139">When the session is complete, the \<EndSession> tag is used, containing the related session ID value.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="098ee-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="098ee-140">See Also</span></span>  
 [<span data-ttu-id="098ee-141">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="098ee-141">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
