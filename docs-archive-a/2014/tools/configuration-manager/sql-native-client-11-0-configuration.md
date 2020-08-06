---
title: SQL Native Client 11.0 配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- client configuration [SQL Server], SQL Server Native Client
ms.assetid: e73143e9-5e7b-4d0a-8827-ab900efdcb35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 183dd2d161b1bf0b13140a607167b81dab086fdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578609"
---
# <a name="sql-native-client-110-configuration"></a><span data-ttu-id="479fa-102">SQL Native Client 11.0 配置</span><span class="sxs-lookup"><span data-stu-id="479fa-102">SQL Native Client 11.0 Configuration</span></span>
  <span data-ttu-id="479fa-103">本节包含了按 F1 后看到的有关   配置管理器中的“SQL Server Native Client 配置”对话框的帮助主题[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="479fa-103">This section contains the F1 Help topics for the **SQL Server Native Client Configuration** dialogs in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="479fa-104">Native Client 是客户端计算机用于连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的网络库，与 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起启动。</span><span class="sxs-lookup"><span data-stu-id="479fa-104">Native Client is the network library that client computers use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], starting with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="479fa-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 配置中配置的设置将在运行客户端程序的计算机上使用。</span><span class="sxs-lookup"><span data-stu-id="479fa-105">The settings configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Configuration, are used on the computer running the client program.</span></span> <span data-ttu-id="479fa-106">在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的计算机上配置这些设置时，它们仅影响那些运行在服务器上的客户端程序。</span><span class="sxs-lookup"><span data-stu-id="479fa-106">When configured on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they affect only those client programs running on the server.</span></span>  
  
 <span data-ttu-id="479fa-107">这些设置不会影响连接到早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的客户端，除非它们使用与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一起启动的客户端工具，例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="479fa-107">These settings do not affect clients connecting to previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], unless they are using the client tools starting with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="479fa-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="479fa-108">In this Section</span></span>  
  
-   [<span data-ttu-id="479fa-109">SQL Server Native Client 配置属性（“标志”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-109">SQL Server Native Client Configuration Properties &#40;Flags Tab&#41;</span></span>](../../../2014/tools/configuration-manager/sql-server-native-client-configuration-properties-flags-tab.md)  
  
-   [<span data-ttu-id="479fa-110">客户端协议（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="479fa-110">Client Protocols &#40;SQL Server Configuration Manager&#41;</span></span>](../../relational-databases/sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="479fa-111">客户端协议属性（“顺序”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-111">Client Protocols Properties &#40;Order Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-properties-order-tab.md)  
  
    -   [<span data-ttu-id="479fa-112">客户端协议 - Shared Memory 属性（“协议”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-112">Client Protocols - Shared Memory Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-shared-memory-properties-protocol-tab.md)  
  
    -   [<span data-ttu-id="479fa-113">客户端协议-TCP 和 IP 属性 &#40;协议选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="479fa-113">Client Protocols - TCP and IP Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-tcp-and-ip-properties-protocol-tab.md)  
  
    -   [<span data-ttu-id="479fa-114">客户端协议 - Named Pipes 属性（“协议”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-114">Client Protocols - Named Pipes Properties &#40;Protocol Tab&#41;</span></span>](../../../2014/tools/configuration-manager/client-protocols-named-pipes-properties-protocol-tab.md)  
  
-   [<span data-ttu-id="479fa-115">别名（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="479fa-115">Aliases &#40;SQL Server Configuration Manager&#41;</span></span>](../../../2014/tools/configuration-manager/aliases-sql-server-configuration-manager.md)  
  
    -   [<span data-ttu-id="479fa-116">新建别名（“别名”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-116">New Alias &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)  
  
    -   [<span data-ttu-id="479fa-117"><别名>属性（“别名”选项卡）</span><span class="sxs-lookup"><span data-stu-id="479fa-117">&#60;Alias&#62; Properties &#40;Alias Tab&#41;</span></span>](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
    -   [<span data-ttu-id="479fa-118">使用 Shared Memory 协议创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="479fa-118">Creating a Valid Connection String Using Shared Memory Protocol</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
    -   [<span data-ttu-id="479fa-119">使用 TCP IP 创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="479fa-119">Creating a Valid Connection String Using TCP IP</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
    -   [<span data-ttu-id="479fa-120">使用命名管道创建有效的连接字符串</span><span class="sxs-lookup"><span data-stu-id="479fa-120">Creating a Valid Connection String Using Named Pipes</span></span>](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
