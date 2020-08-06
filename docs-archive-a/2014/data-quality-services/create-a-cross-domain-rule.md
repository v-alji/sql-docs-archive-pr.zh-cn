---
title: 创建跨域规则 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.testcdrule.f1
- sql12.dqs.dm.cdrules.f1
ms.assetid: 0f3f5ba4-cc47-4d66-866e-371a042d1f21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cddcd9bbd2fc8d95fe8645781de5fe4e936050a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683064"
---
# <a name="create-a-cross-domain-rule"></a><span data-ttu-id="f16ae-102">创建跨域规则</span><span class="sxs-lookup"><span data-stu-id="f16ae-102">Create a Cross-Domain Rule</span></span>
  <span data-ttu-id="f16ae-103">本主题描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的知识库中为复合域创建跨域规则。</span><span class="sxs-lookup"><span data-stu-id="f16ae-103">This topic describes how to create a cross-domain rule for a composite domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="f16ae-104">跨域规则测试在复合域中包含的单一域中各值之间的关系。</span><span class="sxs-lookup"><span data-stu-id="f16ae-104">A cross-domain rule tests the relationship between values in single domains that are included in a composite domain.</span></span> <span data-ttu-id="f16ae-105">跨域规则必须在复合域中保持正确，这样才能认为域值是准确的并且符合业务要求。</span><span class="sxs-lookup"><span data-stu-id="f16ae-105">A cross-domain rule must hold true across a composite domain in order for domain values to be considered accurate and conformant to business requirements.</span></span> <span data-ttu-id="f16ae-106">跨域规则用于验证、更正和标准化域值。</span><span class="sxs-lookup"><span data-stu-id="f16ae-106">A cross-domain rule is used to validate, correct, and standardize domain values.</span></span>  
  
 <span data-ttu-id="f16ae-107">将分别为复合域中的单一域之一定义跨域规则的 If 子句和 Then 子句。</span><span class="sxs-lookup"><span data-stu-id="f16ae-107">The If clause and Then clause of a cross-domain rule are each defined for one of the single domains in the composite domain.</span></span> <span data-ttu-id="f16ae-108">必须为不同的单一域定义每个子句。</span><span class="sxs-lookup"><span data-stu-id="f16ae-108">Each clause must be defined for a different single domain.</span></span> <span data-ttu-id="f16ae-109">跨域规则必须与多个单一域相关；不能为复合域定义简单域规则（仅针对单一域）。</span><span class="sxs-lookup"><span data-stu-id="f16ae-109">A cross-domain rule must relate to multiple single domains; you cannot define a simple domain rule (for only a single domain) for a composite domain.</span></span> <span data-ttu-id="f16ae-110">您应该通过为单一域定义域规则来这样做。</span><span class="sxs-lookup"><span data-stu-id="f16ae-110">You would do so by defining a domain rule for a single domain.</span></span> <span data-ttu-id="f16ae-111">If 子句和 Then 子句可分别包含一个或多个条件。</span><span class="sxs-lookup"><span data-stu-id="f16ae-111">The If clause and the Then clause can each contain one or more conditions.</span></span>  
  
 <span data-ttu-id="f16ae-112">具有可定义条件的跨域规则将规则逻辑应用于条件中的值的同义词以及这些值本身。</span><span class="sxs-lookup"><span data-stu-id="f16ae-112">A cross-domain rule that has definitive conditions will apply the rules logic to synonyms of the value in the conditions, as well the values themselves.</span></span> <span data-ttu-id="f16ae-113">If 和 Then 子句的可定义条件是值等于、值不等于、值处于和值不处于。</span><span class="sxs-lookup"><span data-stu-id="f16ae-113">The definitive conditions for the If and Then clauses are Value is equal to, Value is not equal to, Value is in, or Value is not in.</span></span> <span data-ttu-id="f16ae-114">例如，假定对于某一复合域，你具有以下跨域规则：“For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'”。</span><span class="sxs-lookup"><span data-stu-id="f16ae-114">For example, suppose that you have the following cross-domain rule for a composite domain: "For 'City', if Value is equal to 'Los Angeles', then for 'State', Value is equal to 'CA'.</span></span> <span data-ttu-id="f16ae-115">如果“Los Angeles”和“LA”是同义词，则此规则对于“Los Angeles CA”和“LA CA”将返回正确结果，对于“Los Angeles WA”和“LA WA”将返回错误结果。</span><span class="sxs-lookup"><span data-stu-id="f16ae-115">"If 'Los Angeles' and 'LA' are synonyms, this rule will return correct for 'Los Angeles CA' and 'LA CA' and in error for 'Los Angeles WA' and 'LA WA'.</span></span>  
  
 <span data-ttu-id="f16ae-116">除了让您知道跨域规则的有效性之外，跨域规则 *“值等于”* 中的可定义 **Then**子句还在数据清理活动过程中更正数据。</span><span class="sxs-lookup"><span data-stu-id="f16ae-116">Apart from just letting you know about the validity of a cross-domain rule, the definitive *Then* clause in a cross-domain rule, **Value is equal to**, also corrects the data during the data-cleansing activity.</span></span> <span data-ttu-id="f16ae-117">有关详细信息，请参阅 [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) 中的 [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="f16ae-117">For more information, see [Data Correction using Definitive Cross-Domain Rules](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md#CDCorrection) in [Cleanse Data in a Composite Domain](../../2014/data-quality-services/cleanse-data-in-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="f16ae-118">应首先考虑仅影响单一域的所有简单规则，之后才考虑跨域规则。</span><span class="sxs-lookup"><span data-stu-id="f16ae-118">Cross-domain rules are taken into consideration after all simple rules that affect only a single domain.</span></span> <span data-ttu-id="f16ae-119">只有在某个值通过单一域规则（如果它们存在）之后，才会应用跨域规则。</span><span class="sxs-lookup"><span data-stu-id="f16ae-119">Only if a value passes single domain rules (if they exist) is the cross-domain rule applied.</span></span> <span data-ttu-id="f16ae-120">对其运行某个规则的复合域和单一域必须全都定义后，才能执行该规则。</span><span class="sxs-lookup"><span data-stu-id="f16ae-120">The composite domain and the single domains that a rule is run on must all be defined before the rule can be executed.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f16ae-121">开始之前</span><span class="sxs-lookup"><span data-stu-id="f16ae-121">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="f16ae-122">先决条件</span><span class="sxs-lookup"><span data-stu-id="f16ae-122">Prerequisites</span></span>  
 <span data-ttu-id="f16ae-123">若要创建一个跨域规则，必须已创建并打开了一个复合域。</span><span class="sxs-lookup"><span data-stu-id="f16ae-123">To create a cross-domain rule, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f16ae-124">Security</span><span class="sxs-lookup"><span data-stu-id="f16ae-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f16ae-125">权限</span><span class="sxs-lookup"><span data-stu-id="f16ae-125">Permissions</span></span>  
 <span data-ttu-id="f16ae-126">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能创建跨域规则。</span><span class="sxs-lookup"><span data-stu-id="f16ae-126">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a cross-domain rule.</span></span>  
  
##  <a name="create-cross-domain-rules"></a><a name="Create"></a> <span data-ttu-id="f16ae-127">创建跨域规则</span><span class="sxs-lookup"><span data-stu-id="f16ae-127">Create Cross-Domain Rules</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="f16ae-128">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f16ae-128">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="f16ae-129">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的主屏幕中，打开或创建一个知识库。</span><span class="sxs-lookup"><span data-stu-id="f16ae-129">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="f16ae-130">选择 **“域管理”** 作为活动，然后单击 **“打开”** 或 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="f16ae-130">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="f16ae-131">有关详细信息，请参阅 [创建知识库](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [打开知识库](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="f16ae-131">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f16ae-132">域管理在 Data Quality Service 客户端页面中执行，该页面包含用于单独域管理操作的五个选项卡。</span><span class="sxs-lookup"><span data-stu-id="f16ae-132">Domain management is performed in a page of the Data Quality Service client that contains five tabs for separate domain management operations.</span></span> <span data-ttu-id="f16ae-133">它不是一个向导驱动的过程；任何管理操作都可以单独执行。</span><span class="sxs-lookup"><span data-stu-id="f16ae-133">It is not a wizard-driven process; any management operation can be performed separately.</span></span>  
  
3.  <span data-ttu-id="f16ae-134">从 **“域管理”** 页上的 **“域列表”** 中，选择您要为其创建域规则的复合域，或者创建一个新的复合域。</span><span class="sxs-lookup"><span data-stu-id="f16ae-134">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="f16ae-135">如果您必须创建新域，请参阅 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="f16ae-135">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="f16ae-136">单击 **“复合域规则”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f16ae-136">Click the **CD Rules** tab.</span></span>  
  
5.  <span data-ttu-id="f16ae-137">单击 **“添加新的域规则”**，然后为该规则输入名称和说明。</span><span class="sxs-lookup"><span data-stu-id="f16ae-137">Click **Add a new domain rule**, and then enter a name and description for the rule.</span></span>  
  
6.  <span data-ttu-id="f16ae-138">选择 **“活动”** 可指定将运行该规则（默认设置），取消选中则可以阻止该规则运行。</span><span class="sxs-lookup"><span data-stu-id="f16ae-138">Select **Active** to specify that the rule will be run (the default), and deselect to prevent the rule from running.</span></span>  
  
7.  <span data-ttu-id="f16ae-139">按如下所示创建 If 子句：</span><span class="sxs-lookup"><span data-stu-id="f16ae-139">Create the If clause as follows:</span></span>  
  
    1.  <span data-ttu-id="f16ae-140">在 If 子句窗格中的域列表中，选择在复合域中包括的单一域之一以便作为 If 子句的对象。</span><span class="sxs-lookup"><span data-stu-id="f16ae-140">In the domain list in the If clause pane, select one of the single domains included in the composite domain to be the subject of the If clause.</span></span> <span data-ttu-id="f16ae-141">您可以选择复合域中的任何单一域。</span><span class="sxs-lookup"><span data-stu-id="f16ae-141">You can select any single domain in the composite domain.</span></span>  
  
    2.  <span data-ttu-id="f16ae-142">从下拉列表中选择某个条件作为子句的第一个条件。</span><span class="sxs-lookup"><span data-stu-id="f16ae-142">Select a condition from the drop-down list for the first condition of the clause.</span></span>  
  
    3.  <span data-ttu-id="f16ae-143">如果该条件需要值，则在文本框中输入与该条件相关联的值。</span><span class="sxs-lookup"><span data-stu-id="f16ae-143">If the condition requires a value, enter the value in the text box associated with the condition.</span></span>  
  
    4.  <span data-ttu-id="f16ae-144">如果 If 子句要求其他条件，则单击 **“向所选子句添加新的条件”**。</span><span class="sxs-lookup"><span data-stu-id="f16ae-144">If the If clause requires another condition, click **Adds a new condition to the selected clause**.</span></span> <span data-ttu-id="f16ae-145">选择操作符和条件，并且根据需要为该条件输入值。</span><span class="sxs-lookup"><span data-stu-id="f16ae-145">Select the operator, select a condition, and enter a value for the condition, if necessary.</span></span>  
  
    5.  <span data-ttu-id="f16ae-146">若要更改这些条件的顺序，请通过单击其左侧选择一个条件，再单击向上或向下箭头。</span><span class="sxs-lookup"><span data-stu-id="f16ae-146">To change the order of the conditions, select a condition by clicking to its left, and then click the up or down arrow.</span></span>  
  
    6.  <span data-ttu-id="f16ae-147">若要隐藏条件，请单击域名左侧的减号。</span><span class="sxs-lookup"><span data-stu-id="f16ae-147">To hide the conditions, click the minus sign to the left of the domain name.</span></span> <span data-ttu-id="f16ae-148">单击加号可显示条件。</span><span class="sxs-lookup"><span data-stu-id="f16ae-148">Click the plus ign to display the conditions.</span></span>  
  
8.  <span data-ttu-id="f16ae-149">在 Then 子句窗格的域列表中通过选择并非 If 子句的对象的单一域，创建 Then 子句。</span><span class="sxs-lookup"><span data-stu-id="f16ae-149">Create the Then clause by selecting a single domain, other than the subject of the If clause, in the domain list in the Then clause pane.</span></span> <span data-ttu-id="f16ae-150">然后，使用与生成 If 子句相同的步骤生成 Then 子句。</span><span class="sxs-lookup"><span data-stu-id="f16ae-150">Then build the Then clause using the same steps that you did in building the If clause.</span></span>  
  
9. <span data-ttu-id="f16ae-151">继续执行下面的测试过程。</span><span class="sxs-lookup"><span data-stu-id="f16ae-151">Proceed to the testing procedure below.</span></span>  
  
##  <a name="test-cross-domain-rules"></a><a name="Test"></a> <span data-ttu-id="f16ae-152">测试跨域规则</span><span class="sxs-lookup"><span data-stu-id="f16ae-152">Test Cross-Domain Rules</span></span>  
  
1.  <span data-ttu-id="f16ae-153">按如下所示测试跨域规则：</span><span class="sxs-lookup"><span data-stu-id="f16ae-153">Test the cross-domain rule as follows:</span></span>  
  
    1.  <span data-ttu-id="f16ae-154">单击复合域窗格右上角中的 **“对测试数据运行所选域规则”** 图标。</span><span class="sxs-lookup"><span data-stu-id="f16ae-154">Click the **Run the selected domain rule on test data to** icon in the upper right-hand corner of the composite domain pane.</span></span>  
  
    2.  <span data-ttu-id="f16ae-155">在 **“测试域规则”** 对话框中，单击 **“为域规则添加新的测试字词”** 图标。</span><span class="sxs-lookup"><span data-stu-id="f16ae-155">In the **Test Domain Rule** dialog box, click the **Adds a New Testing Term for the Domain Rule** icon.</span></span>  
  
    3.  <span data-ttu-id="f16ae-156">为与 If 子句相关联的单一域以及与 Then 子句相关联的单一域输入测试值。</span><span class="sxs-lookup"><span data-stu-id="f16ae-156">Enter test values for the single domain associated with the If clause and the single domain associated with the Then clause.</span></span> <span data-ttu-id="f16ae-157">在 If 子句中输入的测试值必须满足该子句的条件，否则，将在 **“有效性”** 列中输入一个问号，指示跨域规则不应用于测试数据。</span><span class="sxs-lookup"><span data-stu-id="f16ae-157">The test values entered in the If clause must meet the conditions for that clause, or a question mark will be entered in the **Validity** column indicating that the cross-domain rule does not apply to the test data.</span></span>  
  
    4.  <span data-ttu-id="f16ae-158">再次单击 **“为域规则添加新的测试字词”** 图标以便添加另一组测试值。</span><span class="sxs-lookup"><span data-stu-id="f16ae-158">Click the **Adds a new testing term for the domain rule** icon again to add another set of test values.</span></span>  
  
    5.  <span data-ttu-id="f16ae-159">单击 "对**所有字词测试域规则**" 图标。</span><span class="sxs-lookup"><span data-stu-id="f16ae-159">Click the **Test the Domain Rule on All the Terms** icon.</span></span> <span data-ttu-id="f16ae-160">如果一组测试值有效，则 DQS 将在 **“有效性”** 列中为该行输入一个复选标记。</span><span class="sxs-lookup"><span data-stu-id="f16ae-160">If a set of test values is valid, DQS will enter a check in the **Validity** column for the row.</span></span> <span data-ttu-id="f16ae-161">如果该组测试值无效，则 DQS 将在“有效性”列中为该行输入一个内含惊叹号的三角形。</span><span class="sxs-lookup"><span data-stu-id="f16ae-161">If the set of test values is not valid, DQS will enter a triangle with an exclamation point in the Validity column for the row.</span></span>  
  
    6.  <span data-ttu-id="f16ae-162">完成测试后，在 **“测试复合域规则”** 对话框中单击 **“关闭”** 。</span><span class="sxs-lookup"><span data-stu-id="f16ae-162">After your testing is complete, click **Close** in the **Test Composite Domain Rule** dialog box.</span></span>  
  
2.  <span data-ttu-id="f16ae-163">在完成了您的跨域规则后，单击 **“完成”** 以完成域管理活动，如 [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f16ae-163">When you have completed your cross-domain rules, click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-cross-domain-rule"></a><a name="FollowUp"></a> <span data-ttu-id="f16ae-164">跟进：创建跨域规则后</span><span class="sxs-lookup"><span data-stu-id="f16ae-164">Follow Up: After Creating a Cross-Domain Rule</span></span>  
 <span data-ttu-id="f16ae-165">在创建跨域规则后，您可以对域执行其他域管理任务，可以执行知识发现以便向域添加知识，或者可以向域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="f16ae-165">After you create a cross-down rule, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="f16ae-166">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="f16ae-166">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
