---
title: DQS 中的 Reference Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4ed286b5834d81f775ee097672bfbc861c0b369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586987"
---
# <a name="reference-data-services-in-dqs"></a><span data-ttu-id="1c1f1-102">DQS 中的 Reference Data Services</span><span class="sxs-lookup"><span data-stu-id="1c1f1-102">Reference Data Services in DQS</span></span>
  <span data-ttu-id="1c1f1-103">引用数据指的是可信公共域或高级商业内容提供程序中提供的一组准确和完整的相关或分类全局数据（超越企业的界限）。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-103">Reference data refers to an accurate and complete set of related or categorized global data (beyond the boundaries of an enterprise) that is available at trusted public domains or from premium commercial content providers.</span></span>  
  
 <span data-ttu-id="1c1f1-104">通过 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 中的“引用数据服务”功能，您可以订阅第三方引用数据提供程序，通过对照其高质量数据进行验证以轻松地清理和丰富您的业务数据。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-104">The Reference Data Service feature in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) enables you to subscribe to third-party reference data providers, and to easily cleanse and enrich your business data by validating it against their high-quality data.</span></span> <span data-ttu-id="1c1f1-105">您可以使用 DQS 内领先的数据质量服务提供程序的服务在清理过程中对数据执行标准化、更正数据或使数据更为丰富。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-105">You can use services from leading data quality service providers from within DQS to standardize, correct, or enrich your data during the cleansing process.</span></span> <span data-ttu-id="1c1f1-106">例如，您可以使用区号或邮政编码列表对照引用数据来验证您的客户的地址。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-106">For example, you can use a list of area codes or zip codes against the reference data to validate addresses of your customers.</span></span>  
  
 <span data-ttu-id="1c1f1-107">“引用数据服务”功能具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="1c1f1-107">The Reference Data Service feature has the following benefits:</span></span>  
  
-   <span data-ttu-id="1c1f1-108">借助引用数据，您可以通过将您的数据与第三方公司保证的数据进行比较来确保您数据的质量。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-108">Reference data enables you to ensure the quality of your data by comparing it to data guaranteed by a third-party company.</span></span>  
  
-   <span data-ttu-id="1c1f1-109">引用数据过程合并到 DQS 知识库生成和数据质量项目中，这使您可以建立全面的数据质量过程。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-109">The reference data process is incorporated into DQS knowledge base building and a data quality project, enabling you to institute a comprehensive data quality process.</span></span>  
  
-   <span data-ttu-id="1c1f1-110">支持使用来自 Azure Marketplace 的引用数据，以及直接来自第三方引用数据提供程序的引用数据。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-110">Supports using reference data from Azure Marketplace as well as directly from third party reference data providers.</span></span>  
  
