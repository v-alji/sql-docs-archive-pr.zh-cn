---
title: FTP 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d14635a4d90c267801f6d372dda5c7bcc7f4869f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694521"
---
# <a name="ftp-connection-manager-editor"></a><span data-ttu-id="6213b-102">FTP 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="6213b-102">FTP Connection Manager Editor</span></span>
  <span data-ttu-id="6213b-103">使用 **“FTP 连接管理器编辑器”** 对话框可以指定用于连接到 FTP 服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="6213b-103">Use the **FTP Connection Manager Editor** dialog box to specify properties for connecting to an FTP server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6213b-104">FTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="6213b-104">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="6213b-105">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="6213b-105">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="6213b-106">若要了解有关 FTP 连接管理器的详细信息，请参阅 [FTP Connection Manager](connection-manager/ftp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="6213b-106">To learn more about the FTP connection manager, see [FTP Connection Manager](connection-manager/ftp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6213b-107">选项</span><span class="sxs-lookup"><span data-stu-id="6213b-107">Options</span></span>  
 <span data-ttu-id="6213b-108">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="6213b-108">**Server name**</span></span>  
 <span data-ttu-id="6213b-109">提供 FTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6213b-109">Provide the name of the FTP server.</span></span>  
  
 <span data-ttu-id="6213b-110">**服务器端口**</span><span class="sxs-lookup"><span data-stu-id="6213b-110">**Server port**</span></span>  
 <span data-ttu-id="6213b-111">指定用来连接的 FTP 服务器的端口号。</span><span class="sxs-lookup"><span data-stu-id="6213b-111">Specify the port number on the FTP server to use for the connection.</span></span> <span data-ttu-id="6213b-112">此属性的默认值为 **21**。</span><span class="sxs-lookup"><span data-stu-id="6213b-112">The default value of this property is **21**.</span></span>  
  
 <span data-ttu-id="6213b-113">**用户名**</span><span class="sxs-lookup"><span data-stu-id="6213b-113">**User name**</span></span>  
 <span data-ttu-id="6213b-114">提供用于访问 FTP 服务器的用户名。</span><span class="sxs-lookup"><span data-stu-id="6213b-114">Provide a user name to access the FTP server.</span></span> <span data-ttu-id="6213b-115">此属性的默认值为“匿名”。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6213b-115">The default value of this property is **anonymous**.</span></span>  
  
 <span data-ttu-id="6213b-116">**密码**</span><span class="sxs-lookup"><span data-stu-id="6213b-116">**Password**</span></span>  
 <span data-ttu-id="6213b-117">提供用于访问 FTP 服务器的密码。</span><span class="sxs-lookup"><span data-stu-id="6213b-117">Provide the password to access the FTP server.</span></span>  
  
 <span data-ttu-id="6213b-118">**超时值(秒)**</span><span class="sxs-lookup"><span data-stu-id="6213b-118">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="6213b-119">指定在超时之前任务所用的秒数。值**0**指示无限长的时间。</span><span class="sxs-lookup"><span data-stu-id="6213b-119">Specify the number of seconds the task takes before timing out. A value of **0** indicates an infinite amount of time.</span></span> <span data-ttu-id="6213b-120">此属性的默认值为 **60**。</span><span class="sxs-lookup"><span data-stu-id="6213b-120">The default value of this property is **60**.</span></span>  
  
 <span data-ttu-id="6213b-121">**使用被动模式**</span><span class="sxs-lookup"><span data-stu-id="6213b-121">**Use passive mode**</span></span>  
 <span data-ttu-id="6213b-122">指定是由服务器还是由客户端启动连接。</span><span class="sxs-lookup"><span data-stu-id="6213b-122">Specify whether the server or the client initiates the connection.</span></span> <span data-ttu-id="6213b-123">服务器使用主动模式启动连接，客户端使用被动模式启动连接。</span><span class="sxs-lookup"><span data-stu-id="6213b-123">The server initiates the connection in active mode, and the client activates the connection in passive mode.</span></span> <span data-ttu-id="6213b-124">此属性的默认值为“主动模式”。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6213b-124">The default value of this property is **active mode**.</span></span>  
  
 <span data-ttu-id="6213b-125">**重试**</span><span class="sxs-lookup"><span data-stu-id="6213b-125">**Retries**</span></span>  
 <span data-ttu-id="6213b-126">指定任务尝试连接的次数。</span><span class="sxs-lookup"><span data-stu-id="6213b-126">Specify the number of times the task attempts to make a connection.</span></span> <span data-ttu-id="6213b-127">如果值为 **0** ，则表示不限制尝试次数。</span><span class="sxs-lookup"><span data-stu-id="6213b-127">A value of **0** indicates no limit to the number of attempts.</span></span>  
  
 <span data-ttu-id="6213b-128">**块区大小(KB)**</span><span class="sxs-lookup"><span data-stu-id="6213b-128">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="6213b-129">提供传输数据的块区大小 (KB)。</span><span class="sxs-lookup"><span data-stu-id="6213b-129">Provide a chunk size in kilobytes for transmitting data.</span></span>  
  
 <span data-ttu-id="6213b-130">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="6213b-130">**Test Connection**</span></span>  
 <span data-ttu-id="6213b-131">在配置 FTP 连接管理器后，请通过单击“测试连接”\*\*\*\* 确认该连接是否正常。</span><span class="sxs-lookup"><span data-stu-id="6213b-131">After configuring the FTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6213b-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6213b-132">See Also</span></span>  
 [<span data-ttu-id="6213b-133">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="6213b-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
