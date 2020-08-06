---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ea44fc9591602bfc8279924e10a1803d0d5a87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577738"
---
# <a name="mssqlserver_10003"></a><span data-ttu-id="bac55-102">MSSQLSERVER_10003</span><span class="sxs-lookup"><span data-stu-id="bac55-102">MSSQLSERVER_10003</span></span>
    
## <a name="details"></a><span data-ttu-id="bac55-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="bac55-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bac55-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="bac55-104">Product Name</span></span>|<span data-ttu-id="bac55-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bac55-105">SQL Server</span></span>|  
|<span data-ttu-id="bac55-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="bac55-106">Event ID</span></span>|<span data-ttu-id="bac55-107">10003</span><span class="sxs-lookup"><span data-stu-id="bac55-107">10003</span></span>|  
|<span data-ttu-id="bac55-108">事件源</span><span class="sxs-lookup"><span data-stu-id="bac55-108">Event Source</span></span>|<span data-ttu-id="bac55-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bac55-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bac55-110">组件</span><span class="sxs-lookup"><span data-stu-id="bac55-110">Component</span></span>|<span data-ttu-id="bac55-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bac55-111">SQLEngine</span></span>|  
|<span data-ttu-id="bac55-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="bac55-112">Symbolic Name</span></span>|<span data-ttu-id="bac55-113">HR_E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bac55-113">HR_E_OUTOFMEMORY</span></span>|  
|<span data-ttu-id="bac55-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="bac55-114">Message Text</span></span>|<span data-ttu-id="bac55-115">提供程序内存不足。</span><span class="sxs-lookup"><span data-stu-id="bac55-115">The provider ran out of memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bac55-116">说明</span><span class="sxs-lookup"><span data-stu-id="bac55-116">Explanation</span></span>  
 <span data-ttu-id="bac55-117">系统内存不足导致 OLE DB 访问接口内存不足。</span><span class="sxs-lookup"><span data-stu-id="bac55-117">Low system memory has caused the OLE DB provider to run out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bac55-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="bac55-118">User Action</span></span>  
 <span data-ttu-id="bac55-119">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="bac55-119">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bac55-120">如果无效，请重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="bac55-120">If that does not help, restart the computer.</span></span> <span data-ttu-id="bac55-121">如果问题仍然存在，请使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 收集 OLE DB 跟踪事件，并向 OLE DB 提供程序的产品支持人员提供此数据。</span><span class="sxs-lookup"><span data-stu-id="bac55-121">If the problem persists, collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac55-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bac55-122">See Also</span></span>  
 <span data-ttu-id="bac55-123">[SQL Server Profiler 模板和权限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="bac55-123">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="bac55-124">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="bac55-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
