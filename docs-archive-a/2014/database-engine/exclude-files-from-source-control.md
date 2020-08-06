---
title: 从源代码管理中排除文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690044"
---
# <a name="exclude-files-from-source-control"></a><span data-ttu-id="4feda-102">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="4feda-102">Exclude Files from Source Control</span></span>
  <span data-ttu-id="4feda-103">如果正在使用的解决方案包含不需要源代码管理服务的文件，则可以使用 "**从源代码管理中排除**" 命令从源代码管理中排除文件。</span><span class="sxs-lookup"><span data-stu-id="4feda-103">If the solution you are working on contains files that do not require source control services, you can use the **Exclude from Source Control** command to exclude the file from source control.</span></span> <span data-ttu-id="4feda-104">如果执行上述操作，这些被排除的文件仍会保留在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 数据库中，但不再随项目签入或签出。</span><span class="sxs-lookup"><span data-stu-id="4feda-104">When you do this, the file remains in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database, but it is no longer checked in or out with the project.</span></span>  
  
 <span data-ttu-id="4feda-105">只应在生成的文件上使用 "**从源代码管理中排除**" 命令。</span><span class="sxs-lookup"><span data-stu-id="4feda-105">You should use the **Exclude from Source Control** command only on generated files.</span></span> <span data-ttu-id="4feda-106">生成的文件是指可以通过 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 解决方案中其他文件的内容完全重新创建的文件。</span><span class="sxs-lookup"><span data-stu-id="4feda-106">A generated file is one that can be entirely re-created by [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] based on the contents of another file in the solution.</span></span>  
  
### <a name="to-exclude-a-file-from-source-control"></a><span data-ttu-id="4feda-107">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="4feda-107">To exclude a file from source control</span></span>  
  
1.  <span data-ttu-id="4feda-108">在解决方案资源管理器中，选择要排除的文件。</span><span class="sxs-lookup"><span data-stu-id="4feda-108">In Solution Explorer, select the file to exclude.</span></span>  
  
2.  <span data-ttu-id="4feda-109">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 " **Exclude** *\<file name>* **从源代码管理中**排除"。</span><span class="sxs-lookup"><span data-stu-id="4feda-109">On the **File** menu, point to **Source Control**, and then click **Exclude** *\<file name>* **from Source Control**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4feda-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4feda-110">See Also</span></span>  
 <span data-ttu-id="4feda-111">[源代码管理基础知识](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="4feda-111">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="4feda-112">[设置源代码管理选项](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="4feda-112">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="4feda-113">更改源代码管理连接</span><span class="sxs-lookup"><span data-stu-id="4feda-113">Change Source Control Connections</span></span>](../../2014/database-engine/change-source-control-connections.md)  
  
  
