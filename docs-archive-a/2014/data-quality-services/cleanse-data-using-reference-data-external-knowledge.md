---
title: 使用引用数据（外部）知识清理数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 107fd3bbf3c6f14e50cb6527400697aab7c7d6a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683080"
---
# <a name="cleanse-data-using-reference-data-external-knowledge"></a><span data-ttu-id="9745f-102">使用引用数据（外部）知识清理数据</span><span class="sxs-lookup"><span data-stu-id="9745f-102">Cleanse Data Using Reference Data (External) Knowledge</span></span>
  <span data-ttu-id="9745f-103">本主题说明如何使用引用数据提供程序中的知识清理数据。</span><span class="sxs-lookup"><span data-stu-id="9745f-103">This topic describes how to cleanse data using knowledge from the reference data providers.</span></span> <span data-ttu-id="9745f-104">尽管运行清理活动的所有步骤与使用来自引用数据提供程序的知识清理数据（请参阅[使用 DQS（内部）知识清理数据[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]中的说明）的步骤相同，但本主题提供的信息特定于使用 ](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md) (DQS) 中的引用数据服务清理数据。</span><span class="sxs-lookup"><span data-stu-id="9745f-104">While all the steps of running a cleansing activity remains the same for cleansing your data using knowledge from the reference data providers as explained in the [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md), this topic provides information specific to data cleansing using reference data service in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>

 <span data-ttu-id="9745f-105">在您使用 DQS 中的引用数据服务功能清理数据时，该 DQS 清理过程将映射的域值以批处理请求的形式发送到引用数据服务提供程序中。</span><span class="sxs-lookup"><span data-stu-id="9745f-105">When you use the reference data service feature in DQS to cleanse your data, the DQS cleansing process sends the mapped domain values to the reference data service provider as a batch request.</span></span> <span data-ttu-id="9745f-106">引用数据服务将会响应以下信息：</span><span class="sxs-lookup"><span data-stu-id="9745f-106">The reference data service responds with the following information:</span></span>

-   <span data-ttu-id="9745f-107">建议的更正</span><span class="sxs-lookup"><span data-stu-id="9745f-107">Suggested correction</span></span>

-   <span data-ttu-id="9745f-108">置信度</span><span class="sxs-lookup"><span data-stu-id="9745f-108">Confidence</span></span>

-   <span data-ttu-id="9745f-109">有关映射的域的其他信息。</span><span class="sxs-lookup"><span data-stu-id="9745f-109">Additional information about the mapped domain.</span></span> <span data-ttu-id="9745f-110">引用数据还可以对源执行标准化和分析，也可以使用其他数据丰富源的内容。</span><span class="sxs-lookup"><span data-stu-id="9745f-110">Reference data can also standardize, parse, or enrich the source with additional data.</span></span> <span data-ttu-id="9745f-111">此信息在响应的附加字段中提供。</span><span class="sxs-lookup"><span data-stu-id="9745f-111">This information is provided in additional fields in the response.</span></span>

 <span data-ttu-id="9745f-112">在从引用数据服务获取响应后，在清理活动过程中在 DQS 中将发生以下情况：</span><span class="sxs-lookup"><span data-stu-id="9745f-112">After getting the response from reference data service, the following happens in DQS during the cleansing activity:</span></span>

-   <span data-ttu-id="9745f-113">基于在将域与引用数据服务进行映射的过程中指定的 **“自动更正阈值”** 和 **“最低置信度”** 值，将根据置信度自动更正或建议域值。</span><span class="sxs-lookup"><span data-stu-id="9745f-113">Based on the **Auto Correction Threshold** and **Min Confidence** values specified during mapping of the domains with reference data service, domain values are automatically corrected or suggested based on the confidence level.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9745f-114">您在将域映射到引用数据服务过程中指定的阈值在使用引用数据服务中的知识清理数据时同样适用，但在 **“常规设置”** 选项卡的 **“配置”** 部分中指定的阈值则不适用。</span><span class="sxs-lookup"><span data-stu-id="9745f-114">The threshold values that you specify during mapping a domain to a reference data service are applied while cleansing data using the knowledge in reference data service, and not the ones that are specified in the **General Settings** tab in the **Configuration** section.</span></span> <span data-ttu-id="9745f-115">有关为引用数据清理指定阈值的信息，请参阅[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)中的步骤9。</span><span class="sxs-lookup"><span data-stu-id="9745f-115">For information about specifying threshold values for reference data cleansing, see step 9 in [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

