---
title: 游标事务隔离级别 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: rothja
ms.author: jroth
ms.openlocfilehash: 30f3dc8a9136a7cbe1d5897cb0bcc9fff8c35ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692400"
---
# <a name="cursor-transaction-isolation-level"></a><span data-ttu-id="e3a2a-102">游标事务隔离级别</span><span class="sxs-lookup"><span data-stu-id="e3a2a-102">Cursor Transaction Isolation Level</span></span>
  <span data-ttu-id="e3a2a-103">游标的完整锁定行为基于由客户端设置的并发属性和事务隔离级别之间的交互。</span><span class="sxs-lookup"><span data-stu-id="e3a2a-103">The complete locking behavior of cursors is based on an interaction between concurrency attributes and the transaction isolation level set by the client.</span></span> <span data-ttu-id="e3a2a-104">ODBC 客户端使用[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION 或 SQL_COPT_SS_TXN_ISOLATION 属性设置事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="e3a2a-104">ODBC clients set the transaction isolation level using the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION or SQL_COPT_SS_TXN_ISOLATION attributes.</span></span> <span data-ttu-id="e3a2a-105">通过将并发和事务隔离级别选项的锁定行为进行组合，可以确定特定游标环境的锁定行为。</span><span class="sxs-lookup"><span data-stu-id="e3a2a-105">The locking behavior of a specific cursor environment is determined by combining the locking behaviors of the concurrency and transaction isolation level options.</span></span>  
  
 <span data-ttu-id="e3a2a-106">Native Client ODBC 驱动程序支持以下游标事务隔离级别 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="e3a2a-106">The following cursor transaction isolation levels are supported by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
-   <span data-ttu-id="e3a2a-107">已提交读 (SQL_TXN_READ_COMMITTED)</span><span class="sxs-lookup"><span data-stu-id="e3a2a-107">Read committed (SQL_TXN_READ_COMMITTED)</span></span>  
  
-   <span data-ttu-id="e3a2a-108">未提交读 (SQL_TXN_READ_UNCOMMITTED)</span><span class="sxs-lookup"><span data-stu-id="e3a2a-108">Read uncommitted (SQL_TXN_READ_UNCOMMITTED)</span></span>  
  
-   <span data-ttu-id="e3a2a-109">可重复读 (SQL_TXN_REPEATABLE_READ)</span><span class="sxs-lookup"><span data-stu-id="e3a2a-109">Repeatable read (SQL_TXN_REPEATABLE_READ)</span></span>  
  
-   <span data-ttu-id="e3a2a-110">可序列化 (SQL_TXN_SERIALIZABLE)</span><span class="sxs-lookup"><span data-stu-id="e3a2a-110">Serializable (SQL_TXN_SERIALIZABLE)</span></span>  
  
-   <span data-ttu-id="e3a2a-111">快照 (SQL_TXN_SS_SNAPSHOT)</span><span class="sxs-lookup"><span data-stu-id="e3a2a-111">Snapshot (SQL_TXN_SS_SNAPSHOT)</span></span>  
  
 <span data-ttu-id="e3a2a-112">请注意，ODBC API 指定了其他事务隔离级别，但不支持这些级别 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e3a2a-112">Note that the ODBC API specifies additional transaction isolation levels, but these are not supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a2a-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3a2a-113">See Also</span></span>  
 [<span data-ttu-id="e3a2a-114">游标属性</span><span class="sxs-lookup"><span data-stu-id="e3a2a-114">Cursor Properties</span></span>](cursor-properties.md)  
  
  
