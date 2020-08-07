---
title: 将值从 Excel 文件导入到域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.failingvalues.f1
- sql12.dqs.kb.importfailing.f1
- sql12.dqs.kb.importselect.f1
ms.assetid: 04cde693-2043-477f-8417-fcc463ca7195
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7726f7ad41dfe3609a52f1d09473cab748580778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588701"
---
# <a name="import-values-from-an-excel-file-into-a-domain"></a><span data-ttu-id="af612-102">将值从 Excel 文件导入到域</span><span class="sxs-lookup"><span data-stu-id="af612-102">Import Values from an Excel File into a Domain</span></span>
  <span data-ttu-id="af612-103">本主题介绍如何将值从 Excel 文件导入到 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的域中。</span><span class="sxs-lookup"><span data-stu-id="af612-103">This topic describes how to import values from an Excel file into a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="af612-104">使用 Excel 文件将域值导入到 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序中可以简化知识生成过程、节省时间并提高效率。</span><span class="sxs-lookup"><span data-stu-id="af612-104">Using an Excel file to import domain values into the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="af612-105">借助这一方法，在 Excel 文件或文本文件中具有有效数据值列表的人士能够将这些值导入到域中。</span><span class="sxs-lookup"><span data-stu-id="af612-105">It enables people who have a list of valid data values in an Excel file or a text file to import those values into a domain.</span></span> <span data-ttu-id="af612-106">从 Excel 文件，您可以将域值导入到某个域中，或者将多个域导入到知识库中。</span><span class="sxs-lookup"><span data-stu-id="af612-106">From an Excel file you can import domain values into a domain or domains into a knowledge base.</span></span> <span data-ttu-id="af612-107">有关将域导入到知识库的详细信息，请参阅[知识发现中的从 Excel 文件中导入域](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)。不支持导出到 excel 文件的 )  (。</span><span class="sxs-lookup"><span data-stu-id="af612-107">(See [Import Domains from an Excel File in Knowledge Discovery](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md) for more information about importing domains into a knowledge base.) Exporting to an Excel file is not supported.</span></span>  
  
 <span data-ttu-id="af612-108">您可以通过两种方式导入数据值：</span><span class="sxs-lookup"><span data-stu-id="af612-108">You can import data values in two ways:</span></span>  
  
-   <span data-ttu-id="af612-109">创建一个新域然后将值从 Excel 文件导入到该域中，在这种情况下，所有值都将添加到该域中。</span><span class="sxs-lookup"><span data-stu-id="af612-109">Create a new domain and then import values into it from an Excel file, in which case all values are added to the domain.</span></span>  
  
-   <span data-ttu-id="af612-110">将值导入到一个现有的已填充域中，在这种情况下，仅导入新值。</span><span class="sxs-lookup"><span data-stu-id="af612-110">Import values into an existing, populated domain, in which case only new values are imported.</span></span> <span data-ttu-id="af612-111">将不会导入所有已存在的值。</span><span class="sxs-lookup"><span data-stu-id="af612-111">All values that already exist will not be imported.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af612-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="af612-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="af612-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="af612-113">Prerequisites</span></span>  
 <span data-ttu-id="af612-114">若要从 Excel 文件导入域，Excel 必须安装在装有 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序的计算机上，以便导入域值或整个域；您必须使用域值创建了一个 Excel 文件（请参阅 [How the import works](#How)）；并且必须创建并打开了要将域导入其中的知识库。</span><span class="sxs-lookup"><span data-stu-id="af612-114">To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is installed on in order to import domain values or a complete domain; you must have created an Excel file with domain values (see [How the import works](#How)); and you must have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af612-115">Security</span><span class="sxs-lookup"><span data-stu-id="af612-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af612-116">权限</span><span class="sxs-lookup"><span data-stu-id="af612-116">Permissions</span></span>  
 <span data-ttu-id="af612-117">您必须具有针对 DQS_MAIN 数据库的 dqs_kb_editor 或 dqs_administrator 角色，才能从 Excel 文件导入域值。</span><span class="sxs-lookup"><span data-stu-id="af612-117">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import domains values from an Excel file.</span></span>  
  
##  <a name="import-values-from-an-excel-file-into-a-domain"></a><a name="Import"></a><span data-ttu-id="af612-118">将值从 Excel 文件导入到域中</span><span class="sxs-lookup"><span data-stu-id="af612-118">Import values from an Excel file into a domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="af612-119">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="af612-119">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="af612-120">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在域管理活动中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="af612-120">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="af612-121">如果将值添加到新域，则使用 **“创建域”** 图标创建一个新域，然后在域列表中选择这个新域。</span><span class="sxs-lookup"><span data-stu-id="af612-121">If adding values to a new domain, create a new domain using the **Create a Domain** icon, and then select the new domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="af612-122">如果将值添加到某个现有域中，则在域列表中选择该域。</span><span class="sxs-lookup"><span data-stu-id="af612-122">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
5.  <span data-ttu-id="af612-123">单击 **“域值”** 选项卡，在图标栏中单击 **“导入值”** 图标，然后单击 **“从 Excel 导入有效值”**。</span><span class="sxs-lookup"><span data-stu-id="af612-123">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import valid values from Excel**.</span></span>  
  
6.  <span data-ttu-id="af612-124">在 **“导入域值”** 对话框中，单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="af612-124">In the **Import Domain Values** dialog box, click **Browse**.</span></span>  
  
7.  <span data-ttu-id="af612-125">在 **“选择文件”** 对话框中，移到包含您要从其导入域值的 Excel 文件，选择该文件（具有 .xlsx、.xls 或 .csv 扩展名），然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="af612-125">In the **Select file** dialog box, move to the folder that contains the Excel file that you want to import domain values from, select the file (with a .xlsx, .xls, or .csv extension), and then click **Open**.</span></span> <span data-ttu-id="af612-126">该文件必须或者位于您从其运行 DQS 的客户端上，或者位于用户有权访问的共享文件中。</span><span class="sxs-lookup"><span data-stu-id="af612-126">The file must be either on the client that you run DQS from, or in a share file that the user has access to.</span></span>  
  
8.  <span data-ttu-id="af612-127">从 **“工作表”** 下拉列表中，选择您要从其导入的工作表。</span><span class="sxs-lookup"><span data-stu-id="af612-127">From the **Worksheet** drop-down list, select the worksheet that you are importing from.</span></span>  
  
9. <span data-ttu-id="af612-128">如果电子表格中的第一行表示域名，并且所有其他行表示有效的域值，则选择 **“将第一行用作标头”** 。</span><span class="sxs-lookup"><span data-stu-id="af612-128">Select **Use first row as header** if the first row in the spreadsheet represents the domain name, and all other rows represent valid domain values.</span></span>  
  
10. <span data-ttu-id="af612-129">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="af612-129">Click **OK**.</span></span> <span data-ttu-id="af612-130">将显示一个进度栏，指示成功导入了多少个值、未导入多少个值以及值的总数。</span><span class="sxs-lookup"><span data-stu-id="af612-130">A progress bar is displayed, with an indication of how many values have been imported successfully, how many were not imported, and the total number of values.</span></span> <span data-ttu-id="af612-131">单击 **“取消”** 按钮将取消该过程。</span><span class="sxs-lookup"><span data-stu-id="af612-131">Click the **Cancel** button to cancel the process.</span></span>  
  
11. <span data-ttu-id="af612-132">确认“导入完成”显示在“导入域值”对话框中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af612-132">Verify that "Import complete" is displayed in the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="af612-133">在此对话框中查看哪些值已成功导入、哪些值未导入。</span><span class="sxs-lookup"><span data-stu-id="af612-133">See which values were successfully imported, and which were not, in this dialog box.</span></span> <span data-ttu-id="af612-134">该对话框将指示文件的名称和路径、操作的完成状态、成功导入了多少个值、未导入多少个值以及处理的值的总数。</span><span class="sxs-lookup"><span data-stu-id="af612-134">It indicates the name of the file and the file's path, the completion status of the operation, how many values have been imported successfully, how many values were not imported, and the total number of values processed.</span></span>  
  
12. <span data-ttu-id="af612-135">对于未成功导入的那些值，单击“日志”可显示“导入域值 – 失败值”对话框，从而查看导入操作失败的原因\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af612-135">For those values that were not successfully imported, click **Log** to display the **Import Domain Values - Failing Values** dialog box to see why the import operation failed.</span></span> <span data-ttu-id="af612-136">**“失败值”** 列将显示未能从 Excel 文件导入到域中的值， **“原因”** 列将说明导入失败的原因。</span><span class="sxs-lookup"><span data-stu-id="af612-136">The **Failing Value** column shows the values that failed to be imported from an Excel file into a domain, and the **Reason** column explains why the import failed.</span></span> <span data-ttu-id="af612-137">单击 **“复制到剪贴板”** 可以将 **“失败值”** 表复制到剪贴板上，从而可以将该表复制到其他程序中，例如复制到 Excel 电子表格或记事本文件中。</span><span class="sxs-lookup"><span data-stu-id="af612-137">Click **Copy to clipboard** to copy the **Failing Value** table onto the clipboard, from which you can copy it into another program, such as an Excel spreadsheet or a Notepad file.</span></span> <span data-ttu-id="af612-138">单击 **“确定”** 关闭 **“失败值”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="af612-138">Click **OK** to close the **Failing Values** dialog box.</span></span>  
  
13. <span data-ttu-id="af612-139">单击 **“确定”** 将完成导入操作并且关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="af612-139">Click **OK** to complete the import operation and close the dialog box.</span></span> <span data-ttu-id="af612-140">在导入成功完成后， **“域值”** 页上的域值列表将刷新并且将包含新导入的值。</span><span class="sxs-lookup"><span data-stu-id="af612-140">When the import has completed successfully, the domain values list on the **Domain Values** page is refreshed and will include the new imported values.</span></span> <span data-ttu-id="af612-141">筛选器将更改为 **“所有值”** ，并且 **“仅显示新内容”** 将被选中。</span><span class="sxs-lookup"><span data-stu-id="af612-141">The filter is changed to **All Values** and **Show Only New** is selected.</span></span> <span data-ttu-id="af612-142">如果在导入操作后选中了 **“仅显示新内容”** ，将仅显示从 Excel 文件导入的值。</span><span class="sxs-lookup"><span data-stu-id="af612-142">When **Show Only New** is selected after the import operation, only the values imported from the Excel file will be displayed.</span></span>  
  
14. <span data-ttu-id="af612-143">单击 **“完成”** 将值添加到知识库。</span><span class="sxs-lookup"><span data-stu-id="af612-143">Click **Finish** to add the values to the knowledge base.</span></span>  
  
##  <a name="follow-up-after-importing-values-from-an-excel-file-into-a-domain"></a><a name="FollowUp"></a><span data-ttu-id="af612-144">跟进：在将值从 Excel 文件导入到域后</span><span class="sxs-lookup"><span data-stu-id="af612-144">Follow Up: After Importing Values from an Excel File into a Domain</span></span>  
 <span data-ttu-id="af612-145">在将值导入到某个域中之后，您可以对该域执行其他域管理任务，可以执行知识发现以便向该域添加知识，或者可以向该域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="af612-145">After you import values into a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="af612-146">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="af612-146">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="importing-synonyms"></a><a name="Synonyms"></a><span data-ttu-id="af612-147">导入同义词</span><span class="sxs-lookup"><span data-stu-id="af612-147">Importing Synonyms</span></span>  
 <span data-ttu-id="af612-148">按如下所示导入同义词：</span><span class="sxs-lookup"><span data-stu-id="af612-148">Synonyms are imported as follows:</span></span>  
  
-   <span data-ttu-id="af612-149">首先，导入所有值，然后建立同义词连接。</span><span class="sxs-lookup"><span data-stu-id="af612-149">First, all values are imported, then the synonym connection is established.</span></span>  
  
-   <span data-ttu-id="af612-150">如果无法连接同义词值，在日志屏幕将出现错误。</span><span class="sxs-lookup"><span data-stu-id="af612-150">If it is impossible to connect synonym values, an error will appear in the log screen.</span></span> <span data-ttu-id="af612-151">文件中的前导值和同义词可以导入到域中，但将不会被设为同义词。</span><span class="sxs-lookup"><span data-stu-id="af612-151">It is possible that the leading values and the synonyms in the file will be imported to the domain, but will not be set as synonyms.</span></span>  
  
 <span data-ttu-id="af612-152">以下内容适用于设置同义词连接的过程：</span><span class="sxs-lookup"><span data-stu-id="af612-152">The following apply to the process of setting synonym connections:</span></span>  
  
-   <span data-ttu-id="af612-153">如果该 Excel 文件中的前导值已在域中作为其他值的同义词存在，则您必须手动设置同义词（例如，在 Excel 文件中，我们希望值 A 将是值 B 的前导值，但在该域中，值 A 作为值 C 的同义词出现）。</span><span class="sxs-lookup"><span data-stu-id="af612-153">If the leading value in the Excel file already exists in the domain as a synonym of a different value, you will have to set the synonyms manually (e.g., in the Excel file we want that value A will be the leading value for value B, but in the domain value A appears as a synonym of value C).</span></span> <span data-ttu-id="af612-154">除了在导入完成后手动设置同义词之外，您还可以取消现有同义词上的值的链接（例如，取消上面的值 A 和 C 的链接），然后导入文件。</span><span class="sxs-lookup"><span data-stu-id="af612-154">In addition to setting synonyms manually after the import completes, you can also unlink values that are at present synonyms (for example, unlink values A and C above), and then import the file.</span></span>  
  
-   <span data-ttu-id="af612-155">如果同义词已连接到其他前导值，则必须手动设置同义词。</span><span class="sxs-lookup"><span data-stu-id="af612-155">If the synonym is already connected to a different leading value, you will have to set the synonyms manually.</span></span>  
  
-   <span data-ttu-id="af612-156">如果出于任何原因不能在应用程序中手动连接这些值，则这些值将不适用于导入操作。</span><span class="sxs-lookup"><span data-stu-id="af612-156">If the values cannot be connected manually in the application for any reason, it will not be applicable through the import operation.</span></span>  
  
##  <a name="how-the-import-works"></a><a name="How"></a><span data-ttu-id="af612-157">导入的工作方式</span><span class="sxs-lookup"><span data-stu-id="af612-157">How the import works</span></span>  
 <span data-ttu-id="af612-158">此操作将导入下列值：</span><span class="sxs-lookup"><span data-stu-id="af612-158">The following values are imported by this operation:</span></span>  
  
 <span data-ttu-id="af612-159">在导入操作中，DQS 按如下所示从 Excel 文件进行导入：</span><span class="sxs-lookup"><span data-stu-id="af612-159">In the import operation, DQS imports from an Excel file as follows:</span></span>  
  
-   <span data-ttu-id="af612-160">将导入正确的值和新值。</span><span class="sxs-lookup"><span data-stu-id="af612-160">Correct values and new values are imported.</span></span> <span data-ttu-id="af612-161">如果已经存在一个或多个导入的域值，这些值将不会导入。</span><span class="sxs-lookup"><span data-stu-id="af612-161">If one or more of the imported domain values already exists, the values will not be imported.</span></span>  
  
-   <span data-ttu-id="af612-162">与域规则相矛盾的值将作为无效值导入。</span><span class="sxs-lookup"><span data-stu-id="af612-162">A value that contradicts a domain rule will be imported as an invalid value.</span></span>  
  
-   <span data-ttu-id="af612-163">如果某个值不属于该域的数据类型或者为 null，将不会从文件中导入该值。</span><span class="sxs-lookup"><span data-stu-id="af612-163">A value will not be imported from the file if the value is not of the domain's data type or is null.</span></span>  
  
-   <span data-ttu-id="af612-164">值将按它们在文件中出现的顺序导入。</span><span class="sxs-lookup"><span data-stu-id="af612-164">Values are imported in the order in which they appear in the file.</span></span>  
  
-   <span data-ttu-id="af612-165">每一行都表示某个域值。</span><span class="sxs-lookup"><span data-stu-id="af612-165">Each row represents a domain value.</span></span>  
  
-   <span data-ttu-id="af612-166">第一行或者表示域名，或者是第一个数据值或记录，视 **“将第一行用作标题”** 复选框的设置而定。</span><span class="sxs-lookup"><span data-stu-id="af612-166">The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.</span></span> <span data-ttu-id="af612-167">如果您在使用 .xslx 或 .xls 文件时选择了 **“将第一行用作标头”** ，则为 null 的任何列名都将自动转换为 F*n*，并且任何重复列都将在其名称后追加一个编号。</span><span class="sxs-lookup"><span data-stu-id="af612-167">If you select **Use First Row as header** when using an .xslx or .xls file, any column names that are null will be automatically converted into F*n*, and any columns that are duplicate will have a number appended to them.</span></span>  
  
-   <span data-ttu-id="af612-168">如果您在导入操作完成前取消该操作，则该操作将回滚，并且将不会导入任何数据。</span><span class="sxs-lookup"><span data-stu-id="af612-168">If you cancel the import operation before it has completed, the operation will be rolled back and no data will be imported.</span></span>  
  
-   <span data-ttu-id="af612-169">第一列中的值将导入到域中。</span><span class="sxs-lookup"><span data-stu-id="af612-169">The values in the first column are imported into the domain.</span></span> <span data-ttu-id="af612-170">如果除了第一列之外，还填充一个或多个其他列，则这些列中的值将作为同义词添加（请参阅 [导入同义词](#Synonyms)）。</span><span class="sxs-lookup"><span data-stu-id="af612-170">If in addition to the first column, one or more additional columns are populated, then the values in those columns will be added as synonyms (see [Importing Synonyms](#Synonyms)).</span></span>  
  
    -   <span data-ttu-id="af612-171">预期的格式为：第一列将是前导值，第二列和以后的列将是同义词。</span><span class="sxs-lookup"><span data-stu-id="af612-171">The expected format is that the first column will be leading values and the second column and above will be synonyms.</span></span>  
  
    -   <span data-ttu-id="af612-172">您可以在同一行或不同行中导入多个同义词。</span><span class="sxs-lookup"><span data-stu-id="af612-172">You can import multiple synonyms in the same row or in different rows.</span></span> <span data-ttu-id="af612-173">例如，如果你要导入“NYC”和“New York City”作为“New York”的同义词，则可以导入在第 1 列中具有“New York”、在第 2 列中具有“NYC”、在第 3 列中具有“New York City”的单个行；或者，您可以导入在第 1 列中具有“New York”、在第 2 列中具有“NYC”的一行，以及在第一列中具有“New York”、在第 2 列中具有“New York City”的另一行。</span><span class="sxs-lookup"><span data-stu-id="af612-173">For example, if you want to import "NYC" and "New York City" as synonyms for "New York", you can import a single row with "New York" in column 1, "NYC" in column 2, and "New York City" in column 3; or you can import one row with "New York" in column 1 and "NYC" in column 2, and another row with "New York" in column 1 and "New York City" in column 2.</span></span> <span data-ttu-id="af612-174">请注意，如果值“New York”已在域中存在，将只添加同义词，并且用户在导入过程中将不会收到指示该值已存在的错误消息。</span><span class="sxs-lookup"><span data-stu-id="af612-174">Note that if the value "New York" already exists in the domain, only the synonyms will be added, and the user will not receive an error during the import process telling him that the value already exist.</span></span> <span data-ttu-id="af612-175">如果第一个值已不存在，则它将被添加到域中。</span><span class="sxs-lookup"><span data-stu-id="af612-175">If the first value does not already exist, it will be added to the domain.</span></span>  
  
 <span data-ttu-id="af612-176">下列规则适用于要用于导入的 Excel 文件：</span><span class="sxs-lookup"><span data-stu-id="af612-176">The following rules apply to the Excel file being used for the import:</span></span>  
  
-   <span data-ttu-id="af612-177">该 Excel 文件可以具有扩展名 .xlsx、.xls 或 .csv。</span><span class="sxs-lookup"><span data-stu-id="af612-177">The Excel file can have the extension .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="af612-178">Microsoft Excel 必须安装在装有 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序的计算机上，以便导入域值或整个域。</span><span class="sxs-lookup"><span data-stu-id="af612-178">Microsoft Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is installed on in order to import domain values or a complete domain.</span></span> <span data-ttu-id="af612-179">支持 Excel 版本 2003 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="af612-179">Excel versions 2003 and later are supported.</span></span> <span data-ttu-id="af612-180">如果使用 64 位版本的 Excel，则仅支持 Excel 2003 文件；而不支持 Excel 2007 或 2010 文件。</span><span class="sxs-lookup"><span data-stu-id="af612-180">If the 64-bit version of Excel is used, only Excel 2003 files are supported; Excel 2007 or 2010 files are not supported.</span></span>  
  
-   <span data-ttu-id="af612-181">Excel 64 位安装不支持 .xlsx 类型的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="af612-181">Excel files of type .xlsx are not supported for an Excel 64-bit installation.</span></span> <span data-ttu-id="af612-182">如果您使用的是 64 位的 Excel，则将电子表格文件另存为 .xls 文件或 .csv 文件，或者改而安装 32 位的 Excel。</span><span class="sxs-lookup"><span data-stu-id="af612-182">If you are using 64-bit Excel, save the spreadsheet file as an .xls file or a .csv file, or install an Excel 32-bit installation instead.</span></span>  
  
-   <span data-ttu-id="af612-183">在 .xlsx 和 .xls 文件中，列的数据类型由前八行确定。</span><span class="sxs-lookup"><span data-stu-id="af612-183">In .xlsx and .xls files, the data type of the column is determined by the first eight rows.</span></span> <span data-ttu-id="af612-184">如果前八行的列数据类型是混合类型，则列类型将是字符串。</span><span class="sxs-lookup"><span data-stu-id="af612-184">If the column data type of the first eight rows is mixed, the column type will be string.</span></span> <span data-ttu-id="af612-185">如果第 9 行和更高行的单元不符合该数据类型，将向它提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="af612-185">If a cell for row 9 and higher does not conform to that data type, it will be given a null value.</span></span>  
  
-   <span data-ttu-id="af612-186">在 .csv 文件中，数据类型由前八行中的主要数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="af612-186">In .csv files, the data type is determined by the most prevalent data type in the first eight rows.</span></span>  
  
-   <span data-ttu-id="af612-187">如果该 Excel 文件未采用正确的格式或已损坏，则导入操作将导致错误。</span><span class="sxs-lookup"><span data-stu-id="af612-187">If the Excel file is not in the right format or is corrupted, the import operation will result in an error.</span></span>  
  
  
