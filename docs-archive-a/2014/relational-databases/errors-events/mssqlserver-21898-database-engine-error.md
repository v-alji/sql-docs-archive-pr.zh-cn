---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78ce7eacf7f026bf9977af2c367b954a3639b357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689396"
---
# <a name="mssqlserver_21898"></a><span data-ttu-id="dbbac-102">MSSQLSERVER_21898</span><span class="sxs-lookup"><span data-stu-id="dbbac-102">MSSQLSERVER_21898</span></span>
    
## <a name="details"></a><span data-ttu-id="dbbac-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="dbbac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dbbac-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="dbbac-104">Product Name</span></span>|<span data-ttu-id="dbbac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dbbac-105">SQL Server</span></span>|  
|<span data-ttu-id="dbbac-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dbbac-106">Event ID</span></span>|<span data-ttu-id="dbbac-107">21898</span><span class="sxs-lookup"><span data-stu-id="dbbac-107">21898</span></span>|  
|<span data-ttu-id="dbbac-108">事件源</span><span class="sxs-lookup"><span data-stu-id="dbbac-108">Event Source</span></span>|<span data-ttu-id="dbbac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dbbac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dbbac-110">组件</span><span class="sxs-lookup"><span data-stu-id="dbbac-110">Component</span></span>|<span data-ttu-id="dbbac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dbbac-111">SQLEngine</span></span>|  
|<span data-ttu-id="dbbac-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="dbbac-112">Symbolic Name</span></span>|<span data-ttu-id="dbbac-113">SQLErrorNum21898</span><span class="sxs-lookup"><span data-stu-id="dbbac-113">SQLErrorNum21898</span></span>|  
|<span data-ttu-id="dbbac-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="dbbac-114">Message Text</span></span>|<span data-ttu-id="dbbac-115">发布服务器“%s”使用的是分发数据库“%s”，而不是“%s”（后者是承载发布数据库“%s”所需的）。</span><span class="sxs-lookup"><span data-stu-id="dbbac-115">The publisher '%s' uses distribution database '%s' and not '%s' which is required in order to host the publishing database '%s'.</span></span> <span data-ttu-id="dbbac-116">请在分发服务器“%s”上运行 `sp_changedistpublisher`，以将发布服务器使用的分发数据库更改为“%s”。</span><span class="sxs-lookup"><span data-stu-id="dbbac-116">Run `sp_changedistpublisher` at distributor '%s' to change the distribution database used by the publisher to '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dbbac-117">说明</span><span class="sxs-lookup"><span data-stu-id="dbbac-117">Explanation</span></span>  
 <span data-ttu-id="dbbac-118">`sp_validate_redirected_publisher`在本地分发服务器上， 查询 msdb.dbo.MSdistpublishers，以验证新的发布服务器使用的分发数据库与原始发布服务器使用的分发数据库相同。</span><span class="sxs-lookup"><span data-stu-id="dbbac-118">`sp_validate_redirected_publisher` queries msdb.dbo.MSdistpublishers at the local distributor to verify that the distribution database used by the new publisher is the same as the distribution database used by the original publisher.</span></span> <span data-ttu-id="dbbac-119">当这些数据库不同时将返回此错误，同时使发布服务器不适合作为发布服务器数据库的主机。</span><span class="sxs-lookup"><span data-stu-id="dbbac-119">This error is returned when these databases are different, making the publisher an unsuitable host for the publisher database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dbbac-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="dbbac-120">User Action</span></span>  
 <span data-ttu-id="dbbac-121">执行存储过程 `sp_changedistpublisher`，以将新发布服务器的分发数据库更改为由原始发布服务器使用的分发数据库。</span><span class="sxs-lookup"><span data-stu-id="dbbac-121">Execute stored procedure `sp_changedistpublisher` to change the distribution database for the new publisher to that used by the original publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbbac-122">如果在分发服务器上针对发布服务器运行 `sp_changedistpublisher` 时输入了错误的分发数据库，则运行 `sp_adddistpublisher` 将会解决此问题。</span><span class="sxs-lookup"><span data-stu-id="dbbac-122">Running `sp_changedistpublisher` will address the problem if the wrong distribution database was entered when `sp_adddistpublisher` was run at the distributor for the publisher.</span></span> <span data-ttu-id="dbbac-123">但是，如果远程发布服务器具有其他发布数据库中的现有发布，而这些发布使用所标识的分发数据库，则此更改不适当。</span><span class="sxs-lookup"><span data-stu-id="dbbac-123">However, if the remote publisher has existing publications from another publishing database that make use of the identified distribution database, this change is not appropriate.</span></span> <span data-ttu-id="dbbac-124">使用命名分发数据库的复制需要系统化地删除，然后使用原始发布服务器的分发数据库重新建立，这样，新的发布服务器才能成为合适的主机。</span><span class="sxs-lookup"><span data-stu-id="dbbac-124">Replication using the named distribution database needs to be systematically removed and then reestablished using the original publisher's distribution database in order for the new publisher to function as a suitable host.</span></span>  
  
  
