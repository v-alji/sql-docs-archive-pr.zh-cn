---
title: 修改跟踪模板 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a26d0a70f65b6ff60dcf42ffb98e67dc0d2b52d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577974"
---
# <a name="modify-trace-templates"></a><span data-ttu-id="2406f-102">修改跟踪模板</span><span class="sxs-lookup"><span data-stu-id="2406f-102">Modify Trace Templates</span></span>
  <span data-ttu-id="2406f-103">用户可以在运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的本地计算机上的文件中修改保存的模板。</span><span class="sxs-lookup"><span data-stu-id="2406f-103">You can modify templates that are saved in a file on the local computer on which [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running.</span></span> <span data-ttu-id="2406f-104">也可以修改从那些文件派生的模板。</span><span class="sxs-lookup"><span data-stu-id="2406f-104">You can also modify templates derived from those files.</span></span> <span data-ttu-id="2406f-105">修改现有模板时，可以在 **“跟踪属性”** 对话框的 **“事件选择”** 选项卡上，以最初设置属性时相同的顺序编辑事件类和数据列等模板属性。</span><span class="sxs-lookup"><span data-stu-id="2406f-105">When you modify existing templates, you edit template properties such as event classes and data columns, in the same order that the properties were set originally, on the **Events Selection** tab of the **Trace Properties** dialog box.</span></span> <span data-ttu-id="2406f-106">可以添加和删除事件类和数据列，也可以对筛选进行更改。</span><span class="sxs-lookup"><span data-stu-id="2406f-106">Event classes and data columns can be added or removed, and filters can be changed.</span></span> <span data-ttu-id="2406f-107">修改模板后，将创建用户特定的模板，并且将保持原始系统模板的完整性。</span><span class="sxs-lookup"><span data-stu-id="2406f-107">After the template is modified, a user-specific template is created and the original system template is left intact.</span></span> <span data-ttu-id="2406f-108">有关详细信息，请参阅 [保存跟踪和跟踪模板](save-traces-and-trace-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="2406f-108">For more information, see [Save Traces and Trace Templates](save-traces-and-trace-templates.md).</span></span>  
  
 <span data-ttu-id="2406f-109">如果您无法想起（或者没有保存）创建跟踪时使用的原始模板，或希望以后运行同一跟踪，则可能需要从现有的跟踪文件派生一个模板。</span><span class="sxs-lookup"><span data-stu-id="2406f-109">You may need to derive a template from an existing trace file if you cannot remember (or have not saved) the original template that was used to create the trace, or if you want to run the same trace at a later date.</span></span> <span data-ttu-id="2406f-110">在使用现有跟踪时，可以查看属性，但是不能修改属性。</span><span class="sxs-lookup"><span data-stu-id="2406f-110">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="2406f-111">若要修改属性，请停止或暂停跟踪。</span><span class="sxs-lookup"><span data-stu-id="2406f-111">To modify the properties, stop or pause the trace.</span></span> <span data-ttu-id="2406f-112">有关详细信息，请参阅[从跟踪文件或跟踪表派生模板 (SQL Server Profiler)](sql-server-profiler.md) 和[从正在运行的跟踪派生模板 (SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="2406f-112">For more information, see [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](sql-server-profiler.md) and [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="2406f-113">**创建跟踪模板**</span><span class="sxs-lookup"><span data-stu-id="2406f-113">**To create a trace template**</span></span>  
  
 [<span data-ttu-id="2406f-114">创建跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2406f-114">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="2406f-115">**通过跟踪模板运行跟踪**</span><span class="sxs-lookup"><span data-stu-id="2406f-115">**To run a trace from a trace template**</span></span>  
  
 [<span data-ttu-id="2406f-116">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2406f-116">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="2406f-117">**修改跟踪模板**</span><span class="sxs-lookup"><span data-stu-id="2406f-117">**To modify a trace template**</span></span>  
  
 [<span data-ttu-id="2406f-118">使用 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2406f-118">Using SQL Server Profiler</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [<span data-ttu-id="2406f-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2406f-119">Using Transact-SQL</span></span>](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 <span data-ttu-id="2406f-120">**在跟踪模板或跟踪文件中添加或删除事件**</span><span class="sxs-lookup"><span data-stu-id="2406f-120">**To add or remove events from a trace template or trace file**</span></span>  
  
 [<span data-ttu-id="2406f-121">使用 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2406f-121">Using SQL Server Profiler</span></span>](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="2406f-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2406f-122">Using Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="2406f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2406f-123">See Also</span></span>  
 [<span data-ttu-id="2406f-124">启动跟踪</span><span class="sxs-lookup"><span data-stu-id="2406f-124">Start a Trace</span></span>](start-a-trace.md)  
  
  
