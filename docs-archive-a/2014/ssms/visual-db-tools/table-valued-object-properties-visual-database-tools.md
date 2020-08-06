---
title: 表值对象属性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f1c1e6414d0059dfd1d43bbbb40eabdfc9470b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691457"
---
# <a name="table-valued-object-properties-visual-database-tools"></a><span data-ttu-id="8233c-102">表值对象属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8233c-102">Table-Valued Object Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="8233c-103">在 **查询设计器和视图设计器**中选择表值对象时，这些属性将显示在“属性”窗口中。</span><span class="sxs-lookup"><span data-stu-id="8233c-103">These properties appear in the Properties window when you select a table-valued object in **Query and View Designer**.</span></span> <span data-ttu-id="8233c-104">表值对象可以是视图、同义词、派生表和表值函数。</span><span class="sxs-lookup"><span data-stu-id="8233c-104">The table-valued object could be a view, synonym, derived table, or table-valued function.</span></span> <span data-ttu-id="8233c-105">除非另行说明，否则这些属性在“属性”  窗口中为只读。</span><span class="sxs-lookup"><span data-stu-id="8233c-105">Unless otherwise noted, these properties are read-only in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8233c-106">本主题中的属性按类别排序，而不是按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="8233c-106">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8233c-107">根据当前设置或版本的不同，所看到的对话框和菜单命令可能与帮助中描述的对话框和菜单命令有所不同。</span><span class="sxs-lookup"><span data-stu-id="8233c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8233c-108">若要更改设置，请在“工具”菜单上选择“导入和导出设置”。</span><span class="sxs-lookup"><span data-stu-id="8233c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="8233c-109">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="8233c-109">**Identity Category**</span></span>  
 <span data-ttu-id="8233c-110">展开此项可显示“名称”  和“TVO 类型”  属性。</span><span class="sxs-lookup"><span data-stu-id="8233c-110">Expands to show the **Name** and **TVO Type** properties.</span></span>  
  
 <span data-ttu-id="8233c-111">**名称**</span><span class="sxs-lookup"><span data-stu-id="8233c-111">**Name**</span></span>  
 <span data-ttu-id="8233c-112">显示所选表值对象的名称。</span><span class="sxs-lookup"><span data-stu-id="8233c-112">Shows the name of the selected table-valued object.</span></span>  
  
 <span data-ttu-id="8233c-113">**TVO 类型**</span><span class="sxs-lookup"><span data-stu-id="8233c-113">**TVO Type**</span></span>  
 <span data-ttu-id="8233c-114">显示表值对象的类型。</span><span class="sxs-lookup"><span data-stu-id="8233c-114">Shows which type of table-valued object.</span></span> <span data-ttu-id="8233c-115">其类型可以是基表、视图、表值函数或派生表。</span><span class="sxs-lookup"><span data-stu-id="8233c-115">It can be either a base table, view, table-valued function, or a derived table.</span></span>  
  
 <span data-ttu-id="8233c-116">**查询设计器类别**</span><span class="sxs-lookup"><span data-stu-id="8233c-116">**Query DesignerCategory**</span></span>  
 <span data-ttu-id="8233c-117">展开此项可显示“别名”  、“列列表”  、“全名”  和“参数列表”  属性。</span><span class="sxs-lookup"><span data-stu-id="8233c-117">Expands to show properties for **Alias**, **Column List**, **Full Name**, and **Parameter List**.</span></span>  
  
 <span data-ttu-id="8233c-118">**Alias**</span><span class="sxs-lookup"><span data-stu-id="8233c-118">**Alias**</span></span>  
 <span data-ttu-id="8233c-119">显示所选表值对象的别名。</span><span class="sxs-lookup"><span data-stu-id="8233c-119">Shows the alias for the selected table-valued object.</span></span> <span data-ttu-id="8233c-120">若要添加或更改别名，请在字段中键入相应内容。</span><span class="sxs-lookup"><span data-stu-id="8233c-120">To add or change an alias, type it into the field.</span></span>  
  
 <span data-ttu-id="8233c-121">**列列表**</span><span class="sxs-lookup"><span data-stu-id="8233c-121">**Column List**</span></span>  
 <span data-ttu-id="8233c-122">显示所选表值对象中包含的列。</span><span class="sxs-lookup"><span data-stu-id="8233c-122">Shows the columns included in the selected table-valued object.</span></span> <span data-ttu-id="8233c-123">若要在单独的窗口中查看这些列，请单击“列列表”，再单击属性右侧的省略号 (…)。</span><span class="sxs-lookup"><span data-stu-id="8233c-123">To see them in a separate window, click Column List and then click the ellipses (...) to the right of the property.</span></span>  
  
 <span data-ttu-id="8233c-124">**全名**</span><span class="sxs-lookup"><span data-stu-id="8233c-124">**Full Name**</span></span>  
 <span data-ttu-id="8233c-125">显示所选表值对象的名称，包括诸如对象的架构或数据源之类的其他信息。</span><span class="sxs-lookup"><span data-stu-id="8233c-125">Shows the name of the selected table-valued object, including additional information such as the schema or data source of the object.</span></span>  
  
 <span data-ttu-id="8233c-126">**参数列表**</span><span class="sxs-lookup"><span data-stu-id="8233c-126">**Parameter List**</span></span>  
 <span data-ttu-id="8233c-127">显示为所选表值函数定义的参数。</span><span class="sxs-lookup"><span data-stu-id="8233c-127">Shows the parameters defined for selected table-valued function.</span></span> <span data-ttu-id="8233c-128">若要为这些参数定义值，请单击“参数列表”，再单击属性右侧的省略号 (…)。</span><span class="sxs-lookup"><span data-stu-id="8233c-128">To define a value for the parameters, click Parameter List and then click the ellipses (...) to the right of the property.</span></span> <span data-ttu-id="8233c-129">在“函数参数”对话框中，键入相应的值。</span><span class="sxs-lookup"><span data-stu-id="8233c-129">In the Function Parameters dialog box, type in values.</span></span> <span data-ttu-id="8233c-130">只有在选择了表值函数时，此属性才可用。</span><span class="sxs-lookup"><span data-stu-id="8233c-130">This property is only available when a table-valued function is selected.</span></span>  
  
  
