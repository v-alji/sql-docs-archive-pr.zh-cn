---
title: 删除业务规则 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8e6db486f71634cf025c57eabbedeeb9efdbc437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682917"
---
# <a name="delete-a-business-rule-master-data-services"></a><span data-ttu-id="735b7-102">删除业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="735b7-102">Delete a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="735b7-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当不再需要某个业务规则时，可以删除它。</span><span class="sxs-lookup"><span data-stu-id="735b7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a business rule when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="735b7-104">您可以通过排除业务规则而不是删除它来防止针对业务规则验证数据。</span><span class="sxs-lookup"><span data-stu-id="735b7-104">You can prevent data from being validated against a business rule by excluding it, rather than deleting it.</span></span> <span data-ttu-id="735b7-105">有关详细信息，请参阅 [排除业务规则 (Master Data Services)](exclude-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="735b7-105">For more information, see [Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="735b7-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="735b7-106">Prerequisites</span></span>  
 <span data-ttu-id="735b7-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="735b7-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="735b7-108">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="735b7-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="735b7-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="735b7-109">You must be a model administrator.</span></span> <span data-ttu-id="735b7-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="735b7-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-business-rule"></a><span data-ttu-id="735b7-111">删除业务规则</span><span class="sxs-lookup"><span data-stu-id="735b7-111">To delete a business rule</span></span>  
  
1.  <span data-ttu-id="735b7-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="735b7-113">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="735b7-114">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="735b7-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="735b7-115">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="735b7-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="735b7-116">从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。</span><span class="sxs-lookup"><span data-stu-id="735b7-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="735b7-117">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="735b7-118">在网格中，单击要删除的业务规则所对应的行。</span><span class="sxs-lookup"><span data-stu-id="735b7-118">In the grid, click the row for the business rule you want to delete.</span></span>  
  
8.  <span data-ttu-id="735b7-119">单击 "**删除所选业务规则**"。</span><span class="sxs-lookup"><span data-stu-id="735b7-119">Click **Delete selected business rule**.</span></span>  
  
9. <span data-ttu-id="735b7-120">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-120">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="735b7-121">"**状态**" 列中的值为 "**待删除**"。</span><span class="sxs-lookup"><span data-stu-id="735b7-121">The value in the **Status** column is **Deletion pending**.</span></span>  
  
10. <span data-ttu-id="735b7-122">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-122">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="735b7-123">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="735b7-123">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="735b7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="735b7-124">See Also</span></span>  
 <span data-ttu-id="735b7-125">[排除业务规则 &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="735b7-125">[Exclude a Business Rule &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="735b7-126">[创建和发布业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="735b7-126">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="735b7-127">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="735b7-127">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
