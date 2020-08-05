---
title: 选择维度属性 (维度向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4961092517ce1d38cfd4086ec083a939242652d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579835"
---
# <a name="select-dimension-attributes-dimension-wizard"></a><span data-ttu-id="127db-102">选择维度属性（维度向导）</span><span class="sxs-lookup"><span data-stu-id="127db-102">Select Dimension Attributes (Dimension Wizard)</span></span>
  <span data-ttu-id="127db-103">可以使用 **“选择维度属性”** 页选择和修改要创建的维度的属性。</span><span class="sxs-lookup"><span data-stu-id="127db-103">Use the **Select Dimension Attributes** page to select and modify the attributes for the dimension to be created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="127db-104">如果您无法读取任何列的值，请将向导窗口最大化并改变每个列标题的宽度直到可以读取这些值。</span><span class="sxs-lookup"><span data-stu-id="127db-104">If you cannot read the values for any column, maximize the wizard window and change the width of each column heading until you can read the values.</span></span>  
  
 <span data-ttu-id="127db-105">**打开维度向导**</span><span class="sxs-lookup"><span data-stu-id="127db-105">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="127db-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的**解决方案资源管理器**中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目的“维度”文件夹，然后单击“新建维度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="127db-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="127db-107">选项</span><span class="sxs-lookup"><span data-stu-id="127db-107">Options</span></span>  
 <span data-ttu-id="127db-108">(带复选框的列)</span><span class="sxs-lookup"><span data-stu-id="127db-108">(Column with check boxes)</span></span>  
 <span data-ttu-id="127db-109">选择此项将包括维度中的属性。</span><span class="sxs-lookup"><span data-stu-id="127db-109">Select to include an attribute in the dimension.</span></span>  
  
 <span data-ttu-id="127db-110">若要包含特定属性，请选中该属性的复选框。</span><span class="sxs-lookup"><span data-stu-id="127db-110">To include a specific attribute, select the check box for that attribute.</span></span>  
  
 <span data-ttu-id="127db-111">若要包含所有属性，请选中列标题中的复选框。</span><span class="sxs-lookup"><span data-stu-id="127db-111">To include all attributes, select the check box in the column header.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="127db-112">键属性的复选框不能清除。</span><span class="sxs-lookup"><span data-stu-id="127db-112">The check box for the key attribute cannot be cleared.</span></span>  
  
 <span data-ttu-id="127db-113">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="127db-113">**Attribute Name**</span></span>  
 <span data-ttu-id="127db-114">列出可用属性。</span><span class="sxs-lookup"><span data-stu-id="127db-114">Lists the available attributes.</span></span>  
  
 <span data-ttu-id="127db-115">若要更改属性的名称，请单击属性名称并键入该属性的新名称。</span><span class="sxs-lookup"><span data-stu-id="127db-115">To change the name of an attribute, click the attribute name and type a new name for the attribute.</span></span>  
  
 <span data-ttu-id="127db-116">**启用浏览**</span><span class="sxs-lookup"><span data-stu-id="127db-116">**Enable Browsing**</span></span>  
 <span data-ttu-id="127db-117">选中此项可使最终用户能够浏览并筛选属性。</span><span class="sxs-lookup"><span data-stu-id="127db-117">Select to make the attribute available to the end user for browsing and filtering.</span></span> <span data-ttu-id="127db-118">对于键属性，必须选中 **“启用浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="127db-118">**Enable Browsing** must be selected for the key attribute.</span></span> <span data-ttu-id="127db-119">对于非键属性，默认未选中“启用浏览”\*\*\*\*，这将导致非键属性只显示为成员属性。</span><span class="sxs-lookup"><span data-stu-id="127db-119">For non-key attributes, the default is not to have **Enable Browsing** selected, which causes the non-key attributes to be shown only as member properties.</span></span>  
  
 <span data-ttu-id="127db-120">在大多数情况下，将 `AttributeHierarchyEnabled` 属性设置为 `True` 或 `False` 可以使浏览分别为可用或不可用。</span><span class="sxs-lookup"><span data-stu-id="127db-120">In most cases, the attribute is made available or not available for browsing by setting the `AttributeHierarchyEnabled` property to `True` or `False`, respectively.</span></span> <span data-ttu-id="127db-121">但是，在下列三种情况中，向导使用不同的设置。</span><span class="sxs-lookup"><span data-stu-id="127db-121">However, in the following three cases, the wizard uses different settings.</span></span>  
  
|<span data-ttu-id="127db-122">案例</span><span class="sxs-lookup"><span data-stu-id="127db-122">Case</span></span>|<span data-ttu-id="127db-123">设置</span><span class="sxs-lookup"><span data-stu-id="127db-123">Settings</span></span>|  
|----------|--------------|  
|<span data-ttu-id="127db-124">维度包含父子层次结构并且没有选中“启用浏览”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="127db-124">A dimension contains a parent-child hierarchy and **Enable Browsing** is not selected</span></span>|<span data-ttu-id="127db-125">向导将键特性的 `AttributeHierarchyEnabled` 属性设置保留为 `True`，并将 `AttributeHierarchyVisible` 属性设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="127db-125">The wizard leaves the `AttributeHierarchyEnabled` property set to `True`, and sets the `AttributeHierarchyVisible` attribute to `False` for the key attribute.</span></span>|  
|<span data-ttu-id="127db-126">维度中的表包含指向维度中没有的表的外键</span><span class="sxs-lookup"><span data-stu-id="127db-126">A table in a dimension contains a foreign key to a table that is not in the dimension</span></span>|<span data-ttu-id="127db-127">向导选择该外键作为要包含的属性，但不选中 **“启用浏览”**。</span><span class="sxs-lookup"><span data-stu-id="127db-127">The wizard selects the foreign key as an attribute to be included, but will not select **Enable Browsing**.</span></span> <span data-ttu-id="127db-128">如果保留这些设置，则特性的 `AttributeHiearchyEnabled` 属性将设置为 `True`，而 `AttributeHierarchyVisible` 属性将设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="127db-128">If you keep these settings, the `AttributeHiearchyEnabled` property of the attribute will be set to `True`, and the `AttributeHierarchyVisible` property will be set to `False`.</span></span>|  
|<span data-ttu-id="127db-129">维度包含通过可为空值的外键列访问的雪花型表</span><span class="sxs-lookup"><span data-stu-id="127db-129">A dimension contains snowflake tables that are reached through nullable foreign key columns</span></span><br /><br /> <span data-ttu-id="127db-130">－和－</span><span class="sxs-lookup"><span data-stu-id="127db-130">-and-</span></span><br /><br /> <span data-ttu-id="127db-131">对于基于雪花型表键的属性，不选中“启用浏览”</span><span class="sxs-lookup"><span data-stu-id="127db-131">Enable Browsing for the attribute that is based on the key of the snowflake table is not selected</span></span>|<span data-ttu-id="127db-132">向导将创建 `AttributeHiearchyEnabled` 属性设置为 `True`，`AttributeHierarchyVisible` 属性设置为 `False` 的新特性。</span><span class="sxs-lookup"><span data-stu-id="127db-132">The wizard will create the new attribute that has the `AttributeHiearchyEnabled` property set to `True`, and the `AttributeHierarchyVisible` property set to `False`.</span></span>|  
  
 <span data-ttu-id="127db-133">**特性类型**</span><span class="sxs-lookup"><span data-stu-id="127db-133">**Attribute Type**</span></span>  
 <span data-ttu-id="127db-134">（可选）设置属性的类型。</span><span class="sxs-lookup"><span data-stu-id="127db-134">(Optional) Set the type for the attribute.</span></span> <span data-ttu-id="127db-135">默认值为 **Regular**。</span><span class="sxs-lookup"><span data-stu-id="127db-135">The default value is **Regular**.</span></span> <span data-ttu-id="127db-136">属性类型向客户端应用程序提供属性中可能包含的信息类型的指南。</span><span class="sxs-lookup"><span data-stu-id="127db-136">The attribute type provides guidance to client applications on what information the attribute might contain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127db-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="127db-137">See Also</span></span>  
 <span data-ttu-id="127db-138">[维度向导的 F1 帮助](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="127db-138">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="127db-139">[Analysis Services 多维数据 &#40;维度&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="127db-139">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="127db-140">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="127db-140">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
