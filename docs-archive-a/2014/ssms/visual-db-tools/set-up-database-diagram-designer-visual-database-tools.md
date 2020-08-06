---
title: 设置数据库关系图设计器 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d59fa2ed197a410de6b68e388e76d2bf21c334d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690997"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a><span data-ttu-id="eb2bd-102">设置数据库关系图设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="eb2bd-102">Set Up Database Diagram Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="eb2bd-103">若要使用数据库关系图设计器，必须首先由 **db_owner** 角色的成员对其进行设置，以控制对关系图的访问。</span><span class="sxs-lookup"><span data-stu-id="eb2bd-103">To use Database Diagram Designer, it must first be set up by a member of the **db_owner** role to control access to diagrams.</span></span>  
  
### <a name="to-set-up-database-diagramming"></a><span data-ttu-id="eb2bd-104">设置数据库关系图创建功能</span><span class="sxs-lookup"><span data-stu-id="eb2bd-104">To set up database diagramming</span></span>  
  
1.  <span data-ttu-id="eb2bd-105">在对象资源管理器中，展开相应的数据库节点。</span><span class="sxs-lookup"><span data-stu-id="eb2bd-105">From Object Explorer, expand a database node.</span></span>  
  
2.  <span data-ttu-id="eb2bd-106">展开该数据库连接下的“数据库关系图”节点。</span><span class="sxs-lookup"><span data-stu-id="eb2bd-106">Expand the Database Diagrams node under the database connection.</span></span>  
  
3.  <span data-ttu-id="eb2bd-107">如果希望设置数据库关系图，请在出现提示时选择“是”  。</span><span class="sxs-lookup"><span data-stu-id="eb2bd-107">Select **Yes** when prompted if you want to set up database diagramming.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb2bd-108">这将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库上创建数据库关系图表、系统存储过程和一个系统函数。</span><span class="sxs-lookup"><span data-stu-id="eb2bd-108">This will create the database diagram table, system stored procedures, and a system function on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="eb2bd-109">Visual Studio 将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上创建以下对象：</span><span class="sxs-lookup"><span data-stu-id="eb2bd-109">Visual Studio will create the following objects on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="eb2bd-110">sysdiagrams 表</span><span class="sxs-lookup"><span data-stu-id="eb2bd-110">sysdiagrams table</span></span>  
  
    2.  <span data-ttu-id="eb2bd-111">sp_alterdiagram 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-111">sp_alterdiagram stored procedure</span></span>  
  
    3.  <span data-ttu-id="eb2bd-112">sp_creatediagram 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-112">sp_creatediagram stored procedure</span></span>  
  
    4.  <span data-ttu-id="eb2bd-113">sp_dropdiagram 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-113">sp_dropdiagram stored procedure</span></span>  
  
    5.  <span data-ttu-id="eb2bd-114">sp_renamediagram 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-114">sp_renamediagram stored procedure</span></span>  
  
    6.  <span data-ttu-id="eb2bd-115">fn_diagramobjects 函数</span><span class="sxs-lookup"><span data-stu-id="eb2bd-115">fn_diagramobjects function</span></span>  
  
    7.  <span data-ttu-id="eb2bd-116">sp_helpdiagrams 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-116">sp_helpdiagrams stored procedure</span></span>  
  
    8.  <span data-ttu-id="eb2bd-117">sp_helpdiagramsdefinition 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-117">sp_helpdiagramsdefinition stored procedure</span></span>  
  
    9. <span data-ttu-id="eb2bd-118">sp_upgraddiagrams 存储过程</span><span class="sxs-lookup"><span data-stu-id="eb2bd-118">sp_upgraddiagrams stored procedure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2bd-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb2bd-119">See Also</span></span>  
 <span data-ttu-id="eb2bd-120">[了解数据库关系图所有权 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="eb2bd-120">[Understand Database Diagram Ownership &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="eb2bd-121">[从早期版本升级数据库关系图 &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="eb2bd-121">[Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="eb2bd-122">ALTER AUTHORIZATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="eb2bd-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
