---
title: 数据库引擎扩展存储过程编程 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], programming
- stored procedures [SQL Server], extended
- Database Engine [SQL Server], stored procedures
- macros [SQL Server]
- Extended Stored Procedure API [SQL Server]
ms.assetid: 158a6765-0542-4e84-b5ab-f173d946ef5e
author: rothja
ms.author: jroth
ms.openlocfilehash: fecb8f996ddfcaede83cdb330e9c82bffdce5819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590861"
---
# <a name="database-engine-extended-stored-procedure-programming"></a><span data-ttu-id="487cc-102">数据库引擎扩展存储过程编程</span><span class="sxs-lookup"><span data-stu-id="487cc-102">Database Engine Extended Stored Procedure Programming</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="487cc-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="487cc-103">Use CLR Integration instead.</span></span> <span data-ttu-id="487cc-104">有关详细信息，请参阅[公共语言运行时 (CLR) 集成编程概念](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="487cc-104">For more information, see [Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](clr-integration/common-language-runtime-clr-integration-programming-concepts.md).</span></span>  
  
 <span data-ttu-id="487cc-105">[!INCLUDE[msCoName](../includes/msconame-md.md)]扩展存储过程 API 提供基于服务器的应用程序编程接口 (API) 来扩展 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="487cc-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Extended Stored Procedure API provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="487cc-106">此 API 由用于生成应用程序的 C 和 C++ 函数以及宏组成，分为扩展存储过程和网关应用程序两个类别。</span><span class="sxs-lookup"><span data-stu-id="487cc-106">The API consists of C and C++ functions and macros used to build applications in the following categories: extended stored procedures and gateway applications.</span></span>  
  
 <span data-ttu-id="487cc-107">使用扩展存储过程可以用编程语言（例如 C）创建自己的外部例程。扩展存储过程对于用户的显示方式和执行方式与典型存储过程相同。</span><span class="sxs-lookup"><span data-stu-id="487cc-107">Extended stored procedures allow you to create your own external routines in a programming language such as C. The extended stored procedures appear to users as typical stored procedures and are executed in the same way.</span></span> <span data-ttu-id="487cc-108">可以将参数传递给扩展存储过程，而且扩展存储过程可以返回结果和状态。</span><span class="sxs-lookup"><span data-stu-id="487cc-108">Parameters can be passed to extended stored procedures, and they can return results and return status.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="487cc-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="487cc-109">In This Section</span></span>  
 [<span data-ttu-id="487cc-110">编写扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="487cc-110">Programming Extended Stored Procedures</span></span>](extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)  
 <span data-ttu-id="487cc-111">说明如何创建、管理和使用扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="487cc-111">Explains how to create, manage, and use extended stored procedures.</span></span>  
  
 [<span data-ttu-id="487cc-112">扩展存储过程程序员参考</span><span class="sxs-lookup"><span data-stu-id="487cc-112">Extended Stored Procedures Programmer's Reference</span></span>](extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
 <span data-ttu-id="487cc-113">包含扩展存储过程 API 的参考主题。</span><span class="sxs-lookup"><span data-stu-id="487cc-113">Contains reference topics for the Extended Stored Procedure API.</span></span>  
  
  
