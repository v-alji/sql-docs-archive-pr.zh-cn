---
title: 更改显式层次结构名称 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, changing name
ms.assetid: 12991603-474e-4042-b160-b1f7979694b1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3cb8d1108650395ebd970edbb2ea31f5daebbd27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691772"
---
# <a name="change-an-explicit-hierarchy-name-master-data-services"></a><span data-ttu-id="f38b6-102">更改显式层次结构名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f38b6-102">Change an Explicit Hierarchy Name (Master Data Services)</span></span>
  <span data-ttu-id="f38b6-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以更改显式层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="f38b6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an explicit hierarchy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f38b6-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="f38b6-104">Prerequisites</span></span>  
 <span data-ttu-id="f38b6-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="f38b6-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f38b6-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="f38b6-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f38b6-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="f38b6-107">You must be a model administrator.</span></span> <span data-ttu-id="f38b6-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f38b6-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-an-explicit-hierarchy"></a><span data-ttu-id="f38b6-109">更改显式层次结构名称</span><span class="sxs-lookup"><span data-stu-id="f38b6-109">To change the name of an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="f38b6-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="f38b6-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f38b6-111">在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。</span><span class="sxs-lookup"><span data-stu-id="f38b6-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="f38b6-112">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="f38b6-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f38b6-113">选择包含您要重命名的显式层次结构的实体所对应的行。</span><span class="sxs-lookup"><span data-stu-id="f38b6-113">Select the row for the entity that contains the explicit hierarchy you want to rename.</span></span>  
  
5.  <span data-ttu-id="f38b6-114">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="f38b6-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="f38b6-115">在 "**编辑实体**" 页上，单击要重命名的显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="f38b6-115">On the **Edit Entity** page, click the explicit hierarchy you want to rename.</span></span>  
  
7.  <span data-ttu-id="f38b6-116">单击 "**编辑所选层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="f38b6-116">Click **Edit selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="f38b6-117">在 "**显式层次结构名称**" 框中，键入更新后的层次结构名称。</span><span class="sxs-lookup"><span data-stu-id="f38b6-117">In the **Explicit hierarchy name** box, type the updated name of the hierarchy.</span></span>  
  
9. <span data-ttu-id="f38b6-118">单击 "**保存层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="f38b6-118">Click **Save hierarchy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38b6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f38b6-119">See Also</span></span>  
 <span data-ttu-id="f38b6-120">[显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f38b6-120">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="f38b6-121">[创建显式层次结构 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f38b6-121">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="f38b6-122">删除显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f38b6-122">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)  
  
  
