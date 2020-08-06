---
title: 设置跟踪文件的最大文件大小 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa990c610f7aa8bf82690c8c201c6643eb712191
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691434"
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="c7402-102">设置跟踪文件的最大文件大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c7402-102">Set a Maximum File Size for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="c7402-103">使用以下步骤可设置跟踪文件的最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="c7402-103">Use the following procedure to set the maximum file size for a trace file.</span></span>  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a><span data-ttu-id="c7402-104">设置跟踪文件的最大文件大小</span><span class="sxs-lookup"><span data-stu-id="c7402-104">To set a maximum file size for a trace file</span></span>  
  
1.  <span data-ttu-id="c7402-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，然后连接到 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="c7402-105">On the **File** menu, click **New Trace**, and then connect to an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="c7402-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c7402-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7402-107">如果选择“建立连接后立即开始跟踪”，则不会显示“跟踪属性”对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="c7402-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="c7402-108">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="c7402-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="c7402-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="c7402-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="c7402-110">在“模板名称”列表中，选择跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="c7402-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="c7402-111">选择 **“保存到文件”** ，然后指定存储跟踪信息的文件。</span><span class="sxs-lookup"><span data-stu-id="c7402-111">Select **Save to file**, and then specify a file to store the trace information.</span></span>  
  
5.  <span data-ttu-id="c7402-112">在 **“设置最大文件大小”** 复选框中，指定跟踪的最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="c7402-112">In the **Set maximum file size** check box, specify a maximum file size for the trace.</span></span> <span data-ttu-id="c7402-113">当文件大小达到此最大值时，跟踪文件就不再记录到此文件中。</span><span class="sxs-lookup"><span data-stu-id="c7402-113">When the file size reaches this maximum, trace events are no longer recorded in this file.</span></span> <span data-ttu-id="c7402-114">如果选中“启用文件滚动更新”（默认情况下选中此选项），则出现以下情况：</span><span class="sxs-lookup"><span data-stu-id="c7402-114">If you select **Enable file rollover** (which is selected by default),the following occurs:</span></span>  
  
     <span data-ttu-id="c7402-115">如果使用文件滚动更新选项，则在达到最大文件大小时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会关闭当前文件并创建一个新文件。</span><span class="sxs-lookup"><span data-stu-id="c7402-115">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="c7402-116">新文件的名称与上一个文件相同，但是在其名称后追加了一个指明顺序的整数。例如，如果原始跟踪文件命名为 filename_1.trc，则下一个跟踪文件就为 filename_2.trc，依此类推。</span><span class="sxs-lookup"><span data-stu-id="c7402-116">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence; for example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="c7402-117">如果分配给新的滚动更新文件的名称已经被现有文件使用，则现有文件将被覆盖，除非它是只读的。</span><span class="sxs-lookup"><span data-stu-id="c7402-117">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read-only.</span></span> <span data-ttu-id="c7402-118">将跟踪数据保存到文件时，默认情况下启用文件滚动选项。</span><span class="sxs-lookup"><span data-stu-id="c7402-118">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
     <span data-ttu-id="c7402-119">如果启用了文件滚动更新选项，则在使用其他某种方法停止跟踪之前，跟踪将一直继续。</span><span class="sxs-lookup"><span data-stu-id="c7402-119">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="c7402-120">若要停止在达到文件大小限制后进行跟踪，请禁用文件滚动更新选项。</span><span class="sxs-lookup"><span data-stu-id="c7402-120">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7402-121">FAT32 文件系统将文件大小限制为略微小于 4 GB。</span><span class="sxs-lookup"><span data-stu-id="c7402-121">The FAT32 file system limits files to slightly less than 4 gigabytes (GB).</span></span> <span data-ttu-id="c7402-122">当跟踪文件达到该大小时，跟踪将会失败，并出现错误“磁盘空间不足”。</span><span class="sxs-lookup"><span data-stu-id="c7402-122">When the trace file reaches that size, the trace fails with the error "Not enough disk space."</span></span> <span data-ttu-id="c7402-123">若要创建更大的文件，请使用 NTFS 文件系统。</span><span class="sxs-lookup"><span data-stu-id="c7402-123">To create larger files, use the NTFS file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7402-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7402-124">See Also</span></span>  
 [<span data-ttu-id="c7402-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="c7402-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
