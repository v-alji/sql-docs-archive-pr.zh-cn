---
title: 报表生成器中的报表部件和数据集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fe86481-9c41-4535-a4b7-c7c4d780cab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ad592561fa8d1ee7a57bc83eb89d9aec1ba6f6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694266"
---
# <a name="report-parts-and-datasets-in-report-builder"></a><span data-ttu-id="2eb28-102">报表生成器中的报表部件和数据集</span><span class="sxs-lookup"><span data-stu-id="2eb28-102">Report Parts and Datasets in Report Builder</span></span>
  <span data-ttu-id="2eb28-103">在报表生成器中，在报表中包含数据的最简单方式是从报表部件库添加报表部件。</span><span class="sxs-lookup"><span data-stu-id="2eb28-103">In Report Builder, the easiest way to include data in a report is to add report parts from the Report Part Gallery.</span></span> <span data-ttu-id="2eb28-104">报表部件包含它们所依赖的数据集，这些数据集称为 *相关数据集*。</span><span class="sxs-lookup"><span data-stu-id="2eb28-104">Report parts contain the datasets that they depend on, which are known as *dependent datasets*.</span></span> <span data-ttu-id="2eb28-105">相关数据集基于共享数据源，并且可以是嵌入数据集或共享数据集。</span><span class="sxs-lookup"><span data-stu-id="2eb28-105">Dependent datasets are based on shared data sources and can be either embedded datasets or shared datasets.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="2eb28-106">在报表中包含数据的另一种简单的方式是使用一个共享数据集。</span><span class="sxs-lookup"><span data-stu-id="2eb28-106">Another easy way to include data in a report is to use a shared dataset.</span></span> <span data-ttu-id="2eb28-107">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb28-107">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-report-part-with-dependent-datasets-to-your-report"></a><a name="Adding"></a><span data-ttu-id="2eb28-108">向报表添加具有相关数据集的报表部件</span><span class="sxs-lookup"><span data-stu-id="2eb28-108">Adding a Report Part with Dependent Datasets to Your Report</span></span>  
 <span data-ttu-id="2eb28-109">在向您的报表中添加报表部件时，该部件所包含的相关数据集也添加到您的报表中。</span><span class="sxs-lookup"><span data-stu-id="2eb28-109">When you add a report part to your report, the dependent datasets that it contains are also added to your report.</span></span> <span data-ttu-id="2eb28-110">因为报告部件可以包括含有许多其他报表项的矩形，所以，它可以将多个相关数据集添加到报表中。</span><span class="sxs-lookup"><span data-stu-id="2eb28-110">Because a report part might include a rectangle that contains many other report items, it can add multiple dependent datasets to your report.</span></span> <span data-ttu-id="2eb28-111">每个共享数据集都是一个独立的引用；它依赖的共享数据源不会添加到报表中。</span><span class="sxs-lookup"><span data-stu-id="2eb28-111">Each shared dataset is an independent reference; the shared data source that it depends on is not added to your report.</span></span> <span data-ttu-id="2eb28-112">每个嵌入数据集也添加它所依赖的嵌入数据源或共享数据源。</span><span class="sxs-lookup"><span data-stu-id="2eb28-112">Each embedded dataset also adds the embedded or shared data source that it depends on.</span></span>  
  
 <span data-ttu-id="2eb28-113">嵌入数据源的凭据不作为报表部件的一部分保存。</span><span class="sxs-lookup"><span data-stu-id="2eb28-113">The credentials for an embedded data source are not saved as part of the report part.</span></span> <span data-ttu-id="2eb28-114">如果某一嵌入数据源添加到您的报表中，则在运行该报表时系统将提示您输入凭据。</span><span class="sxs-lookup"><span data-stu-id="2eb28-114">If an embedded data source is added to your report, you will be prompted for credentials when you run the report.</span></span> <span data-ttu-id="2eb28-115">若要避免提示输入凭据，使用的报表部件应基于具有存储的凭据的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="2eb28-115">To avoid being prompted for credentials, use report parts that are based on shared data sources with stored credentials.</span></span>  
  
 <span data-ttu-id="2eb28-116">在向报表添加报表部件后，添加的数据集与您创建的嵌入数据集或共享数据集没有什么不同。</span><span class="sxs-lookup"><span data-stu-id="2eb28-116">After you add a report part to your report, the added datasets are no different than embedded or shared datasets that you create.</span></span> <span data-ttu-id="2eb28-117">您可以在“报表数据”窗格中查看其他数据集。</span><span class="sxs-lookup"><span data-stu-id="2eb28-117">You can view the additional datasets in the Report Data pane.</span></span> <span data-ttu-id="2eb28-118">嵌入数据集将出现在相应的共享数据源之下，共享数据集将出现在“共享数据集”文件夹之下。</span><span class="sxs-lookup"><span data-stu-id="2eb28-118">Embedded datasets appear under the corresponding shared data source and shared datasets appear under the Shared Datasets folder.</span></span>  
  
  
