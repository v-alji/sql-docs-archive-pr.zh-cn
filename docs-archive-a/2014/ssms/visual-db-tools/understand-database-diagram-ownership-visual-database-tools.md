---
title: 了解数据库关系图所有权 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21d0f6f006328d8843bbbe12ee066a8564fb722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690994"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a><span data-ttu-id="3da14-102">了解数据库关系图所有权 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3da14-102">Understand Database Diagram Ownership (Visual Database Tools)</span></span>
  <span data-ttu-id="3da14-103">若要使用数据库关系图设计器，必须先由 db_owne 角色（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的一个角色）的成员对其进行设置，以控制对关系图的访问。</span><span class="sxs-lookup"><span data-stu-id="3da14-103">To use Database Diagram Designer it must first be set up by a member of the db_owner role (a role of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) to control access to diagrams.</span></span> <span data-ttu-id="3da14-104">每个关系图都有一个而且只有一个所有者，即创建该关系图的用户。</span><span class="sxs-lookup"><span data-stu-id="3da14-104">Each diagram has one and only one owner, the user who created it.</span></span> <span data-ttu-id="3da14-105">有关设置关系图的详细信息，请参阅[设置数据库关系图设计器 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3da14-105">For more information on setting up diagramming see [Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="3da14-106">关于关系图所有权，需要记住以下几点：</span><span class="sxs-lookup"><span data-stu-id="3da14-106">Some points to keep in mind about diagram ownership:</span></span>  
  
-   <span data-ttu-id="3da14-107">尽管任何可以访问数据库的用户都能够创建关系图，但在创建关系图之后，只有关系图的创建者和 db_owner 角色的所有成员才能查看该关系图。</span><span class="sxs-lookup"><span data-stu-id="3da14-107">Although any user with access to a database can create a diagram, once the diagram has been created, the only users who can see it are the diagram's creator and any member of the db_owner role.</span></span>  
  
-   <span data-ttu-id="3da14-108">关系图的所有权只能转让给 db_owner 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="3da14-108">Ownership of diagrams can only be transferred to members of the db_owner role.</span></span> <span data-ttu-id="3da14-109">只有当关系图的前一任拥有者已从数据库中移除时，才需要转让所有权。</span><span class="sxs-lookup"><span data-stu-id="3da14-109">This is only possible if the previous owner of the diagram has been removed from the database.</span></span>  
  
-   <span data-ttu-id="3da14-110">如果关系图的拥有者已从数据库中移除，该关系图将一直保留在数据库中，直到 db_owner 角色的成员试图打开该关系图。</span><span class="sxs-lookup"><span data-stu-id="3da14-110">If the owner of a diagram has been removed from the database, the diagram will remain in the database until a member of the db_owner role attempts to open it.</span></span> <span data-ttu-id="3da14-111">此时，db_owner 成员可以选择接管关系图的所有权。</span><span class="sxs-lookup"><span data-stu-id="3da14-111">At that point the db_owner member can choose to take over ownership of the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da14-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3da14-112">See Also</span></span>  
 <span data-ttu-id="3da14-113">[使用数据库关系图 &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3da14-113">[Work with Database Diagrams &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3da14-114">设置数据库关系图设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3da14-114">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
