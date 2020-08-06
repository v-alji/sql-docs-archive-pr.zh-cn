---
title: 目标数据库文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d0ab2c0ff39fc728afc17b59f0d4bae076e4022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590306"
---
# <a name="destination-database-files"></a><span data-ttu-id="e123d-102">目标数据库文件</span><span class="sxs-lookup"><span data-stu-id="e123d-102">Destination Database Files</span></span>
  <span data-ttu-id="e123d-103">可以使用 **“目标数据库文件”** 对话框查看或更改目标服务器上的数据库文件的名称和位置，或为传输数据库任务指定网络文件位置。</span><span class="sxs-lookup"><span data-stu-id="e123d-103">Use the **Destination Database Files** dialog box to view or change the database file names and locations on the destination server, or to specify a network file location for the Transfer Database task.</span></span> <span data-ttu-id="e123d-104">有关此任务的详细信息，请参阅 [传输数据库任务](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e123d-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="e123d-105">若要使用源服务器上数据库文件的名称和位置自动填充此对话框，请首先在 **“传输数据库任务编辑器”** 对话框的 **“数据库”** 页中指定 **SourceConnection** 、 **SourceDatabaseName** 和 **SourceDatabaseFiles** 。</span><span class="sxs-lookup"><span data-stu-id="e123d-105">To automatically populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e123d-106">选项</span><span class="sxs-lookup"><span data-stu-id="e123d-106">Options</span></span>  
 <span data-ttu-id="e123d-107">**目标文件**</span><span class="sxs-lookup"><span data-stu-id="e123d-107">**Destination File**</span></span>  
 <span data-ttu-id="e123d-108">目标服务器上作为传输目标的数据库文件的名称。</span><span class="sxs-lookup"><span data-stu-id="e123d-108">Names of the transferred database files on the destination server.</span></span>  
  
 <span data-ttu-id="e123d-109">请输入文件名，或单击文件名以编辑该名称。</span><span class="sxs-lookup"><span data-stu-id="e123d-109">Enter the file name, or click the file name to edit it.</span></span>  
  
 <span data-ttu-id="e123d-110">**目标文件夹**</span><span class="sxs-lookup"><span data-stu-id="e123d-110">**Destination Folder**</span></span>  
 <span data-ttu-id="e123d-111">数据库文件要传输到的目标服务器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e123d-111">Folder on the destination server where the database files will be transferred to.</span></span>  
  
 <span data-ttu-id="e123d-112">请输入文件夹路径，单击文件夹路径以编辑该路径，或单击“浏览”以找到数据库文件要传输到的目标服务器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e123d-112">Enter the folder path, click the folder path to edit it, or click browse to locate the folder where you want to transfer the database files on the destination server.</span></span>  
  
 <span data-ttu-id="e123d-113">**网络文件共享**</span><span class="sxs-lookup"><span data-stu-id="e123d-113">**Network File Share**</span></span>  
 <span data-ttu-id="e123d-114">数据库文件要传输到的目标服务器上的网络共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="e123d-114">Network shared folder on the destination server where the database files will be transferred to.</span></span> <span data-ttu-id="e123d-115">通过在 **“传输数据库任务编辑器”** 对话框的 **“数据库”** 页中为 **“方法”** 指定 **DatabaseOffline** 以脱机模式传输数据库时，可以使用 **“网络文件共享”** 。</span><span class="sxs-lookup"><span data-stu-id="e123d-115">Use **Network file share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e123d-116">请输入网络文件共享位置，或单击“浏览”以找到网络文件共享位置。</span><span class="sxs-lookup"><span data-stu-id="e123d-116">Enter the network file share location, or click browse to locate the network file share location.</span></span>  
  
 <span data-ttu-id="e123d-117">以脱机模式传输数据库时，数据库文件先复制到 **“网络文件共享”** 位置，然后才会传输到 **“目标文件夹”** 位置。</span><span class="sxs-lookup"><span data-stu-id="e123d-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location before they are transferred to the **Destination folder** location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e123d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e123d-118">See Also</span></span>  
 <span data-ttu-id="e123d-119">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e123d-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e123d-120">[传输数据库任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e123d-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="e123d-121">传输数据库任务编辑器（“数据库”页）</span><span class="sxs-lookup"><span data-stu-id="e123d-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
