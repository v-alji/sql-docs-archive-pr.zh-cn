---
title: Sp_helptrigger 的输出中的新列可能会影响应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590512"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a><span data-ttu-id="065be-102">sp_helptrigger 输出中的新列可能会影响应用程序</span><span class="sxs-lookup"><span data-stu-id="065be-102">New column in output of sp_helptrigger may impact applications</span></span>
  <span data-ttu-id="065be-103">trigger_schemaias sp_helptrigger 系统存储过程返回的结果集中的最后一列。</span><span class="sxs-lookup"><span data-stu-id="065be-103">trigger_schemaias the last column in the result set returned by the sp_helptrigger system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="065be-104">若要获取有关针对特定表定义的触发器的信息，请查询 sys.triggers目录视图。</span><span class="sxs-lookup"><span data-stu-id="065be-104">To obtain information about triggers defined on a particular table, query the sys.triggers catalog view.</span></span>  
  
## <a name="component"></a><span data-ttu-id="065be-105">组件</span><span class="sxs-lookup"><span data-stu-id="065be-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="065be-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="065be-106">Corrective Action</span></span>  
 <span data-ttu-id="065be-107">检查应用程序中是否使用了 sp_helptrigger。</span><span class="sxs-lookup"><span data-stu-id="065be-107">Review the use of sp_helptrigger in applications.</span></span> <span data-ttu-id="065be-108">可能需要修改应用程序以容纳附加列。</span><span class="sxs-lookup"><span data-stu-id="065be-108">You may need to modify your applications to accommodate the additional column.</span></span> <span data-ttu-id="065be-109">另外，还可以改用 sys.triggers 目录视图。</span><span class="sxs-lookup"><span data-stu-id="065be-109">Alternatively, you can use the sys.triggers catalog view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065be-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="065be-110">See Also</span></span>  
 <span data-ttu-id="065be-111">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="065be-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="065be-112">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="065be-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
