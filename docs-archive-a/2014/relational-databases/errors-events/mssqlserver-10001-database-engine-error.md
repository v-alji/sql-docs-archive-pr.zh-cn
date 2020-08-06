---
title: MSSQLSERVER_10001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0542f6d52a4fd194c4b0ae5d1aad501f5e3b8c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691216"
---
# <a name="mssqlserver_10001"></a><span data-ttu-id="575f4-102">MSSQLSERVER_10001</span><span class="sxs-lookup"><span data-stu-id="575f4-102">MSSQLSERVER_10001</span></span>
    
## <a name="details"></a><span data-ttu-id="575f4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="575f4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="575f4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="575f4-104">Product Name</span></span>|<span data-ttu-id="575f4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="575f4-105">SQL Server</span></span>|  
|<span data-ttu-id="575f4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="575f4-106">Event ID</span></span>|<span data-ttu-id="575f4-107">10001</span><span class="sxs-lookup"><span data-stu-id="575f4-107">10001</span></span>|  
|<span data-ttu-id="575f4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="575f4-108">Event Source</span></span>|<span data-ttu-id="575f4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="575f4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="575f4-110">组件</span><span class="sxs-lookup"><span data-stu-id="575f4-110">Component</span></span>|<span data-ttu-id="575f4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="575f4-111">SQLEngine</span></span>|  
|<span data-ttu-id="575f4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="575f4-112">Symbolic Name</span></span>|<span data-ttu-id="575f4-113">HR_E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="575f4-113">HR_E_UNEXPECTED</span></span>|  
|<span data-ttu-id="575f4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="575f4-114">Message Text</span></span>|<span data-ttu-id="575f4-115">提供程序报告了意外的灾难性错误。</span><span class="sxs-lookup"><span data-stu-id="575f4-115">The provider reported an unexpected catastrophic failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="575f4-116">说明</span><span class="sxs-lookup"><span data-stu-id="575f4-116">Explanation</span></span>  
 <span data-ttu-id="575f4-117">分布式查询处理在调用 OLE DB 访问接口期间遇到一个一般性错误。</span><span class="sxs-lookup"><span data-stu-id="575f4-117">Distributed query processing encountered a generic error while calling into the OLE DB provider.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="575f4-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="575f4-118">User Action</span></span>  
 <span data-ttu-id="575f4-119">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 收集 OLE DB 跟踪事件并向 OLE DB 提供程序的产品支持人员提供此数据。</span><span class="sxs-lookup"><span data-stu-id="575f4-119">Collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and  provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575f4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="575f4-120">See Also</span></span>  
 <span data-ttu-id="575f4-121">[SQL Server Profiler 模板和权限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="575f4-121">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="575f4-122">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="575f4-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
