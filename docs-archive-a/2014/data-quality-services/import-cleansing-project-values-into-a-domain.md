---
title: 将清理项目值导入到域中 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.importprojectvalues.f1
ms.assetid: f23e38e2-39e0-42d7-abd5-34d8fcca5d2a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 38616da5a0a8fb9c8f149d9f55a08b63dee5ff6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689595"
---
# <a name="import-cleansing-project-values-into-a-domain"></a><span data-ttu-id="3ecd5-102">将清理项目值导入到域中</span><span class="sxs-lookup"><span data-stu-id="3ecd5-102">Import Cleansing Project Values into a Domain</span></span>
  <span data-ttu-id="3ecd5-103">在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中，您可以将在清理过程中从数据质量清理项目或包含 DQS 清理组件的集成服务包中收集的数据质量知识，导入到域中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-103">In [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), you can import data quality knowledge gathered during the cleansing process in a data quality cleansing project or an Integration Services package containing the DQS Cleansing component into a domain.</span></span> <span data-ttu-id="3ecd5-104">这样可确保可信知识不丢失，而且可以不断地改进知识库。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-104">This ensures that trusted knowledge is not lost, and that the knowledge base is continually improved.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3ecd5-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="3ecd5-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="3ecd5-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="3ecd5-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="3ecd5-107">若要将清理项目值导入到域中，该域必须已在 Data Quality Client 的清理项目中或包含 DQS 清理组件的集成服务包中使用。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-107">To import cleansing project values into a domain, the domain must have been used in the cleansing project in Data Quality Client or in the Integration Services package containing a DQS Cleansing component.</span></span>  
  
-   <span data-ttu-id="3ecd5-108">Data Quality Client 中的清理项目或包含 DQS 清理组件的集成服务包必须已成功完成。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-108">The cleansing project in Data Quality Client or the Integration Services package containing the DQS Cleansing component must have successfully completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3ecd5-109">Security</span><span class="sxs-lookup"><span data-stu-id="3ecd5-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3ecd5-110">权限</span><span class="sxs-lookup"><span data-stu-id="3ecd5-110">Permissions</span></span>  
 <span data-ttu-id="3ecd5-111">您必须具有 DQS_MAIN 数据库的 dqs_kb_editor 或 dqs_administrator 角色，才能将在清理过程中收集的数据质量知识导入到域中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import data quality knowledge gathered during the cleansing process into a domain.</span></span>  
  
##  <a name="import-cleansing-project-values"></a><a name="Import"></a> <span data-ttu-id="3ecd5-112">导入清理项目值</span><span class="sxs-lookup"><span data-stu-id="3ecd5-112">Import Cleansing Project Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="3ecd5-113">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="3ecd5-114">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在域管理活动中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="3ecd5-115">如果将值添加到某个现有域中，则在域列表中选择该域。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-115">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="3ecd5-116">单击 **“域值”** 选项卡，在图标栏中单击 **“导入值”** 图标，然后单击 **“导入项目值”**。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-116">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import project values**.</span></span> <span data-ttu-id="3ecd5-117">此时将显示 **“导入项目值”** 对话框，其中包含使用该域进行清理的数据质量项目以及集成服务包的列表。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-117">The **Import Project Values** dialog box appears with a list of data quality projects and Integration Services packages that were cleansed using the domain.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ecd5-118"> 如果尚未使用域或其任何链接域创建项目，或者项目没有完成，则 **“导入项目值”** 选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-118">If no project has been created using the domain or any of its linked domains, or the project was not finished, the **Import project values** option will not be available.</span></span>  
  
