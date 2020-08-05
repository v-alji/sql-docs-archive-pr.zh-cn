---
title: CLR 集成的体系结构 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], architecture
- architecture [CLR integration]
ms.assetid: 05e4b872-3d21-46de-b4d5-739b5f2a0cf9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bb32e2c7f5eb2079146a2fee64af2e2dbc1d3356
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579740"
---
# <a name="architecture-of-clr-integration"></a><span data-ttu-id="32c66-102">CLR 集成体系结构</span><span class="sxs-lookup"><span data-stu-id="32c66-102">Architecture of CLR Integration</span></span>
  <span data-ttu-id="32c66-103">与 .NET Framework 公共语言运行时 (CLR) 集成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使数据库程序员可以使用诸如 Visual C#、Visual Basic .NET 和 Visual C++ 等语言。</span><span class="sxs-lookup"><span data-stu-id="32c66-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR) enables database programmers to use languages such as Visual C#, Visual Basic .NET, and Visual C++.</span></span> <span data-ttu-id="32c66-104">函数、存储过程、触发器、数据类型和聚合即属于程序员可以用这些语言编写的业务逻辑种类。</span><span class="sxs-lookup"><span data-stu-id="32c66-104">Functions, stored procedures, triggers, data types, and aggregates are among the kinds of business logic that programmers can write with these languages.</span></span>  
  
 <span data-ttu-id="32c66-105">本节阐述了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内的 CLR 集成体系结构，以及该体系结构如何提供安全可靠、可缩放且高效的用户代码运行环境。</span><span class="sxs-lookup"><span data-stu-id="32c66-105">This section describes the architecture of CLR integration inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and how this architecture provides a safe, scalable, secure, and efficient environment to run user code.</span></span>  
  
 <span data-ttu-id="32c66-106">下表列出了本节的主题。</span><span class="sxs-lookup"><span data-stu-id="32c66-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="32c66-107">CLR 宿主环境</span><span class="sxs-lookup"><span data-stu-id="32c66-107">CLR Hosted Environment</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
 <span data-ttu-id="32c66-108">讨论 CLR 集成的体系结构设计目标、机制以及优势。</span><span class="sxs-lookup"><span data-stu-id="32c66-108">Discusses architectural design goals, mechanisms, and benefits of CLR integration.</span></span>  
  
 [<span data-ttu-id="32c66-109">CLR 集成的性能</span><span class="sxs-lookup"><span data-stu-id="32c66-109">Performance of CLR Integration</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
 <span data-ttu-id="32c66-110">纵览 CLR 集成体系结构的性能注意事项。</span><span class="sxs-lookup"><span data-stu-id="32c66-110">Covers performance considerations of the CLR integration architecture.</span></span>  
  
  
