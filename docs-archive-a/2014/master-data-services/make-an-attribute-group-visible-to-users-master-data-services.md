---
title: 使属性组对用户可见 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 309ad0392cd717d4a8a11470621144ef9e604fd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576869"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a><span data-ttu-id="0eede-102">使属性组对用户可见 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0eede-102">Make an Attribute Group Visible to Users (Master Data Services)</span></span>
  <span data-ttu-id="0eede-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您想要用户在 **“资源管理器”** 功能区域中将选项卡置于网格上方时，使属性组对于用户或组是可见的。</span><span class="sxs-lookup"><span data-stu-id="0eede-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], make an attribute group visible to users or groups when you want users to have tabs above the grid in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="0eede-104">创建属性组时，对除创建者之外的所有用户自动隐藏它。</span><span class="sxs-lookup"><span data-stu-id="0eede-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0eede-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="0eede-105">Prerequisites</span></span>  
 <span data-ttu-id="0eede-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="0eede-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="0eede-107">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="0eede-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="0eede-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="0eede-108">You must be a model administrator.</span></span> <span data-ttu-id="0eede-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0eede-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="0eede-110">必须至少存在一个属性组。</span><span class="sxs-lookup"><span data-stu-id="0eede-110">At least one attribute group must exist.</span></span> <span data-ttu-id="0eede-111">有关详细信息，请参阅 [创建属性组 (Master Data Services)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0eede-111">For more information, see [Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md).</span></span>  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a><span data-ttu-id="0eede-112">使属性组对用户可见</span><span class="sxs-lookup"><span data-stu-id="0eede-112">To make an attribute group visible to users</span></span>  
  
1.  <span data-ttu-id="0eede-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="0eede-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="0eede-114">在 "**模型视图**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**属性组**"。</span><span class="sxs-lookup"><span data-stu-id="0eede-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="0eede-115">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="0eede-115">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="0eede-116">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="0eede-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="0eede-117">单击加号以展开 "**叶组**"、"**合并组**" 或 "**集合组**"，具体取决于要使其可见的组类型。</span><span class="sxs-lookup"><span data-stu-id="0eede-117">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to make visible.</span></span>  
  
6.  <span data-ttu-id="0eede-118">单击加号以便展开要使其可见的组。</span><span class="sxs-lookup"><span data-stu-id="0eede-118">Click the plus sign to expand the group you want to make visible.</span></span>  
  
7.  <span data-ttu-id="0eede-119">单击 "**用户**" 或 "**组**"，具体取决于是否要使组对用户或组可见。</span><span class="sxs-lookup"><span data-stu-id="0eede-119">Click either **Users** or **Groups**, depending on whether you are making the group visible to a user or a group.</span></span>  
  
8.  <span data-ttu-id="0eede-120">单击 "**编辑所选项**"。</span><span class="sxs-lookup"><span data-stu-id="0eede-120">Click **Edit selected item**.</span></span>  
  
9. <span data-ttu-id="0eede-121">单击 "**可用**" 框中的 "用户或组"，然后单击 "**添加**" 箭头。</span><span class="sxs-lookup"><span data-stu-id="0eede-121">Click users or groups in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="0eede-122">若要全部添加，请单击 **“全部添加”** 箭头。</span><span class="sxs-lookup"><span data-stu-id="0eede-122">To add all, click the **Add All** arrow.</span></span>  
  
10. <span data-ttu-id="0eede-123">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="0eede-123">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eede-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0eede-124">See Also</span></span>  
 <span data-ttu-id="0eede-125">[属性组 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0eede-125">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="0eede-126">创建属性组 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0eede-126">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
