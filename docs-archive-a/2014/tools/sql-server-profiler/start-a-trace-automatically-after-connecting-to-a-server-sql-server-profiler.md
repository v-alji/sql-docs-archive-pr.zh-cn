---
title: 连接到服务器后自动启动跟踪 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
author: stevestein
ms.author: sstein
ms.openlocfilehash: a2c8cae3e47a6f48014cbafe588dde782c097260
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690950"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a><span data-ttu-id="62ffc-102">连接到服务器后自动启动跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="62ffc-102">Start a Trace Automatically after Connecting to a Server (SQL Server Profiler)</span></span>
  <span data-ttu-id="62ffc-103">本主题介绍了如何在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]实例后自动启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="62ffc-103">This topic describes how to start traces automatically after connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a><span data-ttu-id="62ffc-104">在使用 SQL Server Profiler 连接到服务器后自动启动跟踪</span><span class="sxs-lookup"><span data-stu-id="62ffc-104">To start a trace automatically after connecting to a server with SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="62ffc-105">在“工具”  菜单上，单击“选项” 。</span><span class="sxs-lookup"><span data-stu-id="62ffc-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="62ffc-106">选择 **“进行连接后立即启动跟踪”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="62ffc-106">Select the **Start tracing immediately after making a connection** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62ffc-107">如果选择“建立连接后立即开始跟踪”，则不会显示“跟踪属性”对话框，而是开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="62ffc-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="62ffc-108">若要编辑跟踪属性，必须先关闭此设置。</span><span class="sxs-lookup"><span data-stu-id="62ffc-108">To edit trace properties, you must first turn this setting off.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ffc-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62ffc-109">See Also</span></span>  
 [<span data-ttu-id="62ffc-110">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="62ffc-110">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
