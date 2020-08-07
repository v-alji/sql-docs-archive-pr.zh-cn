---
title: " (报表管理器) 的 \"新建链接报表\" 页 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61138e51cfd9bb6e1ee124dd4aa3bc224d8aebcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588937"
---
# <a name="new-linked-report-page-report-manager"></a><span data-ttu-id="38e0f-102">“新建链接报表”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="38e0f-102">New Linked Report Page (Report Manager)</span></span>
  <span data-ttu-id="38e0f-103">使用“新建链接报表”页可以创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-103">Use the New Linked Report page to create a linked report.</span></span> <span data-ttu-id="38e0f-104">链接报表是指具有自己的设置和属性、但链接到其他报表的报表定义的报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-104">A linked report is a report with settings and properties of its own, but links to the report definition of another report.</span></span> <span data-ttu-id="38e0f-105">如果您有一个基础报表并且希望在它的基础上针对特定组或特定用户加以改动，则链接报表很有用；根据您指定为参数的区域代码返回不同数据的区域报表便是链接报表的一个例子。</span><span class="sxs-lookup"><span data-stu-id="38e0f-105">Linked reports are useful when you have a base report that you want to vary for specific groups or users; for example, a regional report that returns different data based on a regional code that you specify as a parameter.</span></span> <span data-ttu-id="38e0f-106">链接报表通常是通过参数化报表创建。如果您希望每个报表具有不同的参数值，则可以为每个报表实例保存不同的参数值以创建参数化报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-106">A linked report is typically created from a parameterized report when you want to vary and then save different parameter values with each report instance.</span></span> <span data-ttu-id="38e0f-107">不过，您也可以通过有权访问的任何报表创建链接报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-107">However, you can create a linked report from any report to which you have access.</span></span>  
  
 <span data-ttu-id="38e0f-108">链接报表可以具有自己的名称、说明、位置、参数属性、报表执行属性、报表历史记录属性、权限和订阅。</span><span class="sxs-lookup"><span data-stu-id="38e0f-108">A linked report can have its own name, description, location, parameter properties, report execution properties, report history properties, permissions, and subscriptions.</span></span> <span data-ttu-id="38e0f-109">但是，链接报表必须使用提供报表定义的基础报表的数据源属性和布局。</span><span class="sxs-lookup"><span data-stu-id="38e0f-109">However, a linked report must use the data source properties and layout of the base report that provides the report definition.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="38e0f-110">导航</span><span class="sxs-lookup"><span data-stu-id="38e0f-110">Navigation</span></span>  
 <span data-ttu-id="38e0f-111">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="38e0f-111">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a><span data-ttu-id="38e0f-112">从“内容”页打开“新建链接报表”页</span><span class="sxs-lookup"><span data-stu-id="38e0f-112">To open the New Linked Report page from the Contents page</span></span>  
  
1.  <span data-ttu-id="38e0f-113">打开报表管理器，找到要创建链接报表的报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-113">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="38e0f-114">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="38e0f-114">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="38e0f-115">在下拉菜单中，单击 **“创建链接报表”**。</span><span class="sxs-lookup"><span data-stu-id="38e0f-115">In the drop-down menu, click **Create Linked Report**.</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a><span data-ttu-id="38e0f-116">从报表的“常规属性”页打开“新建链接报表”页</span><span class="sxs-lookup"><span data-stu-id="38e0f-116">To open the New Linked Report page from the General properties page of a report</span></span>  
  
1.  <span data-ttu-id="38e0f-117">打开报表管理器，找到要创建链接报表的报表。</span><span class="sxs-lookup"><span data-stu-id="38e0f-117">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="38e0f-118">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="38e0f-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="38e0f-119">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="38e0f-119">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="38e0f-120">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="38e0f-120">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="38e0f-121">在项工具栏中，单击 **“创建链接报表”**。</span><span class="sxs-lookup"><span data-stu-id="38e0f-121">In the item toolbar, click **Create Linked Report**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="38e0f-122">选项</span><span class="sxs-lookup"><span data-stu-id="38e0f-122">Options</span></span>  
 <span data-ttu-id="38e0f-123">**名称**</span><span class="sxs-lookup"><span data-stu-id="38e0f-123">**Name**</span></span>  
 <span data-ttu-id="38e0f-124">指定链接报表的名称。</span><span class="sxs-lookup"><span data-stu-id="38e0f-124">Specify the name of the linked report.</span></span> <span data-ttu-id="38e0f-125">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="38e0f-125">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="38e0f-126">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="38e0f-126">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="38e0f-127">但是，指定名称时不得使用字符 ; ?</span><span class="sxs-lookup"><span data-stu-id="38e0f-127">However, you must not use the characters ; ?</span></span> <span data-ttu-id="38e0f-128">： \@ & = +，$/\* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="38e0f-128">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="38e0f-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="38e0f-129">**Description**</span></span>  
 <span data-ttu-id="38e0f-130">键入对报表内容的说明。</span><span class="sxs-lookup"><span data-stu-id="38e0f-130">Type a description of the report contents.</span></span> <span data-ttu-id="38e0f-131">有权访问该报表的用户可以在“内容”页中查看此说明。</span><span class="sxs-lookup"><span data-stu-id="38e0f-131">This description appears in the Contents page to users who have permission to access the report.</span></span>  
  
 <span data-ttu-id="38e0f-132">**位置**</span><span class="sxs-lookup"><span data-stu-id="38e0f-132">**Location**</span></span>  
 <span data-ttu-id="38e0f-133">指定包含该报表的文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="38e0f-133">Specify the folder path that contains the report.</span></span> <span data-ttu-id="38e0f-134">默认情况下，链接报表创建时位于基础报表所在的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="38e0f-134">By default, linked reports are created as siblings to the base report.</span></span> <span data-ttu-id="38e0f-135">单击 **“更改位置”** 可以将链接报表放入其他文件夹。</span><span class="sxs-lookup"><span data-stu-id="38e0f-135">Click **Change Location** to put the linked report in a different folder.</span></span>  
  
 <span data-ttu-id="38e0f-136">**确定**</span><span class="sxs-lookup"><span data-stu-id="38e0f-136">**OK**</span></span>  
 <span data-ttu-id="38e0f-137">单击 **“确定”** 可以保存更改并返回基础报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="38e0f-137">Click **OK** to save your changes and return to the General properties page of the base report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e0f-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38e0f-138">See Also</span></span>  
 <span data-ttu-id="38e0f-139">[创建链接报表](reports/create-a-linked-report.md) </span><span class="sxs-lookup"><span data-stu-id="38e0f-139">[Create a Linked Report](reports/create-a-linked-report.md) </span></span>  
 <span data-ttu-id="38e0f-140">[报表 &#40;报表管理器的 "常规属性" 页&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="38e0f-140">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="38e0f-141">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="38e0f-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
