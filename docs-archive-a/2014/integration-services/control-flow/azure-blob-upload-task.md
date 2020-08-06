---
title: Azure Blob 上载任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ca15c5a77a2694293981121f4e5927be8ec0e1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688115"
---
# <a name="azure-blob-upload-task"></a><span data-ttu-id="c1746-102">Azure blob 上载任务</span><span class="sxs-lookup"><span data-stu-id="c1746-102">Azure Blob Upload Task</span></span>
  <span data-ttu-id="c1746-103">“Azure blob 上载任务”可让 SSIS 包将文件上载到 Azure blob 存储区中。</span><span class="sxs-lookup"><span data-stu-id="c1746-103">The Azure Blob Upload Task enables an SSIS package to upload files to an Azure blob storage.</span></span>   
<span data-ttu-id="c1746-104">若要添加“Azure blob 上传任务”  ，请将其拖放到“SSIS 设计器”中，双击或右键单击它，然后单击“编辑”  调出下面的“Azure blob 上传任务编辑器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="c1746-104">To add an **Azure Blob Upload Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure Blob Upload Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="c1746-105">下表介绍了此对话框中的各个字段。</span><span class="sxs-lookup"><span data-stu-id="c1746-105">The following table provides descriptions for the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1746-106">**字段**</span><span class="sxs-lookup"><span data-stu-id="c1746-106">**Field**</span></span>|<span data-ttu-id="c1746-107">**说明**</span><span class="sxs-lookup"><span data-stu-id="c1746-107">**Description**</span></span>|  
|<span data-ttu-id="c1746-108">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="c1746-108">AzureStorageConnection</span></span>|<span data-ttu-id="c1746-109">选择一个现有的 Azure 存储连接管理器或创建一个新的连接管理器，用于引用指向在其中托管 blob 文件的 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="c1746-109">Specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account, which points to where the blob files are hosted.</span></span>|  
|<span data-ttu-id="c1746-110">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="c1746-110">BlobContainer</span></span>|<span data-ttu-id="c1746-111">指定将上载的文件作为 blob 保留的 blob 容器的名称。</span><span class="sxs-lookup"><span data-stu-id="c1746-111">Specifies the name of the blob container that will hold the uploaded files as blobs.</span></span>|  
|<span data-ttu-id="c1746-112">BlobDirectory</span><span class="sxs-lookup"><span data-stu-id="c1746-112">BlobDirectory</span></span>|<span data-ttu-id="c1746-113">指定将上载的文件作为块 blob 存储的 blob 目录。</span><span class="sxs-lookup"><span data-stu-id="c1746-113">Specifies the blob directory where the uploaded file will be stored as a block blob.</span></span> <span data-ttu-id="c1746-114">该 blob 目录是一个虚拟层次结构。</span><span class="sxs-lookup"><span data-stu-id="c1746-114">The blob directory is a virtual hierarchical structure.</span></span> <span data-ttu-id="c1746-115">如果 blob 已存在，它会被替换。</span><span class="sxs-lookup"><span data-stu-id="c1746-115">If the blob already exists, it will be replaced.</span></span>|  
|<span data-ttu-id="c1746-116">LocalDirectory</span><span class="sxs-lookup"><span data-stu-id="c1746-116">LocalDirectory</span></span>|<span data-ttu-id="c1746-117">指定包含要上载的文件的本地目录。</span><span class="sxs-lookup"><span data-stu-id="c1746-117">Specify the local directory that contains the files to be uploaded.</span></span>|  
|<span data-ttu-id="c1746-118">FileName</span><span class="sxs-lookup"><span data-stu-id="c1746-118">FileName</span></span>|<span data-ttu-id="c1746-119">指定名称筛选器以选择具有指定名称模式的文件。</span><span class="sxs-lookup"><span data-stu-id="c1746-119">Specifies a name filter to select files with the specified name pattern.</span></span> <span data-ttu-id="c1746-120">例如</span><span class="sxs-lookup"><span data-stu-id="c1746-120">E.g.</span></span> <span data-ttu-id="c1746-121">MySheet\*.xls\* 包括如 MySheet001.xls 和 MySheetABC.xlsx 等文件。</span><span class="sxs-lookup"><span data-stu-id="c1746-121">MySheet\*.xls\* includes files such as MySheet001.xls and MySheetABC.xlsx.</span></span>|  
|<span data-ttu-id="c1746-122">TimeRangeFrom/TimeRangeTo</span><span class="sxs-lookup"><span data-stu-id="c1746-122">TimeRangeFrom/TimeRangeTo</span></span>|<span data-ttu-id="c1746-123">指定时间范围筛选器。</span><span class="sxs-lookup"><span data-stu-id="c1746-123">Specifies a time range filter.</span></span> <span data-ttu-id="c1746-124">包括介于 **TimeRangeFrom** 和 **TimeRangeTo** 之间修改的文件。</span><span class="sxs-lookup"><span data-stu-id="c1746-124">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be included.</span></span>|  
  
  
