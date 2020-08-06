---
title: 对象依赖关系 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13d1775f1e4e6885fe56a43ce40c4ac155c5b361
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693607"
---
# <a name="object-dependencies"></a><span data-ttu-id="82f5e-102">对象依赖关系</span><span class="sxs-lookup"><span data-stu-id="82f5e-102">Object Dependencies</span></span>
  <span data-ttu-id="82f5e-103">一些数据库对象与其他数据库对象存在依赖关系。</span><span class="sxs-lookup"><span data-stu-id="82f5e-103">Some database objects have dependencies upon other database objects.</span></span> <span data-ttu-id="82f5e-104">例如，视图和存储过程依赖于包含视图或过程返回的数据的表是否存在。</span><span class="sxs-lookup"><span data-stu-id="82f5e-104">For example, views and stored procedures depend upon the existence of tables that contain the data returned by the view or procedure.</span></span> <span data-ttu-id="82f5e-105">当前对象的“对象依赖关系（‘常规’页）”  列出了该对象正常运行所需的数据库对象和依赖于所选对象的对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-105">The **Object Dependencies (General Page)** for the current object lists both the database objects that must be present for the object to function properly and the objects that depend upon the selected object.</span></span> <span data-ttu-id="82f5e-106">在其定义中引用了另一个对象并且该定义存储在系统目录中的对象称为“引用实体”  。</span><span class="sxs-lookup"><span data-stu-id="82f5e-106">An object that references another object in its definition and that definition is stored in the system catalog is called a *referencing entity*.</span></span> <span data-ttu-id="82f5e-107">被另一对象引用的对象称为“被引用实体”  。</span><span class="sxs-lookup"><span data-stu-id="82f5e-107">An object that is referred to by another object is called a *referenced entity*.</span></span>  
  
 <span data-ttu-id="82f5e-108">当前对象的“对象依赖关系（‘高级’页）”  列出了依赖于该对象的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库对象和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-108">The **Object Dependencies (Advanced Page)** for the current object lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects that depend on the object.</span></span> <span data-ttu-id="82f5e-109">这些对象可存储于不同的服务器上。</span><span class="sxs-lookup"><span data-stu-id="82f5e-109">The objects may be stored on different servers.</span></span>  
  
 <span data-ttu-id="82f5e-110">使用此对话框可在更改或删除所选对象之前了解其依赖关系。</span><span class="sxs-lookup"><span data-stu-id="82f5e-110">Use this dialog box to understand the dependencies before changing or deleting the selected object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="82f5e-111">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="82f5e-111">UI element list</span></span>  
 <span data-ttu-id="82f5e-112">**依赖对象**  _\<selected object>_</span><span class="sxs-lookup"><span data-stu-id="82f5e-112">**Objects that depend on**  _\<selected object>_</span></span>  
 <span data-ttu-id="82f5e-113">单击此按钮将列出依赖于所选对象的对象，以及依赖关系跟踪所涉及的对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-113">Clicking this button displays a list of those objects that are dependency-tracked and that depend on the selected object.</span></span>  
  
 <span data-ttu-id="82f5e-114">**对象** _\<selected object>_**取决于**    </span><span class="sxs-lookup"><span data-stu-id="82f5e-114">**Objects on which**  _\<selected object>_  **depends**</span></span>  
 <span data-ttu-id="82f5e-115">单击此按钮将列出所选对象所依赖的并且依赖关系跟踪涉及的对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-115">Clicking this button displays a list of those objects that are dependency-tracked, on which the selected object depends.</span></span>  
  
 <span data-ttu-id="82f5e-116">**依赖项**</span><span class="sxs-lookup"><span data-stu-id="82f5e-116">**Dependencies**</span></span>  
 <span data-ttu-id="82f5e-117">如果单击了“依赖  **的对象”** _\<selected object>_ ，则选择此选项将显示依赖于所选对象的对象的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="82f5e-117">If **Objects that depend on** _\<selected object>_ is clicked, this displays an hierarchical view of objects that depend on the selected object.</span></span> <span data-ttu-id="82f5e-118">如果单击了“ **依赖的对象”** _\<selected object>_  ，则选择此选项将显示所选对象所依赖的对象的层次结构视图。</span><span class="sxs-lookup"><span data-stu-id="82f5e-118">If **Objects on which** _\<selected object>_ **depends** is clicked, this displays an hierarchical view of objects on which the selected object depends.</span></span>  
  
 <span data-ttu-id="82f5e-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="82f5e-119">**Name**</span></span>  
 <span data-ttu-id="82f5e-120">显示上面“依赖关系”  树视图中所选对象的名称。</span><span class="sxs-lookup"><span data-stu-id="82f5e-120">Displays the name of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="82f5e-121">类型 </span><span class="sxs-lookup"><span data-stu-id="82f5e-121">**Type**</span></span>  
 <span data-ttu-id="82f5e-122">显示上面“依赖关系”  树视图中所选对象的类型。</span><span class="sxs-lookup"><span data-stu-id="82f5e-122">Displays the type of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="82f5e-123">**上次同步时间**</span><span class="sxs-lookup"><span data-stu-id="82f5e-123">**Last Sync Time**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="82f5e-124">仅在“高级”  页上提供此选项。</span><span class="sxs-lookup"><span data-stu-id="82f5e-124">This option is available only on the **Advanced** page.</span></span>  
  
 <span data-ttu-id="82f5e-125">指定上次更新依赖关系信息的时间和日期。</span><span class="sxs-lookup"><span data-stu-id="82f5e-125">Specifies the time and date when the dependency information was last updated.</span></span>  
  
 <span data-ttu-id="82f5e-126">**依赖关系类型**</span><span class="sxs-lookup"><span data-stu-id="82f5e-126">**Dependency type**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="82f5e-127">仅在“常规”  页上提供此选项。</span><span class="sxs-lookup"><span data-stu-id="82f5e-127">This option is available only on the **General** page.</span></span>  
  
 <span data-ttu-id="82f5e-128">显示两个对象之间的依赖关系的类型。</span><span class="sxs-lookup"><span data-stu-id="82f5e-128">Displays the type of dependency between two objects.</span></span> <span data-ttu-id="82f5e-129">可以是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="82f5e-129">Can be one of the following:</span></span>  
  
