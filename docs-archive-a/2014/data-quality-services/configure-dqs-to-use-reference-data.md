---
title: 将 DQS 配置为使用引用数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.rds.f1
- sql12.dqs.administration.rdsconfiguration.f1
- sql12.dqs.administration.configuration.createDirectRDS.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 670e984c2afabb70dece75d94701d7a3a03c95bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683076"
---
# <a name="configure-dqs-to-use-reference-data"></a><span data-ttu-id="b987c-102">将 DQS 配置为使用引用数据</span><span class="sxs-lookup"><span data-stu-id="b987c-102">Configure DQS to Use Reference Data</span></span>
  <span data-ttu-id="b987c-103">本主题介绍如何将 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 配置为使用引用数据来清理您的数据。</span><span class="sxs-lookup"><span data-stu-id="b987c-103">This topic describes how to configure [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data for cleansing your data.</span></span> <span data-ttu-id="b987c-104">你可以使用来自 Azure Marketplace 的引用数据，也可以使用来自直接联机第三方引用数据提供程序的引用数据。</span><span class="sxs-lookup"><span data-stu-id="b987c-104">You could either use reference data from Azure Marketplace or from direct online third-party reference data providers.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b987c-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="b987c-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="b987c-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="b987c-106">Prerequisites</span></span>  
 <span data-ttu-id="b987c-107">若要使用来自市场的引用数据，您必须具有有效的市场帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="b987c-107">To use reference data from Marketplace, you must have a valid Marketplace account key.</span></span> <span data-ttu-id="b987c-108">有关创建 Marketplace 帐户密钥的详细信息，请参阅[创建帐户](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="b987c-108">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span> <span data-ttu-id="b987c-109">还可以通过单击 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中 **“管理”** 下的 **“配置”** ，然后单击 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] “引用数据” **选项卡下的** “创建 DataMarket 帐户 ID” **，在** 中创建市场帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="b987c-109">You can also create a Marketplace account key from within [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] by clicking **Configuration** under **Administration** in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, and then clicking **Create a DataMarket Account ID** under the **Reference Data** tab.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b987c-110">Security</span><span class="sxs-lookup"><span data-stu-id="b987c-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b987c-111">权限</span><span class="sxs-lookup"><span data-stu-id="b987c-111">Permissions</span></span>  
 <span data-ttu-id="b987c-112">您必须具有 DQS_MAIN 数据库的 dqs_administrator 角色，才能在 DQS 中配置引用数据服务设置。</span><span class="sxs-lookup"><span data-stu-id="b987c-112">You must have the dqs_administrator role on the DQS_MAIN database to configure reference data service settings in DQS.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> <span data-ttu-id="b987c-113">将 DQS 配置为使用来自市场的引用数据</span><span class="sxs-lookup"><span data-stu-id="b987c-113">Configure DQS to Use Reference Data from Marketplace</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="b987c-114">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b987c-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="b987c-115">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中的 **“管理”** 下，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="b987c-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="b987c-116">如果您的组织使用代理服务器连接到 Internet，则在 **“引用数据”** 选项卡中的 **“网络设置”** 区域下，在 **“代理服务器”** 和 **“端口”** 框中键入适当的值。</span><span class="sxs-lookup"><span data-stu-id="b987c-116">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="b987c-117">在 **“DataMarket 帐户 ID”** 框中指定市场帐户密钥，然后单击 **“验证 DataMarket 帐户 ID”** 图标以验证该帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="b987c-117">Specify the Marketplace account key in the **DataMarket Account ID** box, and click the **Validate DataMarket Account ID** icon to validate the account key.</span></span> <span data-ttu-id="b987c-118">系统将显示一条消息，以显示指定的市场帐户密钥是否有效。</span><span class="sxs-lookup"><span data-stu-id="b987c-118">A message appears to display whether the specified Marketplace account key is valid.</span></span>  
  
 <span data-ttu-id="b987c-119">您现在可以在 DQS 中使用为指定的市场帐户密钥订阅的来自市场的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="b987c-119">You are now ready to use the reference data services from Marketplace in DQS that are subscribed for the specified Marketplace account key.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a><span data-ttu-id="b987c-120">将 DQS 配置为使用来自直接联机第三方引用数据提供程序的引用数据</span><span class="sxs-lookup"><span data-stu-id="b987c-120">Configure DQS to Use Reference Data from Direct Online Third-Party Reference Data Providers</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="b987c-121">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b987c-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="b987c-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中的 **“管理”** 下，单击 **“配置”**。</span><span class="sxs-lookup"><span data-stu-id="b987c-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="b987c-123">如果您的组织使用代理服务器连接到 Internet，则在 **“引用数据”** 选项卡中的 **“网络设置”** 区域下，在 **“代理服务器”** 和 **“端口”** 框中键入适当的值。</span><span class="sxs-lookup"><span data-stu-id="b987c-123">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="b987c-124">在 **“直接联机第三方引用数据服务设置”** 区域中，单击 **“添加新的引用数据服务提供程序”** 图标。</span><span class="sxs-lookup"><span data-stu-id="b987c-124">In the **Direct Online 3rd Party Reference Data Service Settings** area, click the **Add new reference data service provider** icon.</span></span>  
  
5.  <span data-ttu-id="b987c-125">在 **“创建新的直接联机第三方引用数据服务提供程序”** 对话框中，指定以下详细信息：</span><span class="sxs-lookup"><span data-stu-id="b987c-125">In the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box, specify the following details:</span></span>  
  
    1.  <span data-ttu-id="b987c-126">在 **“名称”** 框中，键入新的直接引用数据服务提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="b987c-126">In the **Name** box, type a name of the new direct reference data service provider.</span></span>  
  
    2.  <span data-ttu-id="b987c-127">（可选）在 **“说明”** 框中，键入新的直接引用数据服务提供程序的说明。</span><span class="sxs-lookup"><span data-stu-id="b987c-127">(Optional) In the **Description** box, type a description of the new direct reference data service provider.</span></span>  
  
    3.  <span data-ttu-id="b987c-128">在 **“类别”** 框中，键入新的直接引用数据服务提供程序提供的数据类别。</span><span class="sxs-lookup"><span data-stu-id="b987c-128">In the **Category** box, type the category of the data provided by the new direct reference data service provider.</span></span>  
  
    4.  <span data-ttu-id="b987c-129">在“架构”框中，指定一个架构，此架构定义要从直接引用数据服务提供程序中使用的字段（列名称）的字符串。</span><span class="sxs-lookup"><span data-stu-id="b987c-129">In the Schema box, specify the schema that defines the string of fields (column names) to be used from the direct reference data service provider.</span></span> <span data-ttu-id="b987c-130">字段名称不能包含空格，且字段应该用逗号进行分隔。</span><span class="sxs-lookup"><span data-stu-id="b987c-130">A field name should not contain a space, and the fields should be separated by commas.</span></span> <span data-ttu-id="b987c-131">例如： `FirstName, LastName, City, State`。</span><span class="sxs-lookup"><span data-stu-id="b987c-131">For example: `FirstName, LastName, City, State`.</span></span>  
  
    5.  <span data-ttu-id="b987c-132">在 **URI** 框中，键入直接引用数据服务提供程序的 URI。</span><span class="sxs-lookup"><span data-stu-id="b987c-132">In the **URI** box, type the URI of the direct reference data service provider.</span></span> <span data-ttu-id="b987c-133">DQS 中仅允许安全 URI（地址以 “https://” 开头）。</span><span class="sxs-lookup"><span data-stu-id="b987c-133">Only secure URIs (address starting with "https://") are allowed in DQS.</span></span>  
  
    6.  <span data-ttu-id="b987c-134">在 **“最大批处理大小”** 框中，键入将发送到引用数据服务提供程序以执行清理的每批的最大记录数。</span><span class="sxs-lookup"><span data-stu-id="b987c-134">In the **Max Batch Size** box, type the maximum number of records per batch that will be sent to the reference data service provider for cleansing.</span></span> <span data-ttu-id="b987c-135">可为清理活动指定每批最多 100 条记录。</span><span class="sxs-lookup"><span data-stu-id="b987c-135">A maximum of 100 records per batch can be specified for the cleansing activity.</span></span>  
  
    7.  <span data-ttu-id="b987c-136">在 **“帐户 ID”** 框中，键入订阅引用数据服务提供程序的用户的帐户 ID。</span><span class="sxs-lookup"><span data-stu-id="b987c-136">In the **Account ID** box, type the account ID of the subscriber with the reference data service provider.</span></span>  
  
6.  <span data-ttu-id="b987c-137">单击 **“确定”** 以保存该数据，然后关闭 **“创建新的直接联机第三方引用数据服务提供程序”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b987c-137">Click **OK** to save the data, and close the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box.</span></span> <span data-ttu-id="b987c-138">新添加的直接联机第三方引用数据提供程序将可用于 DQS 的 **“直接引用数据服务提供程序”** 网格中。</span><span class="sxs-lookup"><span data-stu-id="b987c-138">The newly added direct online third party reference data provider becomes available in the **Direct Reference Data Service Providers Grid** in DQS.</span></span>  
  
 <span data-ttu-id="b987c-139">您现在可以在 DQS 中使用新配置的直接联机第三方引用数据服务提供程序提供的引用数据服务。</span><span class="sxs-lookup"><span data-stu-id="b987c-139">You are now ready to use the reference data services from the newly configured direct online third-party reference data service provider in DQS.</span></span>  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a><span data-ttu-id="b987c-140">跟进：在将 DQS 配置为使用引用数据后</span><span class="sxs-lookup"><span data-stu-id="b987c-140">Follow Up: After Configuring DQS to use Reference Data</span></span>  
 <span data-ttu-id="b987c-141">现在您必须将所需的知识库域映射到您刚配置的数据提供程序所提供的引用数据。</span><span class="sxs-lookup"><span data-stu-id="b987c-141">You must now map the required knowledge base domains to the reference data available from the data providers you just configured.</span></span> <span data-ttu-id="b987c-142">为此，请参阅[将域或复合域附加到引用数据](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b987c-142">To do so, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
  
