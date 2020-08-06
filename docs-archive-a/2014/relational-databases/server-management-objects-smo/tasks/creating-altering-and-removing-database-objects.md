---
title: 使用数据库对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14dd0c0175a23f809fc925c5104ac15ac408805b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692833"
---
# <a name="working-with-database-objects"></a><span data-ttu-id="8a470-102">使用数据库对象</span><span class="sxs-lookup"><span data-stu-id="8a470-102">Working with Database Objects</span></span>
  <span data-ttu-id="8a470-103">创建 SMO 对象的各个阶段如下：</span><span class="sxs-lookup"><span data-stu-id="8a470-103">The stages of SMO object creation are as follows:</span></span>  
  
1.  <span data-ttu-id="8a470-104">创建对象的实例。</span><span class="sxs-lookup"><span data-stu-id="8a470-104">Create an instance of the object.</span></span>  
  
2.  <span data-ttu-id="8a470-105">设置对象属性。</span><span class="sxs-lookup"><span data-stu-id="8a470-105">Set the object properties.</span></span>  
  
3.  <span data-ttu-id="8a470-106">创建子对象的实例。</span><span class="sxs-lookup"><span data-stu-id="8a470-106">Create instances of the child objects.</span></span>  
  
4.  <span data-ttu-id="8a470-107">设置子对象属性。</span><span class="sxs-lookup"><span data-stu-id="8a470-107">Set the child object properties.</span></span>  
  
5.  <span data-ttu-id="8a470-108">创建对象。</span><span class="sxs-lookup"><span data-stu-id="8a470-108">Create the object.</span></span>  
  
 <span data-ttu-id="8a470-109">当在 SMO 应用程序中创建 SMO 对象的实例时，在发出 `Create` 方法之前，这些实例不会存在于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中。</span><span class="sxs-lookup"><span data-stu-id="8a470-109">When instances of SMO objects are created in an SMO application, they do not exist on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] until the `Create` method is issued.</span></span> <span data-ttu-id="8a470-110">但是，不必针对每个单独的对象发出 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="8a470-110">However, it is not necessary to issue a `Create` method for every individual object.</span></span> <span data-ttu-id="8a470-111">如果某一对象具有一组子对象，则只需要父对象运行 `Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="8a470-111">If an object has a set of child objects, only the parent object is required to run the `Create` method.</span></span> <span data-ttu-id="8a470-112">例如，表定义要求它至少包含一个列才能存在。</span><span class="sxs-lookup"><span data-stu-id="8a470-112">For example, the definition of a table requires that it contains at least one column to exist.</span></span> <span data-ttu-id="8a470-113">并且，列不能独立于表存在。</span><span class="sxs-lookup"><span data-stu-id="8a470-113">Also, a column cannot exist in isolation without a table.</span></span> <span data-ttu-id="8a470-114">表与其列之间存在相互依赖的关系。</span><span class="sxs-lookup"><span data-stu-id="8a470-114">There is a codependent relationship between the table and its columns.</span></span>  
  
 <span data-ttu-id="8a470-115">使用 <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> 方法可以更改对象。</span><span class="sxs-lookup"><span data-stu-id="8a470-115">The <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> method lets you make changes to an object.</span></span> <span data-ttu-id="8a470-116">对对象的若干更改（例如，向对象的集合之一添加子对象或更改属性值）将组成一批共同运行。</span><span class="sxs-lookup"><span data-stu-id="8a470-116">Several changes to an object, such as adding child objects to one of the object's collections or changing a property value, are batched together and run as one.</span></span> <span data-ttu-id="8a470-117">`Alter` 方法减少了网络流量，并提高了整体性能。</span><span class="sxs-lookup"><span data-stu-id="8a470-117">The `Alter` method reduces network traffic and improves overall performance.</span></span>  
  
 <span data-ttu-id="8a470-118">`Drop` 语句用于删除最初创建该对象所需的对象及其相互依赖的所有子对象。</span><span class="sxs-lookup"><span data-stu-id="8a470-118">The `Drop` statement is used to remove an object and all its codependent child objects that were required to create the object initially.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a470-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a470-119">See Also</span></span>  
 [<span data-ttu-id="8a470-120">SMO 对象模型</span><span class="sxs-lookup"><span data-stu-id="8a470-120">SMO Object Model</span></span>](../smo-object-model.md)  
  
  
