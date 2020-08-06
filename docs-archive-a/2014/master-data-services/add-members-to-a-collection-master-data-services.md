---
title: 将成员添加到集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], adding members
ms.assetid: 1a7155e6-2d4a-4ed1-a72c-edb37fa1a46b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce2038f3bc90a2f17506b0aadaaf9707fa911896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590893"
---
# <a name="add-members-to-a-collection-master-data-services"></a><span data-ttu-id="a11c1-102">将成员添加到集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a11c1-102">Add Members to a Collection (Master Data Services)</span></span>
  <span data-ttu-id="a11c1-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以将叶成员和合并成员添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="a11c1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can add leaf and consolidated members to a collection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a11c1-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="a11c1-104">Prerequisites</span></span>  
 <span data-ttu-id="a11c1-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="a11c1-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a11c1-106">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="a11c1-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="a11c1-107">对于您要将成员添加到的集合模型对象，您必须至少具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="a11c1-107">You must have a minimum of **Update** permission to the collection model object that you are adding members to.</span></span>  
  
-   <span data-ttu-id="a11c1-108">集合必须存在。</span><span class="sxs-lookup"><span data-stu-id="a11c1-108">A collection must exist.</span></span> <span data-ttu-id="a11c1-109">有关详细信息，请参阅[创建集合 (Master Data Services)](create-a-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a11c1-109">For more information, see [Create a Collection &#40;Master Data Services&#41;](create-a-collection-master-data-services.md).</span></span>  
  
### <a name="to-add-members-to-a-collection"></a><span data-ttu-id="a11c1-110">将成员添加到集合</span><span class="sxs-lookup"><span data-stu-id="a11c1-110">To add members to a collection</span></span>  
  
1.  <span data-ttu-id="a11c1-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="a11c1-111">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="a11c1-112">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="a11c1-112">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="a11c1-113">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="a11c1-113">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="a11c1-114">从菜单栏中，指向“集合”\*\*\*\*，然后单击“entity_name”\*\*。</span><span class="sxs-lookup"><span data-stu-id="a11c1-114">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="a11c1-115">在网格中，单击要将成员添加到的集合对应的行。</span><span class="sxs-lookup"><span data-stu-id="a11c1-115">In the grid, click the row for the collection you want to add members to.</span></span>  
  
6.  <span data-ttu-id="a11c1-116">单击 **“集合成员”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a11c1-116">Click the **Collection Members** tab.</span></span>  
  
7.  <span data-ttu-id="a11c1-117">单击 **“编辑成员”**。</span><span class="sxs-lookup"><span data-stu-id="a11c1-117">Click **Edit Members**.</span></span>  
  
8.  <span data-ttu-id="a11c1-118">若要筛选可用成员列表，请从左侧列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="a11c1-118">To filter the list of available members, select from the list on the left.</span></span>  
  
9. <span data-ttu-id="a11c1-119">单击包含您要添加的成员的行，然后单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="a11c1-119">Click the row with the member you want to add and click **Add**.</span></span>  
  
10. <span data-ttu-id="a11c1-120">或者，单击 **“向上”** 或 **“向下”** 重新排列集合成员。</span><span class="sxs-lookup"><span data-stu-id="a11c1-120">Optionally, rearrange collection members by clicking **Up** or **Down**.</span></span>  
  
11. <span data-ttu-id="a11c1-121">或者，单击 **“权重”** 列中的值设置权重值。</span><span class="sxs-lookup"><span data-stu-id="a11c1-121">Optionally, set weight values by clicking the value in the **Weight** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a11c1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a11c1-122">See Also</span></span>  
 [<span data-ttu-id="a11c1-123">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a11c1-123">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
