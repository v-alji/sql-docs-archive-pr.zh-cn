---
title: 定义维度的排序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579857"
---
# <a name="define-the-ordering-for-a-dimension"></a><span data-ttu-id="3db4a-102">定义维度的排序</span><span class="sxs-lookup"><span data-stu-id="3db4a-102">Define the Ordering for a Dimension</span></span>
  <span data-ttu-id="3db4a-103">可通过将属性排序增强功能添加到多维数据集或维度中，指定属性成员的排序方式。</span><span class="sxs-lookup"><span data-stu-id="3db4a-103">Add the attribute ordering enhancement to a cube or dimension to specify how the members of an attribute are ordered.</span></span> <span data-ttu-id="3db4a-104">成员可以按属性的名称或键进行排序，也可以按另一个属性的名称或键基于属性关系进行排序。</span><span class="sxs-lookup"><span data-stu-id="3db4a-104">Members can be ordered by the name or the key of the attribute, or by the name or the key of another attribute (based on an attribute relationship).</span></span> <span data-ttu-id="3db4a-105">默认情况下，成员按名称排序。</span><span class="sxs-lookup"><span data-stu-id="3db4a-105">By default, members are ordered by the name.</span></span> <span data-ttu-id="3db4a-106">此增强功能将更改维度中的属性的 `OrderBy` 和 `OrderByAttributeID` 属性设置。</span><span class="sxs-lookup"><span data-stu-id="3db4a-106">This enhancement changes the `OrderBy` and `OrderByAttributeID` property settings for attributes in a dimension.</span></span>  
  
 <span data-ttu-id="3db4a-107">若要添加属性排序功能，可以使用商业智能向导，并在 **“选择增强功能”** 页中选择 **“指定属性顺序”** 选项。</span><span class="sxs-lookup"><span data-stu-id="3db4a-107">To add attribute ordering, you use the Business Intelligence Wizard, and select the **Specify attribute ordering** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="3db4a-108">然后，此向导将指引您完成相应的步骤，以选择要应用属性排序的维度，并指定如何对所选维度的属性进行排序。</span><span class="sxs-lookup"><span data-stu-id="3db4a-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply attribute ordering and specifying how to order the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="3db4a-109">选择维度</span><span class="sxs-lookup"><span data-stu-id="3db4a-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="3db4a-110">在向导的第一个 **“指定属性顺序”** 页上，指定要应用属性排序的维度。</span><span class="sxs-lookup"><span data-stu-id="3db4a-110">On the first **Specify Attribute Ordering** page of the wizard, you specify the dimension to which you want to apply attribute ordering.</span></span> <span data-ttu-id="3db4a-111">添加到此所选维度中的属性排序增强功能将导致维度发生更改。</span><span class="sxs-lookup"><span data-stu-id="3db4a-111">The attribute ordering enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="3db4a-112">所有包含选定维度的多维数据集都将继承这些更改。</span><span class="sxs-lookup"><span data-stu-id="3db4a-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="specifying-ordering"></a><span data-ttu-id="3db4a-113">指定顺序</span><span class="sxs-lookup"><span data-stu-id="3db4a-113">Specifying Ordering</span></span>  
 <span data-ttu-id="3db4a-114">在向导的第二个 **“指定属性顺序”** 页上，指定维度中的所有属性将如何进行排序。</span><span class="sxs-lookup"><span data-stu-id="3db4a-114">On the second **Specify Attribute Ordering** page of the wizard, you specify how all the attributes in the dimension will be ordered.</span></span>  
  
 <span data-ttu-id="3db4a-115">在 **“排序依据属性”** 列中，可以更改用来进行排序的属性。</span><span class="sxs-lookup"><span data-stu-id="3db4a-115">In the **Ordering Attribute** column, you can change the attribute used to do the ordering.</span></span> <span data-ttu-id="3db4a-116">如果要用于对成员排序的属性不在列表中，请向下滚动列表，然后选择 **\<New attribute...>** 打开 "**选择列**" 对话框，在该对话框中，可以选择维度表中的列。</span><span class="sxs-lookup"><span data-stu-id="3db4a-116">If the attribute that you want to use to order members is not in the list, scroll down the list, and then select **\<New attribute...>** to open the **Select a Column** dialog box, where you can select a column in a dimension table.</span></span> <span data-ttu-id="3db4a-117">如果使用 **“选择列”** 对话框来选择列，则可以创建可用来对属性的成员进行排序的其他属性。</span><span class="sxs-lookup"><span data-stu-id="3db4a-117">Selecting a column by using the **Select a Column** dialog box creates an additional attribute with which to order members of an attribute.</span></span>  
  
 <span data-ttu-id="3db4a-118">然后，可以在 **“条件”** 列中选择按 **“键”** 还是按 **“名称”** 来对属性的成员进行排序。</span><span class="sxs-lookup"><span data-stu-id="3db4a-118">In the **Criteria** column, you can then select whether to order the members of the attribute by either **Key** or **Name**.</span></span>  
  
  
