---
title: 将跟踪结果保存到文件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9644751cda3689cf7b7cb00ec25310bc700ca1c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692019"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a><span data-ttu-id="8eb9b-102">将跟踪结果保存到文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="8eb9b-102">Save Trace Results to a File (SQL Server Profiler)</span></span>
  <span data-ttu-id="8eb9b-103">本主题说明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]将跟踪结果保存到文件。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-103">This topic describes how to save trace results to a file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-file"></a><span data-ttu-id="8eb9b-104">将跟踪结果保存到文件</span><span class="sxs-lookup"><span data-stu-id="8eb9b-104">To save trace results to a file</span></span>  
  
1.  <span data-ttu-id="8eb9b-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="8eb9b-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eb9b-107">如果选择“建立连接后立即开始跟踪”，则不会显示“跟踪属性”对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="8eb9b-108">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="8eb9b-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="8eb9b-110">选中 **“保存到文件”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-110">Select the **Save to file** check box.</span></span>  
  
     <span data-ttu-id="8eb9b-111">将显示“另存为”对话框。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-111">The **Save As**dialog box appears.</span></span>  
  
4.  <span data-ttu-id="8eb9b-112">在“另存为”对话框中指定路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-112">Specify a path and filename in the **Save As**dialog box.</span></span> <span data-ttu-id="8eb9b-113">单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-113">Click **Save.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eb9b-114">请确保 SQL Server 服务有足够的权限写入到指定目录的文件中。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-114">Ensure that the SQL Server service has sufficient permissions to write to a file in the directory specified.</span></span>  
  
5.  <span data-ttu-id="8eb9b-115">在“跟踪属性”对话框的“设置最大文件大小 (MB)”文本框中，输入最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-115">In the **Trace Properties** dialog box, enter the maximum file size in the **Set maximum file size (MB)** text box.</span></span> <span data-ttu-id="8eb9b-116">默认值为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-116">The default value is 5 megabytes (MB).</span></span>  
  
6.  <span data-ttu-id="8eb9b-117">还可以指定下列选项：</span><span class="sxs-lookup"><span data-stu-id="8eb9b-117">Optionally, specify the following options:</span></span>  
  
    -   <span data-ttu-id="8eb9b-118">选中 **“启用文件滚动更新”** 复选框，在达到最大文件大小后，使 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 立即创建新文件来存储跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-118">Select the **Enable file rollover** check box to have [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] create new files for trace data once the maximum file size is reached.</span></span> <span data-ttu-id="8eb9b-119">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-119">This option is selected by default.</span></span>  
  
    -   <span data-ttu-id="8eb9b-120">选中 **“服务器处理跟踪数据”** 复选框以确保服务器记录每个跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-120">Select the **Server processes trace data** check box to ensure that the server records each trace event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8eb9b-121">清除“服务器处理跟踪数据”后，如果记录事件会显著降低性能，则服务器不会记录事件。</span><span class="sxs-lookup"><span data-stu-id="8eb9b-121">When **Server processes trace data**is cleared, the server does not record events if recording events significantly degrades performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb9b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8eb9b-122">See Also</span></span>  
 [<span data-ttu-id="8eb9b-123">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="8eb9b-123">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
