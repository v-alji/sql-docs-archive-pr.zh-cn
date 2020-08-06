---
title: 检查包含可疑页的数据库的完整性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cc1f87917c78f34ec7722fa21a1a67fda40a8c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682820"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a><span data-ttu-id="6a57f-102">检查包含可疑页的数据库的完整性</span><span class="sxs-lookup"><span data-stu-id="6a57f-102">Check Integrity of Database with Suspect Pages</span></span>
  <span data-ttu-id="6a57f-103">此规则检查数据库状态设置为可疑的用户数据库。</span><span class="sxs-lookup"><span data-stu-id="6a57f-103">This rule checks for user databases that have the database status set to suspect.</span></span> <span data-ttu-id="6a57f-104">当 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 读取包含 824 错误的数据库页时，该页将被视为可疑，其页 ID 将记录在 msdb 的 suspect_pages 表中，并且包含该页的数据库将设置为可疑。</span><span class="sxs-lookup"><span data-stu-id="6a57f-104">When the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.</span></span>  
  
 <span data-ttu-id="6a57f-105">错误 824 表示在读取操作期间检测到逻辑一致性错误。</span><span class="sxs-lookup"><span data-stu-id="6a57f-105">Error 824 indicates that a logical consistency error was detected during a read operation.</span></span> <span data-ttu-id="6a57f-106">此错误通常表示由有问题的 I/O 子系统组件引起的数据损坏。</span><span class="sxs-lookup"><span data-stu-id="6a57f-106">This error frequently indicates data corruption caused by a faulty I/O subsystem component.</span></span> <span data-ttu-id="6a57f-107">这是一个威胁数据库完整性的严重错误条件，必须立即纠正。</span><span class="sxs-lookup"><span data-stu-id="6a57f-107">This is a severe error condition that threatens database integrity and must be corrected immediately.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="6a57f-108">最佳做法建议</span><span class="sxs-lookup"><span data-stu-id="6a57f-108">Best Practices Recommendations</span></span>  
  
-   <span data-ttu-id="6a57f-109">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以了解此数据库的 824 错误的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6a57f-109">Review the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the details of the 824 error for this database.</span></span>  
  
-   <span data-ttu-id="6a57f-110">完成完整的数据库一致性检查 ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="6a57f-110">Complete a full database consistency check ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).</span></span>  
  
-   <span data-ttu-id="6a57f-111">实现在 [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)中定义的用户操作。</span><span class="sxs-lookup"><span data-stu-id="6a57f-111">Implement the user actions that are defined in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="6a57f-112">有关详细信息</span><span class="sxs-lookup"><span data-stu-id="6a57f-112">For More Information</span></span>  
 [<span data-ttu-id="6a57f-113">管理 suspect_pages 表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6a57f-113">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
