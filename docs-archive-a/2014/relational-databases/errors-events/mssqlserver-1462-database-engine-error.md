---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 704b847bde2d7b4da9da91b4b24bfe2b9e2afa07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589647"
---
# <a name="mssqlserver_1462"></a><span data-ttu-id="27e52-102">MSSQLSERVER_1462</span><span class="sxs-lookup"><span data-stu-id="27e52-102">MSSQLSERVER_1462</span></span>
    
## <a name="details"></a><span data-ttu-id="27e52-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="27e52-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27e52-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="27e52-104">Product Name</span></span>|<span data-ttu-id="27e52-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="27e52-105">SQL Server</span></span>|  
|<span data-ttu-id="27e52-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="27e52-106">Event ID</span></span>|<span data-ttu-id="27e52-107">1462</span><span class="sxs-lookup"><span data-stu-id="27e52-107">1462</span></span>|  
|<span data-ttu-id="27e52-108">事件源</span><span class="sxs-lookup"><span data-stu-id="27e52-108">Event Source</span></span>|<span data-ttu-id="27e52-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="27e52-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="27e52-110">组件</span><span class="sxs-lookup"><span data-stu-id="27e52-110">Component</span></span>|<span data-ttu-id="27e52-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="27e52-111">SQLEngine</span></span>|  
|<span data-ttu-id="27e52-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="27e52-112">Symbolic Name</span></span>|<span data-ttu-id="27e52-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span><span class="sxs-lookup"><span data-stu-id="27e52-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span></span>|  
|<span data-ttu-id="27e52-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="27e52-114">Message Text</span></span>|<span data-ttu-id="27e52-115">由于重做操作失败，数据库镜像被禁用。</span><span class="sxs-lookup"><span data-stu-id="27e52-115">Database mirroring is disabled due to a failed redo operation.</span></span> <span data-ttu-id="27e52-116">无法恢复。</span><span class="sxs-lookup"><span data-stu-id="27e52-116">Unable to resume.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="27e52-117">说明</span><span class="sxs-lookup"><span data-stu-id="27e52-117">Explanation</span></span>  
 <span data-ttu-id="27e52-118">数据库镜像无法对镜像重做日志记录。</span><span class="sxs-lookup"><span data-stu-id="27e52-118">Database mirroring failed to redo a log record on the mirror.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="27e52-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="27e52-119">Possible Causes</span></span>  
 <span data-ttu-id="27e52-120">最可能的原因是，添加文件操作在主体数据库上完成，但由于主体服务器和镜像服务器上的文件名和目录结构不同而使该操作在镜像数据库上失败。</span><span class="sxs-lookup"><span data-stu-id="27e52-120">The most likely cause is that an add-file operation completed on the principal database but then failed on the mirror database because file names or directory structures differ on the principal server and mirror server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="27e52-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="27e52-121">User Action</span></span>  
 <span data-ttu-id="27e52-122">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志，了解产生此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="27e52-122">Look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the cause of this error.</span></span> <span data-ttu-id="27e52-123">尝试解决此原因并恢复对数据库的镜像。</span><span class="sxs-lookup"><span data-stu-id="27e52-123">Try to resolve the cause and resume mirroring on the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e52-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27e52-124">See Also</span></span>  
 [<span data-ttu-id="27e52-125">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="27e52-125">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
