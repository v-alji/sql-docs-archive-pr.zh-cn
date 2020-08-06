---
title: 如何为 CDC 准备 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a327fa18-58f4-4e69-bb87-44faf47e20ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbd285faaa55a28ad82beb673fa783570809bd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682363"
---
# <a name="how-to-prepare-sql-server-for-cdc"></a><span data-ttu-id="c0063-102">如何为 CDC 准备 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0063-102">How to Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="c0063-103">Oracle CDC 服务要求所有目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都包含 MSXDBCDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="c0063-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="c0063-104">您可以在 CDC 服务配置控制台中使用“准备 SQL Server”操作创建此数据库。只能为每个目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例执行一次此任务。</span><span class="sxs-lookup"><span data-stu-id="c0063-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="c0063-105">下面的内容介绍如何使用 CDC 服务配置控制台为 Oracle 变更数据捕获准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="c0063-105">The following describes how to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for Oracle Change Data Capture using the CDC Service Configuration Console.</span></span> <span data-ttu-id="c0063-106">此过程创建 MSXDBCDC 数据库，并且定义所需的表、存储过程和其他所需项目。</span><span class="sxs-lookup"><span data-stu-id="c0063-106">This process creates the MSXDBCDC database and defines the required tables, stored procedures, and other required artifacts.</span></span>  
  
 <span data-ttu-id="c0063-107">为 Oracle CDC 准备 SQL Server 是由 Oracle CDC 服务管理员进行的。</span><span class="sxs-lookup"><span data-stu-id="c0063-107">Preparing the SQL Server for Oracle CDC is done by the Oracle CDC Service Administrator.</span></span> <span data-ttu-id="c0063-108">有关 CDC 服务管理员角色的详细信息，请参阅[Attunity 适用于 Oracle 的更改数据捕获服务的用户角色](user-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="c0063-108">For more information about the CDC Service Administrator role, see [User Roles for Change Data Capture Service for Oracle by Attunity](user-roles.md).</span></span>  
  
### <a name="to-enable-sql-server-for-cdc"></a><span data-ttu-id="c0063-109">为 CDC 启用 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0063-109">To enable SQL Server for CDC</span></span>  
  
1.  <span data-ttu-id="c0063-110">从 **“开始”** 菜单上，选择 **“Oracle CDC 服务配置”** 。</span><span class="sxs-lookup"><span data-stu-id="c0063-110">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="c0063-111">从左侧的窗格中选择 **“本地 CDC 服务”** ，然后从 **“操作”** 窗格中单击 **“准备 SQL Server”** 。</span><span class="sxs-lookup"><span data-stu-id="c0063-111">From the left pane, select **Local CDC Services** then from the **Actions** pane, click **Prepare SQL Server**.</span></span>  
  
     <span data-ttu-id="c0063-112">还可以右键单击“本地 CDC 服务”  ，然后选择“准备 SQL Server”  。</span><span class="sxs-lookup"><span data-stu-id="c0063-112">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
3.  <span data-ttu-id="c0063-113">在“为 Oracle CDC 准备 SQL Server 实例”对话框中输入所需信息。</span><span class="sxs-lookup"><span data-stu-id="c0063-113">Enter the required information in the Preparing SQL Server Instance for Oracle CDC dialog box.</span></span> <span data-ttu-id="c0063-114">有关如何在此对话框中输入所需信息的信息，请参阅 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)。</span><span class="sxs-lookup"><span data-stu-id="c0063-114">For information on how to enter the required information into this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span>  
  
     <span data-ttu-id="c0063-115">若要为 Oracle CDC 准备 SQL Server 实例，该登录名必须对 MSXDBCDC 数据库具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="c0063-115">To Prepare the SQL Server instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="c0063-116">输入对 MSXDBCDC 数据库具有写入权限的登录名的凭据，例如 `sysasmin` 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="c0063-116">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
 <span data-ttu-id="c0063-117">**注意**：可以单击“查看脚本”  来查看安装脚本的只读版本。</span><span class="sxs-lookup"><span data-stu-id="c0063-117">**Note**: You can click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="c0063-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员可以将此脚本复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理控制台，以便根据需要编辑和执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="c0063-118">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Console to edit and execute it, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0063-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0063-119">See Also</span></span>  
 [<span data-ttu-id="c0063-120">为 CDC 准备 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0063-120">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
