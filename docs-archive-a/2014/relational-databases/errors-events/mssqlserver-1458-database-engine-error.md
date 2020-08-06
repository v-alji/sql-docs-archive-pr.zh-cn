---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efa45177a92402b25099be5bb3e3dcc91a5fa6d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589650"
---
# <a name="mssqlserver_1458"></a><span data-ttu-id="7344f-102">MSSQLSERVER_1458</span><span class="sxs-lookup"><span data-stu-id="7344f-102">MSSQLSERVER_1458</span></span>
    
## <a name="details"></a><span data-ttu-id="7344f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="7344f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7344f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="7344f-104">Product Name</span></span>|<span data-ttu-id="7344f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7344f-105">SQL Server</span></span>|  
|<span data-ttu-id="7344f-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7344f-106">Event ID</span></span>|<span data-ttu-id="7344f-107">1458</span><span class="sxs-lookup"><span data-stu-id="7344f-107">1458</span></span>|  
|<span data-ttu-id="7344f-108">事件源</span><span class="sxs-lookup"><span data-stu-id="7344f-108">Event Source</span></span>|<span data-ttu-id="7344f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7344f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7344f-110">组件</span><span class="sxs-lookup"><span data-stu-id="7344f-110">Component</span></span>|<span data-ttu-id="7344f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7344f-111">SQLEngine</span></span>|  
|<span data-ttu-id="7344f-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="7344f-112">Symbolic Name</span></span>|<span data-ttu-id="7344f-113">DBM_FAILREDO_ON_PRIMARY</span><span class="sxs-lookup"><span data-stu-id="7344f-113">DBM_FAILREDO_ON_PRIMARY</span></span>|  
|<span data-ttu-id="7344f-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="7344f-114">Message Text</span></span>|<span data-ttu-id="7344f-115">'%.\*ls' 数据库的主体副本遇到错误 %d，状态 %d，严重性 %d。</span><span class="sxs-lookup"><span data-stu-id="7344f-115">The principal copy of the '%.\*ls' database encountered error %d, status %d, severity %d.</span></span> <span data-ttu-id="7344f-116">数据库镜像已挂起。</span><span class="sxs-lookup"><span data-stu-id="7344f-116">Database mirroring has been suspended.</span></span> <span data-ttu-id="7344f-117">请尝试纠正错误条件，然后继续镜像。</span><span class="sxs-lookup"><span data-stu-id="7344f-117">Try to resolve the error condition, and resume mirroring.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7344f-118">说明</span><span class="sxs-lookup"><span data-stu-id="7344f-118">Explanation</span></span>  
 <span data-ttu-id="7344f-119">该消息指出主体数据库遇到了导致数据库镜像被挂起的错误。</span><span class="sxs-lookup"><span data-stu-id="7344f-119">This messages indicates that the principal database encountered an error that caused database mirroring to be suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7344f-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="7344f-120">User Action</span></span>  
 <span data-ttu-id="7344f-121">导致此错误的大多数原因可以自我更正。</span><span class="sxs-lookup"><span data-stu-id="7344f-121">Most cases of this error are self correcting.</span></span> <span data-ttu-id="7344f-122">如果该问题仍然存在，重新启动数据库或服务器实例通常可以更正该问题。</span><span class="sxs-lookup"><span data-stu-id="7344f-122">If the problem persists, restarting the database or server instance typically corrects the problem.</span></span> <span data-ttu-id="7344f-123">有关详细信息，请查看每个伙伴中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以获得出现在此消息之前的关联错误。</span><span class="sxs-lookup"><span data-stu-id="7344f-123">For more information, look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on each partner for the associated error that preceded this message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7344f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7344f-124">See Also</span></span>  
 [<span data-ttu-id="7344f-125">监视数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7344f-125">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
