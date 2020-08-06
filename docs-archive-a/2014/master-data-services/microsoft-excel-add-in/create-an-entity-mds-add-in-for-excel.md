---
title: 创建实体 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d354abb3-88fe-4b40-a374-f6256b84ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87ad67f7347da87c67afc11590df6775af4cf3d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576865"
---
# <a name="create-an-entity-mds-add-in-for-excel"></a><span data-ttu-id="dca8e-102">创建实体（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="dca8e-102">Create an Entity (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="dca8e-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，管理员可以创建新的实体来存储数据。</span><span class="sxs-lookup"><span data-stu-id="dca8e-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create new entities to store data.</span></span> <span data-ttu-id="dca8e-104">当您创建实体时，应加载要存储的数据的至少一个抽样。</span><span class="sxs-lookup"><span data-stu-id="dca8e-104">When you create an entity you should load at least a sampling of the data you want to store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dca8e-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="dca8e-105">Prerequisites</span></span>  
 <span data-ttu-id="dca8e-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="dca8e-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="dca8e-107">您必须有权访问 **“系统管理”** 功能区域和 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="dca8e-107">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="dca8e-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="dca8e-108">You must be a model administrator.</span></span> <span data-ttu-id="dca8e-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dca8e-109">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="dca8e-110">您必须具有要在其中创建实体的现有模型。</span><span class="sxs-lookup"><span data-stu-id="dca8e-110">You must have an existing model to create the entity in.</span></span> <span data-ttu-id="dca8e-111">有关详细信息，请参阅[创建模型 (Master Data Services)](../create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dca8e-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../create-a-model-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="dca8e-112">请确保您的数据满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="dca8e-112">Ensure that your data meets the following requirements:</span></span>  
  
    -   <span data-ttu-id="dca8e-113">数据应具有标题行。</span><span class="sxs-lookup"><span data-stu-id="dca8e-113">The data should have a header row.</span></span>  
  
    -   <span data-ttu-id="dca8e-114">具有 **“名称”** 和 **“代码”** 列是有帮助的。</span><span class="sxs-lookup"><span data-stu-id="dca8e-114">It is helpful to have **Name** and **Code** columns.</span></span> <span data-ttu-id="dca8e-115">**“代码”** 是每行的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="dca8e-115">**Code** is a unique identifier for each row.</span></span>  
  
    -   <span data-ttu-id="dca8e-116">您应该除了标题行之外还具有至少一行数据。</span><span class="sxs-lookup"><span data-stu-id="dca8e-116">You should have at least one row of data other than the header.</span></span> <span data-ttu-id="dca8e-117">不是所有列都需要值，但数据应该代表将位于实体中的数据。</span><span class="sxs-lookup"><span data-stu-id="dca8e-117">All columns do not need values, but the data should be representative of the data that will be in the entity.</span></span>  
  
    -   <span data-ttu-id="dca8e-118">如果你具有包含唯一标识符的列（在 MDS 中称作 **代码**），则请确保这些值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dca8e-118">If you have a column that contains a unique identifier (known in MDS as **Code**), ensure that the values are unique.</span></span> <span data-ttu-id="dca8e-119">如果没有包含标识符的列，则可以让这些列在您创建实体时自动生成。</span><span class="sxs-lookup"><span data-stu-id="dca8e-119">If no column contains identifiers, you can have them generated automatically when you create the entity.</span></span>  
  
    -   <span data-ttu-id="dca8e-120">请确保没有单元包含公式。</span><span class="sxs-lookup"><span data-stu-id="dca8e-120">Ensure that no cells contain formulas.</span></span>  
  
    -   <span data-ttu-id="dca8e-121">请确保没有单元包含时间值。</span><span class="sxs-lookup"><span data-stu-id="dca8e-121">Ensure that no cells contain time values.</span></span> <span data-ttu-id="dca8e-122">可以将日期值保存在 MDS 中，但不能保存时间值。</span><span class="sxs-lookup"><span data-stu-id="dca8e-122">Date values can be saved in MDS but time values cannot.</span></span>  
  
### <a name="to-create-an-entity-and-load-data"></a><span data-ttu-id="dca8e-123">创建实体和加载数据</span><span class="sxs-lookup"><span data-stu-id="dca8e-123">To create an entity and load data</span></span>  
  
1.  <span data-ttu-id="dca8e-124">打开或创建包含您要加载的数据的 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="dca8e-124">Open or create an Excel worksheet that contains data you want to load.</span></span>  
  
