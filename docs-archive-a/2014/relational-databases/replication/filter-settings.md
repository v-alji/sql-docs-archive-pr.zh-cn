---
title: 筛选器设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d82d5f38eb460f392f1eb2ed3387ce3d97757db5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578092"
---
# <a name="filter-settings"></a><span data-ttu-id="65a1d-102">筛选器设置</span><span class="sxs-lookup"><span data-stu-id="65a1d-102">Filter Settings</span></span>
  <span data-ttu-id="65a1d-103">可以使用 **“筛选设置”** 对话框为复制监视器中的网格定义筛选器。</span><span class="sxs-lookup"><span data-stu-id="65a1d-103">The **Filter Settings** dialog box lets you define filters for grids in Replication Monitor.</span></span> <span data-ttu-id="65a1d-104">例如，若要只显示 **“所有订阅”** 选项卡上处于活动状态的订阅，请从 **“列名”** 列选择 **“状态”** ，从 **“运算符”** 列选择 **“等于”** 并从 **“值1”** 列选择 **“活动”** 。</span><span class="sxs-lookup"><span data-stu-id="65a1d-104">For example, to show only those subscriptions that are active on the **All Subscriptions** tab, select **Status** from the **Column Name** column, **Equals** from the **Operator** column, and **Active** from the **Value1** column.</span></span> <span data-ttu-id="65a1d-105">在您基于一个或多个列定义筛选器之后，将应用筛选器以便网格中只显示与筛选器条件匹配的子集行。</span><span class="sxs-lookup"><span data-stu-id="65a1d-105">After you define a filter that is based one or more columns, the filter is applied so that the grid displays only the subset of rows that match the filter criteria.</span></span>  
  
## <a name="options"></a><span data-ttu-id="65a1d-106">选项</span><span class="sxs-lookup"><span data-stu-id="65a1d-106">Options</span></span>  
 <span data-ttu-id="65a1d-107">**列名称**</span><span class="sxs-lookup"><span data-stu-id="65a1d-107">**Column Name**</span></span>  
 <span data-ttu-id="65a1d-108">选择要对其进行筛选的列的名称。</span><span class="sxs-lookup"><span data-stu-id="65a1d-108">Select the name of the column on which you want to filter.</span></span> <span data-ttu-id="65a1d-109">您可以使筛选器基于一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="65a1d-109">You can base a filter on one or more columns.</span></span>  
  
 <span data-ttu-id="65a1d-110">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="65a1d-110">**Operator**</span></span>  
 <span data-ttu-id="65a1d-111">为筛选器选择一个运算符，例如 **“小于或等于”** 。</span><span class="sxs-lookup"><span data-stu-id="65a1d-111">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="65a1d-112">**“值1”** 和 **“值2”**</span><span class="sxs-lookup"><span data-stu-id="65a1d-112">**Value1** and **Value2**</span></span>  
 <span data-ttu-id="65a1d-113">为筛选器输入或选择一个值。</span><span class="sxs-lookup"><span data-stu-id="65a1d-113">Enter or select a value for the filter.</span></span> <span data-ttu-id="65a1d-114">大多数运算符只要求在 **“值1”** 列中提供值，但 **“介于”** 和 **“不介于”** 运算符还要求在 **“值2”** 列中提供值。</span><span class="sxs-lookup"><span data-stu-id="65a1d-114">Most operators only require a value in the **Value1** column, but the **Between** and **Not Between** operators also require a value in the **Value2** column.</span></span>  
  
 <span data-ttu-id="65a1d-115">**清除筛选器**</span><span class="sxs-lookup"><span data-stu-id="65a1d-115">**Clear Filter**</span></span>  
 <span data-ttu-id="65a1d-116">单击此按钮可以清除已定义的所有筛选器。</span><span class="sxs-lookup"><span data-stu-id="65a1d-116">Click this button to clear all filters that have been defined.</span></span> <span data-ttu-id="65a1d-117">若要删除某个筛选器，请选中此筛选器行并按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="65a1d-117">To remove a single filter, select the filter row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a1d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65a1d-118">See Also</span></span>  
 [<span data-ttu-id="65a1d-119">监视复制</span><span class="sxs-lookup"><span data-stu-id="65a1d-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