-   <span data-ttu-id="9745f-116">域值划分为以下几个类别： **“建议”**、 **“新建”**、 **“无效”**、 **“已更正”** 和 **“正确”**。</span><span class="sxs-lookup"><span data-stu-id="9745f-116">Domain values are categorized into the following: **Suggested**, **New**, **Invalid**, **Corrected**, and **Correct**.</span></span>

-   <span data-ttu-id="9745f-117">附加数据将追加到源中，并且该信息与清理后的数据一起提供以供导出。</span><span class="sxs-lookup"><span data-stu-id="9745f-117">Additional data is appended to the source, and the information is available along with the cleansed data for exporting.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="9745f-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="9745f-118">Before You Begin</span></span>

###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="9745f-119">先决条件</span><span class="sxs-lookup"><span data-stu-id="9745f-119">Prerequisites</span></span>
 <span data-ttu-id="9745f-120">您必须将 DQS 知识库中的所需域映射到适当的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="9745f-120">You must have mapped required domains in a DQS knowledge base to the appropriate reference data service.</span></span> <span data-ttu-id="9745f-121">此外，知识库必须包含有关您要清理的数据类型的知识。</span><span class="sxs-lookup"><span data-stu-id="9745f-121">Additionally, the knowledge base must contain knowledge about the type of data that you want to cleanse.</span></span> <span data-ttu-id="9745f-122">例如，如果要清理包含美国地址的源数据，则必须将自己的域映射到为美国地址提供高质量数据的引用数据服务提供程序。</span><span class="sxs-lookup"><span data-stu-id="9745f-122">For example, if you want to cleanse your source data that contains US addresses, you must map your domains to a reference data service provider that provides high-quality" data for US addresses.</span></span> <span data-ttu-id="9745f-123">有关详细信息，请参阅[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9745f-123">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9745f-124">Security</span><span class="sxs-lookup"><span data-stu-id="9745f-124">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9745f-125">权限</span><span class="sxs-lookup"><span data-stu-id="9745f-125">Permissions</span></span>
 <span data-ttu-id="9745f-126">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_kb_operator 角色，才能执行数据清理。</span><span class="sxs-lookup"><span data-stu-id="9745f-126">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to perform data cleansing.</span></span>

