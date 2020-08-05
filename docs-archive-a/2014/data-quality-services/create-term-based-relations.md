---
title: 创建基于字词的关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.kbtermsbased.f1
ms.assetid: 66db9277-d892-4dae-8a82-060fd3ba6949
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6b7424b962679af766efc10278def8947fc07b51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579077"
---
# <a name="create-term-based-relations"></a><span data-ttu-id="707cb-102">创建基于字词的关系</span><span class="sxs-lookup"><span data-stu-id="707cb-102">Create Term-Based Relations</span></span>
  <span data-ttu-id="707cb-103">本主题描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中为域创建基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="707cb-103">This topic describes how to create term-based relations for a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="707cb-104">通过基于字词的关系 (TBR)，您可以对域中作为值的一部分的字词进行更正。</span><span class="sxs-lookup"><span data-stu-id="707cb-104">A term-based relation (TBR) enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="707cb-105">基于字词的关系使完全相同的多个值（只有其公共部分的拼写除外）可被视为相同的同义词。</span><span class="sxs-lookup"><span data-stu-id="707cb-105">It enables multiple values that are identical except for the spelling of a common part of them to be considered identical synonyms.</span></span> <span data-ttu-id="707cb-106">例如，可以设置一个基于字词的关系，该关系可将字词“Inc.”</span><span class="sxs-lookup"><span data-stu-id="707cb-106">For example, you can set up a term-based relation that changes the term "Inc."</span></span> <span data-ttu-id="707cb-107">更改为“Incorporated”。</span><span class="sxs-lookup"><span data-stu-id="707cb-107">to "Incorporated".</span></span> <span data-ttu-id="707cb-108">字词“Inc.”</span><span class="sxs-lookup"><span data-stu-id="707cb-108">The term "Inc."</span></span> <span data-ttu-id="707cb-109">将在其每次出现在域中时发生更改。</span><span class="sxs-lookup"><span data-stu-id="707cb-109">will be changed each time it occurs in the domain.</span></span> <span data-ttu-id="707cb-110">“Contoso, Inc.”的实例</span><span class="sxs-lookup"><span data-stu-id="707cb-110">Instances of "Contoso, Inc."</span></span> <span data-ttu-id="707cb-111">将更改为“Contoso, Incorporated”，并且这两个值将被视为精确同义词。</span><span class="sxs-lookup"><span data-stu-id="707cb-111">will be changed "Contoso, Incorporated", and the two values will be considered exact synonyms.</span></span>  
  
 <span data-ttu-id="707cb-112">若要使用基于字词的关系，可以生成一个“值/更正为”对的列表，例如“Inc.”</span><span class="sxs-lookup"><span data-stu-id="707cb-112">To use term-based relations, you build a list of Value/Correct To pairs, such as "Inc."</span></span> <span data-ttu-id="707cb-113">和“Incorporated”或“Senior”和“Sr.”。</span><span class="sxs-lookup"><span data-stu-id="707cb-113">and "Incorporated", or "Senior" and "Sr.".</span></span> <span data-ttu-id="707cb-114">通过使用基于字词的关系，您可以在整个域中更改某一字词，而不必手动将单独的域值设置为同义词。</span><span class="sxs-lookup"><span data-stu-id="707cb-114">Using a term-based relation enables you to change a term throughout the domain without manually setting individual domain values as synonyms.</span></span> <span data-ttu-id="707cb-115">您也可以指定更正某个值，即使知识发现以前尚未发现该值。</span><span class="sxs-lookup"><span data-stu-id="707cb-115">You can specify that a value be corrected even if knowledge discovery has not discovered that value previously.</span></span> <span data-ttu-id="707cb-116">如果基于字词的关系转换导致两个值完全相同，则 DQS 将在它们之间创建一个同义词关系（在知识发现中）、更正关系（在数据更正中）或精确匹配（在匹配中）。</span><span class="sxs-lookup"><span data-stu-id="707cb-116">If a term-based relation transformation causes two values to be identical, then DQS will create a synonym relationship between them (in knowledge discovery), a correction relationship between them (in data correction), or an exact match (in matching).</span></span>  
  
 <span data-ttu-id="707cb-117">基于字词的关系转换和符号转换（其中，特殊字符将被空格或 null 替换）都在分析前的预处理阶段中完成。</span><span class="sxs-lookup"><span data-stu-id="707cb-117">Term-based relations transformation and symbols transformation (in which special characters are replaced by a space or a null) are both done in a pre-processing stage before analysis.</span></span> <span data-ttu-id="707cb-118">如果请求复合域分析，将在这两个转换前执行分析，因为分隔符分析要求符号。</span><span class="sxs-lookup"><span data-stu-id="707cb-118">If composite domain parsing is requested, it will be performed before the two transformations, because delimiter parsing requires symbols.</span></span> <span data-ttu-id="707cb-119">其他操作（例如域规则和域值更改）将会在转换后执行。</span><span class="sxs-lookup"><span data-stu-id="707cb-119">Other operations, such as domain rules and domain value changes, will be performed after the transformations.</span></span> <span data-ttu-id="707cb-120">对于匹配，在匹配活动前，将基于字词的关系应用于源数据，而与您是否运行清理无关。</span><span class="sxs-lookup"><span data-stu-id="707cb-120">For matching, term-based relations are applied on the source data before the matching activity regardless of whether you run cleansing.</span></span>  
  
 <span data-ttu-id="707cb-121">**基于字词的关系和域管理**</span><span class="sxs-lookup"><span data-stu-id="707cb-121">**Term-Based Relations and Domain Management**</span></span>  
  
 <span data-ttu-id="707cb-122">在域管理中应用基于字词的关系时，DQS 将应用知识发现、清理或匹配过程中的更改；但是，DQS 不更改域值本身以便遵从基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="707cb-122">When you apply a term-based relation in domain management, DQS will apply the changes in the knowledge discovery, cleansing, or matching processes; however, DQS does not change the domain value itself to conform to the term-based relation.</span></span> <span data-ttu-id="707cb-123">换句话说，如果在 **“域管理”** 页的 **“基于字词的关系”** 选项卡上输入并接受一个基于字词的关系，该更改不会在同一页的 **“域值”** 选项卡中执行。</span><span class="sxs-lookup"><span data-stu-id="707cb-123">In other words, if you enter and accept a term-based relation in the **Term-Based Relations** tab of the **Domain Management** page, the change will not be made in the **Domain Values** tab of the same page.</span></span> <span data-ttu-id="707cb-124">这使您可以随后更改 TBR。</span><span class="sxs-lookup"><span data-stu-id="707cb-124">This enables you to change the TBR subsequently.</span></span>  
  
 <span data-ttu-id="707cb-125">**基于字词的关系和数据清理**</span><span class="sxs-lookup"><span data-stu-id="707cb-125">**Term-Based Relations and Data Cleaning**</span></span>  
  
 <span data-ttu-id="707cb-126">在域中应用基于字词的关系并运行数据清理过程时，DQS 将在清理过程中应用更改，但是这些更改不会应用于知识库中的字词。</span><span class="sxs-lookup"><span data-stu-id="707cb-126">When you apply a term-based relation in a domain and then run the data cleansing process, DQS applies the changes during cleansing, but does not apply the changes to terms in the knowledge base.</span></span>  
  
