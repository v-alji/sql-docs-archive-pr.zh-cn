---
title: Azure HDInsight 创建群集任务 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4029e3a01cbcfe04be5f2879a9b60866bfc867a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688112"
---
# <a name="azure-hdinsight-create-cluster-task"></a><span data-ttu-id="f9904-102">Azure HDInsight 创建群集任务</span><span class="sxs-lookup"><span data-stu-id="f9904-102">Azure HDInsight Create Cluster Task</span></span>
<span data-ttu-id="f9904-103">“Azure HDInsight 创建群集任务”  启用一个 SSIS 包来创建指定的 Azure 订阅和资源组中的一个 Azure HDInsight 群集。</span><span class="sxs-lookup"><span data-stu-id="f9904-103">The **Azure HDInsight Create Cluster Task** enables an SSIS package to create an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]  
> - <span data-ttu-id="f9904-104">新建 HDInsight 群集可能需要花费 10~20 分钟。</span><span class="sxs-lookup"><span data-stu-id="f9904-104">Creating a new HDInsight cluster may take 10~20 minutes.</span></span>  
> - <span data-ttu-id="f9904-105">这里存在与创建和运行 Azure HDInsight 群集相关的成本。</span><span class="sxs-lookup"><span data-stu-id="f9904-105">There is a cost associated with creating and running an Azure HDInsight cluster.</span></span> <span data-ttu-id="f9904-106">有关详细信息，请参阅 [HDInsight 定价](https://azure.microsoft.com/pricing/details/hdinsight/)。</span><span class="sxs-lookup"><span data-stu-id="f9904-106">See [HDInsight Pricing](https://azure.microsoft.com/pricing/details/hdinsight/) for details.</span></span>  
  
<span data-ttu-id="f9904-107">若要添加“Azure HDInsight 创建群集任务”\*\*\*\*，可将其拖放到 SSIS 设计器，然后双击或右键单击，再单击“编辑”\*\*\*\* 以查看以下“Azure HDInsight 创建群集任务编辑器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="f9904-107">To add an **Azure HDInsight Create Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Create Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="f9904-108">下表提供了此对话框中的字段说明。</span><span class="sxs-lookup"><span data-stu-id="f9904-108">The following table provides a description of the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9904-109">**字段**</span><span class="sxs-lookup"><span data-stu-id="f9904-109">**Field**</span></span>|<span data-ttu-id="f9904-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="f9904-110">**Description**</span></span>|  
|<span data-ttu-id="f9904-111">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="f9904-111">AzureResourceManagerConnection</span></span>|<span data-ttu-id="f9904-112">选择一个现有的 Azure 资源管理器连接管理器，或创建一个用于创建 HDInsight 群集的新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f9904-112">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to create the HDInsight cluster.</span></span>|  
|<span data-ttu-id="f9904-113">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="f9904-113">AzureStorageConnection</span></span>|<span data-ttu-id="f9904-114">选择一个现有的 Azure 存储连接管理器；或者创建一个新的连接管理器，该管理器引用将与 HDInsight 群集关联的 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="f9904-114">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account that will be associated with the HDInsight cluster.</span></span>|
|<span data-ttu-id="f9904-115">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="f9904-115">SubscriptionId</span></span>|<span data-ttu-id="f9904-116">指定将在其中创建 HDInsight 群集的订阅的 ID。</span><span class="sxs-lookup"><span data-stu-id="f9904-116">Specify the ID of the subscription the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="f9904-117">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="f9904-117">ResourceGroup</span></span>|<span data-ttu-id="f9904-118">指定将在其中创建 HDInsight 群集的 Azure 资源组。</span><span class="sxs-lookup"><span data-stu-id="f9904-118">Specify the Azure resource group the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="f9904-119">位置</span><span class="sxs-lookup"><span data-stu-id="f9904-119">Location</span></span>|<span data-ttu-id="f9904-120">指定 HDInsight 群集的位置。</span><span class="sxs-lookup"><span data-stu-id="f9904-120">Specify the location of the HDInsight cluster.</span></span> <span data-ttu-id="f9904-121">必须在与指定的 Azure 存储账户相同的位置创建群集。</span><span class="sxs-lookup"><span data-stu-id="f9904-121">The cluster must be created in the same location as the Azure Storage Account specified.</span></span>|  
|<span data-ttu-id="f9904-122">ClusterName</span><span class="sxs-lookup"><span data-stu-id="f9904-122">ClusterName</span></span>|<span data-ttu-id="f9904-123">指定要创建的 HDInsight 群集的名称。</span><span class="sxs-lookup"><span data-stu-id="f9904-123">Specify a name for the HDInsight cluster to be created.</span></span>|  
|<span data-ttu-id="f9904-124">clusterSize</span><span class="sxs-lookup"><span data-stu-id="f9904-124">ClusterSize</span></span>|<span data-ttu-id="f9904-125">指定要在群集中创建的节点数。</span><span class="sxs-lookup"><span data-stu-id="f9904-125">Specify the number of nodes to create in the cluster.</span></span>|  
|<span data-ttu-id="f9904-126">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="f9904-126">BlobContainer</span></span>|<span data-ttu-id="f9904-127">指定要与 HDInsight 群集相关联的默认存储容器的名称。</span><span class="sxs-lookup"><span data-stu-id="f9904-127">Specify the name of the default storage container to be associated with the HDInsight cluster.</span></span>|  
|<span data-ttu-id="f9904-128">UserName</span><span class="sxs-lookup"><span data-stu-id="f9904-128">UserName</span></span>|<span data-ttu-id="f9904-129">指定用于连接到 HDInsight 群集的用户名。</span><span class="sxs-lookup"><span data-stu-id="f9904-129">Specify the user name to be used for connecting to the HDInsight cluster.</span></span>|  
|<span data-ttu-id="f9904-130">密码</span><span class="sxs-lookup"><span data-stu-id="f9904-130">Password</span></span>|<span data-ttu-id="f9904-131">指定用于连接到 HDInsight 群集的密码。</span><span class="sxs-lookup"><span data-stu-id="f9904-131">Specify the password to be used for connecting to the HDInsight cluster.</span></span>|
|<span data-ttu-id="f9904-132">SshUserName</span><span class="sxs-lookup"><span data-stu-id="f9904-132">SshUserName</span></span>|<span data-ttu-id="f9904-133">指定使用 SSH 远程访问 HDInsight 群集时使用的用户名称。</span><span class="sxs-lookup"><span data-stu-id="f9904-133">Specify the user name used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="f9904-134">SshPassword</span><span class="sxs-lookup"><span data-stu-id="f9904-134">SshPassword</span></span>|<span data-ttu-id="f9904-135">指定使用 SSH 远程访问 HDInsight 群集的密码。</span><span class="sxs-lookup"><span data-stu-id="f9904-135">Specify the password used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="f9904-136">FailIfExists</span><span class="sxs-lookup"><span data-stu-id="f9904-136">FailIfExists</span></span>|<span data-ttu-id="f9904-137">指定如果群集已存在时任务是否失败。</span><span class="sxs-lookup"><span data-stu-id="f9904-137">Specify whether the task should fail if the cluster already exists.</span></span>|  
  
> [!NOTE]  
> <span data-ttu-id="f9904-138">HDInsight 群集和 Azure 存储帐户的位置必须相同。</span><span class="sxs-lookup"><span data-stu-id="f9904-138">The locations of the HDInsight cluster and the Azure Storage Account must be the same.</span></span>