-   <span data-ttu-id="82f5e-130">架构绑定依赖关系</span><span class="sxs-lookup"><span data-stu-id="82f5e-130">Schema-bound dependency</span></span>  
  
     <span data-ttu-id="82f5e-131">是两个对象之间的一种关系，只要引用对象存在，这种关系就可防止删除或修改被引用的对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-131">Is a relationship between two objects that prevents the referenced object from being dropped or modified as long as the referencing object exists.</span></span> <span data-ttu-id="82f5e-132">当通过使用 WITH SCHEMABINDING 子句创建视图或用户定义的函数时，或者当表通过 CHECK 或 DEFAULT 约束或在计算列的定义中引用另一对象时，将创建架构绑定依赖关系。</span><span class="sxs-lookup"><span data-stu-id="82f5e-132">A schema-bound dependency is created when a view or user-defined function is created by using the WITH SCHEMABINDING clause, or when a table references another object through a CHECK or DEFAULT constraint or in the definition of a computed column.</span></span>  
  
-   <span data-ttu-id="82f5e-133">非架构绑定依赖关系</span><span class="sxs-lookup"><span data-stu-id="82f5e-133">Non-schema-bound dependency</span></span>  
  
     <span data-ttu-id="82f5e-134">是两个对象之间的一种关系，这种关系不能防止删除或修改被引用的对象。</span><span class="sxs-lookup"><span data-stu-id="82f5e-134">Is a relationship between two objects that does not prevent the referenced object from being dropped or modified.</span></span>  
  
-   <span data-ttu-id="82f5e-135">不可用或未解析的实体</span><span class="sxs-lookup"><span data-stu-id="82f5e-135">Not available or Unresolved Entity</span></span>  
  
     <span data-ttu-id="82f5e-136">指示无法确定依赖关系的类型。</span><span class="sxs-lookup"><span data-stu-id="82f5e-136">Indicates the dependency type cannot be determined.</span></span> <span data-ttu-id="82f5e-137">只有所选对象位于早于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]实例上时才会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="82f5e-137">This occurs only when the selected object is on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
  
