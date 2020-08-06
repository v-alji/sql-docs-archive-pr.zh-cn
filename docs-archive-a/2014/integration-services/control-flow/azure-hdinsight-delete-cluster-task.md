---
title: Azure HDInsight 删除群集任务 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: db0a15aaea37c6d18c1d3c2136e0fd0c94eb7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589832"
---
# <a name="azure-hdinsight-delete-cluster-task"></a><span data-ttu-id="28c3c-102">Azure HDInsight 删除群集任务</span><span class="sxs-lookup"><span data-stu-id="28c3c-102">Azure HDInsight Delete Cluster Task</span></span>
<span data-ttu-id="28c3c-103">Azure HDInsight 删除群集任务启用一个 SSIS 包来删除指定的 Azure 订阅和资源组中的一个 Azure HDInsight 群集  。</span><span class="sxs-lookup"><span data-stu-id="28c3c-103">The **Azure HDInsight Delete Cluster Task** enables an SSIS package to delete an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]
> <span data-ttu-id="28c3c-104">删除 HDInsight 群集可能需要 10~20 分钟。</span><span class="sxs-lookup"><span data-stu-id="28c3c-104">Deleting an HDInsight cluster may take 10~20 minutes.</span></span>  
  
<span data-ttu-id="28c3c-105">若要添加 **Azure HDInsight 删除群集任务**，可将其拖放到 SSIS 设计器，然后双击或右键单击“编辑”， \*\*\*\* 以查看以下 **Azure Blob 删除群集任务编辑器** 对话框。</span><span class="sxs-lookup"><span data-stu-id="28c3c-105">To add an **Azure HDInsight Delete Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Delete Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="28c3c-106">下表提供了此对话框中的字段说明。</span><span class="sxs-lookup"><span data-stu-id="28c3c-106">The following table provides a description for the fields in the dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28c3c-107">**字段**</span><span class="sxs-lookup"><span data-stu-id="28c3c-107">**Field**</span></span>|<span data-ttu-id="28c3c-108">**说明**</span><span class="sxs-lookup"><span data-stu-id="28c3c-108">**Description**</span></span>|  
|<span data-ttu-id="28c3c-109">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="28c3c-109">AzureResourceManagerConnection</span></span>|<span data-ttu-id="28c3c-110">选择一个现有 Azure 资源管理器连接管理器，或创建一个用于删除 HDInsight 群集的新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="28c3c-110">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to delete the HDInsight cluster.</span></span>|
|<span data-ttu-id="28c3c-111">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="28c3c-111">SubscriptionId</span></span>|<span data-ttu-id="28c3c-112">指定 HDInsight 群集所在的订阅的 ID。</span><span class="sxs-lookup"><span data-stu-id="28c3c-112">Specify the ID of the subscription the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="28c3c-113">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="28c3c-113">ResourceGroup</span></span>|<span data-ttu-id="28c3c-114">指定 HDInsight 群集所在的 Azure 资源组。</span><span class="sxs-lookup"><span data-stu-id="28c3c-114">Specify the Azure resource group the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="28c3c-115">ClusterName</span><span class="sxs-lookup"><span data-stu-id="28c3c-115">ClusterName</span></span>|<span data-ttu-id="28c3c-116">指定要删除的群集的名称。</span><span class="sxs-lookup"><span data-stu-id="28c3c-116">Specify the name of the cluster to be deleted.</span></span>|  
|<span data-ttu-id="28c3c-117">FailIfNotExists</span><span class="sxs-lookup"><span data-stu-id="28c3c-117">FailIfNotExists</span></span>|<span data-ttu-id="28c3c-118">指定如果群集不存在时任务是否会失败。</span><span class="sxs-lookup"><span data-stu-id="28c3c-118">Specify whether the task should fail if the cluster does not exist.</span></span>|
