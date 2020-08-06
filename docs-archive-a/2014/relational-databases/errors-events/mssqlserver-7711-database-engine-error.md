---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e29b2ea993e8e5332ef03b05f628dc791e20aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586716"
---
# <a name="mssqlserver_7711"></a><span data-ttu-id="5e202-102">MSSQLSERVER_7711</span><span class="sxs-lookup"><span data-stu-id="5e202-102">MSSQLSERVER_7711</span></span>
    
## <a name="details"></a><span data-ttu-id="5e202-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5e202-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e202-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5e202-104">Product Name</span></span>|<span data-ttu-id="5e202-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5e202-105">SQL Server</span></span>|  
|<span data-ttu-id="5e202-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5e202-106">Event ID</span></span>|<span data-ttu-id="5e202-107">7711</span><span class="sxs-lookup"><span data-stu-id="5e202-107">7711</span></span>|  
|<span data-ttu-id="5e202-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5e202-108">Event Source</span></span>|<span data-ttu-id="5e202-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5e202-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5e202-110">组件</span><span class="sxs-lookup"><span data-stu-id="5e202-110">Component</span></span>|<span data-ttu-id="5e202-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5e202-111">SQLEngine</span></span>|  
|<span data-ttu-id="5e202-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5e202-112">Symbolic Name</span></span>|<span data-ttu-id="5e202-113">PRT_RANGE_OVERLAP</span><span class="sxs-lookup"><span data-stu-id="5e202-113">PRT_RANGE_OVERLAP</span></span>|  
|<span data-ttu-id="5e202-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5e202-114">Message Text</span></span>|<span data-ttu-id="5e202-115">为表或索引或其中一个分区多次指定了 DATA_COMPRESSION 选项。</span><span class="sxs-lookup"><span data-stu-id="5e202-115">The DATA_COMPRESSION option was specified more than once for the table or index or one of its partitions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5e202-116">说明</span><span class="sxs-lookup"><span data-stu-id="5e202-116">Explanation</span></span>  
 <span data-ttu-id="5e202-117">以下语句之一中的 DATA_COMPRESSION 选项出错：</span><span class="sxs-lookup"><span data-stu-id="5e202-117">An error occurred in the DATA_COMPRESSION option in one of the following statements:</span></span>  
  
-   <span data-ttu-id="5e202-118">CREATE TABLE</span><span class="sxs-lookup"><span data-stu-id="5e202-118">CREATE TABLE</span></span>  
  
-   <span data-ttu-id="5e202-119">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="5e202-119">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="5e202-120">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="5e202-120">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="5e202-121">ALTER INDEX</span><span class="sxs-lookup"><span data-stu-id="5e202-121">ALTER INDEX</span></span>  
  
 <span data-ttu-id="5e202-122">如果引用的表或索引已分区，则 DATA_COMPRESSION 选项对其中至少一个分区列出了不止一次。</span><span class="sxs-lookup"><span data-stu-id="5e202-122">If the table or index cited is partitioned, the DATA_COMPRESSION option was listed more than one time for at least one of the partitions.</span></span> <span data-ttu-id="5e202-123">如果表或索引未分区，则不止一次引用了 DATA_COMPRESSION 选项。</span><span class="sxs-lookup"><span data-stu-id="5e202-123">If the table or index is not partitioned, the DATA_COMPRESSION option was cited more than one time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e202-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="5e202-124">User Action</span></span>  
 <span data-ttu-id="5e202-125">对于已分区表或已分区索引，请确保仅对每个分区指定一次 DATA_COMPRESSION 选项。</span><span class="sxs-lookup"><span data-stu-id="5e202-125">For a partitioned table or index, make sure that the DATA_COMPRESSION option is specified only one time for each partition.</span></span> <span data-ttu-id="5e202-126">对于未分区的表或索引，请在语句中仅使用一次 DATA_COMPRESSION 选项。</span><span class="sxs-lookup"><span data-stu-id="5e202-126">For a table or index that is not partitioned, use the DATA_COMPRESSION option only one time in the statement.</span></span>  
  
  
