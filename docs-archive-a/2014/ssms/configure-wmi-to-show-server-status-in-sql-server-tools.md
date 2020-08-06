---
title: 在 SQL Server 工具中将 WMI 配置为显示服务器状态 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 138abbe2b7b819d6afd6da62135f7cd7ce86496f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692086"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a><span data-ttu-id="53aff-102">在 SQL Server 工具中将 WMI 配置为显示服务器状态</span><span class="sxs-lookup"><span data-stu-id="53aff-102">Configure WMI to Show Server Status in SQL Server Tools</span></span>
  <span data-ttu-id="53aff-103">本主题介绍了如何在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]中配置 WMI 以便在 SQL Server 工具中显示服务器状态。</span><span class="sxs-lookup"><span data-stu-id="53aff-103">This topic describes how to configure WMI to show the server status in SQL Server tools in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="53aff-104">连接到服务器后，已注册的服务器和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的对象资源管理器组件以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器均使用 Windows Management Instrumentation (WMI) 来获取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理 (MSSQLSERVER) 服务的状态。</span><span class="sxs-lookup"><span data-stu-id="53aff-104">When connecting to servers, both the Registered Servers and Object Explorer components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], as well as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, use Windows Management Instrumentation (WMI) to obtain the status of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER) services.</span></span> <span data-ttu-id="53aff-105">若要显示服务的状态，用户必须具有远程访问 WMI 对象的权限。</span><span class="sxs-lookup"><span data-stu-id="53aff-105">To display the status of the service, the user must have rights to remotely access the WMI object.</span></span> <span data-ttu-id="53aff-106">服务器必须已安装 WMI 才能配置此权限。</span><span class="sxs-lookup"><span data-stu-id="53aff-106">The server must have WMI installed to configure this permission.</span></span>  
  
##  <a name="to-configure-wmi-permission"></a><a name="SSMSProcedure"></a><span data-ttu-id="53aff-107">配置 WMI 权限</span><span class="sxs-lookup"><span data-stu-id="53aff-107">To configure WMI permission</span></span>  
  
1.  <span data-ttu-id="53aff-108">在远程服务器的“开始”  菜单上，单击“运行”  。</span><span class="sxs-lookup"><span data-stu-id="53aff-108">On the **Start** menu on the remote server, click **Run**.</span></span>  
  
2.  <span data-ttu-id="53aff-109">在 "**打开**" 框中键入 `wmimgmt.msc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="53aff-109">In the **Open** box type `wmimgmt.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="53aff-110">在 **Windows 管理体系结构**程序中，右键单击“WMI 控制(本地)”  ，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="53aff-110">In the **Windows Management Infrastructure** program, right-click **WMI Control (Local)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="53aff-111">在“WMI 控制(本地) 属性”  对话框的“安全性”  选项卡中，展开“Root”  ，再单击“CIMV2”  。</span><span class="sxs-lookup"><span data-stu-id="53aff-111">In the **WMI Control (Local) Properties** dialog box, on the **Security** tab, expand **Root**, and then click **CIMV2**.</span></span>  
  
5.  <span data-ttu-id="53aff-112">单击“安全设置”  打开“安全设置 ROOT\CIMV2”  对话框。</span><span class="sxs-lookup"><span data-stu-id="53aff-112">Click **Security** to open the **Security for ROOT\CIMV2** dialog box.</span></span>  
  
6.  <span data-ttu-id="53aff-113">向“组或用户名称”  框中添加一个组或用户，并将其选中。</span><span class="sxs-lookup"><span data-stu-id="53aff-113">Add a group or user to the **Group or user names** box and select it.</span></span>  
  
7.  <span data-ttu-id="53aff-114">在“\<group or user> 权限”框中，为希望远程检测服务状态的用户选择“远程启用”权限的“允许”列。</span><span class="sxs-lookup"><span data-stu-id="53aff-114">In the **Permissions for**_\<group or user>_ box, select the **Allow** column, for the **Remote Enable** permission, for users whom you wish to remotely detect the service status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53aff-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53aff-115">See Also</span></span>  
 [<span data-ttu-id="53aff-116">启动、停止或暂停 SQL Server 代理服务</span><span class="sxs-lookup"><span data-stu-id="53aff-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
