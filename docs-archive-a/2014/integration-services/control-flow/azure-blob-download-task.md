---
title: Azure Blob 下载任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2f61260b1fceaad3c27a0ce6ab6af28b15582bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688116"
---
# <a name="azure-blob-download-task"></a><span data-ttu-id="1a8b3-102">Azure Blob 下载任务</span><span class="sxs-lookup"><span data-stu-id="1a8b3-102">Azure Blob Download Task</span></span>
  <span data-ttu-id="1a8b3-103">Azure Blob 下载任务启用了一个 SSIS 包来从 Azure blob 存储区下载文件。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-103">The Azure Blob Download Task enables an SSIS package to download files from an Azure blob storage.</span></span>   
<span data-ttu-id="1a8b3-104">若要添加 **Azure Blob 下载任务**，可将其拖放到 SSIS 设计器，然后双击或右键单击“编辑”，以查看以下“Azure Blob 下载任务编辑器”对话框   。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-104">To add an **Azure Blob Download Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Download Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1a8b3-105">下表提供了此对话框中的字段说明。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-105">The following table provides description for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a8b3-106">**字段**</span><span class="sxs-lookup"><span data-stu-id="1a8b3-106">**Field**</span></span>|<span data-ttu-id="1a8b3-107">**说明**</span><span class="sxs-lookup"><span data-stu-id="1a8b3-107">**Description**</span></span>|  
|<span data-ttu-id="1a8b3-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="1a8b3-108">AzureStorageConnection</span></span>|<span data-ttu-id="1a8b3-109">选择一个现有的 Azure 存储连接管理器或创建一个新的连接管理器，用于引用指向在其中托管 blob 文件的 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="1a8b3-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="1a8b3-110">BlobContainer</span></span>|<span data-ttu-id="1a8b3-111">指定包含要下载的 blob 文件的 blob 容器的名称。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-111">Specifies the name of the blob container that contains the blob files to be downloaded.</span></span>|  
|<span data-ttu-id="1a8b3-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="1a8b3-112">BlobDirectory</span></span>|<span data-ttu-id="1a8b3-113">指定包含要下载的 blob 文件的 blob 目录。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-113">Specifies the blob directory that contains the blob files to be downloaded.</span></span> <span data-ttu-id="1a8b3-114">该 blob 目录是一个虚拟层次结构。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-114">The blob directory is a virtual hierarchical structure.</span></span>|  
|<span data-ttu-id="1a8b3-115">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="1a8b3-115">LocalDirectory</span></span>|<span data-ttu-id="1a8b3-116">指定将在其中存储下载的 blob 文件的本地目录。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-116">Specifies the local directory where the downloaded blob files will be stored.</span></span>|  
|<span data-ttu-id="1a8b3-117">FileName</span><span class="sxs-lookup"><span data-stu-id="1a8b3-117">FileName</span></span>|<span data-ttu-id="1a8b3-118">指定名称筛选器以选择具有指定名称模式的文件。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-118">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="1a8b3-119">例如</span><span class="sxs-lookup"><span data-stu-id="1a8b3-119">E.g.</span></span> <span data-ttu-id="1a8b3-120">MySheet\*.xls\* 包括如 MySheet001.xls 和 MySheetABC.xlsx 等文件。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-120">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="1a8b3-121">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="1a8b3-121">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="1a8b3-122">指定时间范围筛选器。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-122">Specifies a time range filter.</span></span> <span data-ttu-id="1a8b3-123">包括介于 **TimeRangeFrom** 和 **TimeRangeTo** 之间修改的文件。</span><span class="sxs-lookup"><span data-stu-id="1a8b3-123">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
