---
title: 在90或更高版本的兼容模式中，包含 TOP 的视图不支持 WITH CHECK OPTION |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586083"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a><span data-ttu-id="c1331-102">在 90 或更高的兼容模式下，包含 TOP 的视图不支持 WITH CHECK OPTION</span><span class="sxs-lookup"><span data-stu-id="c1331-102">WITH CHECK OPTION is not supported in views that contain TOP in 90 or later compatibility modes</span></span>
  <span data-ttu-id="c1331-103">升级顾问检测到了使用 WITH CHECK OPTION 的视图，并在该视图或者被引用视图的 SELECT 语句中检测到了 TOP 子句。</span><span class="sxs-lookup"><span data-stu-id="c1331-103">Upgrade Advisor detected a view that uses the WITH CHECK OPTION and a TOP clause in the SELECT statement of the view or in a referenced view.</span></span> <span data-ttu-id="c1331-104">当数据库兼容模式设置为 80 或更低时，用此方式定义的视图会错误地允许通过视图修改数据，从而产生不准确的结果。</span><span class="sxs-lookup"><span data-stu-id="c1331-104">Views defined this way incorrectly allow data to be modified through the view and may produce inaccurate results when the database compatibility mode is set to 80 and earlier.</span></span> <span data-ttu-id="c1331-105">如果使用 WITH CHECK OPTION 的视图或者被引用视图使用了 TOP 子句，且数据库兼容模式设置为 90 或更高，则无法通过该视图插入或更新数据。</span><span class="sxs-lookup"><span data-stu-id="c1331-105">Data cannot be inserted or updated through a view that uses WITH CHECK OPTION when the view or a referenced view uses the TOP clause and the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c1331-106">组件</span><span class="sxs-lookup"><span data-stu-id="c1331-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="c1331-107">纠正措施</span><span class="sxs-lookup"><span data-stu-id="c1331-107">Corrective Action</span></span>  
 <span data-ttu-id="c1331-108">升级时，用户数据库将保持其兼容模式。</span><span class="sxs-lookup"><span data-stu-id="c1331-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="c1331-109">如果需要通过使用 WITH CHECK OPTION 和 TOP 的视图来修改数据，请在将数据库兼容模式更改为 100 或更高前修改这类视图。</span><span class="sxs-lookup"><span data-stu-id="c1331-109">Before you change the database compatibility mode to 100 or later, modify views that use both WITH CHECK OPTION and TOP if data modification through the view is required.</span></span> <span data-ttu-id="c1331-110">有关详细信息，请参阅[&#40;transact-sql&#41;sp_dbcmptlevel ](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c1331-110">For more information, see [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1331-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1331-111">See Also</span></span>  
 <span data-ttu-id="c1331-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c1331-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c1331-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="c1331-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
