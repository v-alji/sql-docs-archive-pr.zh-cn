---
title: 选择对象（对象资源管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.selectobjects.f1
ms.assetid: 692477fe-dd7c-403d-acd2-bb108b6077f1
author: stevestein
ms.author: sstein
ms.openlocfilehash: ceec604d9fe07b339af11ed69226d41a7f616678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682639"
---
# <a name="select-objects-object-explorer"></a><span data-ttu-id="de2fb-102">选择对象（对象资源管理器）</span><span class="sxs-lookup"><span data-stu-id="de2fb-102">Select Objects (Object Explorer)</span></span>
  <span data-ttu-id="de2fb-103">使用“选择对象”  对话框可以向另一个对话框的列表中添加对象。</span><span class="sxs-lookup"><span data-stu-id="de2fb-103">Use the **Select Objects** dialog box to add an object to a list in another dialog box.</span></span> <span data-ttu-id="de2fb-104">对话框的标题以及对话框中可用的选项取决于该对话框的打开方式。</span><span class="sxs-lookup"><span data-stu-id="de2fb-104">The dialog box title and the options available in the dialog box depend upon how it was opened.</span></span> <span data-ttu-id="de2fb-105">只显示可用的选项，例如，当您为新对象选择所有者时，只有登录名选项可用。</span><span class="sxs-lookup"><span data-stu-id="de2fb-105">Only available options appear; for instance, only logins are available when you are selecting an owner for a new object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="de2fb-106">选项</span><span class="sxs-lookup"><span data-stu-id="de2fb-106">Options</span></span>  
 <span data-ttu-id="de2fb-107">**选择这些对象类型**</span><span class="sxs-lookup"><span data-stu-id="de2fb-107">**Select these object types**</span></span>  
 <span data-ttu-id="de2fb-108">显示类型列表，将选择属于所列类型的对象。</span><span class="sxs-lookup"><span data-stu-id="de2fb-108">Displays a list of the types of which the objects to be selected belong.</span></span> <span data-ttu-id="de2fb-109">这些类型包括 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 级别和数据库级别的主体和安全对象。</span><span class="sxs-lookup"><span data-stu-id="de2fb-109">The types include [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] level and database level principals and securables.</span></span> <span data-ttu-id="de2fb-110">此框使用从“选择对象类型”  对话框（可使用“对象类型”  按钮进行访问）中选择的选项进行填充。</span><span class="sxs-lookup"><span data-stu-id="de2fb-110">This box is populated from the selections made from the **Select Object Types** dialog box, accessed from the **Objects Type** button.</span></span>  
  
 <span data-ttu-id="de2fb-111">**输入要选择的对象名称**</span><span class="sxs-lookup"><span data-stu-id="de2fb-111">**Enter the object names to select**</span></span>  
 <span data-ttu-id="de2fb-112">输入要选择的对象名称列表，用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="de2fb-112">Enter a semicolon-separated list of names of the objects to be selected.</span></span> <span data-ttu-id="de2fb-113">要选择的对象必须属于在“选择这些对象类型”  框中列出的类型。</span><span class="sxs-lookup"><span data-stu-id="de2fb-113">Objects to be selected must be of a type listed in the **Select these object types** box.</span></span> <span data-ttu-id="de2fb-114">可从单击“浏览”  按钮所访问的列表中选择对象。</span><span class="sxs-lookup"><span data-stu-id="de2fb-114">Objects can be selected from a list accessed by clicking the **Browse** button.</span></span>  
  
 <span data-ttu-id="de2fb-115">**对象类型**</span><span class="sxs-lookup"><span data-stu-id="de2fb-115">**Object Types**</span></span>  
 <span data-ttu-id="de2fb-116">显示对象类型列表。</span><span class="sxs-lookup"><span data-stu-id="de2fb-116">Displays a list of object types.</span></span> <span data-ttu-id="de2fb-117">通过选中与类型相应的复选框选择一个或多个类型。</span><span class="sxs-lookup"><span data-stu-id="de2fb-117">Select one or more by selecting the check box corresponding to the type.</span></span>  
  
 <span data-ttu-id="de2fb-118">**检查名称**</span><span class="sxs-lookup"><span data-stu-id="de2fb-118">**Check Names**</span></span>  
 <span data-ttu-id="de2fb-119">验证“输入要选择的对象名称”  框中的对象名称。</span><span class="sxs-lookup"><span data-stu-id="de2fb-119">Validates the object names in the **Enter the object names to select** box.</span></span> <span data-ttu-id="de2fb-120">如果列出的对象名称无效，则会显示“找不到名称”  对话框。</span><span class="sxs-lookup"><span data-stu-id="de2fb-120">If an object name that is not valid is listed, the **Name not Found** dialog box is presented.</span></span> <span data-ttu-id="de2fb-121">使用此对话框，可以更正对象名称，也可以从要选择的对象列表中删除对象名称。</span><span class="sxs-lookup"><span data-stu-id="de2fb-121">With this dialog box, the name can be corrected or removed from the list of objects to select.</span></span>  
  
 <span data-ttu-id="de2fb-122">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="de2fb-122">**Browse**</span></span>  
 <span data-ttu-id="de2fb-123">显示“查找对象”  对话框。</span><span class="sxs-lookup"><span data-stu-id="de2fb-123">Presents the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="de2fb-124">该对话框包含“选择这些对象类型”  框中所列类型的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="de2fb-124">This contains a list of objects of the types listed in the **Select These Object Types** box.</span></span> <span data-ttu-id="de2fb-125">通过选中相应的复选框可以从该列表中选择对象。</span><span class="sxs-lookup"><span data-stu-id="de2fb-125">Select objects from this list by selecting the corresponding check boxes.</span></span>  
  
  
