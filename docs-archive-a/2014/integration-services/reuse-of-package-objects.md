---
title: 重用包对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b7612cb2684bb842108068b062e54fbe9dee4327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687988"
---
# <a name="reuse-of-package-objects"></a><span data-ttu-id="f7693-102">重用包对象</span><span class="sxs-lookup"><span data-stu-id="f7693-102">Reuse of Package Objects</span></span>
  <span data-ttu-id="f7693-103">要经常重用的包功能。</span><span class="sxs-lookup"><span data-stu-id="f7693-103">Frequently packages functionality that you want to reuse.</span></span> <span data-ttu-id="f7693-104">例如，如果创建了一组任务，可能希望将这些项作为一个组一起重用，或者可能希望重用单个项，如在其他 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中创建的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f7693-104">For example, if you created a set of tasks, you might want to reuse the items together as a group, or you might want to reuse a single item such as a connection manager that you created in a different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="copy-and-paste"></a><span data-ttu-id="f7693-105">复制和粘贴</span><span class="sxs-lookup"><span data-stu-id="f7693-105">Copy and Paste</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f7693-106">和 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器支持复制和粘贴包对象，包对象可以包括控制流项、数据流项和连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f7693-106">and [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer support copying and pasting package objects, which can include control flow items, data flow items, and connection managers.</span></span> <span data-ttu-id="f7693-107">可以在项目之间和包之间进行复制和粘贴。</span><span class="sxs-lookup"><span data-stu-id="f7693-107">You can copy and paste between projects and between packages.</span></span> <span data-ttu-id="f7693-108">如果解决方案包含了多个项目，则可以在项目之间进行复制，并且项目可以属于不同类型。</span><span class="sxs-lookup"><span data-stu-id="f7693-108">If the solution contains multiple projects you can copy between projects, and the projects can be of different types.</span></span>  
  
 <span data-ttu-id="f7693-109">如果解决方案包含多个包，则可以在它们之间进行复制和粘贴。</span><span class="sxs-lookup"><span data-stu-id="f7693-109">If a solution contains multiple packages, you can copy and paste between them.</span></span> <span data-ttu-id="f7693-110">包可以位于相同或不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中。</span><span class="sxs-lookup"><span data-stu-id="f7693-110">The packages can be in the same or different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="f7693-111">但是，包对象可能对其他对象有依赖关系，没有这些对象它们将无效。</span><span class="sxs-lookup"><span data-stu-id="f7693-111">However, package objects may have dependencies on other objects, without which they are not valid.</span></span> <span data-ttu-id="f7693-112">例如，“执行 SQL”任务使用连接管理器，因此还必须复制连接管理器才能使任务工作。</span><span class="sxs-lookup"><span data-stu-id="f7693-112">For example, an Execute SQL task uses a connection manager, which you must copy as well to make the task work.</span></span> <span data-ttu-id="f7693-113">而且，某些包对象需要包已经包含某个对象，如果没有此对象，则无法将所复制的对象成功粘贴到包中。</span><span class="sxs-lookup"><span data-stu-id="f7693-113">Also, some package objects require that the package already contain a certain object, and without this object you cannot successfully paste the copied objects into a package.</span></span> <span data-ttu-id="f7693-114">例如，包至少要有一个“数据流”任务，否则无法将数据流粘贴到该包。</span><span class="sxs-lookup"><span data-stu-id="f7693-114">For example, you cannot paste a data flow into a package that does not have at least one Data Flow task.</span></span>  
  
 <span data-ttu-id="f7693-115">您可能会发现自己重复地复制了同一个包。</span><span class="sxs-lookup"><span data-stu-id="f7693-115">You may find that you copy the same packages repeatedly.</span></span> <span data-ttu-id="f7693-116">若要避免复制进程，可以将这些包指定为模板，并在创建新包时使用它们。</span><span class="sxs-lookup"><span data-stu-id="f7693-116">To avoid the copy process, you can designate these packages as templates and use them when you create new packages.</span></span>  
  
 <span data-ttu-id="f7693-117">复制包对象时，[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 会向新对象的 `ID` 属性自动分配新的 GUID，并更新 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="f7693-117">When you copy a package object, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatically assigns a new GUID to the `ID` property of the new object and updates the `Name` property.</span></span>  
  
 <span data-ttu-id="f7693-118">无法复制变量。</span><span class="sxs-lookup"><span data-stu-id="f7693-118">You cannot copy variables.</span></span> <span data-ttu-id="f7693-119">如果诸如任务这样的对象使用了变量，则必须在目标包中重新创建变量。</span><span class="sxs-lookup"><span data-stu-id="f7693-119">If an object such as a task uses variables, then you must re-create the variables in the destination package.</span></span> <span data-ttu-id="f7693-120">相比之下，如果复制整个包，则包中的变量也会被复制。</span><span class="sxs-lookup"><span data-stu-id="f7693-120">In contrast, if you copy the entire package, then the variables in the package are also copied.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f7693-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f7693-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f7693-122">复制包对象</span><span class="sxs-lookup"><span data-stu-id="f7693-122">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
-   [<span data-ttu-id="f7693-123">复制项目项</span><span class="sxs-lookup"><span data-stu-id="f7693-123">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
-   [<span data-ttu-id="f7693-124">将包保存为包模板</span><span class="sxs-lookup"><span data-stu-id="f7693-124">Save a Package as a Package Template</span></span>](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
