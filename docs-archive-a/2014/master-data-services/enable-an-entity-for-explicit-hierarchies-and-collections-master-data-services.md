---
title: 为显式层次结构和集合启用实体 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], enabling for collections
- entities [Master Data Services], enabling for explicit hierarchies
ms.assetid: 380e77e5-ad60-43d4-9605-34a84525f5dd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a8129b3f67f050603f85ffb782a9dd209cb303fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682908"
---
# <a name="enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services"></a><span data-ttu-id="7f683-102">为显式层次结构和集合启用实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7f683-102">Enable an Entity for Explicit Hierarchies and Collections (Master Data Services)</span></span>
  <span data-ttu-id="7f683-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，为显式层次结构和集合启用一个实体，以便您可以为该实体创建显式层次结构和集合。</span><span class="sxs-lookup"><span data-stu-id="7f683-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], enable an entity for explicit hierarchies and collections so that you can create explicit hierarchies and collections for the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7f683-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="7f683-104">Prerequisites</span></span>  
 <span data-ttu-id="7f683-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="7f683-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7f683-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="7f683-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7f683-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="7f683-107">You must be a model administrator.</span></span> <span data-ttu-id="7f683-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7f683-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7f683-109">实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="7f683-109">An entity must exist.</span></span> <span data-ttu-id="7f683-110">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7f683-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-enable-an-entity-for-explicit-hierarchies-and-collections"></a><span data-ttu-id="7f683-111">为显式层次结构和集合启用实体</span><span class="sxs-lookup"><span data-stu-id="7f683-111">To enable an entity for explicit hierarchies and collections</span></span>  
  
1.  <span data-ttu-id="7f683-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="7f683-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7f683-113">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="7f683-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="7f683-114">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="7f683-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7f683-115">为您要更新的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="7f683-115">Select the row for the entity that you want to update.</span></span>  
  
5.  <span data-ttu-id="7f683-116">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="7f683-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="7f683-117">从 "**启用显式层次结构和集合**" 列表中，选择 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="7f683-117">From the **Enable explicit hierarchies and collections** list, select **Yes**.</span></span>  
  
7.  <span data-ttu-id="7f683-118">在 "**显式层次结构名称**" 框中，键入显式层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="7f683-118">In the **Explicit hierarchy name** box, type a name for an explicit hierarchy.</span></span>  
  
8.  <span data-ttu-id="7f683-119">也可以取消选中“强制的层次结构”\*\*\*\* 复选框，以便将层次结构创建为非强制的层次结构。</span><span class="sxs-lookup"><span data-stu-id="7f683-119">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="7f683-120">单击 "**保存实体**"。</span><span class="sxs-lookup"><span data-stu-id="7f683-120">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7f683-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7f683-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="7f683-122">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7f683-122">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
-   [<span data-ttu-id="7f683-123">创建集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7f683-123">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f683-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f683-124">See Also</span></span>  
 <span data-ttu-id="7f683-125">[实体 &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7f683-125">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="7f683-126">[显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7f683-126">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="7f683-127">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7f683-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
