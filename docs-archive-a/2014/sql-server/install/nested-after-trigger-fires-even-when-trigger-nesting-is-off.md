---
title: 即使触发器嵌套处于关闭状态，嵌套的 AFTER 触发器也会激发 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f91c04e8d69880b451c1479e2907cd1910e8f9c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694246"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a><span data-ttu-id="4563d-102">即使触发器嵌套功能设置为 OFF，也会触发嵌套的 AFTER 触发器</span><span class="sxs-lookup"><span data-stu-id="4563d-102">Nested AFTER trigger fires even when trigger nesting is OFF</span></span>
  <span data-ttu-id="4563d-103">升级顾问检测到一个嵌套在一个或多个表中定义的 INSTEAD OF 触发器中的 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="4563d-103">Upgrade Advisor detected an AFTER trigger nested inside an INSTEAD OF trigger that is defined on one or more tables.</span></span> <span data-ttu-id="4563d-104">即使在 `nested triggers` 服务器配置选项设置为 0 时，也可能会激发嵌套 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="4563d-104">Nested AFTER triggers may fire even when the `nested triggers` server configuration option is set to 0.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4563d-105">组件</span><span class="sxs-lookup"><span data-stu-id="4563d-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4563d-106">说明</span><span class="sxs-lookup"><span data-stu-id="4563d-106">Description</span></span>  
 <span data-ttu-id="4563d-107">即使 `nested triggers` 服务器配置选项设置为 0，也会激发嵌套在 INSTEAD OF 触发器内的第一个 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="4563d-107">The first AFTER trigger nested inside an INSTEAD OF trigger fires even if the `nested triggers` server configuration option is set to 0.</span></span> <span data-ttu-id="4563d-108">但是，在此设置下，不会激发后续的 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="4563d-108">However, under this setting, subsequent AFTER triggers do not fire.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4563d-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="4563d-109">Corrective Action</span></span>  
 <span data-ttu-id="4563d-110">检查嵌套触发器的应用程序以确定当 `nested triggers` 服务器配置选项设置为 0 时，应用程序是否仍然遵循有关此新行为的业务规则，然后进行适当的修改。</span><span class="sxs-lookup"><span data-stu-id="4563d-110">Review your applications for nested triggers to determine whether the applications still comply with your business rules with regard to this new behavior when the `nested triggers` server configuration option is set to 0, and then make appropriate modifications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4563d-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4563d-111">See Also</span></span>  
 <span data-ttu-id="4563d-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4563d-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4563d-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="4563d-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
