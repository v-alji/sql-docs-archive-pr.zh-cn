---
title: 定义筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5154f002c5a35bc78e2eb6777f2cc7bb3d56b635
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578131"
---
# <a name="define-filters"></a><span data-ttu-id="c2bc6-102">定义筛选器</span><span class="sxs-lookup"><span data-stu-id="c2bc6-102">Define Filters</span></span>
  <span data-ttu-id="c2bc6-103">可以使用 **“定义筛选器”** 对话框定义筛选器，然后将筛选器应用于数据冲突以在网格中查看冲突的子集。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-103">The **Define Filters** dialog box allows you to define filters that you then apply to data conflicts to see a subset of the conflicts in the grid.</span></span> <span data-ttu-id="c2bc6-104">若要定义筛选器，请从 **“运算符”** 下拉列表框中选择运算符，然后输入值。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-104">To define a filter, choose an operator from the **Operator** drop-down list box and then enter a value.</span></span> <span data-ttu-id="c2bc6-105">例如，若要只显示冲突解决落选方为服务器 **ReplTest1**的那些冲突，请从 **“运算符”** 下拉列表框中选择 **“等于”** ，然后在第一个 **“值”** 列中输入 **ReplTest1** 。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-105">For example, to show only those conflicts in which the conflict loser is server **ReplTest1**, select **Equal to** from the **Operator** drop-down list box and enter **ReplTest1** in the first **Value** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c2bc6-106">选项</span><span class="sxs-lookup"><span data-stu-id="c2bc6-106">Options</span></span>  
 <span data-ttu-id="c2bc6-107">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="c2bc6-107">**Operator**</span></span>  
 <span data-ttu-id="c2bc6-108">为筛选器选择一个运算符，例如 **“小于或等于”** 。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-108">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="c2bc6-109">**值**</span><span class="sxs-lookup"><span data-stu-id="c2bc6-109">**Value**</span></span>  
 <span data-ttu-id="c2bc6-110">为筛选器输入一个值。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-110">Enter a value for the filter.</span></span> <span data-ttu-id="c2bc6-111">大多数运算符只需要在第一个 **“值”** 列中输入值，但 **“介于”** 和 **“不介于”** 运算符需要在两个 **“值”** 列中都输入值。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-111">Most operators only require a value in the first **Value** column, but the **Between** and **Not Between** operators require a value in both of the **Value** columns.</span></span>  
  
 <span data-ttu-id="c2bc6-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="c2bc6-112">**Clear**</span></span>  
 <span data-ttu-id="c2bc6-113">单击此按钮可以清除先前定义的所有筛选器。</span><span class="sxs-lookup"><span data-stu-id="c2bc6-113">Click this button to clear all filters that have been previously defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2bc6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2bc6-114">See Also</span></span>  
 <span data-ttu-id="c2bc6-115">[Microsoft 复制冲突查看器（合并复制）](microsoft-replication-conflict-viewer-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c2bc6-115">[Microsoft Replication Conflict Viewer &#40;Merge Replication&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span></span>  
 [<span data-ttu-id="c2bc6-116">Microsoft 复制冲突查看器（事务复制）</span><span class="sxs-lookup"><span data-stu-id="c2bc6-116">Microsoft Replication Conflict Viewer &#40;Transactional Replication&#41;</span></span>](microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
