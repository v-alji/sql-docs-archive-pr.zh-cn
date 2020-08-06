---
title: 文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cebb5438003c6b14c547d14012ff1bc1175a706d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692468"
---
# <a name="file-connection-manager"></a><span data-ttu-id="bcad2-102">文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="bcad2-102">File Connection Manager</span></span>
  <span data-ttu-id="bcad2-103">文件连接管理器使包可以在运行时引用现有的文件或文件夹，或者创建文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-103">A File connection manager enables a package to reference an existing file or folder, or to create a file or folder at run time.</span></span> <span data-ttu-id="bcad2-104">例如，您可以引用 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="bcad2-104">For example, you can reference an Excel file.</span></span> <span data-ttu-id="bcad2-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的某些组件使用文件中的信息来执行其工作。</span><span class="sxs-lookup"><span data-stu-id="bcad2-105">Certain components in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] use information in files to perform their work.</span></span> <span data-ttu-id="bcad2-106">例如，执行 SQL 任务可以引用包含该任务执行的 SQL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="bcad2-106">For example, an Execute SQL task can reference a file that contains the SQL statements that the task executes.</span></span> <span data-ttu-id="bcad2-107">其他组件对文件执行操作。</span><span class="sxs-lookup"><span data-stu-id="bcad2-107">Other components perform operations on files.</span></span> <span data-ttu-id="bcad2-108">例如，文件系统任务可以引用一个文件，以便将其复制到新的位置。</span><span class="sxs-lookup"><span data-stu-id="bcad2-108">For example, the File System task can reference a file to copy it to a new location.</span></span>  
  
## <a name="usage-types-of-the-file-connection-manager"></a><span data-ttu-id="bcad2-109">文件连接管理器的使用类型</span><span class="sxs-lookup"><span data-stu-id="bcad2-109">Usage Types of the File Connection Manager</span></span>  
 <span data-ttu-id="bcad2-110">文件连接管理器的 `FileUsageType` 属性指定如何使用文件连接。</span><span class="sxs-lookup"><span data-stu-id="bcad2-110">The `FileUsageType` property of the File connection manager specifies how the file connection is used.</span></span> <span data-ttu-id="bcad2-111">文件连接管理器可以创建文件、创建文件夹、使用现有文件或使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-111">The File connection manager can create a file, create a folder, use an existing file, or use an existing folder.</span></span>  
  
 <span data-ttu-id="bcad2-112">下表列出了 `FileUsageType` 的值。</span><span class="sxs-lookup"><span data-stu-id="bcad2-112">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="bcad2-113">值</span><span class="sxs-lookup"><span data-stu-id="bcad2-113">Value</span></span>|<span data-ttu-id="bcad2-114">说明</span><span class="sxs-lookup"><span data-stu-id="bcad2-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="bcad2-115">文件连接管理器使用现有文件。</span><span class="sxs-lookup"><span data-stu-id="bcad2-115">File connection manager uses an existing file.</span></span>|  
|`1`|<span data-ttu-id="bcad2-116">文件连接管理器创建文件。</span><span class="sxs-lookup"><span data-stu-id="bcad2-116">File connection manager creates a file.</span></span>|  
|`2`|<span data-ttu-id="bcad2-117">文件连接管理器使用现有文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-117">File connection manager uses an existing folder.</span></span>|  
|`3`|<span data-ttu-id="bcad2-118">文件连接管理器创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-118">File connection manager creates a folder.</span></span>|  
  
## <a name="multiple-file-or-folder-connections"></a><span data-ttu-id="bcad2-119">多个文件或文件夹连接</span><span class="sxs-lookup"><span data-stu-id="bcad2-119">Multiple File or Folder Connections</span></span>  
 <span data-ttu-id="bcad2-120">文件连接管理器只能引用一个文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-120">The File connection manager can reference only one file or folder.</span></span> <span data-ttu-id="bcad2-121">若要引用多个文件或文件夹，请使用多文件连接管理器，而不是文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="bcad2-121">To reference multiple files or folders, use a Multiple Files connection manager instead of a File connection manager.</span></span> <span data-ttu-id="bcad2-122">有关详细信息，请参阅 [Multiple Files Connection Manager](multiple-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="bcad2-122">For more information, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
## <a name="configuration-of-the-file-connection-manager"></a><span data-ttu-id="bcad2-123">文件连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="bcad2-123">Configuration of the File Connection Manager</span></span>  
 <span data-ttu-id="bcad2-124">将文件连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定文件连接的连接管理器，设置该文件连接的属性，并将该文件连接添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="bcad2-124">When you add a File connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a File connection at run time, sets the File connection properties, and adds the File connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="bcad2-125">该连接管理器的 `ConnectionManagerType` 属性设置为 `FILE`。</span><span class="sxs-lookup"><span data-stu-id="bcad2-125">The `ConnectionManagerType` property of the connection manager is set to `FILE`.</span></span>  
  
 <span data-ttu-id="bcad2-126">可以用下列方式配置文件连接管理器：</span><span class="sxs-lookup"><span data-stu-id="bcad2-126">You can configure a File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="bcad2-127">指定使用类型。</span><span class="sxs-lookup"><span data-stu-id="bcad2-127">Specify the usage type.</span></span>  
  
-   <span data-ttu-id="bcad2-128">指定文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="bcad2-128">Specify a file or folder.</span></span>  
  
 <span data-ttu-id="bcad2-129">通过在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的“属性”窗口中指定表达式，可以设置文件连接管理器的 ConnectionString 属性。</span><span class="sxs-lookup"><span data-stu-id="bcad2-129">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="bcad2-130">但是，为了避免在使用表达式指定文件或文件夹时出现验证错误，请在 "**文件连接管理器编辑器**" 中，为 "**文件/文件夹**" 添加文件或文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="bcad2-130">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="bcad2-131">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="bcad2-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bcad2-132">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [文件连接管理器编辑器](../file-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="bcad2-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [File Connection Manager Editor](../file-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="bcad2-133">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="bcad2-133">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
