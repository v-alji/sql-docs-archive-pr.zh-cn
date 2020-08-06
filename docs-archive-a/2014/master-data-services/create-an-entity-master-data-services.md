---
title: 创建实体 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7cefdedd07ee248f12b3b17337878934a2b1aa84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590887"
---
# <a name="create-an-entity-master-data-services"></a><span data-ttu-id="d47ed-102">创建实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d47ed-102">Create an Entity (Master Data Services)</span></span>
  <span data-ttu-id="d47ed-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建一个实体以便包含成员及其属性。</span><span class="sxs-lookup"><span data-stu-id="d47ed-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an entity to contain members and their attributes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d47ed-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="d47ed-104">Prerequisites</span></span>  
 <span data-ttu-id="d47ed-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d47ed-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d47ed-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="d47ed-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="d47ed-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="d47ed-107">You must be a model administrator.</span></span> <span data-ttu-id="d47ed-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d47ed-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d47ed-109">模型必须存在。</span><span class="sxs-lookup"><span data-stu-id="d47ed-109">A model must exist.</span></span> <span data-ttu-id="d47ed-110">有关详细信息，请参阅[创建模型 (Master Data Services)](../../2014/master-data-services/create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d47ed-110">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-an-entity"></a><span data-ttu-id="d47ed-111">创建实体</span><span class="sxs-lookup"><span data-stu-id="d47ed-111">To create an entity</span></span>  
  
1.  <span data-ttu-id="d47ed-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="d47ed-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="d47ed-113">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="d47ed-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="d47ed-114">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="d47ed-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="d47ed-115">单击 "**添加实体**"。</span><span class="sxs-lookup"><span data-stu-id="d47ed-115">Click **Add entity**.</span></span>  
  
5.  <span data-ttu-id="d47ed-116">在 "**实体名称**" 框中，键入实体的名称。</span><span class="sxs-lookup"><span data-stu-id="d47ed-116">In the **Entity name** box, type the name of the entity.</span></span>  
  
6.  <span data-ttu-id="d47ed-117">在 "**临时表的名称**" 框中，键入临时表的名称。</span><span class="sxs-lookup"><span data-stu-id="d47ed-117">In the **Name for staging tables** box, type a name for the staging table.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d47ed-118">使用模型名称作为临时表名称的一部分，例如 Modelname_Entityname\*\*。</span><span class="sxs-lookup"><span data-stu-id="d47ed-118">Use the model name as part of the staging table name, for example *Modelname_Entityname*.</span></span> <span data-ttu-id="d47ed-119">这便于在数据库中查找表。</span><span class="sxs-lookup"><span data-stu-id="d47ed-119">This makes the tables easier to find in the database.</span></span> <span data-ttu-id="d47ed-120">有关临时表的详细信息，请参阅[数据导入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d47ed-120">For more information about the staging tables, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
7.  <span data-ttu-id="d47ed-121">可选。</span><span class="sxs-lookup"><span data-stu-id="d47ed-121">Optional.</span></span> <span data-ttu-id="d47ed-122">选中 **“自动创建代码值”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="d47ed-122">Select the **Create Code values automatically** check box.</span></span> <span data-ttu-id="d47ed-123">有关详细信息，请参阅[&#41;&#40;Master Data Services 自动创建代码](../../2014/master-data-services/automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d47ed-123">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="d47ed-124">从 "**启用显式层次结构和集合**" 列表中，选择下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="d47ed-124">From the **Enable explicit hierarchies and collections** list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="d47ed-125">“否”。</span><span class="sxs-lookup"><span data-stu-id="d47ed-125">**No**.</span></span> <span data-ttu-id="d47ed-126">如果您无需为显式层次结构和集合启用实体，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="d47ed-126">Select this option if you do not need to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="d47ed-127">您可以根据需要在以后更改此项。</span><span class="sxs-lookup"><span data-stu-id="d47ed-127">You can change this later if needed.</span></span>  
  
    -   <span data-ttu-id="d47ed-128">**是**</span><span class="sxs-lookup"><span data-stu-id="d47ed-128">**Yes**.</span></span> <span data-ttu-id="d47ed-129">如果您想要为显式层次结构和集合启用实体，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="d47ed-129">Select this option when you want to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="d47ed-130">在 "**显式层次结构名称**" 框中，键入名称。</span><span class="sxs-lookup"><span data-stu-id="d47ed-130">In the **Explicit hierarchy name** box, type a name.</span></span> <span data-ttu-id="d47ed-131">（可选）选择 "**必需层次结构" (包括所有叶成员**，使显式层次结构成为强制层次结构。</span><span class="sxs-lookup"><span data-stu-id="d47ed-131">Optionally, select **Mandatory hierarchy (all leaf members are included** to make the explicit hierarchy a mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="d47ed-132">单击 "**保存实体**"。</span><span class="sxs-lookup"><span data-stu-id="d47ed-132">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d47ed-133">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d47ed-133">Next Steps</span></span>  
  
-   [<span data-ttu-id="d47ed-134">创建文本属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d47ed-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="d47ed-135">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d47ed-135">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="d47ed-136">创建文件属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d47ed-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d47ed-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d47ed-137">See Also</span></span>  
 <span data-ttu-id="d47ed-138">[实体 &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d47ed-138">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="d47ed-139">[显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d47ed-139">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="d47ed-140">[更改实体名称 &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d47ed-140">[Change an Entity Name &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="d47ed-141">删除实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d47ed-141">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
