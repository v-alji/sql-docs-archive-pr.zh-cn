---
title: 为 CDC 准备 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dafa29d9bdb0c27decb605398a6d1cfe383427e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579008"
---
# <a name="prepare-sql-server-for-cdc"></a><span data-ttu-id="cdec3-102">为 CDC 准备 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cdec3-102">Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="cdec3-103">Oracle CDC 服务要求所有目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都包含 MSXDBCDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="cdec3-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="cdec3-104">您可以在 CDC 服务配置控制台中使用“准备 SQL Server”操作创建此数据库。</span><span class="sxs-lookup"><span data-stu-id="cdec3-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.</span></span> <span data-ttu-id="cdec3-105">这将创建一个特殊的脚本，运行此脚本可创建所需的表、存储过程以及此数据库的其他所需项目。</span><span class="sxs-lookup"><span data-stu-id="cdec3-105">This creates a special script that is run to create the required tables, stored procedures, and other required artifacts for this database.</span></span> <span data-ttu-id="cdec3-106">只能为每个目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例执行一次此任务。</span><span class="sxs-lookup"><span data-stu-id="cdec3-106">This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="cdec3-107">有关 MSXDBCDC 数据库的详细信息，请参阅“MSXDBCDC 数据库”。</span><span class="sxs-lookup"><span data-stu-id="cdec3-107">For more information about the MSXDBCDC database, see The MSXDBCDC Database.</span></span>  
  
 <span data-ttu-id="cdec3-108">在 CDC 服务配置控制台中，单击“准备 SQL Server”。 </span><span class="sxs-lookup"><span data-stu-id="cdec3-108">In the CDC Service Configuration Console, click **Prepare SQL Server**.</span></span> <span data-ttu-id="cdec3-109">如果此选项不可用，则请确保在该控制台的左侧窗格中选择了“本地 CDC 服务”。 </span><span class="sxs-lookup"><span data-stu-id="cdec3-109">If this option is not available, make sure that **Local CDC Services** is selected in the left pane of the console.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cdec3-110">选项</span><span class="sxs-lookup"><span data-stu-id="cdec3-110">Options</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="cdec3-111">服务器名称</span><span class="sxs-lookup"><span data-stu-id="cdec3-111">Server Name</span></span>  
 <span data-ttu-id="cdec3-112">键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="cdec3-112">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="cdec3-113">身份验证</span><span class="sxs-lookup"><span data-stu-id="cdec3-113">Authentication</span></span>  
 <span data-ttu-id="cdec3-114">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="cdec3-114">Select one of the following:</span></span>  
  
-   <span data-ttu-id="cdec3-115">**Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="cdec3-115">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="cdec3-116">**SQL Server 身份验证**：如果选择此选项，则必须在连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中为用户键入“用户名”  和“密码”  。</span><span class="sxs-lookup"><span data-stu-id="cdec3-116">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="cdec3-117">若要为 Oracle CDC 准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，该登录名必须对 MSXDBCDC 数据库具有写入权限。</span><span class="sxs-lookup"><span data-stu-id="cdec3-117">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="cdec3-118">输入对 MSXDBCDC 数据库具有写入权限的登录名的凭据，例如 `sysasmin` 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="cdec3-118">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
### <a name="options"></a><span data-ttu-id="cdec3-119">选项</span><span class="sxs-lookup"><span data-stu-id="cdec3-119">Options</span></span>  
 <span data-ttu-id="cdec3-120">单击箭头可以查看要配置的可用选项。</span><span class="sxs-lookup"><span data-stu-id="cdec3-120">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="cdec3-121">您可以选择保留这些选项不变，使用其默认值。</span><span class="sxs-lookup"><span data-stu-id="cdec3-121">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="cdec3-122">可用选项是：</span><span class="sxs-lookup"><span data-stu-id="cdec3-122">The available options are:</span></span>  
  
-   <span data-ttu-id="cdec3-123">**连接超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC 服务将等待与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，超过该时间后即超时。默认值为 **15**。</span><span class="sxs-lookup"><span data-stu-id="cdec3-123">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="cdec3-124">**执行超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC Windows 服务将等待命令执行，超过该时间后即超时。默认值为 **30**。</span><span class="sxs-lookup"><span data-stu-id="cdec3-124">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="cdec3-125">**加密连接**：选择“加密连接”  将使用加密连接进行 Oracle CDC 服务和目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间的通信。</span><span class="sxs-lookup"><span data-stu-id="cdec3-125">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="cdec3-126">**高级**：根据需要键入任何其他连接属性。</span><span class="sxs-lookup"><span data-stu-id="cdec3-126">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
### <a name="view-script"></a><span data-ttu-id="cdec3-127">查看脚本</span><span class="sxs-lookup"><span data-stu-id="cdec3-127">View Script</span></span>  
 <span data-ttu-id="cdec3-128">单击“查看脚本”  可查看安装脚本的只读版本。</span><span class="sxs-lookup"><span data-stu-id="cdec3-128">Click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="cdec3-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员可以将此脚本复制到 SQL Server 管理控制台，以便根据需要进行编辑。</span><span class="sxs-lookup"><span data-stu-id="cdec3-129">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the SQL Server Management Console to edit it, if necessary.</span></span> <span data-ttu-id="cdec3-130">有关准备 SQL Server 脚本的详细信息，请参阅 [为 Oracle CDC 视图脚本准备 SQL Server](prepare-sql-server-for-oracle-cdc-view-script.md)。</span><span class="sxs-lookup"><span data-stu-id="cdec3-130">For more information about the Prepare SQL Server Script, see [Prepare SQL Server for Oracle CDC-View Script](prepare-sql-server-for-oracle-cdc-view-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdec3-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdec3-131">See Also</span></span>  
 <span data-ttu-id="cdec3-132">[如何使用 CDC 服务](work-with-cdc-services.md) </span><span class="sxs-lookup"><span data-stu-id="cdec3-132">[How to Work with CDC Services](work-with-cdc-services.md) </span></span>  
 [<span data-ttu-id="cdec3-133">如何为 CDC 准备 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cdec3-133">How to Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
