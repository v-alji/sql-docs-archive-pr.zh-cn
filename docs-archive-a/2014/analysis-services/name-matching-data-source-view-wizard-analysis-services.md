---
title: " (数据源视图向导) 的名称匹配 (Analysis Services) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50cc46db7f582e0aea1570dadc956336ef8be074
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587042"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a><span data-ttu-id="e69e3-102">名称匹配（数据源视图向导）(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e69e3-102">Name Matching (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="e69e3-103">可以使用 **“名称匹配”** 页，针对为数据源视图选择的表以及架构中的其他表，选择用于检测它们之间可能存在的关系的条件。</span><span class="sxs-lookup"><span data-stu-id="e69e3-103">Use the **Name Matching** page to select the criterion to use for detecting possible relationships between the tables that you select for the data source view and the other tables in the schema.</span></span> <span data-ttu-id="e69e3-104">如果这些表之间不存在物理外键关系，则可以使用所选的条件帮助标识相关的表并将这些表添加到数据源视图中。</span><span class="sxs-lookup"><span data-stu-id="e69e3-104">If no physical foreign key relationships exist between the tables, this criterion helps you identify and add related tables to the data source view.</span></span> <span data-ttu-id="e69e3-105">通过名称匹配标识的逻辑关系也可以添加到数据源视图中。</span><span class="sxs-lookup"><span data-stu-id="e69e3-105">The logical relationships that are identified by name matching are also added to the data source view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e69e3-106">只有在您选择的数据源包含多个表，并且这些表中的任意表之间都没有外键关系时，此页才会显示。</span><span class="sxs-lookup"><span data-stu-id="e69e3-106">This page appears only if you select a data source that has multiple tables but no foreign key relationships between any one of the tables.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e69e3-107">选项</span><span class="sxs-lookup"><span data-stu-id="e69e3-107">Options</span></span>  
 <span data-ttu-id="e69e3-108">**通过匹配列创建逻辑关系**</span><span class="sxs-lookup"><span data-stu-id="e69e3-108">**Create logical relationships by matching columns**</span></span>  
 <span data-ttu-id="e69e3-109">选择此项可使用名称匹配条件，针对您选择的要包含在数据源视图中的表以及架构中的其他表，检测它们之间可能的逻辑依赖关系和关系。</span><span class="sxs-lookup"><span data-stu-id="e69e3-109">Select to use a name-matching criterion to detect possible logical dependencies and relationships between the tables that you select to include in the data source view and the other tables in the schema.</span></span> <span data-ttu-id="e69e3-110">如果清除此复选框，则不会使用任何名称匹配条件来标识数据源中表之间的逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="e69e3-110">If you clear this check box, no name-matching criterion is used to identify logical relationships between tables in the data source.</span></span>  
  
 <span data-ttu-id="e69e3-111">**外键匹配**</span><span class="sxs-lookup"><span data-stu-id="e69e3-111">**Foreign key matches**</span></span>  
 <span data-ttu-id="e69e3-112">选择用于在数据源中的表与视图之间创建逻辑关系的条件。</span><span class="sxs-lookup"><span data-stu-id="e69e3-112">Select the criterion to use for creating logical relationships between tables and views in the data source.</span></span> <span data-ttu-id="e69e3-113">匹配字符串中将忽略非字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="e69e3-113">Non-alphanumeric characters are ignored in matching strings.</span></span> <span data-ttu-id="e69e3-114">例如，“Customer ID”、“Customer_ID”和“CustomerID”相互匹配。</span><span class="sxs-lookup"><span data-stu-id="e69e3-114">For example, "Customer ID", "Customer_ID", "CustomerID" all match.</span></span> <span data-ttu-id="e69e3-115">选择下表中的选项之一可在指定条件下创建关系：</span><span class="sxs-lookup"><span data-stu-id="e69e3-115">Select one of the options in the following table to create relationships under the specified conditions.</span></span>  
  
|<span data-ttu-id="e69e3-116">Select</span><span class="sxs-lookup"><span data-stu-id="e69e3-116">Select</span></span>|<span data-ttu-id="e69e3-117">执行的创建操作</span><span class="sxs-lookup"><span data-stu-id="e69e3-117">To create</span></span>|  
|------------|---------------|  
|<span data-ttu-id="e69e3-118">**与主键同名**</span><span class="sxs-lookup"><span data-stu-id="e69e3-118">**Same name as primary key**</span></span>|<span data-ttu-id="e69e3-119">对于任何表，只要其中包含的任意一列的名称与所选表的主键列名相匹配，就创建与该表之间的逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="e69e3-119">A logical relationship to any table with a column name that matches the name of the primary key column in a selected table.</span></span>|  
|<span data-ttu-id="e69e3-120">**与目标表同名**</span><span class="sxs-lookup"><span data-stu-id="e69e3-120">**Same name as destination table name**</span></span>|<span data-ttu-id="e69e3-121">对于任何表，只要其中包含的任意一列的名称与所选表的名称相匹配，就创建与该表之间的逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="e69e3-121">A logical relationship to any table with a column name that matches the name of a selected table.</span></span>|  
|<span data-ttu-id="e69e3-122">**目标表名 + 主键名**</span><span class="sxs-lookup"><span data-stu-id="e69e3-122">**Destination table name + primary key name**</span></span>|<span data-ttu-id="e69e3-123">对于任何表，只要其中包含的任意一列的名称与所选表的名称和主键列名按该顺序连在一起的所选表的名称相匹配，就创建与该表之间的逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="e69e3-123">A logical relationship to any table in which a column name matches the selected table name concatenated with the name of the primary key column for the selected table, in that order.</span></span> <span data-ttu-id="e69e3-124">该连接形式中的非字母数字字符将被忽略（例如，“Product ID”、“Product_ID”和“ProductID”相互匹配）。</span><span class="sxs-lookup"><span data-stu-id="e69e3-124">Non-alphanumeric characters within the concatenation are ignored (for example, "Product ID", "Product_ID" and "ProductID" all match).</span></span>|  
  
 <span data-ttu-id="e69e3-125">**说明和示例**</span><span class="sxs-lookup"><span data-stu-id="e69e3-125">**Description and sample**</span></span>  
 <span data-ttu-id="e69e3-126">查看所选条件的说明和示例。</span><span class="sxs-lookup"><span data-stu-id="e69e3-126">View a description and a sample of the selected criterion.</span></span>  
  
  
