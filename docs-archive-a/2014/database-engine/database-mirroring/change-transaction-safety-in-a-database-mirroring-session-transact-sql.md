---
title: 更改数据库镜像会话中的事务安全 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579776"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="2ae21-102">更改数据库镜像会话中的事务安全 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2ae21-102">Change Transaction Safety in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="2ae21-103">事务安全是控制会话运行模式的属性。</span><span class="sxs-lookup"><span data-stu-id="2ae21-103">Transaction safety is the attribute that controls the operating mode of the session.</span></span> <span data-ttu-id="2ae21-104">但是，数据库所有者可以随时更改事务安全。</span><span class="sxs-lookup"><span data-stu-id="2ae21-104">At any time, however, the database owner can change the transaction safety.</span></span> <span data-ttu-id="2ae21-105">默认情况下，事务安全级别的设置为 FULL（同步运行模式）。</span><span class="sxs-lookup"><span data-stu-id="2ae21-105">By default, the level of transaction safety is set to FULL (synchronous operating mode).</span></span>  
  
 <span data-ttu-id="2ae21-106">关闭事务安全可将会话切换到异步运行模式，该模式可使性能达到最佳。</span><span class="sxs-lookup"><span data-stu-id="2ae21-106">Turning off transaction safety shifts the session into asynchronous operating mode, which maximizes performance.</span></span> <span data-ttu-id="2ae21-107">主体不可用时镜像将停止，但它可以作为备用使用（故障转移需要使用可能会丢失数据的强制服务）。</span><span class="sxs-lookup"><span data-stu-id="2ae21-107">If the principal becomes unavailable, the mirror stops but is available as a warm standby (failover requires forcing service with possible data loss).</span></span>  
  
### <a name="to-turn-on-transaction-safety"></a><span data-ttu-id="2ae21-108">打开事务安全</span><span class="sxs-lookup"><span data-stu-id="2ae21-108">To turn on transaction safety</span></span>  
  
1.  <span data-ttu-id="2ae21-109">连接到主体服务器。</span><span class="sxs-lookup"><span data-stu-id="2ae21-109">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="2ae21-110">发出以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="2ae21-110">Issue the following Transact-SQL statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     <span data-ttu-id="2ae21-111">其中，\<database> 为镜像数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="2ae21-111">where *\<database>* is the name of the mirrored database.</span></span>  
  
### <a name="to-turn-off-transaction-safety"></a><span data-ttu-id="2ae21-112">关闭事务安全</span><span class="sxs-lookup"><span data-stu-id="2ae21-112">To turn off transaction safety</span></span>  
  
1.  <span data-ttu-id="2ae21-113">连接到主体服务器。</span><span class="sxs-lookup"><span data-stu-id="2ae21-113">Connect to the principal server.</span></span>  
  
2.  <span data-ttu-id="2ae21-114">发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="2ae21-114">Issue the following statement:</span></span>  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     <span data-ttu-id="2ae21-115">其中，\<database> 是镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="2ae21-115">where *\<database>* is the mirrored database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae21-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ae21-116">See Also</span></span>  
 <span data-ttu-id="2ae21-117">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="2ae21-117">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 [<span data-ttu-id="2ae21-118">数据库镜像运行模式</span><span class="sxs-lookup"><span data-stu-id="2ae21-118">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
