---
title: 更改业务规则名称 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], changing name
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0e99047ffe27332aaed4514394ca2357942a1297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591462"
---
# <a name="change-a-business-rule-name-master-data-services"></a><span data-ttu-id="c7862-102">更改业务规则名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c7862-102">Change a Business Rule Name (Master Data Services)</span></span>
  <span data-ttu-id="c7862-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当分配的业务规则名称不能满足您的业务需要时，可以更改此名称。</span><span class="sxs-lookup"><span data-stu-id="c7862-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], change a business rule name when the name assigned does not meet your business needs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7862-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="c7862-104">Prerequisites</span></span>  
 <span data-ttu-id="c7862-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="c7862-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c7862-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="c7862-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="c7862-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="c7862-107">You must be a model administrator.</span></span> <span data-ttu-id="c7862-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c7862-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c7862-109">业务规则必须存在。</span><span class="sxs-lookup"><span data-stu-id="c7862-109">A business rule must exist.</span></span> <span data-ttu-id="c7862-110">有关详细信息，请参阅[创建和发布业务规则 (Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c7862-110">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-a-business-rule"></a><span data-ttu-id="c7862-111">更改业务规则的名称</span><span class="sxs-lookup"><span data-stu-id="c7862-111">To change the name of a business rule</span></span>  
  
1.  <span data-ttu-id="c7862-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="c7862-113">从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="c7862-114">在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="c7862-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="c7862-115">从 **“实体”** 列表中，选择某一实体。</span><span class="sxs-lookup"><span data-stu-id="c7862-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="c7862-116">从 "**成员类型**" 列表中，选择成员的类型。</span><span class="sxs-lookup"><span data-stu-id="c7862-116">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="c7862-117">从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="c7862-118">在网格中的业务规则行中，双击 "**名称**" 字段。</span><span class="sxs-lookup"><span data-stu-id="c7862-118">In the grid, in the row for the business rule, double-click the **Name** field.</span></span>  
  
8.  <span data-ttu-id="c7862-119">为业务规则键入名称。</span><span class="sxs-lookup"><span data-stu-id="c7862-119">Type a name for the business rule.</span></span>  
  
9. <span data-ttu-id="c7862-120">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="c7862-120">Press ENTER.</span></span>  
  
10. <span data-ttu-id="c7862-121">单击 **“发布业务规则”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-121">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="c7862-122">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-122">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="c7862-123">规则的状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="c7862-123">The rule's status changes to **Active**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7862-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7862-124">See Also</span></span>  
 [<span data-ttu-id="c7862-125">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c7862-125">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
