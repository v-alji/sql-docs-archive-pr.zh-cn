---
title: 运行 SQL Server Profiler 所需的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], permissions
- traces [SQL Server], replaying
- replaying traces
- SQL Server Profiler, permissions
- security [SQL Server], SQL Server Profiler
ms.assetid: 5c580a87-88ae-4314-8fe1-54ade83f227f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e73ffe2e127299db9a9e37e48f089aab2cccca52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692039"
---
# <a name="permissions-required-to-run-sql-server-profiler"></a><span data-ttu-id="5f3c9-102">运行 SQL Server Profiler 所需的权限</span><span class="sxs-lookup"><span data-stu-id="5f3c9-102">Permissions Required to Run SQL Server Profiler</span></span>
  <span data-ttu-id="5f3c9-103">默认情况下，用户运行 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 所需的权限与执行用于创建跟踪的 Transact-SQL 存储过程所需的权限相同。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-103">By default, running [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] requires the same user permissions as the Transact-SQL stored procedures that are used to create traces.</span></span> <span data-ttu-id="5f3c9-104">若要运行 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]，用户必须拥有 ALTER TRACE 权限。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-104">To run [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], users must be granted the ALTER TRACE permission.</span></span> <span data-ttu-id="5f3c9-105">有关详细信息，请参阅 [GRANT 服务器权限 (Transact-SQL)](/sql/t-sql/statements/grant-server-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-105">For more information, see [GRANT Server Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5f3c9-106">拥有 SHOWPLAN、ALTER TRACE 或 VIEW SERVER STATE 权限的用户可以对显示计划输出中捕获的查询进行查看。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-106">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="5f3c9-107">这些查询可能包含敏感信息，例如密码。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-107">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="5f3c9-108">因此，建议您仅将这些权限授予有权查看敏感信息的一类用户，例如 db_owner 固定数据库角色的成员或 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-108">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the db_owner fixed database role, or members of the sysadmin fixed server role.</span></span> <span data-ttu-id="5f3c9-109">此外，建议您最好将包含显示计划相关事件的显示计划文件或跟踪文件保存到使用 NTFS 文件系统的某个位置，并且只允许有权查看敏感信息的用户对之进行访问。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-109">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>

## <a name="permissions-used-to-replay-traces"></a><span data-ttu-id="5f3c9-110">用于重播跟踪的权限</span><span class="sxs-lookup"><span data-stu-id="5f3c9-110">Permissions Used to Replay Traces</span></span>
 <span data-ttu-id="5f3c9-111">重播跟踪也要求重播跟踪的用户拥有 ALTER TRACE 权限。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-111">Replaying traces also requires that the user who is replaying the trace have the ALTER TRACE permission.</span></span>

 <span data-ttu-id="5f3c9-112">但是，如果重播期间在重播的跟踪中遇到 Audit Login 事件， [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 将使用 EXECUTE AS 命令。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-112">However, during replay, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] uses the EXECUTE AS command if an Audit Login event is encountered in the trace that is being replayed.</span></span> [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="5f3c9-113">使用 EXECUTE AS 命令模拟与登录事件关联的用户。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-113">uses the EXECUTE AS command to impersonate the user who is associated with the login event.</span></span>

 <span data-ttu-id="5f3c9-114">如果 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 在重播的跟踪中遇到登录事件，将执行下列权限检查：</span><span class="sxs-lookup"><span data-stu-id="5f3c9-114">If [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] encounters a login event in a trace that is being replayed, the following permission checks are performed:</span></span>

1.  <span data-ttu-id="5f3c9-115">拥有 ALTER TRACE 权限的用户 1 开始重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-115">User1, who has the ALTER TRACE permission, starts replaying a trace.</span></span>

2.  <span data-ttu-id="5f3c9-116">在重播的跟踪中遇到用户 2 的登录事件。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-116">A login event for User2 is encountered in the replayed trace.</span></span>

3.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="5f3c9-117">使用 EXECUTE AS 命令模拟用户 2。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-117">uses the EXECUTE AS command to impersonate User2.</span></span>

4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f3c9-118">尝试验证用户 2 的身份，根据结果的不同会出现下列情况之一：</span><span class="sxs-lookup"><span data-stu-id="5f3c9-118">attempts to authenticate User2, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="5f3c9-119">如果用户 2 无法通过身份验证， [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 将返回一个错误，并以用户 1 的身份继续重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-119">If User2 cannot be authenticated, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] returns an error, and continues replaying the trace as User1.</span></span>

    2.  <span data-ttu-id="5f3c9-120">如果用户 2 成功通过身份验证，将以用户 2 的身份继续重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-120">If User2 is successfully authenticated, replaying the trace as User2 continues.</span></span>

5.  <span data-ttu-id="5f3c9-121">检查用户 2 对目标数据库的权限，根据结果的不同会出现下列情况之一：</span><span class="sxs-lookup"><span data-stu-id="5f3c9-121">Permissions for User2 are checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="5f3c9-122">如果用户 2 拥有对目标数据库的权限，则模拟成功，并以用户 2 的身份重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-122">If User2 has permissions on the target database, impersonation has succeeded, and the trace is replayed as User2.</span></span>

    2.  <span data-ttu-id="5f3c9-123">如果用户 2 不拥有对目标数据库的权限，则服务器将检查该数据库的 Guest 用户。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-123">If User2 does not have permissions on the target database, the server checks for a Guest user on that database.</span></span>

6.  <span data-ttu-id="5f3c9-124">将检查目标数据库中是否存在 Guest 用户，根据结果的不同会出现下列情况之一：</span><span class="sxs-lookup"><span data-stu-id="5f3c9-124">Existence of a Guest user is checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="5f3c9-125">如果 Guest 帐户存在，将以 Guest 帐户重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-125">If a Guest account exists, the trace is replayed as the Guest account.</span></span>

    2.  <span data-ttu-id="5f3c9-126">如果目标数据库中不存在 Guest 帐户，将返回一个错误，并以用户 1 的身份重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="5f3c9-126">If no Guest account exists on the target database, an error is returned and the trace is replayed as User1.</span></span>

 <span data-ttu-id="5f3c9-127">以下关系图说明了重播跟踪时此检查权限的过程：</span><span class="sxs-lookup"><span data-stu-id="5f3c9-127">The following diagram shows this process of checking permission when replaying traces:</span></span>

 <span data-ttu-id="5f3c9-128">![SQL Server Profiler 重播跟踪权限](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler 重播跟踪权限")</span><span class="sxs-lookup"><span data-stu-id="5f3c9-128">![SQL Server Profiler replay trace permissions](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler replay trace permissions")</span></span>

## <a name="see-also"></a><span data-ttu-id="5f3c9-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f3c9-129">See Also</span></span>
 <span data-ttu-id="5f3c9-130">[SQL Server Profiler 存储过程 &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [重播跟踪](replay-traces.md)[创建跟踪 &#40;SQL Server Profiler](create-a-trace-sql-server-profiler.md)&#41;[重播跟踪表 &#40;](replay-a-trace-table-sql-server-profiler.md) SQL Server Profiler&#41;[重播跟踪文件 &#40;SQL Server Profiler](replay-a-trace-file-sql-server-profiler.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="5f3c9-130">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [Replay Traces](replay-traces.md) [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md) [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)</span></span>


