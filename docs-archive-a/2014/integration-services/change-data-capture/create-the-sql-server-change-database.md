---
title: 创建 SQL Server 更改数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaeb26d5bea4c9e50db29aaa45297ba763dbbfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693018"
---
# <a name="create-the-sql-server-change-database"></a><span data-ttu-id="52a6e-102">创建 SQL Server 更改数据库</span><span class="sxs-lookup"><span data-stu-id="52a6e-102">Create the SQL Server Change Database</span></span>
  <span data-ttu-id="52a6e-103">当您启动新建实例向导时，“创建 CDC 数据库”页将打开。</span><span class="sxs-lookup"><span data-stu-id="52a6e-103">When you start the New Instance wizard, the Create CDC Database page opens.</span></span> <span data-ttu-id="52a6e-104">使用“创建 CDC 数据库”页可提供与新的 CDC 实例有关的信息并且创建新的更改数据库。</span><span class="sxs-lookup"><span data-stu-id="52a6e-104">Use the Create CDC Database page to provide information about the new CDC instance and create a new Change database.</span></span>  
  
 <span data-ttu-id="52a6e-105">在您创建新的 CDC 数据库时，将为 SQL Server CDC 启用该数据库，并且此启用将要求作为 `sysadmin` 固定服务器角色的成员的登录名。</span><span class="sxs-lookup"><span data-stu-id="52a6e-105">When you create a new CDC database it is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="52a6e-106">在启动“创建 Oracle CDC 实例”向导的用户不是 `sysadmin` 固定服务器角色的成员时，“连接到 SQL Server”对话框将打开，并且请求 sysadmin 角色成员的凭据以便执行“为 SQL Server CDC 启用数据库”任务。</span><span class="sxs-lookup"><span data-stu-id="52a6e-106">When a user that starts the Create an Oracle CDC Instance wizard is not a member of the `sysadmin` fixed-server role, the Connect to SQL Server dialog box opens and requests the credentials for a member of the sysadmin role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="52a6e-107">在创建 CDC 数据库时， `sysadmin` 登录名将被放弃，并且使用在进入 Oracle 设计器控制台时使用的原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名继续工作。</span><span class="sxs-lookup"><span data-stu-id="52a6e-107">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52a6e-108">对于并非“为 SQL Server CDC 启用数据库”的其他任务，用于运行“新建实例向导”的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名必须具有 `dbcreator` 固定服务器角色，并且对 MSXDBCDC 数据库具有 UPDATE 权限。</span><span class="sxs-lookup"><span data-stu-id="52a6e-108">For tasks other than Enable the database for SQL Server CDC of, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used for running the New Instance Wizard must have the `dbcreator` fixed-server role and UPDATE permissions on the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="52a6e-109">有关在“连接到 SQL Server”对话框中输入数据的信息，请参阅 [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md)。</span><span class="sxs-lookup"><span data-stu-id="52a6e-109">For information on entering the data in the Connect to SQL Server dialog box, see [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="52a6e-110">选项</span><span class="sxs-lookup"><span data-stu-id="52a6e-110">Options</span></span>  
 <span data-ttu-id="52a6e-111">**Oracle CDC 实例**</span><span class="sxs-lookup"><span data-stu-id="52a6e-111">**Oracle CDC Instance**</span></span>  
 <span data-ttu-id="52a6e-112">键入与您正创建的 CDC 实例有关的以下信息。</span><span class="sxs-lookup"><span data-stu-id="52a6e-112">Type the following information about the CDC instance you are creating.</span></span>  
  
-   <span data-ttu-id="52a6e-113">**名称**：键入新服务的名称。</span><span class="sxs-lookup"><span data-stu-id="52a6e-113">**Name**: Type a name for the new service.</span></span> <span data-ttu-id="52a6e-114">该名称将是新的更改数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="52a6e-114">This will also be the name of the new Change database.</span></span>  
  
-   <span data-ttu-id="52a6e-115">**说明**：为新实例键入用于帮助标识它的说明。</span><span class="sxs-lookup"><span data-stu-id="52a6e-115">**Description**: Type a description for the new instance to help you identify it.</span></span> <span data-ttu-id="52a6e-116">此为可选项。</span><span class="sxs-lookup"><span data-stu-id="52a6e-116">This is optional.</span></span>  
  
 <span data-ttu-id="52a6e-117">**SQL Server 更改数据库**</span><span class="sxs-lookup"><span data-stu-id="52a6e-117">**SQL Server Change Database**</span></span>  
 <span data-ttu-id="52a6e-118">此部分用于创建数据库。</span><span class="sxs-lookup"><span data-stu-id="52a6e-118">This section is used to create the database.</span></span>  
  
1.  <span data-ttu-id="52a6e-119">**更改数据库**：新的更改数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="52a6e-119">**Change Database**: The name of the new Change database.</span></span> <span data-ttu-id="52a6e-120">该数据库的名称就是您向实例提供的名称。</span><span class="sxs-lookup"><span data-stu-id="52a6e-120">The name of the database is the same as the name that you gave to the instance.</span></span> <span data-ttu-id="52a6e-121">此只读字段显示数据库的完整路径。</span><span class="sxs-lookup"><span data-stu-id="52a6e-121">This read-only field displays the full path to the database.</span></span>  
  
2.  <span data-ttu-id="52a6e-122">**创建数据库**：单击 **“创建数据库”** 可创建数据库。</span><span class="sxs-lookup"><span data-stu-id="52a6e-122">**Create Database**: Click **Create Database** to create the database.</span></span>  
  
     <span data-ttu-id="52a6e-123">若要创建数据库，该登录名必须具有 `sysasmin` 服务器角色。</span><span class="sxs-lookup"><span data-stu-id="52a6e-123">To create the database, the login must have the `sysasmin` server role.</span></span> <span data-ttu-id="52a6e-124">有关详细信息，请参阅上面的安全说明。</span><span class="sxs-lookup"><span data-stu-id="52a6e-124">See the security note above for more information.</span></span>  
  
     <span data-ttu-id="52a6e-125">创建数据库后，可以单击 **“下一步”** 以便 [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md)。</span><span class="sxs-lookup"><span data-stu-id="52a6e-125">After you create the database, you can click **Next** to [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a6e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52a6e-126">See Also</span></span>  
 <span data-ttu-id="52a6e-127">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="52a6e-127">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="52a6e-128">Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="52a6e-128">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
  
