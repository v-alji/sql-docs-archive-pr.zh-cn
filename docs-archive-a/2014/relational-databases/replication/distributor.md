---
title: 分发服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c601a540088b5cd9d7a2033510a5cf9b83c3170e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578104"
---
# <a name="distributor"></a><span data-ttu-id="b770b-102">分发服务器</span><span class="sxs-lookup"><span data-stu-id="b770b-102">Distributor</span></span>
  <span data-ttu-id="b770b-103">**“分发服务器”** 页出现在配置分发向导和新建发布向导中。</span><span class="sxs-lookup"><span data-stu-id="b770b-103">The **Distributor** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="b770b-104">分发服务器是包含分发数据库并为所有类型的复制存储元数据和历史记录数据的服务器。</span><span class="sxs-lookup"><span data-stu-id="b770b-104">The Distributor is a server that contains the distribution database and stores metadata and history data for all types of replication.</span></span> <span data-ttu-id="b770b-105">分发服务器还为事务复制存储事务。</span><span class="sxs-lookup"><span data-stu-id="b770b-105">The Distributor also stores transactions for transactional replication.</span></span> <span data-ttu-id="b770b-106">分发服务器与发布服务器可以是同一服务器（本地分发服务器），也可以是不同的服务器（远程分发服务器）。</span><span class="sxs-lookup"><span data-stu-id="b770b-106">The Distributor can be the same server as the Publisher (a local Distributor) or it can be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="b770b-107">分发服务器的角色根据所实现的复制类型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="b770b-107">The role of the Distributor varies, depending on which type of replication you implement.</span></span> <span data-ttu-id="b770b-108">通常，对于事务复制，分发服务器角色要远比合并复制和快照复制重要。</span><span class="sxs-lookup"><span data-stu-id="b770b-108">In general, its role is much greater for transactional replication than it is for merge replication and snapshot replication.</span></span> <span data-ttu-id="b770b-109">合并和快照复制通常使用本地分发服务器，而对于繁忙的系统来说，为事务复制使用远程分发服务器可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="b770b-109">Merge and snapshot replication typically use a local Distributor, but transactional replication on a very busy system can benefit from using a remote Distributor.</span></span>  
  
 <span data-ttu-id="b770b-110">分发服务器在其所在服务器上使用以下附加资源：</span><span class="sxs-lookup"><span data-stu-id="b770b-110">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="b770b-111">如果在分发服务器上存储发布的快照文件（通常如此），则需要附加磁盘空间来存储快照文件。</span><span class="sxs-lookup"><span data-stu-id="b770b-111">Additional disk space if the snapshot files for the publication are stored on it (which they typically are).</span></span>  
  
-   <span data-ttu-id="b770b-112">存储分发数据库所需的附加磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="b770b-112">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="b770b-113">运行于分发服务器上的复制代理执行推送订阅所需的附加处理器资源。</span><span class="sxs-lookup"><span data-stu-id="b770b-113">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="b770b-114">选作分发服务器的服务器应有足够的磁盘空间和处理器运算能力，以支持该服务器上的复制和任何其他活动。</span><span class="sxs-lookup"><span data-stu-id="b770b-114">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b770b-115">选项</span><span class="sxs-lookup"><span data-stu-id="b770b-115">Options</span></span>  
 <span data-ttu-id="b770b-116">**“\<ServerName>”将充当自己的分发服务器；SQL Server 将创建分发数据库和日志**</span><span class="sxs-lookup"><span data-stu-id="b770b-116">**'\<ServerName>' will act as its own Distributor; SQL Server will create a distribution database and log**</span></span>  
 <span data-ttu-id="b770b-117">选择此选项可将所连接的服务器配置为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b770b-117">Select this option to configure the server you are connected to as a Distributor.</span></span>  
  
 <span data-ttu-id="b770b-118">**使用以下服务器作为分发服务器(注意: 您选择的服务器必须已配置为分发服务器)**</span><span class="sxs-lookup"><span data-stu-id="b770b-118">**Use the following server as the Distributor (Note: the server you select must already be configured as a Distributor)**</span></span>  
 <span data-ttu-id="b770b-119">选择此选项，再单击下面的服务器名称，可将另外一个服务配置为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b770b-119">Select this option and then click on the name of a server below to configure another server as the Distributor.</span></span>  
  
 <span data-ttu-id="b770b-120">**添加**</span><span class="sxs-lookup"><span data-stu-id="b770b-120">**Add**</span></span>  
 <span data-ttu-id="b770b-121">如果未列出要用作分发服务器的服务器，请单击 **“添加”** 以标识服务器，并将其添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="b770b-121">If the server you want to use as a Distributor is not listed, click **Add** to identify the server and add it to the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b770b-122">若要使用远程服务器作为分发服务器，则远程服务器必须已配置为分发服务器。</span><span class="sxs-lookup"><span data-stu-id="b770b-122">To use a remote server as the Distributor, the remote server must already be configured as a Distributor.</span></span> <span data-ttu-id="b770b-123">对其运行此向导的服务器必须在该分发服务器上启用为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="b770b-123">The server against which this wizard is running must be enabled as a Publisher on that Distributor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b770b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b770b-124">See Also</span></span>  
 <span data-ttu-id="b770b-125">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="b770b-125">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="b770b-126">配置发布和分发</span><span class="sxs-lookup"><span data-stu-id="b770b-126">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
