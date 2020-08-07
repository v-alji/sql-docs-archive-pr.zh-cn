---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 720263939e2f1685649fc41896e8ea10907d92ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589661"
---
# <a name="mssqlserver_1401"></a><span data-ttu-id="f791e-102">MSSQLSERVER_1401</span><span class="sxs-lookup"><span data-stu-id="f791e-102">MSSQLSERVER_1401</span></span>
    
## <a name="details"></a><span data-ttu-id="f791e-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f791e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f791e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f791e-104">Product Name</span></span>|<span data-ttu-id="f791e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f791e-105">SQL Server</span></span>|  
|<span data-ttu-id="f791e-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f791e-106">Event ID</span></span>|<span data-ttu-id="f791e-107">1401</span><span class="sxs-lookup"><span data-stu-id="f791e-107">1401</span></span>|  
|<span data-ttu-id="f791e-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f791e-108">Event Source</span></span>|<span data-ttu-id="f791e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f791e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f791e-110">组件</span><span class="sxs-lookup"><span data-stu-id="f791e-110">Component</span></span>|<span data-ttu-id="f791e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f791e-111">SQLEngine</span></span>|  
|<span data-ttu-id="f791e-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f791e-112">Symbolic Name</span></span>|<span data-ttu-id="f791e-113">DBM_MASTERSTARTUP</span><span class="sxs-lookup"><span data-stu-id="f791e-113">DBM_MASTERSTARTUP</span></span>|  
|<span data-ttu-id="f791e-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f791e-114">Message Text</span></span>|<span data-ttu-id="f791e-115">数据库镜像主线程例程的启动因以下原因失败: %ls。</span><span class="sxs-lookup"><span data-stu-id="f791e-115">Startup of the database-mirroring master thread routine failed for the following reason: %ls.</span></span> <span data-ttu-id="f791e-116">请纠正此错误的原因，然后重新启动 SQL Server 服务。</span><span class="sxs-lookup"><span data-stu-id="f791e-116">Correct the cause of this error, and restart the SQL Server service.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f791e-117">说明</span><span class="sxs-lookup"><span data-stu-id="f791e-117">Explanation</span></span>  
 <span data-ttu-id="f791e-118">镜像控制线程启动失败。</span><span class="sxs-lookup"><span data-stu-id="f791e-118">Startup of the mirroring control thread failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f791e-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="f791e-119">User Action</span></span>  
 <span data-ttu-id="f791e-120">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中，查看此消息之前的相关错误。</span><span class="sxs-lookup"><span data-stu-id="f791e-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, look for the associated error that preceded this message.</span></span> <span data-ttu-id="f791e-121">请纠正此错误的原因，然后重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务 (MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="f791e-121">Correct the cause of this error, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service (MSSQLSERVER).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f791e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f791e-122">See Also</span></span>  
 [<span data-ttu-id="f791e-123">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="f791e-123">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