##  <a name="cleanse-your-data-using-reference-data-knowledge"></a><a name="Cleanse"></a> <span data-ttu-id="9745f-127">使用引用数据知识清理您的数据</span><span class="sxs-lookup"><span data-stu-id="9745f-127">Cleanse Your Data Using Reference Data Knowledge</span></span>
 <span data-ttu-id="9745f-128">接下来，我们将使用在上一主题中映射的域，[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)，并使用 Azure Marketplace 中的 Melissa 数据服务。</span><span class="sxs-lookup"><span data-stu-id="9745f-128">We will continue with the same example of using the domains that we mapped in the previous topic, [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md), with the Melissa Data service in Azure Marketplace.</span></span> <span data-ttu-id="9745f-129">现在，我们将使用相同的域来清理一些示例美国地址。</span><span class="sxs-lookup"><span data-stu-id="9745f-129">Now, we will use the same domains to cleanse some sample US addresses.</span></span> <span data-ttu-id="9745f-130">清理数据的步骤与[使用 DQS（内部）知识清理数据](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中介绍的步骤相同。</span><span class="sxs-lookup"><span data-stu-id="9745f-130">The steps to cleanse data are the same as described in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span> <span data-ttu-id="9745f-131">但是，我们在该过程中将会在需要时提醒您注意。</span><span class="sxs-lookup"><span data-stu-id="9745f-131">However, we will draw you attention wherever necessary during the process.</span></span>

1.  <span data-ttu-id="9745f-132">创建一个数据质量项目，并且选择 **“清理”** 活动。</span><span class="sxs-lookup"><span data-stu-id="9745f-132">Create a data quality project, and select the **Cleansing** activity.</span></span> <span data-ttu-id="9745f-133">请参阅 [Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md)。</span><span class="sxs-lookup"><span data-stu-id="9745f-133">See [Create a Data Quality Project](../../2014/data-quality-services/create-a-data-quality-project.md).</span></span>

2.  <span data-ttu-id="9745f-134">在 **“映射”** 页上，将以下 4 个域与您的源数据中的相应列进行映射： **Address Line**、 **City**、 **State**和 **Zip**。</span><span class="sxs-lookup"><span data-stu-id="9745f-134">On the **Map** page, map the following 4 domains with appropriate columns in your source data: **Address Line**, **City**, **State**, and **Zip**.</span></span> <span data-ttu-id="9745f-135">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="9745f-135">Click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9745f-136">当您在 **“地址验证”** 复合域中映射了所有 4 个域后，数据清理现在将在复合域级别完成，而非在单独的域级别完成。</span><span class="sxs-lookup"><span data-stu-id="9745f-136">As you have mapped all the 4 domains within the **Address Verification** composite domain, the data cleansing will now be done at the composite domain level, and not at the individual domain level.</span></span>

3.  <span data-ttu-id="9745f-137">在 **“清理”** 页上，通过单击 **“开始”** 运行计算机辅助的清理过程。</span><span class="sxs-lookup"><span data-stu-id="9745f-137">On the **Cleanse** page, run the computer-assisted cleansing process by clicking **Start**.</span></span> <span data-ttu-id="9745f-138">在清理过程结束后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="9745f-138">After the cleansing process is over, click **Next**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9745f-139">在 **“清理”** 页上，DQS 通过以下两种方式显示与附加到引用数据服务的域有关的信息：</span><span class="sxs-lookup"><span data-stu-id="9745f-139">On the **Cleanse** page, DQS displays information about the domains that are attached to reference data service in the following two ways:</span></span>
    > 
    >  -   <span data-ttu-id="9745f-140">"**开始**" 按钮下会显示一条消息： "域 \<Domain1> ， \<Domain2> ,... \<DomainN>使用引用数据服务提供程序清理。 "</span><span class="sxs-lookup"><span data-stu-id="9745f-140">A message is displayed below the **Start** button: "Domains \<Domain1>, \<Domain2>,... \<DomainN> are cleansed using reference data service provider."</span></span> <span data-ttu-id="9745f-141">在此示例中，将显示以下消息：“使用引用数据服务提供程序清理域地址验证。”</span><span class="sxs-lookup"><span data-stu-id="9745f-141">In this example, the following message will be displayed: "Domain Address Verification is cleansed using reference data service provider."</span></span>
    > -   <span data-ttu-id="9745f-142">与附加到引用数据服务提供程序的域一起显示在 "**探查器**" 区域中的图标 "![域附加到 RDS](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "将域附加到 RDS")"。</span><span class="sxs-lookup"><span data-stu-id="9745f-142">An icon, ![Domain is attached to RDS](../../2014/data-quality-services/media/dqs-rdsindicator.JPG "Domain is attached to RDS"), is displayed in the **Profiler** area against the domains attached to reference data service provider.</span></span> <span data-ttu-id="9745f-143">在此示例中，将针对 **“地址验证”** 复合域显示该图标。</span><span class="sxs-lookup"><span data-stu-id="9745f-143">In this example, the icon will be displayed against the **Address Verification** composite domain.</span></span>

4.  <span data-ttu-id="9745f-144">在 **“管理和查看结果”** 页上，查看您的域值。</span><span class="sxs-lookup"><span data-stu-id="9745f-144">On the **Manage and view results** page, review your domain values.</span></span> <span data-ttu-id="9745f-145">根据在将域映射到引用数据服务的过程中在 **“建议的候选项”** 框中指定的建议的最大数目，引用数据服务可为一个值显示多个建议（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="9745f-145">The reference data service can display more than one suggestion, if available, for a value depending upon the maximum number of suggestions specified in the **Suggested Candidates** box during the mapping of the domain to the reference data service.</span></span> <span data-ttu-id="9745f-146">例如，为下面的美国地址显示两项建议：</span><span class="sxs-lookup"><span data-stu-id="9745f-146">For example, two suggestions are displayed for the following US address:</span></span>

     <span data-ttu-id="9745f-147">**原始值：**</span><span class="sxs-lookup"><span data-stu-id="9745f-147">**Original value:**</span></span>

    |<span data-ttu-id="9745f-148">Address Line</span><span class="sxs-lookup"><span data-stu-id="9745f-148">Address Line</span></span>|<span data-ttu-id="9745f-149">城市</span><span class="sxs-lookup"><span data-stu-id="9745f-149">City</span></span>|<span data-ttu-id="9745f-150">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="9745f-150">State</span></span>|<span data-ttu-id="9745f-151">Zip</span><span class="sxs-lookup"><span data-stu-id="9745f-151">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="9745f-152">1 msft way</span><span class="sxs-lookup"><span data-stu-id="9745f-152">1 msft way</span></span>|<span data-ttu-id="9745f-153">Redmond</span><span class="sxs-lookup"><span data-stu-id="9745f-153">Redmond</span></span>||<span data-ttu-id="9745f-154">98052</span><span class="sxs-lookup"><span data-stu-id="9745f-154">98052</span></span>|

     <span data-ttu-id="9745f-155">**建议的值：**</span><span class="sxs-lookup"><span data-stu-id="9745f-155">**Suggested values:**</span></span>

    |<span data-ttu-id="9745f-156">Address Line</span><span class="sxs-lookup"><span data-stu-id="9745f-156">Address Line</span></span>|<span data-ttu-id="9745f-157">城市</span><span class="sxs-lookup"><span data-stu-id="9745f-157">City</span></span>|<span data-ttu-id="9745f-158">州省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="9745f-158">State</span></span>|<span data-ttu-id="9745f-159">Zip</span><span class="sxs-lookup"><span data-stu-id="9745f-159">Zip</span></span>|
    |------------------|----------|-----------|---------|
    |<span data-ttu-id="9745f-160">1 Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9745f-160">1 Microsoft Way</span></span>|<span data-ttu-id="9745f-161">Redmond</span><span class="sxs-lookup"><span data-stu-id="9745f-161">Redmond</span></span>|<span data-ttu-id="9745f-162">WA</span><span class="sxs-lookup"><span data-stu-id="9745f-162">WA</span></span>|<span data-ttu-id="9745f-163">98052</span><span class="sxs-lookup"><span data-stu-id="9745f-163">98052</span></span>|
    |<span data-ttu-id="9745f-164">PO Box 1</span><span class="sxs-lookup"><span data-stu-id="9745f-164">PO Box 1</span></span>|<span data-ttu-id="9745f-165">Redmond</span><span class="sxs-lookup"><span data-stu-id="9745f-165">Redmond</span></span>|<span data-ttu-id="9745f-166">WA</span><span class="sxs-lookup"><span data-stu-id="9745f-166">WA</span></span>|<span data-ttu-id="9745f-167">98073</span><span class="sxs-lookup"><span data-stu-id="9745f-167">98073</span></span>|

     <span data-ttu-id="9745f-168">![使用参考数据服务清除](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "使用参考数据服务清除")</span><span class="sxs-lookup"><span data-stu-id="9745f-168">![Cleansing using reference data service](../../2014/data-quality-services/media/dqs-rdscleansing.JPG "Cleansing using reference data service")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9745f-169">对于复合域，DQS 还以不同的颜色突出显示计算机辅助清理过程中已更正的单独域。</span><span class="sxs-lookup"><span data-stu-id="9745f-169">For composite domains, DQS also highlights the individual domains in a different color that were corrected during the computer-assisted cleansing process.</span></span> <span data-ttu-id="9745f-170">例如，在这个示例中， **Address Line** 和 **State** 域已更正，因此以青色突出显示。</span><span class="sxs-lookup"><span data-stu-id="9745f-170">For example, in this case, the **Address Line** and **State** domains were corrected, and therefore highlighted in cyan.</span></span>

5.  <span data-ttu-id="9745f-171">在您检查完所有域值后，单击 **“下一步”** 以导出数据。</span><span class="sxs-lookup"><span data-stu-id="9745f-171">After you are done with reviewing all the domain values, click **Next** to export the data.</span></span>

6.  <span data-ttu-id="9745f-172">在 **“导出”** 页上，您将注意到除了与每个域的清理活动有关的常规信息（“源”、“原因”、“置信度”和“状态”）之外，还有 Melissa Data 引用数据服务提供的与您的地址有关的附加信息，例如您的地址的经度和维度、国家/地区名称、地址类型（多层楼房、街道等）等。</span><span class="sxs-lookup"><span data-stu-id="9745f-172">On the **Export** page, you will notice that apart from the regular information about the cleansing activity for each domain (Source, Reason, Confidence, and Status), there is additional information provided by the Melissa Data reference data service about your address data, such as latitude and longitude of your address, county name, address type (highrise, street, etc.), and so on.</span></span>

7.  <span data-ttu-id="9745f-173">将您的数据导出到所需目标（SQL Server、CSV 或 Excel），然后单击 **“完成”** 关闭该项目。</span><span class="sxs-lookup"><span data-stu-id="9745f-173">Export your data to the required destination (SQL Server, CSV, or Excel), and click **Finish** to close the project.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="9745f-174">如果您使用的是 64 位版本的 Excel，则无法将已清理的数据导出到 Excel 文件；只能导出到 SQL Server 数据库或 .csv 文件。</span><span class="sxs-lookup"><span data-stu-id="9745f-174">If you are using 64-bit version of Excel, you cannot export the cleansed data to an Excel file; you can export only to a SQL Server database or to a .csv file.</span></span>


