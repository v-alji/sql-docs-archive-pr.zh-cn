---
title: 设置最大并行度选项以获取最佳性能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3043a656cbe1ac1ec40f0d0a67b6eac057005af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693262"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a><span data-ttu-id="58d90-102">设置最大并行度选项以获取最佳性能</span><span class="sxs-lookup"><span data-stu-id="58d90-102">Set the Max Degree of Parallelism Option for Optimal Performance</span></span>
  <span data-ttu-id="58d90-103">此规则确定最大并行度 (MAXDOP) 选项是否设置为大于 8 的值。</span><span class="sxs-lookup"><span data-stu-id="58d90-103">This rule determines whether the max degree of parallelism (MAXDOP) option for a value greater than 8.</span></span> <span data-ttu-id="58d90-104">将此选项设置为大于 8 的值通常导致不必要的资源消耗和性能下降。</span><span class="sxs-lookup"><span data-stu-id="58d90-104">Setting this option to a larger value often causes unwanted resource consumption and performance degradation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="58d90-105">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="58d90-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="58d90-106">通过使用 sp_configure 将最大并行度选项设置为 8 或更小。</span><span class="sxs-lookup"><span data-stu-id="58d90-106">Set the max degree of parallelism option to 8 or less by using sp_configure.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="58d90-107">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="58d90-107">For More Information</span></span>  
 [<span data-ttu-id="58d90-108">Microsoft 知识库文章 329204</span><span class="sxs-lookup"><span data-stu-id="58d90-108">Microsoft Knowledge Base article 329204</span></span>](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [<span data-ttu-id="58d90-109">配置 max degree of parallelism 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="58d90-109">Configure the max degree of parallelism Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [<span data-ttu-id="58d90-110">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="58d90-110">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
