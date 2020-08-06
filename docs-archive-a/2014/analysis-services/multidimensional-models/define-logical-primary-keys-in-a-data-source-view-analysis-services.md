---
title: 在数据源视图中定义逻辑主键 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25092e5d754381c572dcdbfc03e5ee0f29c1df24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587086"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a><span data-ttu-id="d5349-102">在数据源视图中定义逻辑主键 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="d5349-102">Define Logical Primary Keys in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="d5349-103">数据源视图向导和数据源视图设计器自动根据基础数据库表为添加到数据源视图的表定义主键。</span><span class="sxs-lookup"><span data-stu-id="d5349-103">The Data Source View Wizard and Data Source View Designer automatically define a primary key for a table that is added to a data source view based on underlying database table.</span></span>  
  
 <span data-ttu-id="d5349-104">有时，您可能需要在数据源视图中手动定义主键。</span><span class="sxs-lookup"><span data-stu-id="d5349-104">Occasionally, you may need to manually define a primary key in the data source view.</span></span> <span data-ttu-id="d5349-105">例如，出于性能或设计方面的原因，数据源中的表可能没有显式定义的主键列。</span><span class="sxs-lookup"><span data-stu-id="d5349-105">For example, for performance or design reasons, tables in a data source may not have explicitly defined primary key columns.</span></span> <span data-ttu-id="d5349-106">命名查询和视图也可能遗漏表的主键列。</span><span class="sxs-lookup"><span data-stu-id="d5349-106">Named queries and views may also omit the primary key column for a table.</span></span> <span data-ttu-id="d5349-107">如果表、视图或命名查询未定义物理主键，则可以在数据源视图设计器中为表、视图或命名查询手动定义一个逻辑主键。</span><span class="sxs-lookup"><span data-stu-id="d5349-107">If a table, view, or named query does not have a physical primary key defined, you can manually define a logical primary key on the table, view or named query in Data Source View Designer.</span></span>  
  
## <a name="set-a-logical-primary-key"></a><span data-ttu-id="d5349-108">设置逻辑主键</span><span class="sxs-lookup"><span data-stu-id="d5349-108">Set a Logical Primary Key</span></span>  
 <span data-ttu-id="d5349-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中，需要使用主键来唯一标识表中的记录，标识维度表中的键列，以及支持表、视图和命名查询之间的关系。</span><span class="sxs-lookup"><span data-stu-id="d5349-109">Primary keys are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to uniquely identify records in a table, identify key columns in dimension tables and to support relationships between tables, views and named queries.</span></span> <span data-ttu-id="d5349-110">使用这些关系，可以构造用于从基础数据源中检索数据和元数据的查询，还可以利用高级商业智能功能。</span><span class="sxs-lookup"><span data-stu-id="d5349-110">These relationships are used to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="d5349-111">任何列都可用于逻辑主键（包括命名计算）。</span><span class="sxs-lookup"><span data-stu-id="d5349-111">Any column can be used for the logical primary key, including a named calculation.</span></span> <span data-ttu-id="d5349-112">创建逻辑主键时，将在数据源视图中创建一个唯一约束并将其标记为主键约束。</span><span class="sxs-lookup"><span data-stu-id="d5349-112">When you create a logical primary key, a unique constraint is created in the data source view and marked as a primary key constraint.</span></span> <span data-ttu-id="d5349-113">在所选表中指定的任何其他现有逻辑主键都将被删除。</span><span class="sxs-lookup"><span data-stu-id="d5349-113">Any other existing logical primary key specified in the selected table is deleted.</span></span>  
  
1.  <span data-ttu-id="d5349-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开项目或连接到数据库，此项目或数据库包含要在其中设置逻辑主键的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="d5349-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to set a logical primary key.</span></span>  
  
2.  <span data-ttu-id="d5349-115">在解决方案资源管理器中，展开“数据源视图”\*\*\*\* 文件夹，然后双击数据源视图。</span><span class="sxs-lookup"><span data-stu-id="d5349-115">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
     <span data-ttu-id="d5349-116">若要查找表或视图，可以通过单击 "**数据源视图**" 菜单或右键单击 "**表**" 或 "**关系图**" 窗格的打开区域，使用 "**查找表**" 选项。</span><span class="sxs-lookup"><span data-stu-id="d5349-116">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View**  menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
3.  <span data-ttu-id="d5349-117">在“表”\*\*\*\* 或“关系图”\*\*\*\* 窗格中，右键单击要用于定义逻辑主键的一列或多列，再单击“设置逻辑主键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d5349-117">In either the **Tables** or the **Diagram** pane, right-click the column or columns that you want to use to define a logical primary key, and then click **Set Logical Primary Key**.</span></span>  
  
     <span data-ttu-id="d5349-118">设置逻辑主键的选项仅可用于没有主键的表。</span><span class="sxs-lookup"><span data-stu-id="d5349-118">The option to set a logical primary key is available only for tables that do not have a primary key.</span></span>  
  
     <span data-ttu-id="d5349-119">请注意，在设置该键后，键图标现在标识主键列。</span><span class="sxs-lookup"><span data-stu-id="d5349-119">Notice that after you set the key, a key icon now identifies the primary key columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5349-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5349-120">See Also</span></span>  
 <span data-ttu-id="d5349-121">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d5349-121">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d5349-122">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="d5349-122">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
