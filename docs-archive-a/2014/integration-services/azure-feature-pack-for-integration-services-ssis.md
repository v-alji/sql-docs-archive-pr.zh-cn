---
title: Azure 功能包 |Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bca2b4d3ce91f6010fbe01da836efd8a67ca6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683037"
---
# <a name="azure-feature-pack"></a><span data-ttu-id="a68e6-102">Azure 功能包</span><span class="sxs-lookup"><span data-stu-id="a68e6-102">Azure Feature Pack</span></span>
<span data-ttu-id="a68e6-103">用于 Azure 的 SQL Server Integration Services (SSIS) 功能包是一个扩展包，可为 SSIS 提供本页面上列出的组件，用于连接到 Azure 服务、在 Azure 与本地数据源之间传输数据以及处理 Azure 中存储的数据。</span><span class="sxs-lookup"><span data-stu-id="a68e6-103">SQL Server Integration Services (SSIS) Feature Pack for Azure is an extension that provides the components listed on this page for SSIS to connect to Azure services, transfer data between Azure and on-premises data sources, and process data stored in Azure.</span></span>

## <a name="components-in-the-feature-pack"></a><span data-ttu-id="a68e6-104">功能包中的组件</span><span class="sxs-lookup"><span data-stu-id="a68e6-104">Components in the Feature Pack</span></span>
  
