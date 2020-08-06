---
title: 升级后验证计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18cc0f93ddec46025f659bcb9489bfff3ca846ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689865"
---
# <a name="validate-plan-guides-after-upgrade"></a><span data-ttu-id="afd45-102">升级后验证计划指南</span><span class="sxs-lookup"><span data-stu-id="afd45-102">Validate Plan Guides After Upgrade</span></span>
  <span data-ttu-id="afd45-103">建议在将应用程序升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的新版本时，重新评估和测试计划指南定义。</span><span class="sxs-lookup"><span data-stu-id="afd45-103">We recommend re-evaluating and testing plan guide definitions when you upgrade your application to a new release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afd45-104">性能优化要求和计划指南匹配行为可能会发生更改。</span><span class="sxs-lookup"><span data-stu-id="afd45-104">Performance tuning requirements and plan guide matching behavior may change.</span></span> <span data-ttu-id="afd45-105">尽管无效的计划指南不会导致查询失败，但仍应在不使用计划指南的情况下对计划进行编译，并且该计划可能不是最好的选择。</span><span class="sxs-lookup"><span data-stu-id="afd45-105">Although an invalid plan guide will not cause a query to fail, the plan is compiled without using the plan guide and may not be the best choice.</span></span> <span data-ttu-id="afd45-106">将数据库升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]后，建议执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="afd45-106">After upgrading a database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="afd45-107">使用 [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) 函数验证现有的计划指南。</span><span class="sxs-lookup"><span data-stu-id="afd45-107">Validate existing plan guides by using the [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="afd45-108">使用扩展事件可通过使用 [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) 事件监视在一段时间内是否有被误导的计划。</span><span class="sxs-lookup"><span data-stu-id="afd45-108">Use extended events to monitor for misguided plans for some period of time by using the [Plan Guide Unsuccessful](../event-classes/plan-guide-unsuccessful-event-class.md) event.</span></span>  
  
  
