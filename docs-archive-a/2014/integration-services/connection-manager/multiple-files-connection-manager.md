---
title: 多文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ebd45aa4f0794d98be6a79125bf1874913d491
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589835"
---
# <a name="multiple-files-connection-manager"></a><span data-ttu-id="d4ae0-102">多文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="d4ae0-102">Multiple Files Connection Manager</span></span>
  <span data-ttu-id="d4ae0-103">多文件连接管理器使包可以在运行时引用现有的文件和文件夹，或者创建文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-103">A Multiple Files connection manager enables a package to reference existing files and folders, or to create files and folders at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4ae0-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的内置任务和数据流组件不使用多文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-104">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="d4ae0-105">但是，可以在脚本任务或脚本组件中使用此连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-105">However, you can use this connection manager in the Script task or Script component.</span></span> <span data-ttu-id="d4ae0-106">有关如何在脚本任务中使用连接管理器的信息，请参阅 [在脚本任务中连接数据源](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-106">For information about how to use connection managers in the Script task, see [Connecting to Data Sources in the Script Task](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md).</span></span> <span data-ttu-id="d4ae0-107">有关如何在脚本组件中使用连接管理器的信息，请参阅 [连接到脚本组件中的数据源] (。/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="d4ae0-107">For information about how to use connection managers in the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span></span>  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a><span data-ttu-id="d4ae0-108">多文件连接管理器的使用类型</span><span class="sxs-lookup"><span data-stu-id="d4ae0-108">Usage Types of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="d4ae0-109">多文件连接管理器的 `FileUsageType` 属性指定如何使用连接。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-109">The `FileUsageType` property of the Multiple Files connection manager specifies how the connection is used.</span></span> <span data-ttu-id="d4ae0-110">多文件连接管理器可以创建文件、创建文件夹、使用现有文件以及使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-110">The Multiple Files connection manager can create files, create folders, use existing files, and use existing folders.</span></span>  
  
 <span data-ttu-id="d4ae0-111">下表列出了 `FileUsageType` 的值。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-111">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="d4ae0-112">值</span><span class="sxs-lookup"><span data-stu-id="d4ae0-112">Value</span></span>|<span data-ttu-id="d4ae0-113">说明</span><span class="sxs-lookup"><span data-stu-id="d4ae0-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4ae0-114">**0**</span><span class="sxs-lookup"><span data-stu-id="d4ae0-114">**0**</span></span>|<span data-ttu-id="d4ae0-115">多文件连接管理器使用现有文件。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-115">Multiple Files connection manager uses an existing file.</span></span>|  
|<span data-ttu-id="d4ae0-116">**1**</span><span class="sxs-lookup"><span data-stu-id="d4ae0-116">**1**</span></span>|<span data-ttu-id="d4ae0-117">多文件连接管理器创建文件。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-117">Multiple Files connection manager creates a file.</span></span>|  
|<span data-ttu-id="d4ae0-118">**2**</span><span class="sxs-lookup"><span data-stu-id="d4ae0-118">**2**</span></span>|<span data-ttu-id="d4ae0-119">多文件连接管理器使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-119">Multiple Files connection manager uses an existing folder.</span></span>|  
|<span data-ttu-id="d4ae0-120">**3**</span><span class="sxs-lookup"><span data-stu-id="d4ae0-120">**3**</span></span>|<span data-ttu-id="d4ae0-121">多文件连接管理器创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-121">Multiple Files connection manager creates a folder.</span></span>|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a><span data-ttu-id="d4ae0-122">多文件连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="d4ae0-122">Configuration of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="d4ae0-123">向包中添加多文件连接管理器时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定多文件连接的连接管理器，设置多文件连接属性，并将多文件连接添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-123">When you add a Multiple Files connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Files connection at run time, sets the Multiple Files connection properties, and adds the Multiple Files connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="d4ae0-124">该连接管理器的 `ConnectionManagerType` 属性设置为 `MULTIFILE`。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-124">The `ConnectionManagerType` property of the connection manager is set to `MULTIFILE`.</span></span>  
  
 <span data-ttu-id="d4ae0-125">可以按以下方法配置多文件连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d4ae0-125">You can configure a Multiple Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="d4ae0-126">指定文件和文件夹的使用类型。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-126">Specify the usage type of files and folders.</span></span>  
  
-   <span data-ttu-id="d4ae0-127">指定文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-127">Specify files and folders.</span></span>  
  
-   <span data-ttu-id="d4ae0-128">如果使用多个文件或文件夹，指定访问文件和文件夹的顺序。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-128">If using multiple files or folders, specify the order in which the files and folders are accessed.</span></span>  
  
 <span data-ttu-id="d4ae0-129">如果多文件连接管理器引用了多个文件和文件夹，那么文件和文件夹的路径应由竖线 (|) 分开。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-129">If the Multiple Files connection manager references multiple files and folders, the paths of the files and folders are separated by the pipe (|) character.</span></span> <span data-ttu-id="d4ae0-130">连接管理器的 `ConnectionString` 属性的格式如下：</span><span class="sxs-lookup"><span data-stu-id="d4ae0-130">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="d4ae0-131">也可以用通配符指定多个文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-131">You can also specify multiple files or folders using wildcard characters.</span></span> <span data-ttu-id="d4ae0-132">例如，若要引用 C 驱动器上的所有文本文件， `ConnectionString` 可以将属性的值设置为 c： \\ \* .txt。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-132">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="d4ae0-133">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d4ae0-134">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [“添加文件连接管理器”对话框 UI 参考](add-file-connection-manager-dialog-box-ui-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add File Connection Manager Dialog Box UI Reference](add-file-connection-manager-dialog-box-ui-reference.md).</span></span>  
  
 <span data-ttu-id="d4ae0-135">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="d4ae0-135">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
