---
title: 创建合并成员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c41673f6f3bf1f4de2a831ecd659321b273b6af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690678"
---
# <a name="create-a-consolidated-member-master-data-services"></a><span data-ttu-id="ac3ec-102">创建合并成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ac3ec-102">Create a Consolidated Member (Master Data Services)</span></span>
  <span data-ttu-id="ac3ec-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]在中，在您想要显式层次结构的父节点时创建合并成员。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a consolidated member when you want a parent node for an explicit hierarchy.</span></span> <span data-ttu-id="ac3ec-104">合并成员可以具有其自己的属性。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-104">Consolidated members can have their own attributes.</span></span> <span data-ttu-id="ac3ec-105">它们用于分组。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-105">They are used for grouping.</span></span> <span data-ttu-id="ac3ec-106">如以下示例中所示，合并成员可用于其下具有帐户的帐户组。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-106">As shown in the following example, consolidated members can be used for account groups that have accounts under them.</span></span>

 <span data-ttu-id="ac3ec-107">![MDS 合并成员](../../2014/master-data-services/media/mds-consolidated-members.png "MDS 合并成员")</span><span class="sxs-lookup"><span data-stu-id="ac3ec-107">![MDS Consolidated Members](../../2014/master-data-services/media/mds-consolidated-members.png "MDS Consolidated Members")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac3ec-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="ac3ec-108">Prerequisites</span></span>
 <span data-ttu-id="ac3ec-109">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="ac3ec-109">To perform this procedure:</span></span>

-   <span data-ttu-id="ac3ec-110">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-110">You must have permission to access the **Explorer** functional area.</span></span>

-   <span data-ttu-id="ac3ec-111">\*\*\*\* 对于您要将成员添加到的实体的合并模型对象，您必须至少具有“更新”权限。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-111">You must have a minimum of **Update** permission to the consolidated model object for the entity you are adding a member to.</span></span>

### <a name="to-create-a-consolidated-member"></a><span data-ttu-id="ac3ec-112">创建合并成员</span><span class="sxs-lookup"><span data-stu-id="ac3ec-112">To create a consolidated member</span></span>

1.  <span data-ttu-id="ac3ec-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>

2.  <span data-ttu-id="ac3ec-114">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-114">From the **Version** list, select a version.</span></span>

3.  <span data-ttu-id="ac3ec-115">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-115">Click **Explorer**.</span></span>

4.  <span data-ttu-id="ac3ec-116">\*\*\*\* 从菜单栏中，指向“层次结构”，然后单击您要将合并成员添加到的层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-116">From the menu bar, point to **Hierarchies** and click the name of the hierarchy you want to add a consolidated member to.</span></span>

5.  <span data-ttu-id="ac3ec-117">\*\*\*\* 在网格上方，选择 **“合并成员”** 或“层次结构中的所有合并成员”选项。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-117">Above the grid, select either the **Consolidated members** or the **All consolidated members in hierarchy** option.</span></span>

6.  <span data-ttu-id="ac3ec-118">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-118">Click **Add**.</span></span>

7.  <span data-ttu-id="ac3ec-119">在右侧窗格中，填写字段。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-119">In the pane on the right, complete the fields.</span></span>

8.  <span data-ttu-id="ac3ec-120">可选。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-120">Optional.</span></span> <span data-ttu-id="ac3ec-121">\*\*\*\* 在“批注”框中，键入有关添加成员原因的注释。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-121">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="ac3ec-122">有权访问成员的所有用户都可以查看批注。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-122">All users who have access to the member can view the annotation.</span></span>

9. <span data-ttu-id="ac3ec-123">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ac3ec-123">Click **OK**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ac3ec-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ac3ec-124">Next Steps</span></span>

-   [<span data-ttu-id="ac3ec-125">在层次结构中移动 &#40;Master Data Services 的成员&#41;</span><span class="sxs-lookup"><span data-stu-id="ac3ec-125">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a><span data-ttu-id="ac3ec-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac3ec-126">See Also</span></span>
 <span data-ttu-id="ac3ec-127">[创建显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [创建叶成员 &#40;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) Master Data Services[使用过渡过程](add-update-and-delete-data-master-data-services.md)[成员](../../2014/master-data-services/members-master-data-services.md)&#41;Master Data Services &#40;Master Data Services[显式层次结构](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)&#41;&#40;Master Data Services</span><span class="sxs-lookup"><span data-stu-id="ac3ec-127">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [Create a Leaf Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) [Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) [Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)</span></span>