##  <a name="customizing-dependent-datasets"></a><a name="Customizing"></a><span data-ttu-id="2eb28-119">自定义从属数据集</span><span class="sxs-lookup"><span data-stu-id="2eb28-119">Customizing Dependent Datasets</span></span>  
 <span data-ttu-id="2eb28-120">在向报表添加报表部件后，您可以预览它并决定是否对数据进行某些更改。</span><span class="sxs-lookup"><span data-stu-id="2eb28-120">After you add report parts to your report, you might preview it and decide to make some changes to the data.</span></span> <span data-ttu-id="2eb28-121">您能够进行的更改取决于您正在处理的数据集的类型。</span><span class="sxs-lookup"><span data-stu-id="2eb28-121">What you can change depends on the type of dataset that you are working with.</span></span>  
  
 <span data-ttu-id="2eb28-122">若要更改某一嵌入数据集的数据和数据选项，您可以编辑包括查询在内的数据集属性，就像您自己创建了该数据集一样。</span><span class="sxs-lookup"><span data-stu-id="2eb28-122">To change data and data options for an embedded dataset, you can edit the dataset properties, including the query, just as if you had created the dataset yourself.</span></span>  
  
 <span data-ttu-id="2eb28-123">若要更改共享数据集的数据和数据选项，您只能在您具有足够权限的报表服务器上更改共享数据集定义。</span><span class="sxs-lookup"><span data-stu-id="2eb28-123">To change a data and data options for a shared dataset, you can change the shared dataset definition on the report server only you have sufficient permissions.</span></span> <span data-ttu-id="2eb28-124">您还可以通过添加筛选器、添加计算字段以及更改诸如区分大小写之类的数据选项，自定义您的报表中共享数据集的实例。</span><span class="sxs-lookup"><span data-stu-id="2eb28-124">You can also customize the instance of the shared dataset in your report by adding filters, adding calculated fields, and changing data options such as case sensitivity.</span></span> <span data-ttu-id="2eb28-125">有关详细信息，请参阅[嵌入数据集和共享数据集（报表生成器和 SSRS）](embedded-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb28-125">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="2eb28-126">有关如何更改共享数据集的定义或者如何在报表中显示共享数据集的最新数据更改的详细信息，请参阅[创建共享数据集或嵌入数据集（报表生成器和 SSRS）](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)和[在“报表数据”窗格中添加、编辑和刷新字段（报表生成器和 SSRS）](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb28-126">For more information about how to change the definition of a shared dataset or how to show the latest data changes for a shared dataset in your report, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) and [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
  
##  <a name="publishing-dependent-datasets-as-shared-datasets"></a><a name="Publishing"></a> <span data-ttu-id="2eb28-127">将相关数据集作为共享数据集发布</span><span class="sxs-lookup"><span data-stu-id="2eb28-127">Publishing Dependent Datasets as Shared Datasets</span></span>  
 <span data-ttu-id="2eb28-128">当您发布具有相关数据集的报表项时，可以选择将每个数据集作为共享数据集发布，或者作为保持嵌入在报表项中的嵌入数据集发布。</span><span class="sxs-lookup"><span data-stu-id="2eb28-128">When you publish a report item that has dependent datasets, you have the option to publish each dataset as a shared dataset or as an embedded dataset that remains embedded in the report item.</span></span>  
  
 <span data-ttu-id="2eb28-129">在您选择共享数据集选项时，该数据集将作为共享数据集定义保存到报表服务器中。</span><span class="sxs-lookup"><span data-stu-id="2eb28-129">When you select the shared dataset option, the dataset is saved to the report server as a shared dataset definition.</span></span> <span data-ttu-id="2eb28-130">在您的报表中，使用该数据集的每个报表项都更新为指向现在位于报表服务器上的共享数据集。</span><span class="sxs-lookup"><span data-stu-id="2eb28-130">In your report, every report item that uses that dataset is updated to point to the shared dataset that is now on the report server.</span></span> <span data-ttu-id="2eb28-131">因此将发生以下两种情况：</span><span class="sxs-lookup"><span data-stu-id="2eb28-131">Two things happen as a result:</span></span>  
  
1.  <span data-ttu-id="2eb28-132">在“发布”对话框中，已发布的每个共享数据集均从可供发布的项的列表中删除。</span><span class="sxs-lookup"><span data-stu-id="2eb28-132">In the Publish dialog box, each shared dataset that has been published is removed from the list of items that are available to publish.</span></span>  
  
2.  <span data-ttu-id="2eb28-133">当您退出报表生成器或启动一个新报表时，系统将提示您保存您的报表。</span><span class="sxs-lookup"><span data-stu-id="2eb28-133">When you exit Report Builder or start a new report, you are prompted to save your report.</span></span> <span data-ttu-id="2eb28-134">如果您没有保存您的报表，则在下次打开此报表并发布报表项时，可能会发布相同数据集的新副本。</span><span class="sxs-lookup"><span data-stu-id="2eb28-134">If you do not save your report, the next time you open this report and publish report items, you might publish new copies of the same datasets.</span></span> <span data-ttu-id="2eb28-135">为了避免共享数据集的多个副本保存到报表服务器上，我们建议您保存该报表。</span><span class="sxs-lookup"><span data-stu-id="2eb28-135">To prevent saving multiple copies of shared datasets to the report server, we recommend that you save the report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2eb28-136">为了确保您和他人能够继续成功地使用来自共享数据集的数据，您必须理解确保报表项的安全所基于的原理。</span><span class="sxs-lookup"><span data-stu-id="2eb28-136">To ensure that you and others can continue to successfully use data from a shared dataset, you must understand the principles behind securing report items.</span></span> <span data-ttu-id="2eb28-137">有关详细信息，请参阅 [保护共享数据集项](../security/secure-shared-dataset-items.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb28-137">For more information, see [Secure Shared Dataset Items](../security/secure-shared-dataset-items.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="2eb28-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2eb28-138">See Also</span></span>  
 <span data-ttu-id="2eb28-139">[报表设计视图 &#40;报表生成器&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2eb28-139">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="2eb28-140">[安全 &#40;报表生成器&#41;](../report-builder/security-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2eb28-140">[Security &#40;Report Builder&#41;](../report-builder/security-report-builder.md) </span></span>  
 <span data-ttu-id="2eb28-141">[报表部件 &#40;报表生成器和 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2eb28-141">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2eb28-142">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2eb28-142">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
