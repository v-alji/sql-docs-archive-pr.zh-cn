---
title: 更改属性名称 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abbe5f666daed42b25b46f02e954343b57446145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690687"
---
# <a name="change-an-attribute-name-master-data-services"></a><span data-ttu-id="8589d-102">更改属性名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8589d-102">Change an Attribute Name (Master Data Services)</span></span>
  <span data-ttu-id="8589d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以更改属性的名称。</span><span class="sxs-lookup"><span data-stu-id="8589d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an attribute.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8589d-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="8589d-104">Prerequisites</span></span>  
 <span data-ttu-id="8589d-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="8589d-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8589d-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="8589d-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="8589d-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="8589d-107">You must be a model administrator.</span></span> <span data-ttu-id="8589d-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8589d-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-attribute-name"></a><span data-ttu-id="8589d-109">更改属性名称</span><span class="sxs-lookup"><span data-stu-id="8589d-109">To change an attribute name</span></span>  
  
1.  <span data-ttu-id="8589d-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="8589d-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="8589d-111">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="8589d-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="8589d-112">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="8589d-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="8589d-113">单击包含您要更改其名称的属性的实体所在行。</span><span class="sxs-lookup"><span data-stu-id="8589d-113">Click the row for the entity that contains the attribute with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="8589d-114">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="8589d-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="8589d-115">在 "**编辑实体**" 页上，单击要更改其名称的属性。</span><span class="sxs-lookup"><span data-stu-id="8589d-115">On the **Edit Entity** page, click the attribute with the name you want to change.</span></span>  
  
7.  <span data-ttu-id="8589d-116">单击 "**编辑所选属性**"。</span><span class="sxs-lookup"><span data-stu-id="8589d-116">Click **Edit selected attribute**.</span></span>  
  
8.  <span data-ttu-id="8589d-117">在 **“名称”** 框中，键入属性的新名称。</span><span class="sxs-lookup"><span data-stu-id="8589d-117">In the **Name** box, type the updated name of the attribute.</span></span> <span data-ttu-id="8589d-118">有关不可用作属性名称的单词列表，请参阅[保留字 (Master Data Services)](reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8589d-118">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="8589d-119">单击 **“保存属性”**。</span><span class="sxs-lookup"><span data-stu-id="8589d-119">Click **Save attribute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8589d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8589d-120">See Also</span></span>  
 <span data-ttu-id="8589d-121">[Master Data Services 创建文本属性 &#40;&#41;](create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8589d-121">[Create a Text Attribute &#40;Master Data Services&#41;](create-a-text-attribute-master-data-services.md) </span></span>  
 <span data-ttu-id="8589d-122">[删除属性 &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8589d-122">[Delete an Attribute &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="8589d-123">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8589d-123">Attributes &#40;Master Data Services&#41;</span></span>](attributes-master-data-services.md)  
  
  
