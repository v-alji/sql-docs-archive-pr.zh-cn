---
title: 自动生成代码属性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6c442f37ffe322985ba55b29b2c4cd539b8a3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589746"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a><span data-ttu-id="e2b24-102">自动生成 Code 属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e2b24-102">Automatically Generate Code Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="e2b24-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，当希望在每次创建新成员时自动为 Code 值分配一个整数时，自动为实体的 Code 属性设置值。</span><span class="sxs-lookup"><span data-stu-id="e2b24-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's Code attribute when you want an integer to be automatically assigned to the Code value each time a new member is created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e2b24-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="e2b24-104">Prerequisites</span></span>  
 <span data-ttu-id="e2b24-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="e2b24-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e2b24-106">您必须有权访问 **“系统管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="e2b24-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="e2b24-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="e2b24-107">You must be a model administrator.</span></span> <span data-ttu-id="e2b24-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b24-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="e2b24-109">实体必须存在。</span><span class="sxs-lookup"><span data-stu-id="e2b24-109">The entity must exist.</span></span> <span data-ttu-id="e2b24-110">有关详细信息，请参阅[创建实体 (Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b24-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-code-values"></a><span data-ttu-id="e2b24-111">自动生成 Code 值</span><span class="sxs-lookup"><span data-stu-id="e2b24-111">To automatically generate Code values</span></span>  
  
1.  <span data-ttu-id="e2b24-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="e2b24-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="e2b24-113">在 "**模型资源管理器**" 页上，从菜单栏中指向 "**管理**"，然后单击 "**实体**"。</span><span class="sxs-lookup"><span data-stu-id="e2b24-113">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="e2b24-114">在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="e2b24-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="e2b24-115">为您要生成其代码的实体选择行。</span><span class="sxs-lookup"><span data-stu-id="e2b24-115">Select the row for the entity that you want to generate codes for.</span></span>  
  
5.  <span data-ttu-id="e2b24-116">单击 **“编辑所选实体”**。</span><span class="sxs-lookup"><span data-stu-id="e2b24-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="e2b24-117">选中 **“自动创建代码值”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="e2b24-117">Select the **Create Code values automatically** check box.</span></span>  
  
7.  <span data-ttu-id="e2b24-118">在 **“起始”** 框中，键入开始递增的数字。</span><span class="sxs-lookup"><span data-stu-id="e2b24-118">In the **Start with** box, type a number to begin incrementing.</span></span> <span data-ttu-id="e2b24-119">如果成员已存在，则将基于最大的现有值设置 Code。</span><span class="sxs-lookup"><span data-stu-id="e2b24-119">If members already exist, the Code will be set based on the highest existing value.</span></span> <span data-ttu-id="e2b24-120">例如，如果最大的现有 Code 值为 299，则下一个成员的 Code 值将设置为 300。</span><span class="sxs-lookup"><span data-stu-id="e2b24-120">For example, if the highest existing Code value is 299, the next member's Code value will be set to 300.</span></span>  
  
8.  <span data-ttu-id="e2b24-121">单击 "**保存实体**"。</span><span class="sxs-lookup"><span data-stu-id="e2b24-121">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b24-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2b24-122">See Also</span></span>  
 <span data-ttu-id="e2b24-123">[自动创建代码 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e2b24-123">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 [<span data-ttu-id="e2b24-124">自动生成 Code 之外的属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e2b24-124">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
