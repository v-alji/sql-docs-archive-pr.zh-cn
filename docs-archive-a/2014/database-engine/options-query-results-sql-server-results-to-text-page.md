---
title: 选项 (查询结果-SQL Server-) 文本页的结果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToText
ms.assetid: 2ccbdf17-e14f-42f1-a836-ca999a3432c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ece458e4bab9a57cb6692d4ac6dfdf2e8f4bd22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690775"
---
# <a name="options-query-results-sql-server-results-to-text-page"></a><span data-ttu-id="9aa27-102">选项 (查询结果-SQL Server-结果到文本页) </span><span class="sxs-lookup"><span data-stu-id="9aa27-102">Options (Query Results-SQL Server-Results to Text Page)</span></span>
  <span data-ttu-id="9aa27-103">使用此页可以指定以文本格式显示查询结果集的选项。</span><span class="sxs-lookup"><span data-stu-id="9aa27-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="9aa27-104">对这些选项所做的更改只应用于新的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="9aa27-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="9aa27-105">若要更改当前查询的选项，请在 "**查询**" 菜单上单击 "**查询选项**"，或在查询窗口中单击右键， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 然后选择 "**查询选项**"。</span><span class="sxs-lookup"><span data-stu-id="9aa27-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window, and select **Query Options**.</span></span> <span data-ttu-id="9aa27-106">在 **“查询选项”** 对话框中的 **“结果”** 下，单击 **“文本”**。</span><span class="sxs-lookup"><span data-stu-id="9aa27-106">In the **Query Options** dialog box, under **Results**, click **Text**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9aa27-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="9aa27-107">UI element list</span></span>  
 <span data-ttu-id="9aa27-108">**输出格式**</span><span class="sxs-lookup"><span data-stu-id="9aa27-108">**Output format**</span></span>  
 <span data-ttu-id="9aa27-109">默认情况下，将在通过用空格分隔结果而得到的列中显示输出。</span><span class="sxs-lookup"><span data-stu-id="9aa27-109">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="9aa27-110">您还可以使用逗号、制表符或空格来分隔列。</span><span class="sxs-lookup"><span data-stu-id="9aa27-110">Other options are to use commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="9aa27-111">从此下拉列表中选择“自定义分隔符”\*\*\*\*，可以在“自定义分隔符”\*\*\*\* 文本框中指定其他分隔字符。</span><span class="sxs-lookup"><span data-stu-id="9aa27-111">Select **Custom delimiter** from this drop-down list to specify a different delimiting character in the **Custom delimiter** text box.</span></span>  
  
 <span data-ttu-id="9aa27-112">**“自定义分隔符”**</span><span class="sxs-lookup"><span data-stu-id="9aa27-112">**Custom delimiter**</span></span>  
 <span data-ttu-id="9aa27-113">自行指定用于分隔列的字符。</span><span class="sxs-lookup"><span data-stu-id="9aa27-113">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="9aa27-114">只有在“输出格式”\*\*\*\* 下拉列表框中单击“自定义分隔符”时，此文本框才可用。</span><span class="sxs-lookup"><span data-stu-id="9aa27-114">This text box is available only if you clicked Custom delimiter in the **Output format** drop-down list box.</span></span>  
  
 <span data-ttu-id="9aa27-115">**在结果集中包括列标题**</span><span class="sxs-lookup"><span data-stu-id="9aa27-115">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="9aa27-116">如果不希望每列都带有列标题，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="9aa27-116">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="9aa27-117">**在结果集中包括查询**</span><span class="sxs-lookup"><span data-stu-id="9aa27-117">**Include the query in the result set**</span></span>  
 <span data-ttu-id="9aa27-118">在结果窗格中，若要在查询结果前面包括正在运行的查询文本，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="9aa27-118">Select this check box to include the text of the query that is running in the results pane before the results of the query.</span></span>  
  
 <span data-ttu-id="9aa27-119">**接收到结果时滚动**</span><span class="sxs-lookup"><span data-stu-id="9aa27-119">**Scroll as results are received**</span></span>  
 <span data-ttu-id="9aa27-120">选中此复选框将使得结果集的显示侧重于结尾处最近返回的记录。</span><span class="sxs-lookup"><span data-stu-id="9aa27-120">Select this check box to keep the display focus on the most recently returned records at the end of the results set.</span></span> <span data-ttu-id="9aa27-121">清除此复选框，则使其侧重于接收到的前几行。</span><span class="sxs-lookup"><span data-stu-id="9aa27-121">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="9aa27-122">**右对齐数值**</span><span class="sxs-lookup"><span data-stu-id="9aa27-122">**Right align numeric values**</span></span>  
 <span data-ttu-id="9aa27-123">选中此复选框可以将数值与列的右侧对齐。</span><span class="sxs-lookup"><span data-stu-id="9aa27-123">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="9aa27-124">这样，就可以更方便地查看具有固定小数位数的数值。</span><span class="sxs-lookup"><span data-stu-id="9aa27-124">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="9aa27-125">**在执行查询后放弃结果**</span><span class="sxs-lookup"><span data-stu-id="9aa27-125">**Discard result after query executes**</span></span>  
 <span data-ttu-id="9aa27-126">当查询结果在查询窗口的结果窗格中显示之后，若要放弃查询结果，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="9aa27-126">Select this check box to discard the query results after they are displayed in the results pane of the query window.</span></span>  
  
 <span data-ttu-id="9aa27-127">**在单独选项卡中显示结果**</span><span class="sxs-lookup"><span data-stu-id="9aa27-127">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="9aa27-128">选中此复选框可在新文档窗口中显示结果集，而不是在查询文档窗口的底部显示。</span><span class="sxs-lookup"><span data-stu-id="9aa27-128">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="9aa27-129">**执行查询后切换到“结果”选项卡**</span><span class="sxs-lookup"><span data-stu-id="9aa27-129">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="9aa27-130">若要自动将屏幕焦点设置到结果集，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="9aa27-130">Select this check box to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="9aa27-131">**每列中显示的最大字符数**</span><span class="sxs-lookup"><span data-stu-id="9aa27-131">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="9aa27-132">此值默认为 256。</span><span class="sxs-lookup"><span data-stu-id="9aa27-132">This value defaults to 256.</span></span> <span data-ttu-id="9aa27-133">增大此值可显示更大的结果集，而不会将其截断。</span><span class="sxs-lookup"><span data-stu-id="9aa27-133">Increase this value to display larger result sets without truncation.</span></span> <span data-ttu-id="9aa27-134">最大值为 8,192。</span><span class="sxs-lookup"><span data-stu-id="9aa27-134">The maximum value is 8,192.</span></span>  
  
 <span data-ttu-id="9aa27-135">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="9aa27-135">**Reset to Default**</span></span>  
 <span data-ttu-id="9aa27-136">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="9aa27-136">Resets all values on this page to the original default values.</span></span>  
  
  
