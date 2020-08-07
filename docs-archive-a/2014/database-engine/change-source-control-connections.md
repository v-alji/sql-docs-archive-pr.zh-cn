---
title: 更改源代码管理连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 077a09cdca0c0aff777184f04467ca39592690aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588067"
---
# <a name="change-source-control-connections"></a><span data-ttu-id="a3fd7-102">更改源代码管理连接</span><span class="sxs-lookup"><span data-stu-id="a3fd7-102">Change Source Control Connections</span></span>
  <span data-ttu-id="a3fd7-103">第一次从源代码管理中添加或打开解决方案时，源代码管理提供程序会在本地解决方案目录的根文件夹与对应的服务器文件夹之间创建一个关联。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-103">The first time you add or open a solution from source control, your source control provider creates an association between the root folder of the local solution directory and its corresponding server folder.</span></span>  
  
 <span data-ttu-id="a3fd7-104">根文件夹（还称为统一根）位于客户端。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-104">The root folder (also called unified root) resides on the client.</span></span> <span data-ttu-id="a3fd7-105">由解决方案或项目引用的所有文件均可在此文件夹下找到。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-105">It is the folder beneath which all the files referenced by a solution or project can be found.</span></span> <span data-ttu-id="a3fd7-106">若要找到解决方案的最新版本、历史记录及其状态信息，请找到驻留在源代码管理服务器上的服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-106">To find the latest version of a solution, its history, and its status information, locate the server folder, which resides on the source control server.</span></span> <span data-ttu-id="a3fd7-107">在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe 中，服务器文件夹被称为项目。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-107">In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, server folders are called projects.</span></span>  
  
 <span data-ttu-id="a3fd7-108">多数情况下，需要将解决方案与其服务器文件夹解除绑定或断开连接。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-108">In many situations, you need to unbind or disconnect a solution from its server folder.</span></span> <span data-ttu-id="a3fd7-109">例如，如果您的源代码管理提供程序所在的计算机无法使用，则可以连接到备份计算机，将解决方案重新绑定到备份的服务器文件夹，然后继续正常工作。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-109">For example, if the computer on which your source control provider resides is unavailable, you can connect to a backup computer, rebind your solution to a backed-up server folder, and resume working normally.</span></span> <span data-ttu-id="a3fd7-110">而且，如果源代码管理项目是派生的，则可能需要将解决方案绑定到新项目版本所在的服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-110">Also, if a source control project is forked, you may have to bind your solution to the server folder where the new project version resides.</span></span>  
  
 <span data-ttu-id="a3fd7-111">使用源代码管理提供程序的用户界面来更改与解决方案绑定的服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-111">Use the user interface of the source control provider to change the server folder that a solution is bound to.</span></span> <span data-ttu-id="a3fd7-112">可以从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 环境内打开源代码管理用户界面。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-112">You can open the source control user interface from within the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span>  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a><span data-ttu-id="a3fd7-113">从 Studio 环境中打开源代码管理用户界面</span><span class="sxs-lookup"><span data-stu-id="a3fd7-113">To open the source control user interface from the Studio environment</span></span>  
  
1.  <span data-ttu-id="a3fd7-114">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**启动 Microsoft Visual SourceSafe**"。</span><span class="sxs-lookup"><span data-stu-id="a3fd7-114">On the **File** menu, point to **Source Control**, and then click **Launch Microsoft Visual SourceSafe**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fd7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3fd7-115">See Also</span></span>  
 <span data-ttu-id="a3fd7-116">[源代码管理基础知识](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="a3fd7-116">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="a3fd7-117">[设置源代码管理选项](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="a3fd7-117">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="a3fd7-118">从源代码管理中排除文件</span><span class="sxs-lookup"><span data-stu-id="a3fd7-118">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