5.  <span data-ttu-id="3ecd5-119">在 **“导入项目值”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="3ecd5-119">In the **Import Project Values** dialog box:</span></span>  
  
    -   <span data-ttu-id="3ecd5-120">在 **“已导入”** 下拉列表中选择 **“全部”** 以显示所有项目，或选择 **“否”** 仅显示尚未导入值的项目。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-120">Select **All** in the **Imported** drop-down list to display all projects, or **No** to display only projects whose values have not been imported yet.</span></span>  
  
    -   <span data-ttu-id="3ecd5-121">选择要从中导入值的项目。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-121">Select the project that you want to import values from.</span></span>  
  
    -   <span data-ttu-id="3ecd5-122">如果选择 **“从‘新建’选项卡中添加值”** ，则除了 **“正确”** 和 **“已更正”** 选项卡中的值之外，还将导入新建选项卡中的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-122">Select **Add values from New tab** to import values in the new tab, in addition to values in the **Correct** and **Corrected** tabs.</span></span>  
  
    -   <span data-ttu-id="3ecd5-123">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="3ecd5-124">您将返回到 **“域值”** 选项卡；在值成功导入后，将显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-124">You return to the **Domain Values** tab, and a message is displayed on successful import of the values.</span></span> <span data-ttu-id="3ecd5-125">**“值”** 表中将显示已导入的值，因此也是首次进入域中的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-125">Values that have been imported, and so are new to the domain, will be displayed in the **Values** table.</span></span>  
  
7.  <span data-ttu-id="3ecd5-126">取消选择 **“仅显示新内容”** 以显示域中的所有值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-126">Deselect **Show Only New** to display all values that are in the domain.</span></span>  
  
8.  <span data-ttu-id="3ecd5-127">选择 **“正确”**、 **“错误”** 或 **“无效”** 以仅显示具有所选类型的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-127">Select **Correct**, **Error**, or **Invalid** to display only those values of the selected type.</span></span>  
  
9. <span data-ttu-id="3ecd5-128">若要搜索特定字符串，在 **“查找”** 文本框中输入该字符串。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-128">To search for a specific string, enter the string in the **Find** text box.</span></span> <span data-ttu-id="3ecd5-129">单击向上或向下箭头可以逐一查看满足搜索条件的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-129">Click the up or down arrow to step through the values that meet the search criteria.</span></span> <span data-ttu-id="3ecd5-130">这些值将突出显示为黄色。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-130">They will be highlighted in yellow.</span></span>  
  
