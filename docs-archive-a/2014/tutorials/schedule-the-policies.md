---
title: 计划策略 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1bce1b9d650606e9485899c34c72ca6b27a72dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691378"
---
# <a name="schedule-the-policies"></a><span data-ttu-id="c363d-102">计划策略</span><span class="sxs-lookup"><span data-stu-id="c363d-102">Schedule the Policies</span></span>
  <span data-ttu-id="c363d-103">在此任务中，您将计划在前一个任务中导入的最佳实践策略。</span><span class="sxs-lookup"><span data-stu-id="c363d-103">In this task, you will schedule the best practices policies that you imported in the previous task.</span></span>  
  
### <a name="to-schedule-the-best-practices-policies"></a><span data-ttu-id="c363d-104">计划最佳实践策略</span><span class="sxs-lookup"><span data-stu-id="c363d-104">To schedule the best practices policies</span></span>  
  
1.  <span data-ttu-id="c363d-105">在对象资源管理器中，依次展开 "**管理**"、"**策略管理**"、"**策略**"，右键单击最佳实践策略，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="c363d-105">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Policies**, right-click a best practices policy, and then click **Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c363d-106">作为替代方法，若要轻松查看哪些策略与最佳做法相关联并对最佳实践类别进行排序，请依次展开 "**管理**"、"**策略管理**"，然后单击 "**策略**"。</span><span class="sxs-lookup"><span data-stu-id="c363d-106">As an alternative, to easily see which policies are associated with best practices and to sort the best practices categories, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span> <span data-ttu-id="c363d-107">在“视图”\*\*\*\* 菜单中，单击“对象资源管理器详细信息”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c363d-107">On the **View** menu, click **Object Explorer Details**.</span></span> <span data-ttu-id="c363d-108">在 "**对象资源管理器详细信息**" 窗格中，单击 "**类别**" 标题以按类别对策略进行排序。</span><span class="sxs-lookup"><span data-stu-id="c363d-108">In the **Object Explorer Details** pane, click the **Category** heading to sort the policies by category.</span></span> <span data-ttu-id="c363d-109">最佳实践策略具有前缀**Microsoft 最佳实践**。</span><span class="sxs-lookup"><span data-stu-id="c363d-109">The best practices policies have the prefix **Microsoft Best Practices**.</span></span> <span data-ttu-id="c363d-110">右键单击要配置的策略，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="c363d-110">Right-click the policy that you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c363d-111">在 "**打开策略**" 对话框的 "**常规**" 页上的 "**评估模式**" 列表中，单击 "**按计划**"。</span><span class="sxs-lookup"><span data-stu-id="c363d-111">On the **General** page of the **Open Policy** dialog box, in the **Evaluation Mode** list, click **On schedule**.</span></span>  
  
3.  <span data-ttu-id="c363d-112">在 "**计划**" 框的旁边，单击 "**选择**" 以指定现有计划，或单击 "**新建**" 以创建新计划。</span><span class="sxs-lookup"><span data-stu-id="c363d-112">Next to the **Schedule** box, click **Pick** to specify an existing schedule, or click **New** to create a new schedule.</span></span>  
  
4.  <span data-ttu-id="c363d-113">配置计划后，可以选中页面顶部附近的 "**已启用**" 复选框以启用计划策略。</span><span class="sxs-lookup"><span data-stu-id="c363d-113">After you have configured a schedule, you can select the **Enabled** check box near the top of the page to enable the scheduled policy.</span></span>  
  
5.  <span data-ttu-id="c363d-114">对于要计划的每种策略，重复步骤 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="c363d-114">Repeats steps 1 through 4 for each policy that you want to schedule.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c363d-115">若要在运行计划的策略之后查看评估结果，请打开目标实例上的“策略历史记录”日志。</span><span class="sxs-lookup"><span data-stu-id="c363d-115">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="c363d-116">若要打开日志，请右键单击 "**策略管理**"，然后单击 "**查看历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="c363d-116">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c363d-117">摘要</span><span class="sxs-lookup"><span data-stu-id="c363d-117">Summary</span></span>  
 <span data-ttu-id="c363d-118">您配置了要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的单个实例上运行的计划的策略。</span><span class="sxs-lookup"><span data-stu-id="c363d-118">You configured scheduled policies to run on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c363d-119">如果您想要将计划的策略部署到多个实例上，则继续执行本教程中的下一个任务。</span><span class="sxs-lookup"><span data-stu-id="c363d-119">If you want to deploy scheduled policies to multiple instances, continue to the next task in this tutorial.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c363d-120">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c363d-120">Next Steps</span></span>  
 [<span data-ttu-id="c363d-121">将计划的策略部署到多个实例</span><span class="sxs-lookup"><span data-stu-id="c363d-121">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
