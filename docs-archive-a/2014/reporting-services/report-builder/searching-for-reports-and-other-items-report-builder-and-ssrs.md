---
title: 搜索报表和其他项（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a964cbdbc674fb3d29e18b5e5075695f0033801e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577341"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a><span data-ttu-id="66f72-102">搜索报表和其他项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="66f72-102">Searching for Reports and Other Items (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="66f72-103">您可以使用报表管理器在报表服务器中按名称或说明搜索特定的项。</span><span class="sxs-lookup"><span data-stu-id="66f72-103">You can use Report Manager to search a report server for specific items by name or description.</span></span> <span data-ttu-id="66f72-104">可以搜索发布的报表、报表模型、文件夹、共享数据源和资源。</span><span class="sxs-lookup"><span data-stu-id="66f72-104">You can search for published reports, report models, folders, shared data sources, and resources.</span></span> <span data-ttu-id="66f72-105">无法搜索计划、所有者、角色分配、订阅或者报表历史记录中的特定快照。</span><span class="sxs-lookup"><span data-stu-id="66f72-105">You cannot search for schedules, owners, role assignments, specific snapshots in report history, or subscriptions.</span></span> <span data-ttu-id="66f72-106">搜索是在存储项的报表服务器数据库上执行的。</span><span class="sxs-lookup"><span data-stu-id="66f72-106">The search is performed on the report server database where the items are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66f72-107">对于由报表服务器管理的项，执行文件系统搜索不会为其返回搜索结果。</span><span class="sxs-lookup"><span data-stu-id="66f72-107">Performing a file system search will not return search results for items managed by a report server.</span></span>  
  
-   <span data-ttu-id="66f72-108">若要在报表管理器中搜索项，请在页面顶部的 **“搜索”** 文本框中键入搜索字符串。</span><span class="sxs-lookup"><span data-stu-id="66f72-108">To search for items in Report Manager, type a search string in the **Search for** text box at the top of the page.</span></span> <span data-ttu-id="66f72-109">搜索将从文件夹层次结构的顶部节点开始，然后逐渐涉及每一个分支。</span><span class="sxs-lookup"><span data-stu-id="66f72-109">Searches begin at the top node in the folder hierarchy and then proceed through every branch.</span></span> <span data-ttu-id="66f72-110">如果您无权访问特定分支，就会将其跳过。</span><span class="sxs-lookup"><span data-stu-id="66f72-110">If you do not have permission to access a specific branch, that branch is skipped.</span></span> <span data-ttu-id="66f72-111">这一点适用于其他用户的“我的报表”文件夹以及一般情况下不可用的其他文件夹。</span><span class="sxs-lookup"><span data-stu-id="66f72-111">This applies to My Reports folders that belong to other users, and to other folders that are not generally available.</span></span> <span data-ttu-id="66f72-112">搜索结果中将只包含您有权查看的报表和项。</span><span class="sxs-lookup"><span data-stu-id="66f72-112">Only reports and items that you have permission to view are included in the search results.</span></span>  
  
-   <span data-ttu-id="66f72-113">若要按名称或说明搜索项，请指定希望匹配的全部或部分文本。</span><span class="sxs-lookup"><span data-stu-id="66f72-113">To search for an item by name or description, specify all or part of the text that you want to match.</span></span> <span data-ttu-id="66f72-114">搜索字符串不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="66f72-114">The search string is not case-sensitive.</span></span> <span data-ttu-id="66f72-115">不能使用搜索运算符来规定或排除搜索条件，如加号 (+) 或减号 (-)。</span><span class="sxs-lookup"><span data-stu-id="66f72-115">You cannot use search operators such as plus (+) or minus (-) symbols to require or exclude search criteria.</span></span>  
  
-   <span data-ttu-id="66f72-116">若要在报表中搜索特定文本，请使用报表顶部的工具栏。</span><span class="sxs-lookup"><span data-stu-id="66f72-116">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="66f72-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66f72-117">See Also</span></span>  
 <span data-ttu-id="66f72-118">[在报表管理器 &#40;报表生成器和 SSRS 中查找和查看报表&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f72-118">[Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66f72-119">[使用我的报表 &#40;报表生成器和 SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f72-119">[Using My Reports &#40;Report Builder and SSRS&#41;](using-my-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66f72-120">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f72-120">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="66f72-121">打开和关闭报表（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="66f72-121">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)  
  
  