-   <span data-ttu-id="707cb-127">如果基于字词的关系所更改的值在域中但不是同义词，它将显示在 **“更正为”** 列（位于 **“管理和查看结果”** 页的 **“已更正”** 选项卡下）中，且将“原因”设置为“基于字词的关系”。</span><span class="sxs-lookup"><span data-stu-id="707cb-127">If a value as changed by a term-based relation is in the domain, but is not a synonym, will be shown in the **Correct to** column under the **Corrected** tab of the **Manage and View results** page, with the Reason set to Term based relation.</span></span>  
  
-   <span data-ttu-id="707cb-128">如果基于字词的关系所更改的值不在域中且 DQS 找到了匹配值，则该值将更改为它且显示在“已更正”选项卡或“建议的”选项卡下（具体取决于置信度级别）。</span><span class="sxs-lookup"><span data-stu-id="707cb-128">If a value as changed by a term-based relation is not in the domain, and DQS finds a matching value, the value will be corrected to it and will appear under the Corrected tab or the Suggested tab, based on the confidence level.</span></span> <span data-ttu-id="707cb-129">如果找不到匹配值，该值将显示在“新建”下并带一个 TBR 更正项。</span><span class="sxs-lookup"><span data-stu-id="707cb-129">If no match is found, the value will appear under New with a TBR correction.</span></span> <span data-ttu-id="707cb-130">这么做是因为即使您更正了 TBR，也不表示该值是正确的。</span><span class="sxs-lookup"><span data-stu-id="707cb-130">This is done because even if you correct the TBR, it does not mean that the value is correct.</span></span>  
  
