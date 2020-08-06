---
title: MSSQLSERVER_8710 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65fb6b3efb42c282347f560353a2b21edc337859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591906"
---
# <a name="mssqlserver_8710"></a><span data-ttu-id="36b58-102">MSSQLSERVER_8710</span><span class="sxs-lookup"><span data-stu-id="36b58-102">MSSQLSERVER_8710</span></span>
    
## <a name="details"></a><span data-ttu-id="36b58-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="36b58-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36b58-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="36b58-104">Product Name</span></span>|<span data-ttu-id="36b58-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="36b58-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="36b58-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="36b58-106">Event ID</span></span>|<span data-ttu-id="36b58-107">8710</span><span class="sxs-lookup"><span data-stu-id="36b58-107">8710</span></span>|  
|<span data-ttu-id="36b58-108">事件源</span><span class="sxs-lookup"><span data-stu-id="36b58-108">Event Source</span></span>|<span data-ttu-id="36b58-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="36b58-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="36b58-110">组件</span><span class="sxs-lookup"><span data-stu-id="36b58-110">Component</span></span>|<span data-ttu-id="36b58-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="36b58-111">SQLEngine</span></span>|  
|<span data-ttu-id="36b58-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="36b58-112">Symbolic Name</span></span>|<span data-ttu-id="36b58-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span><span class="sxs-lookup"><span data-stu-id="36b58-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span></span>|  
|<span data-ttu-id="36b58-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="36b58-114">Message Text</span></span>|<span data-ttu-id="36b58-115">必须提供与 CUBE、ROLLUP 或 GROUPING SET 查询一起使用的聚合函数，才能合并子聚合。</span><span class="sxs-lookup"><span data-stu-id="36b58-115">Aggregate functions that are used with CUBE, ROLLUP, or GROUPING SET queries must provide for the merging of subaggregates.</span></span> <span data-ttu-id="36b58-116">若要修复此问题，请删除该聚合函数或在 GROUP BY 子句基础上使用 UNION ALL 编写查询。</span><span class="sxs-lookup"><span data-stu-id="36b58-116">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="36b58-117">说明</span><span class="sxs-lookup"><span data-stu-id="36b58-117">Explanation</span></span>  
 <span data-ttu-id="36b58-118">CUBE、ROLLUP 或 GROUPING SETS 不提供合并子聚合的方法，而将它们与聚合函数一起使用即可合并子聚合。</span><span class="sxs-lookup"><span data-stu-id="36b58-118">An aggregate function has been used with CUBE, ROLLUP, or GROUPING SETS that does not provide a method for merging subaggregates.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36b58-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="36b58-119">User Action</span></span>  
 <span data-ttu-id="36b58-120">若要修复此问题，请删除该聚合函数或在 GROUP BY 子句基础上使用 UNION ALL 编写查询。</span><span class="sxs-lookup"><span data-stu-id="36b58-120">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>  
  
  
