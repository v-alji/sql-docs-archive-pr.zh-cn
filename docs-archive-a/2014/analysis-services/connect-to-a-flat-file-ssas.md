---
title: " (SSAS) 连接到平面文件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579218"
---
# <a name="connect-to-a-flat-file-ssas"></a><span data-ttu-id="8c49a-102">连接到平面文件 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="8c49a-102">Connect to a Flat File (SSAS)</span></span>
  <span data-ttu-id="8c49a-103">“表导入向导”\*\*\*\* 的这一页可用于连接到平面文件 (.txt)、制表符分隔的文件 (.tab) 或逗号分隔的文件 (.csv)。</span><span class="sxs-lookup"><span data-stu-id="8c49a-103">This page of the **Table Import Wizard** enables you to connect to a flat file (.txt), tab-separated file (.tab), or a comma-separated file (.csv).</span></span> <span data-ttu-id="8c49a-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="8c49a-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="8c49a-105">若要连接到平面文件，必须在计算机上安装 ACE 访问接口。</span><span class="sxs-lookup"><span data-stu-id="8c49a-105">To connect to a flat file, you must have the ACE provider installed on your computer.</span></span> <span data-ttu-id="8c49a-106">有关详细信息，请参阅[数据源支持（SSAS 表格）](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="8c49a-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c49a-107">在此页中选择文件时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="8c49a-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="8c49a-108">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选文件中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="8c49a-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="8c49a-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="8c49a-109">UI element list</span></span>  
 <span data-ttu-id="8c49a-110">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="8c49a-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="8c49a-111">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="8c49a-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="8c49a-112">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="8c49a-112">This is a required field.</span></span>  
  
 <span data-ttu-id="8c49a-113">**文件路径**</span><span class="sxs-lookup"><span data-stu-id="8c49a-113">**File Path**</span></span>  
 <span data-ttu-id="8c49a-114">指定文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="8c49a-114">Specify a full path for the file.</span></span>  
  
 <span data-ttu-id="8c49a-115">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="8c49a-115">**Browse**</span></span>  
 <span data-ttu-id="8c49a-116">导航至文件可用的位置。</span><span class="sxs-lookup"><span data-stu-id="8c49a-116">Navigate to a location where a file is available.</span></span>  
  
 <span data-ttu-id="8c49a-117">**列分隔符**</span><span class="sxs-lookup"><span data-stu-id="8c49a-117">**Column Separator**</span></span>  
 <span data-ttu-id="8c49a-118">从可用列分隔符的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="8c49a-118">Select from a list of available column separators.</span></span> <span data-ttu-id="8c49a-119">选择不可能出现在文本中的分隔符。</span><span class="sxs-lookup"><span data-stu-id="8c49a-119">Choose a separator that is not likely to occur in the text.</span></span>  
  
|<span data-ttu-id="8c49a-120">值</span><span class="sxs-lookup"><span data-stu-id="8c49a-120">Value</span></span>|<span data-ttu-id="8c49a-121">说明</span><span class="sxs-lookup"><span data-stu-id="8c49a-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8c49a-122">制表符 (t)</span><span class="sxs-lookup"><span data-stu-id="8c49a-122">Tab (t)</span></span>|<span data-ttu-id="8c49a-123">列由制表符 (t) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-123">Columns are separated by a tab (t).</span></span>|  
|<span data-ttu-id="8c49a-124">逗号 (,)</span><span class="sxs-lookup"><span data-stu-id="8c49a-124">Comma (,)</span></span>|<span data-ttu-id="8c49a-125">列由逗号 (,) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-125">Columns are separated by a comma (,).</span></span>|  
|<span data-ttu-id="8c49a-126">分号 (;)</span><span class="sxs-lookup"><span data-stu-id="8c49a-126">Semicolon (;)</span></span>|<span data-ttu-id="8c49a-127">列由分号 (;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-127">Columns are separated by a semicolon (;).</span></span>|  
|<span data-ttu-id="8c49a-128">空格 ( )</span><span class="sxs-lookup"><span data-stu-id="8c49a-128">Space ( )</span></span>|<span data-ttu-id="8c49a-129">列由空格 ( ) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-129">Columns are separated by a space ( ).</span></span>|  
|<span data-ttu-id="8c49a-130">冒号 (:)</span><span class="sxs-lookup"><span data-stu-id="8c49a-130">Colon (:)</span></span>|<span data-ttu-id="8c49a-131">列由冒号 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-131">Columns are separated by a colon (:).</span></span>|  
|<span data-ttu-id="8c49a-132">竖线 (|)</span><span class="sxs-lookup"><span data-stu-id="8c49a-132">Vertical Bar (&#124;)</span></span>|<span data-ttu-id="8c49a-133">列由竖线 (|) 分隔。</span><span class="sxs-lookup"><span data-stu-id="8c49a-133">Columns are separated by a vertical bar (&#124;).</span></span>|  
  
 <span data-ttu-id="8c49a-134">**高级**</span><span class="sxs-lookup"><span data-stu-id="8c49a-134">**Advanced**</span></span>  
 <span data-ttu-id="8c49a-135">为平面文件指定编码和区域设置选项。</span><span class="sxs-lookup"><span data-stu-id="8c49a-135">Specify the encoding and locale options for the flat file.</span></span>  
  
 <span data-ttu-id="8c49a-136">**使用第一行作为列标题**</span><span class="sxs-lookup"><span data-stu-id="8c49a-136">**Use first row as column headers**</span></span>  
 <span data-ttu-id="8c49a-137">指定是否要使用第一个数据行作为目标表的列标题。</span><span class="sxs-lookup"><span data-stu-id="8c49a-137">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="8c49a-138">**数据预览**</span><span class="sxs-lookup"><span data-stu-id="8c49a-138">**Data preview**</span></span>  
 <span data-ttu-id="8c49a-139">预览所选文件中的数据，并且使用以下选项修改数据导入。</span><span class="sxs-lookup"><span data-stu-id="8c49a-139">Preview the data in the selected file, and use the following options to modify the data import.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c49a-140">只有文件中的前 50 行显示在此预览。</span><span class="sxs-lookup"><span data-stu-id="8c49a-140">Only the first 50 rows in the file are displayed in this preview.</span></span>  
  
|<span data-ttu-id="8c49a-141">选项</span><span class="sxs-lookup"><span data-stu-id="8c49a-141">Option</span></span>|<span data-ttu-id="8c49a-142">说明</span><span class="sxs-lookup"><span data-stu-id="8c49a-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8c49a-143">**列标题中的复选框**</span><span class="sxs-lookup"><span data-stu-id="8c49a-143">**Checkbox in the column header**</span></span>|<span data-ttu-id="8c49a-144">选中该复选框可在数据导入中包括列。</span><span class="sxs-lookup"><span data-stu-id="8c49a-144">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="8c49a-145">取消选中该复选框则从数据导入中删除列。</span><span class="sxs-lookup"><span data-stu-id="8c49a-145">Clear the checkbox to remove the column from the data import.</span></span>|  
|<span data-ttu-id="8c49a-146">**列标题中的下箭头按钮**</span><span class="sxs-lookup"><span data-stu-id="8c49a-146">**Down-arrow button in the column header**</span></span>|<span data-ttu-id="8c49a-147">对列中的数据进行排序和筛选。</span><span class="sxs-lookup"><span data-stu-id="8c49a-147">Sort and filter data in the column.</span></span>|  
  
 <span data-ttu-id="8c49a-148">**清除行筛选器**</span><span class="sxs-lookup"><span data-stu-id="8c49a-148">**Clear Row Filters**</span></span>  
 <span data-ttu-id="8c49a-149">删除已应用于列中数据的所有筛选器。</span><span class="sxs-lookup"><span data-stu-id="8c49a-149">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