-   <span data-ttu-id="707cb-131">如果基于字词的关系所更改的值在域中但值错误/无效且已有更正项，则该值将显示在“已更正”选项卡下且具有更正项和原因“域值”。</span><span class="sxs-lookup"><span data-stu-id="707cb-131">If a value as changed by a term-based relation is in the domain, but the value is Error/Invalid with existing correction, the value will appear under the Corrected tab with its correction and the reason Domain Value.</span></span>  
  
-   <span data-ttu-id="707cb-132">如果基于字词的关系所更改的值在域中但值错误/无效且无更正项，则该值将显示在“无效”选项卡下且具有原因“域值”。</span><span class="sxs-lookup"><span data-stu-id="707cb-132">If a value as changed by a term-based relation is in the domain, but the value is Error/Invalid with no correction, the value will appear under the Invalid tab with the reason Domain Value.</span></span>  
  
 <span data-ttu-id="707cb-133">**基于字词的关系和知识发现**</span><span class="sxs-lookup"><span data-stu-id="707cb-133">**Term-Based Relations and Knowledge Discovery**</span></span>  
  
 <span data-ttu-id="707cb-134">当您应用基于字词的关系，然后运行知识发现过程时，符合 TBR 的所有值将保持原样并被标识为正确值。</span><span class="sxs-lookup"><span data-stu-id="707cb-134">When you apply a term-based relation and then run the knowledge discovery process, any value that conforms to the TBR will remain as is and will be identified as a correct value.</span></span> <span data-ttu-id="707cb-135">TBR 所更改的所有值将被导入为正确值并被标识为符合 TBR 的值的同义词。</span><span class="sxs-lookup"><span data-stu-id="707cb-135">Any value that is changed by a TBR will be imported as a correct value, and will be identified as a synonym to a value that conforms to the TBR.</span></span>  
  
 <span data-ttu-id="707cb-136">**基于字词的关系和将清理值导入域**</span><span class="sxs-lookup"><span data-stu-id="707cb-136">**Term-Based Relations and Import Cleansing Values into a Domain**</span></span>  
  
 <span data-ttu-id="707cb-137">如果您将在清理过程中收集的数据质量知识导入到域中，TBR 所更改的值将作为正确值导入。</span><span class="sxs-lookup"><span data-stu-id="707cb-137">If you import data quality knowledge gathered during the cleansing process into a domain, a value that is changed by a TBR will be imported as a correct value.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="707cb-138">开始之前</span><span class="sxs-lookup"><span data-stu-id="707cb-138">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="707cb-139">先决条件</span><span class="sxs-lookup"><span data-stu-id="707cb-139">Prerequisites</span></span>  
 <span data-ttu-id="707cb-140">若要创建基于字词的关系，您必须具有在域管理活动中打开的知识库。</span><span class="sxs-lookup"><span data-stu-id="707cb-140">To create term-based relations, you must have a domain opened in the Domain Management activity.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="707cb-141">Security</span><span class="sxs-lookup"><span data-stu-id="707cb-141">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="707cb-142">权限</span><span class="sxs-lookup"><span data-stu-id="707cb-142">Permissions</span></span>  
 <span data-ttu-id="707cb-143">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能创建基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="707cb-143">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create term-based relations.</span></span>  
  
