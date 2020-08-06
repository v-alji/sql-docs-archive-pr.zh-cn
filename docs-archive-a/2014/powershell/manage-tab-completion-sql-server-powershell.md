---
title: 管理 Tab 填写功能 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72bcf96245c536d6ea444bc1d7964b7579e793c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591436"
---
# <a name="manage-tab-completion-sql-server-powershell"></a><span data-ttu-id="9f8ed-102">管理 Tab 填写功能 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9f8ed-102">Manage Tab Completion (SQL Server PowerShell)</span></span>
  <span data-ttu-id="9f8ed-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 管理单元引入了三个变量（`$SqlServerMaximumTabCompletion`、`$SqlServerMaximumChildItems` 和 `$SqlServerIncludeSystemObjects`）来控制 Windows PowerShell 的 Tab 填写功能。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins introduce three variables (`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems`, and `$SqlServerIncludeSystemObjects`) to control Windows PowerShell tab completion.</span></span> <span data-ttu-id="9f8ed-104">Tab 填写功能通过返回名称以您正在键入的字符串开头的项目的表，而减少了必须键入的内容量。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-104">Tab completion reduces the amount of typing you must do by returning tables of items whose names start with the string you are typing.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="9f8ed-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="9f8ed-105">Before You Begin</span></span>  
 <span data-ttu-id="9f8ed-106">使用 Windows PowerShell 的 Tab 填写功能，在键入路径或 cmdlet 名称的一部分之后，可以按 Tab 键获得其名称与已键入内容相匹配的项列表。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-106">With Windows PowerShell tab-completion, when you have typed part of a path or cmdlet name, you can hit the Tab key to get a list of the items whose names match what you have already typed.</span></span> <span data-ttu-id="9f8ed-107">之后，可以从该列表中选择所需的项，而不必键入该名称的其余部分。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-107">You can then select the item you want from the list without having to type the rest of the name.</span></span>  
  
 <span data-ttu-id="9f8ed-108">如果正在处理的数据库中包含大量对象，则 Tab 填写列表可能会变得非常大。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-108">If you are working in a database that has a lot of objects, the tab-completion lists can become very large.</span></span> <span data-ttu-id="9f8ed-109">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象类型（如视图）也具有大量系统对象。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-109">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] object types, such as views, also have large numbers of system objects.</span></span>  
  
 <span data-ttu-id="9f8ed-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理单元引入了三个可用来控制由 Tab 补全和 **Get-ChildItem**所提供的信息量的系统变量。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins introduces three system variables that you can use to control the amount of information presented by tab-completion and **Get-ChildItem**.</span></span>  
  
 <span data-ttu-id="9f8ed-111">**$SqlServerMaximumTabCompletion =** *n*</span><span class="sxs-lookup"><span data-stu-id="9f8ed-111">**$SqlServerMaximumTabCompletion =** *n*</span></span>  
 <span data-ttu-id="9f8ed-112">指定要包括在 Tab 填写列表中的对象的最大数量。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-112">Specifies the maximum number of objects to include in a tab-completion list.</span></span> <span data-ttu-id="9f8ed-113">如果你在具有多于 *n* 个对象的路径节点处选择 Tab，则 Tab 补全列表会在 *n*处被截断。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-113">If you select Tab at a path node having more than *n* objects, the tab-completion list is truncated at *n*.</span></span> <span data-ttu-id="9f8ed-114">*n* 为整数。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-114">*n* is an integer.</span></span> <span data-ttu-id="9f8ed-115">默认设置为 0，表示对所列出对象的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-115">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="9f8ed-116">**$SqlServerMaximumChildItems =** *n*</span><span class="sxs-lookup"><span data-stu-id="9f8ed-116">**$SqlServerMaximumChildItems =** *n*</span></span>  
 <span data-ttu-id="9f8ed-117">指定由 **Get-ChildItem**显示的对象的最大数量。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-117">Specifies the maximum number of objects displayed by **Get-ChildItem**.</span></span> <span data-ttu-id="9f8ed-118">如果在具有多于 **n** 个对象的路径节点处运行 *Get-ChildItem* ，则该列表会在 *n*处被截断。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-118">If **Get-ChildItem** is run at a path node having more than *n* objects, the list is truncated at *n*.</span></span> <span data-ttu-id="9f8ed-119">*n* 为整数。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-119">*n* is an integer.</span></span> <span data-ttu-id="9f8ed-120">默认设置为 0，表示对所列出对象的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-120">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="9f8ed-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span><span class="sxs-lookup"><span data-stu-id="9f8ed-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span></span>  
 <span data-ttu-id="9f8ed-122">如果为 **$True**，则 Tab 补全和 **Get-ChildItem**将显示系统对象。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-122">If **$True**, system objects are displayed by tab-completion and **Get-ChildItem**.</span></span> <span data-ttu-id="9f8ed-123">如果为 **$False**，则将不显示系统对象。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-123">If **$False**, no system objects are displayed.</span></span> <span data-ttu-id="9f8ed-124">默认设置为 **$False**。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-124">The default setting is **$False**.</span></span>  
  
## <a name="set-the-sql-server-tab-completion-variables"></a><span data-ttu-id="9f8ed-125">设置 SQL Server 的 Tab 填写变量</span><span class="sxs-lookup"><span data-stu-id="9f8ed-125">Set the SQL Server Tab Completion Variables</span></span>  
 <span data-ttu-id="9f8ed-126">对于您要更改其默认值的任何变量，将该变量设置为新值。</span><span class="sxs-lookup"><span data-stu-id="9f8ed-126">For any of the variables you want to change from the default value, set the variable to the new value.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="9f8ed-127">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9f8ed-127">Example (PowerShell)</span></span>  
 <span data-ttu-id="9f8ed-128">以下示例将对所有三个变量进行设置并列出其设置：</span><span class="sxs-lookup"><span data-stu-id="9f8ed-128">The following example sets all three variables and lists their settings:</span></span>  
  
```powershell
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f8ed-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f8ed-129">See Also</span></span>  
 [<span data-ttu-id="9f8ed-130">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f8ed-130">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
