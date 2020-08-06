---
title: 权限层次结构（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9a04e5595e509de63b362b31b240e113e635581d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688761"
---
# <a name="permissions-hierarchy-database-engine"></a><span data-ttu-id="77edf-102">权限层次结构（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="77edf-102">Permissions Hierarchy (Database Engine)</span></span>
  <span data-ttu-id="77edf-103">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 管理着可以通过权限进行保护的实体的分层集合。</span><span class="sxs-lookup"><span data-stu-id="77edf-103">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] manages a hierarchical collection of entities that can be secured with permissions.</span></span> <span data-ttu-id="77edf-104">这些实体称为“安全对象” 。</span><span class="sxs-lookup"><span data-stu-id="77edf-104">These entities are known as *securables*.</span></span> <span data-ttu-id="77edf-105">最主要的安全对象是服务器和数据库，但可以在更细化的级别设置各种权限。</span><span class="sxs-lookup"><span data-stu-id="77edf-105">The most prominent securables are servers and databases, but discrete permissions can be set at a much finer level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="77edf-106">通过验证主体是否已被授予适当权限来控制主体对安全对象的操作。</span><span class="sxs-lookup"><span data-stu-id="77edf-106">regulates the actions of principals on securables by verifying that they have been granted appropriate permissions.</span></span>

 <span data-ttu-id="77edf-107">下图显示了 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 权限层次结构之间的关系。</span><span class="sxs-lookup"><span data-stu-id="77edf-107">The following illustration shows the relationships among the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions hierarchies.</span></span>

 <span data-ttu-id="77edf-108">![数据库引擎权限层次结构图](../../database-engine/media/wj-security-layers.gif "数据库引擎权限层次结构图")</span><span class="sxs-lookup"><span data-stu-id="77edf-108">![Diagram of Database Engine permissions hierarchies](../../database-engine/media/wj-security-layers.gif "Diagram of Database Engine permissions hierarchies")</span></span>

## <a name="chart-of-sql-server-permissions"></a><span data-ttu-id="77edf-109">SQL Server 权限图表</span><span class="sxs-lookup"><span data-stu-id="77edf-109">Chart of SQL Server Permissions</span></span>
 <span data-ttu-id="77edf-110">若要获取 pdf 格式的所有 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 权限的海报大小的图表，请参阅 [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf)。</span><span class="sxs-lookup"><span data-stu-id="77edf-110">For a poster sized chart of all [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions in pdf format, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>

## <a name="working-with-permissions"></a><span data-ttu-id="77edf-111">使用权限</span><span class="sxs-lookup"><span data-stu-id="77edf-111">Working with Permissions</span></span>
 <span data-ttu-id="77edf-112">可以使用常见的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询 GRANT、DENY 和 REVOKE 来操作权限。</span><span class="sxs-lookup"><span data-stu-id="77edf-112">Permissions can be manipulated with the familiar [!INCLUDE[tsql](../../includes/tsql-md.md)] queries GRANT, DENY, and REVOKE.</span></span> <span data-ttu-id="77edf-113">有关权限的信息，可以在 [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) 和 [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) 目录视图中看到。</span><span class="sxs-lookup"><span data-stu-id="77edf-113">Information about permissions is visible in the [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) and [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) catalog views.</span></span> <span data-ttu-id="77edf-114">也可以使用内置函数来查询权限信息。</span><span class="sxs-lookup"><span data-stu-id="77edf-114">There is also support for querying permissions information by using built-in functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="77edf-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77edf-115">See Also</span></span>
 <span data-ttu-id="77edf-116">[保护 SQL Server](securing-sql-server.md) [权限 &#40;数据库引擎&#41;](permissions-database-engine.md) [安全对象](securables.md)[主体 &#40;数据库引擎&#41;](authentication-access/principals-database-engine.md) [授予 &#40;transact-sql&#41;](/sql/t-sql/statements/grant-transact-sql) [REVOKE &#40;transact-sql&#41;](/sql/t-sql/statements/revoke-transact-sql) [DENY &#40;transact-sql&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME](/sql/t-sql/functions/has-perms-by-name-transact-sql) [&#40;&#41;fn_builtin_permissions](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) &#40;transact-sql&#41;sys. server_permissions &#40;&#41;database_permissions transact-sql &#40;[的](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) [&#41;。](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="77edf-116">[Securing SQL Server](securing-sql-server.md) [Permissions &#40;Database Engine&#41;](permissions-database-engine.md) [Securables](securables.md) [Principals &#40;Database Engine&#41;](authentication-access/principals-database-engine.md) [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql) [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) [sys.server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span></span>


