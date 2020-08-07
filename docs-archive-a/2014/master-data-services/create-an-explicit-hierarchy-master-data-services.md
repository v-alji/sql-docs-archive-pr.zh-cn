---
title: 创建显式层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aebf95e68f210fe5a573aed092231670c10fa188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588579"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="2a6dd-102">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2a6dd-102">Create an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="2a6dd-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您需要其成员可在任何级别存在的不规则层次结构时，创建显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an explicit hierarchy when you need a ragged hierarchy in which members can exist at any level.</span></span> <span data-ttu-id="2a6dd-104">显式层次结构包含来自单个实体的成员。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-104">Explicit hierarchies contain members from a single entity.</span></span>  
  
 <span data-ttu-id="2a6dd-105">创建显式层次结构后，可以在 **“资源管理器”** 功能区域中为该层次结构添加成员。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-105">After you create an explicit hierarchy, you can add members to it in the **Explorer** functional area.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2a6dd-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="2a6dd-106">Prerequisites</span></span>  
 <span data-ttu-id="2a6dd-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="2a6dd-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2a6dd-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2a6dd-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-109">You must be a model administrator.</span></span> <span data-ttu-id="2a6dd-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="2a6dd-111">必须为显式层次结构和集合启用了实体。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-111">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="2a6dd-112">有关详细信息，请参阅为[显式层次结构和集合启用实体 &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-112">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-an-explicit-hierarchy"></a><span data-ttu-id="2a6dd-113">创建显式层次结构</span><span class="sxs-lookup"><span data-stu-id="2a6dd-113">To create an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="2a6dd-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2a6dd-115">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="2a6dd-116">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2a6dd-117">为您要为其创建显式层次结构的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-117">Select the row for the entity that you want to create an explicit hierarchy for.</span></span>  
  
5.  <span data-ttu-id="2a6dd-118">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="2a6dd-119">在 "**编辑实体**" 页上的 "**显式层次结构**" 窗格中，单击 "**添加显式层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-119">On the **Edit Entity** page, in the **Explicit hierarchies** pane, click **Add explicit hierarchy**.</span></span>  
  
7.  <span data-ttu-id="2a6dd-120">在 "**添加显式层次结构**" 页上的 "**显式层次结构名称**" 框中，键入层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-120">On the **Add Explicit Hierarchy** page, in the **Explicit hierarchy name** box, type a name for the hierarchy.</span></span>  
  
8.  <span data-ttu-id="2a6dd-121">也可以取消选中“强制的层次结构”\*\*\*\* 复选框，以便将层次结构创建为非强制的层次结构。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-121">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span> <span data-ttu-id="2a6dd-122">有关层次结构类型的详细信息，请参阅 [显式层次结构 (Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-122">For more information about hierarchy types, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="2a6dd-123">单击 "**保存层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-123">Click **Save hierarchy**.</span></span>  
  
10. <span data-ttu-id="2a6dd-124">在 "**编辑实体**" 页上，单击 "**保存实体**"。</span><span class="sxs-lookup"><span data-stu-id="2a6dd-124">On the **Edit Entity** page, click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2a6dd-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2a6dd-125">Next Steps</span></span>  
  
-   [<span data-ttu-id="2a6dd-126">创建合并成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2a6dd-126">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [<span data-ttu-id="2a6dd-127">在层次结构中移动 &#40;Master Data Services 的成员&#41;</span><span class="sxs-lookup"><span data-stu-id="2a6dd-127">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="2a6dd-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a6dd-128">See Also</span></span>  
 <span data-ttu-id="2a6dd-129">[显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2a6dd-129">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="2a6dd-130">[具有显式大写字母 &#40;Master Data Services 的派生层次结构&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2a6dd-130">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="2a6dd-131">更改显式层次结构名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2a6dd-131">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
