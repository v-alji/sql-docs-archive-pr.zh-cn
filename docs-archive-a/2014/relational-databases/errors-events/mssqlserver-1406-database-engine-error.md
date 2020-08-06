---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adaa0084b875f720c477189e0e8e085af124f4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690631"
---
# <a name="mssqlserver_1406"></a><span data-ttu-id="06a87-102">MSSQLSERVER_1406</span><span class="sxs-lookup"><span data-stu-id="06a87-102">MSSQLSERVER_1406</span></span>
    
## <a name="details"></a><span data-ttu-id="06a87-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="06a87-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06a87-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="06a87-104">Product Name</span></span>|<span data-ttu-id="06a87-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06a87-105">SQL Server</span></span>|  
|<span data-ttu-id="06a87-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="06a87-106">Event ID</span></span>|<span data-ttu-id="06a87-107">1406</span><span class="sxs-lookup"><span data-stu-id="06a87-107">1406</span></span>|  
|<span data-ttu-id="06a87-108">事件源</span><span class="sxs-lookup"><span data-stu-id="06a87-108">Event Source</span></span>|<span data-ttu-id="06a87-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06a87-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06a87-110">组件</span><span class="sxs-lookup"><span data-stu-id="06a87-110">Component</span></span>|<span data-ttu-id="06a87-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06a87-111">SQLEngine</span></span>|  
|<span data-ttu-id="06a87-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="06a87-112">Symbolic Name</span></span>|<span data-ttu-id="06a87-113">DBM_BADSTATEFORFORCESERVICE</span><span class="sxs-lookup"><span data-stu-id="06a87-113">DBM_BADSTATEFORFORCESERVICE</span></span>|  
|<span data-ttu-id="06a87-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="06a87-114">Message Text</span></span>|<span data-ttu-id="06a87-115">无法安全地强制执行服务。</span><span class="sxs-lookup"><span data-stu-id="06a87-115">Unable to force service safely.</span></span> <span data-ttu-id="06a87-116">请删除数据库镜像并恢复数据库 "%.\*ls" 以获得访问权。</span><span class="sxs-lookup"><span data-stu-id="06a87-116">Remove database mirroring and recover database "%.\*ls" to gain access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06a87-117">说明</span><span class="sxs-lookup"><span data-stu-id="06a87-117">Explanation</span></span>  
 <span data-ttu-id="06a87-118">由于镜像状态不能保证强制服务过程正确进行，所以 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 不能强制服务。</span><span class="sxs-lookup"><span data-stu-id="06a87-118">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot force service because the mirroring state cannot guarantee that the force service process would work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06a87-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="06a87-119">User Action</span></span>  
 <span data-ttu-id="06a87-120">删除数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="06a87-120">Remove database mirroring.</span></span> <span data-ttu-id="06a87-121">然后可以恢复该镜像数据库以获得它的访问权。</span><span class="sxs-lookup"><span data-stu-id="06a87-121">You can then recover the mirror database to gain access to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a87-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06a87-122">See Also</span></span>  
 <span data-ttu-id="06a87-123">[在数据库镜像会话中强制服务 (Transact-SQL)](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="06a87-123">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 [<span data-ttu-id="06a87-124">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06a87-124">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
