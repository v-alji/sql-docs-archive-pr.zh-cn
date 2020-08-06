---
title: 在数据源视图中添加或删除表或视图 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
author: minewiskan
ms.author: owend
ms.openlocfilehash: da1bc2b1ac0af7576cfe3c3593b451f78d6a9fae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590955"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a><span data-ttu-id="1deb5-102">在数据源视图中添加或删除表或视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1deb5-102">Adding or Removing Tables or Views in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="1deb5-103">在您在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中创建了数据源视图 (DSV) 后，可以通过添加或删除表和列，包括来自其他数据源的表和列，在数据源视图设计器中修改数据源视图。</span><span class="sxs-lookup"><span data-stu-id="1deb5-103">After you have created a data source view (DSV) in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can modify it in Data Source View Designer by adding or removing tables and columns, including tables and columns from another data source.</span></span>  
  
 <span data-ttu-id="1deb5-104">若要在数据源视图设计器中打开该 DSV，请在解决方案资源管理器中双击该 DSV。</span><span class="sxs-lookup"><span data-stu-id="1deb5-104">To open the DSV in Data Source View Designer, you double-click the DSV in Solution Explorer.</span></span> <span data-ttu-id="1deb5-105">一旦打开该 DSV 后，可使用按钮栏或菜单上的“添加/删除表”\*\*\*\* 命令来修改或扩展该 DSV。</span><span class="sxs-lookup"><span data-stu-id="1deb5-105">Once you open the DSV, you can use the **Add/Remove Tables** command on the button bar or menu to modify or extend the DSV.</span></span> <span data-ttu-id="1deb5-106">您还可以在关系图中使用这些对象。</span><span class="sxs-lookup"><span data-stu-id="1deb5-106">You can also work with the objects in the diagram.</span></span> <span data-ttu-id="1deb5-107">例如，您可以选择某一对象，然后使用键盘上的 Delete 键删除对象。</span><span class="sxs-lookup"><span data-stu-id="1deb5-107">For example, you can select an object and then use the Delete key on your keyboard to remove an object.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1deb5-108">删除表时要格外小心。</span><span class="sxs-lookup"><span data-stu-id="1deb5-108">Use caution when removing a table.</span></span> <span data-ttu-id="1deb5-109">删除表将从 DSV 中删除所有关联列和关系，并且将使绑定到该表的所有对象失效。</span><span class="sxs-lookup"><span data-stu-id="1deb5-109">Removing a table deletes all the associated columns and relationships from the DSV and invalidates all objects bound to that table.</span></span>  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a><span data-ttu-id="1deb5-110">选择要添加或删除的表或视图</span><span class="sxs-lookup"><span data-stu-id="1deb5-110">Selecting Tables or Views to Add or Remove</span></span>  
 <span data-ttu-id="1deb5-111">使用“添加/删除表”\*\*\*\* 对话框，可以在“可用对象”\*\*\*\* 和“包含的对象”\*\*\*\* 列表之间移动表或视图。</span><span class="sxs-lookup"><span data-stu-id="1deb5-111">Using the **Add/Remove Tables** dialog box, you can move tables or views between the **Available objects** and **Included objects** lists.</span></span> <span data-ttu-id="1deb5-112">**“可用对象”** 列表最初包含主数据源中还没有位于数据源视图中的所有表或视图。</span><span class="sxs-lookup"><span data-stu-id="1deb5-112">The **Available objects** list initially includes any tables or views in the primary data source that are not already in the data source view.</span></span> <span data-ttu-id="1deb5-113">如果主数据源支持 `OPENROWSET` 函数，则还可以从项目或数据库中的其他数据源添加表或视图。</span><span class="sxs-lookup"><span data-stu-id="1deb5-113">If the primary data source supports the `OPENROWSET` function, you can also add tables or views from other data sources in the project or database.</span></span>  
  
 <span data-ttu-id="1deb5-114">在将表添加到 DSV 中或者从 DSV 中删除表时，还会将该表添加到 DSV 的当前选定关系图中或从中删除。</span><span class="sxs-lookup"><span data-stu-id="1deb5-114">Adding or removing a table to the DSV also adds or removes the table to the currently selected diagram in the DSV.</span></span> <span data-ttu-id="1deb5-115">有关关系图的详细信息，请参阅 [使用数据源视图设计器中的关系图 (Analysis Services)](work-with-diagrams-in-data-source-view-designer-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1deb5-115">For more information on diagrams, see [Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).</span></span>  
  
 <span data-ttu-id="1deb5-116">在“添加/删除表”\*\*\*\* 对话框中将表移至“包含的对象”\*\*\*\* 列表后，可以添加所有相关表。</span><span class="sxs-lookup"><span data-stu-id="1deb5-116">After you move a table to the **Included objects** list in the **Add/Remove Tables** dialog box, you can add all related tables.</span></span> <span data-ttu-id="1deb5-117">如果数据源中存在外键约束，此操作将根据该外键约束添加表。</span><span class="sxs-lookup"><span data-stu-id="1deb5-117">This operation adds tables according to foreign key constraints in the data source, if such constraints exist.</span></span> <span data-ttu-id="1deb5-118">如果不存在外键约束，则可以使用数据源视图的 `NameMatchingCriteria` 属性通过为表中匹配的列名指定生成适当关系的条件来确定关系。</span><span class="sxs-lookup"><span data-stu-id="1deb5-118">If foreign key constraints do not exist, you can use the `NameMatchingCriteria` property of the data source view to determine relationships by specifying a criterion for matching column names in tables to generate likely relationships.</span></span> <span data-ttu-id="1deb5-119">如果为 `NameMatchingCriteria` 数据源视图指定了属性，则单击 "**添加相关表**" 以从数据源中添加具有匹配列名称的表。</span><span class="sxs-lookup"><span data-stu-id="1deb5-119">If the `NameMatchingCriteria`property is specified for the data source view, click **Add Related Tables** to add tables from the data source that have matching column names.</span></span> <span data-ttu-id="1deb5-120">有关设置属性的详细信息 `NameMatchingCriteria` ，请参阅[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="1deb5-120">For more information about setting the `NameMatchingCriteria` property, see [Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1deb5-121">向数据源视图中添加对象或从中删除对象不会影响基础数据源。</span><span class="sxs-lookup"><span data-stu-id="1deb5-121">Adding or removing objects in a data source view does not affect the underlying data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1deb5-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1deb5-122">See Also</span></span>  
 <span data-ttu-id="1deb5-123">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="1deb5-123">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="1deb5-124">使用数据源视图设计器中的关系图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1deb5-124">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
