---
title: 在网络上或不在网络上运行 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a80e7e4d42f322bc42d0c67c57e3a1f9bddb87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586966"
---
# <a name="run-sql-server-with-or-without-a-network"></a><span data-ttu-id="49ce7-102">在网络上或不在网络上运行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="49ce7-102">Run SQL Server With or Without a Network</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="49ce7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以在网络上运行，也可以不在网络上运行。</span><span class="sxs-lookup"><span data-stu-id="49ce7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can run on a network, or it can function without a network.</span></span>  
  
## <a name="running-sql-server-on-a-network"></a><span data-ttu-id="49ce7-104">在网络上运行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="49ce7-104">Running SQL Server on a Network</span></span>  
 <span data-ttu-id="49ce7-105">若要使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能够通过网络进行通信， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务必须正在运行。</span><span class="sxs-lookup"><span data-stu-id="49ce7-105">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to communicate over a network, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service must be running.</span></span> <span data-ttu-id="49ce7-106">默认情况下， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 将自动启动内置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="49ce7-106">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows automatically starts the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="49ce7-107">若要了解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务是否已启动，请在命令提示符下键入：</span><span class="sxs-lookup"><span data-stu-id="49ce7-107">To find out whether the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has been started, at the command prompt, type the following:</span></span>  
  
 <span data-ttu-id="49ce7-108">**net start**</span><span class="sxs-lookup"><span data-stu-id="49ce7-108">**net start**</span></span>  
  
 <span data-ttu-id="49ce7-109">如果与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 关联的服务已经启动，那么 **net start** 输出中会显示下列服务：</span><span class="sxs-lookup"><span data-stu-id="49ce7-109">If the services associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have been started, the following services will appear in the **net start** output:</span></span>  
  
-   <span data-ttu-id="49ce7-110">Analysis Services (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="49ce7-110">Analysis Services (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="49ce7-111">SQL Server (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="49ce7-111">SQL Server (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="49ce7-112">SQL Server 代理 (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="49ce7-112">SQL Server Agent (MSSQLSERVER)</span></span>  
  
## <a name="running-sql-server-without-a-network"></a><span data-ttu-id="49ce7-113">不在网络上运行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="49ce7-113">Running SQL Server Without a Network</span></span>  
 <span data-ttu-id="49ce7-114">当不在网络上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，无需启动内置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="49ce7-114">When running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without a network, you do not need to start the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="49ce7-115">即使没有网络， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、SQL Server 配置管理器、 **net start** 和 **net stop** 命令仍然有效。因此，无论是网络操作还是独立操作，启动和停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的过程是完全相同的。</span><span class="sxs-lookup"><span data-stu-id="49ce7-115">Because [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQL Server Configuration Manager, and the **net start** and **net stop** commands are functional even without a network, the procedures for starting and stopping an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are identical for a network or stand-alone operation.</span></span>  
  
 <span data-ttu-id="49ce7-116">当从本地客户端（如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd **）连接到独立的**实例时，将不使用网络而使用本地管道直接连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="49ce7-116">When connecting to an instance of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a local client such as **sqlcmd**, you bypass the network and connect directly to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a local pipe.</span></span> <span data-ttu-id="49ce7-117">本地管道和网络管道的区别在于是否使用网络。</span><span class="sxs-lookup"><span data-stu-id="49ce7-117">The difference between a local pipe and a network pipe is whether you are using a network.</span></span> <span data-ttu-id="49ce7-118">除非特别指明，否则本地管道和网络管道都使用标准管道 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .\pipe\sql\query) 与\\\\实例建立连接。</span><span class="sxs-lookup"><span data-stu-id="49ce7-118">Both local and network pipes establish a connection with an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the standard pipe (\\\\.\pipe\sql\query), unless otherwise directed.</span></span>  
  
 <span data-ttu-id="49ce7-119">如果在连接到本地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时不指定服务器名称，则使用的就是本地管道。</span><span class="sxs-lookup"><span data-stu-id="49ce7-119">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without specifying a server name, you are using a local pipe.</span></span> <span data-ttu-id="49ce7-120">如果连接到本地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并显式指定了服务器名称，则所使用的就是网络管道或另一种网络进程间通信 (IPC) 机制，例如，网间数据包交换/有序数据包交换 (IPX/SPX)（假定已将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置成使用多种网络）。</span><span class="sxs-lookup"><span data-stu-id="49ce7-120">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and specify a server name explicitly, you are using either a network pipe or another network interprocess communication (IPC) mechanism, such as Internetwork Packet Exchange/Sequenced Packet Exchange (IPX/SPX) (assuming you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use multiple networks).</span></span> <span data-ttu-id="49ce7-121">由于独立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支持网络管道，因此必须在从客户端连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，省略不必要的 **/** <Server_name> 自变量。</span><span class="sxs-lookup"><span data-stu-id="49ce7-121">Because a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support network pipes, you must omit the unnecessary **/**_<Server_name>_ argument when connecting to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client.</span></span> <span data-ttu-id="49ce7-122">例如，若要从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] osql **连接到独立的**实例，请键入：</span><span class="sxs-lookup"><span data-stu-id="49ce7-122">For example, to connect to a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from **osql**, type:</span></span>  
  
 <span data-ttu-id="49ce7-123">osql /Usa /P \<saPassword></span><span class="sxs-lookup"><span data-stu-id="49ce7-123">**osql /Usa /P** _\<saPassword>_</span></span>  
  
  
