---
title: 自动创建代码 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9c12e000b2f6ff2ecad07bd62f8c6c05afa36f82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576873"
---
# <a name="automatic-code-creation-master-data-services"></a><span data-ttu-id="bdf7d-102">自动创建代码 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bdf7d-102">Automatic Code Creation (Master Data Services)</span></span>
  <span data-ttu-id="bdf7d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以为 Code 属性或任何其他数值属性自动生成数值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], numeric values can be automatically generated for the Code attribute, or for any other numeric attribute.</span></span> <span data-ttu-id="bdf7d-104">自动生成代码时，不会阻止您输入其他代码值；实际上只是自动设置初始值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-104">When codes are generated automatically, you are not prevented from entering other values for codes; rather an initial value is automatically set.</span></span>  
  
## <a name="generating-code-values"></a><span data-ttu-id="bdf7d-105">生成 Code 值</span><span class="sxs-lookup"><span data-stu-id="bdf7d-105">Generating Code Values</span></span>  
 <span data-ttu-id="bdf7d-106">管理员可以通过编辑关联实体的属性，为 Code 特性配置自动生成的值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-106">Administrators can configure automatically-generated values for the Code attribute by editing the associated entity's properties.</span></span> <span data-ttu-id="bdf7d-107">他们可以指定一个初始值，让每个后续值依次增加 1。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-107">They can specify an initial value, and each subsequent value is increased by one.</span></span>  
  
 <span data-ttu-id="bdf7d-108">在相关工具之一中或使用临时过程向 MDS 中输入 Code 值时，可以保留 Code 值为空，Code 值将自动生成。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-108">When you enter Code values into MDS, either in one of the tools or by using the staging process, you can leave the Code value blank and a Code value will be automatically generated.</span></span> <span data-ttu-id="bdf7d-109">也可以指定您选择的 Code 值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-109">Or you can specify a Code value of your choice.</span></span>  
  
## <a name="generating-other-attribute-values"></a><span data-ttu-id="bdf7d-110">生成其他属性值</span><span class="sxs-lookup"><span data-stu-id="bdf7d-110">Generating Other Attribute Values</span></span>  
 <span data-ttu-id="bdf7d-111">管理员可以通过创建业务规则，自动为 Code 之外的属性生成值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-111">Administrators can automatically generate values for attributes other than Code by creating business rules.</span></span> <span data-ttu-id="bdf7d-112">他们可以指定一个初始值，然后指定每个后续值按其递增的值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-112">They can specify an initial value, and specify the number each subsequent value is incremented by.</span></span>  
  
 <span data-ttu-id="bdf7d-113">在相关工具之一中或使用临时过程向 MDS 中输入属性值时，可以保留属性值为空。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-113">When you enter attribute values into MDS, either in one of the tools or by using the staging process, you can leave the attribute value blank.</span></span> <span data-ttu-id="bdf7d-114">应用业务规则时，将以最大的现有值为基础增加值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-114">When business rules are applied, the values will be incremented based on the highest existing value.</span></span> <span data-ttu-id="bdf7d-115">例如，如果规则是“属性默认为一个从 1 开始、增量为 4 的生成值”，并且属性当前的最大值是 700，则添加的下一个成员的值将是 704。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-115">For example, if your rule is "Default attribute to a generated value that starts at 1 and increments by 4" and the highest current value for the attribute is 700, the value for the next member that's added will be 704.</span></span>  
  
## <a name="deleting-automatically-generated-values"></a><span data-ttu-id="bdf7d-116">删除自动生成的值</span><span class="sxs-lookup"><span data-stu-id="bdf7d-116">Deleting Automatically Generated Values</span></span>  
 <span data-ttu-id="bdf7d-117">在管理员启用为 Code 属性自动生成值之后，用户可能会意外删除具有要重复使用的 Code 值的成员。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-117">After an administrator enables automatically generated values for the Code attribute, users may accidentally delete a member that had a Code value they want to reuse.</span></span> <span data-ttu-id="bdf7d-118">将显示错误消息 "成员代码已被删除的成员使用"。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-118">The error message "The member code is already used by a member that was deleted" will be displayed.</span></span> <span data-ttu-id="bdf7d-119">下面是两种可能的解决方案：</span><span class="sxs-lookup"><span data-stu-id="bdf7d-119">There are two possible solutions:</span></span>  
  
-   <span data-ttu-id="bdf7d-120">在 "**版本管理**" 功能区域中，管理员可以撤消删除成员时所发生的事务。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-120">In the **Version Management** functional area, an administrator can reverse the transaction that occurred when the member was deleted.</span></span> <span data-ttu-id="bdf7d-121">但是，这意味着将还原以前的所有成员的属性和层次结构和集合中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-121">However, this means that all of the former member's attributes and membership in hierarchies and collections is restored.</span></span> <span data-ttu-id="bdf7d-122">有关详细信息，请参阅[反转事务 &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-122">For more information, see [Reverse a Transaction &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="bdf7d-123">管理员可以使用临时过程永久删除成员。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-123">An administrator can use the staging process to permanently delete the member.</span></span> <span data-ttu-id="bdf7d-124">有关详细信息，请参阅[&#41;&#40;Master Data Services 停用或删除成员](add-update-and-delete-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-124">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bdf7d-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="bdf7d-125">Related Tasks</span></span>  
  
|<span data-ttu-id="bdf7d-126">任务说明</span><span class="sxs-lookup"><span data-stu-id="bdf7d-126">Task Description</span></span>|<span data-ttu-id="bdf7d-127">主题</span><span class="sxs-lookup"><span data-stu-id="bdf7d-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="bdf7d-128">自动为 Code 属性生成值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-128">Automatically generate values for the Code attribute.</span></span>|[<span data-ttu-id="bdf7d-129">自动生成 Code 属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bdf7d-129">Automatically Generate Code Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|<span data-ttu-id="bdf7d-130">自动为其他属性生成值。</span><span class="sxs-lookup"><span data-stu-id="bdf7d-130">Automatically generate values for other attributes.</span></span>|[<span data-ttu-id="bdf7d-131">自动生成 Code 之外的属性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bdf7d-131">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="bdf7d-132">相关内容</span><span class="sxs-lookup"><span data-stu-id="bdf7d-132">Related Content</span></span>  
  
-   [<span data-ttu-id="bdf7d-133">Master Data Services 概述</span><span class="sxs-lookup"><span data-stu-id="bdf7d-133">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="bdf7d-134">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bdf7d-134">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="bdf7d-135">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bdf7d-135">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
