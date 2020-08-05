---
title: 本机编译的存储过程支持的构造 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: f3bc7e28fa2a868ac39c6adbb2dea3cc5c3ace73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580746"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a><span data-ttu-id="7cdd0-102">本机编译的存储过程支持的构造</span><span class="sxs-lookup"><span data-stu-id="7cdd0-102">Supported Constructs on Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="7cdd0-103">本主题列出了本机编译的存储过程中支持的构造。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-103">This topic lists the supported constructs on natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="7cdd0-104">有关不支持的构造的信息，请参阅 [内存中 OLTP 不支持的 Transact-SQL 构造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-104">For information about unsupported constructs, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="procedure-ddl"></a><span data-ttu-id="7cdd0-105">过程 DDL</span><span class="sxs-lookup"><span data-stu-id="7cdd0-105">Procedure DDL</span></span>  
 <span data-ttu-id="7cdd0-106">支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="7cdd0-106">The following are supported:</span></span>  
  
-   <span data-ttu-id="7cdd0-107">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7cdd0-107">CREATE PROCEDURE</span></span>  
  
-   <span data-ttu-id="7cdd0-108">DROP PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="7cdd0-108">DROP PROCEDURE</span></span>  
  
-   <span data-ttu-id="7cdd0-109">SCHEMABINDING（对于本机编译存储过程是必需的）</span><span class="sxs-lookup"><span data-stu-id="7cdd0-109">SCHEMABINDING (required for natively compiled stored procedures)</span></span>  
  
-   <span data-ttu-id="7cdd0-110">NATIVE_COMPILATION</span><span class="sxs-lookup"><span data-stu-id="7cdd0-110">NATIVE_COMPILATION</span></span>  
  
-   <span data-ttu-id="7cdd0-111">可将参数声明为 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-111">Parameters can be declared as NOT NULL.</span></span>  
  
-   <span data-ttu-id="7cdd0-112">表值参数。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-112">Table-valued parameters.</span></span>  
  
## <a name="security"></a><span data-ttu-id="7cdd0-113">安全性</span><span class="sxs-lookup"><span data-stu-id="7cdd0-113">Security</span></span>  
 <span data-ttu-id="7cdd0-114">支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="7cdd0-114">The following are supported:</span></span>  
  
-   <span data-ttu-id="7cdd0-115">用于过程：EXECUTE AS OWNER、SELF 和 USER。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-115">For procedures: EXECUTE AS OWNER, SELF, and user.</span></span>  
  
-   <span data-ttu-id="7cdd0-116">表和过程的 GRANT 和 DENY 权限。</span><span class="sxs-lookup"><span data-stu-id="7cdd0-116">GRANT and DENY permissions on tables and procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdd0-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cdd0-117">See Also</span></span>  
 [<span data-ttu-id="7cdd0-118">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="7cdd0-118">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
