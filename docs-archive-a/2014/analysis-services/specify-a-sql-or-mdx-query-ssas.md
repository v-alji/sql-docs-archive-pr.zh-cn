---
title: " (SSAS) 指定 SQL 或 MDX 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.specsqlmdxquery.f1
ms.assetid: e4128221-3b46-48be-b0f1-d82477ce6782
author: minewiskan
ms.author: owend
ms.openlocfilehash: bce5e92aaed7a62311e989d6963e4fa5764028ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691896"
---
# <a name="specify-a-sql-or-mdx-query-ssas"></a><span data-ttu-id="8f8c6-102">指定 SQL 或 MDX 查询 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="8f8c6-102">Specify a SQL or MDX Query (SSAS)</span></span>
  <span data-ttu-id="8f8c6-103">**“表导入向导”** 的这一页可用于通过使用 SQL 或 MDX 查询导入数据。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-103">This page of the **Table Import Wizard** enables you to import data by using a SQL or MDX query.</span></span> <span data-ttu-id="8f8c6-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="8f8c6-105">此查询可以处理导入的数据。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-105">The query can manipulate the data that is imported.</span></span> <span data-ttu-id="8f8c6-106">例如，您可以联接来自不同表的数据，或仅选择符合特定条件的行。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-106">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="8f8c6-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="8f8c6-107">UI element list</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f8c6-108">术语</span><span class="sxs-lookup"><span data-stu-id="8f8c6-108">Term</span></span>|<span data-ttu-id="8f8c6-109">定义</span><span class="sxs-lookup"><span data-stu-id="8f8c6-109">Definition</span></span>|  
|<span data-ttu-id="8f8c6-110">**友好的查询名称**</span><span class="sxs-lookup"><span data-stu-id="8f8c6-110">**Friendly Query Name**</span></span>|<span data-ttu-id="8f8c6-111">为查询键入唯一名称。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-111">Type a unique name for the query.</span></span> <span data-ttu-id="8f8c6-112">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-112">This is a required field.</span></span>|  
|<span data-ttu-id="8f8c6-113">**SQL 语句**</span><span class="sxs-lookup"><span data-stu-id="8f8c6-113">**SQL Statement**</span></span>|<span data-ttu-id="8f8c6-114">键入或粘贴 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-114">Type or paste a SQL statement.</span></span>|  
|<span data-ttu-id="8f8c6-115">**验证**</span><span class="sxs-lookup"><span data-stu-id="8f8c6-115">**Validate**</span></span>|<span data-ttu-id="8f8c6-116">确定 SQL 语句是否有效。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-116">Determine if the SQL statement is valid.</span></span>|  
|<span data-ttu-id="8f8c6-117">**设计**</span><span class="sxs-lookup"><span data-stu-id="8f8c6-117">**Design**</span></span>|<span data-ttu-id="8f8c6-118">使用查询设计器对话框设计 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-118">Design a SQL statement by using the query designer dialog box.</span></span> <span data-ttu-id="8f8c6-119">有关详细信息，请参阅[关系查询设计器用户界面 (SSAS)](relational-query-designer-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="8f8c6-119">For more information, see [Relational Query Designer &#40;SSAS&#41;](relational-query-designer-ssas.md).</span></span>|  
  
  
