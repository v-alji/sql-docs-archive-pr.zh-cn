---
title: 确定是否已安装并启动数据库引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693085"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a><span data-ttu-id="2bb6b-102">确定是否已安装并启动数据库引擎</span><span class="sxs-lookup"><span data-stu-id="2bb6b-102">Determine Whether the Database Engine Is Installed and Started</span></span>
  <span data-ttu-id="2bb6b-103">成功安装 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 后可将文件安装到文件系统，在注册表中创建注册表项并安装数个工具。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-103">A successful installation of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installs files to the file system, creates entries in the registry, and installs several tools.</span></span> <span data-ttu-id="2bb6b-104">本主题说明如何使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 配置管理器来确定是否已在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中安装并启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-104">This topic describes how to determine whether the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed and started in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2bb6b-105">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="2bb6b-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a><span data-ttu-id="2bb6b-106">如何使用 SQL Server 配置管理器查看和启动数据库引擎</span><span class="sxs-lookup"><span data-stu-id="2bb6b-106">How to view and start the Database Engine by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="2bb6b-107">单击 **“开始”** ，依次指向 **“所有程序”** 、 **Microsoft SQL Server**、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-107">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
     <span data-ttu-id="2bb6b-108">如果在 **“开始”** 菜单中没有这些项，则不能正确安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-108">If you do not have these entries on the **Start** menu, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not correctly installed.</span></span> <span data-ttu-id="2bb6b-109">运行安装程序以安装 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-109">Run Setup to install the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bb6b-110">在 **SQL Server 配置管理器**的左窗格中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-110">In **SQL Server Configuration Manager**, on the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="2bb6b-111">此时右窗格列出多项与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]相关的服务。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-111">The right pane lists several services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2bb6b-112">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 作为默认实例安装，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务将作为 SQL Server (MSSQLSERVER) 列出；如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 作为命名实例安装，则该服务将作为 SQL Server (\<*instance_name*>) 列出  。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-112">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is listed as **SQL Server (MSSQLSERVER)** if it is the default instance; or **SQL Server (**\<*instance_name*>**)**, if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed as a named instance.</span></span> <span data-ttu-id="2bb6b-113">除非更改实例名称，否则将 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 安装为具有名称 **SQLEXPRESS**的命名实例。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-113">Unless the instance name is changed, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as a named instance with the name **SQLEXPRESS**.</span></span> <span data-ttu-id="2bb6b-114">绿色的三角形图标指示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在运行。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-114">A green triangle icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is running.</span></span> <span data-ttu-id="2bb6b-115">红色的正方形图标指示[!INCLUDE[ssDE](../../includes/ssde-md.md)]已停止。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-115">A red square icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is stopped.</span></span>  
  
3.  <span data-ttu-id="2bb6b-116">若要启动[!INCLUDE[ssDE](../../includes/ssde-md.md)]，请在右窗格中，右键单击 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，再单击“启动”。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-116">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)], in the right pane, right-click the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Start**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2bb6b-117">安装过程中，用户可以选择安装程序文件和数据库文件的位置。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-117">During setup, the user can select a location in which to install the program files and the database files.</span></span> <span data-ttu-id="2bb6b-118">如果用户接受默认位置，文件将安装到 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] 和 C:\Program Files\Microsoft SQL Server\MSSQL.*x*，其中 *x* 为编号。</span><span class="sxs-lookup"><span data-stu-id="2bb6b-118">If the user accepts the default location, the files are installed to [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] and C:\Program Files\Microsoft SQL Server\MSSQL.*x*, where *x* is a number.</span></span>  
  
  
