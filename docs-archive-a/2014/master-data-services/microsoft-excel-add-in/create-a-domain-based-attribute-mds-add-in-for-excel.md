---
title: 创建基于域的属性 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bda0c7f63ad380aaea5d980d2e729822ec9a3d22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576867"
---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a><span data-ttu-id="7eaad-102">创建基于域的属性（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="7eaad-102">Create a Domain-based Attribute (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="7eaad-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，管理员在想要将列中的值限制为一组特定值时可以创建基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="7eaad-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create a domain-based attribute when they want to constrain the values in a column to a specific set of values.</span></span>  
  
 <span data-ttu-id="7eaad-104">这些值可以已处于工作表中，也可以来自某一现有实体。</span><span class="sxs-lookup"><span data-stu-id="7eaad-104">The values can already be in the worksheet or they can come from an existing entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7eaad-105"> 如果用户在该约束列键入某个值，而不是从列表中进行选择，则错误在发布时将显示在 **$InputStatus$** 列中。</span><span class="sxs-lookup"><span data-stu-id="7eaad-105">If users type a value in the constrained column, rather than selecting from the list, errors are displayed in the **$InputStatus$** column when they publish.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7eaad-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="7eaad-106">Prerequisites</span></span>  
 <span data-ttu-id="7eaad-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="7eaad-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7eaad-108">您必须有权访问 **“系统管理”** 功能区域和 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="7eaad-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="7eaad-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="7eaad-109">You must be a model administrator.</span></span> <span data-ttu-id="7eaad-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7eaad-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7eaad-111">模型和实体必须已经存在。</span><span class="sxs-lookup"><span data-stu-id="7eaad-111">The model and entity must already exist.</span></span>  
  
### <a name="to-perform-this-procedure"></a><span data-ttu-id="7eaad-112">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="7eaad-112">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="7eaad-113">在 Excel 中，加载包含要约束的列（属性）的实体。</span><span class="sxs-lookup"><span data-stu-id="7eaad-113">In Excel, load the entity that contains the column (attribute) you want to constrain.</span></span> <span data-ttu-id="7eaad-114">有关详细信息，请参阅将[数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="7eaad-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="7eaad-115">单击要约束的列中的任意单元。</span><span class="sxs-lookup"><span data-stu-id="7eaad-115">Click any cell in the column you want to constrain.</span></span>  
  
3.  <span data-ttu-id="7eaad-116">在 **“生成模型”** 组中，单击 **“特性属性”**。</span><span class="sxs-lookup"><span data-stu-id="7eaad-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="7eaad-117">在“特性属性”\*\*\*\* 对话框的“属性类型”\*\*\*\* 列表中，选择“约束列表(基于域)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7eaad-117">In the **Attribute Properties** dialog box, in the **Attribute type** list, choose **Constrained list (domain-based)**.</span></span>  
  
5.  <span data-ttu-id="7eaad-118">在 **“使用以下位置的值填充属性”** 列表中：</span><span class="sxs-lookup"><span data-stu-id="7eaad-118">In the **Populate the attribute with values from** list:</span></span>  
  
    -   <span data-ttu-id="7eaad-119">若要使用工作表中的值，请选择 **“所选列”**。</span><span class="sxs-lookup"><span data-stu-id="7eaad-119">To use values from the worksheet, choose **the selected column**.</span></span> <span data-ttu-id="7eaad-120">将使用所选列中的值创建新实体和新的临时表。</span><span class="sxs-lookup"><span data-stu-id="7eaad-120">A new entity and new staging table will be created with the values from the selected column.</span></span>  
  
    -   <span data-ttu-id="7eaad-121">若要使用现有实体中的值，请选择该实体的名称。</span><span class="sxs-lookup"><span data-stu-id="7eaad-121">To use values from an existing entity, choose the name of the entity.</span></span>  
  
6.  <span data-ttu-id="7eaad-122">如果您在前一步骤中选择 **“所选列”** ，则在 **“新实体名称”** 框中键入新实体的名称。</span><span class="sxs-lookup"><span data-stu-id="7eaad-122">If you chose **the selected column** in the previous step, in the **New entity name** box, type a name for the new entity.</span></span> <span data-ttu-id="7eaad-123">该名称可与列（属性）名称相同。</span><span class="sxs-lookup"><span data-stu-id="7eaad-123">This can be the same as the column (attribute) name.</span></span>  
  
7.  <span data-ttu-id="7eaad-124">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7eaad-124">Click **OK**.</span></span> <span data-ttu-id="7eaad-125">列中的每个单元现在都有一个可供用户从中选择的值列表。</span><span class="sxs-lookup"><span data-stu-id="7eaad-125">Each cell in the column now has a list of values for users to choose from.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7eaad-126">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7eaad-126">Next Steps</span></span>  
  
-   <span data-ttu-id="7eaad-127">若要在约束列表中添加和删除值，请加载属性基于的实体。</span><span class="sxs-lookup"><span data-stu-id="7eaad-127">To add and delete values in the constrained list, load the entity that the attribute is based on.</span></span> <span data-ttu-id="7eaad-128">有关加载实体的详细信息，请参阅将[数据从 MDS 加载到 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="7eaad-128">For more information on loading entities, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eaad-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7eaad-129">See Also</span></span>  
 <span data-ttu-id="7eaad-130">[基于域的属性 &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7eaad-130">[Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="7eaad-131">[创建实体 &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="7eaad-131">[Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="7eaad-132">生成模型（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="7eaad-132">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
