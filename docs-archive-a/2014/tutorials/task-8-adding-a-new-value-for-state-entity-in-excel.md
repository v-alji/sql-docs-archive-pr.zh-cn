---
title: 任务8：在 Excel 中为 State 实体添加新值 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cace99419997e48088420c331a823cdf3639a3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690896"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a><span data-ttu-id="1754c-102">任务 8：在 Excel 中为 State 实体添加新值</span><span class="sxs-lookup"><span data-stu-id="1754c-102">Task 8: Adding a New Value for State Entity in Excel</span></span>
  <span data-ttu-id="1754c-103">在本任务中，您将在 Excel 中为 State 实体添加值，并且将更改发布到 MDS 服务器。</span><span class="sxs-lookup"><span data-stu-id="1754c-103">In this task, you add a value for the State entity in Excel and publish the change to the MDS server.</span></span>  
  
1.  <span data-ttu-id="1754c-104">单击底部的 "新建" 选项卡，在 Excel 中添加**工作表**。</span><span class="sxs-lookup"><span data-stu-id="1754c-104">Add a **work sheet** in Excel by clicking the new tab at the bottom.</span></span>  
  
     <span data-ttu-id="1754c-105">![Excel -“新建工作表”选项卡](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel -“新建工作表”选项卡")</span><span class="sxs-lookup"><span data-stu-id="1754c-105">![Excel - New Worksheet Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - New Worksheet Tab")</span></span>  
  
2.  <span data-ttu-id="1754c-106">在**Excel**中，单击菜单上的 "**主数据**" 选项卡，然后单击功能区上的 "**显示资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="1754c-106">In **Excel**, click the **Master Data** tab on the menu, and then click **Show Explorer** on the ribbon.</span></span>  
  
3.  <span data-ttu-id="1754c-107">在**主数据资源管理器**中，选择 "**模型\*\*\*\*供应商**"。</span><span class="sxs-lookup"><span data-stu-id="1754c-107">In the **Master Data Explorer**, select **Suppliers** for **Model**.</span></span> <span data-ttu-id="1754c-108">应会在实体列表中看到两个实体：**供应商**和**状态**。</span><span class="sxs-lookup"><span data-stu-id="1754c-108">You should see two entities: **Supplier** and **State** in the entity list.</span></span>  
  
4.  <span data-ttu-id="1754c-109">双击列表中的 "**状态**"。</span><span class="sxs-lookup"><span data-stu-id="1754c-109">Double-click **State** in the list.</span></span> <span data-ttu-id="1754c-110">来自 MDS 的**状态**实体的所有成员应显示在工作表中。</span><span class="sxs-lookup"><span data-stu-id="1754c-110">All the members of the **State** entity from MDS should be displayed in the worksheet.</span></span>  
  
5.  <span data-ttu-id="1754c-111">现在，在末尾添加具有以下值的行：**北卡罗来纳**for **Name**和**NC** for **Code**。</span><span class="sxs-lookup"><span data-stu-id="1754c-111">Now, add a row at the end with the following values: **North Carolina** for **Name** and **NC** for **Code**.</span></span> <span data-ttu-id="1754c-112">颜色编码可以将任何新的/更新的记录与其他记录区分开来。</span><span class="sxs-lookup"><span data-stu-id="1754c-112">The color coding differentiates any new/updated records from the other records.</span></span>  
  
     <span data-ttu-id="1754c-113">![Excel - 将北卡罗来纳州添加到“州/省”](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - 将北卡罗来纳州添加到“州/省”")</span><span class="sxs-lookup"><span data-stu-id="1754c-113">![Excel - Add North Carolina to States](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Add North Carolina to States")</span></span>  
  
6.  <span data-ttu-id="1754c-114">在功能区上单击 "**发布**"，将更改发布到 MDS。</span><span class="sxs-lookup"><span data-stu-id="1754c-114">Click **Publish** on the ribbon to publish the change to MDS.</span></span>  
  
     <span data-ttu-id="1754c-115">![Excel -“主数据”选项卡上的“发布”按钮](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel -“主数据”选项卡上的“发布”按钮")</span><span class="sxs-lookup"><span data-stu-id="1754c-115">![Excel - Publish Button on Master Data Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - Publish Button on Master Data Tab")</span></span>  
  
7.  <span data-ttu-id="1754c-116">请注意，在 "**发布并添加批注**" 对话框上，选择 "对**所有更改使用相同的批注**"。</span><span class="sxs-lookup"><span data-stu-id="1754c-116">On the **Publish and Annotate** dialog box, notice that the **Use same annotation for all changes** is selected.</span></span> <span data-ttu-id="1754c-117">您可以在此处为所有更改输入单个批注。</span><span class="sxs-lookup"><span data-stu-id="1754c-117">You can enter a single annotation for all the changes here.</span></span>  
  
8.  <span data-ttu-id="1754c-118">选择 "**查看更改并单独提供批注**" 选项，以便为每个更改提供批注 (在本例中，只有一个) 。</span><span class="sxs-lookup"><span data-stu-id="1754c-118">Select **Review changes and provide annotations individually** option to provide annotation for each change (in this case, only one).</span></span>  
  
     <span data-ttu-id="1754c-119">![Excel -“发布并添加批注”对话框](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel -“发布并添加批注”对话框")</span><span class="sxs-lookup"><span data-stu-id="1754c-119">![Excel - Publish and Annotate Dialog Box](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - Publish and Annotate Dialog Box")</span></span>  
  
9. <span data-ttu-id="1754c-120">单击 "**发布**" 以将数据发布到 MDS。</span><span class="sxs-lookup"><span data-stu-id="1754c-120">Click **Publish** to publish data to MDS.</span></span>  
  
10. <span data-ttu-id="1754c-121">请注意，将**北卡罗莱纳州**的行的**颜色编码**为 "**状态**" 与其他记录相同。</span><span class="sxs-lookup"><span data-stu-id="1754c-121">Notice that **color coding** for the row with **North Carolina** as the **State** is same as other records now.</span></span>  
  
11. <span data-ttu-id="1754c-122">**可选：** 使用**主数据管理器**中的 "**资源管理器**" 来验证是否已将新成员 (NC) 添加到**State**实体。</span><span class="sxs-lookup"><span data-stu-id="1754c-122">**Optional:** Verify that the new member (NC) is added to the **State** entity by using the **Explorer** in **Master Data Manager**.</span></span>  
  
12. <span data-ttu-id="1754c-123">在 Excel 中，右键单击底部的**状态**工作表，然后单击 "**删除**" 以删除该工作表。</span><span class="sxs-lookup"><span data-stu-id="1754c-123">In Excel, right-click the **State** worksheet at the bottom, and click **Delete** to delete the worksheet.</span></span> <span data-ttu-id="1754c-124">删除该工作表不会从 MDS 服务器中删除任何数据。</span><span class="sxs-lookup"><span data-stu-id="1754c-124">Deleting the worksheet does not delete any data from the MDS server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1754c-125">下一步</span><span class="sxs-lookup"><span data-stu-id="1754c-125">Next Step</span></span>  
 [<span data-ttu-id="1754c-126">任务 9：使用主数据管理器创建派生层次结构</span><span class="sxs-lookup"><span data-stu-id="1754c-126">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
