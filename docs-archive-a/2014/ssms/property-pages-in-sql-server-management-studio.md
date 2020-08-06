---
title: SQL Server Management Studio 中的属性页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- property pages [SQL Server Management Studio]
ms.assetid: 719282c3-e9cc-4e0e-9a83-7fb8b8b17f67
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3fae6a07fbaa2a259fcca5c3807094b31e0d52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692083"
---
# <a name="property-pages-in-sql-server-management-studio"></a><span data-ttu-id="4f234-102">SQL Server Management Studio 中的属性页</span><span class="sxs-lookup"><span data-stu-id="4f234-102">Property Pages in SQL Server Management Studio</span></span>
  <span data-ttu-id="4f234-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的属性页对话框均使用可展开和折叠类别的通用格式显示信息。</span><span class="sxs-lookup"><span data-stu-id="4f234-103">Property page dialog boxes in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] all use a common format displaying information with expanding and collapsing categories.</span></span> <span data-ttu-id="4f234-104">显示的字段取决于具体的属性。</span><span class="sxs-lookup"><span data-stu-id="4f234-104">The fields shown depend on the particular property.</span></span> <span data-ttu-id="4f234-105">显示为灰色的属性为只读属性。</span><span class="sxs-lookup"><span data-stu-id="4f234-105">Properties shown in gray are read-only.</span></span> <span data-ttu-id="4f234-106">“按分类顺序”和“字母顺序”按钮位于每个属性页的顶部附近。</span><span class="sxs-lookup"><span data-stu-id="4f234-106">Categorized and Alphabetic buttons are near the top of each property page.</span></span>  
  
 <span data-ttu-id="4f234-107">下表对 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 属性页对话框的常用元素进行了说明。</span><span class="sxs-lookup"><span data-stu-id="4f234-107">The following table describes the common elements of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] property page dialog boxes.</span></span>  
  
|<span data-ttu-id="4f234-108">元素</span><span class="sxs-lookup"><span data-stu-id="4f234-108">Element</span></span>|<span data-ttu-id="4f234-109">说明</span><span class="sxs-lookup"><span data-stu-id="4f234-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f234-110">**按分类顺序**</span><span class="sxs-lookup"><span data-stu-id="4f234-110">**Categorized**</span></span>|<span data-ttu-id="4f234-111">按类别列出所选对象的所有属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="4f234-111">Lists all properties and property values for the selected object, sorted by category.</span></span> <span data-ttu-id="4f234-112">在类别视图中，可以将类别折叠起来以减少可见属性的数量。</span><span class="sxs-lookup"><span data-stu-id="4f234-112">In category view, you can collapse a category to reduce the number of visible properties.</span></span> <span data-ttu-id="4f234-113">折叠或展开类别时，类别名称的左侧将显示一个加号 (+) 或减号 (-)。</span><span class="sxs-lookup"><span data-stu-id="4f234-113">When you expand or collapse a category, you see a plus sign (+) or minus sign (-) to the left of the category name.</span></span> <span data-ttu-id="4f234-114">类别按字母顺序列出。</span><span class="sxs-lookup"><span data-stu-id="4f234-114">Categories are listed alphabetically.</span></span>|  
|<span data-ttu-id="4f234-115">**字母顺序**</span><span class="sxs-lookup"><span data-stu-id="4f234-115">**Alphabetic**</span></span>|<span data-ttu-id="4f234-116">按字母顺序列出所选对象的所有属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="4f234-116">Lists all properties and property values for the selected object, sorted alphabetically.</span></span>|  
|<span data-ttu-id="4f234-117">属性名称</span><span class="sxs-lookup"><span data-stu-id="4f234-117">Property name</span></span>|<span data-ttu-id="4f234-118">网格中的第一列列出属性名称。</span><span class="sxs-lookup"><span data-stu-id="4f234-118">The first column in the grid lists the property names.</span></span>|  
|<span data-ttu-id="4f234-119">属性</span><span class="sxs-lookup"><span data-stu-id="4f234-119">Properties</span></span>|<span data-ttu-id="4f234-120">网格中的第二列列出属性值。</span><span class="sxs-lookup"><span data-stu-id="4f234-120">The second column in the grid lists the property values.</span></span>|  
|<span data-ttu-id="4f234-121">说明窗格</span><span class="sxs-lookup"><span data-stu-id="4f234-121">Description pane</span></span>|<span data-ttu-id="4f234-122">说明窗格显示在属性页的底部，可以显示属性的类型和简短说明。</span><span class="sxs-lookup"><span data-stu-id="4f234-122">The description pane appears at the bottom of the page and shows the property type and a short description of the property.</span></span> <span data-ttu-id="4f234-123">可以使用快捷菜单上的“说明”  命令打开或关闭属性的说明。</span><span class="sxs-lookup"><span data-stu-id="4f234-123">You can turn the description of the property off and on using the **Description** command on the shortcut menu.</span></span>|  
  
  