-   <span data-ttu-id="a68e6-105">连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-105">Connection Managers</span></span>  
  
    -   [<span data-ttu-id="a68e6-106">Azure 存储连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-106">Azure Storage Connection Manager</span></span>](connection-manager/azure-storage-connection-manager.md)  
  
    -   [<span data-ttu-id="a68e6-107">Azure 订阅连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-107">Azure Subscription Connection Manager</span></span>](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [<span data-ttu-id="a68e6-108">Azure Data Lake Store 连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-108">Azure Data Lake Store Connection Manager</span></span>](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [<span data-ttu-id="a68e6-109">Azure 资源管理器连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-109">Azure Resource Manager Connection Manager</span></span>](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [<span data-ttu-id="a68e6-110">Azure HDInsight 连接管理器</span><span class="sxs-lookup"><span data-stu-id="a68e6-110">Azure HDInsight Connection Manager</span></span>](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   <span data-ttu-id="a68e6-111">任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-111">Tasks</span></span>  
  
    -   [<span data-ttu-id="a68e6-112">Azure blob 上传任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-112">Azure Blob Upload Task</span></span>](control-flow/azure-blob-upload-task.md)  
  
    -   [<span data-ttu-id="a68e6-113">Azure Blob 下载任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-113">Azure Blob Download Task</span></span>](control-flow/azure-blob-download-task.md)  
  
    -   [<span data-ttu-id="a68e6-114">Azure HDInsight Hive 任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-114">Azure HDInsight Hive Task</span></span>](control-flow/azure-hdinsight-hive-task.md)  
  
    -   <span data-ttu-id="a68e6-115">[Azure HDInsight Pig 任务](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="a68e6-115">[Azure HDInsight Pig Task](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)</span></span>
  
    -   [<span data-ttu-id="a68e6-116">Azure HDInsight 创建群集任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-116">Azure HDInsight Create Cluster Task</span></span>](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [<span data-ttu-id="a68e6-117">Azure HDInsight 删除群集任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-117">Azure HDInsight Delete Cluster Task</span></span>](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [<span data-ttu-id="a68e6-118">Azure SQL DW 上传任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-118">Azure SQL DW Upload Task</span></span>](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [<span data-ttu-id="a68e6-119">Azure Data Lake Store 文件系统任务</span><span class="sxs-lookup"><span data-stu-id="a68e6-119">Azure Data Lake Store File System Task</span></span>](control-flow/file-system-task.md)    
  
-   <span data-ttu-id="a68e6-120">数据流组件</span><span class="sxs-lookup"><span data-stu-id="a68e6-120">Data Flow Components</span></span>  
  
    -   <span data-ttu-id="a68e6-121">[Azure Blob 源](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="a68e6-121">[Azure Blob Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)</span></span>  
  
    -   [<span data-ttu-id="a68e6-122">Azure Blob 目标</span><span class="sxs-lookup"><span data-stu-id="a68e6-122">Azure Blob Destination</span></span>](data-flow/azure-blob-destination.md)  
    
    -   [<span data-ttu-id="a68e6-123">Azure Data Lake Store 源</span><span class="sxs-lookup"><span data-stu-id="a68e6-123">Azure Data Lake Store Source</span></span>](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [<span data-ttu-id="a68e6-124">Azure Data Lake Store 目标</span><span class="sxs-lookup"><span data-stu-id="a68e6-124">Azure Data Lake Store Destination</span></span>](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   <span data-ttu-id="a68e6-125">Azure Blob 枚举器 & ADLS 文件枚举器。</span><span class="sxs-lookup"><span data-stu-id="a68e6-125">Azure Blob Enumerator & ADLS File Enumerator.</span></span> <span data-ttu-id="a68e6-126">请参阅[Foreach 循环容器](control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a68e6-126">See [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 
## <a name="download-the-feature-pack"></a><span data-ttu-id="a68e6-127">下载功能包</span><span class="sxs-lookup"><span data-stu-id="a68e6-127">Download the Feature Pack</span></span>  
<span data-ttu-id="a68e6-128">下载用于 Azure 的 SQL Server Integration Services (SSIS) 功能包。</span><span class="sxs-lookup"><span data-stu-id="a68e6-128">Download the SQL Server Integration Services (SSIS) Feature Pack for Azure.</span></span>  
  
-   [<span data-ttu-id="a68e6-129">用于 Azure 的 Microsoft SQL Server 2014 Integration Services 功能包</span><span class="sxs-lookup"><span data-stu-id="a68e6-129">Microsoft SQL Server 2014 Integration Services Feature Pack for Azure</span></span>](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a><span data-ttu-id="a68e6-130">先决条件</span><span class="sxs-lookup"><span data-stu-id="a68e6-130">Prerequisites</span></span>  
<span data-ttu-id="a68e6-131">必须在安装此功能包之前安装以下系统必备组件。</span><span class="sxs-lookup"><span data-stu-id="a68e6-131">You must install the following prerequisites before installing this feature pack.</span></span>  
  
-   <span data-ttu-id="a68e6-132">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="a68e6-132">SQL Server Integration Services</span></span>  
-   <span data-ttu-id="a68e6-133">.Net Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a68e6-133">.Net Framework 4.5</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="a68e6-134">方案</span><span class="sxs-lookup"><span data-stu-id="a68e6-134">Scenarios</span></span>  
  
### <a name="big-data-processing"></a><span data-ttu-id="a68e6-135">大数据处理</span><span class="sxs-lookup"><span data-stu-id="a68e6-135">Big Data Processing</span></span>  
 <span data-ttu-id="a68e6-136">使用 Azure Connector 可完成以下大数据处理工作：</span><span class="sxs-lookup"><span data-stu-id="a68e6-136">Use Azure Connector to complete following big data processing work:</span></span>  
  
1.  <span data-ttu-id="a68e6-137">使用 Azure Blob 上载任务可将输入数据上载到 Azure Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="a68e6-137">Use the Azure Blob Upload Task to upload input data to Azure Blob Storage.</span></span>  
  
2.  <span data-ttu-id="a68e6-138">使用 Azure HDInsight 创建群集任务可创建 Azure HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="a68e6-138">Use the Azure HDInsight Create Cluster Task to create an Azure HDInsight cluster.</span></span> <span data-ttu-id="a68e6-139">如果要使用自己的群集，则此步骤是可选的。</span><span class="sxs-lookup"><span data-stu-id="a68e6-139">This step is optional if you want to use your own cluster.</span></span>  
  
3.  <span data-ttu-id="a68e6-140">使用 Azure HDInsight Hive 任务或 Azure HDInsight Pig 任务可在 Azure HDInsight 群集上调用 Pig 或 Hive 作业。</span><span class="sxs-lookup"><span data-stu-id="a68e6-140">Use the Azure HDInsight Hive Task or Azure HDInsight Pig Task to invoke a Pig or Hive job on the Azure HDInsight cluster.</span></span>  
  
4.  <span data-ttu-id="a68e6-141">使用 Azure HDInsight 删除群集任务可在使用之后删除 HDInsight 群集（如果在步骤 #2 中创建了按需 HDInsight 群集）。</span><span class="sxs-lookup"><span data-stu-id="a68e6-141">Use the Azure HDInsight Delete Cluster Task to delete the HDInsight Cluster after use if you have created an on-demand HDInsight cluster in step #2.</span></span>  
  
5.  <span data-ttu-id="a68e6-142">使用 Azure HDInsight Blob 下载任务可从 Azure Blob 存储下载 Pig/Hive 输出数据。</span><span class="sxs-lookup"><span data-stu-id="a68e6-142">Use the Azure HDInsight Blob Download Task to download the Pig/Hive output data from the Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="a68e6-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span><span class="sxs-lookup"><span data-stu-id="a68e6-143">![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "SSIS-AzureConnector-BigDataScenario")</span></span>  
  
### <a name="cloud-data-archiving"></a><span data-ttu-id="a68e6-144">云数据存档</span><span class="sxs-lookup"><span data-stu-id="a68e6-144">Cloud Data Archiving</span></span>  
 <span data-ttu-id="a68e6-145">使用 SSIS 包中的 Azure Blob 目标可将输出数据写入 Azure Blob 存储，或使用 Azure Blob 源可从 Azure Blob 存储读取数据。</span><span class="sxs-lookup"><span data-stu-id="a68e6-145">Use the Azure Blob Destination in an SSIS package to write output data to an Azure Blob Storage, or use the Azure Blob Source to read data from an Azure Blob Storage.</span></span>  
  
 <span data-ttu-id="a68e6-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span><span class="sxs-lookup"><span data-stu-id="a68e6-146">![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")</span></span>  
  
 <span data-ttu-id="a68e6-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span><span class="sxs-lookup"><span data-stu-id="a68e6-147">![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")</span></span>  
  
 <span data-ttu-id="a68e6-148">将 Foreach 循环容器与 Azure Blob 枚举器一起使用可处理多个 bob 文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="a68e6-148">And use the Foreach Loop Container with Azure Blob Enumerator to process data in multiple bob files.</span></span>  
  
 <span data-ttu-id="a68e6-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span><span class="sxs-lookup"><span data-stu-id="a68e6-149">![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")</span></span>  
  
  
