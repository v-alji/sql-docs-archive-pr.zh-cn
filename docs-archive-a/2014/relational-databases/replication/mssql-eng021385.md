---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b73d3216f07cb44d750a37149634258648f1bd48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688822"
---
# <a name="mssql_eng021385"></a><span data-ttu-id="0d532-102">MSSQL_ENG021385</span><span class="sxs-lookup"><span data-stu-id="0d532-102">MSSQL_ENG021385</span></span>
    
## <a name="message-details"></a><span data-ttu-id="0d532-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="0d532-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d532-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0d532-104">Product Name</span></span>|<span data-ttu-id="0d532-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0d532-105">SQL Server</span></span>|  
|<span data-ttu-id="0d532-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0d532-106">Event ID</span></span>|<span data-ttu-id="0d532-107">21385</span><span class="sxs-lookup"><span data-stu-id="0d532-107">21385</span></span>|  
|<span data-ttu-id="0d532-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0d532-108">Event Source</span></span>|<span data-ttu-id="0d532-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0d532-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0d532-110">组件</span><span class="sxs-lookup"><span data-stu-id="0d532-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="0d532-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="0d532-111">Symbolic Name</span></span>||  
|<span data-ttu-id="0d532-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="0d532-112">Message Text</span></span>|<span data-ttu-id="0d532-113">快照无法处理发布 '%s'。</span><span class="sxs-lookup"><span data-stu-id="0d532-113">Snapshot failed to process publication '%s'.</span></span> <span data-ttu-id="0d532-114">可能是由于活动架构的更改操作或者是所添加的新项目所致。</span><span class="sxs-lookup"><span data-stu-id="0d532-114">Possibly due to active schema change activity or new articles being added.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d532-115">说明</span><span class="sxs-lookup"><span data-stu-id="0d532-115">Explanation</span></span>  
 <span data-ttu-id="0d532-116">如果快照代理开始运行时正在对发布数据库进行更改（包括添加或删除项目以及对已发布的对象执行架构更改），就会产生此错误。</span><span class="sxs-lookup"><span data-stu-id="0d532-116">This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d532-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="0d532-117">User Action</span></span>  
 <span data-ttu-id="0d532-118">完成对发布数据库的更改后，重新启动快照代理。</span><span class="sxs-lookup"><span data-stu-id="0d532-118">Restart the Snapshot Agent after changes to the publication database are complete.</span></span> <span data-ttu-id="0d532-119">有关详细信息，请参阅[启动和停止复制代理 (SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 和[复制代理可执行文件概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="0d532-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d532-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d532-120">See Also</span></span>  
 [<span data-ttu-id="0d532-121">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="0d532-121">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
