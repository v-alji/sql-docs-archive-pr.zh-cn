---
title: 级别属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 553503b9d35142bcc998b4ec12ad2e29d4c66318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578499"
---
# <a name="level-properties"></a><span data-ttu-id="700a2-102">级别属性</span><span class="sxs-lookup"><span data-stu-id="700a2-102">Level Properties</span></span> 
  <span data-ttu-id="700a2-103">下表列出了用户定义层次结构中的一个级别的属性并对其进行了说明。</span><span class="sxs-lookup"><span data-stu-id="700a2-103">The following table lists and describes the properties of a level in a user-defined hierarchy.</span></span>  
  
|<span data-ttu-id="700a2-104">属性</span><span class="sxs-lookup"><span data-stu-id="700a2-104">Property</span></span>|<span data-ttu-id="700a2-105">说明</span><span class="sxs-lookup"><span data-stu-id="700a2-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="700a2-106">说明</span><span class="sxs-lookup"><span data-stu-id="700a2-106">Description</span></span>|<span data-ttu-id="700a2-107">包含对级别的说明。</span><span class="sxs-lookup"><span data-stu-id="700a2-107">Contains the description of the level.</span></span>|  
|<span data-ttu-id="700a2-108">HideMemberIf</span><span class="sxs-lookup"><span data-stu-id="700a2-108">HideMemberIf</span></span>|<span data-ttu-id="700a2-109">指示是否应该从客户端应用程序中隐藏某一级别的成员以及何时隐藏。</span><span class="sxs-lookup"><span data-stu-id="700a2-109">Indicates whether and when a member in a level should be hidden from client applications.</span></span> <span data-ttu-id="700a2-110">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="700a2-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="700a2-111">从不</span><span class="sxs-lookup"><span data-stu-id="700a2-111">Never</span></span><br /> <span data-ttu-id="700a2-112">从不隐藏成员。</span><span class="sxs-lookup"><span data-stu-id="700a2-112">Members are never hidden.</span></span> <span data-ttu-id="700a2-113">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="700a2-113">This is the default value.</span></span><br /><br /> <span data-ttu-id="700a2-114">OnlyChildWithNoName</span><span class="sxs-lookup"><span data-stu-id="700a2-114">OnlyChildWithNoName</span></span><br /> <span data-ttu-id="700a2-115">当成员是其父级的唯一子级并且成员名称为空时，隐藏该成员。</span><span class="sxs-lookup"><span data-stu-id="700a2-115">A member is hidden when the member is the only child of its parent and the member's name is empty.</span></span><br /><br /> <span data-ttu-id="700a2-116">OnlyChildWithParentName</span><span class="sxs-lookup"><span data-stu-id="700a2-116">OnlyChildWithParentName</span></span><br /> <span data-ttu-id="700a2-117">当成员是其父级的唯一子级并且成员名称与其父级的名称相同时，隐藏该成员。</span><span class="sxs-lookup"><span data-stu-id="700a2-117">A member is hidden when the member is the only child of its parent and the member's name is identical to that of its parent.</span></span><br /><br /> <span data-ttu-id="700a2-118">NoName</span><span class="sxs-lookup"><span data-stu-id="700a2-118">NoName</span></span><br /> <span data-ttu-id="700a2-119">当成员的名称为空时，隐藏该成员。</span><span class="sxs-lookup"><span data-stu-id="700a2-119">A member is hidden when the member's name is empty.</span></span><br /><br /> <span data-ttu-id="700a2-120">ParentName</span><span class="sxs-lookup"><span data-stu-id="700a2-120">ParentName</span></span><br /> <span data-ttu-id="700a2-121">当成员的名称与其父级的名称相同时，隐藏该成员。</span><span class="sxs-lookup"><span data-stu-id="700a2-121">A member is hidden when the member's name is identical to that of its parent.</span></span>|  
|<span data-ttu-id="700a2-122">ID</span><span class="sxs-lookup"><span data-stu-id="700a2-122">ID</span></span>|<span data-ttu-id="700a2-123">包含级别的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="700a2-123">Contains the unique identifier (ID) of the level.</span></span>|  
|<span data-ttu-id="700a2-124">名称</span><span class="sxs-lookup"><span data-stu-id="700a2-124">Name</span></span>|<span data-ttu-id="700a2-125">包含级别的友好名称。</span><span class="sxs-lookup"><span data-stu-id="700a2-125">Contains the friendly name of the level.</span></span> <span data-ttu-id="700a2-126">默认情况下，级别的名称与源属性的名称相同。</span><span class="sxs-lookup"><span data-stu-id="700a2-126">By default, the name of a level is the same as the name of the source attribute.</span></span>|  
|<span data-ttu-id="700a2-127">SourceAttribute</span><span class="sxs-lookup"><span data-stu-id="700a2-127">SourceAttribute</span></span>|<span data-ttu-id="700a2-128">包含级别所基于的源属性的名称。</span><span class="sxs-lookup"><span data-stu-id="700a2-128">Contains the name of the source attribute on which the level is based.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="700a2-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="700a2-129">See Also</span></span>  
 [<span data-ttu-id="700a2-130">用户层次结构属性</span><span class="sxs-lookup"><span data-stu-id="700a2-130">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
