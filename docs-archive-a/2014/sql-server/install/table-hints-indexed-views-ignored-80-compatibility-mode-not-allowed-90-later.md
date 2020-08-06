---
title: 在80兼容模式下将忽略索引视图定义中的表提示，在90模式或更高版本中不允许使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cf3cb2b06dc477d93c8fd42312b4835ded42afb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691495"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a><span data-ttu-id="a41f6-102">在 80 兼容模式中将忽略索引视图定义中的表提示且在 90 或更高的模式中不允许表提示</span><span class="sxs-lookup"><span data-stu-id="a41f6-102">Table hints in indexed view definitions are ignored in 80 compatibility mode and are not allowed in 90 mode or later</span></span>
  <span data-ttu-id="a41f6-103">在 90 或更高的兼容模式中，不允许索引视图定义中的表提示。</span><span class="sxs-lookup"><span data-stu-id="a41f6-103">Table hints in the definitions of indexed views are not permitted in the compatibility mode of 90 or later.</span></span> <span data-ttu-id="a41f6-104">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的以下主题：“设计索引视图”、“创建索引视图”和“查询提示 ([!INCLUDE[tsql](../../includes/tsql-md.md)])”。</span><span class="sxs-lookup"><span data-stu-id="a41f6-104">For more information, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online: "Designing Indexed Views," "Creating Indexed Views," and "Query Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])."</span></span>  
  
## <a name="component"></a><span data-ttu-id="a41f6-105">组件</span><span class="sxs-lookup"><span data-stu-id="a41f6-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="a41f6-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="a41f6-106">Corrective Action</span></span>  
 <span data-ttu-id="a41f6-107">必须从索引视图的定义中删除表提示。</span><span class="sxs-lookup"><span data-stu-id="a41f6-107">Table hints must be removed from the definitions of indexed views.</span></span> <span data-ttu-id="a41f6-108">不管使用哪种兼容模式，我们建议您测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="a41f6-108">Regardless of which compatibility mode is used, we recommend that you test the application.</span></span> <span data-ttu-id="a41f6-109">通过测试应用程序，可以确保在创建、更新和访问索引视图时（包括当索引视图与查询匹配时），程序按预期运行。</span><span class="sxs-lookup"><span data-stu-id="a41f6-109">By testing the application, you can make sure it performs as expected when indexed views are created, updated, and accessed, including when indexed views are matched to queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a41f6-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a41f6-110">See Also</span></span>  
 <span data-ttu-id="a41f6-111">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="a41f6-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="a41f6-112">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="a41f6-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
