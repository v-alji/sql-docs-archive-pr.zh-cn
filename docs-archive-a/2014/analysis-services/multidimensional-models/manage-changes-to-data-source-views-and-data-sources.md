---
title: 管理对数据源视图和数据源所做的更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f558ce6aaf9e57576d5773322352d33b81a3392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689058"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a><span data-ttu-id="e3335-102">管理对数据源视图和数据源所做的更改</span><span class="sxs-lookup"><span data-stu-id="e3335-102">Manage Changes to Data Source Views and Data Sources</span></span>
  <span data-ttu-id="e3335-103">在重新运行架构生成向导时，它重用初始生成使用的相同数据源和数据源视图。</span><span class="sxs-lookup"><span data-stu-id="e3335-103">When the Schema Generation Wizard is rerun, it reuses the same data source and data source view that it used for the original generation.</span></span> <span data-ttu-id="e3335-104">如果您添加数据源或数据源视图，则向导不会使用该数据源或数据源视图。</span><span class="sxs-lookup"><span data-stu-id="e3335-104">If you add a data source or a data source view, the wizard does not use it.</span></span> <span data-ttu-id="e3335-105">如果您在初始生成后删除原始数据源或数据源视图，则必须从头运行向导。</span><span class="sxs-lookup"><span data-stu-id="e3335-105">If you delete the original data source or data source view after the initial generation, you must run the wizard from the beginning.</span></span> <span data-ttu-id="e3335-106">向导中的所有先前设置也会被删除。</span><span class="sxs-lookup"><span data-stu-id="e3335-106">All previous settings in the wizard are also deleted.</span></span> <span data-ttu-id="e3335-107">下次运行架构生成向导时，基础数据库中任何绑定到已删除数据源或数据源视图的现有对象都被视为用户创建的对象。</span><span class="sxs-lookup"><span data-stu-id="e3335-107">Any existing objects in an underlying database that were bound to a deleted data source or data source view are treated as user-created objects the next time you run the Schema Generation Wizard.</span></span>  
  
 <span data-ttu-id="e3335-108">如果数据源视图并未反映基础数据库生成时的实际状态，则架构生成向导在生成主题区域数据库架构时可能会遇到错误。</span><span class="sxs-lookup"><span data-stu-id="e3335-108">If the data source view does not reflect the actual state of the underlying database at the time of generation, the Schema Generation Wizard may encounter errors when it generates the schema for the subject area database.</span></span> <span data-ttu-id="e3335-109">例如，如果数据源视图指定列的数据类型为 **int**，但该列的数据类型实际为 **string**，则架构生成向导会将外键的数据类型设置为 **INT** 以便与数据源视图相匹配，而在创建关系时会失败，因为实际类型为 **string**。</span><span class="sxs-lookup"><span data-stu-id="e3335-109">For example, if the data source view specifies that the data type for a column is **int**, but data type for the column is actually **string**, the Schema Generation Wizard sets the data type for the foreign key to **INT** to match the data source view and then fails when it creates the relationship because the actual type is **string**.</span></span>  
  
 <span data-ttu-id="e3335-110">另一方面，如果您将数据源连接字符串更改为先前生成的其他数据库，则不会生成任何错误。</span><span class="sxs-lookup"><span data-stu-id="e3335-110">On the other hand, if you change the data source connection string to a different database from the previous generation, no error is generated.</span></span> <span data-ttu-id="e3335-111">将会使用新的数据库，并且不会对先前数据库进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="e3335-111">The new database is used, and no change is made to the previous database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3335-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3335-112">See Also</span></span>  
 [<span data-ttu-id="e3335-113">了解增量生成</span><span class="sxs-lookup"><span data-stu-id="e3335-113">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)  
  
  
