---
title: 在 "日志事件" 窗口中查看日志条目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16b6f11758d7de2c833731cd007426000a01d8ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682927"
---
# <a name="view-log-entries-in-the-log-events-window"></a><span data-ttu-id="b5ad2-102">在“日志事件”窗口中查看日志项</span><span class="sxs-lookup"><span data-stu-id="b5ad2-102">View Log Entries in the Log Events Window</span></span>
  <span data-ttu-id="b5ad2-103">此过程描述如何运行包并查看它写入的日志项。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-103">This procedure describes how to run a package and view the log entries it writes.</span></span> <span data-ttu-id="b5ad2-104">您可以实时查看日志项。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-104">You can view the log entries in real time.</span></span> <span data-ttu-id="b5ad2-105">此外，还可以将写入 **“日志事件”** 窗口的日志项复制并保存，以便进行进一步分析。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-105">The log entries that are written to the **Log Events** window can also be copied and saved for further analysis.</span></span>  
  
 <span data-ttu-id="b5ad2-106">不需要将日志项写入日志即可将这些项写入 **“日志事件”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-106">It is not necessary to write the log entries to a log to write the entries to the **Log Events** window.</span></span>  
  
### <a name="to-view-log-entries"></a><span data-ttu-id="b5ad2-107">查看日志项</span><span class="sxs-lookup"><span data-stu-id="b5ad2-107">To view log entries</span></span>  
  
1.  <span data-ttu-id="b5ad2-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b5ad2-109">在 **SSIS** 菜单上单击 **“日志事件”** 。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-109">On the **SSIS** menu, click **Log Events**.</span></span> <span data-ttu-id="b5ad2-110">通过将 View.LogEvents 命令映射为在 **“选项”** 对话框的 **“键盘”** 页中所选的组合键，您可以选择显示 **“日志事件”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-110">You can optionally display the **Log Events** window by mapping the View.LogEvents command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="b5ad2-111">在“调试”菜单上，单击“开始调试”。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-111">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="b5ad2-112">当运行时遇到为日志记录启用的事件和自定义消息时，每个事件或消息的日志项将写入 **“日志事件”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-112">As the runtime encounters the events and custom messages that are enabled for logging, log entries for each event or message are written to the **Log Events** window.</span></span>  
  
4.  <span data-ttu-id="b5ad2-113">在“调试”菜单上，单击“停止调试”。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-113">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
     <span data-ttu-id="b5ad2-114">日志项在 **“日志事件”** 窗口中保留可用状态，直到重新运行包、运行其他包或关闭 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-114">The log entries remain available in the **Log Events** window until you rerun the package, run a different package, or close [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
5.  <span data-ttu-id="b5ad2-115">在 **“日志事件”** 窗口中查看日志项。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-115">View the log entries in the **Log Events** window.</span></span>  
  
6.  <span data-ttu-id="b5ad2-116">（可选）单击要复制的日志项，右键单击，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-116">Optionally, click the log entries to copy, right-click, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="b5ad2-117">（可选）双击日志项，然后在“日志条目”对话框中，查看单个日志项的详细信息。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b5ad2-117">Optionally, double-click a log entry, and in the **Log Entry** dialog box, view the details for a single log entry.</span></span>  
  
8.  <span data-ttu-id="b5ad2-118">在 **“日志条目”** 对话框中，单击向上和向下键头，以显示上一个或下一个日志项，并单击复制图标以复制该日志项。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-118">In the **Log Entry** dialog box, click the up and down arrows to display the previous or next log entry, and click the copy icon to copy the log entry.</span></span>  
  
9. <span data-ttu-id="b5ad2-119">打开文本编辑器，粘贴，然后将日志项保存到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="b5ad2-119">Open a text editor, paste, and then save the log entry to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ad2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5ad2-120">See Also</span></span>  
 [<span data-ttu-id="b5ad2-121">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="b5ad2-121">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
