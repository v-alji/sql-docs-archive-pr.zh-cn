---
title: 任务4：管理和查看结果 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 34fc2a7821fc275a0a0787f703d61a74ea3ee000
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689172"
---
# <a name="task-4-manaing-and-viewing-results"></a><span data-ttu-id="f559e-102">任务 4：管理和查看报表</span><span class="sxs-lookup"><span data-stu-id="f559e-102">Task 4: Manaing and Viewing Results</span></span>
  <span data-ttu-id="f559e-103">在该任务中，您查看计算机辅助清理的结果，还对供应商数据执行交互式清理。</span><span class="sxs-lookup"><span data-stu-id="f559e-103">In this task, you review the results of computer-assisted cleansing and also perform interactive cleansing on the supplier data.</span></span> <span data-ttu-id="f559e-104">有关更多详细信息，请参阅[交互式清理阶段](https://msdn.microsoft.com/library/hh213061.aspx#Interactive)。</span><span class="sxs-lookup"><span data-stu-id="f559e-104">See [Interactive Cleansing Stage](https://msdn.microsoft.com/library/hh213061.aspx#Interactive) for more details.</span></span>  
  
1.  <span data-ttu-id="f559e-105">从域列表中选择 "**联系人电子邮件**域"。</span><span class="sxs-lookup"><span data-stu-id="f559e-105">Select **Contact Email** domain from the list of domains.</span></span>  
  
2.  <span data-ttu-id="f559e-106">切换到右窗格中的 "**无效**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-106">Switch to the **Invalid** tab in the right pane.</span></span> <span data-ttu-id="f559e-107">请注意，末尾缺少字符 "" 的两个电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f559e-107">Notice that two email addresses that were missing character 's' at the end.</span></span> <span data-ttu-id="f559e-108">通过域规则发现的这两封电子邮件都无效，要求所有电子邮件地址以\*\* \@ adventure-works.com\*\* (的 ") 。</span><span class="sxs-lookup"><span data-stu-id="f559e-108">These two emails that were found to be invalid by the domain rule that requires all email addresses to end with **\@adventure-works.com** (with 's').</span></span> <span data-ttu-id="f559e-109">在清理时，DQS 使用此域规则来确定电子邮件是否有效。</span><span class="sxs-lookup"><span data-stu-id="f559e-109">DQS uses the domain rule while cleansing to determine whether an email is a valid one or not.</span></span> <span data-ttu-id="f559e-110">此选项卡显示在知识库中被标记为无效的域值或不符合域规则要求的值。</span><span class="sxs-lookup"><span data-stu-id="f559e-110">This tab displays the domain values that were either marked as invalid in the knowledge base or failed a domain rule.</span></span> <span data-ttu-id="f559e-111">在这种情况下，这些值不符合域规则的要求（电子邮件验证）。</span><span class="sxs-lookup"><span data-stu-id="f559e-111">In this case, these values failed the domain rule (Email Validation).</span></span>  
  
