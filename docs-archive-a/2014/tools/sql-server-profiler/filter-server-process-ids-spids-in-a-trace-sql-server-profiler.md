---
title: 在跟踪中筛选服务器进程 ID (SPID) (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: stevestein
ms.author: sstein
ms.openlocfilehash: 99ae7eac6f19bd942a04f97b0a7da580eadc9dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692619"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a><span data-ttu-id="10ba9-102">在跟踪中筛选服务器进程 ID (SPID) (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="10ba9-102">Filter Server Process IDs (SPIDs) in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="10ba9-103">本主题说明了如何通过 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]在跟踪中筛选服务器进程标识符 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="10ba9-103">This topic describes how to filter server process identifiers (SPIDs) in a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-system-ids-in-a-trace"></a><span data-ttu-id="10ba9-104">在跟踪中筛选系统 ID</span><span class="sxs-lookup"><span data-stu-id="10ba9-104">To filter system IDs in a trace</span></span>  
  
1.  <span data-ttu-id="10ba9-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="10ba9-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="10ba9-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="10ba9-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="10ba9-107">如果选择了 "**建立连接后立即开始跟踪**"，则不会显示 "**跟踪属性**" 对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="10ba9-107">if **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="10ba9-108">若要关闭此设置，请在“工具”菜单上，单击“选项”，然后清除“建立连接后立即开始跟踪”复选框。</span><span class="sxs-lookup"><span data-stu-id="10ba9-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="10ba9-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="10ba9-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="10ba9-110">在“使用模板”\*\*\*\* 名称列表中，选择跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="10ba9-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="10ba9-111">根据需要，指定保存跟踪结果的目标文件或表。</span><span class="sxs-lookup"><span data-stu-id="10ba9-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="10ba9-112">在“事件选择”\*\*\*\* 选项卡上，单击“SPID”\*\*\*\* 列标题以启动“编辑筛选器”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="10ba9-112">On the **Events Selection**tab, click the **SPID**column heading to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="10ba9-113">还可以右键单击列标题，然后选择“编辑列筛选器”。</span><span class="sxs-lookup"><span data-stu-id="10ba9-113">You can also right-click the column heading and choose **Edit Column Filter**.</span></span> <span data-ttu-id="10ba9-114">如果 **SPID** 列不出现，请选中 **“显示所有列”** 框。</span><span class="sxs-lookup"><span data-stu-id="10ba9-114">If the **SPID** column does not appear, check the **Show all columns** box.</span></span>  
  
6.  <span data-ttu-id="10ba9-115">在 **“编辑筛选器”** 对话框中，展开相应的比较运算符，输入 SPID 作为比较的值。</span><span class="sxs-lookup"><span data-stu-id="10ba9-115">In the **Edit Filter** dialog box, expand the appropriate comparison operator, and enter a SPID as a value for the comparison.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ba9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10ba9-116">See Also</span></span>  
 [<span data-ttu-id="10ba9-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="10ba9-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
