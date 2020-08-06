---
title: 创建派生层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 20469ad30222e43a3104503cc32187c2e6512743
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689930"
---
# <a name="create-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="51449-102">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="51449-102">Create a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="51449-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您需要确保成员存在于正确级别的基于级别的层次结构时，创建派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="51449-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a derived hierarchy when you want a level-based hierarchy that ensures that members exist at the correct level.</span></span> <span data-ttu-id="51449-104">派生层次结构基于在模型中存在的基于域的属性关系。</span><span class="sxs-lookup"><span data-stu-id="51449-104">Derived hierarchies are based on the domain-based attribute relationships that exist in a model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51449-105">如果对于某一成员不存在基于域的属性值，则在派生层次结构中将不包括该成员。</span><span class="sxs-lookup"><span data-stu-id="51449-105">If a domain-based attribute value doesn't exist for a member, the member is not included in the derived hierarchy.</span></span> <span data-ttu-id="51449-106">若要获取针对所有成员的基于域的属性值，请参阅[要求属性值 (Master Data Services)](require-attribute-values-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="51449-106">See [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md) to require a domain-based attribute value for all members.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="51449-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="51449-107">Prerequisites</span></span>  
 <span data-ttu-id="51449-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="51449-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="51449-109">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="51449-109">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="51449-110">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="51449-110">You must be a model administrator.</span></span> <span data-ttu-id="51449-111">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="51449-111">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-derived-hierarchy"></a><span data-ttu-id="51449-112">创建派生层次结构</span><span class="sxs-lookup"><span data-stu-id="51449-112">To create a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="51449-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="51449-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="51449-114">在 "**模型视图**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="51449-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="51449-115">在 **“派生层次结构维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="51449-115">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="51449-116">单击 "**添加派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="51449-116">Click **Add derived hierarchy**.</span></span>  
  
5.  <span data-ttu-id="51449-117">在 **“添加派生层次结构”** 页上的 **“派生层次结构名称”** 框中，键入层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="51449-117">On the **Add Derived Hierarchy** page, in the **Derived hierarchy name** box, type a name for the hierarchy.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="51449-118">使用在层次结构中描述级别的名称，例如， **Product to Subcategory to Category**。</span><span class="sxs-lookup"><span data-stu-id="51449-118">Use a name that describes the levels in the hierarchy, for example **Product to Subcategory to Category**.</span></span>  
  
6.  <span data-ttu-id="51449-119">单击 **“保存派生层次结构”**。</span><span class="sxs-lookup"><span data-stu-id="51449-119">Click **Save derived hierarchy**.</span></span>  
  
7.  <span data-ttu-id="51449-120">在 "**编辑派生层次结构**" 页上的 "**可用实体和层次结构**" 窗格中，单击某一实体或层次结构并将其拖到 "**当前级别**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="51449-120">On the **Edit Derived Hierarchy** page, in the **Available Entities and Hierarchies** pane, click an entity or hierarchy and drag it to the **Current Levels** pane.</span></span>  
  
8.  <span data-ttu-id="51449-121">继续拖动实体或层次结构，直到完成您的层次结构。</span><span class="sxs-lookup"><span data-stu-id="51449-121">Continue dragging entities or hierarchies until your hierarchy is complete.</span></span>  
  
9. <span data-ttu-id="51449-122">单击 **“上一步”**。</span><span class="sxs-lookup"><span data-stu-id="51449-122">Click **Back**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51449-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51449-123">See Also</span></span>  
 <span data-ttu-id="51449-124">[派生层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="51449-124">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="51449-125">[具有显式大写字母 &#40;Master Data Services 的派生层次结构&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="51449-125">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="51449-126">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="51449-126">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
  
