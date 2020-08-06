---
title: 保留字 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c54bb371cd8f797cfb36f015387e0e21339c0426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587451"
---
# <a name="reserved-words-master-data-services"></a><span data-ttu-id="6c978-102">保留字 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6c978-102">Reserved Words (Master Data Services)</span></span>
  <span data-ttu-id="6c978-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您创建模型对象或成员时，不能使用某些字词。</span><span class="sxs-lookup"><span data-stu-id="6c978-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you create model objects or members, some words cannot be used.</span></span> <span data-ttu-id="6c978-104">使用这些字词可能导致错误。</span><span class="sxs-lookup"><span data-stu-id="6c978-104">Using these words may cause errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c978-105">您还应限制使用特殊字符（符号、连字符等）。</span><span class="sxs-lookup"><span data-stu-id="6c978-105">You should also limit your use of special characters (symbols, hyphenation, etc.).</span></span>  
  
-   [<span data-ttu-id="6c978-106">模型</span><span class="sxs-lookup"><span data-stu-id="6c978-106">Models</span></span>](#models)  
  
-   [<span data-ttu-id="6c978-107">实体</span><span class="sxs-lookup"><span data-stu-id="6c978-107">Entities</span></span>](#entities)  
  
-   [<span data-ttu-id="6c978-108">显式层次结构</span><span class="sxs-lookup"><span data-stu-id="6c978-108">Explicit Hierarchies</span></span>](#exhierarchies)  
  
-   [<span data-ttu-id="6c978-109">属性</span><span class="sxs-lookup"><span data-stu-id="6c978-109">Attributes</span></span>](#attributes)  
  
-   [<span data-ttu-id="6c978-110">成员</span><span class="sxs-lookup"><span data-stu-id="6c978-110">Members</span></span>](#members)  
  
##  <a name="models"></a><a name="models"></a><span data-ttu-id="6c978-111">机型</span><span class="sxs-lookup"><span data-stu-id="6c978-111">Models</span></span>  
 <span data-ttu-id="6c978-112">如果创建的模型的名称设置为 "**名称**"，请不要选择 "**使用与模型相同的名称创建实体**"，因为**名称**不能用于实体名称。</span><span class="sxs-lookup"><span data-stu-id="6c978-112">If you create a model with the name set to **Name**, do not select **Create entity with same name as model** because **Name** cannot be used for the name of an entity.</span></span>  
  
##  <a name="entities"></a><a name="entities"></a><span data-ttu-id="6c978-113">条目</span><span class="sxs-lookup"><span data-stu-id="6c978-113">Entities</span></span>  
 <span data-ttu-id="6c978-114">对于实体名称，不能使用 **Name** 或 **Code**。</span><span class="sxs-lookup"><span data-stu-id="6c978-114">For entity names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a><span data-ttu-id="6c978-115">显式层次结构</span><span class="sxs-lookup"><span data-stu-id="6c978-115">Explicit Hierarchies</span></span>  
 <span data-ttu-id="6c978-116">对于显式层次结构名称，不能使用 **Name** 或 **Code**。</span><span class="sxs-lookup"><span data-stu-id="6c978-116">For explicit hierarchy names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="attributes"></a><a name="attributes"></a><span data-ttu-id="6c978-117">属性</span><span class="sxs-lookup"><span data-stu-id="6c978-117">Attributes</span></span>  
  
-   <span data-ttu-id="6c978-118">**ID**</span><span class="sxs-lookup"><span data-stu-id="6c978-118">**ID**</span></span>  
  
-   <span data-ttu-id="6c978-119">**代码**</span><span class="sxs-lookup"><span data-stu-id="6c978-119">**Code**</span></span>  
  
-   <span data-ttu-id="6c978-120">**名称**</span><span class="sxs-lookup"><span data-stu-id="6c978-120">**Name**</span></span>  
  
-   <span data-ttu-id="6c978-121">**EnterDTM**</span><span class="sxs-lookup"><span data-stu-id="6c978-121">**EnterDTM**</span></span>  
  
-   <span data-ttu-id="6c978-122">**EnterUserID**</span><span class="sxs-lookup"><span data-stu-id="6c978-122">**EnterUserID**</span></span>  
  
-   <span data-ttu-id="6c978-123">**EnterUserName**</span><span class="sxs-lookup"><span data-stu-id="6c978-123">**EnterUserName**</span></span>  
  
-   <span data-ttu-id="6c978-124">**LastChgDTM**</span><span class="sxs-lookup"><span data-stu-id="6c978-124">**LastChgDTM**</span></span>  
  
-   <span data-ttu-id="6c978-125">**LastChgUserID**</span><span class="sxs-lookup"><span data-stu-id="6c978-125">**LastChgUserID**</span></span>  
  
-   <span data-ttu-id="6c978-126">**Status_ID**</span><span class="sxs-lookup"><span data-stu-id="6c978-126">**Status_ID**</span></span>  
  
-   <span data-ttu-id="6c978-127">**ValidationStatus_ID**</span><span class="sxs-lookup"><span data-stu-id="6c978-127">**ValidationStatus_ID**</span></span>  
  
-   <span data-ttu-id="6c978-128">**Version_ID**</span><span class="sxs-lookup"><span data-stu-id="6c978-128">**Version_ID**</span></span>  
  
##  <a name="members"></a><a name="members"></a><span data-ttu-id="6c978-129">组员</span><span class="sxs-lookup"><span data-stu-id="6c978-129">Members</span></span>  
 <span data-ttu-id="6c978-130">对于成员，不能对**Code**属性值使用**MDMMemberStatus**或**ROOT** 。</span><span class="sxs-lookup"><span data-stu-id="6c978-130">For members, you cannot use **MDMMemberStatus** or **ROOT** for the **Code** attribute value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c978-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c978-131">See Also</span></span>  
 [<span data-ttu-id="6c978-132">Master Data Services 概述</span><span class="sxs-lookup"><span data-stu-id="6c978-132">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
  
