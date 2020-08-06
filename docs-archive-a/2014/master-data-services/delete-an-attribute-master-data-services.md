---
title: 删除属性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 96db56dac9356b1131e722fc7f6b779c93305bb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682919"
---
# <a name="delete-an-attribute-master-data-services"></a><span data-ttu-id="a4cc4-102">删除属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a4cc4-102">Delete an Attribute (Master Data Services)</span></span>
  <span data-ttu-id="a4cc4-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您希望永久删除某个属性以及所有关联的属性值时，可以删除此属性。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute when you want to permanently delete the attribute and all associated attribute values.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a4cc4-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="a4cc4-104">Prerequisites</span></span>  
 <span data-ttu-id="a4cc4-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="a4cc4-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a4cc4-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a4cc4-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-107">You must be a model administrator.</span></span> <span data-ttu-id="a4cc4-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute"></a><span data-ttu-id="a4cc4-109">删除属性</span><span class="sxs-lookup"><span data-stu-id="a4cc4-109">To delete an attribute</span></span>  
  
1.  <span data-ttu-id="a4cc4-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a4cc4-111">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="a4cc4-112">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="a4cc4-113">为包含您要删除的属性的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-113">Select the row for the entity that contains the attribute you want to delete.</span></span>  
  
5.  <span data-ttu-id="a4cc4-114">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="a4cc4-115">在 "**编辑实体**" 页上，单击要删除的属性。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-115">On the **Edit Entity** page, click the attribute you want to delete.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4cc4-116">不能删除 Name 或 Code 属性。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-116">You cannot delete the Name or Code attributes.</span></span>  
  
7.  <span data-ttu-id="a4cc4-117">单击 "**删除所选属性**"。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-117">Click **Delete selected attribute**.</span></span>  
  
8.  <span data-ttu-id="a4cc4-118">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-118">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="a4cc4-119">在附加确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="a4cc4-119">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cc4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4cc4-120">See Also</span></span>  
 <span data-ttu-id="a4cc4-121">[属性 &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a4cc4-121">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="a4cc4-122">[基于域的属性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a4cc4-122">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="a4cc4-123">[Master Data Services 创建文本属性 &#40;&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a4cc4-123">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="a4cc4-124">创建基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a4cc4-124">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
