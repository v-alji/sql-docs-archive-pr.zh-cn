---
title: 在知识发现中从 Excel 文件中导入域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 332045466b95088523acda97a931168b0bb5c1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588702"
---
# <a name="import-domains-from-an-excel-file-in-knowledge-discovery"></a><span data-ttu-id="0cb02-102">在知识发现中从 Excel 文件中导入域</span><span class="sxs-lookup"><span data-stu-id="0cb02-102">Import Domains from an Excel File in Knowledge Discovery</span></span>
  <span data-ttu-id="0cb02-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 知识发现活动中从某一 Excel 文件导入一个或多个域。</span><span class="sxs-lookup"><span data-stu-id="0cb02-103">This topic describes how to import one or more domains from an Excel file in the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) knowledge discovery activity.</span></span> <span data-ttu-id="0cb02-104">该导入过程简化了知识生成过程，并且可以节省时间和精力。</span><span class="sxs-lookup"><span data-stu-id="0cb02-104">The import process simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="0cb02-105">借助这一方法，在 Excel 文件或文本文件中具有数据的人士能够创建包含这些数据的知识库。</span><span class="sxs-lookup"><span data-stu-id="0cb02-105">It enables people who have data in an Excel file or a text file to create a knowledge base with that data.</span></span> <span data-ttu-id="0cb02-106"> (请参阅将[值从 Excel 文件导入到域](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)中，以了解有关将值导入到现有知识库的域中的详细信息。不支持导出到 Excel 文件 ) 。</span><span class="sxs-lookup"><span data-stu-id="0cb02-106">(See [Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) for more information about importing values into a domain of an existing knowledge base.) Exporting to an Excel file is not supported.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0cb02-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="0cb02-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="0cb02-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="0cb02-108">Prerequisites</span></span>  
 <span data-ttu-id="0cb02-109">若要从 Excel 文件导入域，Excel 必须安装在装有 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的计算机上；您必须使用域值创建了一个 Excel 文件（请参阅 [How the import works](#How)）；并且必须创建并打开了要将域导入其中的知识库。</span><span class="sxs-lookup"><span data-stu-id="0cb02-109">To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] is installed on; you must have created an Excel file with domain values (see [How the import works](#How)); and you must have created and opened a knowledge base to import the domain into.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0cb02-110">Security</span><span class="sxs-lookup"><span data-stu-id="0cb02-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0cb02-111">权限</span><span class="sxs-lookup"><span data-stu-id="0cb02-111">Permissions</span></span>  
 <span data-ttu-id="0cb02-112">您必须具有针对 DQS_MAIN 数据库的 dqs_kb_editor 或 dqs_administrator 角色，才能从 Excel 文件导入域。</span><span class="sxs-lookup"><span data-stu-id="0cb02-112">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import domains from an Excel file.</span></span>  
  
##  <a name="import-domains-from-an-excel-file-into-a-knowledge-base"></a><a name="Import"></a><span data-ttu-id="0cb02-113">将域从 Excel 文件导入到知识库中</span><span class="sxs-lookup"><span data-stu-id="0cb02-113">Import domains from an Excel file into a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="0cb02-114">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb02-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="0cb02-115">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="0cb02-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0cb02-116">通过以下方式创建要导入的新知识库：单击 **“新建知识库”**，为新知识库输入名称，为 **“创建知识库自”** 选择 **“无”**，选择 **“知识发现”** 活动，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="0cb02-116">Create a new knowledge base to import into by clicking **New knowledge base**, entering a name for the knowledge base, selecting **None** for **Create knowledge base from**, selecting the **Knowledge Discovery** activity, and then clicking **Create**.</span></span>  
  
    -   <span data-ttu-id="0cb02-117">通过以下方式打开要导入的现有知识库：单击 **“打开知识库”**，选择知识库，选择 **“知识发现”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0cb02-117">Open an existing knowledge base to import into by clicking **Open knowledge base**, selecting the knowledge base, selecting **Knowledge Discovery**, and then clicking **Next**.</span></span>  
  
3.  <span data-ttu-id="0cb02-118">在“映射” \*\*\*\* 页中，为“数据源” \*\*\*\* 选择“Excel 文件” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cb02-118">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
4.  <span data-ttu-id="0cb02-119">在 **“Excel 文件”** 行中单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="0cb02-119">Click **Browse** on the **Excel File** line.</span></span>  
  
5.  <span data-ttu-id="0cb02-120">在 **“选择 Excel 文件”** 对话框中，移到包含您要从其导入的 Excel 文件的文件夹，选择该 Excel 文件，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="0cb02-120">In the **Select an Excel File** dialog box, move to the folder that contains the Excel file that you want to import from, select the Excel file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="0cb02-121">从 **“工作表”** 下拉列表中，选择您要从其导入的 Excel 文件中的工作表。</span><span class="sxs-lookup"><span data-stu-id="0cb02-121">From the **Worksheet** drop-down list, select the worksheet in the Excel file that you want to import from.</span></span>  
  
7.  <span data-ttu-id="0cb02-122">如果您希望第一行作为数据标头，并且希望第一行中的值用作列名称，则选择 **“将第一行用作标头”** 。</span><span class="sxs-lookup"><span data-stu-id="0cb02-122">Select **Use First Row as header** if you want the first row to be considered a data header, and if you want the values in the first row to be used as column names.</span></span> <span data-ttu-id="0cb02-123">如果您希望第一行作为数据值，则取消选择 **“将第一行用作标头”** ，在此情况下，DQS 将使用 Excel 标头名称（字母）用于列。</span><span class="sxs-lookup"><span data-stu-id="0cb02-123">Deselect **Use First Row as header** if you want the first row to be considered a data value, in which case DQS will use the Excel header names (alphabetical letters) for the column.</span></span>  
  
8.  <span data-ttu-id="0cb02-124">选择某一列，然后或者将某个现有域映射到该列，或者创建一个新域，方法是单击 **“创建域”** 图标，在 **“创建域”** 对话框中创建一个域，然后将该域映射到该列。</span><span class="sxs-lookup"><span data-stu-id="0cb02-124">Select a column, and then either map an existing domain to the column, or create a new domain by clicking the **Create a Domain** icon, creating a domain in the **Create a domain** dialog box, and then mapping the domain to the column.</span></span> <span data-ttu-id="0cb02-125">该域的数据类型必须与该列的数据类型匹配。</span><span class="sxs-lookup"><span data-stu-id="0cb02-125">The data type of the domain must match the data type of the column.</span></span> <span data-ttu-id="0cb02-126">为电子表格的所有列重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="0cb02-126">Repeat for all columns of the spreadsheet.</span></span>  
  
9. <span data-ttu-id="0cb02-127">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0cb02-127">Click **Next**.</span></span>  
  
10. <span data-ttu-id="0cb02-128">在 **“发现”** 页中，单击 **“开始”** 以便分析 Excel 电子表格中的数据。</span><span class="sxs-lookup"><span data-stu-id="0cb02-128">In the **Discover** page, click **Start** to analyze the data in the Excel spreadsheet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0cb02-129">如果在上载完数据前离开该页，则文件上载过程将终止。</span><span class="sxs-lookup"><span data-stu-id="0cb02-129">If you leave the page before the data has been uploaded, the file upload process will be terminated.</span></span>  
  
11. <span data-ttu-id="0cb02-130">验证分析已成功完成，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="0cb02-130">Verify that the analysis completed successfully, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="0cb02-131">在 **“管理域值”** 页中，验证在 **“域”** 列表中列出了正确的域并且在域表中输入了值。</span><span class="sxs-lookup"><span data-stu-id="0cb02-131">In the **Manage Domain Values** page, verify that the correct domains are listed in the **Domains** list and that values are entered in the domain table.</span></span>  
  
13. <span data-ttu-id="0cb02-132">单击 **“完成”**，然后单击 **“发布”** 以便发布知识库，或者单击 **“否”** 以便不发布。</span><span class="sxs-lookup"><span data-stu-id="0cb02-132">Click **Finish**, and then click **Publish** to publish the knowledge base, or **No** not to publish.</span></span>  
  
14. <span data-ttu-id="0cb02-133">验证知识库已发布，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="0cb02-133">Verify that the knowledge base was published, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-importing-domains-from-an-excel-file"></a><a name="FollowUp"></a> <span data-ttu-id="0cb02-134">跟进：在从 Excel 文件导入域后</span><span class="sxs-lookup"><span data-stu-id="0cb02-134">Follow Up: After Importing Domains from an Excel File</span></span>  
 <span data-ttu-id="0cb02-135">在从 Excel 文件导入域之后，您可以将知识添加到域中，或在清理或匹配项目中使用域，具体取决于域的内容。</span><span class="sxs-lookup"><span data-stu-id="0cb02-135">After you import domains from an Excel file, you can add knowledge to the domains or use the domains in a cleansing or matching project, depending on the contents of the domains.</span></span> <span data-ttu-id="0cb02-136">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)、[管理复合域](../../2014/data-quality-services/managing-a-composite-domain.md)、[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)、[数据清理](../../2014/data-quality-services/data-cleansing.md)或[数据匹配](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb02-136">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="how-the-import-works"></a><a name="How"></a><span data-ttu-id="0cb02-137">导入的工作方式</span><span class="sxs-lookup"><span data-stu-id="0cb02-137">How the import works</span></span>  
 <span data-ttu-id="0cb02-138">在导入操作中，DQS 按如下所示解释 Excel 文件：</span><span class="sxs-lookup"><span data-stu-id="0cb02-138">In the import operation, DQS interprets an Excel file as follows:</span></span>  
  
-   <span data-ttu-id="0cb02-139">列表示域</span><span class="sxs-lookup"><span data-stu-id="0cb02-139">A column represents a domain</span></span>  
  
-   <span data-ttu-id="0cb02-140">行表示数据记录</span><span class="sxs-lookup"><span data-stu-id="0cb02-140">A row represents a data record</span></span>  
  
-   <span data-ttu-id="0cb02-141">第一行或者表示域名，或者是第一个数据值或记录，视 **“将第一行用作标题”** 复选框的设置而定。</span><span class="sxs-lookup"><span data-stu-id="0cb02-141">The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.</span></span>  
  
 <span data-ttu-id="0cb02-142">下列规则适用于导入操作：</span><span class="sxs-lookup"><span data-stu-id="0cb02-142">The following rules apply to the import operation:</span></span>  
  
-   <span data-ttu-id="0cb02-143">此操作将域值导入到知识库中。</span><span class="sxs-lookup"><span data-stu-id="0cb02-143">This operation imports domain values into a knowledge base.</span></span> <span data-ttu-id="0cb02-144">它不导入域规则或匹配策略。</span><span class="sxs-lookup"><span data-stu-id="0cb02-144">It does not import domain rules or a matching policy.</span></span>  
  
-   <span data-ttu-id="0cb02-145">该 Excel 文件可以具有扩展名 .xlsx、.xls 或 .csv。</span><span class="sxs-lookup"><span data-stu-id="0cb02-145">The Excel file can have the extension .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="0cb02-146">Microsoft Excel 必须安装在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 计算机上，以便导入域值或整个域。</span><span class="sxs-lookup"><span data-stu-id="0cb02-146">Microsoft Excel must be installed on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer to import domain values or a complete domain.</span></span> <span data-ttu-id="0cb02-147">支持 Excel 版本 2003 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="0cb02-147">Excel versions 2003 and later are supported.</span></span> <span data-ttu-id="0cb02-148">如果使用 64 位版本的 Excel，将仅支持 Excel 2003 文件；而不支持 Excel 2007 或 2010 文件。</span><span class="sxs-lookup"><span data-stu-id="0cb02-148">If the 64-bit version of Excel is used, only Excel 2003 files will be supported; Excel 2007 or 2010 files will not be supported.</span></span>  
  
-   <span data-ttu-id="0cb02-149">Excel 64 位安装不支持 .xlsx 类型的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="0cb02-149">Excel files of type .xlsx are not supported for an Excel 64-bit installation.</span></span> <span data-ttu-id="0cb02-150">如果您使用的是 64 位 Excel，将以 .xls 文件保存电子表格文件。</span><span class="sxs-lookup"><span data-stu-id="0cb02-150">If you are using 64-bit Excel, save the spreadsheet file as an .xls file.</span></span>  
  
-   <span data-ttu-id="0cb02-151">在 .xlsx 和 .xls 文件中，列的数据类型由前八行中最主要的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="0cb02-151">In .xlsx and .xls files, the data type of the column is determined by the most prevalent data type in the first eight rows.</span></span> <span data-ttu-id="0cb02-152">如果某一单元不符合该数据类型，将向它提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="0cb02-152">If a cell does not conform to that data type, it will be given a null value.</span></span>  
  
-   <span data-ttu-id="0cb02-153">在 .csv 文件中，数据类型由前八行中的主要数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="0cb02-153">In .csv files, the data type is determined by the most prevalent data type in the first eight rows.</span></span>  
  
-   <span data-ttu-id="0cb02-154">Excel 电子表格中不符合域规则的值将作为无效值导入。</span><span class="sxs-lookup"><span data-stu-id="0cb02-154">A value in an Excel spreadsheet that does not conform to a domain rule will be imported as an invalid value.</span></span>  
  
-   <span data-ttu-id="0cb02-155">如果该 Excel 文件未采用正确的格式或已损坏，则导入操作将导致错误。</span><span class="sxs-lookup"><span data-stu-id="0cb02-155">If the Excel file is not in the right format or is corrupted, the import operation will result in an error.</span></span>  
  
  
