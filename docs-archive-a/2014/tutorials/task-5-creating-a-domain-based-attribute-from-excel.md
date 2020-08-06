---
title: 任务5：从 Excel 中创建基于域的属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b866478150fb4c06a3c4ea1ee6c227527f963219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689675"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a><span data-ttu-id="fc6a9-102">任务 5：从 Excel 中创建基于域的属性</span><span class="sxs-lookup"><span data-stu-id="fc6a9-102">Task 5: Creating a Domain-Based Attribute from Excel</span></span>
  <span data-ttu-id="fc6a9-103">在此任务中，您将**供应商**实体的**State**属性转换为**基于域的属性**。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-103">In this task, you convert the **State** attribute of the **Supplier** entity as a **domain-based attribute**.</span></span> <span data-ttu-id="fc6a9-104">将状态属性配置为基于域的属性并将其发布到 MDS 后，将在 MDS 服务器上创建一个名为 "**状态**" 的新实体，其中包含列中的所有值，并使用 "**状态**" 实体中的值填充 "**供应商**" 实体的 "**状态**" 属性。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-104">After you configure the State attribute to be a domain-based one and publish it to MDS, a new entity named **State** will be created on MDS server with all the values in the column and the **State** attribute of the **Supplier** entity will be populated with values from the **State** entity.</span></span> <span data-ttu-id="fc6a9-105">现在，**供应**商模型应具有两个实体 **：供应商和\*\*\*\*州**，其中**供应商**实体的**state**属性是依赖于**州**实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-105">Now, the **Suppliers** model should have two entities: **Supplier** and **State** where the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on **State** entity.</span></span>  
  
1.  <span data-ttu-id="fc6a9-106">切换到**清理并匹配 Suppliers.xlsx**打开的**Excel**窗口。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-106">Switch to **Excel** window that has **Cleansed and Matched Suppliers.xlsx** open.</span></span>  
  
2.  <span data-ttu-id="fc6a9-107">单击功能区上的 "**刷新**" 按钮可从 MDS 获取最新更新。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-107">Click **Refresh** button on the ribbon to get the latest updates from MDS.</span></span> <span data-ttu-id="fc6a9-108">如果执行了可选**任务 4**，则应该会看到另外两个记录。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-108">You should see the two more records if you have performed the optional **Task 4**.</span></span>  
  
3.  <span data-ttu-id="fc6a9-109">在**标题行**中单击 "列名称**状态** (单元格**I1**) 。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-109">Click column name **State** (cell **I1**) in the **header row**.</span></span>  
  
     <span data-ttu-id="fc6a9-110">![Excel -“特性”属性按钮](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel -“特性”属性按钮")</span><span class="sxs-lookup"><span data-stu-id="fc6a9-110">![Excel - Attribute Properties Button](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - Attribute Properties Button")</span></span>  
  
4.  <span data-ttu-id="fc6a9-111">在功能区上单击 "**特性属性**"。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-111">Click **Attribute Properties** on the ribbon.</span></span>  
  
5.  <span data-ttu-id="fc6a9-112">在 "**特性属性**" 对话框中，选择 "**约束列表 (基于域的) **作为**属性类型**。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-112">In the **Attribute Properties** dialog box, select **Constrained list (Domain-based)** for the **Attribute type**.</span></span>  
  
6.  <span data-ttu-id="fc6a9-113">键入**新实体名称**的**状态**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-113">Type **State** for the **New entity name** and click **OK**.</span></span>  
  
     <span data-ttu-id="fc6a9-114">![Excel -“特性”属性对话框](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel -“特性”属性对话框")</span><span class="sxs-lookup"><span data-stu-id="fc6a9-114">![Excel - Attribute Properties Dialog Box](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribute Properties Dialog Box")</span></span>  
  
7.  <span data-ttu-id="fc6a9-115">现在，在 Excel 中，单击 "**状态**" 列中的任何值时，应会看到**向下箭头**。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-115">Now, in Excel, you should see **down arrow** when you click any value in the **State** column.</span></span> <span data-ttu-id="fc6a9-116">可以根据需要使用下拉列表来更改该值。</span><span class="sxs-lookup"><span data-stu-id="fc6a9-116">You can change the value by using the drop-down list if you need.</span></span>  
  
     <span data-ttu-id="fc6a9-117">![Excel - 带州/省的下拉列表](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - 带州/省的下拉列表")</span><span class="sxs-lookup"><span data-stu-id="fc6a9-117">![Excel - Drop Down List with States](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - Drop Down List with States")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="fc6a9-118">下一步</span><span class="sxs-lookup"><span data-stu-id="fc6a9-118">Next Step</span></span>  
 [<span data-ttu-id="fc6a9-119">任务 6：验证基于域的属性是否使用主数据管理器进行创建</span><span class="sxs-lookup"><span data-stu-id="fc6a9-119">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
