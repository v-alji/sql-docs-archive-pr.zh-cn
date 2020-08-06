---
title: 将域或复合域附加到引用数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.refdata.f1
- sql12.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d54dcb01823253eeda92cc3a576d73a45de4ef7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578468"
---
# <a name="attach-a-domain-or-composite-domain-to-reference-data"></a><span data-ttu-id="73f50-102">将域或复合域附加到参考数据</span><span class="sxs-lookup"><span data-stu-id="73f50-102">Attach a Domain or Composite Domain to Reference Data</span></span>
  <span data-ttu-id="73f50-103">本主题介绍如何将数据质量知识库中的域/复合域附加到 Azure Marketplace 中的引用数据服务，以便针对高质量引用数据生成知识。</span><span class="sxs-lookup"><span data-stu-id="73f50-103">This topic describes how to attach domains/composite domains in a data quality knowledge base to a reference data service in Azure Marketplace to build knowledge against the high-quality reference data.</span></span> <span data-ttu-id="73f50-104">每个引用数据服务包含一个架构（数据列）。</span><span class="sxs-lookup"><span data-stu-id="73f50-104">Each reference data service contains a schema (data columns).</span></span> <span data-ttu-id="73f50-105">在将域或复合域附加到引用数据服务后，必须将此附加域或所附加的复合域内的各个域映射到引用数据服务架构中的相应列。</span><span class="sxs-lookup"><span data-stu-id="73f50-105">After attaching a domain or a composite domain to a reference data service, you must map the attached domain or the individual domains within the attached composite domain to the appropriate columns in a reference data service schema.</span></span> <span data-ttu-id="73f50-106">通过将复合域附加到引用数据服务，您可以只将一个域附加到引用数据服务，然后将复合域内的各域映射到引用数据服务架构中的相应列。</span><span class="sxs-lookup"><span data-stu-id="73f50-106">Attaching a composite domain to a reference data service enables you to attach just one domain to a reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="73f50-107">当将域映射到引用数据服务架构中的列时，附加到引用数据服务的复合域会出现在域下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="73f50-107">The composite domain attached to a reference data service is available in the domains drop-down list while mapping domains to the columns in the reference data service schema.</span></span> <span data-ttu-id="73f50-108">不要将复合域映射到引用数据服务中的列；只需将复合域内的各个域映射到引用数据服务架构中的相应列。</span><span class="sxs-lookup"><span data-stu-id="73f50-108">Do not map the composite domain to a column in the reference data service schema; you must only map individual domains within a composite domain to the appropriate columns in the reference data service schema.</span></span> <span data-ttu-id="73f50-109">否则，将导致错误。</span><span class="sxs-lookup"><span data-stu-id="73f50-109">Otherwise, it will result in an error.</span></span>  
  
 <span data-ttu-id="73f50-110">如果您应该选择使用某一引用数据服务，则引用数据服务架构可能具有一个必须映射到适当域的必填列。</span><span class="sxs-lookup"><span data-stu-id="73f50-110">A reference data service schema can have a mandatory column that must be mapped with appropriate domain should you choose to use the reference data service.</span></span> <span data-ttu-id="73f50-111">引用数据架构中的必填列使用“(M)”与列名称区分开来。</span><span class="sxs-lookup"><span data-stu-id="73f50-111">The mandatory column in a reference data schema is identified with "(M)" against the column name.</span></span> <span data-ttu-id="73f50-112">例如，“AddressLine”是“Melissa Data - Address Data”中的必填架构列，而“CompanyName”是“Digital Trowel Inc. - Us companies and professional data for SQL users”中的必填架构列\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73f50-112">For example, **AddressLine** is the mandatory schema column in **Melissa Data - Address Data** and **CompanyName** is the mandatory schema column in **Digital Trowel Inc. - Us companies and professional data for SQL users**.</span></span>  
  
 <span data-ttu-id="73f50-113">在此主题中，我们将创建四个域：Address Line、City、State 和 Zip。在复合域 Address Verification 之下，将该复合域附加到 Melissa Data - Address Check 引用数据服务，然后将复合域内的各个域映射到引用数据服务架构中的相应列\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73f50-113">In this topic, we will create four domains: **Address Line**, **City**, **State**, and **Zip**, under a composite domain, **Address Verification**, attach the composite domain to the **Melissa Data - Address Check** reference data service, and then map the individual domains within the composite domain to appropriate columns in the reference data service schema.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="73f50-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="73f50-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="73f50-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="73f50-115">Prerequisites</span></span>  
 <span data-ttu-id="73f50-116">您必须配置了 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 后才能使用引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="73f50-116">You must have configured [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data services.</span></span> <span data-ttu-id="73f50-117">请参阅[将 DQS 配置为使用引用数据](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="73f50-117">See [Configure DQS to Use Reference Data](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73f50-118">Security</span><span class="sxs-lookup"><span data-stu-id="73f50-118">Security</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="73f50-119">权限</span><span class="sxs-lookup"><span data-stu-id="73f50-119">Permissions</span></span>  
 <span data-ttu-id="73f50-120">您必须具有针对 DQS_MAIN 数据库的 dqs_kb_editor 角色才能将域映射到引用数据。</span><span class="sxs-lookup"><span data-stu-id="73f50-120">You must have the dqs_kb_editor role on the DQS_MAIN database to map domains to reference data.</span></span>  
  
##  <a name="map-domains-to-reference-data-from-melissa-data"></a><a name="Map"></a><span data-ttu-id="73f50-121">将域映射到 Melissa 数据中的引用数据</span><span class="sxs-lookup"><span data-stu-id="73f50-121">Map domains to reference data from Melissa Data</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="73f50-122">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="73f50-122">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="73f50-123">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，在 **“知识库管理”** 下，单击 **“新建知识库”**。</span><span class="sxs-lookup"><span data-stu-id="73f50-123">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Knowledge Base Management**, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="73f50-124">在 **“新建知识库”** 屏幕上，为新的知识库键入名称，单击 **“域管理”** 活动，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="73f50-124">In the **New knowledge base** screen, type a name for the new knowledge base, click the **Domain Management** activity, and click **Create**.</span></span>  
  
4.  <span data-ttu-id="73f50-125">在 **“域管理”** 屏幕中，单击 **“创建域”** 图标以创建一个域。</span><span class="sxs-lookup"><span data-stu-id="73f50-125">In the **Domain Management** screen, click the **Create a domain** icon to create a domain.</span></span> <span data-ttu-id="73f50-126">创建下列四个域： **Address Line**、 **City**、 **State**和 **Zip**。</span><span class="sxs-lookup"><span data-stu-id="73f50-126">Create the following four domains: **Address Line**, **City**, **State**, and **Zip**.</span></span>  
  
5.  <span data-ttu-id="73f50-127">单击 **“创建复合域”** 图标以便创建一个复合域。</span><span class="sxs-lookup"><span data-stu-id="73f50-127">Click the **Create a composite domain** icon to create a composite domain.</span></span> <span data-ttu-id="73f50-128">在 **“创建复合域”** 对话框中，在 **“复合域名称”** 框中键入 **Address Verification** ，并且在该复合域中包括在步骤 3 中创建的所有域。</span><span class="sxs-lookup"><span data-stu-id="73f50-128">In the **Create a composite domain** dialog box, type **Address Verification** in the **Composite Domain Name** box, and include all the domains created in step 3 in the composite domain.</span></span> <span data-ttu-id="73f50-129">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="73f50-129">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="73f50-130">在左侧的 **“域”** 窗格中，通过单击 **Address Verification**选择该复合域，然后单击右侧的 **“引用数据”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="73f50-130">In the **Domain** pane on the left side, select the composite domain by clicking **Address Verification**, and then click the **Reference Data** tab on the right side.</span></span>  
  
7.  <span data-ttu-id="73f50-131">单击 **“浏览”** 图标。</span><span class="sxs-lookup"><span data-stu-id="73f50-131">Click the **Browse** icon.</span></span>  
  
8.  <span data-ttu-id="73f50-132">在 **“联机引用数据提供程序目录”** 对话框中：</span><span class="sxs-lookup"><span data-stu-id="73f50-132">In the **Online Reference Data Providers Catalog** dialog box:</span></span>  
  
    1.  <span data-ttu-id="73f50-133">在“DataMarket Data Quality Services”下，选中“Melissa Data - Address”复选框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73f50-133">Under **DataMarket Data Quality Services**, select the **Melissa Data - Address Check** box.</span></span>  
  
    2.  <span data-ttu-id="73f50-134">将 Melissa Data - Address Check 引用数据服务的列映射到适当的域（Address Line、City、State 和 Zip）。</span><span class="sxs-lookup"><span data-stu-id="73f50-134">Map the columns of the Melissa Data - Address Check reference data service with the appropriate domains (Address Line, City, State, and Zip).</span></span> <span data-ttu-id="73f50-135">您通过在 **“RDS 架构”** 列中选择某一引用数据服务列，然后在 **“域”** 列中选择适当的域，映射这些列。</span><span class="sxs-lookup"><span data-stu-id="73f50-135">You map the columns by selecting a reference data service column in the **RDS Schema** column, and then selecting the appropriate domain in the **Domain** column.</span></span> <span data-ttu-id="73f50-136">若要在表中添加更多的行，请单击 **“添加架构项”** 图标。</span><span class="sxs-lookup"><span data-stu-id="73f50-136">To add more rows in the table, click the **Add Schema Entry** icon.</span></span>  
  
    3.  <span data-ttu-id="73f50-137">单击 **“确定”** 保存更改并关闭 **“联机引用数据提供程序目录”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="73f50-137">Click **OK** to save the changes, and close the **Online Reference Data Providers Catalog** dialog box.</span></span>  
  
         <span data-ttu-id="73f50-138">![“联机引用数据访问接口目录”对话框](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "“联机引用数据访问接口目录”对话框")</span><span class="sxs-lookup"><span data-stu-id="73f50-138">![Online Reference Data Providers Catalog dialog box](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Online Reference Data Providers Catalog dialog box")</span></span>  
  
        > [!NOTE]  
        >  -   <span data-ttu-id="73f50-139">在 "**联机引用数据提供程序目录**" 对话框中， **DataMarket data Quality Services**节点将显示已在 Azure Marketplace 中订阅的所有引用数据服务提供程序。</span><span class="sxs-lookup"><span data-stu-id="73f50-139">In the **Online Reference Data Providers Catalog** dialog box, the **DataMarket Data Quality Services** node displays all the reference data service providers that you have subscribed to in Azure Marketplace.</span></span> <span data-ttu-id="73f50-140">如果您已在 DQS 中配置了直接联机第三方引用数据服务提供程序，则它们将显示在称作 **“第三方直接联机提供程序”** 的另一个节点下（现在未提供，因为没有在 DQS 中配置直接联机第三方引用数据服务提供程序）。</span><span class="sxs-lookup"><span data-stu-id="73f50-140">If you have configured direct online third-party reference data service providers in DQS, they will appear under another node called **3rd Party Direct Online Providers** (not available now as no direct online third-party reference data service providers are configured in DQS).</span></span>  
  
9. <span data-ttu-id="73f50-141">您将返回到 "**引用数据**" 选项卡。如果需要，请在 "**提供程序设置**" 区域中更改以下框中的值：</span><span class="sxs-lookup"><span data-stu-id="73f50-141">You will return to the **Reference Data** tab. In the **Provider Settings** area, change values in the following boxes, if required:</span></span>  
  
    -   <span data-ttu-id="73f50-142">**自动更正阈值**：将自动完成从其置信度高于此域值的引用数据服务进行的更正。</span><span class="sxs-lookup"><span data-stu-id="73f50-142">**Auto Correction Threshold**: Corrections from reference data service with confidence level above this threshold values will be automatically done.</span></span> <span data-ttu-id="73f50-143">以相应百分比值的小数表示形式输入一个值。</span><span class="sxs-lookup"><span data-stu-id="73f50-143">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="73f50-144">例如，对于 90% 输入 0.9。</span><span class="sxs-lookup"><span data-stu-id="73f50-144">For example, enter 0.9 for 90%.</span></span>  
  
    -   <span data-ttu-id="73f50-145">**建议的候选项**：要从引用数据服务显示的建议候选项的数目。</span><span class="sxs-lookup"><span data-stu-id="73f50-145">**Suggested Candidates**: Number of suggested candidates to display from the reference data service.</span></span>  
  
    -   <span data-ttu-id="73f50-146">**最低置信度**：将忽略来自其置信度低于该值的引用数据服务的建议。</span><span class="sxs-lookup"><span data-stu-id="73f50-146">**Min Confidence**: Suggestions from reference data service with confidence level lower than this value will be ignored.</span></span> <span data-ttu-id="73f50-147">以相应百分比值的小数表示形式输入一个值。</span><span class="sxs-lookup"><span data-stu-id="73f50-147">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="73f50-148">例如，对于 60% 输入 0.6。</span><span class="sxs-lookup"><span data-stu-id="73f50-148">For example, enter 0.6 for 60%.</span></span>  
  
10. <span data-ttu-id="73f50-149">单击 **“完成”** 将发布知识库。</span><span class="sxs-lookup"><span data-stu-id="73f50-149">Click **Finish** to publish the knowledge base.</span></span> <span data-ttu-id="73f50-150">在知识库成功发布后，将会出现一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="73f50-150">A confirmation message appears after the knowledge base is published successfully.</span></span>  
  
 <span data-ttu-id="73f50-151">现在可以将此知识库用于数据质量项目中的清理活动，以便基于 Melissa Data 通过 Azure Marketplace 提供的知识标准化和清理源数据中的美国地址。</span><span class="sxs-lookup"><span data-stu-id="73f50-151">You can now use this knowledge base for cleansing activity in a data quality project to standardize and cleanse US addresses in your source data based on the knowledge provided by Melissa Data through Azure Marketplace.</span></span>  
  
##  <a name="follow-up-after-mapping-a-domain-to-reference-data"></a><a name="FollowUp"></a><span data-ttu-id="73f50-152">跟进：在将域映射到引用数据后</span><span class="sxs-lookup"><span data-stu-id="73f50-152">Follow Up: After Mapping a Domain to Reference Data</span></span>  
 <span data-ttu-id="73f50-153">创建一个数据质量项目，然后通过将其与本主题中创建的知识库进行比较，对包含美国地址的源数据运行清理活动。</span><span class="sxs-lookup"><span data-stu-id="73f50-153">Create a data quality project, and run the cleansing activity on your source data containing US addresses by comparing it against the knowledge base created in this topic.</span></span> <span data-ttu-id="73f50-154">请参阅[使用引用数据（外部）知识清理数据](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)。</span><span class="sxs-lookup"><span data-stu-id="73f50-154">See [Cleanse Data Using Reference Data &#40;External&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f50-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73f50-155">See Also</span></span>  
 <span data-ttu-id="73f50-156">[DQS 中的引用数据服务](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="73f50-156">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 [<span data-ttu-id="73f50-157">数据清理</span><span class="sxs-lookup"><span data-stu-id="73f50-157">Data Cleansing</span></span>](../../2014/data-quality-services/data-cleansing.md)  
  
  
