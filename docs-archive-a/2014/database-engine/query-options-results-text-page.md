---
title: 查询选项 () 文本页的结果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: rothja
ms.author: jroth
ms.openlocfilehash: 45019450c8fc959b440aac5bf1e9098e59cecefc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589861"
---
# <a name="query-options-results-text-page"></a><span data-ttu-id="94b4d-102">“查询选项”中的“结果”（“文本”页）</span><span class="sxs-lookup"><span data-stu-id="94b4d-102">Query Options Results (Text Page)</span></span>
  <span data-ttu-id="94b4d-103">使用此页可以指定以文本格式显示查询结果集的选项。</span><span class="sxs-lookup"><span data-stu-id="94b4d-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="94b4d-104">在选择 **“将结果保存到文件”** 时也会应用此页上的设置。</span><span class="sxs-lookup"><span data-stu-id="94b4d-104">The settings on this page also apply when **Results to File** is selected.</span></span>  
  
 <span data-ttu-id="94b4d-105">**输出格式**</span><span class="sxs-lookup"><span data-stu-id="94b4d-105">**Output format**</span></span>  
 <span data-ttu-id="94b4d-106">默认情况下，将在通过用空格分隔结果而得到的列中显示输出。</span><span class="sxs-lookup"><span data-stu-id="94b4d-106">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="94b4d-107">您还可以使用逗号、制表符或空格来分隔列。</span><span class="sxs-lookup"><span data-stu-id="94b4d-107">Other options are using commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="94b4d-108">选中 **“自定义分隔符”** 复选框，可以在 **“自定义分隔符”** 框中指定其他分隔字符。</span><span class="sxs-lookup"><span data-stu-id="94b4d-108">Select the **Custom delimiter** check box to specify a different delimiting character in the **Custom delimiter** box.</span></span>  
  
 <span data-ttu-id="94b4d-109">**“自定义分隔符”**</span><span class="sxs-lookup"><span data-stu-id="94b4d-109">**Custom delimiter**</span></span>  
 <span data-ttu-id="94b4d-110">自行指定用于分隔列的字符。</span><span class="sxs-lookup"><span data-stu-id="94b4d-110">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="94b4d-111">只有在 **“输出格式”** 框中选中 **“自定义分隔符”** 复选框后，才可使用此选项。</span><span class="sxs-lookup"><span data-stu-id="94b4d-111">This option is only available if the **Custom delimiter** check box is selected in the **Output format** box.</span></span>  
  
 <span data-ttu-id="94b4d-112">**在结果集中包括列标题**</span><span class="sxs-lookup"><span data-stu-id="94b4d-112">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="94b4d-113">如果不希望每列都带有列标题，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="94b4d-113">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="94b4d-114">**接收到结果时滚动**</span><span class="sxs-lookup"><span data-stu-id="94b4d-114">**Scroll as results are received**</span></span>  
 <span data-ttu-id="94b4d-115">选中此复选框将使得结果集的显示侧重于结尾处最近返回的记录。</span><span class="sxs-lookup"><span data-stu-id="94b4d-115">Select this check box to keep the display focus on the most recently returned records at the bottom.</span></span> <span data-ttu-id="94b4d-116">清除此复选框，则使其侧重于接收到的前几行。</span><span class="sxs-lookup"><span data-stu-id="94b4d-116">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="94b4d-117">**右对齐数值**</span><span class="sxs-lookup"><span data-stu-id="94b4d-117">**Right align numeric values**</span></span>  
 <span data-ttu-id="94b4d-118">选中此复选框可以将数值与列的右侧对齐。</span><span class="sxs-lookup"><span data-stu-id="94b4d-118">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="94b4d-119">这样，就可以更方便地查看具有固定小数位数的数值。</span><span class="sxs-lookup"><span data-stu-id="94b4d-119">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="94b4d-120">**在执行查询后放弃结果**</span><span class="sxs-lookup"><span data-stu-id="94b4d-120">**Discard result after query executes**</span></span>  
 <span data-ttu-id="94b4d-121">当屏幕显示接收到查询结果之后，通过放弃查询结果来释放内存。</span><span class="sxs-lookup"><span data-stu-id="94b4d-121">Frees memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="94b4d-122">**在单独选项卡中显示结果**</span><span class="sxs-lookup"><span data-stu-id="94b4d-122">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="94b4d-123">选中此复选框可在新文档窗口中显示结果集，而不是在查询文档窗口的底部显示。</span><span class="sxs-lookup"><span data-stu-id="94b4d-123">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="94b4d-124">**执行查询后切换到“结果”选项卡**</span><span class="sxs-lookup"><span data-stu-id="94b4d-124">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="94b4d-125">单击此项可将屏幕焦点自动设置到结果集。</span><span class="sxs-lookup"><span data-stu-id="94b4d-125">Click to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="94b4d-126">**每列中显示的最大字符数**</span><span class="sxs-lookup"><span data-stu-id="94b4d-126">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="94b4d-127">此值默认为 256。</span><span class="sxs-lookup"><span data-stu-id="94b4d-127">This value defaults to 256.</span></span> <span data-ttu-id="94b4d-128">增大此值可显示更大的结果集，而不会将其截断。</span><span class="sxs-lookup"><span data-stu-id="94b4d-128">Increase this value to display larger result sets without truncation.</span></span>  
  
 <span data-ttu-id="94b4d-129">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="94b4d-129">**Reset to Default**</span></span>  
 <span data-ttu-id="94b4d-130">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="94b4d-130">Resets all values on this page to the original default values.</span></span>  
  
## <a name="saving-a-text-result-set-with-headers"></a><span data-ttu-id="94b4d-131">使用标题保存文本结果集</span><span class="sxs-lookup"><span data-stu-id="94b4d-131">Saving a text result set with headers</span></span>  
 <span data-ttu-id="94b4d-132">若要将查询结果保存为带有标题的文本文件，请选中 **“在结果集中包括列标题”** 复选框，并选择一种带分隔符的输出格式。</span><span class="sxs-lookup"><span data-stu-id="94b4d-132">To save query results as a text file with headers, select the **Include column headers in the result set** check box and a delimited output format.</span></span> <span data-ttu-id="94b4d-133">现在，如果单击工具栏上的\*\*\*\*“将结果保存到文件”，或者右键单击任何查询结果，再单击\*\*\*\*“将结果另存为”，并键入一个文件名，然后单击\*\*\*\*“保存”，报表文件将包含标题。</span><span class="sxs-lookup"><span data-stu-id="94b4d-133">Now the report file will contain headers when you click **Results to File** on the toolbar, or when you right-click any query results, click **Save Results As**, type a file name, and then click **Save**.</span></span>  
  
  
