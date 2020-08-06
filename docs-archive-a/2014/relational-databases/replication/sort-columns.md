---
title: 列排序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e5fe56688a009fd60a7731b199f32352d78bb5eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694445"
---
# <a name="sort-columns"></a><span data-ttu-id="79d12-102">列排序</span><span class="sxs-lookup"><span data-stu-id="79d12-102">Sort Columns</span></span>
  <span data-ttu-id="79d12-103">可以使用 **“列排序”** 对话框，根据一个或多个列对复制监视器中的网格进行排序。</span><span class="sxs-lookup"><span data-stu-id="79d12-103">The **Sort Columns** dialog box lets you sort grids in Replication Monitor based on one or more columns.</span></span> <span data-ttu-id="79d12-104">（也可以单击复制监视器网格中的列标题，按单个列进行排序）。</span><span class="sxs-lookup"><span data-stu-id="79d12-104">(You can also sort on a single column by clicking the column header in the Replication Monitor grid).</span></span> <span data-ttu-id="79d12-105">例如，若要基于状态对 **“所有订阅”** 选项卡中的订阅进行排序，再基于连接类型进行排序，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="79d12-105">For example, to sort subscriptions on the **All Subscriptions** tab based on status and then connection type, follow these steps:</span></span>  
  
1.  <span data-ttu-id="79d12-106">在网格的第一行中，选择 **“列名”** 列中的 **“状态”** 并从 **“排序顺序”** 列中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="79d12-106">In the first row of the grid, select **Status** from the **Column Name** column and a value from the **Sort Order** column</span></span>  
  
2.  <span data-ttu-id="79d12-107">在网格的第二行中，选择 **“列名”** 列中的 **“连接类型”** 并从 **“排序顺序”** 列中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="79d12-107">In the second row of the grid, select **Connection Type** from the **Column Name** column, and a value from the **Sort Order** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="79d12-108">选项</span><span class="sxs-lookup"><span data-stu-id="79d12-108">Options</span></span>  
 <span data-ttu-id="79d12-109">**列名称**</span><span class="sxs-lookup"><span data-stu-id="79d12-109">**Column Name**</span></span>  
 <span data-ttu-id="79d12-110">要作为排序依据的列的名称。</span><span class="sxs-lookup"><span data-stu-id="79d12-110">The name of the column on which you want to sort.</span></span> <span data-ttu-id="79d12-111">可以按一个或多个列进行排序。</span><span class="sxs-lookup"><span data-stu-id="79d12-111">You can sort on one or more columns.</span></span> <span data-ttu-id="79d12-112">出于列值计算方式方面的原因，不能按 **“发布”** 选项卡上的 **“当前平均性能”** 或 **“当前最差的性能”** 列进行排序。</span><span class="sxs-lookup"><span data-stu-id="79d12-112">You cannot sort on the **Current Average Performance** or **Current Worst Performance** columns on the **Publications** tab, because of the way in which these column values are calculated.</span></span>  
  
 <span data-ttu-id="79d12-113">**排序顺序**</span><span class="sxs-lookup"><span data-stu-id="79d12-113">**Sort Order**</span></span>  
 <span data-ttu-id="79d12-114">指定值为 **“升序”** 或 **“降序”** 。</span><span class="sxs-lookup"><span data-stu-id="79d12-114">Specify a value of **Ascending** or **Descending**.</span></span>  
  
 <span data-ttu-id="79d12-115">**全部清除**</span><span class="sxs-lookup"><span data-stu-id="79d12-115">**Clear All**</span></span>  
 <span data-ttu-id="79d12-116">清除排序网格中的所有行。</span><span class="sxs-lookup"><span data-stu-id="79d12-116">Remove all rows from the sorting grid.</span></span> <span data-ttu-id="79d12-117">若要移除某个行，请选择该行，然后按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="79d12-117">To remove a single row, select the row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d12-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79d12-118">See Also</span></span>  
 [<span data-ttu-id="79d12-119">监视复制</span><span class="sxs-lookup"><span data-stu-id="79d12-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
