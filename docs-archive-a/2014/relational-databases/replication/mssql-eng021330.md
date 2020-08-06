---
title: MSSQL_ENG021330 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4338756a641b23bfc6f52da6b3de296bb6415756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688825"
---
# <a name="mssql_eng021330"></a><span data-ttu-id="8f33e-102">MSSQL_ENG021330</span><span class="sxs-lookup"><span data-stu-id="8f33e-102">MSSQL_ENG021330</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8f33e-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="8f33e-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f33e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8f33e-104">Product Name</span></span>|<span data-ttu-id="8f33e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8f33e-105">SQL Server</span></span>|  
|<span data-ttu-id="8f33e-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8f33e-106">Event ID</span></span>|<span data-ttu-id="8f33e-107">21330</span><span class="sxs-lookup"><span data-stu-id="8f33e-107">21330</span></span>|  
|<span data-ttu-id="8f33e-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8f33e-108">Event Source</span></span>|<span data-ttu-id="8f33e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8f33e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8f33e-110">组件</span><span class="sxs-lookup"><span data-stu-id="8f33e-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8f33e-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="8f33e-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8f33e-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="8f33e-112">Message Text</span></span>|<span data-ttu-id="8f33e-113">无法在复制工作目录下创建子目录。(%ls)</span><span class="sxs-lookup"><span data-stu-id="8f33e-113">Failed to create a sub-directory under the replication working directory.(%ls)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8f33e-114">说明</span><span class="sxs-lookup"><span data-stu-id="8f33e-114">Explanation</span></span>  
 <span data-ttu-id="8f33e-115">当手动初始化订阅而且创建存储复制脚本的目录有问题时，会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="8f33e-115">This error can occur when a subscription is initialized manually, and there is a problem creating the directory in which replication scripts are stored.</span></span> <span data-ttu-id="8f33e-116">权限问题可导致此错误：在不使用快照的情况下初始化订阅时，在发布服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户对分发服务器上的快照文件夹必须具有写权限。</span><span class="sxs-lookup"><span data-stu-id="8f33e-116">The error can be caused by a permissions issue: when a subscription is initialized without using a snapshot, the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher must have write permissions on the snapshot folder at the Distributor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8f33e-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="8f33e-117">User Action</span></span>  
 <span data-ttu-id="8f33e-118">请确保已为快照文件夹指定正确的路径，并且在发布服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的帐户具有足够的权限。</span><span class="sxs-lookup"><span data-stu-id="8f33e-118">Ensure that the correct path has been specified for the snapshot folder and that the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher has sufficient permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f33e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f33e-119">See Also</span></span>  
 <span data-ttu-id="8f33e-120">[指定默认快照位置](snapshot-options.md#snapshot-folder-locations) </span><span class="sxs-lookup"><span data-stu-id="8f33e-120">[Specify the Default Snapshot Location](snapshot-options.md#snapshot-folder-locations) </span></span>  
 <span data-ttu-id="8f33e-121">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8f33e-121">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="8f33e-122">初始化事务订阅（不使用快照）</span><span class="sxs-lookup"><span data-stu-id="8f33e-122">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
