---
title: 显示页码或其他报表属性（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efc3d5d5de11af1fcdfefc52ed12d5057ee12668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586435"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a><span data-ttu-id="37d31-102">显示页码或其他报表属性（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37d31-102">Display Page Numbers or Other Report Properties (Report Builder and SSRS)</span></span>
  <span data-ttu-id="37d31-103">可以方便地向报表的页眉或页脚添加页码、报表标题、文件名和其他报表属性。</span><span class="sxs-lookup"><span data-stu-id="37d31-103">It's easy to add page numbers, a report title, file name, and other report properties to the page headers or footers of your report.</span></span> <span data-ttu-id="37d31-104">这些属性在“报表数据”窗格的“内置字段”文件夹中存储为字段：</span><span class="sxs-lookup"><span data-stu-id="37d31-104">These properties are stored as fields in the Built-in Fields folder in the Report Data pane:</span></span>  
  
-   <span data-ttu-id="37d31-105">执行时间</span><span class="sxs-lookup"><span data-stu-id="37d31-105">Execution time</span></span>  
  
-   <span data-ttu-id="37d31-106">页码</span><span class="sxs-lookup"><span data-stu-id="37d31-106">Page number</span></span>  
  
-   <span data-ttu-id="37d31-107">报表文件夹</span><span class="sxs-lookup"><span data-stu-id="37d31-107">Report folder</span></span>  
  
-   <span data-ttu-id="37d31-108">报表名称</span><span class="sxs-lookup"><span data-stu-id="37d31-108">Report name</span></span>  
  
-   <span data-ttu-id="37d31-109">报表服务器 URL</span><span class="sxs-lookup"><span data-stu-id="37d31-109">Report server URL</span></span>  
  
-   <span data-ttu-id="37d31-110">全部页</span><span class="sxs-lookup"><span data-stu-id="37d31-110">Total pages</span></span>  
  
-   <span data-ttu-id="37d31-111">用户 ID</span><span class="sxs-lookup"><span data-stu-id="37d31-111">User ID</span></span>  
  
-   <span data-ttu-id="37d31-112">语言</span><span class="sxs-lookup"><span data-stu-id="37d31-112">Language</span></span>  
  
 <span data-ttu-id="37d31-113">对于页码，您可能希望在数字前添加单词“Page”。</span><span class="sxs-lookup"><span data-stu-id="37d31-113">For a page number, you may want to add the word "Page" before the number.</span></span> <span data-ttu-id="37d31-114">也可能希望显示总页数。</span><span class="sxs-lookup"><span data-stu-id="37d31-114">You may also want to show the total number of pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37d31-115">将总页数添加到页脚在运行或预览报表时可能会降低性能。</span><span class="sxs-lookup"><span data-stu-id="37d31-115">Adding the total number of pages to the footer may slow performance when you run or preview your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a><span data-ttu-id="37d31-116">添加页码或其他报表属性</span><span class="sxs-lookup"><span data-stu-id="37d31-116">To add a page number or other report properties</span></span>  
  
1.  <span data-ttu-id="37d31-117">在“报表数据”窗格中，展开“内置字段”文件夹。</span><span class="sxs-lookup"><span data-stu-id="37d31-117">In the Report Data pane, expand the Built-in Fields folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="37d31-118">如果看不到“报表数据”窗格，请在“视图”选项卡上选中“报表数据”  。</span><span class="sxs-lookup"><span data-stu-id="37d31-118">If you don't see the Report Data pane, on the View tab, check **Report Data**.</span></span>  
  
2.  <span data-ttu-id="37d31-119">将 **“页码”** 字段从“报表数据”窗格拖动到报表表头和表尾。</span><span class="sxs-lookup"><span data-stu-id="37d31-119">Drag the **Page Number** field from the Report Data pane to the report header or footer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="37d31-120">页脚将自动添加到报表。</span><span class="sxs-lookup"><span data-stu-id="37d31-120">The page footer is added to the report automatically.</span></span> <span data-ttu-id="37d31-121">若要添加页眉，请在 **“插入”** 选项卡上，单击 **“页眉”** ，然后单击 **“添加页眉”** 。</span><span class="sxs-lookup"><span data-stu-id="37d31-121">To add a page header, on the **Insert** tab, click **Header**, and then click **Add Header**.</span></span>  
    >   
    >  <span data-ttu-id="37d31-122">将添加一个包含简单表达式 [&PageNumber] 的文本框。</span><span class="sxs-lookup"><span data-stu-id="37d31-122">A text box that contains the simple expression [&PageNumber] is added.</span></span>  
  
### <a name="to-add-the-word-page-before-the-page-number"></a><span data-ttu-id="37d31-123">在页码前添加单词 "Page"</span><span class="sxs-lookup"><span data-stu-id="37d31-123">To add the word "Page" before the page number</span></span>  
  
1.  <span data-ttu-id="37d31-124">右键单击包含 [&PageNumber] 的文本框，然后单击“表达式”  。</span><span class="sxs-lookup"><span data-stu-id="37d31-124">Right-click the text box that contains [&PageNumber] and click **Expressions**.</span></span>  
  
     <span data-ttu-id="37d31-125">“为以下项设置表达式: 值”文本框包含表达式 =Globals!PageNumber  。</span><span class="sxs-lookup"><span data-stu-id="37d31-125">The **Set Expression for: Value** text box contains the expression =Globals!PageNumber.</span></span>  
  
2.  <span data-ttu-id="37d31-126">将光标放在 = 号后，然后键入 `"Page " &`。</span><span class="sxs-lookup"><span data-stu-id="37d31-126">Place the cursor after the = sign and type `"Page " &`.</span></span>  
  
     <span data-ttu-id="37d31-127">该表达式现在变为 ="Page "&Globals!PageNumber</span><span class="sxs-lookup"><span data-stu-id="37d31-127">The expression is now  ="Page "&Globals!PageNumber</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a><span data-ttu-id="37d31-128">在页码后面添加总页数</span><span class="sxs-lookup"><span data-stu-id="37d31-128">To add total number of pages after the page number</span></span>  
  
1.  <span data-ttu-id="37d31-129">右键单击包含表达式的文本框，然后单击 **“表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="37d31-129">Right click the text box with the expression and click **Expressions**.</span></span>  
  
2.  <span data-ttu-id="37d31-130">在表达式的末尾键入 &" of "&  。</span><span class="sxs-lookup"><span data-stu-id="37d31-130">Type **&" of "&** at the end of the expression.</span></span>  
  
3.  <span data-ttu-id="37d31-131">在“类别”窗格中，展开“内置字段”，然后双击 TotalPages   。</span><span class="sxs-lookup"><span data-stu-id="37d31-131">In the Category pane, expand **Built-in Fields** and double-click **TotalPages**.</span></span>  
  
     <span data-ttu-id="37d31-132">该表达式现在变为 ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span><span class="sxs-lookup"><span data-stu-id="37d31-132">The expression is now ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37d31-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37d31-133">See Also</span></span>  
 <span data-ttu-id="37d31-134">[页眉和页脚（报表生成器和 SSRS）](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="37d31-134">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="37d31-135">设置文本框中文本的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="37d31-135">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
