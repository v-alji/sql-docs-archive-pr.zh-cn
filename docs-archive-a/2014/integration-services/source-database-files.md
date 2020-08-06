---
title: 源数据库文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31f0c0e0c633ead0c093bdc8e1f20c9b8f23cc28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694009"
---
# <a name="source-database-files"></a><span data-ttu-id="4bb21-102">源数据库文件</span><span class="sxs-lookup"><span data-stu-id="4bb21-102">Source database files</span></span>
  <span data-ttu-id="4bb21-103">可以使用 **“源数据库文件”** 对话框查看源服务器上的数据库文件的名称和位置，或者为传输数据库任务指定网络文件共享位置。</span><span class="sxs-lookup"><span data-stu-id="4bb21-103">Use the **Source Database Files** dialog box to view the database file names and locations on the source server, or to specify a network file share location for the Transfer Database task.</span></span> <span data-ttu-id="4bb21-104">有关此任务的详细信息，请参阅 [传输数据库任务](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="4bb21-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="4bb21-105">若要使用源服务器上数据库文件的名称和位置填充此对话框，请首先在 **“传输数据库任务编辑器”** 对话框的 **“数据库”** 页中指定 **SourceConnection** 和 **SourceDatabaseName** 。</span><span class="sxs-lookup"><span data-stu-id="4bb21-105">To populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection** and **SourceDatabaseName** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4bb21-106">选项</span><span class="sxs-lookup"><span data-stu-id="4bb21-106">Options</span></span>  
 <span data-ttu-id="4bb21-107">**源文件**</span><span class="sxs-lookup"><span data-stu-id="4bb21-107">**Source File**</span></span>  
 <span data-ttu-id="4bb21-108">源服务器上要传输的数据库文件的名称。</span><span class="sxs-lookup"><span data-stu-id="4bb21-108">Database file names on the source server that will be transferred.</span></span> <span data-ttu-id="4bb21-109">**“源文件”** 是只读的。</span><span class="sxs-lookup"><span data-stu-id="4bb21-109">**Source File** is read only.</span></span>  
  
 <span data-ttu-id="4bb21-110">**源文件夹**</span><span class="sxs-lookup"><span data-stu-id="4bb21-110">**Source Folder**</span></span>  
 <span data-ttu-id="4bb21-111">源服务器上包含要传输的数据库文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4bb21-111">Folder on the source server where the database files to be transferred reside.</span></span> <span data-ttu-id="4bb21-112">**“源文件夹”** 是只读的。</span><span class="sxs-lookup"><span data-stu-id="4bb21-112">**Source Folder** is read only.</span></span>  
  
 <span data-ttu-id="4bb21-113">**网络文件共享**</span><span class="sxs-lookup"><span data-stu-id="4bb21-113">**Network File Share**</span></span>  
 <span data-ttu-id="4bb21-114">源服务器上要从中传输数据库文件的网络共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="4bb21-114">Network shared folder on the source server from where the database files will be transferred.</span></span> <span data-ttu-id="4bb21-115">通过在 **“传输数据库任务编辑器”** 对话框的 **“数据库”** 页中为 **“方法”** 指定 **DatabaseOffline** 以脱机模式传输数据库时，可以使用 **“网络文件共享”** 。</span><span class="sxs-lookup"><span data-stu-id="4bb21-115">Use **Network File Share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="4bb21-116">输入网络文件共享位置，或单击浏览按钮“(…)”可查找网络文件共享位置  。</span><span class="sxs-lookup"><span data-stu-id="4bb21-116">Enter the network file share location, or click the browse button **(...)** to locate the network file share location.</span></span>  
  
 <span data-ttu-id="4bb21-117">以脱机模式传输数据库时，数据库文件在传输到目标服务器之前将被复制到源服务器上的 **“网络文件共享”** 位置。</span><span class="sxs-lookup"><span data-stu-id="4bb21-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location on the source server before they are transferred to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb21-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bb21-118">See Also</span></span>  
 <span data-ttu-id="4bb21-119">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4bb21-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4bb21-120">[传输数据库任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="4bb21-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="4bb21-121">传输数据库任务编辑器（“数据库”页）</span><span class="sxs-lookup"><span data-stu-id="4bb21-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
