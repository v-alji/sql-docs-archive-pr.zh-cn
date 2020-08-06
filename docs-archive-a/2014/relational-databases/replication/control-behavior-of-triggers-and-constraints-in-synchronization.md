---
title: 控制同步期间触发器和约束的行为 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88176f43295fe2ab1f5f5643a46db1ce6132c5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577565"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="f1a58-102">控制同步期间触发器和约束的行为（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="f1a58-102">Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="f1a58-103">在同步期间，复制代理对复制表执行 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)、[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) 和 [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) 语句，这可能导致执行这些表上的数据操作语言 (DML) 触发器。</span><span class="sxs-lookup"><span data-stu-id="f1a58-103">During synchronization, replication agents execute [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql), and [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) statements on replicated tables, which can cause data manipulation language (DML) triggers on these tables to be executed.</span></span> <span data-ttu-id="f1a58-104">有些情况下，可能需要在同步期间防止这些触发器触发或防止约束被强制执行。</span><span class="sxs-lookup"><span data-stu-id="f1a58-104">There are cases when you may need to prevent these triggers from firing or constraints from being enforced during synchronization.</span></span> <span data-ttu-id="f1a58-105">此行为取决于触发器或约束的创建方式。</span><span class="sxs-lookup"><span data-stu-id="f1a58-105">This behavior depends on how the trigger or constraint is created.</span></span>  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a><span data-ttu-id="f1a58-106">防止触发器在同步期间执行</span><span class="sxs-lookup"><span data-stu-id="f1a58-106">To prevent triggers from executing during synchronization</span></span>  
  
1.  <span data-ttu-id="f1a58-107">创建新触发器时，请指定 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) 的 NOT FOR REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="f1a58-107">When creating a new trigger, specify the NOT FOR REPLICATION option of [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
2.  <span data-ttu-id="f1a58-108">对于现有触发器，请指定 [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) 的 NOT FOR REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="f1a58-108">For an existing trigger, specify the NOT FOR REPLICATION option of [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).</span></span>  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a><span data-ttu-id="f1a58-109">防止约束在同步期间被强制执行</span><span class="sxs-lookup"><span data-stu-id="f1a58-109">To prevent constraints from being enforced during synchronization</span></span>  
  
1.  <span data-ttu-id="f1a58-110">创建新 CHECK 或 FOREIGN KEY 约束时，请在 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 的约束定义中指定 CHECK NOT FOR REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="f1a58-110">When creating a new CHECK or FOREIGN KEY constraint, specify CHECK NOT FOR REPLICATION option in the constraint definition of [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a58-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1a58-111">See Also</span></span>  
 [<span data-ttu-id="f1a58-112">创建表（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="f1a58-112">Create Tables &#40;Database Engine&#41;</span></span>](../tables/create-tables-database-engine.md)  
  
  
