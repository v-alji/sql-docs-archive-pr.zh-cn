---
title: 重新标记 SQL Server 数据挖掘外接 () |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
ms.openlocfilehash: a625676f60e2da32e19b85a94002b51eeb9ac816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586989"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a><span data-ttu-id="4d071-102">重新标记（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="4d071-102">Relabel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="4d071-103">![重新标记工具的 Office 13 图标](media/dm13-relabel.gif "重新标记工具的 Office 13 图标")</span><span class="sxs-lookup"><span data-stu-id="4d071-103">![Office 13 icon for Relabel tool](media/dm13-relabel.gif "Office 13 icon for Relabel tool")</span></span>

 <span data-ttu-id="4d071-104">使用 Excel 数据挖掘客户端可以为数据创建新标签，以便使分析结果更容易理解。</span><span class="sxs-lookup"><span data-stu-id="4d071-104">The Data Mining Client for Excel helps you create new labels for data to make it easier to understand the results of analysis.</span></span>

 <span data-ttu-id="4d071-105">重新标记的原因包括：</span><span class="sxs-lookup"><span data-stu-id="4d071-105">Reasons for relabeling include:</span></span>

-   <span data-ttu-id="4d071-106">数据的结果经过编码，如 1 表示男性，2 表示女性。</span><span class="sxs-lookup"><span data-stu-id="4d071-106">The data includes results that were coded, such as 1 for Male and 2 for Female.</span></span>

-   <span data-ttu-id="4d071-107">要将数值装入存储桶，并希望为范围给出一个说明性名称。</span><span class="sxs-lookup"><span data-stu-id="4d071-107">You are bucketing numeric values and want to give the ranges a descriptive name.</span></span>

-   <span data-ttu-id="4d071-108">要简化长名称。</span><span class="sxs-lookup"><span data-stu-id="4d071-108">You want to simplify long names.</span></span>

## <a name="using-the-relabel-wizard"></a><span data-ttu-id="4d071-109">使用重新标记向导</span><span class="sxs-lookup"><span data-stu-id="4d071-109">Using the Relabel Wizard</span></span>

1.  <span data-ttu-id="4d071-110">在 "**数据挖掘**" 功能区中，单击 "**清除**"，然后选择 "**重新标记**"。</span><span class="sxs-lookup"><span data-stu-id="4d071-110">In the **Data Mining** ribbon, click **Clean** and then select **Re-Label**.</span></span>

2.  <span data-ttu-id="4d071-111">选择具有要修复的数据的表或数据范围。</span><span class="sxs-lookup"><span data-stu-id="4d071-111">Select the table or data range that has the data you want to fix.</span></span>

3.  <span data-ttu-id="4d071-112">在向导的 "**重新标记**" 页中，选择单个列，方法是从下拉列表中选择列，或者单击 "**数据示例**" 窗格中的列。</span><span class="sxs-lookup"><span data-stu-id="4d071-112">In the **Re-label** page of the wizard, select a single column, either by choosing the column from the dropdown list, or by clicking the column in the **Data samples** pane.</span></span>

     <span data-ttu-id="4d071-113">"**数据示例**" 窗格只显示大约50行的数据，但会进行采样以确保看到的值很好。</span><span class="sxs-lookup"><span data-stu-id="4d071-113">The **Data samples** pane only shows about 50 rows of data, but they are sampled to ensure that you see a good spread of values.</span></span>

     <span data-ttu-id="4d071-114">单击 "**计数**" 列标题，按每个值的计数进行排序。</span><span class="sxs-lookup"><span data-stu-id="4d071-114">Click the column header for **Count** to sort by the count of each value.</span></span>

     <span data-ttu-id="4d071-115">你还可以按**原始标签**排序，如果你想要先重新标记所有最高值或最低值，这很方便。</span><span class="sxs-lookup"><span data-stu-id="4d071-115">You can also sort by **Original Labels**, which is handy if you want to re-label all the highest or lowest values first.</span></span>

4.  <span data-ttu-id="4d071-116">在向导的 "**重新标记**数据" 页中，查看 "**原始标签**" 列中的值，并决定要如何分组或编辑这些值。</span><span class="sxs-lookup"><span data-stu-id="4d071-116">In the **Re-label** data page of the wizard, review the values in the **Original Labels** column, and decide how you want to group or edit them.</span></span>

5.  <span data-ttu-id="4d071-117">在 "**新标签**" 下的行中键入新值。</span><span class="sxs-lookup"><span data-stu-id="4d071-117">Type a new value into the row under **New Labels**.</span></span> <span data-ttu-id="4d071-118">您还可以从现有值列表中选择值。</span><span class="sxs-lookup"><span data-stu-id="4d071-118">You can also choose a value from the list of existing values.</span></span> <span data-ttu-id="4d071-119">随着您键入新值，这些值将立即可供重复使用。</span><span class="sxs-lookup"><span data-stu-id="4d071-119">As you type new values, they become available for re-use right away.</span></span>

6.  <span data-ttu-id="4d071-120">输入足够的行后，单击 "**下一步**"，然后在 "**选择目标**" 页上，选择保存重新标记数据的位置。</span><span class="sxs-lookup"><span data-stu-id="4d071-120">When you have entered enough rows, click **Next**, and on the **Select Destination** page, choose where you'll save the relabeled data.</span></span>

    -   <span data-ttu-id="4d071-121">**作为新列添加到当前工作表**</span><span class="sxs-lookup"><span data-stu-id="4d071-121">**Add as a new column to the current worksheet**</span></span>

         <span data-ttu-id="4d071-122">单击此选项可将包含新值的新列添加到表中。</span><span class="sxs-lookup"><span data-stu-id="4d071-122">Click to add a new column to the table that contains the new values.</span></span>

    -   <span data-ttu-id="4d071-123">**将工作表数据及其更改复制到新工作表**</span><span class="sxs-lookup"><span data-stu-id="4d071-123">**Copy sheet data with changes to a new worksheet**</span></span>

         <span data-ttu-id="4d071-124">单击此选项可创建一个包含更新数据的新工作表。</span><span class="sxs-lookup"><span data-stu-id="4d071-124">Click to create a new worksheet that contains the updated data.</span></span>

    -   <span data-ttu-id="4d071-125">**就地更改数据**</span><span class="sxs-lookup"><span data-stu-id="4d071-125">**Change data in place**</span></span>

         <span data-ttu-id="4d071-126">单击此选项可将原始数据替换为新值。</span><span class="sxs-lookup"><span data-stu-id="4d071-126">Click to replace the original data with the new values.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d071-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d071-127">See Also</span></span>
 [<span data-ttu-id="4d071-128">浏览和清除数据</span><span class="sxs-lookup"><span data-stu-id="4d071-128">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)


