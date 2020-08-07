---
title: 阻止 SQL Server 的实例自动启动 (SQL Server 配置管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f93f5abc749f589ab4208b3a4c9434ca63b8769
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587598"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="3b55d-102">防止 SQL Server 实例自动启动（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="3b55d-102">Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="3b55d-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中禁止 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例自动启动。</span><span class="sxs-lookup"><span data-stu-id="3b55d-103">This topic describes how prevent an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3b55d-104">通常配置为自动启动。</span><span class="sxs-lookup"><span data-stu-id="3b55d-104">is normally configured to start automatically.</span></span> <span data-ttu-id="3b55d-105">您可以通过将实例的启动模式设置为手动来更改此默认设置。</span><span class="sxs-lookup"><span data-stu-id="3b55d-105">You can change that by setting the start mode for the instance to manual.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3b55d-106">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="3b55d-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a><span data-ttu-id="3b55d-107">防止自动启动 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="3b55d-107">To prevent automatic startup of an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="3b55d-108">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="3b55d-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="3b55d-109">在 SQL Server 配置管理器中，展开 **“服务”** ，再单击 **SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="3b55d-109">In SQL Server Configuration Manager, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="3b55d-110">在“详细信息”窗格中，右键单击“” ，再单击“属性” </span><span class="sxs-lookup"><span data-stu-id="3b55d-110">In the details pane, right-click **MSSQLServer**, and then click **Properties.**</span></span>  
  
4.  <span data-ttu-id="3b55d-111">在 " **SQL Server \<**_instancename_**> 属性**" 对话框的 "**属性**" 框中，将 "**启动模式**" 的值设置为 "**手动**"。</span><span class="sxs-lookup"><span data-stu-id="3b55d-111">In the **SQL Server \<**_instancename_**> Properties** dialog box, in the **Properties** box, set the value of **Start Mode** to **Manual**.</span></span>  
  
5.  <span data-ttu-id="3b55d-112"> 单击“确定”关闭“SQL Server \<**_instancename_**> 属性”对话框，然后再关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="3b55d-112">Click **OK** to close the **SQL Server \<**_instancename_**> Properties** dialog box, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b55d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b55d-113">See Also</span></span>  
 [<span data-ttu-id="3b55d-114">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="3b55d-114">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
