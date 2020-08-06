---
title: 创建和管理 (SSAS 表格) 的透视 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d0029ff61aa05e2e83f34833c3d0af17ddb3beb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578491"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a><span data-ttu-id="f0d1c-102">创建和管理透视（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="f0d1c-102">Create and Manage Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="f0d1c-103">透视定义某一模型的可查看子集，借此您可以将注意力集中在该模型中的特定业务或特定应用上。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-103">Perspectives define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span> <span data-ttu-id="f0d1c-104">本主题中的任务说明如何使用模型设计器中的 **“透视”** 对话框来创建和管理透视。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-104">The tasks in this topic describe how to create and manage perspectives by using the **Perspectives** dialog box in the model designer.</span></span>  
  
 <span data-ttu-id="f0d1c-105">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="f0d1c-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="f0d1c-106">添加透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-106">To add a perspective</span></span>](#bkmk_add)  
  
-   [<span data-ttu-id="f0d1c-107">编辑透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-107">To edit a perspective</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="f0d1c-108">重命名透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-108">To rename a perspective</span></span>](#bkmk_rename)  
  
-   [<span data-ttu-id="f0d1c-109">删除透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-109">To delete a perspective</span></span>](#bkmk_delete)  
  
-   [<span data-ttu-id="f0d1c-110">复制透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-110">To copy a perspective</span></span>](#bkmk_copy)  
  
## <a name="tasks"></a><span data-ttu-id="f0d1c-111">任务</span><span class="sxs-lookup"><span data-stu-id="f0d1c-111">Tasks</span></span>  
 <span data-ttu-id="f0d1c-112">为了创建透视，您将使用 **“透视”** 对话框，您可以在此添加、编辑、删除、复制和查看透视。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-112">To create perspectives, you will use the **Perspectives** dialog box, where you can add, edit, delete, copy, and view perspectives.</span></span> <span data-ttu-id="f0d1c-113">若要查看 **“透视”** 对话框，请在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中单击 **“模型”** 菜单，然后单击 **“透视”**。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-113">To view the **Perspectives** dialog box, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click on the **Model** menu, and then click **Perspectives**.</span></span>  
  
###  <a name="to-add-a-perspective"></a><a name="bkmk_add"></a> <span data-ttu-id="f0d1c-114">添加透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-114">To add a perspective</span></span>  
  
-   <span data-ttu-id="f0d1c-115">若要添加新的透视，请单击 **“新建透视”**。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-115">To add a new perspective, click **New Perspective**.</span></span> <span data-ttu-id="f0d1c-116">然后，您可以选中和取消选中要包括的字段对象，并为新的透视提供名称。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-116">You can then check and uncheck field objects to be included and provide a name for the new perspective.</span></span>  
  
     <span data-ttu-id="f0d1c-117">如果您创建具有所有字段对象字段的一个空透视，则使用该透视的用户将看到一个空的字段列表。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-117">If you create an empty perspective with all of the field object fields, then a user using this perspective will see an empty Field List.</span></span> <span data-ttu-id="f0d1c-118">透视应包含至少一个表和列。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-118">Perspectives should contain at least one table and column.</span></span>  
  
###  <a name="to-edit-a-perspective"></a><a name="bkmk_edit"></a><span data-ttu-id="f0d1c-119">编辑透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-119">To edit a perspective</span></span>  
  
-   <span data-ttu-id="f0d1c-120">若要修改透视，请选中和取消选中透视的列中的字段，这将从透视中添加和删除字段对象。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-120">To modify a perspective, check and uncheck fields in the perspective's column, which adds and removes field objects from the perspective.</span></span>  
  
###  <a name="to-rename-a-perspective"></a><a name="bkmk_rename"></a><span data-ttu-id="f0d1c-121">重命名透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-121">To rename a perspective</span></span>  
  
-   <span data-ttu-id="f0d1c-122">当鼠标悬停在透视的列标题上时 (透视) 的名称时，将显示 "**重命名**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-122">When you hover over a perspective's column header (the name of the perspective), the **Rename** button appears.</span></span> <span data-ttu-id="f0d1c-123">若要重命名该透视，请单击 **“重命名”**，然后输入新名称或编辑现有名称。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-123">To rename the perspective, click **Rename**, and then enter a new name or edit the existing name.</span></span>  
  
###  <a name="to-delete-a-perspective"></a><a name="bkmk_delete"></a><span data-ttu-id="f0d1c-124">删除透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-124">To delete a perspective</span></span>  
  
-   <span data-ttu-id="f0d1c-125">当鼠标悬停在透视的列标题上时 (透视) 的名称时，将显示 "**删除**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-125">When you hover over a perspective's column header (the name of the perspective), the **Delete** button appears.</span></span> <span data-ttu-id="f0d1c-126">若要删除透视，请单击 **“删除”** 按钮，然后在确认窗口中单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-126">To delete the perspective, click the **Delete** button, and then click **Yes** in the confirmation window.</span></span>  
  
###  <a name="to-copy-a-perspective"></a><a name="bkmk_copy"></a><span data-ttu-id="f0d1c-127">复制透视</span><span class="sxs-lookup"><span data-stu-id="f0d1c-127">To copy a perspective</span></span>  
  
-   <span data-ttu-id="f0d1c-128">当您将鼠标指针悬停在透视的列标题上时，"**复制**" 按钮将出现。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-128">When you hover over a perspective's column header, the **Copy** button appears.</span></span> <span data-ttu-id="f0d1c-129">若要创建该透视的副本，请单击 **“复制”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-129">To create a copy of that perspective, click the **Copy** button.</span></span> <span data-ttu-id="f0d1c-130">所选透视的副本将作为新透视添加到现有透视的右侧。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-130">A copy of the selected perspective is added as a new perspective to the right of existing perspectives.</span></span> <span data-ttu-id="f0d1c-131">新的透视将继承复制的透视的名称，并且“复制”\*\* 批注将追加到名称的末尾。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-131">The new perspective inherits the name of the copied perspective and a *- Copy* annotation is appended to the end of the name.</span></span> <span data-ttu-id="f0d1c-132">例如，如果创建了*sales*透视的副本，则新的透视称为*销售-副本*。</span><span class="sxs-lookup"><span data-stu-id="f0d1c-132">For example, if a copy of the *Sales* perspective is created, the new perspective is called *Sales - Copy*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d1c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0d1c-133">See Also</span></span>  
 <span data-ttu-id="f0d1c-134">[SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="f0d1c-134">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="f0d1c-135">层次结构（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="f0d1c-135">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
