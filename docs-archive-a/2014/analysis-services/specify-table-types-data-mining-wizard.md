---
title: " (数据挖掘向导) 指定表类型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88c09f26958c37ed0a99efb54a5eb5c08505d16b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589244"
---
# <a name="specify-table-types-data-mining-wizard"></a><span data-ttu-id="3dc51-102">指定表类型(数据挖掘向导)</span><span class="sxs-lookup"><span data-stu-id="3dc51-102">Specify Table Types (Data Mining Wizard)</span></span>
  <span data-ttu-id="3dc51-103">可以使用 **“指定表类型”** 页指定用于定义挖掘结构的表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-103">Use the **Specify Table Types** page to identify the tables to use to define the mining structure.</span></span> <span data-ttu-id="3dc51-104">如果未选择某个表，则将不能使用该表来定义挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="3dc51-104">If a table is not selected, it will not be used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dc51-105"> 可以在以后在 **数据挖掘设计器** 的 **“挖掘结构”** 选项卡上添加表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-105">You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.</span></span>  
  
 <span data-ttu-id="3dc51-106">**有关详细信息，请参阅** [嵌套表（Analysis Services – 数据挖掘）](data-mining/nested-tables-analysis-services-data-mining.md)、[数据挖掘向导（Analysis Services - 数据挖掘）](data-mining/data-mining-wizard-analysis-services-data-mining.md)和[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="3dc51-106">**For More Information:** [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="3dc51-107">选项</span><span class="sxs-lookup"><span data-stu-id="3dc51-107">Options</span></span>  
 <span data-ttu-id="3dc51-108">**表**</span><span class="sxs-lookup"><span data-stu-id="3dc51-108">**Tables**</span></span>  
 <span data-ttu-id="3dc51-109">显示在向导的“选择数据源视图”\*\*\*\* 页上选择的数据源视图中的表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-109">Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.</span></span>  
  
 <span data-ttu-id="3dc51-110">**区分**</span><span class="sxs-lookup"><span data-stu-id="3dc51-110">**Case**</span></span>  
 <span data-ttu-id="3dc51-111">选择一个要用作事例表的表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-111">Select one table to use as the case table.</span></span>  
  
 <span data-ttu-id="3dc51-112">**嵌套**</span><span class="sxs-lookup"><span data-stu-id="3dc51-112">**Nested**</span></span>  
 <span data-ttu-id="3dc51-113">选择要用作嵌套表的表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-113">Select the tables to use as nested tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dc51-114">这些表必须与事例表具有多对一关系，而不是一对多关系。</span><span class="sxs-lookup"><span data-stu-id="3dc51-114">These tables must have a many-to-one relationship with the case table, not a one-to-many relationship.</span></span> <span data-ttu-id="3dc51-115">必须在数据源视图中指定此关系，才能将表选择为嵌套表。</span><span class="sxs-lookup"><span data-stu-id="3dc51-115">You must specify this relationship in the data source view before you can select the table as nested.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc51-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3dc51-116">See Also</span></span>  
 <span data-ttu-id="3dc51-117">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3dc51-117">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3dc51-118">[在数据挖掘向导 &#40;选择数据源视图&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3dc51-118">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="3dc51-119">在数据挖掘向导 &#40;指定定型数据&#41;</span><span class="sxs-lookup"><span data-stu-id="3dc51-119">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