2.  <span data-ttu-id="dca8e-125">选择要将新实体加载到的单元。</span><span class="sxs-lookup"><span data-stu-id="dca8e-125">Select the cells you want to load into the new entity.</span></span>  
  
3.  <span data-ttu-id="dca8e-126">在 **“主数据”** 选项卡上的 **“生成模型”** 组中，单击 **“创建实体”**。</span><span class="sxs-lookup"><span data-stu-id="dca8e-126">On the **Master Data** tab, in the **Build Model** group, click **Create Entity**.</span></span>  
  
4.  <span data-ttu-id="dca8e-127">如果系统提示您连接到某一 MDS 存储库，则进行连接。</span><span class="sxs-lookup"><span data-stu-id="dca8e-127">If you are prompted to connect to an MDS repository, connect.</span></span>  
  
5.  <span data-ttu-id="dca8e-128">在 **“创建实体”** 对话框中，保留默认范围或者更改该范围以便应用于您想要加载的数据。</span><span class="sxs-lookup"><span data-stu-id="dca8e-128">In the **Create Entity** dialog box, leave the default range or change it to apply to the data you want to load.</span></span>  
  
6.  <span data-ttu-id="dca8e-129">不要取消选中 **“我的数据带有标题”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="dca8e-129">Do not clear the **My data has headers** check box.</span></span>  
  
7.  <span data-ttu-id="dca8e-130">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="dca8e-130">From the **Model** list, select a model.</span></span>  
  
8.  <span data-ttu-id="dca8e-131">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="dca8e-131">From the **Version** list, select a version.</span></span>  
  
9. <span data-ttu-id="dca8e-132">在 **“新的实体名称”** 框中，键入实体的名称。</span><span class="sxs-lookup"><span data-stu-id="dca8e-132">In the **New entity name** box, type a name for the entity.</span></span>  
  
10. <span data-ttu-id="dca8e-133">从 **“代码”** 列表中，选择包含唯一标识符或具有自动生成的代码的列。</span><span class="sxs-lookup"><span data-stu-id="dca8e-133">From the **Code** list, select the column that contains unique identifiers or have codes generated automatically.</span></span>  
  
11. <span data-ttu-id="dca8e-134">可选。</span><span class="sxs-lookup"><span data-stu-id="dca8e-134">Optional.</span></span> <span data-ttu-id="dca8e-135">从 **“名称”** 列表中，选择包含每个成员的名称的列。</span><span class="sxs-lookup"><span data-stu-id="dca8e-135">From the **Name** list, select a column that contains names for each member.</span></span>  
  
12. <span data-ttu-id="dca8e-136">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="dca8e-136">Click **OK**.</span></span> <span data-ttu-id="dca8e-137">在已成功创建该实体后，将显示一个新的标题行，单元将突出显示，并且工作表名称将更新以匹配该实体名称。</span><span class="sxs-lookup"><span data-stu-id="dca8e-137">When the entity has been created successfully, a new header row is displayed, the cells are highlighted, and the sheet name is updated to match the entity name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dca8e-138">后续步骤</span><span class="sxs-lookup"><span data-stu-id="dca8e-138">Next Steps</span></span>  
  
-   <span data-ttu-id="dca8e-139">若要查看发生的错误，请在 **“发布并验证”** 组中单击 **“显示状态”**。</span><span class="sxs-lookup"><span data-stu-id="dca8e-139">To view errors that occurred, in the **Publish and Validate** group, click **Show Status**.</span></span> <span data-ttu-id="dca8e-140">将显示 ValidationStatus 和 InputStatus 列。</span><span class="sxs-lookup"><span data-stu-id="dca8e-140">ValidationStatus and InputStatus columns are displayed.</span></span> <span data-ttu-id="dca8e-141">有关详细信息，请参阅[验证数据（用于 Excel 的 MDS 外接程序）](validating-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="dca8e-141">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
-   <span data-ttu-id="dca8e-142">确认属性以您期望的数据类型创建。</span><span class="sxs-lookup"><span data-stu-id="dca8e-142">Confirm that the attributes were created as the data type you expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca8e-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dca8e-143">See Also</span></span>  
 [<span data-ttu-id="dca8e-144">创建基于域的属性（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="dca8e-144">Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;</span></span>](create-a-domain-based-attribute-mds-add-in-for-excel.md)  
  
  
