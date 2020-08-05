---
title: 连接到 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6639118b3bd531e5cece8899eb0d68e00e566186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579011"
---
# <a name="connection-to-sql-server"></a><span data-ttu-id="c8592-102">连接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c8592-102">Connection to SQL Server</span></span>
  <span data-ttu-id="c8592-103">在不含对 MSXDBCDC 数据库具有写入权限的数据库角色（例如 **db_owner** 角色）的登录名尝试创建某一 Oracle CDC 实例时，“连接到 SQL Server”对话框将显示。</span><span class="sxs-lookup"><span data-stu-id="c8592-103">When a login without a database role that includes write permission (for example the **db_owner** role) to the MSXDBCDC database attempts to create an Oracle CDC instanced, the Connect to SQL Server dialog box is displayed.</span></span>  
  
 <span data-ttu-id="c8592-104">在此对话框中，必须为对 MSXDBCDC 数据库具有写入权限的登录名（例如 **db_owner** 数据库角色）输入凭据，以便创建新的 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="c8592-104">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role to create the new Oracle CDC instance.</span></span>  
  
 <span data-ttu-id="c8592-105">在“连接到 SQL Server”对话框中输入以下信息。</span><span class="sxs-lookup"><span data-stu-id="c8592-105">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="c8592-106">服务器名称</span><span class="sxs-lookup"><span data-stu-id="c8592-106">Server Name</span></span>  
 <span data-ttu-id="c8592-107">键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="c8592-107">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="c8592-108">身份验证</span><span class="sxs-lookup"><span data-stu-id="c8592-108">Authentication</span></span>  
 <span data-ttu-id="c8592-109">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="c8592-109">Select one of the following:</span></span>  
  
-   <span data-ttu-id="c8592-110">Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="c8592-110">Windows Authentication</span></span>  
  
-   <span data-ttu-id="c8592-111">**SQL Server 身份验证**：如果选择此选项，则必须在连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中为用户键入“登录名”和“密码”。</span><span class="sxs-lookup"><span data-stu-id="c8592-111">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
### <a name="options"></a><span data-ttu-id="c8592-112">选项</span><span class="sxs-lookup"><span data-stu-id="c8592-112">Options</span></span>  
 <span data-ttu-id="c8592-113">单击箭头可以查看要配置的可用选项。</span><span class="sxs-lookup"><span data-stu-id="c8592-113">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="c8592-114">您可以选择保留这些选项不变，使用其默认值。</span><span class="sxs-lookup"><span data-stu-id="c8592-114">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="c8592-115">可用选项是：</span><span class="sxs-lookup"><span data-stu-id="c8592-115">The available options are:</span></span>  
  
-   <span data-ttu-id="c8592-116">**连接超时值**：键入一个时间（秒），未超过该时间，程序将等待建立与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，超过该时间后将生成超时错误。</span><span class="sxs-lookup"><span data-stu-id="c8592-116">**Connection Timeout**: Type the time (in seconds) the program waits for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection to be established before producing a timeout error.</span></span> <span data-ttu-id="c8592-117">默认值为 **15**。</span><span class="sxs-lookup"><span data-stu-id="c8592-117">The default value is **15**.</span></span>  
  
-   <span data-ttu-id="c8592-118">**执行超时值**：键入一个时间（秒），未超过该时间，程序将等待 SQL 命令执行完成，超过该时间后将生成超时错误。</span><span class="sxs-lookup"><span data-stu-id="c8592-118">**Execution Timeout**: Type the time (in seconds) that the program waits for SQL command execution to finish before producing a timeout error.</span></span> <span data-ttu-id="c8592-119">默认值为 **30**。</span><span class="sxs-lookup"><span data-stu-id="c8592-119">The default value is **30**.</span></span>  
  
-   <span data-ttu-id="c8592-120">**加密连接**：选择“加密连接”  可确保对正在建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接进行加密以保护隐私。</span><span class="sxs-lookup"><span data-stu-id="c8592-120">**Encrypt Connection**: Select **Encrypt Connection** to ensure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection that being established is encrypted to guarantee privacy.</span></span>  
  
-   <span data-ttu-id="c8592-121">**高级**：单击“高级”  并根据需要在“高级连接属性”对话框中键入任何附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="c8592-121">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8592-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8592-122">See Also</span></span>  
 [<span data-ttu-id="c8592-123">针对 CDC 服务的 SQL Server 连接所需权限</span><span class="sxs-lookup"><span data-stu-id="c8592-123">SQL Server Connection Required Permissions for the CDC Service</span></span>](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
