---
title: “命令”窗口
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: rothja
ms.author: jroth
ms.openlocfilehash: c766ed5408de96b6a2305ce377f9031947618a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590151"
---
# <a name="command-window"></a><span data-ttu-id="39ca9-102">“命令”窗口</span><span class="sxs-lookup"><span data-stu-id="39ca9-102">Command Window</span></span>
  <span data-ttu-id="39ca9-103">使用“命令窗口”  可以对“[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 查询编辑器”窗口中当前所调试的代码运行命令，例如调试和编辑命令。</span><span class="sxs-lookup"><span data-stu-id="39ca9-103">Use the **CommandWindow** to run commands, such as debug and edit commands, against the code in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Query Editor window that is currently being debugged.</span></span> <span data-ttu-id="39ca9-104">只有在调试模式下才可以使用 **“命令窗口”** 。</span><span class="sxs-lookup"><span data-stu-id="39ca9-104">You must be in debug mode to use the **Command Window**.</span></span> <span data-ttu-id="39ca9-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器支持许多在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]“命令”  窗口中支持的命令。</span><span class="sxs-lookup"><span data-stu-id="39ca9-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports many of the commands that are also supported in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Command** window.</span></span> <span data-ttu-id="39ca9-106">有关详细信息，请参阅 [Visual Studio“命令”窗口](https://go.microsoft.com/fwlink/?LinkId=112007)。</span><span class="sxs-lookup"><span data-stu-id="39ca9-106">For more information, see [Visual Studio Command Window](https://go.microsoft.com/fwlink/?LinkId=112007).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="39ca9-107">任务列表</span><span class="sxs-lookup"><span data-stu-id="39ca9-107">Task List</span></span>  
 <span data-ttu-id="39ca9-108">**访问“命令”窗口**</span><span class="sxs-lookup"><span data-stu-id="39ca9-108">**To access the Command Window**</span></span>  
  
-   <span data-ttu-id="39ca9-109">在 **“调试”** 菜单中，单击 **“启动调试”** 。</span><span class="sxs-lookup"><span data-stu-id="39ca9-109">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
 <span data-ttu-id="39ca9-110">**打印变量的值**</span><span class="sxs-lookup"><span data-stu-id="39ca9-110">**To print the value of a variable**</span></span>  
  
-   <span data-ttu-id="39ca9-111">在**命令**中，键入 " \*\*Debug \<VariableName> \*\*"，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="39ca9-111">In the **CommandWindow**, type **Debug.Print \<VariableName>**, and then press ENTER.</span></span>  
  
 <span data-ttu-id="39ca9-112">**列出有关当前线程的信息**</span><span class="sxs-lookup"><span data-stu-id="39ca9-112">**To list information about the current thread**</span></span>  
  
-   <span data-ttu-id="39ca9-113">在**命令**中，键入 `Debug.ListThread` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="39ca9-113">In the **CommandWindow**, type `Debug.ListThread`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="39ca9-114">**将变量添加到“快速监视”窗口**</span><span class="sxs-lookup"><span data-stu-id="39ca9-114">**To add a variable to the QuickWatch window**</span></span>  
  
-   <span data-ttu-id="39ca9-115">在**命令**中，键入\*\*Debug \<VariableName> \*\*，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="39ca9-115">In the **CommandWindow**, type **Debug.QuickWatch \<VariableName>**, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ca9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39ca9-116">See Also</span></span>  
 [<span data-ttu-id="39ca9-117">Transact-SQL 调试器</span><span class="sxs-lookup"><span data-stu-id="39ca9-117">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