10. <span data-ttu-id="3ecd5-131">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-131">Click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3ecd5-132"> 有关使用 **“域值”** 选项卡上的值的详细信息，请参阅 [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-132">For more information on working with values in the **Domain Values** tab, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
##  <a name="follow-up-after-importing-project-values-into-a-domain"></a><a name="FollowUp"></a> <span data-ttu-id="3ecd5-133">跟进：将项目值导入到域后</span><span class="sxs-lookup"><span data-stu-id="3ecd5-133">Follow Up: After Importing Project Values into a Domain</span></span>  
 <span data-ttu-id="3ecd5-134">将在清理过程中收集的数据质量知识导入到域中后，您可以对该域和值执行其他域管理任务。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-134">After you import data quality knowledge gathered during the cleansing process into a domain, you can perform other domain management tasks on the domain and the values.</span></span> <span data-ttu-id="3ecd5-135">有关详细信息，请参阅[管理域](../../2014/data-quality-services/managing-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-135">For more information, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
##  <a name="values-that-will-be-imported"></a><a name="Values"></a> <span data-ttu-id="3ecd5-136">要导入的值</span><span class="sxs-lookup"><span data-stu-id="3ecd5-136">Values that Will Be Imported</span></span>  
 <span data-ttu-id="3ecd5-137">下面的值将从项目导入到域中：</span><span class="sxs-lookup"><span data-stu-id="3ecd5-137">The following values will be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="3ecd5-138">仅字符串值导入到域中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-138">Only string values are imported to the domain.</span></span>  
  
-   <span data-ttu-id="3ecd5-139">将只导入 **“清理”** 活动的 **“管理和查看结果”** 页上 **“正确”** 、 **“已更正”** 和 **“新建”** 选项卡上的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-139">Only values from the **Correct**, **Corrected**, and **New** tabs on the **Manage and View results** page of the **Cleansing** activity will be imported.</span></span> <span data-ttu-id="3ecd5-140">如果在 **“导入项目值”** 对话框中选中了 **“从‘新建’选项卡中添加值”** 复选框，将只导入 **“新建”** 选项卡中的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-140">Values from the **New** tab will be imported only if the **Add values from New tab** check box in the **Import Project Values** dialog box has been selected.</span></span>  
  
-   <span data-ttu-id="3ecd5-141">值将作为正确的值或具有更正的错误值进行导入。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-141">Values will be imported as correct or as an error with its correction.</span></span> <span data-ttu-id="3ecd5-142">仅导入具有更正值的错误值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-142">Only an error value with a correction value will be imported.</span></span>  
  
-   <span data-ttu-id="3ecd5-143">更正值将为知识库中不存在的新值或现有的正确值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-143">The correction value will be either a new value that does not exist in the knowledge base or an existing correct value.</span></span>  
  
-   <span data-ttu-id="3ecd5-144">仅将在值级别上（而不是记录级别）执行的更正导入到知识库中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-144">Only corrections performed on the value level, not the record level, will be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="3ecd5-145">如果导入的值与域规则相矛盾，则会创建无效值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-145">Invalid values will be created if the imported value contradicts a domain rule.</span></span>  
  
-   <span data-ttu-id="3ecd5-146">如果您一次导入多个项目中的值，这些值按先后顺序导入。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-146">If you import values from several projects at once, the values are imported in a sequential order.</span></span>  
  
-   <span data-ttu-id="3ecd5-147">域中因基于字词的关系而导致的更正值将作为正确值（不是错误）导入。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-147">A correction made as a result of a term-based relation in a domain is imported as a correct value (not as an error).</span></span>  
  
##  <a name="values-that-will-not-be-imported"></a><a name="ValuesNot"></a> <span data-ttu-id="3ecd5-148">不会导入的值</span><span class="sxs-lookup"><span data-stu-id="3ecd5-148">Values that Will Not Be Imported</span></span>  
 <span data-ttu-id="3ecd5-149">下面的值将不会从项目导入到域中：</span><span class="sxs-lookup"><span data-stu-id="3ecd5-149">The following values will not be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="3ecd5-150">不会导入 **“清理”** 活动的 **“管理和查看结果”** 页上 **“建议”** 和 **“无效”** 选项卡上的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-150">Values from the **Suggested** and **Invalid** tabs on the **Manage and View results** page of the **Cleansing** activity will not be imported.</span></span>  
  
-   <span data-ttu-id="3ecd5-151">如果在清理项目中找到的值与域中的现有值冲突，则跳过在该项目中找到的值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-151">If a value found in the cleansing project contradicts an existing value in the domain, the value found in the project is skipped.</span></span> <span data-ttu-id="3ecd5-152">这将包括清理值与知识库值之间的冲突。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-152">This will include conflicts between cleansing and knowledge base values.</span></span>  
  
-   <span data-ttu-id="3ecd5-153">不会将在记录级别执行的更正导入到知识库中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-153">Corrections performed on the record level will not be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="3ecd5-154">如果要替换的值已被引用数据服务更正或批准为正确的，则不会将该值导入到域中。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-154">No value will be imported to a domain if the value that it would replace was corrected or approved as correct by a reference data service.</span></span>  
  
-   <span data-ttu-id="3ecd5-155">如果某个更正值在知识库中显示为无效或错误的值，则无论是错误值还是更正值都不会被导入。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-155">If a correction value appears in the knowledge base as an invalid or error value, neither the error nor the correction value will be imported.</span></span>  
  
-   <span data-ttu-id="3ecd5-156">如果域作为复合域的一部分且对复合域执行清理，将不会导入任何值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-156">If the domain is part of a composite domain, and the cleansing was performed on the composite domain, no values will be imported.</span></span>  
  
-   <span data-ttu-id="3ecd5-157">仅当知识库处于工作状态且知识库由正在执行导入的用户锁定，才可从项目中导入值。</span><span class="sxs-lookup"><span data-stu-id="3ecd5-157">You can import values from a project only when the knowledge base has a state of in-work and the knowledge base is locked by the user who is importing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecd5-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ecd5-158">See Also</span></span>  
 <span data-ttu-id="3ecd5-159">[数据清理](../../2014/data-quality-services/data-cleansing.md) </span><span class="sxs-lookup"><span data-stu-id="3ecd5-159">[Data Cleansing](../../2014/data-quality-services/data-cleansing.md) </span></span>  
 [<span data-ttu-id="3ecd5-160">DQS 清理转换</span><span class="sxs-lookup"><span data-stu-id="3ecd5-160">DQS Cleansing Transformation</span></span>](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  
