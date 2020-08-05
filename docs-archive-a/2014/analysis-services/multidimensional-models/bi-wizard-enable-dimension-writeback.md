---
title: 启用维度写回 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
ms.openlocfilehash: cba4a54e8a51d022c6f84a4c81d32f359a95692a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579853"
---
# <a name="enable-dimension-writeback"></a><span data-ttu-id="2ccbb-102">“启用维度写回”</span><span class="sxs-lookup"><span data-stu-id="2ccbb-102">Enable Dimension Writeback</span></span>
  <span data-ttu-id="2ccbb-103">通过为多维数据集或维度添加维度写回增强功能，可以使用户手动修改维度结构和成员。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-103">Add the dimension writeback enhancement to a cube or dimension to allow users to manually modify the dimension structure and members.</span></span> <span data-ttu-id="2ccbb-104">对允许写维度的更新直接记录在该维度表中。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-104">Updates to a write-enabled dimension are recorded directly in the dimension table.</span></span> <span data-ttu-id="2ccbb-105">此增强功能更改了维度的 `WriteEnabled` 属性设置。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-105">This enhancement changes the `WriteEnabled` property setting for a dimension.</span></span>  
  
 <span data-ttu-id="2ccbb-106">若要添加维度写回，请使用商业智能向导，然后在 **“选择增强功能”** 页中选择 **“启用维度写回”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-106">To add dimension writeback, you use the Business Intelligence Wizard, and select the **Enable dimension writeback** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="2ccbb-107">然后，此向导将指引您完成相应的步骤，以选择要应用维度写回的维度，并为所选维度设置此选项。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension writeback and setting this option for the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ccbb-108">仅对 SQL Server 关系数据库和数据市场支持写回。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-108">Writeback is supported for SQL Server relational databases and data marts only.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="2ccbb-109">选择维度</span><span class="sxs-lookup"><span data-stu-id="2ccbb-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="2ccbb-110">在向导的第一个 **“启用维度写回”** 页中，指定要应用维度写回的维度。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-110">On the first **Enable Dimension Writeback** page of the wizard, you specify the dimension to which you want to apply dimension writeback.</span></span> <span data-ttu-id="2ccbb-111">为该所选维度添加的维度写回增强功能将导致维度发生更改。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-111">The dimension writeback enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="2ccbb-112">所有包含选定维度的多维数据集都将继承这些更改。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="setting-dimension-writeback-capability"></a><span data-ttu-id="2ccbb-113">设置维度写回功能</span><span class="sxs-lookup"><span data-stu-id="2ccbb-113">Setting Dimension Writeback Capability</span></span>  
 <span data-ttu-id="2ccbb-114">在向导的第二个 **“启用维度写回”** 页中，实际设置 **“在维度中启用写回”** 选项。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-114">On the second **Enable Dimension Writeback** page of the wizard, you actually set the **Enable writeback in the dimension** option.</span></span> <span data-ttu-id="2ccbb-115">选择此选项将使维度的 `WriteEnabled` 属性自动设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-115">Selecting this option automatically sets the `WriteEnabled` property of the dimension to `True`.</span></span> <span data-ttu-id="2ccbb-116">清除此选项将使该属性自动设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-116">Clearing this option automatically sets the property to `False`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ccbb-117">备注</span><span class="sxs-lookup"><span data-stu-id="2ccbb-117">Remarks</span></span>  
 <span data-ttu-id="2ccbb-118">创建新成员时，必须包括维度中的所有属性。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-118">When you create a new member, you must include every attribute in a dimension.</span></span> <span data-ttu-id="2ccbb-119">您不能插入未指定维度的键属性值的成员。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-119">You cannot insert a member without specifying a value for the key attribute of the dimension.</span></span> <span data-ttu-id="2ccbb-120">因此，创建成员时，应服从对维度表定义的任何约束（例如，非空键值）。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-120">Therefore, creating members is subject to any constraints (such as non-null key values) that are defined on the dimension table.</span></span> <span data-ttu-id="2ccbb-121">您还应该考虑可能由维度属性指定的列，例如在 `CustomRollupColumn`、`CustomRollupPropertiesColumn` 或 `UnaryOperatorColumn` 维度属性中指定的列。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-121">You should also consider columns optionally specified by dimension properties, such as columns specified in the `CustomRollupColumn`, `CustomRollupPropertiesColumn` or the `UnaryOperatorColumn` dimension properties.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2ccbb-122">如果您使用 SQL Azure 作为数据源来执行写回到 Analysis Services 数据库，则该操作将失败。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-122">If you use SQL Azure as a data source to perform writeback into an Analysis Services database, the operation fails.</span></span> <span data-ttu-id="2ccbb-123">这是默认设置，因为默认不启用实现多个活动的结果集 (MARS) 的提供程序选项。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-123">This is by design, because the provider option that enables multiple active result sets (MARS) is not turned on by default.</span></span>  
>   
>  <span data-ttu-id="2ccbb-124">解决方法是在连接字符串中添加以下设置，以便支持 MARS 并启用写回：</span><span class="sxs-lookup"><span data-stu-id="2ccbb-124">The workaround is to add the following setting in the connection string, to support MARS and to enable writeback:</span></span>  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  <span data-ttu-id="2ccbb-125">有关详细信息，请参阅[使用多个活动结果集 &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)。</span><span class="sxs-lookup"><span data-stu-id="2ccbb-125">For more information see [Using Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ccbb-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ccbb-126">See Also</span></span>  
 [<span data-ttu-id="2ccbb-127">启用写操作的维度</span><span class="sxs-lookup"><span data-stu-id="2ccbb-127">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
