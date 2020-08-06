---
title: 排除业务规则 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 317964dcbc7b2cbe212c415b3aa4f9f1a0743301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689493"
---
# <a name="exclude-a-business-rule-master-data-services"></a><span data-ttu-id="a2d0d-102">排除业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a2d0d-102">Exclude a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="a2d0d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，如果您不希望永久删除业务规则，而又不希望针对此规则验证数据，则可以排除该规则。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclude a business rule when you do not want to delete the rule permanently, but you do not want to validate data against it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a2d0d-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="a2d0d-104">Prerequisites</span></span>  
 <span data-ttu-id="a2d0d-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="a2d0d-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a2d0d-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a2d0d-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-107">You must be a model administrator.</span></span> <span data-ttu-id="a2d0d-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-exclude-a-business-rule"></a><span data-ttu-id="a2d0d-109">排除业务规则</span><span class="sxs-lookup"><span data-stu-id="a2d0d-109">To exclude a business rule</span></span>  
  
1.  <span data-ttu-id="a2d0d-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a2d0d-111">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-111">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="a2d0d-112">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-112">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a2d0d-113">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-113">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="a2d0d-114">从 "**成员类型**" 列表中，选择成员的类型。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-114">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="a2d0d-115">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-115">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="a2d0d-116">在网格中的业务规则行中，选中 "**排除**" 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-116">In the grid, in the row for the business rule, select the check box in the **Exclude** column.</span></span> <span data-ttu-id="a2d0d-117">"**状态**" 列中的值为 "**排除待定**"。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-117">The value in the **Status** column is **Exclusion pending**.</span></span>  
  
8.  <span data-ttu-id="a2d0d-118">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-118">Click **Publish business rules**.</span></span>  
  
9. <span data-ttu-id="a2d0d-119">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-119">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="a2d0d-120">"**状态**" 列中的值已**排除**。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-120">The value in the **Status** column is **Excluded**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d0d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2d0d-121">See Also</span></span>  
 <span data-ttu-id="a2d0d-122">[删除业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2d0d-122">[Delete a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="a2d0d-123">[创建和发布业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a2d0d-123">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="a2d0d-124">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a2d0d-124">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
