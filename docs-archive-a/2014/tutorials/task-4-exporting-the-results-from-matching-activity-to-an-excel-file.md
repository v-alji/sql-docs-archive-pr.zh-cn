---
title: 任务4：将匹配活动的结果导出到 Excel 文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b583e44f887fc0595fb904ec977f1de28c2fecd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691367"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a><span data-ttu-id="15131-102">任务 4：将匹配活动的结果导出到 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="15131-102">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>
  <span data-ttu-id="15131-103">在本任务中，您将匹配活动的结果导出到 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="15131-103">In this task, you export the results from the matching activity to an Excel file.</span></span>

1.  <span data-ttu-id="15131-104">在 "**导出**" 页中，选择 " **Excel 文件**" 作为**目标类型**。</span><span class="sxs-lookup"><span data-stu-id="15131-104">In the **Export** page, select **Excel File** for the **Destination Type**.</span></span>

2.  <span data-ttu-id="15131-105">选择**存活结果**选项。</span><span class="sxs-lookup"><span data-stu-id="15131-105">Select **Survivorship Results** option.</span></span> <span data-ttu-id="15131-106">在存活过程中，DQS 根据所选的**存活规则**确定每个群集的存活记录。</span><span class="sxs-lookup"><span data-stu-id="15131-106">In the survivorship process, DQS determines a survivor record for each cluster based on the **Survivorship Rule** you selected.</span></span>

3.  <span data-ttu-id="15131-107">单击 "**浏览**" 并导航到要在其中存储输出文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="15131-107">Click **Browse** and navigate to the folder where you want to store the output file.</span></span>

4.  <span data-ttu-id="15131-108">键入 "清理"，为名称**匹配 Suppliers.xls** ，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="15131-108">Type **Cleansed and Matched Suppliers.xls** for the name and click **Open**.</span></span>

5.  <span data-ttu-id="15131-109">确认为**存活规则**选择了 "**透视记录**"。</span><span class="sxs-lookup"><span data-stu-id="15131-109">Confirm that **Pivot Record** is selected for the **Survivorship Rule**.</span></span> <span data-ttu-id="15131-110">当您选择此选项时，为分类的输出选择每个分类的透视记录。</span><span class="sxs-lookup"><span data-stu-id="15131-110">When you select this option, the pivot record for each cluster is picked for the output from a cluster.</span></span> <span data-ttu-id="15131-111">存留规则的其他选项有：</span><span class="sxs-lookup"><span data-stu-id="15131-111">The other options for the Survivorship Rule are:</span></span>

    1.  <span data-ttu-id="15131-112">**最完整记录：** 存活记录是具有最大填充字段数的记录。</span><span class="sxs-lookup"><span data-stu-id="15131-112">**Most complete record:** Survivor record is the one with the largest number of populated fields.</span></span>

    2.  <span data-ttu-id="15131-113">**最长记录：** 存活记录是源字段中具有最大字词数的记录。</span><span class="sxs-lookup"><span data-stu-id="15131-113">**Longest record:** Survivor record is the one with the largest number of terms in source fields.</span></span>

    3.  <span data-ttu-id="15131-114">**最完整且最长的记录：** 存活记录是具有最大填充字段数的记录，每个字段中的字词数最多。</span><span class="sxs-lookup"><span data-stu-id="15131-114">**Most complete and longest record:** Survivor record is the one with the largest number of populated fields, and has the largest number of terms in each field.</span></span>

     <span data-ttu-id="15131-115">![从“匹配”页导出结果](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "从“匹配”页导出结果")</span><span class="sxs-lookup"><span data-stu-id="15131-115">![Export Results from Matching Page](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Export Results from Matching Page")</span></span>

6.  <span data-ttu-id="15131-116">单击 "**导出**" 将结果导出到 Excel 文件中。</span><span class="sxs-lookup"><span data-stu-id="15131-116">Click **Export** to export the results to an Excel file.</span></span>

7.  <span data-ttu-id="15131-117">单击 "**关闭**" 以关闭 "**匹配导出**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="15131-117">Click **Close** to close the **Matching Export** dialog box.</span></span>

8.  <span data-ttu-id="15131-118">单击 "**完成**" 以完成匹配活动。</span><span class="sxs-lookup"><span data-stu-id="15131-118">Click **Finish** to finish the matching activity.</span></span>

9. <span data-ttu-id="15131-119">打开**清理并匹配 Suppliers.xlsx**文件，确认没有 (供应商) 的任何重复项。</span><span class="sxs-lookup"><span data-stu-id="15131-119">Open the **Cleansed and Matched Suppliers.xlsx** file and confirm that you do not see any duplicates (SupplierID).</span></span>

 <span data-ttu-id="15131-120">现在，您的供应商数据已经过清理和匹配，删除了重复项。</span><span class="sxs-lookup"><span data-stu-id="15131-120">Now, you have supplier data that has been cleansed and matched to remove duplicates.</span></span>

## <a name="next-step"></a><span data-ttu-id="15131-121">下一步</span><span class="sxs-lookup"><span data-stu-id="15131-121">Next Step</span></span>
 [<span data-ttu-id="15131-122">第 4 课：在 MDS 中存储供应商数据</span><span class="sxs-lookup"><span data-stu-id="15131-122">Lesson 4: Storing Supplier Data in MDS</span></span>](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


