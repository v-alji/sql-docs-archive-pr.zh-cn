---
title: 导航访问权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576851"
---
# <a name="navigational-access-master-data-services"></a><span data-ttu-id="bb5cb-102">导航访问权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bb5cb-102">Navigational Access (Master Data Services)</span></span>
  <span data-ttu-id="bb5cb-103">导航访问权限适用于在 **“模型”** 选项卡上分配的模型对象安全性。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-103">Navigational access applies to model object security, which is assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="bb5cb-104">导航访问权限是所获得的高于已分配安全性级别的访问权限。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-104">Navigational access is the access you get to levels higher than where you've assigned security.</span></span>  
  
 <span data-ttu-id="bb5cb-105">在本示例中，权限将分配给某一实体，因此在模型级别授予导航访问权限。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-105">In this example, permissions are assigned to an entity, and so navigational access is granted at the model level.</span></span>  
  
 <span data-ttu-id="bb5cb-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="bb5cb-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>  
  
 <span data-ttu-id="bb5cb-107">**实体**</span><span class="sxs-lookup"><span data-stu-id="bb5cb-107">**Entities**</span></span>  
  
 <span data-ttu-id="bb5cb-108">在您向某一实体、其叶成员或其合并成员分配权限时，导航访问权限意味着您可以读取或更新所有成员的名称和代码。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-108">When you assign permission to an entity, its leaf members, or its consolidated members, navigational access means you can read or update the name and code for all members.</span></span> <span data-ttu-id="bb5cb-109">您还可以读取模型名称。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-109">You can also read the model name.</span></span>  
  
 <span data-ttu-id="bb5cb-110">**特性**</span><span class="sxs-lookup"><span data-stu-id="bb5cb-110">**Attributes**</span></span>  
  
 <span data-ttu-id="bb5cb-111">在您向某一属性分配权限时，导航访问权限意味着您可以读取或更新实体中所有成员的名称和代码。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-111">When you assign permission to an attribute, navigational access means you can read or update the name and code for all members in the entity.</span></span> <span data-ttu-id="bb5cb-112">您还可以读取模型名称。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-112">You can also read the model name.</span></span>  
  
 <span data-ttu-id="bb5cb-113">**集合**</span><span class="sxs-lookup"><span data-stu-id="bb5cb-113">**Collections**</span></span>  
  
 <span data-ttu-id="bb5cb-114">在您向集合分配权限时，您可以读取或更新名称、代码、说明和所有者 ID。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-114">When you assign permissions to collections, you can read or update the name, code, description and owner ID.</span></span> <span data-ttu-id="bb5cb-115">您还可以读取模型名称。</span><span class="sxs-lookup"><span data-stu-id="bb5cb-115">You can also read the model name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5cb-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb5cb-116">See Also</span></span>  
 [<span data-ttu-id="bb5cb-117">如何确定权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bb5cb-117">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](how-permissions-are-determined-master-data-services.md)  
  
  
