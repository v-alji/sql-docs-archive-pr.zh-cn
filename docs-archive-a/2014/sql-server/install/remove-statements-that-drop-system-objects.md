---
title: 删除删除系统对象的语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577234"
---
# <a name="remove-statements-that-drop-system-objects"></a><span data-ttu-id="28ccf-102">删除用于去除系统对象的语句</span><span class="sxs-lookup"><span data-stu-id="28ccf-102">Remove statements that drop system objects</span></span>
  <span data-ttu-id="28ccf-103">升级顾问检测到用于删除系统对象的语句。</span><span class="sxs-lookup"><span data-stu-id="28ccf-103">Upgrade Advisor detected statements that drop system objects.</span></span> <span data-ttu-id="28ccf-104">系统对象（包括扩展存储过程）部署在只读**资源**数据库 (mssqlsystemresource.mdf) 中，无法删除。</span><span class="sxs-lookup"><span data-stu-id="28ccf-104">System objects, including extended stored procedures, are deployed in the read-only **resource** database (mssqlsystemresource) and cannot be dropped.</span></span> <span data-ttu-id="28ccf-105">请修改您的应用程序以撤消或拒绝针对系统对象的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="28ccf-105">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="28ccf-106">组件</span><span class="sxs-lookup"><span data-stu-id="28ccf-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="28ccf-107">说明</span><span class="sxs-lookup"><span data-stu-id="28ccf-107">Description</span></span>  
 <span data-ttu-id="28ccf-108">不能使用 DROP TABLE、DROP PROCEDURE 和**sp_dropextendedproc**等语句删除系统对象，因为这些对象部署在只读**资源**数据库中。</span><span class="sxs-lookup"><span data-stu-id="28ccf-108">Statements such as DROP TABLE, DROP PROCEDURE, and **sp_dropextendedproc** cannot be used to remove system objects, because these objects are deployed in the read-only **resource** database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="28ccf-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="28ccf-109">Corrective Action</span></span>  
 <span data-ttu-id="28ccf-110">从您的应用程序中删除所有试图删除系统对象的语句。</span><span class="sxs-lookup"><span data-stu-id="28ccf-110">Remove all statements that try to drop system objects from your applications.</span></span> <span data-ttu-id="28ccf-111">请修改您的应用程序以撤消或拒绝针对系统对象的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="28ccf-111">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span> <span data-ttu-id="28ccf-112">另外，也可以使用外围应用配置器 (SAC) 工具禁用这些对象中的部分对象。</span><span class="sxs-lookup"><span data-stu-id="28ccf-112">Alternatively, you can use the Surface Area Configuration (SAC) tool to disable some of these objects.</span></span> <span data-ttu-id="28ccf-113">例如，可以使用 SAC 工具禁用或启用**xp_cmdshell**扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="28ccf-113">For example, the **xp_cmdshell** extended stored procedure can be disabled or enabled using the SAC tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ccf-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28ccf-114">See Also</span></span>  
 <span data-ttu-id="28ccf-115">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="28ccf-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="28ccf-116">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="28ccf-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
