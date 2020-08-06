---
title: 查看 Windows 应用程序日志 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689348"
---
# <a name="view-the-windows-application-log-windows"></a><span data-ttu-id="96190-102">查看 Windows 应用程序日志 (Windows)</span><span class="sxs-lookup"><span data-stu-id="96190-102">View the Windows Application Log (Windows)</span></span>
  <span data-ttu-id="96190-103">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Windows 应用程序日志后，每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话都将新事件写入该日志。</span><span class="sxs-lookup"><span data-stu-id="96190-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="96190-104">与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志不同，不是每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时都创建新的应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="96190-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-the-windows-application-log"></a><span data-ttu-id="96190-105">查看 Windows 应用程序日志</span><span class="sxs-lookup"><span data-stu-id="96190-105">To view the Windows application log</span></span>  
  
1.  <span data-ttu-id="96190-106">在 **“开始”** 菜单上，依次指向 **“所有程序”**、 **“管理工具”**，然后单击 **“事件查看器”**。</span><span class="sxs-lookup"><span data-stu-id="96190-106">On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
2.  <span data-ttu-id="96190-107">在事件查看器中，单击 **“应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="96190-107">In Event Viewer, click **Application**.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="96190-108">事件由“源”列中的 **MSSQLSERVER** 项（命名实例以 **MSSQL$** _<instance_name>_ 标识）标识。</span><span class="sxs-lookup"><span data-stu-id="96190-108">events are identified by the entry **MSSQLSERVER** (named instances are identified with **MSSQL$**_<instance_name>_) in the **Source** column.</span></span> <span data-ttu-id="96190-109">SQL Server 代理事件由 SQLSERVERAGENT 项标识（对于已命名的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件使用 SQLAgent$\<*instance_name*> 标识）。</span><span class="sxs-lookup"><span data-stu-id="96190-109">SQL Server Agent events are identified by the entry SQLSERVERAGENT (for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events are identified with **SQLAgent$**\<*instance_name*>).</span></span> <span data-ttu-id="96190-110">Microsoft Search 服务事件由 **Microsoft Search**项标识。</span><span class="sxs-lookup"><span data-stu-id="96190-110">Microsoft Search service events are identified by the entry **Microsoft Search**.</span></span>  
  
4.  <span data-ttu-id="96190-111">若要查看另一台计算机的日志，请右键单击“事件查看器”\*\*\*\*，再单击“连接到另一台计算机”\*\*\*\*，并完成“选择计算机”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="96190-111">To view the log of a different computer, right-click **Event Viewer**, click **Connect to another computer,** and complete the **Select Computer**dialog box.</span></span>  
  
5.  <span data-ttu-id="96190-112">另外，若要仅显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件，请在 **“查看”** 菜单上单击 **“筛选器”**，并在 **“事件源”** 列表中，选择 **MSSQLSERVER**。</span><span class="sxs-lookup"><span data-stu-id="96190-112">Optionally, to display only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, on the **View** menu click **Filter**, and in the **Event source** list, select **MSSQLSERVER**.</span></span> <span data-ttu-id="96190-113">若要仅查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件，请在 **“事件源”** 列表中选择 **SQLSERVERAGENT** 。</span><span class="sxs-lookup"><span data-stu-id="96190-113">To view only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events, instead select **SQLSERVERAGENT** in the **Event source** list.</span></span>  
  
6.  <span data-ttu-id="96190-114">若要查看有关某事件的详细信息，请双击该事件。</span><span class="sxs-lookup"><span data-stu-id="96190-114">To view more information about an event, double-click the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96190-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96190-115">See Also</span></span>  
 [<span data-ttu-id="96190-116">查看 SQL Server 错误日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="96190-116">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
