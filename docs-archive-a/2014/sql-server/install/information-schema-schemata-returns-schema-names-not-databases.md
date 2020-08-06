---
title: INFORMATION_SCHEMA。架构返回数据库中的架构名称，而不是实例中的数据库 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cb2a34a59bf6257c188210fc7bf2aeacb70f6b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590527"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a><span data-ttu-id="9e085-102">INFORMATION_SCHEMA.SCHEMATA 返回数据库中的架构名称，而不是实例中的数据库</span><span class="sxs-lookup"><span data-stu-id="9e085-102">INFORMATION_SCHEMA.SCHEMATA returns schema names in a database, not databases in an instance</span></span>
  <span data-ttu-id="9e085-103">升级顾问检测到了引用 INFORMATION_SCHEMA.SCHEMATA 视图的语句。</span><span class="sxs-lookup"><span data-stu-id="9e085-103">Upgrade Advisor detected statements that reference the INFORMATION_SCHEMA.SCHEMATA view.</span></span> <span data-ttu-id="9e085-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本中，此视图返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="9e085-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e085-105">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本中，该视图返回数据库中的所有架构。</span><span class="sxs-lookup"><span data-stu-id="9e085-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, the view returns all schemas in a database.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9e085-106">组件</span><span class="sxs-lookup"><span data-stu-id="9e085-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="9e085-107">说明</span><span class="sxs-lookup"><span data-stu-id="9e085-107">Description</span></span>  
 <span data-ttu-id="9e085-108">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本中，INFORMATION_SCHEMA.SCHEMATA 视图返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="9e085-108">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the INFORMATION_SCHEMA.SCHEMATA view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e085-109">现在，该视图返回数据库中的所有架构，这是符合 SQL 标准的。</span><span class="sxs-lookup"><span data-stu-id="9e085-109">Now, the view returns all schemas in a database, which complies with the SQL Standard.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="9e085-110">纠正措施</span><span class="sxs-lookup"><span data-stu-id="9e085-110">Corrective Action</span></span>  
 <span data-ttu-id="9e085-111">修改应用程序以引用**sys.databases**目录视图以返回实例中的所有数据库 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9e085-111">Modify your application to reference the **sys.databases** catalog view to return all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e085-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e085-112">See Also</span></span>  
 <span data-ttu-id="9e085-113">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9e085-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9e085-114">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="9e085-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
