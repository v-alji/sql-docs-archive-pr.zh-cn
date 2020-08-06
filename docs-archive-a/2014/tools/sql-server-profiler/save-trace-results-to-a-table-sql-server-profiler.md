---
title: 将跟踪结果保存到表 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08acfb4e7136f8b28d1c990d508b8578f96a57b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692008"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a><span data-ttu-id="fe386-102">将跟踪结果保存到表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="fe386-102">Save Trace Results to a Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="fe386-103">本主题说明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]将跟踪结果保存到数据库表。</span><span class="sxs-lookup"><span data-stu-id="fe386-103">This topic describes how to save trace results to a database table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-table"></a><span data-ttu-id="fe386-104">将跟踪结果保存到表</span><span class="sxs-lookup"><span data-stu-id="fe386-104">To save trace results to a table</span></span>  
  
1.  <span data-ttu-id="fe386-105">在 **“文件”** 菜单上，单击 **“新建跟踪”** ，再连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fe386-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="fe386-106">将出现“跟踪属性”对话框。 **“跟踪属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="fe386-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe386-107">如果选择“建立连接后立即开始跟踪”  ，则不会显示“跟踪属性”  对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="fe386-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="fe386-108">若要关闭此设置，请在“工具”  菜单上，单击“选项”  ，然后清除“建立连接后立即开始跟踪”  复选框。</span><span class="sxs-lookup"><span data-stu-id="fe386-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="fe386-109">在 **“跟踪名称”** 框中，键入跟踪的名称，然后单击 **“保存到表”** 。</span><span class="sxs-lookup"><span data-stu-id="fe386-109">In the **Trace name** box, type a name for the trace, and then click **Save to table**.</span></span>  
  
3.  <span data-ttu-id="fe386-110">在 **“连接到服务器”** 对话框中，连接到将包含跟踪表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="fe386-110">In the **Connect to server** dialog box, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the trace table.</span></span>  
  
4.  <span data-ttu-id="fe386-111">在“目标表”  对话框中，从“数据库”  列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="fe386-111">In the **Destination Table** dialog box, select a database from the **Database**list.</span></span>  
  
5.  <span data-ttu-id="fe386-112">在 **“所有者”** 列表中，选择此跟踪的所有者。</span><span class="sxs-lookup"><span data-stu-id="fe386-112">In the **Owner** list, select the owner for the trace.</span></span>  
  
6.  <span data-ttu-id="fe386-113">在 **“表”** 列表中，键入或选择跟踪结果的表名。</span><span class="sxs-lookup"><span data-stu-id="fe386-113">In the **Table** list, type or select the table name for the trace results.</span></span> <span data-ttu-id="fe386-114">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="fe386-114">Click **OK.**</span></span>  
  
7.  <span data-ttu-id="fe386-115">在 "**跟踪属性**" 对话框中，选中 "\*\*设置最大行数 (，) \*\* " 复选框，以指定要保存的最大行数。</span><span class="sxs-lookup"><span data-stu-id="fe386-115">In the **Trace Properties** dialog box, select the **Set maximum rows (in thousands)** check box to specify the maximum number of rows to save.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe386-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe386-116">See Also</span></span>  
 [<span data-ttu-id="fe386-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fe386-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
