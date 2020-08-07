---
title: MSSQLSERVER_10737 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df8a4de014552d3aca00b3eb244f7ff8df56756b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589140"
---
# <a name="mssqlserver_10737"></a><span data-ttu-id="be210-102">MSSQLSERVER_10737</span><span class="sxs-lookup"><span data-stu-id="be210-102">MSSQLSERVER_10737</span></span>
    
## <a name="details"></a><span data-ttu-id="be210-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="be210-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be210-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="be210-104">Product Name</span></span>|<span data-ttu-id="be210-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="be210-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="be210-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="be210-106">Event ID</span></span>|<span data-ttu-id="be210-107">10737</span><span class="sxs-lookup"><span data-stu-id="be210-107">10737</span></span>|  
|<span data-ttu-id="be210-108">事件源</span><span class="sxs-lookup"><span data-stu-id="be210-108">Event Source</span></span>|<span data-ttu-id="be210-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="be210-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="be210-110">组件</span><span class="sxs-lookup"><span data-stu-id="be210-110">Component</span></span>|<span data-ttu-id="be210-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="be210-111">SQLEngine</span></span>|  
|<span data-ttu-id="be210-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="be210-112">Symbolic Name</span></span>|<span data-ttu-id="be210-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span><span class="sxs-lookup"><span data-stu-id="be210-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span></span>|  
|<span data-ttu-id="be210-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="be210-114">Message Text</span></span>|<span data-ttu-id="be210-115">在 ALTER TABLE REBUILD 或 ALTER INDEX REBUILD 语句中，如果在 DATA_COMPRESSION 语句中指定了一个分区，则必须指定 PARTITION=ALL。</span><span class="sxs-lookup"><span data-stu-id="be210-115">In an ALTER TABLE REBUILD or ALTER INDEX REBUILD statement, when a partition is specified in a DATA_COMPRESSION clause, PARTITION=ALL must be specified.</span></span> <span data-ttu-id="be210-116">PARTITION=ALL 子句用来强调表或索引的所有分区将重新生成，即使仅在 DATA_COMPRESSION 子句中指定了一个子集也是如此。</span><span class="sxs-lookup"><span data-stu-id="be210-116">The PARTITION=ALL clause is used to reinforce that all partitions of the table or index will be rebuilt, even if only a subset is specified in the DATA_COMPRESSION clause.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="be210-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="be210-117">User Action</span></span>  
 <span data-ttu-id="be210-118">将 PARTITION=ALL 子句添加到 ALTER TABLE 或 ALTER INDEX 语句中。</span><span class="sxs-lookup"><span data-stu-id="be210-118">Add the PARTITION=ALL clause to the ALTER TABLE or ALTER INDEX statement.</span></span> <span data-ttu-id="be210-119">或者，若要重新生成特定分区，请使用 REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF})。</span><span class="sxs-lookup"><span data-stu-id="be210-119">Or, to rebuild a specific partition, use REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).</span></span>  
  
  
