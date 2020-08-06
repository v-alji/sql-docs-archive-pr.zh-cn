---
title: 删除对 DML 触发器内插入的和删除的表的 DDL 操作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 61f7ab78b5ab6251b7f27401d36423ec27141c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691530"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a><span data-ttu-id="9ec4d-102">删除对于在 DML 触发器内部插入和删除的表的 DDL 操作</span><span class="sxs-lookup"><span data-stu-id="9ec4d-102">Remove DDL operations on the inserted and deleted tables inside DML triggers</span></span>
  <span data-ttu-id="9ec4d-103">不能对 DML 触发器内部的插入表和删除表执行数据定义语言 (DDL) 语句，如 CREATE INDEX。</span><span class="sxs-lookup"><span data-stu-id="9ec4d-103">Data definition language (DDL) statements, such as CREATE INDEX, cannot be performed on the inserted and deleted tables inside DML triggers.</span></span> <span data-ttu-id="9ec4d-104">在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，允许对所插入和删除的表执行某些 DDL 语句。</span><span class="sxs-lookup"><span data-stu-id="9ec4d-104">Some DDL statements on the inserted and deleted tables are permitted in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ec4d-105">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“使用插入的和删除的表”。</span><span class="sxs-lookup"><span data-stu-id="9ec4d-105">For more information, see "Using the inserted and deleted Tables" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9ec4d-106">组件</span><span class="sxs-lookup"><span data-stu-id="9ec4d-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="9ec4d-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="9ec4d-107">Corrective Action</span></span>  
 <span data-ttu-id="9ec4d-108">删除对在 DML 触发器内部插入的和删除的表执行的所有 DDL 操作。</span><span class="sxs-lookup"><span data-stu-id="9ec4d-108">Remove any DDL operations that are performed on the inserted and deleted tables inside DML triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec4d-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ec4d-109">See Also</span></span>  
 <span data-ttu-id="9ec4d-110">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9ec4d-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9ec4d-111">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="9ec4d-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