##  <a name="using-reference-data-from-azure-marketplace"></a><a name="Marketplace"></a><span data-ttu-id="1c1f1-111">使用 Azure Marketplace 中的引用数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-111">Using Reference Data from Azure Marketplace</span></span>  
 <span data-ttu-id="1c1f1-112">DQS 支持使用来自 Azure Marketplace 的引用数据，使内容提供程序能够通过 Marketplace 提供引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-112">DQS supports using reference data from Azure Marketplace to enable content providers to provide reference data services through Marketplace.</span></span> <span data-ttu-id="1c1f1-113">Marketplace 是 Microsoft 的一项服务，它为高质量数据和应用程序提供单一市场和交付渠道来作为云服务。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-113">Marketplace is a service from Microsoft that provides a single marketplace and delivery channel for high-quality data and applications as cloud services.</span></span> <span data-ttu-id="1c1f1-114">有关 Marketplace 的详细信息，请参阅[了解 Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/)。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-114">For more information about Marketplace, see [Learn About Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/).</span></span>  
  
 <span data-ttu-id="1c1f1-115">市场和 DQS 之间的无缝集成简化了与从 DQS 中发现、浏览和获取数据质量项目的信息相关的步骤。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-115">The seamless integration between Marketplace and DQS simplifies the steps associated with discovering, exploring, and acquiring information for data quality projects from within DQS.</span></span> <span data-ttu-id="1c1f1-116">从 DQS 中使用数据，并通过使用一种创新方法将 DQS、市场和引用数据服务提供程序结合起来，帮助 DQS 用户获得高数据质量。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-116">The data is consumed from DQS, and helps DQS users achieve high data quality by bringing together DQS, Marketplace, and reference data service providers in an innovative way.</span></span>  
  
 <span data-ttu-id="1c1f1-117">若要在 DQS 中使用来自市场的引用数据执行清理活动，必须具有市场帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-117">To use reference data from Marketplace in DQS for the cleansing activity, you must have a Marketplace account key.</span></span> <span data-ttu-id="1c1f1-118">创建市场帐户密钥是免费的，仅当您订阅付费数据集时才需要付费。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-118">Creating a Marketplace account key is free, and you pay only if you subscribe to paid datasets.</span></span> <span data-ttu-id="1c1f1-119">订阅和使用免费数据集都不需要付费。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-119">There is no charge for subscribing to, and using free datasets.</span></span> <span data-ttu-id="1c1f1-120">有关创建 Marketplace 帐户密钥的详细信息，请参阅[创建帐户](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-120">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span>  
  
 <span data-ttu-id="1c1f1-121">此外，还可以从 DQS 中执行以下市场活动：</span><span class="sxs-lookup"><span data-stu-id="1c1f1-121">Additionally, you can perform the following Marketplace activities from within DQS:</span></span>  
  
-   <span data-ttu-id="1c1f1-122">浏览市场中的数据集。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-122">Browse data sets in Marketplace.</span></span>  
  
-   <span data-ttu-id="1c1f1-123">创建市场帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-123">Create a Marketplace account key.</span></span>  
  
-   <span data-ttu-id="1c1f1-124">管理您的市场帐户详细信息，如针对数据提供程序的帐户密钥和订阅。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-124">Manage your Marketplace account details such as account keys and subscriptions to data providers.</span></span>  
  
 <span data-ttu-id="1c1f1-125">您可以在 **的** “配置” **屏幕的** “引用数据” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]选项卡中执行这些活动。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-125">You can perform these activities in the **Reference Data** tab of the **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
##  <a name="using-reference-data-directly-from-the-third-party-reference-data-providers"></a><a name="Direct"></a> <span data-ttu-id="1c1f1-126">使用直接来自第三方引用数据提供程序的引用数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-126">Using Reference Data Directly from the Third Party Reference Data Providers</span></span>  
 <span data-ttu-id="1c1f1-127">如果没有连接到 Internet 并由此无法使用市场，DQS 也支持直接连接到组织的网络中提供的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-127">If you are not connected to the Internet and therefore cannot use Marketplace, DQS also supports direct connection to data providers that are available within your organization's network.</span></span> <span data-ttu-id="1c1f1-128">若要使用来自直接联机第三方引用数据提供程序的引用数据，您必须在 DQS 中为此数据提供程序创建一条记录。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-128">To use reference data from direct online third-party reference data providers, you have to create a record for the data provider in DQS.</span></span>  
  
##  <a name="how-to-cleanse-data-by-using-the-reference-data"></a><a name="HowToCleanse"></a> <span data-ttu-id="1c1f1-129">如何使用引用数据清理数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-129">How to Cleanse Data by Using the Reference Data</span></span>  
 <span data-ttu-id="1c1f1-130">在 DQS 中使用引用数据清理您的数据包括以下这些步骤：</span><span class="sxs-lookup"><span data-stu-id="1c1f1-130">Cleansing your data in DQS using reference data includes the following three steps:</span></span>  
  
