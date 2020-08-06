---
title: 验证升级过程中所有文件组均可写 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694212"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a><span data-ttu-id="499d8-102">确保升级过程中所有文件组均可写</span><span class="sxs-lookup"><span data-stu-id="499d8-102">Verify all filegroups are writeable during the upgrade process</span></span>
  <span data-ttu-id="499d8-103">升级顾问检测到其中包含一个或多个只读文件组的数据库。</span><span class="sxs-lookup"><span data-stu-id="499d8-103">Upgrade Advisor detected a database that has one or more read-only filegroups.</span></span> <span data-ttu-id="499d8-104">必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的所有数据库的文件组都设置为 READ_WRITE 后，才能升级。</span><span class="sxs-lookup"><span data-stu-id="499d8-104">All databases in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have filegroups set to READ_WRITE before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="499d8-105">组件</span><span class="sxs-lookup"><span data-stu-id="499d8-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="499d8-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="499d8-106">Corrective Action</span></span>  
 <span data-ttu-id="499d8-107">使用 ALTER DATABASE 将文件组设置为 READ_WRITE。</span><span class="sxs-lookup"><span data-stu-id="499d8-107">Use ALTER DATABASE to set the filegroup to READ_WRITE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499d8-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="499d8-108">See Also</span></span>  
 <span data-ttu-id="499d8-109">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="499d8-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="499d8-110">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="499d8-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
