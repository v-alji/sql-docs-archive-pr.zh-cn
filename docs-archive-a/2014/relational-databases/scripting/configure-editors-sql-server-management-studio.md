---
title: 配置编辑器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e94cdbcd310814081e146e3fd0dbe75260d1240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689845"
---
# <a name="configure-editors-sql-server-management-studio"></a><span data-ttu-id="7f572-102">配置编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7f572-102">Configure Editors (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7f572-103">您可以通过为每个编辑器配置选项，自定义 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 编辑器的操作。</span><span class="sxs-lookup"><span data-stu-id="7f572-103">You can customize the operation of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] editors by configuring the options for each editor.</span></span>  
  
## <a name="settng-editor-options"></a><span data-ttu-id="7f572-104">设置编辑器选项</span><span class="sxs-lookup"><span data-stu-id="7f572-104">Settng Editor Options</span></span>  
 <span data-ttu-id="7f572-105">通过使用“工具”菜单，然后选择“选项…”以便显示“选项”对话框，可设置大多数编辑器选项    。</span><span class="sxs-lookup"><span data-stu-id="7f572-105">Most of the editor options are set by using the **Tools** menu and selecting **Options...** to display an **Options** dialog.</span></span> <span data-ttu-id="7f572-106">在 **“选项”** 对话框中，打开左侧窗格中的 **“文本编辑器”** 节点，以便设置代码和文本编辑选项。</span><span class="sxs-lookup"><span data-stu-id="7f572-106">In the **Options** dialog, open the **Text Editor** node in the left pane to set code and text editing options.</span></span> <span data-ttu-id="7f572-107">“文本编辑器”下方的节点适用于特定编辑器：</span><span class="sxs-lookup"><span data-stu-id="7f572-107">The nodes under Text Editor apply to specific editors:</span></span>  
  
1.  <span data-ttu-id="7f572-108">**所有语言** - 使用此节点设置的选项将应用于所有 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 编辑器。</span><span class="sxs-lookup"><span data-stu-id="7f572-108">**All Languages** - options set using this node apply to all of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] editors.</span></span> <span data-ttu-id="7f572-109">可通过使用其他节点为特定的编辑器设置不同选项，覆盖这些设置。</span><span class="sxs-lookup"><span data-stu-id="7f572-109">You can override these settings by using the other nodes to set different options for a specific editor.</span></span>  
  
2.  <span data-ttu-id="7f572-110">**纯文本** - 使用此节点设置的选项将应用于 MDX、DMX 和文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="7f572-110">**Plain Text** - options set using this node apply to the MDX, DMX, and text editors.</span></span>  
  
3.  <span data-ttu-id="7f572-111">**Transact-SQL** - 使用此节点设置的选项将应用于数据库引擎查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="7f572-111">**Transact-SQL** - options set using this node apply to the Database Engine Query Editor.</span></span>  
  
4.  <span data-ttu-id="7f572-112">**XML** - 使用此节点设置的选项将应用于 XML for Analysis 编辑器。</span><span class="sxs-lookup"><span data-stu-id="7f572-112">**XML** - options set using this node apply to the XML for Analysis editor.</span></span>  
  
 <span data-ttu-id="7f572-113">打开 **“查询执行”** 或 **“查询结果”** 节点，以便自定义查询的执行以及显示结果的方式。</span><span class="sxs-lookup"><span data-stu-id="7f572-113">Open the **Query Execution** or **Query Results** nodes to customize the execution of queries and how the results are displayed.</span></span>  
  
## <a name="editor-configuration-tasks"></a><span data-ttu-id="7f572-114">编辑器配置任务</span><span class="sxs-lookup"><span data-stu-id="7f572-114">Editor Configuration Tasks</span></span>  
  
|<span data-ttu-id="7f572-115">任务说明</span><span class="sxs-lookup"><span data-stu-id="7f572-115">Task Description</span></span>|<span data-ttu-id="7f572-116">主题</span><span class="sxs-lookup"><span data-stu-id="7f572-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="7f572-117">介绍如何指定通过在 Windows 资源管理器中双击具有指定扩展名的文件来打开编辑器。</span><span class="sxs-lookup"><span data-stu-id="7f572-117">Describes how to specify that an editor be opened by double-clicking on a file with a specified extension in Windows Explorer.</span></span>|[<span data-ttu-id="7f572-118">将文件扩展名与代码编辑器关联</span><span class="sxs-lookup"><span data-stu-id="7f572-118">Associate File Extensions to a Code Editor</span></span>](associate-file-extensions-to-a-code-editor.md)|  
|<span data-ttu-id="7f572-119">介绍如何自定义字体以使代码和文本更具可读性。</span><span class="sxs-lookup"><span data-stu-id="7f572-119">Describes how to customize fonts to make code and text more readable.</span></span>|[<span data-ttu-id="7f572-120">更改字体颜色、大小和样式</span><span class="sxs-lookup"><span data-stu-id="7f572-120">Change Font Color, Size, and Style</span></span>](change-font-color-size-and-style.md)|  
|<span data-ttu-id="7f572-121">介绍如何查看属性。</span><span class="sxs-lookup"><span data-stu-id="7f572-121">Describes how to view properties.</span></span>|[<span data-ttu-id="7f572-122">使用 Management Studio 中的“属性”窗口</span><span class="sxs-lookup"><span data-stu-id="7f572-122">Use the Properties Window in Management Studio</span></span>](use-the-properties-window-in-management-studio.md)|  
|<span data-ttu-id="7f572-123">编辑器选项对话框的 F1 帮助页的位置。</span><span class="sxs-lookup"><span data-stu-id="7f572-123">Location of the F1 help pages for the editor options dialogs.</span></span>|[<span data-ttu-id="7f572-124">“查询选项”页的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="7f572-124">Query Options Pages F1 Help</span></span>](../../database-engine/query-options-pages-f1-help.md)|  
  
  
