---
title: 设置跟踪表的最大表大小 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f48efbe02e300e06faf857ed0fb36ae340ad979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682489"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a><span data-ttu-id="0bc39-102">设置跟踪表的最大表大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="0bc39-102">Set a Maximum Table Size for a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="0bc39-103">本主题说明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]设置跟踪表的最大表大小。</span><span class="sxs-lookup"><span data-stu-id="0bc39-103">This topic describes how to set a maximum table size for trace tables by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a><span data-ttu-id="0bc39-104">设置跟踪表的最大表大小</span><span class="sxs-lookup"><span data-stu-id="0bc39-104">To set a maximum table size for a trace table</span></span>  
  
1.  <span data-ttu-id="0bc39-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="0bc39-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="0bc39-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0bc39-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bc39-107">如果选择“建立连接后立即开始跟踪”  ，则不会显示“跟踪属性”  对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="0bc39-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="0bc39-108">若要关闭此设置，请在“工具”  菜单上，单击“选项”  ，然后清除“建立连接后立即开始跟踪”  复选框。</span><span class="sxs-lookup"><span data-stu-id="0bc39-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="0bc39-109">在 **“跟踪名称”** 框中，键入跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="0bc39-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="0bc39-110">在“模板名称”  列表中，选择跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="0bc39-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="0bc39-111">选中“保存到表”  复选框。</span><span class="sxs-lookup"><span data-stu-id="0bc39-111">Select the **Save to table**check box.</span></span>  
  
5.  <span data-ttu-id="0bc39-112">连接到要存储跟踪的服务器。</span><span class="sxs-lookup"><span data-stu-id="0bc39-112">Connect to the server on which you want the trace to be stored.</span></span>  
  
     <span data-ttu-id="0bc39-113">将显示 **“目标表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0bc39-113">The **Destination Table** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="0bc39-114">从 **“数据库”** 列表中，为跟踪选择数据库。</span><span class="sxs-lookup"><span data-stu-id="0bc39-114">Select a database for the trace from the **Database** list.</span></span>  
  
7.  <span data-ttu-id="0bc39-115">在 **“表”** 框中，键入或选择表名。</span><span class="sxs-lookup"><span data-stu-id="0bc39-115">In the **Table** box, type or select a table name.</span></span>  
  
8.  <span data-ttu-id="0bc39-116">选中 **“设置最大行数”** 复选框，然后指定跟踪表的最大行数。</span><span class="sxs-lookup"><span data-stu-id="0bc39-116">Select the **Set maximum rows** check box, and specify a maximum number of rows for the trace table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bc39-117">表中的行数超过指定的最大值时，将不再记录跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="0bc39-117">When the number of rows in the table exceeds the maximum that you have specified, the trace events are no longer recorded.</span></span> <span data-ttu-id="0bc39-118">但是，仍继续跟踪。</span><span class="sxs-lookup"><span data-stu-id="0bc39-118">However, tracing continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc39-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0bc39-119">See Also</span></span>  
 <span data-ttu-id="0bc39-120">[SQL Server 事件探查器](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="0bc39-120">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="0bc39-121">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="0bc39-121">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
