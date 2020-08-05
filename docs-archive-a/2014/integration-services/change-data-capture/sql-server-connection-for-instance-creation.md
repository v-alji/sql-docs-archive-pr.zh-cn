---
title: 用于实例创建的 SQL Server 连接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdff17b763257c2a3280981c1f5c16040cc61413
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579006"
---
# <a name="sql-server-connection-for-instance-creation"></a><span data-ttu-id="ce472-102">用于实例创建的 SQL Server 连接</span><span class="sxs-lookup"><span data-stu-id="ce472-102">SQL Server Connection for Instance Creation</span></span>
  <span data-ttu-id="ce472-103">创建 Oracle CDC 实例时首先要执行的步骤之一是在目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上创建 CDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="ce472-103">One of the first steps when creating an Oracle CDC Instance is the creation of a CDC database on the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="ce472-104">将为 SQL Server CDC 启用该 CDC 数据库，并且此启用将要求作为 `sysadmin` 固定服务器角色的成员的登录名。</span><span class="sxs-lookup"><span data-stu-id="ce472-104">This CDC database is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="ce472-105">在启动“创建 Oracle CDC 实例”向导的用户不是 `sysadmin` 固定服务器角色的成员时，“连接到 SQL Server”对话框将打开，并且请求 `sysadmin` 角色成员的凭据以便执行“为 SQL Server CDC 启用数据库”任务   。</span><span class="sxs-lookup"><span data-stu-id="ce472-105">When a user that starts the **Create an Oracle CDC Instance** wizard is not a member of the `sysadmin` fixed-server role, the **Connect to SQL Server** dialog box opens and requests the credentials for a member of the `sysadmin` role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="ce472-106">在创建 CDC 数据库时， `sysadmin` 登录名将被放弃，并且使用在进入 Oracle 设计器控制台时使用的原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名继续工作。</span><span class="sxs-lookup"><span data-stu-id="ce472-106">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="ce472-107">任务列表</span><span class="sxs-lookup"><span data-stu-id="ce472-107">Task List</span></span>  
 <span data-ttu-id="ce472-108">在“连接到 SQL Server”  对话框中输入以下信息。</span><span class="sxs-lookup"><span data-stu-id="ce472-108">Enter the following information in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="ce472-109">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="ce472-109">**Server Name**</span></span>  
 <span data-ttu-id="ce472-110">键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="ce472-110">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="ce472-111">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="ce472-111">**Authentication**</span></span>  
 <span data-ttu-id="ce472-112">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="ce472-112">Select one of the following:</span></span>  
  
-   <span data-ttu-id="ce472-113">**Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="ce472-113">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="ce472-114">**SQL Server 身份验证**：如果选择此选项，则必须在连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中为用户键入“登录名”  和“密码”  。</span><span class="sxs-lookup"><span data-stu-id="ce472-114">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="ce472-115">该登录名必须具有允许访问 MSXCDCDB 数据库的数据库角色。</span><span class="sxs-lookup"><span data-stu-id="ce472-115">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="ce472-116">建议该登录名还具有访问要使用的任何其他数据库的权限，否则，该用户将无法查看这些数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="ce472-116">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
 <span data-ttu-id="ce472-117">**选项**</span><span class="sxs-lookup"><span data-stu-id="ce472-117">**Options**</span></span>  
 <span data-ttu-id="ce472-118">单击箭头可以查看要配置的可用选项。</span><span class="sxs-lookup"><span data-stu-id="ce472-118">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="ce472-119">您可以选择保留这些选项不变，使用其默认值。</span><span class="sxs-lookup"><span data-stu-id="ce472-119">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="ce472-120">可用选项是：</span><span class="sxs-lookup"><span data-stu-id="ce472-120">The available options are:</span></span>  
  
-   <span data-ttu-id="ce472-121">**连接超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC 服务将等待与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，超过该时间后即超时。默认值为 **15**。</span><span class="sxs-lookup"><span data-stu-id="ce472-121">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="ce472-122">**执行超时值**：键入一个时间（秒钟），未超过该时间，Oracle CDC Windows 服务将等待命令执行，超过该时间后即超时。默认值为 **30**。</span><span class="sxs-lookup"><span data-stu-id="ce472-122">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="ce472-123">**加密连接**：选择“加密连接”  将使用加密连接进行 Oracle CDC 服务和目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间的通信。</span><span class="sxs-lookup"><span data-stu-id="ce472-123">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="ce472-124">**高级**：单击“高级”  并根据需要在“高级连接属性”对话框中键入任何附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="ce472-124">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
     <span data-ttu-id="ce472-125">有关“高级连接属性”对话框的信息，请参阅 [高级连接属性](advanced-connection-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ce472-125">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce472-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce472-126">See Also</span></span>  
 <span data-ttu-id="ce472-127">[创建 SQL Server 更改数据库](create-the-sql-server-change-database.md) </span><span class="sxs-lookup"><span data-stu-id="ce472-127">[Create the SQL Server Change Database](create-the-sql-server-change-database.md) </span></span>  
 [<span data-ttu-id="ce472-128">针对 CDC 设计器的 SQL Server 连接所需权限</span><span class="sxs-lookup"><span data-stu-id="ce472-128">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
