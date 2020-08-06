---
title: "\"选择嵌套表键列\" 对话框 (挖掘结构视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589266"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a><span data-ttu-id="5daa6-102">“选择嵌套表键列”对话框（“挖掘结构”视图）</span><span class="sxs-lookup"><span data-stu-id="5daa6-102">Select a Nested Table Key Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="5daa6-103">可以使用 **“选择嵌套表键列”** 对话框，指定将用作新嵌套表的键的列。</span><span class="sxs-lookup"><span data-stu-id="5daa6-103">Use the **Select a Nested Table Key Column** dialog box to designate a column that will act as the key for the new nested table.</span></span> <span data-ttu-id="5daa6-104">在您退出此对话框后，挖掘结构中将添加一个包含指定键列的新表。</span><span class="sxs-lookup"><span data-stu-id="5daa6-104">When you exit the dialog box, a new table is added to the mining structure that contains the designated key column.</span></span> <span data-ttu-id="5daa6-105">通过右键单击结构，再选择“添加列”，可以向嵌套表中添加其他列。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5daa6-105">You can add additional columns to the nested table by right-clicking the structure and selecting **Add a Column**.</span></span> <span data-ttu-id="5daa6-106">根据使用的是 OLAP 挖掘模型还是关系挖掘模型，该对话框将包含不同的选项。</span><span class="sxs-lookup"><span data-stu-id="5daa6-106">The dialog box contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5daa6-107">选项</span><span class="sxs-lookup"><span data-stu-id="5daa6-107">Options</span></span>  
 <span data-ttu-id="5daa6-108">**源表**</span><span class="sxs-lookup"><span data-stu-id="5daa6-108">**Source table**</span></span>  
 <span data-ttu-id="5daa6-109">挖掘模型所基于的表。</span><span class="sxs-lookup"><span data-stu-id="5daa6-109">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="5daa6-110">此选项仅用于关系挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5daa6-110">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="5daa6-111">**源列**</span><span class="sxs-lookup"><span data-stu-id="5daa6-111">**Source column**</span></span>  
 <span data-ttu-id="5daa6-112">源表中所有可用作嵌套表键的列的列表。</span><span class="sxs-lookup"><span data-stu-id="5daa6-112">A list of all the available columns in the source table that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="5daa6-113">此选项仅用于关系挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5daa6-113">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="5daa6-114">**显示列类型**</span><span class="sxs-lookup"><span data-stu-id="5daa6-114">**Show column types**</span></span>  
 <span data-ttu-id="5daa6-115">可用列数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="5daa6-115">A list of available column data types.</span></span> <span data-ttu-id="5daa6-116">选中或清除数据类型可以对 **“源列”** 中列的列表进行筛选。</span><span class="sxs-lookup"><span data-stu-id="5daa6-116">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="5daa6-117">只有与所选数据类型匹配的列才会显示在 **“源列”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="5daa6-117">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="5daa6-118">此选项仅用于关系挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5daa6-118">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="5daa6-119">**属性**</span><span class="sxs-lookup"><span data-stu-id="5daa6-119">**Attributes**</span></span>  
 <span data-ttu-id="5daa6-120">可用作嵌套表键的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="5daa6-120">A list of attributes that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="5daa6-121">此选项仅用于 OLAP 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5daa6-121">This is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daa6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5daa6-122">See Also</span></span>  
 [<span data-ttu-id="5daa6-123">挖掘结构视图 &#40;数据挖掘模型设计器&#41;</span><span class="sxs-lookup"><span data-stu-id="5daa6-123">Mining Structure View &#40;Data Mining Model Designer&#41;</span></span>](mining-structure-view-data-mining-model-designer.md)  
  
  
