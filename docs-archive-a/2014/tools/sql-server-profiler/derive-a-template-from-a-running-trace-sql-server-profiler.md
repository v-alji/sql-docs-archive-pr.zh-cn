---
title: 从正在运行的跟踪中派生模板 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
ms.assetid: 25a3b845-affb-4b2a-a382-198a4bdd9ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72744ce942cc49038129cf6064349e23c3e9a41d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682495"
---
# <a name="derive-a-template-from-a-running-trace-sql-server-profiler"></a><span data-ttu-id="b5ce7-102">从正在运行的跟踪中派生模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="b5ce7-102">Derive a Template from a Running Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="b5ce7-103">本主题将介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]从正在运行的现有跟踪创建跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-103">This topic describes how to create a trace template from an existing trace while it is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-derive-a-template-from-a-running-trace"></a><span data-ttu-id="b5ce7-104">从正在运行的跟踪派生模板</span><span class="sxs-lookup"><span data-stu-id="b5ce7-104">To derive a template from a running trace</span></span>  
  
1.  <span data-ttu-id="b5ce7-105">必要时，可切换到包含跟踪的窗口。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-105">If necessary, switch to the window that contains the trace.</span></span>  
  
2.  <span data-ttu-id="b5ce7-106">在 **“文件”** 菜单上，指向 **“另存为”** ，再单击 **“跟踪模板”** 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-106">On the **File** menu, point to **Save As**, and then click **Trace Template**.</span></span>  
  
3.  <span data-ttu-id="b5ce7-107">键入名称或从列表中选择一个名称。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-107">Type a name or select one from the list.</span></span> <span data-ttu-id="b5ce7-108">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b5ce7-108">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5ce7-109">如果选择现有模板文件，系统将会询问您是否希望覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-109">If you select an existing template file, you are asked if you want to overwrite the file.</span></span> <span data-ttu-id="b5ce7-110">可以只选择用户定义的模板。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-110">You can only select a user-defined template.</span></span> <span data-ttu-id="b5ce7-111">无法覆盖预定义的系统跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-111">Predefined system trace templates cannot be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ce7-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5ce7-112">See Also</span></span>  
 <span data-ttu-id="b5ce7-113">[SQL Server Profiler 模板和权限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="b5ce7-113">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="b5ce7-114">[创建跟踪模板 (SQL Server Profiler)](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5ce7-114">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="b5ce7-115">[修改跟踪模板 (SQL Server Profiler)](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b5ce7-115">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="b5ce7-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b5ce7-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
