---
title: TSQL 事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 763d5f31fd3562f54b274a74324ed4715b623a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682851"
---
# <a name="tsql-event-category"></a><span data-ttu-id="1c1f1-102">TSQL 事件类别</span><span class="sxs-lookup"><span data-stu-id="1c1f1-102">TSQL Event Category</span></span>
  <span data-ttu-id="1c1f1-103">**TSQL** 事件类别包含一般的 TSQL 事件。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-103">The **TSQL** event category contains general TSQL events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c1f1-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="1c1f1-104">In This Section</span></span>  
  
|<span data-ttu-id="1c1f1-105">主题</span><span class="sxs-lookup"><span data-stu-id="1c1f1-105">Topic</span></span>|<span data-ttu-id="1c1f1-106">说明</span><span class="sxs-lookup"><span data-stu-id="1c1f1-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1c1f1-107">Exec Prepared SQL 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-107">Exec Prepared SQL Event Class</span></span>](exec-prepared-sql-event-class.md)|<span data-ttu-id="1c1f1-108">指示 SqlClient、ODBC、OLE DB 或 DB-Library 执行了已准备好的一条或多条 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-108">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has executed a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="1c1f1-109">Prepare SQL 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-109">Prepare SQL Event Class</span></span>](prepare-sql-event-class.md)|<span data-ttu-id="1c1f1-110">指示 SqlClient、ODBC、OLE DB 或 DB-Library 已准备好了一条或多条要使用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-110">Indicates that SqlClient, ODBC, OLE DB, or DB-Library has prepared a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements for use.</span></span>|  
|[<span data-ttu-id="1c1f1-111">SQL:BatchCompleted 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-111">SQL:BatchCompleted Event Class</span></span>](sql-batchcompleted-event-class.md)|<span data-ttu-id="1c1f1-112">指示已完成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-112">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch has completed.</span></span>|  
|[<span data-ttu-id="1c1f1-113">SQL:BatchStarting 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-113">SQL:BatchStarting Event Class</span></span>](sql-batchstarting-event-class.md)|<span data-ttu-id="1c1f1-114">指示正在启动 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-114">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch is starting.</span></span>|  
|[<span data-ttu-id="1c1f1-115">SQL:StmtCompleted 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-115">SQL:StmtCompleted Event Class</span></span>](sql-stmtcompleted-event-class.md)|<span data-ttu-id="1c1f1-116">指示已完成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-116">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement has completed.</span></span>|  
|[<span data-ttu-id="1c1f1-117">SQL:StmtRecompile 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-117">SQL:StmtRecompile Event Class</span></span>](sql-stmtrecompile-event-class.md)|<span data-ttu-id="1c1f1-118">指示由下列所有类型的批处理引起的语句级重新编译：存储过程、触发器、即席批查询和查询。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-118">Indicates statement-level recompilations caused by all types of batches: stored procedures, triggers, ad hoc batches, and queries.</span></span>|  
|[<span data-ttu-id="1c1f1-119">SQL:StmtStarting 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-119">SQL:StmtStarting Event Class</span></span>](sql-stmtstarting-event-class.md)|<span data-ttu-id="1c1f1-120">指示正在启动 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-120">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is starting.</span></span>|  
|[<span data-ttu-id="1c1f1-121">Unprepare SQL 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-121">Unprepare SQL Event Class</span></span>](unprepare-sql-event-class.md)|<span data-ttu-id="1c1f1-122">指示 SqlClient、ODBC、OLE DB 或 DB-Library 删除了已准备好的一条或多条 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-122">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has deleted a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="1c1f1-123">XQuery Static Type 事件类</span><span class="sxs-lookup"><span data-stu-id="1c1f1-123">XQuery Static Type Event Class</span></span>](xquery-static-type-event-class.md)|<span data-ttu-id="1c1f1-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 执行 XQuery 表达式时出现。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-124">Occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes an XQuery expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c1f1-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c1f1-125">See Also</span></span>  
 [<span data-ttu-id="1c1f1-126">Transact-SQL 引用（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="1c1f1-126">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
