---
title: Azure HDInsight Hive 任务 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afphivetask.f1
- sql11.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5905dee4a7a195a16d217b28b59cc10bb74dd9a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589830"
---
# <a name="azure-hdinsight-hive-task"></a><span data-ttu-id="e0e76-102">Azure HDInsight Hive 任务</span><span class="sxs-lookup"><span data-stu-id="e0e76-102">Azure HDInsight Hive Task</span></span>
<span data-ttu-id="e0e76-103">使用“Azure HDInsight Hive 任务”  在 Azure HDInsight 群集上运行 Hive 脚本。</span><span class="sxs-lookup"><span data-stu-id="e0e76-103">Use the **Azure HDInsight Hive Task** to run Hive script on an Azure HDInsight cluster.</span></span>
     
<span data-ttu-id="e0e76-104">若要添加“Azure HDInsight Hive 任务”  ，可将其拖放到 SSIS 设计器，然后双击或右键单击“编辑”  ，以查看以下“Azure HDInsight Hive 任务编辑器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="e0e76-104">To add an **Azure HDInsight Hive Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Hive Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e0e76-105">以下列表介绍了此对话框中的字段。</span><span class="sxs-lookup"><span data-stu-id="e0e76-105">The following list describes fields in this dialog box.</span></span>  
  
1.  <span data-ttu-id="e0e76-106">对于 HDInsightConnection 字段，请选择一个现有 Azure HDInsight 连接管理器，或创建一个新的连接管理器，引用用于执行脚本的 Azure HDInsight 群集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-106">For the **HDInsightConnection** field, select an existing Azure HDInsight Connection Manager or create a new one that refers to the Azure HDInsight cluster used to execute the script.</span></span>
  
2.  <span data-ttu-id="e0e76-107">对于 AzureStorageConnection 字段，请选择一个现有 Azure 存储连接管理器，或创建一个新的连接管理器，引用与群集关联的 Azure 存储帐户\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-107">For the **AzureStorageConnection** field, select an existing Azure Storage Connection Manager or create a new one that refers to the Azure Storage Account associated with the cluster.</span></span> <span data-ttu-id="e0e76-108">只有在需要下载脚本执行输出和错误日志时，才需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e0e76-108">This is only necessary if you want to download the script execution output and error logs.</span></span>
 
3.  <span data-ttu-id="e0e76-109">对于 BlobContainer 字段，指定与群集关联的存储容器名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-109">For the **BlobContainer** field, specify the storage container name associated with the cluster.</span></span> <span data-ttu-id="e0e76-110">只有在需要下载脚本执行输出和错误日志时，才需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e0e76-110">This is only necessary if you want to download the script execution output and error logs.</span></span>
  
4.  <span data-ttu-id="e0e76-111">对于 LocalLogFolder 字段，指定脚本执行输出和错误日志要下载到的文件夹\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-111">For the **LocalLogFolder** field, specify the folder to which the script execution output and error logs will be downloaded to.</span></span> <span data-ttu-id="e0e76-112">只有在需要下载脚本执行输出和错误日志时，才需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="e0e76-112">This is only necessary if you want to download the script execution output and error logs.</span></span>   
  
5.  <span data-ttu-id="e0e76-113">可通过两种方法指定要执行的 Hive 脚本：</span><span class="sxs-lookup"><span data-stu-id="e0e76-113">There are two ways to specify the Hive script to execute:</span></span>
  
    1.  <span data-ttu-id="e0e76-114">**内联脚本**：通过在“输入脚本”对话框中键入要执行的内联脚本来指定“脚本”字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-114">**In-line script**: Specify the **Script** field by typing in-line the script to execute in the **Enter Script** dialog box.</span></span>
  
    2.  <span data-ttu-id="e0e76-115">**脚本文件**：将脚本文件上传到 Azure Blob 存储，并指定 BlobName 字段\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-115">**Script file**: Upload the script file to Azure Blob Storage and specify the **BlobName** field.</span></span> <span data-ttu-id="e0e76-116">如果该 blob 不在默认存储帐户或与 HDInsight 群集关联的容器中，则必须指定 ExternalStorageAccountName 和 ExternalBlobContainer 字段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0e76-116">If the blob is not in the default storage account or container associated with the HDInsight cluster, the **ExternalStorageAccountName** and **ExternalBlobContainer** fields must be specified.</span></span> <span data-ttu-id="e0e76-117">对于外部 blob，请确保它已配置为可公开访问。</span><span class="sxs-lookup"><span data-stu-id="e0e76-117">For an external blob, make sure that it is configured as publicly accessible.</span></span>  
  
     <span data-ttu-id="e0e76-118">如果同时指定两者，则使用脚本文件并忽略内联脚本。</span><span class="sxs-lookup"><span data-stu-id="e0e76-118">If both are specified, script file will be used and the in-line script will be ignored.</span></span>
