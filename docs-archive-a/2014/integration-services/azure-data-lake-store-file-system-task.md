---
title: Azure Data Lake Store 文件系统任务 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bc37e774c5346190635e50259deb47f2f22a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587995"
---
# <a name="azure-data-lake-store-file-system-task"></a><span data-ttu-id="83d16-102">Azure Data Lake Store 文件系统任务</span><span class="sxs-lookup"><span data-stu-id="83d16-102">Azure Data Lake Store File System Task</span></span>

<span data-ttu-id="83d16-103">**Azure Data Lake Store 文件系统任务**使用户能够在[Azure Data Lake Store (ADLS) ](https://azure.microsoft.com/services/data-lake-store/)上执行各种文件系统操作。</span><span class="sxs-lookup"><span data-stu-id="83d16-103">The **Azure Data Lake Store File System Task** enables users to perform various file system operations on [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).</span></span>

<span data-ttu-id="83d16-104">若要将 Azure Data Lake Store 文件系统任务添加到某个包，请将它从 SSIS 工具箱拖到设计器画布中。</span><span class="sxs-lookup"><span data-stu-id="83d16-104">To add an Azure Data Lake Store File System Task to a package, drag it from SSIS Toolbox to the designer canvas.</span></span> <span data-ttu-id="83d16-105">然后双击该任务，或右键单击该任务，然后选择 "**编辑**"，以打开 "任务编辑器" 对话框。</span><span class="sxs-lookup"><span data-stu-id="83d16-105">Then double-click the task, or right-click the task and select **Edit**, to open the task editor dialog box.</span></span>

<span data-ttu-id="83d16-106">“操作”\*\*\*\* 属性指定要执行的文件系统操作。</span><span class="sxs-lookup"><span data-stu-id="83d16-106">The **Operation** property specifies the file system operation to perform.</span></span> <span data-ttu-id="83d16-107">支持下列操作:</span><span class="sxs-lookup"><span data-stu-id="83d16-107">The following operations are supported.</span></span>

* <span data-ttu-id="83d16-108">**CopyToADLS：** 将文件上载到 ADLS。</span><span class="sxs-lookup"><span data-stu-id="83d16-108">**CopyToADLS:** Upload files to ADLS.</span></span>
* <span data-ttu-id="83d16-109">**CopyFromADLS：** 从 ADLS 下载文件。</span><span class="sxs-lookup"><span data-stu-id="83d16-109">**CopyFromADLS:** Download files from ADLS.</span></span>

<span data-ttu-id="83d16-110">对任何操作都必须指定 Azure Data Lake 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="83d16-110">For any operation, you have to specify an Azure Data Lake connection manager.</span></span>

<span data-ttu-id="83d16-111">下面是特定于每个操作的属性的说明。</span><span class="sxs-lookup"><span data-stu-id="83d16-111">Here are the descriptions of the properties specific to each operation.</span></span>

## <a name="copytoadls"></a><span data-ttu-id="83d16-112">CopyToADLS</span><span class="sxs-lookup"><span data-stu-id="83d16-112">CopyToADLS</span></span>

* <span data-ttu-id="83d16-113">**LocalDirectory：** 指定包含要上载的文件的源目录。</span><span class="sxs-lookup"><span data-stu-id="83d16-113">**LocalDirectory:** Specifies the source directory which contains files to upload.</span></span>
* <span data-ttu-id="83d16-114">**FileNamePattern：** 指定源文件的文件名筛选器。</span><span class="sxs-lookup"><span data-stu-id="83d16-114">**FileNamePattern:** Specifies a file name filter for source files.</span></span> <span data-ttu-id="83d16-115">仅上传名称与指定模式匹配的文件。</span><span class="sxs-lookup"><span data-stu-id="83d16-115">Only files whose name matches the specified pattern will be uploaded.</span></span> <span data-ttu-id="83d16-116">支持 `*` 和 `?` 通配符。</span><span class="sxs-lookup"><span data-stu-id="83d16-116">Wildcards `*` and `?` are supported.</span></span>
* <span data-ttu-id="83d16-117">**SearchRecursively：** 指定是否在源目录中以递归方式搜索要上载的文件。</span><span class="sxs-lookup"><span data-stu-id="83d16-117">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to upload.</span></span>
* <span data-ttu-id="83d16-118">**AzureDataLakeDirectory：** 指定要将文件上载到的 ADLS 目标目录。</span><span class="sxs-lookup"><span data-stu-id="83d16-118">**AzureDataLakeDirectory:** Specifies the ADLS destination directory to upload files to.</span></span>
* <span data-ttu-id="83d16-119">**FileExpiry：** 为上载到 ADLS 的文件指定过期日期和时间，或将此属性保留为空，以指示文件永不过期。</span><span class="sxs-lookup"><span data-stu-id="83d16-119">**FileExpiry:** Specifies an expiration date and time for the files uploaded to ADLS, or leave this property blank to indicate that the files never expire.</span></span>

## <a name="copyfromadls"></a><span data-ttu-id="83d16-120">CopyFromADLS</span><span class="sxs-lookup"><span data-stu-id="83d16-120">CopyFromADLS</span></span>

* <span data-ttu-id="83d16-121">**AzureDataLakeDirectory：** 指定包含待下载文件的 ADLS 源目录。</span><span class="sxs-lookup"><span data-stu-id="83d16-121">**AzureDataLakeDirectory:** Specifies the ADLS source directory which contains the files to download.</span></span>
* <span data-ttu-id="83d16-122">**SearchRecursively：** 指定是否在源目录中以递归方式搜索要下载的文件。</span><span class="sxs-lookup"><span data-stu-id="83d16-122">**SearchRecursively:** Specifies whether to search recursively within the source directory for files to download.</span></span>
* <span data-ttu-id="83d16-123">**LocalDirectory：** 指定要存储已下载文件的目标目录。</span><span class="sxs-lookup"><span data-stu-id="83d16-123">**LocalDirectory:** Specifies the destination directory to store downloaded files.</span></span>
