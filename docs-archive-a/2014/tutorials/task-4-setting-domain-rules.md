---
title: 任务4：设置域规则 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42bdbd0228fdd3515f68ce830581f445242768e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577933"
---
# <a name="task-4-setting-domain-rules"></a><span data-ttu-id="8c4cf-102">任务 4：设置域规则</span><span class="sxs-lookup"><span data-stu-id="8c4cf-102">Task 4: Setting Domain Rules</span></span>
  <span data-ttu-id="8c4cf-103">在此任务中，你将为**联系人电子邮件**域创建一个规则，以验证该电子邮件地址是否以\*\* \@ adventure-works.com\*\*结尾。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-103">In this task, you create a rule for the **Contact Email** domain to verify if the email address ends with **\@adventure-works.com**.</span></span> <span data-ttu-id="8c4cf-104">有关详细信息，请参阅[创建域规则](https://msdn.microsoft.com/library/hh510397.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-104">See [Creating a Domain Rule](https://msdn.microsoft.com/library/hh510397.aspx) topic for more details on the page.</span></span>  
  
1.  <span data-ttu-id="8c4cf-105">单击 "**域列表**" 中的 "**联系人电子邮件**"。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-105">Click **Contact Email** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="8c4cf-106">切换到右窗格中的 "**域规则**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-106">Switch to the **Domain Rules** tab in the right pane.</span></span>  
  
     <span data-ttu-id="8c4cf-107">![“添加新的域规则”工具栏按钮](../../2014/tutorials/media/et-settingdomainrules-01.jpg "“添加新的域规则”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-107">![Add a New Domain Rule Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Add a New Domain Rule Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="8c4cf-108">在右侧窗格中，单击工具栏上的 "**添加新的域规则**" 按钮 (查看图像) 以添加规则。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-108">In the right pane, click **Add a new domain rule** button on the toolbar (see the image) to add a rule.</span></span>  
  
4.  <span data-ttu-id="8c4cf-109">为 "**规则名称**" 键入**电子邮件验证**，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-109">Type **Email Validation** for the **rule name** and press **ENTER**.</span></span> <span data-ttu-id="8c4cf-110">默认情况下，应选中 "**活动**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-110">The **Active** check box should be checked by default.</span></span> <span data-ttu-id="8c4cf-111">此控件允许您临时停用某个规则。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-111">This control allows you to deactivate a rule temporarily.</span></span>  
  
5.  <span data-ttu-id="8c4cf-112">在 "**生成规则**" 窗格中，单击**向下箭头**，然后选择 "**值结束于**"。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-112">In the **Build a Rule** pane, click **down arrow**, and select **Value ends with**.</span></span>  
  
6.  <span data-ttu-id="8c4cf-113">在文本框中键入\*\* \@ adventure-works.com\*\* ，然后按**tab**。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-113">Type **\@adventure-works.com** in the text box and press **TAB**.</span></span> <span data-ttu-id="8c4cf-114">您可以通过在 "**生成规则**" 窗格中单击 **"向选定子句添加新条件"** 工具栏按钮来添加更多条件。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-114">You can add more conditions by clicking **Add a new condition to the selected clause** toolbar button in the **Build a Rule** pane.</span></span>  
  
     <span data-ttu-id="8c4cf-115">![电子邮件验证规则](../../2014/tutorials/media/et-settingdomainrules-02.jpg "电子邮件验证规则")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-115">![Email Validation Rule](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Email Validation Rule")</span></span>  
  
7.  <span data-ttu-id="8c4cf-116">单击右窗格中工具栏上的 "**对测试数据运行所选域规则**" 按钮，针对示例数据测试规则。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-116">Click **Run the selected domain rule on test data** button on the toolbar in the right pane to test the rule against sample data.</span></span>  
  
     <span data-ttu-id="8c4cf-117">![“对测试数据运行域规则”工具栏按钮](../../2014/tutorials/media/et-settingdomainrules-03.jpg "“对测试数据运行域规则”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-117">![Run the Domain Rule on Test Data Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Run the Domain Rule on Test Data Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="8c4cf-118">在 "**测试域规则**" 对话框中，单击工具栏上**的 "为域规则添加新的测试字词"** 。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-118">In the **Test Domain Rule** dialog box, click **Adds a new testing term for the domain rule** button on the toolbar.</span></span>  
  
     <span data-ttu-id="8c4cf-119">![“测试域规则”对话框](../../2014/tutorials/media/et-settingdomainrules-04.jpg "“测试域规则”对话框")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-119">![Test Domain Rule Dialog Box](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Test Domain Rule Dialog Box")</span></span>  
  
9. <span data-ttu-id="8c4cf-120">键入 " **frank7 \@ adventure-works.com** " ("**联系人电子邮件**" 列中) 有效的值。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-120">Type **frank7\@adventure-works.com** (a valid value) in the **Contact Email** column.</span></span>  
  
10. <span data-ttu-id="8c4cf-121">重复前面两个步骤，将**joe2 \@ adventure-work.com** (无效值，不含 ' ) 。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-121">Repeat previous two steps to add **joe2\@adventure-work.com** (an invalid value with no 's').</span></span>  
  
11. <span data-ttu-id="8c4cf-122">单击最后一个按钮 (在工具栏上的**所有字词) 测试域规则**，以根据规则测试输入数据。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-122">Click the last button (**Test the domain rule on all the terms**) on the toolbar to test the input data against the rule.</span></span>  
  
     <span data-ttu-id="8c4cf-123">![“针对所有字词测试域规则”工具栏按钮](../../2014/tutorials/media/et-settingdomainrules-05.jpg "“针对所有字词测试域规则”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-123">![Test the Domain Rule on All Terms Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Test the Domain Rule on All Terms Toolbar Button")</span></span>  
  
12. <span data-ttu-id="8c4cf-124">请注意第一个条目显示为有效项，而第二个条目显示为无效项。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-124">Notice that the first entry is shown as a valid item and the second one as an invalid item.</span></span>  
  
     <span data-ttu-id="8c4cf-125">![测试域规则结果](../../2014/tutorials/media/et-settingdomainrules-06.jpg "测试域规则结果")</span><span class="sxs-lookup"><span data-stu-id="8c4cf-125">![Test Domain Rule Results](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Test Domain Rule Results")</span></span>  
  
13. <span data-ttu-id="8c4cf-126">单击 "**关闭**" 以关闭 "**测试域规则**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8c4cf-126">Click **Close** to close the **Test Domain Rule** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="8c4cf-127">下一步</span><span class="sxs-lookup"><span data-stu-id="8c4cf-127">Next Step</span></span>  
 [<span data-ttu-id="8c4cf-128">任务 5：设置基于字词的关系</span><span class="sxs-lookup"><span data-stu-id="8c4cf-128">Task 5: Setting Term Based Relationships</span></span>](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
