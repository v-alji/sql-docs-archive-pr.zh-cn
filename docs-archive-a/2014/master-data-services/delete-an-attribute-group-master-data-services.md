---
title: 删除属性组 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 833c5cf327034b25d68af123a1fc134372bd6f10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590884"
---
# <a name="delete-an-attribute-group-master-data-services"></a><span data-ttu-id="80326-102">删除属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="80326-102">Delete an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="80326-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您不再需要在 **的** “资源管理器” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中显示属性组选项卡时，可以删除属性组。</span><span class="sxs-lookup"><span data-stu-id="80326-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute group when you no longer need the tab to display in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="80326-104">**注意** 存在属性组时，不属于属性组的属性将不在 **“资源管理器”** 中显示。</span><span class="sxs-lookup"><span data-stu-id="80326-104">**Note** When attribute groups exist, attributes that do not belong to an attribute group are not displayed in **Explorer**.</span></span> <span data-ttu-id="80326-105">不存在属性组时，显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="80326-105">When no attribute groups exist, all attributes are displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="80326-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="80326-106">Prerequisites</span></span>  
 <span data-ttu-id="80326-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="80326-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="80326-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="80326-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="80326-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="80326-109">You must be a model administrator.</span></span> <span data-ttu-id="80326-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="80326-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute-group"></a><span data-ttu-id="80326-111">删除属性组</span><span class="sxs-lookup"><span data-stu-id="80326-111">To delete an attribute group</span></span>  
  
1.  <span data-ttu-id="80326-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="80326-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="80326-113">在 "**模型视图**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**属性组**"。</span><span class="sxs-lookup"><span data-stu-id="80326-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="80326-114">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="80326-114">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="80326-115">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="80326-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="80326-116">单击加号以展开 "**叶组**"、"**合并组**" 或 "**集合组**"，具体取决于要删除的组的类型。</span><span class="sxs-lookup"><span data-stu-id="80326-116">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to delete.</span></span>  
  
6.  <span data-ttu-id="80326-117">单击您要删除的属性组。</span><span class="sxs-lookup"><span data-stu-id="80326-117">Click the attribute group you want to delete.</span></span>  
  
7.  <span data-ttu-id="80326-118">单击 "**删除所选组**"。</span><span class="sxs-lookup"><span data-stu-id="80326-118">Click **Delete selected group**.</span></span>  
  
8.  <span data-ttu-id="80326-119">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="80326-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="80326-120">在附加确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="80326-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80326-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80326-121">See Also</span></span>  
 <span data-ttu-id="80326-122">[属性组 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="80326-122">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="80326-123">创建属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="80326-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
