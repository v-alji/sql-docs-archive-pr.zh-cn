---
title: 将属性添加到维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76a04c42cc501fdca3e5ceb6481452052966796b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577022"
---
# <a name="adding-attributes-to-dimensions"></a><span data-ttu-id="57a72-102">向维度添加属性</span><span class="sxs-lookup"><span data-stu-id="57a72-102">Adding Attributes to Dimensions</span></span>
  <span data-ttu-id="57a72-103">现在，您已经定义了维度，可以用表示维度中各数据元素的属性填充这些维度。</span><span class="sxs-lookup"><span data-stu-id="57a72-103">Now that you have defined dimensions, you can populate them with attributes that represent each data element in the dimension.</span></span> <span data-ttu-id="57a72-104">属性通常基于数据源视图中的字段。</span><span class="sxs-lookup"><span data-stu-id="57a72-104">Attributes are commonly based on fields from a data source view.</span></span> <span data-ttu-id="57a72-105">在向维度中添加属性时，您可以在数据源视图中包括来自任何表的字段。</span><span class="sxs-lookup"><span data-stu-id="57a72-105">When adding attributes to a dimension, you can include fields from any table in the data source view.</span></span>  
  
 <span data-ttu-id="57a72-106">在此任务中，将使用维度设计器向“客户”和“产品”维度中添加属性。</span><span class="sxs-lookup"><span data-stu-id="57a72-106">In this task, you will use Dimension Designer to add attributes to the Customer and Product dimensions.</span></span> <span data-ttu-id="57a72-107">“客户”维度将包括基于“客户”和“地域”表中的字段的属性。</span><span class="sxs-lookup"><span data-stu-id="57a72-107">The Customer dimension will include attributes based on fields from both the Customer and Geography tables.</span></span>  
  
## <a name="adding-attributes-to-the-customer-dimension"></a><span data-ttu-id="57a72-108">向“客户”维度中添加属性</span><span class="sxs-lookup"><span data-stu-id="57a72-108">Adding Attributes to the Customer Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="57a72-109">添加属性</span><span class="sxs-lookup"><span data-stu-id="57a72-109">To add attributes</span></span>  
  
1.  <span data-ttu-id="57a72-110">打开“客户”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="57a72-110">Open Dimension Designer for the Customer dimension.</span></span> <span data-ttu-id="57a72-111">为此，请在解决方案资源管理器的“维度”\*\*\*\* 节点中双击“客户”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="57a72-111">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="57a72-112">在“属性”\*\*\*\* 窗格中，请注意多维数据集向导已经创建的“客户关键字”和“地域关键字”属性。</span><span class="sxs-lookup"><span data-stu-id="57a72-112">In the **Attributes** pane, notice the Customer Key and Geography Key attributes that were created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="57a72-113">在“维度结构”\*\*\*\* 选项卡的工具栏上，确保用于在“数据源视图”\*\*\*\* 窗格中查看表的“缩放”图标设置为 100%。</span><span class="sxs-lookup"><span data-stu-id="57a72-113">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="57a72-114">在“数据源视图”\*\*\*\* 窗格中，将“Customer”\*\*\*\* 表的以下各列拖到“属性”\*\*\*\* 窗格中：</span><span class="sxs-lookup"><span data-stu-id="57a72-114">Drag the following columns from the **Customer** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="57a72-115">**BirthDate**</span><span class="sxs-lookup"><span data-stu-id="57a72-115">**BirthDate**</span></span>  
  
    -   <span data-ttu-id="57a72-116">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="57a72-116">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="57a72-117">**性别**</span><span class="sxs-lookup"><span data-stu-id="57a72-117">**Gender**</span></span>  
  
    -   <span data-ttu-id="57a72-118">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="57a72-118">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="57a72-119">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="57a72-119">**YearlyIncome**</span></span>  
  
    -   <span data-ttu-id="57a72-120">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="57a72-120">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="57a72-121">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="57a72-121">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="57a72-122">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="57a72-122">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="57a72-123">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="57a72-123">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="57a72-124">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="57a72-124">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="57a72-125">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="57a72-125">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="57a72-126">**移动**</span><span class="sxs-lookup"><span data-stu-id="57a72-126">**Phone**</span></span>  
  
    -   <span data-ttu-id="57a72-127">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="57a72-127">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="57a72-128">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="57a72-128">**CommuteDistance**</span></span>  
  
5.  <span data-ttu-id="57a72-129">将“数据源视图”\*\*\*\* 窗格内“Geography”\*\*\*\* 表中的以下各列拖到“属性”\*\*\*\* 窗格中：</span><span class="sxs-lookup"><span data-stu-id="57a72-129">Drag the following columns from the **Geography** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="57a72-130">**城市**</span><span class="sxs-lookup"><span data-stu-id="57a72-130">**City**</span></span>  
  
    -   <span data-ttu-id="57a72-131">**StateProvinceName**</span><span class="sxs-lookup"><span data-stu-id="57a72-131">**StateProvinceName**</span></span>  
  
    -   <span data-ttu-id="57a72-132">**EnglishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="57a72-132">**EnglishCountryRegionName**</span></span>  
  
    -   <span data-ttu-id="57a72-133">**PostalCode**</span><span class="sxs-lookup"><span data-stu-id="57a72-133">**PostalCode**</span></span>  
  
