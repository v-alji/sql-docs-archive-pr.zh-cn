---
title: CLR 用户定义聚合 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587431"
---
# <a name="clr-user-defined-aggregates"></a><span data-ttu-id="180b3-102">CLR 用户定义聚合</span><span class="sxs-lookup"><span data-stu-id="180b3-102">CLR User-Defined Aggregates</span></span>
  <span data-ttu-id="180b3-103">聚合函数对一组值执行计算，并返回单个值。</span><span class="sxs-lookup"><span data-stu-id="180b3-103">Aggregate functions perform a calculation on a set of values and return a single value.</span></span> <span data-ttu-id="180b3-104">传统上， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 只支持内置聚合函数，例如 `SUM` 或 `MAX` ，它对一组输入标量值执行操作，并从该集生成单个聚合值。</span><span class="sxs-lookup"><span data-stu-id="180b3-104">Traditionally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has supported only built-in aggregate functions, such as `SUM` or `MAX`, that operate on a set of input scalar values and generate a single aggregate value from that set.</span></span> <span data-ttu-id="180b3-105">通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 公共语言运行时 (CLR) 的集成，现在开发人员能够利用托管代码创建自定义聚合函数，并且使这些函数可供 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他托管代码访问。</span><span class="sxs-lookup"><span data-stu-id="180b3-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) now allows developers to create custom aggregate functions in managed code, and to make these functions accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span>  
  
 <span data-ttu-id="180b3-106">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="180b3-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="180b3-107">CLR 用户定义聚合的要求</span><span class="sxs-lookup"><span data-stu-id="180b3-107">Requirements for CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates-requirements.md)  
 <span data-ttu-id="180b3-108">概述用于实现 CLR 用户定义聚合函数的要求。</span><span class="sxs-lookup"><span data-stu-id="180b3-108">Provides an overview of the requirements for implementing CLR user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="180b3-109">调用 CLR 用户定义聚合函数</span><span class="sxs-lookup"><span data-stu-id="180b3-109">Invoking CLR User-Defined Aggregate Functions</span></span>](clr-user-defined-aggregate-invoking-functions.md)  
 <span data-ttu-id="180b3-110">说明如何调用用户定义聚合。</span><span class="sxs-lookup"><span data-stu-id="180b3-110">Explains how to invoke user-defined aggregates.</span></span>  
  
  
