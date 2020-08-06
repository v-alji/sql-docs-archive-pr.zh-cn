---
title: 使用“我的报表”（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91d44c0aa8471064753d9b4fb0ecc0de89aa8396
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580005"
---
# <a name="using-my-reports-report-builder-and-ssrs"></a><span data-ttu-id="87979-102">使用“我的报表”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="87979-102">Using My Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="87979-103">在配置为本机模式的报表服务器上，“我的报表”文件夹是一个个人工作区，您可以用它来存储和处理自己的报表。</span><span class="sxs-lookup"><span data-stu-id="87979-103">On a report server configured in native mode, the My Reports folder is a personal workspace that you can use to store and work with reports that you own.</span></span> <span data-ttu-id="87979-104">其他报表服务器文件夹都是公用文件夹，通常要求用户具有高级权限才能添加或修改文件夹内容。</span><span class="sxs-lookup"><span data-stu-id="87979-104">Other report server folders are public and typically require users to have advanced permissions to add to or modify folder contents.</span></span> <span data-ttu-id="87979-105">相反，“我的报表”文件夹则是用户管理的工作区。</span><span class="sxs-lookup"><span data-stu-id="87979-105">In contrast, the My Reports folder is a user-managed workspace.</span></span> <span data-ttu-id="87979-106">您可以添加或删除报表和文件夹，保存带有个性化设置的链接报表。</span><span class="sxs-lookup"><span data-stu-id="87979-106">You can add or remove reports and folders and save linked reports with personalized settings.</span></span>  
  
 <span data-ttu-id="87979-107">从概念上说，“我的报表”文件夹类似于 Windows 文件系统中的“我的文档”文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-107">Conceptually, the My Reports folder is similar to the My Documents folder in the Windows file system.</span></span> <span data-ttu-id="87979-108">尽管每个用户都有一个名为“我的报表”的文件夹，但用户都只能访问各自的相应文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-108">Although each user has a folder called My Reports, the folder that each accesses is different from all other users.</span></span> <span data-ttu-id="87979-109">除了报表服务器管理员之外，其他用户都无法访问您的“我的报表”文件夹中的内容。</span><span class="sxs-lookup"><span data-stu-id="87979-109">Except for report server administrators, other users cannot access the contents of the My Reports folder that belongs to you.</span></span>  
  
 <span data-ttu-id="87979-110">“我的报表”功能是可选的，报表服务器管理员可以禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="87979-110">The My Reports feature is optional and can be disabled by a report server administrator.</span></span> <span data-ttu-id="87979-111">如果启用此功能，您就会在主文件夹中看到“我的报表”文件夹，可以使用报表管理器或 Web 浏览器访问该文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-111">If it is enabled, you will see a My Reports folder in the Home folder, which you can access using the Report Manager or a Web browser.</span></span> <span data-ttu-id="87979-112">有关详细信息，请参阅[在报表管理器中查找和查看报表（报表生成器和 SSRS）](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="87979-112">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="87979-113">在配置为 SharePoint 集成模式的报表服务器上，没有与“我的报表”文件夹等同的项。</span><span class="sxs-lookup"><span data-stu-id="87979-113">On a report server configured in SharePoint integrated mode, there is no equivalent to the My Reports folder.</span></span> <span data-ttu-id="87979-114">有关详细信息，请参阅 [查找、查看和管理报表（报表生成器和 SSRS）](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="87979-114">For more information, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a><span data-ttu-id="87979-115">使用“我的报表”文件夹的方法</span><span class="sxs-lookup"><span data-stu-id="87979-115">Ways to Use My Reports</span></span>  
 <span data-ttu-id="87979-116">在您添加报表、文件夹和其他项之前，“我的报表”为空文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-116">My Reports is empty until you add reports, folders, and other items.</span></span> <span data-ttu-id="87979-117">下面是向“我的报表”文件夹中添加内容的一些方法：</span><span class="sxs-lookup"><span data-stu-id="87979-117">Here are some ways to add content to My Reports.</span></span>  
  
-   <span data-ttu-id="87979-118">创建个人的链接报表，并将其存储在“我的报表”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="87979-118">Create a personal linked report and store it in My Reports.</span></span> <span data-ttu-id="87979-119">并非所有的报表都适合链接。</span><span class="sxs-lookup"><span data-stu-id="87979-119">Not all reports are available for linking.</span></span> <span data-ttu-id="87979-120">有关详细信息，请参阅 [创建链接报表](../reports/create-a-linked-report.md)。</span><span class="sxs-lookup"><span data-stu-id="87979-120">For more information, see [Create a Linked Report](../reports/create-a-linked-report.md).</span></span>  
  
-   <span data-ttu-id="87979-121">上载报表定义 (.rdl) 文件、报表模型 (.smdl) 文件或文件系统中的其他文件。</span><span class="sxs-lookup"><span data-stu-id="87979-121">Upload a report definition (.rdl) file, report model (.smdl) file, or other files from the file system.</span></span> <span data-ttu-id="87979-122">您可以上载任何文件，但报表服务器只处理扩展名为 .rdl 或 .smdl 的报表文件。</span><span class="sxs-lookup"><span data-stu-id="87979-122">You can upload any file, but the report server only processes report files that have an .rdl or .smdl file extension.</span></span> <span data-ttu-id="87979-123">有关详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312)中的“报表定义”和[上传文件或报表（报表管理器）](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="87979-123">For more information, see Report Definitions" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
-   <span data-ttu-id="87979-124">创建您自己的报表并将其发布到“我的报表”文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-124">Create and publish your own reports to My Reports.</span></span> <span data-ttu-id="87979-125">有关详细信息，请参阅[报表设计视图（报表生成器）](report-design-view-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="87979-125">For more information, see [Report Design View &#40;Report Builder&#41;](report-design-view-report-builder.md).</span></span>  
  
 <span data-ttu-id="87979-126">通常，“我的报表”的权限允许您自己管理该文件夹。</span><span class="sxs-lookup"><span data-stu-id="87979-126">Usually, permissions on My Reports allow you to manage the folder yourself.</span></span> <span data-ttu-id="87979-127">但是，最终还是由报表服务器管理员决定用户可以执行哪些任务。</span><span class="sxs-lookup"><span data-stu-id="87979-127">However, the report server administrator ultimately determines which tasks users can perform.</span></span> <span data-ttu-id="87979-128">如果您因权限不足而无法使用“我的报表”文件夹，请咨询报表服务器管理员。</span><span class="sxs-lookup"><span data-stu-id="87979-128">If insufficient permissions prevent you from working with My Reports, see your report server administrator.</span></span>  
  
## <a name="searching-my-reports"></a><span data-ttu-id="87979-129">搜索“我的报表”文件夹</span><span class="sxs-lookup"><span data-stu-id="87979-129">Searching My Reports</span></span>  
 <span data-ttu-id="87979-130">当您搜索报表服务器数据库时，您的“我的报表”文件夹中的内容也在搜索之列，而其他用户的“我的报表”文件夹中的内容则被排除在外。</span><span class="sxs-lookup"><span data-stu-id="87979-130">When you search a report server database, the contents of your My Reports folder are included in the search, while the contents of other user's My Reports folders are excluded.</span></span> <span data-ttu-id="87979-131">搜索结果中将只列出您可以访问的报表。</span><span class="sxs-lookup"><span data-stu-id="87979-131">Search results list only the reports to which you have access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87979-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87979-132">See Also</span></span>  
 [<span data-ttu-id="87979-133">查找、查看和管理报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="87979-133">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
