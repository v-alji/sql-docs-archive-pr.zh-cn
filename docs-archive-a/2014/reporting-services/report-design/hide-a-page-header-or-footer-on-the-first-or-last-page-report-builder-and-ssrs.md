---
title: 在第一页或最后一页 (报表生成器和 SSRS) 隐藏页眉或页脚 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f87ce79b-00d7-4458-a17e-e253a20f720d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60c8789fd098df7347e9cc0f583426478aee06e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682689"
---
# <a name="hide-a-page-header-or-footer-on-the-first-or-last-page-report-builder-and-ssrs"></a><span data-ttu-id="56db6-102">隐藏第一页或最后一页的页眉或页脚（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="56db6-102">Hide a Page Header or Footer on the First or Last Page (Report Builder and SSRS)</span></span>
  <span data-ttu-id="56db6-103">报表可以包含页眉和页脚，它们分别位于每一页的顶部和底部。</span><span class="sxs-lookup"><span data-stu-id="56db6-103">A report can contain a page header and page footer that run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="56db6-104">添加页眉或页脚后，可以在报表的第一页和最后一页选择性地将其隐藏。</span><span class="sxs-lookup"><span data-stu-id="56db6-104">After you a add a header or footer, you can selectively hide it on the first and last pages of a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-a-page-header-on-the-first-or-last-page"></a><span data-ttu-id="56db6-105">隐藏第一页或最后一页的页眉</span><span class="sxs-lookup"><span data-stu-id="56db6-105">To hide a page header on the first or last page</span></span>  
  
1.  <span data-ttu-id="56db6-106">在“设计”视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="56db6-106">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="56db6-107">右键单击页面页眉，再单击“页眉属性”  。</span><span class="sxs-lookup"><span data-stu-id="56db6-107">Right-click the page header, and then click **Header Properties**.</span></span> <span data-ttu-id="56db6-108">将打开 **“报表表头属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="56db6-108">The **Report Header Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="56db6-109">确保未选中 **“显示此报表的页眉”** 。</span><span class="sxs-lookup"><span data-stu-id="56db6-109">Verify that **Display header for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="56db6-110">在 **“打印选项”** 部分，清除每个选项对应的复选框以隐藏报表第一页或最后一页上的显示。</span><span class="sxs-lookup"><span data-stu-id="56db6-110">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-hide-a-page-footer-on-the-first-or-last-page"></a><span data-ttu-id="56db6-111">隐藏第一页或最后一页的页脚</span><span class="sxs-lookup"><span data-stu-id="56db6-111">To hide a page footer on the first or last page</span></span>  
  
1.  <span data-ttu-id="56db6-112">在“设计”视图中打开报表。</span><span class="sxs-lookup"><span data-stu-id="56db6-112">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="56db6-113">右键单击页面页脚，再单击“页脚属性”  。</span><span class="sxs-lookup"><span data-stu-id="56db6-113">Right-click the page footer, and then click **Footer Properties**.</span></span> <span data-ttu-id="56db6-114">将打开 **“报表表尾属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="56db6-114">The **Report Footer Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="56db6-115">确保未选中 **“显示此报表的页脚”** 。</span><span class="sxs-lookup"><span data-stu-id="56db6-115">Verify that **Display footer for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="56db6-116">在 **“打印选项”** 部分，清除每个选项对应的复选框以隐藏报表第一页或最后一页上的显示。</span><span class="sxs-lookup"><span data-stu-id="56db6-116">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56db6-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56db6-117">See Also</span></span>  
 <span data-ttu-id="56db6-118">[页眉和页脚（报表生成器和 SSRS）](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56db6-118">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="56db6-119">[Reporting Services 中的分页（报表生成器和 SSRS）](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="56db6-119">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="56db6-120">添加或删除页面页眉或页脚（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="56db6-120">Add or Remove a Page Header or Footer &#40;Report Builder and SSRS&#41;</span></span>](add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)  
  
  
