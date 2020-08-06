---
title: 只读数据库无法升级 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ba48ed2bd80961a4949dc13f04fed0637ecc27ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589401"
---
# <a name="read-only-databases-cannot-be-upgraded"></a><span data-ttu-id="d029b-102">无法升级只读数据库</span><span class="sxs-lookup"><span data-stu-id="d029b-102">Read-only databases cannot be upgraded</span></span>
  <span data-ttu-id="d029b-103">升级顾问已确定此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的某些数据库无法升级。</span><span class="sxs-lookup"><span data-stu-id="d029b-103">Upgrade Advisor has determined that some databases on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be upgraded.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d029b-104">组件</span><span class="sxs-lookup"><span data-stu-id="d029b-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d029b-105">说明</span><span class="sxs-lookup"><span data-stu-id="d029b-105">Description</span></span>  
 <span data-ttu-id="d029b-106">已检测到一个只读数据库。</span><span class="sxs-lookup"><span data-stu-id="d029b-106">A read-only database has been detected.</span></span> <span data-ttu-id="d029b-107">若要升级此数据库，安装程序必须能写入此数据库。</span><span class="sxs-lookup"><span data-stu-id="d029b-107">To upgrade the database, Setup must be able to write to the database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d029b-108">纠正措施</span><span class="sxs-lookup"><span data-stu-id="d029b-108">Corrective Action</span></span>  
 <span data-ttu-id="d029b-109">如果没有人在使用数据库，请使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 企业管理器、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或 ALTER database 语句将数据库更改为读写数据库。</span><span class="sxs-lookup"><span data-stu-id="d029b-109">When no one is using the database, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or the ALTER DATABASE statement to change the database to read-write.</span></span> <span data-ttu-id="d029b-110">下面的语句可将数据库更改为可读写状态。</span><span class="sxs-lookup"><span data-stu-id="d029b-110">The following statement changes the database to read-write.</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 <span data-ttu-id="d029b-111">有关 ALTER DATABASE 语句的详细信息，请参阅 [!INCLUDE[tsql](../../includes/tsql-md.md)] 联机丛书中的“ALTER DATABASE ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])”主题。</span><span class="sxs-lookup"><span data-stu-id="d029b-111">For more information about the ALTER DATABASE statement, see the "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d029b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d029b-112">See Also</span></span>  
 <span data-ttu-id="d029b-113">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d029b-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d029b-114">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="d029b-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
