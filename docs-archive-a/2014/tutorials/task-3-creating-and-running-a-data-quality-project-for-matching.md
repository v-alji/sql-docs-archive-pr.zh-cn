---
title: 任务3：创建并运行数据质量项目以进行匹配 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 221d6d583c61ee035c20fcb63f0ed5278f2b8678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578586"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a><span data-ttu-id="70e98-102">任务 3：创建并运行数据质量项目以进行匹配</span><span class="sxs-lookup"><span data-stu-id="70e98-102">Task 3: Creating and Running a Data Quality Project for Matching</span></span>
  <span data-ttu-id="70e98-103">在本任务中，您将创建匹配活动的数据质量项目并对已清理的供应商数据运行匹配过程以删除数据中的所有重复项。</span><span class="sxs-lookup"><span data-stu-id="70e98-103">In this task, you create a Data Quality Project for the matching activity and run the matching process on cleansed supplier data to remove any duplicates in the data.</span></span>

1.  <span data-ttu-id="70e98-104">在**DQS 客户端**的主页上，单击 "**新建数据质量项目**"。</span><span class="sxs-lookup"><span data-stu-id="70e98-104">On the main page of **DQS Client**, click **New Data Quality Project**.</span></span>

2.  <span data-ttu-id="70e98-105">键入 "删除**项目名称中的\*\*\*\*供应商重复项**"。</span><span class="sxs-lookup"><span data-stu-id="70e98-105">Type **Remove Supplier Duplicates** from the **Name of the project**.</span></span>

3.  <span data-ttu-id="70e98-106">从 "**使用知识库**" 字段的 kb 列表中选择 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="70e98-106">Select **Suppliers** from the list of KBs for the **Use Knowledge Base** field.</span></span> <span data-ttu-id="70e98-107">您在上一课中在此知识库中创建了匹配策略。</span><span class="sxs-lookup"><span data-stu-id="70e98-107">You have created a matching policy in this knowledge base in the previous lesson.</span></span>

4.  <span data-ttu-id="70e98-108">从右下方窗格的**活动列表**中选择 "**匹配**"。</span><span class="sxs-lookup"><span data-stu-id="70e98-108">Select **Matching** from the **list of activities** from the bottom-right pane.</span></span>

     <span data-ttu-id="70e98-109">![新建数据质量项目 - 已选择匹配](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "新建数据质量项目 - 已选择匹配")</span><span class="sxs-lookup"><span data-stu-id="70e98-109">![New Data Quality Project - Matching Selected](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "New Data Quality Project - Matching Selected")</span></span>

5.  <span data-ttu-id="70e98-110">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="70e98-110">Click **Next**.</span></span>

6.  <span data-ttu-id="70e98-111">在“映射” \*\*\*\* 页中，为“数据源” \*\*\*\* 选择“Excel 文件” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="70e98-111">In the **Map** page, select **Excel File** for **Data Source**.</span></span>

7.  <span data-ttu-id="70e98-112">单击 "**浏览**" 并选择 "**清理供应商 List.xls**，这是清理活动的输出文件。</span><span class="sxs-lookup"><span data-stu-id="70e98-112">Click **Browse** and select **Cleansed Supplier List.xls**, which is the output file from the cleansing activity.</span></span>

8.  <span data-ttu-id="70e98-113">将**供应商的源列**映射到供应商**ID**域、**供应商名称**列到**供应商名称**域，并将**ContactEmailAddress**列映射到**联系人电子邮件**域。</span><span class="sxs-lookup"><span data-stu-id="70e98-113">Map **SupplierID** source column to the **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, and **ContactEmailAddress** column to **Contact Email** domain.</span></span>

9. <span data-ttu-id="70e98-114">单击 "**下一步**" 切换到 "**匹配**" 页。</span><span class="sxs-lookup"><span data-stu-id="70e98-114">Click **Next** to switch to the **Matching** page.</span></span>

10. <span data-ttu-id="70e98-115">单击 "**启动**" 以启动匹配进程。</span><span class="sxs-lookup"><span data-stu-id="70e98-115">Click **Start** to start the matching process.</span></span> <span data-ttu-id="70e98-116">您应看到与上一个任务类似的结果，因为您使用了相同的输入文件来定义匹配策略。</span><span class="sxs-lookup"><span data-stu-id="70e98-116">You should see results similar to those from the previous task because you used the same input file for defining the matching policy.</span></span>

11. <span data-ttu-id="70e98-117">在列表框中查看所有匹配的记录及其匹配分数。</span><span class="sxs-lookup"><span data-stu-id="70e98-117">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="70e98-118">结果应与您在上一个任务中看到的结果相同。</span><span class="sxs-lookup"><span data-stu-id="70e98-118">The results should be same as the ones you saw in the previous task.</span></span> <span data-ttu-id="70e98-119">请参阅上一个任务中的步骤来分析此匹配活动的结果。</span><span class="sxs-lookup"><span data-stu-id="70e98-119">See the steps in the previous task to analyze the results from this matching activity.</span></span>

12. <span data-ttu-id="70e98-120">单击 "**下一步**" 切换到 "**导出**" 页。</span><span class="sxs-lookup"><span data-stu-id="70e98-120">Click **Next** to switch to the **Export** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="70e98-121">下一步</span><span class="sxs-lookup"><span data-stu-id="70e98-121">Next Step</span></span>
 [<span data-ttu-id="70e98-122">任务 4：将匹配活动的结果导出到 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="70e98-122">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


