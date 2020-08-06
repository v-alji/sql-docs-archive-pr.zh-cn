---
title: 显示和保存执行计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e236ed2a298bc8fc9a829948a864f6f5c27a2ba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688849"
---
# <a name="display-and-save-execution-plans"></a><span data-ttu-id="650b1-102">显示和保存执行计划</span><span class="sxs-lookup"><span data-stu-id="650b1-102">Display and Save Execution Plans</span></span>
  <span data-ttu-id="650b1-103">本节说明如何显示执行计划以及如何使用 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]将执行计划保存到 XML 格式的文件中。</span><span class="sxs-lookup"><span data-stu-id="650b1-103">This section explains how to display execution plans and how to save execution plans to a file in XML format by using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="650b1-104">执行计划以图形方式显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询优化器选择的数据检索方法。</span><span class="sxs-lookup"><span data-stu-id="650b1-104">Execution plans graphically display the data retrieval methods chosen by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer.</span></span> <span data-ttu-id="650b1-105">执行计划使用图标表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中特定语句和查询的执行开销，而不是使用 SET SHOWPLAN_ALL 或 SET SHOWPLAN_TEXT 语句生成的表格表示形式。</span><span class="sxs-lookup"><span data-stu-id="650b1-105">Execution plans represent the execution cost of specific statements and queries in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using icons rather than the tabular representation produced by the SET SHOWPLAN_ALL or SET SHOWPLAN_TEXT statements.</span></span> <span data-ttu-id="650b1-106">这种图形表示法对了解查询的性能特征非常有用。</span><span class="sxs-lookup"><span data-stu-id="650b1-106">This graphical approach is very useful for understanding the performance characteristics of a query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="650b1-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="650b1-107">In This Section</span></span>  
  
-   [<span data-ttu-id="650b1-108">显示估计的执行计划</span><span class="sxs-lookup"><span data-stu-id="650b1-108">Display the Estimated Execution Plan</span></span>](display-the-estimated-execution-plan.md)  
  
-   [<span data-ttu-id="650b1-109">显示实际执行计划</span><span class="sxs-lookup"><span data-stu-id="650b1-109">Display an Actual Execution Plan</span></span>](display-an-actual-execution-plan.md)  
  
-   [<span data-ttu-id="650b1-110">以 XML 格式保存执行计划</span><span class="sxs-lookup"><span data-stu-id="650b1-110">Save an Execution Plan in XML Format</span></span>](save-an-execution-plan-in-xml-format.md)  
  
  
