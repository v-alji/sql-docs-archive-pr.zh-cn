---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8577b07586553f4b03714cd31451ac755faf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577723"
---
# <a name="mssqlserver_2519"></a><span data-ttu-id="edf1f-102">MSSQLSERVER_2519</span><span class="sxs-lookup"><span data-stu-id="edf1f-102">MSSQLSERVER_2519</span></span>
    
## <a name="details"></a><span data-ttu-id="edf1f-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="edf1f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edf1f-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="edf1f-104">Product Name</span></span>|<span data-ttu-id="edf1f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="edf1f-105">SQL Server</span></span>|  
|<span data-ttu-id="edf1f-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="edf1f-106">Event ID</span></span>|<span data-ttu-id="edf1f-107">2519</span><span class="sxs-lookup"><span data-stu-id="edf1f-107">2519</span></span>|  
|<span data-ttu-id="edf1f-108">事件源</span><span class="sxs-lookup"><span data-stu-id="edf1f-108">Event Source</span></span>|<span data-ttu-id="edf1f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="edf1f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="edf1f-110">组件</span><span class="sxs-lookup"><span data-stu-id="edf1f-110">Component</span></span>|<span data-ttu-id="edf1f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="edf1f-111">SQLEngine</span></span>|  
|<span data-ttu-id="edf1f-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="edf1f-112">Symbolic Name</span></span>|<span data-ttu-id="edf1f-113">DBCC_NO_EXPRESSION_EVALUATOR</span><span class="sxs-lookup"><span data-stu-id="edf1f-113">DBCC_NO_EXPRESSION_EVALUATOR</span></span>|  
|<span data-ttu-id="edf1f-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="edf1f-114">Message Text</span></span>|<span data-ttu-id="edf1f-115">由于无法初始化内部的表达式计算器，从而无法检查对象 ID O_ID（对象 "O_NAME"）的计算列和用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="edf1f-115">Computed columns and user-defined types cannot be checked for object ID O_ID (object "O_NAME") because the internal expression evaluator could not be initialized.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="edf1f-116">说明</span><span class="sxs-lookup"><span data-stu-id="edf1f-116">Explanation</span></span>  
 <span data-ttu-id="edf1f-117">此信息性消息指示，查询处理器无法为 DBCC 提供内部对象，以允许对计算列和公共语言运行时 (CLR) 用户定义类型进行计算。</span><span class="sxs-lookup"><span data-stu-id="edf1f-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for the evaluation of computed columns and common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="edf1f-118">这意味着在 DBCC 检查索引和基表之间的一致性时，将不检查计算列和 CLR 用户定义类型是否正确或使用它们。</span><span class="sxs-lookup"><span data-stu-id="edf1f-118">This means that computed columns and CLR user-defined types will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="edf1f-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="edf1f-119">User Action</span></span>  
 <span data-ttu-id="edf1f-120">无</span><span class="sxs-lookup"><span data-stu-id="edf1f-120">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf1f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edf1f-121">See Also</span></span>  
 [<span data-ttu-id="edf1f-122">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="edf1f-122">MSSQLSERVER_2518</span></span>](mssqlserver-2518-database-engine-error.md)  
  
  