3.  <span data-ttu-id="f559e-112">在 "**更正为**" 列中，键入以\*\* \@ adventure-works.com\*\* (的 ") 的正确电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f559e-112">In the **Correct To** column, type the right email address that end with **\@adventure-works.com** (with 's').</span></span>  
  
     <span data-ttu-id="f559e-113">![基于电子邮件验证规则的更正](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "基于电子邮件验证规则的更正")</span><span class="sxs-lookup"><span data-stu-id="f559e-113">![Corrections from Email Validation Rule](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Corrections from Email Validation Rule")</span></span>  
  
4.  <span data-ttu-id="f559e-114">单击 "**批准**" 以同时批准两个更改。</span><span class="sxs-lookup"><span data-stu-id="f559e-114">Click **Approve** for both the records to approve both the changes.</span></span> <span data-ttu-id="f559e-115">批准后，记录将移到 "已**更正**" 选项卡。您可以使用 "**批准所有字词**" 工具栏按钮一次性批准所有更改，而不是单独批准每个项。</span><span class="sxs-lookup"><span data-stu-id="f559e-115">When you approve, the records move to the **Corrected** tab. Instead of approving each item separately, you can approve all the changes at once using the **Approve all terms** toolbar button.</span></span>  
  
5.  <span data-ttu-id="f559e-116">切换到右窗格中的 "**新建**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-116">Switch to the **New** tab in the right pane.</span></span> <span data-ttu-id="f559e-117">此选项卡上的值是 DQS 在知识库中尚未具有足够的信息来确定其是否正确的值。</span><span class="sxs-lookup"><span data-stu-id="f559e-117">The values on this tab are the values for which DQS does not have enough information in the knowledge base yet to determine whether the values are correct.</span></span> <span data-ttu-id="f559e-118">因此，它无法更改域值，也无法建议对域值所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f559e-118">Therefore, it cannot change or suggest changes to the domain values.</span></span>  
  
6.  <span data-ttu-id="f559e-119">查看值以确认所有电子邮件都以\*\* \@ adventure-works.com**结尾，并单击工具栏上的 "**批准所有字词\*\*"。</span><span class="sxs-lookup"><span data-stu-id="f559e-119">Review the values to confirm that all the emails end with **\@adventure-works.com** and click **Approve all terms** on the toolbar.</span></span> <span data-ttu-id="f559e-120">此选项卡中的已批准值将移到 "**正确**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-120">The approved values from this tab move to the **Correct** tab.</span></span>  
  
7.  <span data-ttu-id="f559e-121">从域列表中选择 "**国家/地区**" 域。</span><span class="sxs-lookup"><span data-stu-id="f559e-121">Select the **Country** domain from the list of domains.</span></span>  
  
8.  <span data-ttu-id="f559e-122">切换到右窗格中的 "已**更正**" 选项卡，请注意，在结束时，会自动将**美国**数值更正为**美国**。</span><span class="sxs-lookup"><span data-stu-id="f559e-122">Switch to the **Corrected** tab in the right pane and notice that **United State** value is automatically corrected to the **United States** with 's' at the end.</span></span> <span data-ttu-id="f559e-123">此规则不是你为**Country**域定义的规则，但是 DQS 的**83%** 确信正确的值**美国**。</span><span class="sxs-lookup"><span data-stu-id="f559e-123">This rule is not a rule you defined for the **Country** domain, but DQS is **83%** confident that the correct value is **United States**.</span></span> <span data-ttu-id="f559e-124">对于所有**更正**的项，将自动选择 "**批准**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f559e-124">The **Approve** button is automatically selected for all the **Corrected** items.</span></span> <span data-ttu-id="f559e-125">您可以覆盖此行为并拒绝更改。</span><span class="sxs-lookup"><span data-stu-id="f559e-125">You can override this behavior and reject a change.</span></span>  
  
9. <span data-ttu-id="f559e-126">请注意，**美国**更正为 "**美国**"，因为它们是同义词，**美国**是前导 (首选) 值。</span><span class="sxs-lookup"><span data-stu-id="f559e-126">Notice that **USA** is corrected to **United States** because they are synonyms and **United States** is the leading (preferred) value.</span></span>  
  
     <span data-ttu-id="f559e-127">![基于同义词的更正](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "基于同义词的更正")</span><span class="sxs-lookup"><span data-stu-id="f559e-127">![Corrections based on Synonyms](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Corrections based on Synonyms")</span></span>  
  
10. <span data-ttu-id="f559e-128">请注意，已为这些更正后的值选择了 "**批准**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f559e-128">Notice that the **Approve** button is already selected for these corrected values.</span></span> <span data-ttu-id="f559e-129">此行为对于更正的值是默认行为。</span><span class="sxs-lookup"><span data-stu-id="f559e-129">This behavior is the default for the corrected values.</span></span> <span data-ttu-id="f559e-130">你可以拒绝更改，当你执行此操作时，该值将移到 "**无效**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-130">You can reject a change and when you do so, the value moves to the **Invalid** tab.</span></span>  
  
11. <span data-ttu-id="f559e-131">从域列表中选择 "**供应商名称**"。</span><span class="sxs-lookup"><span data-stu-id="f559e-131">Select **Supplier Name** from the list of domains.</span></span>  
  
12. <span data-ttu-id="f559e-132">切换到右窗格中的 "已**更正**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-132">Switch to the **Corrected** tab in the right pane.</span></span>  
  
     <span data-ttu-id="f559e-133">![已更正的供应商名称](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "已更正的供应商名称")</span><span class="sxs-lookup"><span data-stu-id="f559e-133">![Corrected Supplier Names](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "Corrected Supplier Names")</span></span>  
  
    1.  <span data-ttu-id="f559e-134">请注意， **a. Datum Corp.** 已更正为**Datum Corporation** ，**原因**设置为 "**基于字词的关系"。A. Datum Corporation**是 DQS 的已知域值，因为它是在知识发现过程中发现的。</span><span class="sxs-lookup"><span data-stu-id="f559e-134">Notice that **A. Datum Corp.** is corrected to **A. Datum Corporation** and the **Reason** is set to **Term based relation. A. Datum Corporation** is a known domain value to DQS because it was discovered during the knowledge discovery process.</span></span> <span data-ttu-id="f559e-135">因此，DQS 对此更正的**100%** 。</span><span class="sxs-lookup"><span data-stu-id="f559e-135">Therefore, DQS is **100% confident** about this correction.</span></span>  
  
    2.  <span data-ttu-id="f559e-136">请注意 **，Lazy Country Storex**已更正为**lazy country Store**，**置信度**设置为**100%**，**原因**设置为 "**域值**"。</span><span class="sxs-lookup"><span data-stu-id="f559e-136">Notice that **Lazy Country Storex** is corrected to **Lazy Country Store**, **Confidence Level** is set to **100%**, and the **Reason** is set to **Domain Value**.</span></span> <span data-ttu-id="f559e-137">在知识发现过程中，您将**懒惰的国家/地区 Storex**设置为 "**懒惰国家商店**" 的错误作为**更正**，因此 DQS 对于进行此更正是**100%** 。</span><span class="sxs-lookup"><span data-stu-id="f559e-137">During the knowledge discovery process, you set **Lazy Country Storex** as an error with **Lazy Country Store** as the **correction**, so DQS is **100% confident** about making this correction.</span></span>  
  
    3.  <span data-ttu-id="f559e-138">DQS 并不熟悉列表中的其他值，但使用**拼写检查器**找到这些值的更正，并提出适当的更正建议。</span><span class="sxs-lookup"><span data-stu-id="f559e-138">DQS is not familiar with the other values in the list, but it found the corrections for these values using the **Spell Checker** and proposes the appropriate corrections.</span></span> <span data-ttu-id="f559e-139">DQS 并**不 100%** 相信这些更正，但置信度高于80%，这是进行更正的阈值级别，因此 DQS 提出了更正建议。</span><span class="sxs-lookup"><span data-stu-id="f559e-139">DQS is **not 100%** confident about these corrections, but the confidence level is above 80%, which is the threshold level for making corrections, so DQS proposes the corrections.</span></span>  
  
13. <span data-ttu-id="f559e-140">请注意，会自动为所有值启用**批准**。</span><span class="sxs-lookup"><span data-stu-id="f559e-140">Notice that the **Approve** is automatically enabled for all the values.</span></span> <span data-ttu-id="f559e-141">您可以相应地覆盖更正后的值或拒绝更改。</span><span class="sxs-lookup"><span data-stu-id="f559e-141">You can override the corrected value or reject the change as appropriate.</span></span> <span data-ttu-id="f559e-142">默认情况下，为 "已**更正**" 选项卡上的所有值选择 "**批准**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f559e-142">By default the **Approve** button is selected for all the values on the **Corrected** tab.</span></span>  
  
14. <span data-ttu-id="f559e-143">切换到**新**选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-143">Switch to the **New** tab.</span></span>  
  
15. <span data-ttu-id="f559e-144">请注意， **Corp.** 更正为 **"公司"，** 并将 "**合作**" 更正为 "**公司**"，并将 " **inc.** " 更正为 "已**合并**"。</span><span class="sxs-lookup"><span data-stu-id="f559e-144">Notice that **Corp.** is corrected to **Corporation**, **Co.** is corrected to **Company**, and **Inc.** is corrected to **Incorporated**.</span></span> <span data-ttu-id="f559e-145">例如，**合并 inc.** 进行了合并，以**合并合并**和**合并共同。** 已更正为**合并的公司**和**Frabrikam Corp** 。已更正为**Fabrikam Corporation**。</span><span class="sxs-lookup"><span data-stu-id="f559e-145">For example, **Consolidate Inc.** is corrected to **Consolidate Incorporated** and **Consolidated Co.** is corrected to **Consolidated Company**, and **Frabrikam Corp.** is corrected to **Fabrikam Corporation**.</span></span>  <span data-ttu-id="f559e-146">您可以看到，这是**基于字词的关系**。</span><span class="sxs-lookup"><span data-stu-id="f559e-146">You can see that **term-based relation** is mentioned as the reason.</span></span> <span data-ttu-id="f559e-147">可以使用您在域管理活动中定义的基于字词的关系来针对这些更改提出建议。</span><span class="sxs-lookup"><span data-stu-id="f559e-147">These changes are proposed by using the term-based relations you defined during the domain management activity.</span></span> <span data-ttu-id="f559e-148">您可以在此处手动更改**正确**的值。</span><span class="sxs-lookup"><span data-stu-id="f559e-148">You can change the **Correct To** values manually here.</span></span>  
  
16. <span data-ttu-id="f559e-149">滚动列表以查看**Hunxgry Coyote 存储区**，并显示红色波浪线。</span><span class="sxs-lookup"><span data-stu-id="f559e-149">Scroll the list to see **Hunxgry Coyote Store** with a red squiggly line.</span></span> <span data-ttu-id="f559e-150">右键单击该应用程序，然后单击 " **Hungry Coyote Store** (不带 ' x ' ) "。</span><span class="sxs-lookup"><span data-stu-id="f559e-150">Right-click on it and click **Hungy Coyote Store** (with no 'x').</span></span> <span data-ttu-id="f559e-151">"**更正为**" 列应该自动填充了大量的**Coyote 存储**。</span><span class="sxs-lookup"><span data-stu-id="f559e-151">The **Correct To** column should be automatically populated with **Hungry Coyote Store**.</span></span> <span data-ttu-id="f559e-152">您也可以在“更正为”列中手动键入值。</span><span class="sxs-lookup"><span data-stu-id="f559e-152">You can also manually type a value in the Correct To column.</span></span>  
  
17. <span data-ttu-id="f559e-153">单击工具栏中的 "**批准所有字词**"。</span><span class="sxs-lookup"><span data-stu-id="f559e-153">Click **Approve all terms** from the toolbar.</span></span> <span data-ttu-id="f559e-154">指定了 "**正确到**" 值的域值将移到 "已**更正**" 选项卡，并且没有关联的**正确**值的新值将移到 "**正确**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-154">The domain values with the **Correct To** value specified move to the **Corrected** tab and the new values with no associated **Correct To** values move to the **Correct** tab.</span></span>  
  
18. <span data-ttu-id="f559e-155">从 "域" 列表中选择 "**地址验证**" 复合域。</span><span class="sxs-lookup"><span data-stu-id="f559e-155">Select the **Address Validation** composite domain from the domain list.</span></span>  
  
19. <span data-ttu-id="f559e-156">在右侧窗格中，切换到 "**正确**" 选项卡。你应会看到**Azure Marketplace**上的**Melissa 数据地址检查**DQS 服务发现正确的地址。</span><span class="sxs-lookup"><span data-stu-id="f559e-156">In the right pane, switch to the **Correct** tab. You should see the addresses that are found to be correct by the **Melissa Data - Address Check** DQS service on the **Azure Marketplace**.</span></span>  
  
20. <span data-ttu-id="f559e-157">切换到 "已**更正**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f559e-157">Switch to the **Corrected** tab.</span></span>  
  
21. <span data-ttu-id="f559e-158">请注意，将**城市**为**洛杉矶**的记录的**状态**现在设置为 " **CA** "。</span><span class="sxs-lookup"><span data-stu-id="f559e-158">Notice that **State** for the record that has **City** as **Los Angeles** is set to **CA** now.</span></span> <span data-ttu-id="f559e-159">请注意，"**原因**" 字段为 **"城市-省/市/自治区规则" 更正**。</span><span class="sxs-lookup"><span data-stu-id="f559e-159">Notice in the **Reason** field is that **Corrected by Rule 'City-State Rule'**.</span></span>  
  
     <span data-ttu-id="f559e-160">![城市-州/省规则更正](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "城市-州/省规则更正")</span><span class="sxs-lookup"><span data-stu-id="f559e-160">![City-State Rule Correction](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "City-State Rule Correction")</span></span>  
  
22. <span data-ttu-id="f559e-161">请注意，已为列表中的此项选择了 "**批准**" 单选按钮。</span><span class="sxs-lookup"><span data-stu-id="f559e-161">Notice that the **Approve** radio button is already selected for this item in the list.</span></span> <span data-ttu-id="f559e-162">这是 "已**更正**" 选项卡上的项的默认行为。</span><span class="sxs-lookup"><span data-stu-id="f559e-162">This is the default behavior for items on the **Corrected** tab.</span></span>  
  
23. <span data-ttu-id="f559e-163">切换到 "**建议**" 选项卡。查看**Melissa Data-Address 检查**服务建议的更改。</span><span class="sxs-lookup"><span data-stu-id="f559e-163">Switch to the **Suggested** tab. Review the changes suggested by the **Melissa Data - Address Check** service.</span></span>  
  
24. <span data-ttu-id="f559e-164">单击工具栏按钮上的 "**批准所有字词**"，并在**确认**消息框中单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="f559e-164">**Click Approve all terms** on the toolbar button and click **OK** on the **Confirmation** message box.</span></span>  
  
     <span data-ttu-id="f559e-165">![“批准所有字词”工具栏按钮](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "“批准所有字词”工具栏按钮")</span><span class="sxs-lookup"><span data-stu-id="f559e-165">![Approve All Terms Toolbar Button](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "Approve All Terms Toolbar Button")</span></span>  
  
25. <span data-ttu-id="f559e-166">单击 "**下一步**" 切换到 "**导出**" 页。</span><span class="sxs-lookup"><span data-stu-id="f559e-166">Click **Next** to switch to the **Export** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f559e-167">下一步</span><span class="sxs-lookup"><span data-stu-id="f559e-167">Next Step</span></span>  
 [<span data-ttu-id="f559e-168">任务 5：将清理结果导出到 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="f559e-168">Task 5: Exporting Cleansing Results to an Excel File</span></span>](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
