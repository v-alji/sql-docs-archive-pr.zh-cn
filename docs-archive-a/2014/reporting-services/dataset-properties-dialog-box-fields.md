---
title: "\"数据集属性\" 对话框-\"字段\" |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b9d315f85751c0f73896e809a522613fefece5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578729"
---
# <a name="dataset-properties-dialog-box-fields"></a><span data-ttu-id="11e02-102">“数据集属性”对话框 -&gt;“字段”</span><span class="sxs-lookup"><span data-stu-id="11e02-102">Dataset Properties Dialog Box, Fields</span></span>
  <span data-ttu-id="11e02-103">在 **“数据集属性”** 对话框中选择 **“字段”** 可更改报表数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="11e02-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="11e02-104">尽管字段列表是自动填充的，但是可以使用 **“字段”** 来添加、编辑和删除查询及计算字段。</span><span class="sxs-lookup"><span data-stu-id="11e02-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
## <a name="options"></a><span data-ttu-id="11e02-105">选项</span><span class="sxs-lookup"><span data-stu-id="11e02-105">Options</span></span>  
 <span data-ttu-id="11e02-106">**添加**</span><span class="sxs-lookup"><span data-stu-id="11e02-106">**Add**</span></span>  
 <span data-ttu-id="11e02-107">向数据集添加新的查询字段或计算字段。</span><span class="sxs-lookup"><span data-stu-id="11e02-107">Add a new query field or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="11e02-108">**删除**</span><span class="sxs-lookup"><span data-stu-id="11e02-108">**Delete**</span></span>  
 <span data-ttu-id="11e02-109">从数据集中删除所选字段。</span><span class="sxs-lookup"><span data-stu-id="11e02-109">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="11e02-110">**字段名称**</span><span class="sxs-lookup"><span data-stu-id="11e02-110">**Field Name**</span></span>  
 <span data-ttu-id="11e02-111">为字段键入名称。</span><span class="sxs-lookup"><span data-stu-id="11e02-111">Type a name for the field.</span></span> <span data-ttu-id="11e02-112">该字段在数据集中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="11e02-112">The field must be unique within the dataset.</span></span> <span data-ttu-id="11e02-113">对于数据集查询中的每个现有字段，名称是预先填充的。</span><span class="sxs-lookup"><span data-stu-id="11e02-113">For each existing field in the dataset query, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="11e02-114">**字段源**</span><span class="sxs-lookup"><span data-stu-id="11e02-114">**Field Source**</span></span>  
 <span data-ttu-id="11e02-115">为字段输入一个值。</span><span class="sxs-lookup"><span data-stu-id="11e02-115">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="11e02-116">对于计算字段，字段源必须是由数据集查询检索的现有字段的名称或您所创建的表达式。</span><span class="sxs-lookup"><span data-stu-id="11e02-116">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="11e02-117">例如，若要创建表示 10 倍于查询字段 Sales 中值的字段，请使用表达式 `=10 * Fields!Sales.Value`。</span><span class="sxs-lookup"><span data-stu-id="11e02-117">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="11e02-118">对于查询字段，字段源必须是由数据集查询检索的现有字段的名称。</span><span class="sxs-lookup"><span data-stu-id="11e02-118">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="11e02-119">**表达式 (fx)**</span><span class="sxs-lookup"><span data-stu-id="11e02-119">**Expression (fx)**</span></span>  
 <span data-ttu-id="11e02-120">添加或更改计算字段的表达式。</span><span class="sxs-lookup"><span data-stu-id="11e02-120">Add or change an expression for the calculated field.</span></span> <span data-ttu-id="11e02-121">仅当单击 **“添加”** 并选择 **“计算字段”** 时，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="11e02-121">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e02-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11e02-122">See Also</span></span>  
 <span data-ttu-id="11e02-123">[数据集字段集合（报表生成器和 SSRS）](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11e02-123">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11e02-124">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11e02-124">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="11e02-125">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="11e02-125">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
