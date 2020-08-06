---
title: 编辑断点位置
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: rothja
ms.author: jroth
ms.openlocfilehash: 919e62d53d5c9e8898bf1d49c4b5e5aa4c0ed107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576608"
---
# <a name="edit-a-breakpoint-location"></a><span data-ttu-id="9709b-102">编辑断点位置</span><span class="sxs-lookup"><span data-stu-id="9709b-102">Edit a Breakpoint Location</span></span>
  <span data-ttu-id="9709b-103">断点位置指定断点在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件中所处的行和字符位置。</span><span class="sxs-lookup"><span data-stu-id="9709b-103">The breakpoint location specifies the line and character where the breakpoint resides in a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="9709b-104">您可以编辑断点位置以将断点移至脚本的其他位置，或移至其他脚本。</span><span class="sxs-lookup"><span data-stu-id="9709b-104">You can edit the breakpoint location to move the breakpoint to another location in the script, or to a different script.</span></span>  
  
## <a name="editing-a-location"></a><span data-ttu-id="9709b-105">编辑位置</span><span class="sxs-lookup"><span data-stu-id="9709b-105">Editing a Location</span></span>  
 <span data-ttu-id="9709b-106">编辑断点位置时，断点将移至新的位置，并携带所有现有属性一起移动，例如命中计数或条件。</span><span class="sxs-lookup"><span data-stu-id="9709b-106">When you edit a breakpoint location, the breakpoint moves to the new location, carrying with it all of the existing properties, such as a hit count or condition.</span></span>  
  
#### <a name="to-edit-a-breakpoint-location"></a><span data-ttu-id="9709b-107">编辑断点位置</span><span class="sxs-lookup"><span data-stu-id="9709b-107">To Edit a Breakpoint Location</span></span>  
  
1.  <span data-ttu-id="9709b-108">在编辑器窗口中，右键单击断点符号，然后单击快捷菜单上的“位置”  。</span><span class="sxs-lookup"><span data-stu-id="9709b-108">In the editor window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="9709b-109">-或-</span><span class="sxs-lookup"><span data-stu-id="9709b-109">-or-</span></span>  
  
     <span data-ttu-id="9709b-110">在“断点”  窗口中，右键单击断点符号，然后单击快捷菜单的“位置”  。</span><span class="sxs-lookup"><span data-stu-id="9709b-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Location** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="9709b-111">在 **“文件断点”** 对话框中，编辑 **“文件”** 以指定新的文件，编辑 **“行”** 以指定新行，或者编辑 **“字符”** 以指定该行内的新位置。</span><span class="sxs-lookup"><span data-stu-id="9709b-111">In the **File Breakpoint** dialog box, edit **File** to specify a new file, **Line** to specify a new line, or **Character** to specify a new location within the line.</span></span> <span data-ttu-id="9709b-112">如果您指定的新文件已经在查询编辑器窗口中打开，则断点会移至该编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="9709b-112">If the new file you specify is already open in a query editor window, the breakpoint is moved to that editor window.</span></span> <span data-ttu-id="9709b-113">如果文件未打开，则会打开新的编辑器窗口，并在其中载入文件，断点随即移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="9709b-113">If the file is not opened, a new editor window is opened, the file is loaded in, and the breakpoint moved to the new location.</span></span>  
  
     <span data-ttu-id="9709b-114">**“允许源代码与原始版本不同”** 选项在调试 [!INCLUDE[tsql](../../includes/tsql-md.md)]时不起作用。</span><span class="sxs-lookup"><span data-stu-id="9709b-114">The **Allow the source code to be different from the original version** option has no effect when debugging [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9709b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9709b-115">See Also</span></span>  
 <span data-ttu-id="9709b-116">[指定命中次数](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="9709b-116">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 <span data-ttu-id="9709b-117">[指定断点操作](specify-a-breakpoint-action.md) </span><span class="sxs-lookup"><span data-stu-id="9709b-117">[Specify a Breakpoint Action](specify-a-breakpoint-action.md) </span></span>  
 <span data-ttu-id="9709b-118">[指定断点条件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="9709b-118">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="9709b-119">指定断点筛选器</span><span class="sxs-lookup"><span data-stu-id="9709b-119">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)  
