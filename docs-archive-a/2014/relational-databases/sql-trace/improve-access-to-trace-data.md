---
title: 改进对跟踪数据的访问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e01ad04ddd9f7fe6d858c399abb552716f2bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688696"
---
# <a name="improve-access-to-trace-data"></a><span data-ttu-id="93b34-102">改进对跟踪数据的访问</span><span class="sxs-lookup"><span data-stu-id="93b34-102">Improve Access to Trace Data</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="93b34-103">使用 **temp** 目录中的空间来改进对跟踪数据的访问。</span><span class="sxs-lookup"><span data-stu-id="93b34-103">uses space in the **temp** directory to improve access to trace data.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="93b34-104">需要至少 10 兆字节 (MB) 的可用空间。</span><span class="sxs-lookup"><span data-stu-id="93b34-104">requires at least 10 megabytes (MB) of free space.</span></span> <span data-ttu-id="93b34-105">如果在使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]时可用空间低于 10 MB，则所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 功能都将会停止。</span><span class="sxs-lookup"><span data-stu-id="93b34-105">If free space drops below 10 MB while you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] functions stop.</span></span>  
  
 <span data-ttu-id="93b34-106">在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 使用 **temp** 目录的空间时，对该空间的使用可能导致 **temp** 目录所包含的数据量迅速增长。</span><span class="sxs-lookup"><span data-stu-id="93b34-106">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] uses space in the **temp** directory, this space usage may cause the **temp** directory to grow rapidly.</span></span> <span data-ttu-id="93b34-107">为了避免出现文件增大的问题，可以通过更改 TEMP 环境变量的值，将 **temp** 目录放在非系统驱动器的驱动器上。</span><span class="sxs-lookup"><span data-stu-id="93b34-107">To avoid file-growth problems, you can place the **temp** directory on a drive that is not a system drive by changing the value for the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="93b34-108">以下过程说明如何在大多数 Microsoft Windows 操作系统中更改 TEMP 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="93b34-108">The following procedure describes how to change the value for the TEMP environment variable in most Microsoft Windows operating systems.</span></span> <span data-ttu-id="93b34-109">有关设置环境变量的详细信息，请参阅 Windows 操作系统文档。</span><span class="sxs-lookup"><span data-stu-id="93b34-109">For more information about setting environment variables, see your Windows operating system documentation.</span></span>  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a><span data-ttu-id="93b34-110">在 Windows 操作系统中更改 TEMP 环境变量</span><span class="sxs-lookup"><span data-stu-id="93b34-110">To change the TEMP environment variable in Windows operating systems</span></span>  
  
1.  <span data-ttu-id="93b34-111">在 **“开始”** 菜单上，选择 **“控制面板”** ，再单击 **“系统”** 。</span><span class="sxs-lookup"><span data-stu-id="93b34-111">On the **Start** menu, choose **Control Panel**, and then click **System**.</span></span>  
  
2.  <span data-ttu-id="93b34-112">在 **“系统属性”** 对话框中，单击 **“高级”** 选项卡，再单击 **“环境变量”** 。</span><span class="sxs-lookup"><span data-stu-id="93b34-112">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
3.  <span data-ttu-id="93b34-113">向下滚动 **“系统变量”** 列表，选择对应于 **TEMP** 变量的行，并单击 **“编辑”** 。</span><span class="sxs-lookup"><span data-stu-id="93b34-113">Scroll down the list of **System Variables**, select the row that corresponds to the **TEMP** variable, and click **Edit**.</span></span>  
  
4.  <span data-ttu-id="93b34-114">在 **“编辑系统变量”** 对话框中，输入要作为 **temp** 目录的驱动器及目录的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="93b34-114">In the **Edit System Variable** dialog box, enter the path and name of the drive and directory where you want the **temp** directory to be located.</span></span>  
  
5.  <span data-ttu-id="93b34-115">单击 **“确定”** 保存更改。</span><span class="sxs-lookup"><span data-stu-id="93b34-115">Click **OK** to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b34-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93b34-116">See Also</span></span>  
 <span data-ttu-id="93b34-117">[启动 SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="93b34-117">[Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="93b34-118">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="93b34-118">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
