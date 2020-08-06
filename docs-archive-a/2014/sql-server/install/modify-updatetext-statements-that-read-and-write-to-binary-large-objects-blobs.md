---
title: 修改对二进制大型对象进行读写的 UPDATETEXT 语句 (Blob) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 061e7bad0bae5a74d103406265ad79195f79f7db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586169"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a><span data-ttu-id="4ac75-102">修改读写到二进制大型对象(BLOB)的 UPDATETEXT 语句</span><span class="sxs-lookup"><span data-stu-id="4ac75-102">Modify UPDATETEXT statements that read and write to binary large objects (BLOBs)</span></span>
  <span data-ttu-id="4ac75-103">升级顾问检测到 UPDATETEXT 语句使用同一文本指针读写相同的二进制大型对象 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="4ac75-103">Upgrade Advisor detected UPDATETEXT statements that read and write to the same binary large objects (BLOB) by using the same text pointer.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="4ac75-104">不支持以这种方式使用文本指针。</span><span class="sxs-lookup"><span data-stu-id="4ac75-104">does not support the use of text pointers in this manner.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4ac75-105">组件</span><span class="sxs-lookup"><span data-stu-id="4ac75-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="4ac75-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="4ac75-106">Corrective Action</span></span>  
 <span data-ttu-id="4ac75-107">请将 BLOB 复制到一个临时表或表变量，然后将值赋回给原始列。</span><span class="sxs-lookup"><span data-stu-id="4ac75-107">Copy the BLOB to a temporary table or to a table variable, and then assign the value back to the original column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac75-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ac75-108">See Also</span></span>  
 <span data-ttu-id="4ac75-109">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4ac75-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4ac75-110">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="4ac75-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