1.  <span data-ttu-id="1c1f1-131">**在 DQS 中配置引用数据提供程序详细信息**：您必须在 DQS 中配置引用数据服务详细信息，才能在 DQS 中使用引用数据。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-131">**Configuring the reference data provider details in DQS**: Before you can use reference data in DQS, you must configure reference data service details in DQS.</span></span>  
  
    1.  <span data-ttu-id="1c1f1-132">如果您正在使用市场，则提供一个有效的市场帐户密钥，浏览至市场中的 [Data Quality Services](../data-quality-services/data-quality-services.md) 数据类别，并订阅所需的提供程序。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-132">If you are using Marketplace, provide a valid Marketplace account key, browse to the [Data Quality Services](../data-quality-services/data-quality-services.md) data category in Marketplace, and subscribe to the required providers.</span></span>  
  
    2.  <span data-ttu-id="1c1f1-133">如果您正在使用直接联机引用数据提供程序，则在使用之前，必须在 DQS 中添加直接引用数据提供程序详细信息。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-133">If you are using a direct online reference data provider, you must add direct reference data provider details in DQS before you can use it.</span></span>  
  
     <span data-ttu-id="1c1f1-134">对于特定数据提供程序，在 DQS 中配置引用数据提供程序详细信息是一个一次性活动。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-134">Configuring the reference data provider details in DQS is one time activity for a particular data provider.</span></span> <span data-ttu-id="1c1f1-135">在 DQS 中，只有 DQS 管理员才能配置引用数据设置。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-135">Only DQS administrators can configure reference data settings in DQS.</span></span>  
  
2.  <span data-ttu-id="1c1f1-136">**将知识库中的域/复合域映射到引用数据服务**：将域/复合域映射到在步骤 1 中订阅/添加的相应引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-136">**Map a domain/composite domain in a knowledge base to the reference data service**: Map a domain/composite domain to the appropriate reference data service subscribed/added in step 1.</span></span>  
  
3.  <span data-ttu-id="1c1f1-137">**使用映射域在数据质量项目中进行清理活动**：在为 **“清理”** 活动创建数据质量项目时，选择包含在步骤 2 中映射到引用数据服务的域/复合域的知识库，然后执行清理活动。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-137">**Use the Mapped Domains for the Cleansing activity in a data quality project**: While creating a data quality project for the **Cleansing** activity, select the knowledge base that contains domains/composite domains mapped with reference data services in step 2, and perform the cleansing activity.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1c1f1-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1c1f1-138">Related Tasks</span></span>  
  
|<span data-ttu-id="1c1f1-139">任务说明</span><span class="sxs-lookup"><span data-stu-id="1c1f1-139">Task Description</span></span>|<span data-ttu-id="1c1f1-140">主题</span><span class="sxs-lookup"><span data-stu-id="1c1f1-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1c1f1-141">介绍如何配置 DQS 以使用来自 市场或直接第三方联机数据提供程序的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-141">Describes how to configure DQS to use reference data services from Marketplace or direct third-party online data providers.</span></span>|[<span data-ttu-id="1c1f1-142">将 DQS 配置为使用引用数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-142">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="1c1f1-143">介绍如何将知识库中的域/复合域映射到引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-143">Describes how to map a domain/composite domain in a knowledge base to a reference data service.</span></span>|[<span data-ttu-id="1c1f1-144">将域或复合域附加到参考数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-144">Attach a Domain or Composite Domain to Reference Data</span></span>](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|<span data-ttu-id="1c1f1-145">介绍如何使用引用数据服务清理数据。</span><span class="sxs-lookup"><span data-stu-id="1c1f1-145">Describes how to cleanse data using reference data service.</span></span>|[<span data-ttu-id="1c1f1-146">使用引用数据（外部）知识清理数据</span><span class="sxs-lookup"><span data-stu-id="1c1f1-146">Cleanse Data Using Reference Data &#40;External&#41; Knowledge</span></span>](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
