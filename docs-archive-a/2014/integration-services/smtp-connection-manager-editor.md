---
title: SMTP 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14ed49f64b9faca40f575fc6760a8d25c0d4573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694012"
---
# <a name="smtp-connection-manager-editor"></a><span data-ttu-id="789e6-102">SMTP 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="789e6-102">SMTP Connection Manager Editor</span></span>
  <span data-ttu-id="789e6-103">使用“SMTP 连接管理器编辑器”  对话框可以指定简单邮件传输协议 (SMTP) 服务器。</span><span class="sxs-lookup"><span data-stu-id="789e6-103">Use the **SMTP Connection Manager Editor** dialog box to specify a Simple Mail Transfer Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="789e6-104">若要了解有关 SMTP 连接管理器的详细信息，请参阅 [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="789e6-104">To learn more about the SMTP connection manager, see [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="789e6-105">选项</span><span class="sxs-lookup"><span data-stu-id="789e6-105">Options</span></span>  
 <span data-ttu-id="789e6-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="789e6-106">**Name**</span></span>  
 <span data-ttu-id="789e6-107">为连接管理器提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="789e6-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="789e6-108">**说明**</span><span class="sxs-lookup"><span data-stu-id="789e6-108">**Description**</span></span>  
 <span data-ttu-id="789e6-109">描述连接管理器。</span><span class="sxs-lookup"><span data-stu-id="789e6-109">Describe the connection manager.</span></span> <span data-ttu-id="789e6-110">最好按照连接管理器的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="789e6-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="789e6-111">**SMTP 服务器**</span><span class="sxs-lookup"><span data-stu-id="789e6-111">**SMTP server**</span></span>  
 <span data-ttu-id="789e6-112">提供 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="789e6-112">Provide the name of the SMTP server.</span></span>  
  
 <span data-ttu-id="789e6-113">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="789e6-113">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="789e6-114">如果选中此选项，在通过 SMTP 服务器发送邮件时将使用 Windows 身份验证来验证对服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="789e6-114">Select to send mail using an SMTP server that uses Windows Authentication to authenticate access to the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="789e6-115">SMTP 连接管理器仅支持匿名身份验证和 Windows 身份验证，</span><span class="sxs-lookup"><span data-stu-id="789e6-115">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="789e6-116">而不支持基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="789e6-116">It does not support basic authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="789e6-117">使用 Microsoft Exchange 作为 SMTP 服务器时，可能需要将 "**使用 Windows 身份验证**" 设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="789e6-117">When using Microsoft Exchange as the SMTP server, you may need to set **Use Windows Authentication** to `True`.</span></span> <span data-ttu-id="789e6-118">Exchange 服务器可以配置为不支持未经身份验证的 SMTP 连接。</span><span class="sxs-lookup"><span data-stu-id="789e6-118">Exchange servers may be configured to disallow unauthenticated SMTP connections.</span></span>  
  
 <span data-ttu-id="789e6-119">**启用安全套接字层 (SSL)**</span><span class="sxs-lookup"><span data-stu-id="789e6-119">**Enable Secure Sockets Layer (SSL)**</span></span>  
 <span data-ttu-id="789e6-120">如果选中此选项，则在发送电子邮件时，将使用安全套接字层 (SSL) 来加密通信。</span><span class="sxs-lookup"><span data-stu-id="789e6-120">Select to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789e6-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="789e6-121">See Also</span></span>  
 [<span data-ttu-id="789e6-122">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="789e6-122">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
