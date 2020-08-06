---
title: 任务3：从 Excel 文件导入域值 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 707a3925bb6d0014e2a1248f904123b076024e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578584"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a><span data-ttu-id="38bdf-102">任务 3：从 Excel 文件导入域值</span><span class="sxs-lookup"><span data-stu-id="38bdf-102">Task 3: Importing Domain Values from an Excel File</span></span>

  <span data-ttu-id="38bdf-103">在此任务中，您将从 Excel 文件的工作表中导入**状态**域的值。</span><span class="sxs-lookup"><span data-stu-id="38bdf-103">In this task, you import values for the **State** domain from a worksheet of an Excel file.</span></span>

1.  <span data-ttu-id="38bdf-104">单击 "**域列表**" 中的 "**状态**域"。</span><span class="sxs-lookup"><span data-stu-id="38bdf-104">Click **State** domain in the **Domain list**.</span></span>

2.  <span data-ttu-id="38bdf-105">确保右侧窗格中的 "**域值**" 选项卡处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="38bdf-105">Ensure that the **Domain Values** tab is active in the right pane.</span></span>

3.  <span data-ttu-id="38bdf-106">在右侧窗格的工具栏中，单击 "**导入值**" 按钮旁边的**向下箭头**，然后单击 "**从 Excel 导入有效值**"。</span><span class="sxs-lookup"><span data-stu-id="38bdf-106">In the right pane, from the toolbar, click **down arrow** next to the **Import Values** button, and click **Import Valid Values from Excel**.</span></span>

     <span data-ttu-id="38bdf-107">![“从 Excel 导入有效值”菜单](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "“从 Excel 导入有效值”菜单")</span><span class="sxs-lookup"><span data-stu-id="38bdf-107">![Import Valid Values from Excel Menu](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Import Valid Values from Excel Menu")</span></span>

4.  <span data-ttu-id="38bdf-108">单击 "**浏览**"，选择**Suppliers.xls**，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="38bdf-108">Click **Browse**, select **Suppliers.xls**, and click **Open**.</span></span>

5.  <span data-ttu-id="38bdf-109">选择**工作表**的**StatesToImport $** 。</span><span class="sxs-lookup"><span data-stu-id="38bdf-109">Select **StatesToImport$** for the **Worksheet**.</span></span>

     <span data-ttu-id="38bdf-110">![“导入域值”对话框](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "“导入域值”对话框")</span><span class="sxs-lookup"><span data-stu-id="38bdf-110">![Import Domain Values Dialog Box](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "Import Domain Values Dialog Box")</span></span>

6.  <span data-ttu-id="38bdf-111">单击 **"确定"** 以关闭 "**导入域值**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="38bdf-111">Click **OK** to close the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="38bdf-112">您应在列表中看到导入的所有州的名称。</span><span class="sxs-lookup"><span data-stu-id="38bdf-112">You should see all the names of states you imported in the list.</span></span> <span data-ttu-id="38bdf-113">请注意，在导入后会自动选择 "**仅显示新**选项"。</span><span class="sxs-lookup"><span data-stu-id="38bdf-113">Notice that **Show Only New** option is automatically selected after importing.</span></span> <span data-ttu-id="38bdf-114">导入值后，在列表中看不到旧值，这是因为在导入后会自动启用此选项。</span><span class="sxs-lookup"><span data-stu-id="38bdf-114">When you import values and you don't see the old values in the list, it is because this option is automatically enabled after importing.</span></span> <span data-ttu-id="38bdf-115">要查看所有值，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="38bdf-115">To see all the values, clear the check box.</span></span> <span data-ttu-id="38bdf-116">如果再次导入相同的一组值，则不导入任何值，因为它们在域中已存在。</span><span class="sxs-lookup"><span data-stu-id="38bdf-116">If you import the same set of values again, none of the values are imported as they already exist in the domain.</span></span>

     <span data-ttu-id="38bdf-117">![仅显示域值的新复选框](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "仅显示域值的新复选框")</span><span class="sxs-lookup"><span data-stu-id="38bdf-117">![Show Only New Checkbox on Domain Values](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "Show Only New Checkbox on Domain Values")</span></span>

## <a name="next-step"></a><span data-ttu-id="38bdf-118">下一步</span><span class="sxs-lookup"><span data-stu-id="38bdf-118">Next Step</span></span>
 [<span data-ttu-id="38bdf-119">任务 4：设置域规则</span><span class="sxs-lookup"><span data-stu-id="38bdf-119">Task 4: Setting Domain Rules</span></span>](../../2014/tutorials/task-4-setting-domain-rules.md)


