---
title: 捕获登录触发器事件数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
ms.openlocfilehash: b11323702d7468d07783b4d1c763dba691479d9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590649"
---
# <a name="capture-logon-trigger-event-data"></a><span data-ttu-id="b2b6e-102">捕获登录触发器事件数据</span><span class="sxs-lookup"><span data-stu-id="b2b6e-102">Capture Logon Trigger Event Data</span></span>
  <span data-ttu-id="b2b6e-103">若要捕获有关 LOGON 事件的 XML 数据以在登录触发器内部使用，请使用 [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-103">To capture XML data about LOGON events for use inside logon triggers, use the [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) function.</span></span> <span data-ttu-id="b2b6e-104">LOGON 事件将返回以下事件数据架构：</span><span class="sxs-lookup"><span data-stu-id="b2b6e-104">The LOGON event returns the following event data schema:</span></span>  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 <span data-ttu-id="b2b6e-105">包含 `LOGON`。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-105">Contains `LOGON`.</span></span>  
  
 `<PostTime>`  
 <span data-ttu-id="b2b6e-106">包含请求建立会话时的时间。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-106">Contains the time when a session is requested to be established.</span></span>  
  
 `<SID>`  
 <span data-ttu-id="b2b6e-107">包含指定登录名的安全标识号 (SID) 的 Base 64 编码二进制流。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-107">Contains the base 64-encoded binary stream of the security identification number (SID) for the specified login name.</span></span>  
  
 `<ClientHost>`  
 <span data-ttu-id="b2b6e-108">包含建立连接的客户端的主机名。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-108">Contains the host name of the client from where the connection is made.</span></span> <span data-ttu-id="b2b6e-109">如果客户端和服务器名称相同，则此值为“`<local_machine>`”。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-109">The value is '`<local_machine>`' if the client and server name are the same.</span></span> <span data-ttu-id="b2b6e-110">否则，此值为客户端的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-110">Otherwise, the value is the IP address of the client.</span></span>  
  
 `<IsPooled>`  
 <span data-ttu-id="b2b6e-111">如果通过使用连接池重用连接，则此值为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-111">Is `1` if the connection is reused by using connection pooling.</span></span> <span data-ttu-id="b2b6e-112">否则，此值为 `0`。</span><span class="sxs-lookup"><span data-stu-id="b2b6e-112">Otherwise, the value is `0`.</span></span>  
  
  
