---
title: 任务8：创建复合域规则 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4766a1206eb09e98bb20d3712a63762126b682b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589386"
---
# <a name="task-8-creating-a-composite-domain-rule"></a><span data-ttu-id="4dd42-102">任务 8：创建复合域规则</span><span class="sxs-lookup"><span data-stu-id="4dd42-102">Task 8: Creating a Composite Domain Rule</span></span>
  <span data-ttu-id="4dd42-103">在此任务中，您将为 "**地址验证**" 复合域创建规则。</span><span class="sxs-lookup"><span data-stu-id="4dd42-103">In this task, you create a rule for the **Address Validation** composite domain.</span></span> <span data-ttu-id="4dd42-104">定义跨域规则：如果**city**为**洛杉矶，则** **state**必须为**CA** ，其中**City**和**state**是两个域。</span><span class="sxs-lookup"><span data-stu-id="4dd42-104">You define a cross-domain rule: if **City** is **Los Angeles**, **State** must be **CA** where **City** and **State** are two domains.</span></span>  
  
1.  <span data-ttu-id="4dd42-105">在右侧窗格中，切换到 " **CD 规则**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4dd42-105">In the right pane, switch to the **CD Rules** tab.</span></span>  
  
2.  <span data-ttu-id="4dd42-106">单击工具栏中的 "**添加新的域规则**"。</span><span class="sxs-lookup"><span data-stu-id="4dd42-106">Click **Add a new domain rule** from the toolbar.</span></span>  
  
3.  <span data-ttu-id="4dd42-107">键入 " **City-** **Name**规则"，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="4dd42-107">Type **City-State Rule** for **Name** and press **ENTER**.</span></span>  
  
4.  <span data-ttu-id="4dd42-108">在 "**生成规则**" 窗格中，选择 "域列表" 中的 "**城市**"，然后选择 "条件**值等于**"，然后键入**洛杉矶**作为值。</span><span class="sxs-lookup"><span data-stu-id="4dd42-108">In the **Build a Rule** pane, select **City** in the domain list, and select condition **Value is equal to** and type **Los Angeles** for the value.</span></span>  
  
5.  <span data-ttu-id="4dd42-109">在 " **Then** " 窗格中，选择 "域列表" 中的 "**状态**"，然后选择 "**值等于**"，键入**CA**作为值，然后按**tab**。</span><span class="sxs-lookup"><span data-stu-id="4dd42-109">In the **Then** pane, select **State** in the domain list, and select **Value is equal to**, type **CA** for the value, and press **TAB**.</span></span>  
  
     <span data-ttu-id="4dd42-110">![复合域规则](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "复合域规则")</span><span class="sxs-lookup"><span data-stu-id="4dd42-110">![Composite Domain Rule](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Composite Domain Rule")</span></span>  
  
6.  <span data-ttu-id="4dd42-111">单击页面底部的 "**关闭**" 按钮可切换到 DQS 客户端的主页。</span><span class="sxs-lookup"><span data-stu-id="4dd42-111">Click **Close** button at the bottom of the page to switch to the main page of DQS Client.</span></span> <span data-ttu-id="4dd42-112">在下一课将发布知识库。</span><span class="sxs-lookup"><span data-stu-id="4dd42-112">You will publish the knowledge base in the next lesson.</span></span> <span data-ttu-id="4dd42-113">注意，知识库处于锁定状态（锁定图标）。</span><span class="sxs-lookup"><span data-stu-id="4dd42-113">Notice that the knowledge base is in locked state (lock icon).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="4dd42-114">下一步</span><span class="sxs-lookup"><span data-stu-id="4dd42-114">Next Step</span></span>  
 [<span data-ttu-id="4dd42-115">任务 9：配置引用数据服务</span><span class="sxs-lookup"><span data-stu-id="4dd42-115">Task 9: Configuring a Reference Data Service</span></span>](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
