---
title: SQL Server .NET Framework 中的数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- System.Data library
- System.Data.SqlTypes namespace
- data types [CLR integration]
- SqlTypes library
- database objects [CLR integration], data types
- common language runtime [SQL Server], data types
- building database objects [CLR integration], data types
- mapping data types [CLR integration]
ms.assetid: c70d3ffe-2c32-45a5-849b-ef113dda09b9
author: rothja
ms.author: jroth
ms.openlocfilehash: fe0ed680e7050c58738301256575e4138f21276f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693973"
---
# <a name="sql-server-data-types-in-the-net-framework"></a><span data-ttu-id="ebe91-102">.NET Framework 中的 SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="ebe91-102">SQL Server Data Types in the .NET Framework</span></span>
  <span data-ttu-id="ebe91-103">`SqlTypes` 库是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 的基类库的一部分。</span><span class="sxs-lookup"><span data-stu-id="ebe91-103">The `SqlTypes` library is part of the base class library of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="ebe91-104">它设计为向数据类型提供与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中相同的语义和精度。</span><span class="sxs-lookup"><span data-stu-id="ebe91-104">It is designed to provide data types with the same semantics and precision as those found in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="ebe91-105">本主题描述针对 .NET Framework 程序员的新语义，并且介绍在 `System.Data.SqlTypes` 库中包括的 `System.Data` 命名空间中实现的类型。</span><span class="sxs-lookup"><span data-stu-id="ebe91-105">This topic describes the new semantics to .NET Framework programmers, and introduces the types implemented in the `System.Data.SqlTypes` namespace that is included in the `System.Data` library.</span></span>  
  
 <span data-ttu-id="ebe91-106">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="ebe91-106">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="ebe91-107">为 Null 性和三值逻辑比较</span><span class="sxs-lookup"><span data-stu-id="ebe91-107">Nullability and Three-Value Logic Comparisons</span></span>](nullability-and-three-value-logic-comparisons.md)  
 <span data-ttu-id="ebe91-108">介绍如何使用公共语义运行时 (CLR) 集成数据类型处理 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="ebe91-108">Discusses how NULL values are handled with common language runtime (CLR) integration data types.</span></span>  
  
 [<span data-ttu-id="ebe91-109">排序规则和 CLR 集成数据类型</span><span class="sxs-lookup"><span data-stu-id="ebe91-109">Collation and CLR Integration Data Types</span></span>](collation-and-clr-integration-data-types.md)  
 <span data-ttu-id="ebe91-110">介绍如何使用 CLR 集成处理排序规则。</span><span class="sxs-lookup"><span data-stu-id="ebe91-110">Describes how collations are handled with CLR integration.</span></span>  
  
 [<span data-ttu-id="ebe91-111">在 CLR 中处理大型对象 &#40;LOB&#41; 参数</span><span class="sxs-lookup"><span data-stu-id="ebe91-111">Handling Large Object &#40;LOB&#41; Parameters in the CLR</span></span>](handling-large-object-lob-parameters-in-the-clr.md)  
 <span data-ttu-id="ebe91-112">介绍如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 CLR 之间传递 LOB 类型。</span><span class="sxs-lookup"><span data-stu-id="ebe91-112">Describes how to pass LOB types between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the CLR.</span></span>  
  
 [<span data-ttu-id="ebe91-113">映射 CLR 参数数据</span><span class="sxs-lookup"><span data-stu-id="ebe91-113">Mapping CLR Parameter Data</span></span>](mapping-clr-parameter-data.md)  
 <span data-ttu-id="ebe91-114">显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、CLR 集成和 .NET Framework 之间的数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="ebe91-114">Shows data type mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CLR integration, and the .NET Framework.</span></span>  
  
  
