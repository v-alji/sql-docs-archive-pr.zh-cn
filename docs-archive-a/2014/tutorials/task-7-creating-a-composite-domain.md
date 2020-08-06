---
title: 任务7：创建复合域 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577125"
---
# <a name="task-7-creating-a-composite-domain"></a><span data-ttu-id="a6a4d-102">任务 7：创建复合域</span><span class="sxs-lookup"><span data-stu-id="a6a4d-102">Task 7: Creating a Composite Domain</span></span>
  <span data-ttu-id="a6a4d-103">在此任务中，你将创建一个包含**地址行**、**城市**、省/市/**自治区**和**Zip**域的复合域**地址验证**。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-103">In this task, you create a composite domain, **Address Validation**, which comprises **Address Line**, **City**, **State**, and **Zip** domains.</span></span> <span data-ttu-id="a6a4d-104">通过复合域，您可以定义在一个规则中涉及多个域的跨域规则。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-104">A composite domain lets you define a cross-domain rule that involves multiple domains in a rule.</span></span> <span data-ttu-id="a6a4d-105">复合域还有其他一些好处，例如能够将一个字段值分析到多个域中。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-105">There are other advantages to a composite domain such as being able to parse a field value into multiple domains.</span></span>  <span data-ttu-id="a6a4d-106">例如，可以将“全名”字段的值分析到单独的“名字”、“中间名”和“姓氏”域中。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-106">For example, a value for a Full Name field can be parsed into separate First Name, Middle Name, and Last Name domains.</span></span> <span data-ttu-id="a6a4d-107">在本教程中，您将只定义一个跨域规则。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-107">In this tutorial, you only define a cross-domain rule.</span></span> <span data-ttu-id="a6a4d-108">有关更多详细信息，请参阅[管理复合域](https://msdn.microsoft.com/library/hh510399.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-108">See [Managing a Composite Domain](https://msdn.microsoft.com/library/hh510399.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="a6a4d-109">在左侧窗格中，单击工具栏上的 "**创建复合域**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-109">In the left pane, click **Create a composite domain** button on the toolbar.</span></span>  
  
     <span data-ttu-id="a6a4d-110">![“创建复合域”工具栏按钮](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "“创建复合域”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="a6a4d-110">![Create a Composite Domain Toolbar Button](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Create a Composite Domain Toolbar Button")</span></span>  
  
2.  <span data-ttu-id="a6a4d-111">输入**复合域名**的**地址验证**。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-111">Enter **Address Validation** for the **Composite Domain Name**.</span></span>  
  
     <span data-ttu-id="a6a4d-112">![地址验证复合域](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "地址验证复合域")</span><span class="sxs-lookup"><span data-stu-id="a6a4d-112">![Address Validation Composite Domain](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Address Validation Composite Domain")</span></span>  
  
3.  <span data-ttu-id="a6a4d-113">从 "域" 列表中，选择 "**地址行**"、"**城市**"、"省/市/**自治区**" 和 " **Zip** "，然后单击**向右箭头**将其添加到 "**复合域**</span><span class="sxs-lookup"><span data-stu-id="a6a4d-113">From the domain list select **Address Line**, **City**, **State**, and **Zip** and click **right arrow** to add them to the **Domains in Composite Domain** list.</span></span>  
  
4.  <span data-ttu-id="a6a4d-114">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="a6a4d-114">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a6a4d-115">下一步</span><span class="sxs-lookup"><span data-stu-id="a6a4d-115">Next Step</span></span>  
 [<span data-ttu-id="a6a4d-116">任务 8：创建复合域规则</span><span class="sxs-lookup"><span data-stu-id="a6a4d-116">Task 8: Creating a Composite Domain Rule</span></span>](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