##  <a name="create-term-based-relations"></a><a name="Create"></a><span data-ttu-id="707cb-144">创建基于字词的关系</span><span class="sxs-lookup"><span data-stu-id="707cb-144">Create Term-Based Relations</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="707cb-145">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="707cb-145">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="707cb-146">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的主屏幕中，打开或创建一个知识库。</span><span class="sxs-lookup"><span data-stu-id="707cb-146">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="707cb-147">选择 **“域管理”** 作为活动，然后单击 **“打开”** 或 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="707cb-147">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="707cb-148">有关详细信息，请参阅 [创建知识库](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [打开知识库](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="707cb-148">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="707cb-149">域管理在 Data Quality Service 客户端页面中执行，该页面包含用于单独域管理操作的五个选项卡。</span><span class="sxs-lookup"><span data-stu-id="707cb-149">Domain management is performed in a page of the Data Quality Service client that contains five tabs for separate domain management operations.</span></span> <span data-ttu-id="707cb-150">它不是一个向导驱动的过程；任何管理操作都可以单独执行。</span><span class="sxs-lookup"><span data-stu-id="707cb-150">It is not a wizard-driven process; any management operation can be performed separately.</span></span>  
  
3.  <span data-ttu-id="707cb-151">从 **“域管理”** 页上的 **“域列表”** 中，选择您要为其创建域规则的域，或者创建一个新的域。</span><span class="sxs-lookup"><span data-stu-id="707cb-151">From the **Domain list** on the **Domain Management** page, select the domain that you want to create a domain rule for, or create a new domain.</span></span> <span data-ttu-id="707cb-152">如果您必须创建新域，请参阅 [创建域](../../2014/data-quality-services/create-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="707cb-152">If you have to create a new domain, see [Create a Domain](../../2014/data-quality-services/create-a-domain.md).</span></span>  
  
4.  <span data-ttu-id="707cb-153">单击 **“基于字词的关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="707cb-153">Click the **Term-Based Relations** tab.</span></span>  
  
5.  <span data-ttu-id="707cb-154">按如下所示创建基于字词的关系：</span><span class="sxs-lookup"><span data-stu-id="707cb-154">Create term-based relations as follows:</span></span>  
  
    1.  <span data-ttu-id="707cb-155">单击 **“添加新关系”** 可将行添加到“关系”表。</span><span class="sxs-lookup"><span data-stu-id="707cb-155">Click **Add New Relation** to add a row to the Relations table.</span></span>  
  
    2.  <span data-ttu-id="707cb-156">对于添加的行的 **“值”** 列，输入每次在所选域的值中出现时将要更改的字词。</span><span class="sxs-lookup"><span data-stu-id="707cb-156">To the **Value** column of the added row, enter a term that you want to change each time it occurs in a value in the selected domain.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="707cb-157">如果该字词在域中作为整个值存在，或者已在域中作为更正值存在，系统将会向您显示一个错误消息。</span><span class="sxs-lookup"><span data-stu-id="707cb-157">You will get an error if the term exists as a whole value in the domain, or if it already exists as a correcting value in the domain.</span></span>  
  
    3.  <span data-ttu-id="707cb-158">对于 **“更正为”** 列，输入您要将 **“值”** 列中的字词更改为的字词。</span><span class="sxs-lookup"><span data-stu-id="707cb-158">To the **Correct To** column, enter a term that you want to change the term in the **Value** column to.</span></span>  
  
    4.  <span data-ttu-id="707cb-159">再次单击 **“添加新关系”** 可添加另一个基于字词的关系。</span><span class="sxs-lookup"><span data-stu-id="707cb-159">Click **Add New Relations** again to add another term-based relation.</span></span>  
  
    5.  <span data-ttu-id="707cb-160">单击 **“删除所选关系”** 可从“关系”表中删除一个或多个选定的行。</span><span class="sxs-lookup"><span data-stu-id="707cb-160">Click **Delete Selected Relations** to delete one or more selected rows from the Relations table.</span></span> <span data-ttu-id="707cb-161">通过按下 Ctrl 键并单击未选定的行，可以选择多个行。</span><span class="sxs-lookup"><span data-stu-id="707cb-161">You can select multiple rows by pressing the Ctrl button and clicking an unselected row.</span></span>  
  
    6.  <span data-ttu-id="707cb-162">通过在 **“查找”** 文本框中输入一个或多个数字，可以在“关系”表中查找一个值。</span><span class="sxs-lookup"><span data-stu-id="707cb-162">Find a value in the Relations table by entering one or more digits in the **Find** text box.</span></span> <span data-ttu-id="707cb-163">该字符串的匹配项将会突出显示。</span><span class="sxs-lookup"><span data-stu-id="707cb-163">Matches for the string will be highlighted.</span></span> <span data-ttu-id="707cb-164">使用向上箭头和向下箭头可以移到表中该字符串的不同实例。</span><span class="sxs-lookup"><span data-stu-id="707cb-164">Use the up and down arrows to move to different instances of the string in the table.</span></span>  
  
    7.  <span data-ttu-id="707cb-165">**拼写检查器**：如果 **“值”** 或 **“更正为”** 列中的值有红色的波浪下划线，则表示拼写检查器建议对该值加以更正。</span><span class="sxs-lookup"><span data-stu-id="707cb-165">**Speller**: If a value in the **Value** or **Correct to** column has a wavy red underscore, the Speller is suggesting a correction to the value.</span></span> <span data-ttu-id="707cb-166">右键单击带下划线的值，然后选择由拼写检查器提供的建议值之一。</span><span class="sxs-lookup"><span data-stu-id="707cb-166">Right-click the value with the underscore, and select one of the proposed values by the Speller.</span></span> <span data-ttu-id="707cb-167">或者，您可以单击快捷菜单中的 **“添加”** ，以继续使用原始值。</span><span class="sxs-lookup"><span data-stu-id="707cb-167">Alternately, you can click **Add** in the shortcut menu tp proceed with the original value.</span></span> <span data-ttu-id="707cb-168">有关详细信息，请参阅 [使用 DQS 拼写检查器](../../2014/data-quality-services/use-the-dqs-speller.md) 和 [设置域属性](../../2014/data-quality-services/set-domain-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="707cb-168">For more information, see [Use the DQS Speller](../../2014/data-quality-services/use-the-dqs-speller.md) and [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="707cb-169">若要使用拼写检查器，您或者可以在 **“域属性”** 页中启用它，或者如果已在 **“域属性”** 页中禁用它，则可以在 **“基于字词的关系”** 页中单击 **“启用/禁用拼写检查器”** 图标以便在该页上启用它。</span><span class="sxs-lookup"><span data-stu-id="707cb-169">To use the Speller, you can either enable it in the **Domain Properties** page, or if it is disabled in the **Domain Properties** page, you can click the **Enable/Disable Speller** icon on the **Term-Based Relations** page to enable it on this page.</span></span>  
  
6.  <span data-ttu-id="707cb-170">单击 **“应用更改”** 可将基于字词的关系应用于域。</span><span class="sxs-lookup"><span data-stu-id="707cb-170">Click **Apply Changes** to apply the term-based relations to the domain.</span></span>  
  
7.  <span data-ttu-id="707cb-171">单击 **“完成”** 以完成域管理活动，如 [结束域管理活动](../../2014/data-quality-services/end-the-domain-management-activity.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="707cb-171">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-term-based-relations"></a><a name="FollowUp"></a> <span data-ttu-id="707cb-172">跟进：在创建基于字词的关系后</span><span class="sxs-lookup"><span data-stu-id="707cb-172">Follow Up: After Creating Term-Based Relations</span></span>  
 <span data-ttu-id="707cb-173">在创建基于字词的关系后，您可以对域执行其他域管理任务，可以执行知识发现以便向域添加知识，或者可以向域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="707cb-173">After you create term-based relations, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="707cb-174">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="707cb-174">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
