---
title: SMTP 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3c090ab672790901baae01ae86f8d22e008b4ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693432"
---
# <a name="smtp-connection-manager"></a><span data-ttu-id="639fa-102">SMTP 连接管理器</span><span class="sxs-lookup"><span data-stu-id="639fa-102">SMTP Connection Manager</span></span>
  <span data-ttu-id="639fa-103">SMTP 连接管理器使包可以连接到简单邮件传输协议 (SMTP) 服务器。</span><span class="sxs-lookup"><span data-stu-id="639fa-103">An SMTP connection manager enables a package to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="639fa-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的发送邮件任务使用 SMTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="639fa-104">The Send Mail task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an SMTP connection manager.</span></span>  
  
 <span data-ttu-id="639fa-105">如果将 Microsoft Exchange 用作 SMTP 服务器，则可能需要配置 SMTP 连接管理器才能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="639fa-105">When using Microsoft Exchange as the SMTP server, you may need to configure the SMTP connection manager to use Windows Authentication.</span></span> <span data-ttu-id="639fa-106">Exchange 服务器可以配置为不支持未经身份验证的 SMTP 连接。</span><span class="sxs-lookup"><span data-stu-id="639fa-106">Exchange servers may be configured to not allow unauthenticated SMTP connections.</span></span>  
  
## <a name="configuration-the-smtp-connection-manager"></a><span data-ttu-id="639fa-107">SMTP 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="639fa-107">Configuration the SMTP Connection Manager</span></span>  
 <span data-ttu-id="639fa-108">将 SMTP 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定 SMTP 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="639fa-108">When you add an SMTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="639fa-109">该连接管理器的 `ConnectionManagerType` 属性设置为 `SMTP`。</span><span class="sxs-lookup"><span data-stu-id="639fa-109">The `ConnectionManagerType` property of the connection manager is set to `SMTP`.</span></span>  
  
 <span data-ttu-id="639fa-110">可以使用下列方式配置 SMTP 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="639fa-110">You can configure an SMTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="639fa-111">提供一个连接字符串。</span><span class="sxs-lookup"><span data-stu-id="639fa-111">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="639fa-112">指定 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="639fa-112">Specify the name of an SMTP server.</span></span>  
  
-   <span data-ttu-id="639fa-113">指定要使用的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="639fa-113">Specify the authentication method to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="639fa-114">SMTP 连接管理器仅支持匿名身份验证和 Windows 身份验证，</span><span class="sxs-lookup"><span data-stu-id="639fa-114">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="639fa-115">而不支持基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="639fa-115">It does not support basic authentication.</span></span>  
  
-   <span data-ttu-id="639fa-116">指定在发送电子邮件时是否使用安全套接字层 (SSL) 对通信进行加密。</span><span class="sxs-lookup"><span data-stu-id="639fa-116">Specify whether to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
 <span data-ttu-id="639fa-117">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="639fa-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="639fa-118">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [SMTP 连接管理器编辑器](../smtp-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="639fa-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMTP Connection Manager Editor](../smtp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="639fa-119">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="639fa-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