6.  <span data-ttu-id="57a72-134">在 "文件" 菜单上，单击 "**全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="57a72-134">On the File menu, click **Save All**.</span></span>  
  
## <a name="adding-attributes-to-the-product-dimension"></a><span data-ttu-id="57a72-135">向“产品”维度中添加属性</span><span class="sxs-lookup"><span data-stu-id="57a72-135">Adding Attributes to the Product Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="57a72-136">添加属性</span><span class="sxs-lookup"><span data-stu-id="57a72-136">To add attributes</span></span>  
  
1.  <span data-ttu-id="57a72-137">打开“产品”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="57a72-137">Open Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="57a72-138">在解决方案资源管理器中，双击“产品”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="57a72-138">Double-click the **Product** dimension in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="57a72-139">在“属性”\*\*\*\* 窗格中，请注意多维数据集向导创建的“产品密钥”属性。</span><span class="sxs-lookup"><span data-stu-id="57a72-139">In the **Attributes** pane, notice the Product Key attribute that was created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="57a72-140">在“维度结构”\*\*\*\* 选项卡的工具栏上，确保用于在“数据源视图”\*\*\*\* 窗格中查看表的“缩放”图标设置为 100%。</span><span class="sxs-lookup"><span data-stu-id="57a72-140">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="57a72-141">将“数据源视图”\*\*\*\* 窗格内“Product”\*\*\*\* 表中的以下各列拖到“属性”\*\*\*\* 窗格中：</span><span class="sxs-lookup"><span data-stu-id="57a72-141">Drag the following columns from the **Product** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="57a72-142">**StandardCost**</span><span class="sxs-lookup"><span data-stu-id="57a72-142">**StandardCost**</span></span>  
  
    -   <span data-ttu-id="57a72-143">**颜色**</span><span class="sxs-lookup"><span data-stu-id="57a72-143">**Color**</span></span>  
  
    -   <span data-ttu-id="57a72-144">**SafetyStockLevel**</span><span class="sxs-lookup"><span data-stu-id="57a72-144">**SafetyStockLevel**</span></span>  
  
    -   <span data-ttu-id="57a72-145">**ReorderPoint**</span><span class="sxs-lookup"><span data-stu-id="57a72-145">**ReorderPoint**</span></span>  
  
    -   <span data-ttu-id="57a72-146">**ListPrice**</span><span class="sxs-lookup"><span data-stu-id="57a72-146">**ListPrice**</span></span>  
  
    -   <span data-ttu-id="57a72-147">**大小**</span><span class="sxs-lookup"><span data-stu-id="57a72-147">**Size**</span></span>  
  
    -   <span data-ttu-id="57a72-148">**SizeRange**</span><span class="sxs-lookup"><span data-stu-id="57a72-148">**SizeRange**</span></span>  
  
    -   <span data-ttu-id="57a72-149">**Weight**</span><span class="sxs-lookup"><span data-stu-id="57a72-149">**Weight**</span></span>  
  
    -   <span data-ttu-id="57a72-150">**DaysToManufacture**</span><span class="sxs-lookup"><span data-stu-id="57a72-150">**DaysToManufacture**</span></span>  
  
    -   <span data-ttu-id="57a72-151">**ProductLine**</span><span class="sxs-lookup"><span data-stu-id="57a72-151">**ProductLine**</span></span>  
  
    -   <span data-ttu-id="57a72-152">**DealerPrice**</span><span class="sxs-lookup"><span data-stu-id="57a72-152">**DealerPrice**</span></span>  
  
    -   <span data-ttu-id="57a72-153">**类**</span><span class="sxs-lookup"><span data-stu-id="57a72-153">**Class**</span></span>  
  
    -   <span data-ttu-id="57a72-154">**样式**</span><span class="sxs-lookup"><span data-stu-id="57a72-154">**Style**</span></span>  
  
    -   <span data-ttu-id="57a72-155">**ModelName**</span><span class="sxs-lookup"><span data-stu-id="57a72-155">**ModelName**</span></span>  
  
    -   <span data-ttu-id="57a72-156">**StartDate**</span><span class="sxs-lookup"><span data-stu-id="57a72-156">**StartDate**</span></span>  
  
    -   <span data-ttu-id="57a72-157">**EndDate**</span><span class="sxs-lookup"><span data-stu-id="57a72-157">**EndDate**</span></span>  
  
    -   <span data-ttu-id="57a72-158">**Status**</span><span class="sxs-lookup"><span data-stu-id="57a72-158">**Status**</span></span>  
  
5.  <span data-ttu-id="57a72-159">在 "文件" 菜单上，单击 "**全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="57a72-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="57a72-160">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="57a72-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="57a72-161">检查多维数据集和维度属性</span><span class="sxs-lookup"><span data-stu-id="57a72-161">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="57a72-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57a72-162">See Also</span></span>  
 [<span data-ttu-id="57a72-163">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="57a72-163">Dimension Attribute Properties Reference</span></span>](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
