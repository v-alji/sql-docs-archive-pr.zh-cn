---
title: 重播 Transact-SQL 脚本 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5abf22a1201ac927f12ef9e4cfdd1f6d3026d00a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692028"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a><span data-ttu-id="55906-102">重播 Transact-SQL 脚本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="55906-102">Replay a Transact-SQL Script (SQL Server Profiler)</span></span>
  <span data-ttu-id="55906-103">当测试性能问题的可能解决方案时，请使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 重播 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，然后比较更改前后的性能。</span><span class="sxs-lookup"><span data-stu-id="55906-103">When you test possible solutions to a performance problem, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, and compare performance before and after your changes.</span></span>  
  
### <a name="to-replay-a-transact-sql-script"></a><span data-ttu-id="55906-104">重播 Transact-SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="55906-104">To replay a Transact-SQL script</span></span>  
  
1.  <span data-ttu-id="55906-105">在 **“文件”** 菜单上，指向 **“打开”** ，然后单击 **“脚本文件”** 。</span><span class="sxs-lookup"><span data-stu-id="55906-105">On the **File** menu, point to **Open**, and then click **Script File**.</span></span>  
  
2.  <span data-ttu-id="55906-106">选择要打开的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="55906-106">Select the [!INCLUDE[tsql](../../includes/tsql-md.md)] script file you want to open.</span></span> <span data-ttu-id="55906-107">确保 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本包含要重播的事件。</span><span class="sxs-lookup"><span data-stu-id="55906-107">Make sure that the [!INCLUDE[tsql](../../includes/tsql-md.md)] script contains events necessary for replay.</span></span> <span data-ttu-id="55906-108">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55906-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
3.  <span data-ttu-id="55906-109">在 **“重播”** 菜单上，单击 **“启动”** ，连接到要重播脚本的服务器。</span><span class="sxs-lookup"><span data-stu-id="55906-109">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the script.</span></span>  
  
4.  <span data-ttu-id="55906-110">在 **“重播配置”** 对话框中，验证设置，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="55906-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55906-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55906-111">See Also</span></span>  
 <span data-ttu-id="55906-112">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="55906-112">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="55906-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="55906-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
