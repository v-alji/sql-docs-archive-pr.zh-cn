---
title: 删除保留关键字后的冒号 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694244"
---
# <a name="remove-colon-following-reserved-keyword"></a><span data-ttu-id="9db3c-102">删除保留关键字后的冒号</span><span class="sxs-lookup"><span data-stu-id="9db3c-102">Remove colon following reserved keyword</span></span>
  <span data-ttu-id="9db3c-103">升级顾问检测到脚本中包含位于保留关键字后的冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="9db3c-103">The Upgrade Advisor detected a script that contains a colon (:) following a reserved keyword.</span></span> <span data-ttu-id="9db3c-104">在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，会忽略此语法，因而语句能够成功执行。</span><span class="sxs-lookup"><span data-stu-id="9db3c-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this syntax is ignored and the statements execute successfully.</span></span> <span data-ttu-id="9db3c-105">现在，当数据库兼容模式设置为 100 或更高时，此语法会导致语句执行失败。</span><span class="sxs-lookup"><span data-stu-id="9db3c-105">Now, this syntax causes the statement to fail when the database compatibility mode is set to 100 or later.</span></span>  
  
 <span data-ttu-id="9db3c-106">用户数据库将保持其兼容模式。</span><span class="sxs-lookup"><span data-stu-id="9db3c-106">User databases maintain their compatibility mode.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9db3c-107">组件</span><span class="sxs-lookup"><span data-stu-id="9db3c-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="9db3c-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="9db3c-108">Corrective Action</span></span>  
 <span data-ttu-id="9db3c-109">在将数据库兼容模式更改为 100 或更高之前，通过删除保留关键字后跟的冒号对脚本进行修改。</span><span class="sxs-lookup"><span data-stu-id="9db3c-109">Before you change the database compatibility mode to 100 or later, modify your scripts by removing colons that follow reserved keywords.</span></span> <span data-ttu-id="9db3c-110">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“sp_dbcmptlevel”。</span><span class="sxs-lookup"><span data-stu-id="9db3c-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db3c-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9db3c-111">See Also</span></span>  
 <span data-ttu-id="9db3c-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9db3c-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9db3c-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="9db3c-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
