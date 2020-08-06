---
title: 删除修改系统对象的语句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694242"
---
# <a name="remove-statements-that-modify-system-objects"></a><span data-ttu-id="ba1a4-102">删除用于修改系统对象的语句</span><span class="sxs-lookup"><span data-stu-id="ba1a4-102">Remove statements that modify system objects</span></span>
  <span data-ttu-id="ba1a4-103">升级顾问检测到了用于更新系统目录的语句。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-103">Upgrade Advisor detected statements that update the system catalog.</span></span> <span data-ttu-id="ba1a4-104">不允许直接更新系统目录。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-104">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="ba1a4-105">请修改您的 SQL 脚本，使用正式且有记录的 API。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-105">Modify your SQL scripts to use official and documented APIs.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ba1a4-106">组件</span><span class="sxs-lookup"><span data-stu-id="ba1a4-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ba1a4-107">说明</span><span class="sxs-lookup"><span data-stu-id="ba1a4-107">Description</span></span>  
 <span data-ttu-id="ba1a4-108">不允许直接更新系统目录。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-108">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="ba1a4-109">尝试这样做将生成以下错误：</span><span class="sxs-lookup"><span data-stu-id="ba1a4-109">Any attempt to do so will generate the following error:</span></span>  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a><span data-ttu-id="ba1a4-110">纠正措施</span><span class="sxs-lookup"><span data-stu-id="ba1a4-110">Corrective Action</span></span>  
 <span data-ttu-id="ba1a4-111">请修改您的 SQL 脚本，使用正式且有记录的 API。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-111">Modify your SQL scripts to use official and documented APIs.</span></span> <span data-ttu-id="ba1a4-112">例如，使用 ALTER DATABASE *database_name*设置紧急情况，而不是对**sysdatabases**系统表运行 UPDATE 语句。</span><span class="sxs-lookup"><span data-stu-id="ba1a4-112">For example, use ALTER DATABASE *database_name* SET EMERGENCY instead of running an UPDATE statement on the **sysdatabases** system table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1a4-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba1a4-113">See Also</span></span>  
 <span data-ttu-id="ba1a4-114">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ba1a4-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ba1a4-115">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="ba1a4-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
