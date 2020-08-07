---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92479d7727ac2300d6a60d02492667d99a69b022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589135"
---
# <a name="mssqlserver_21893"></a><span data-ttu-id="983c3-102">MSSQLSERVER_21893</span><span class="sxs-lookup"><span data-stu-id="983c3-102">MSSQLSERVER_21893</span></span>
    
## <a name="details"></a><span data-ttu-id="983c3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="983c3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="983c3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="983c3-104">Product Name</span></span>|<span data-ttu-id="983c3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="983c3-105">SQL Server</span></span>|  
|<span data-ttu-id="983c3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="983c3-106">Event ID</span></span>|<span data-ttu-id="983c3-107">21893</span><span class="sxs-lookup"><span data-stu-id="983c3-107">21893</span></span>|  
|<span data-ttu-id="983c3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="983c3-108">Event Source</span></span>|<span data-ttu-id="983c3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="983c3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="983c3-110">组件</span><span class="sxs-lookup"><span data-stu-id="983c3-110">Component</span></span>|<span data-ttu-id="983c3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="983c3-111">SQLEngine</span></span>|  
|<span data-ttu-id="983c3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="983c3-112">Symbolic Name</span></span>|<span data-ttu-id="983c3-113">SQLErrorNum21893</span><span class="sxs-lookup"><span data-stu-id="983c3-113">SQLErrorNum21893</span></span>|  
|<span data-ttu-id="983c3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="983c3-114">Message Text</span></span>|<span data-ttu-id="983c3-115">订阅服务器 (%s)（属于原始发布服务器“%s”）在重定向的发布服务器“%s”中不显示为远程服务器。</span><span class="sxs-lookup"><span data-stu-id="983c3-115">The subscribers ( %s ) of original publisher '%s' do not appear as remote servers at redirected publisher '%s'.</span></span> <span data-ttu-id="983c3-116">`sp_addlinkedserver`在重定向的发布服务器上运行，以将这些订阅服务器添加为远程服务器。</span><span class="sxs-lookup"><span data-stu-id="983c3-116">Run `sp_addlinkedserver` at the redirected publisher to add these subscribers as remote servers .</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="983c3-117">说明</span><span class="sxs-lookup"><span data-stu-id="983c3-117">Explanation</span></span>  
 <span data-ttu-id="983c3-118">`sp_validate_redirected_publisher`在远程服务器上， 使用发布服务器数据库的订阅元数据表来确定其关联的订阅服务器，并验证在订阅服务器的 master.dbo.sysservers 中具有关联的条目。</span><span class="sxs-lookup"><span data-stu-id="983c3-118">`sp_validate_redirected_publisher` uses the subscription metadata tables of the publisher database at the remote server to identify its associated subscribers and verifies that there are associated entries in master.dbo.sysservers for the subscribers.</span></span> <span data-ttu-id="983c3-119">如果任何标识的订阅服务器不存在，则会返回此错误。</span><span class="sxs-lookup"><span data-stu-id="983c3-119">This error is returned if any of the identified subscribers are not present.</span></span>  
  
 <span data-ttu-id="983c3-120">该错误不被视为严重错误。</span><span class="sxs-lookup"><span data-stu-id="983c3-120">This error is not considered a fatal error.</span></span> <span data-ttu-id="983c3-121">遇到该错误的代理将此错误记录为信息性消息，但不会终止，因为在新发布服务器上无法具有适当的订阅服务器条目对复制的影响很有限。</span><span class="sxs-lookup"><span data-stu-id="983c3-121">Agents encountering this error will log the error as informational but will not terminate, since a failure to have appropriate subscriber entries at the new publisher has limited impact on replication.</span></span> <span data-ttu-id="983c3-122">如果在 sysservers 中没有相应的订阅服务器条目，则在通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 执行时，某些订阅管理活动可能会失败。</span><span class="sxs-lookup"><span data-stu-id="983c3-122">Without an appropriate entry for a subscriber in sysservers, some subscription management activities may fail when executed through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="983c3-123">但是，可以通过显式执行管理存储过程成功地执行这些相同的活动。</span><span class="sxs-lookup"><span data-stu-id="983c3-123">However, these same activities can be successfully performed by executing the management stored procedures explicitly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="983c3-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="983c3-124">User Action</span></span>  
 <span data-ttu-id="983c3-125">在重定向的发布服务器上为每个标识的订阅服务器运行 `sp_addlinkedserver`，以将这些订阅服务器添加为远程服务器。</span><span class="sxs-lookup"><span data-stu-id="983c3-125">Run `sp_addlinkedserver` at the redirected publisher for each of the identified subscribers to add them as remote servers.</span></span> <span data-ttu-id="983c3-126">然后，运行 `sp_serveroption` 以设置该服务器的订阅服务器位。</span><span class="sxs-lookup"><span data-stu-id="983c3-126">Then, run `sp_serveroption` to set the subscriber bit for the server.</span></span>  
  
  
