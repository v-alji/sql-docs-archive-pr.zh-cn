---
title: 使用 DQS 默认知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3261c7af28bb5710ede203d1fe27c6540286e9f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579039"
---
# <a name="using-the-dqs-default-knowledge-base"></a><span data-ttu-id="83cb4-102">使用 DQS 默认知识库</span><span class="sxs-lookup"><span data-stu-id="83cb4-102">Using the DQS Default Knowledge Base</span></span>
  <span data-ttu-id="83cb4-103">本主题介绍随 **(DQS) 一起安装的默认知识库**DQS 数据 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="83cb4-103">This topic describes the default knowledge base, **DQS Data**, which is installed with [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="83cb4-104">这是包含以下域的预先生成的默认知识库：</span><span class="sxs-lookup"><span data-stu-id="83cb4-104">This is a pre-built default knowledge base that contains the following domains:</span></span>  
  
-   <span data-ttu-id="83cb4-105">**国家/地区**：对于每个地点，包含常规的长名称（国家/地区指定的官方名称）和短名称（列表、地图等使用的通用名称）、两字母缩写形式、三字母缩写形式和三位代码。</span><span class="sxs-lookup"><span data-stu-id="83cb4-105">**Country/Region**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="83cb4-106">将前导值设置为国家/地区长名称。</span><span class="sxs-lookup"><span data-stu-id="83cb4-106">Leading value is set to the long country name.</span></span>  
  
-   <span data-ttu-id="83cb4-107">**国家/地区（三字母前导）**：对于每个地点包含常规长名称（国家/地区指定的官方名称）和短名称（列表、地图等中使用的通用名称）、两字母缩写形式、三字母缩写形式和三位代码。</span><span class="sxs-lookup"><span data-stu-id="83cb4-107">**Country/Region (three-letter leading)**: Contains the conventional long (official name as designated by the country/region) and short names (common name used in lists, on maps, and so on), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="83cb4-108">将前导值设置为国家/地区三字母缩写形式。</span><span class="sxs-lookup"><span data-stu-id="83cb4-108">Leading values is set to County three-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="83cb4-109">**国家/地区（两字母前导）**：对于每个地点，包含常规的长名称（国家/地区指定的官方名称）和短名称（列表、地图等使用的通用名称）、两字母缩写形式、三字母缩写形式和三位代码。</span><span class="sxs-lookup"><span data-stu-id="83cb4-109">**Country/Region (two-letter leading)**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="83cb4-110">将前导值设置为国家/地区两字母缩写形式。</span><span class="sxs-lookup"><span data-stu-id="83cb4-110">Leading value is set to the Country two-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="83cb4-111">**美国 - 县**：包含美国县的列表。</span><span class="sxs-lookup"><span data-stu-id="83cb4-111">**US - Counties**: Contains a list of US counties.</span></span>  
  
-   <span data-ttu-id="83cb4-112">**美国 - 姓氏**：包含 2000 年人口普查中出现 100 或更多次的姓氏列表。</span><span class="sxs-lookup"><span data-stu-id="83cb4-112">**US - Last Name**: Contains a list of last names (surnames) occurring 100 or more times in the Census 2000.</span></span>  
  
-   <span data-ttu-id="83cb4-113">**美国 - 地方**：包含2000 年人口普查中抽取的 50 个州、哥伦比亚特区和波多黎各的地方名称列表。</span><span class="sxs-lookup"><span data-stu-id="83cb4-113">**US - Places**: Contains a list of places for the 50 states, the District of Columbia, and Puerto Rico extracted from the Census 2010.</span></span>  
  
-   <span data-ttu-id="83cb4-114">**美国 - 州**：包含美国每个州的常规长（官方）名称和两字母缩写形式。</span><span class="sxs-lookup"><span data-stu-id="83cb4-114">**US - State**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="83cb4-115">将前导值设置为常规州名称。</span><span class="sxs-lookup"><span data-stu-id="83cb4-115">Leading value is set to the conventional state name.</span></span>  
  
-   <span data-ttu-id="83cb4-116">**美国 - 州（两字母标头）**：包含美国每个州的常规长（官方）名称和两字母缩写形式。</span><span class="sxs-lookup"><span data-stu-id="83cb4-116">**US - State (2-letter heading)**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="83cb4-117">将前导值设置为两字母缩写形式的州名称。</span><span class="sxs-lookup"><span data-stu-id="83cb4-117">Leading value is set to the two-letter abbreviation state name.</span></span>  
  
## <a name="using-the-default-knowledge-base"></a><span data-ttu-id="83cb4-118">使用默认知识库</span><span class="sxs-lookup"><span data-stu-id="83cb4-118">Using the Default Knowledge Base</span></span>  
 <span data-ttu-id="83cb4-119">您可以通过以下方式使用默认 DQS 知识库（DQS 数据）。</span><span class="sxs-lookup"><span data-stu-id="83cb4-119">You can use the default DQS knowledge base, DQS Data, in the following ways:</span></span>  
  
-   <span data-ttu-id="83cb4-120">使用默认知识库快速启动并运行清理数据质量项目，而不必首先在 DQS 中创建新知识库。</span><span class="sxs-lookup"><span data-stu-id="83cb4-120">Quickly start and run a cleansing data quality project using the default knowledge base without first having to create a new knowledge base in DQS.</span></span>  
  
-   <span data-ttu-id="83cb4-121">对默认知识库运行“域管理”、“知识发现”或“匹配策略”活动。</span><span class="sxs-lookup"><span data-stu-id="83cb4-121">Run the Domain Management, Knowledge Discovery, or Matching Policy activities on the default knowledge base.</span></span> <span data-ttu-id="83cb4-122">为此，请单击 **Data Quality Client Home Screen** 中的 [“打开知识库”](../../2014/data-quality-services/data-quality-client-home-screen.md)，在 **“打开知识库”** 屏幕中选择 **“DQS 数据”** 知识库，然后在 **“选择活动”** 区域中选择所需的活动。</span><span class="sxs-lookup"><span data-stu-id="83cb4-122">To do so, click **Open Knowledge Base** in the [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), select the **DQS Data** knowledge base in the **Open Knowledge Base** screen, and then select the required activity in the **Select Activity** area.</span></span> <span data-ttu-id="83cb4-123">单击“下一步”继续。</span><span class="sxs-lookup"><span data-stu-id="83cb4-123">Click **Next** to proceed.</span></span>  
  
-   <span data-ttu-id="83cb4-124">使用默认知识库创建新知识库。</span><span class="sxs-lookup"><span data-stu-id="83cb4-124">Create a new knowledge base using the default knowledge base.</span></span> <span data-ttu-id="83cb4-125">要从现有知识库创建知识库，请参阅 [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="83cb4-125">To create a knowledge base from an existing knowledge base, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).</span></span>  
  
-   <span data-ttu-id="83cb4-126">在 [Integration Services 中的 DQS 清理组件](https://go.microsoft.com/fwlink/?LinkId=238830) 和 [Master Data Services Excel 外接程序](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)中使用它。</span><span class="sxs-lookup"><span data-stu-id="83cb4-126">Use it in the [DQS Cleansing component in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) and [Master Data Services Add-in for Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cb4-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83cb4-127">See Also</span></span>  
 [<span data-ttu-id="83cb4-128">DQS 知识库和域</span><span class="sxs-lookup"><span data-stu-id="83cb4-128">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
