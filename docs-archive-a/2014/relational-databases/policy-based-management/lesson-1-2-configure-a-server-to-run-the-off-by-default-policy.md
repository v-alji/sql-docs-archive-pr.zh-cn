---
title: 将服务器配置为运行 Off By Default 策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0842a30b7d0bbcd1b01ee9e98ed1ed9a74f0f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578161"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a><span data-ttu-id="c456b-102">将服务器配置为运行 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="c456b-102">Configure a Server to Run the Off By Default Policy</span></span>
  <span data-ttu-id="c456b-103">现在有一个名为 Off By Default 的策略。</span><span class="sxs-lookup"><span data-stu-id="c456b-103">Now you have a policy named Off By Default.</span></span> <span data-ttu-id="c456b-104">在本任务中，您将检查服务器是否符合此策略的要求。</span><span class="sxs-lookup"><span data-stu-id="c456b-104">In this task, you will check to see whether your server complies with the requirements of this policy.</span></span>  
  
### <a name="to-run-the-off-by-default-policy"></a><span data-ttu-id="c456b-105">运行 Off By Default 策略</span><span class="sxs-lookup"><span data-stu-id="c456b-105">To run the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="c456b-106">在对象资源管理器中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，指向“策略”\*\*\*\*，然后单击“评估”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c456b-106">In Object Explorer, right-click your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], point to **Policies**, and then click **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="c456b-107">在“评估策略”\*\*\*\* 对话框中，可以从另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或文件中选择策略。</span><span class="sxs-lookup"><span data-stu-id="c456b-107">In the **Evaluate Policies** dialog box you can select policies from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or from a file.</span></span> <span data-ttu-id="c456b-108">对于此步骤，仍将“源”\*\*\*\* 设置为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c456b-108">For this step, leave **Source** set to your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="c456b-109">在“策略”\*\*\*\* 部分中，选择 **Off By Default** 策略。</span><span class="sxs-lookup"><span data-stu-id="c456b-109">In the **Policies** section, select the **Off By Default** policy.</span></span>  
  
4.  <span data-ttu-id="c456b-110">要查看服务器是否符合该策略，请单击“评估”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c456b-110">To see whether the server is in compliance with the policy, click **Evaluate**.</span></span>  
  
5.  <span data-ttu-id="c456b-111">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 符合该策略，则会在“结果”\*\*\*\* 区域中显示带复选标记的绿色圆圈。</span><span class="sxs-lookup"><span data-stu-id="c456b-111">In the **Results** area, you will see a green circle with a check mark if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] complies with the policy.</span></span> <span data-ttu-id="c456b-112">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不符合该策略，则会显示带 X 的红色圆圈。</span><span class="sxs-lookup"><span data-stu-id="c456b-112">You will see a red circle with an X if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not comply with the policy.</span></span>  
  
6.  <span data-ttu-id="c456b-113">在“目标详细信息”\*\*\*\* 区域中，如果发生了错误，你会在“消息”\*\*\*\* 列中看到其他信息。</span><span class="sxs-lookup"><span data-stu-id="c456b-113">In the **Target Details** area, you will see additional information in the **Message** column if an error occurs.</span></span> <span data-ttu-id="c456b-114">在“消息”\*\*\*\* 列中，单击“查看”\*\*\*\* 以查看报表，其中包含所检查的每个方面属性的检查结果。</span><span class="sxs-lookup"><span data-stu-id="c456b-114">In the **Message** column, click **View** to see a report that contains the results of the check for each facet property that was checked.</span></span>  
  
7.  <span data-ttu-id="c456b-115">页面底部将显示策略说明，“更多帮助”\*\*\*\* 部分显示为策略配置的超链接。</span><span class="sxs-lookup"><span data-stu-id="c456b-115">The policy description is displayed at the bottom of the page, and the **Additional help** section displays the hyperlink that you have configured for the policy.</span></span> <span data-ttu-id="c456b-116">单击消息超链接可打开在创建策略时指定的网页。</span><span class="sxs-lookup"><span data-stu-id="c456b-116">Click the message hyperlink to open the Web page that you specified when you created the policy.</span></span>  
  
8.  <span data-ttu-id="c456b-117">关闭浏览器，然后关闭“结果详细视图”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c456b-117">Close the browser, and then close the **Results Detailed View** dialog box.</span></span>  
  
9. <span data-ttu-id="c456b-118">如果服务器不符合该策略并且你希望禁用数据库邮件，请在“评估结果”\*\*\*\* 页中单击“应用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c456b-118">If the server is out of compliance and you want to disable Database Mail, click **Apply** in the **Evaluation Results** page.</span></span>  
  
10. <span data-ttu-id="c456b-119">关闭“结果详细视图”\*\*\*\* 和“评估策略”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c456b-119">Close both the **Results Detailed View** and the **Evaluate Policies** dialog boxes.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="c456b-120">下一课</span><span class="sxs-lookup"><span data-stu-id="c456b-120">Next Lesson</span></span>  
 [<span data-ttu-id="c456b-121">第 2 课：创建并应用命名标准策略</span><span class="sxs-lookup"><span data-stu-id="c456b-121">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
