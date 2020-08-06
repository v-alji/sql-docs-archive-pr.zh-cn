---
title: 连接到服务器（“登录”页）数据库引擎 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665a5c491b0bea1145c60d15f1006de97281a30d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690315"
---
# <a name="connect-to-server-login-page-database-engine"></a><span data-ttu-id="d9e9c-102">连接到服务器（“登录”页）数据库引擎</span><span class="sxs-lookup"><span data-stu-id="d9e9c-102">Connect to Server (Login Page) Database Engine</span></span>
  <span data-ttu-id="d9e9c-103">使用此选项卡，可以在连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 时查看或指定选项。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9e9c-104">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接，必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证和 Windows 身份验证模式下配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-104">To connect with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode.</span></span> <span data-ttu-id="d9e9c-105">有关如何确定身份验证模式和更改身份验证模式的详细信息，请参阅[更改服务器身份验证模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-105">For more information about how to determine the authentication mode and to change the authentication mode, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d9e9c-106">选项</span><span class="sxs-lookup"><span data-stu-id="d9e9c-106">Options</span></span>  
 <span data-ttu-id="d9e9c-107">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-107">**Server type**</span></span>  
 <span data-ttu-id="d9e9c-108">从对象资源管理器进行服务器注册时，请选择要连接到何种类型的服务器： [!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-108">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="d9e9c-109">对话框的其余部分只显示适用于所选服务器类型的选项。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-109">The rest of the dialog box shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="d9e9c-110">从“已注册的服务器”注册某服务器时，“服务器类型”  框是只读的，并且与“已注册的服务器”组件中显示的服务器类型匹配。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-110">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="d9e9c-111">若要注册其他类型的服务器，请在开始注册新服务器之前，从“已注册的服务器”工具栏中选择[!INCLUDE[ssDE](../../includes/ssde-md.md)]、Analysis Services、Reporting Services 或 Integration Services。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-111">To register a different type of server, select [!INCLUDE[ssDE](../../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="d9e9c-112">在通过 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库引擎的一个实例时，必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，并且必须在“连接到服务器”  对话框的“连接属性”  选项卡上指定一个数据库。请确保选中“加密连接”  复选框。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-112">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="d9e9c-113">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将连接到 **master**。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-113">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="d9e9c-114">如果您指定一个用户数据库，在对象资源管理器中将只会看到该数据库及其对象。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-114">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="d9e9c-115">如果连接到 **master**，可以看到所有数据库。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-115">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="d9e9c-116">有关详细信息，请参阅[AZURE SQL 数据库概述](/azure/sql-database/sql-database-technical-overview)。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-116">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="d9e9c-117">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-117">**Server name**</span></span>  
 <span data-ttu-id="d9e9c-118">选择要连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-118">Select the server instance to connect to.</span></span> <span data-ttu-id="d9e9c-119">默认情况下，显示上次连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-119">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="d9e9c-120">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-120">**Authentication**</span></span>  
 <span data-ttu-id="d9e9c-121">在连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例时，可以使用两种身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-121">Two authentication modes are available when connecting to an instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d9e9c-122">在通过 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库引擎的一个实例时，必须使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，并且必须在“连接到服务器”  对话框的“连接属性”  选项卡上指定一个数据库。请确保选中“加密连接”  复选框。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-122">When connecting to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine through [!INCLUDE[ssSDS](../../includes/sssds-md.md)], you must use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication and specify a database in the **Connect to Server** dialog box, on the **Connection Properties** tab. Ensure that you select the **Encrypt connection** checkbox.</span></span>  
  
 <span data-ttu-id="d9e9c-123">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将连接到 **master**。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-123">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to **master**.</span></span> <span data-ttu-id="d9e9c-124">如果您指定一个用户数据库，在对象资源管理器中将只会看到该数据库及其对象。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-124">If you specify a user database, you will only see that database and its objects in Object Explorer.</span></span> <span data-ttu-id="d9e9c-125">如果连接到 **master**，可以看到所有数据库。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-125">If you connect to **master**, you will be able to see all databases.</span></span> <span data-ttu-id="d9e9c-126">有关详细信息，请参阅[AZURE SQL 数据库概述](/azure/sql-database/sql-database-technical-overview)。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-126">For more information, see the [Azure SQL Database Overview](/azure/sql-database/sql-database-technical-overview).</span></span>  
  
 <span data-ttu-id="d9e9c-127">**Windows 身份验证模式（Windows 身份验证）**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d9e9c-128">Windows 身份验证模式允许用户通过 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-128">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="d9e9c-129">**SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="d9e9c-130">当用户使用指定的登录名和密码从不可信连接进行连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将通过检查是否已设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户以及指定的密码是否与以前记录的密码匹配，自行进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-130">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="d9e9c-131">如果未设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户，则身份验证失败，并且用户会收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9e9c-132">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="d9e9c-133">**用户名**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-133">**User name**</span></span>  
 <span data-ttu-id="d9e9c-134">输入连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-134">Enter the user name to connect with.</span></span> <span data-ttu-id="d9e9c-135">只有在已选择使用 Windows 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-135">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="d9e9c-136">**登录**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-136">**Login**</span></span>  
 <span data-ttu-id="d9e9c-137">输入连接所用的登录名。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-137">Enter the login to connect with.</span></span> <span data-ttu-id="d9e9c-138">只有选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-138">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d9e9c-139">**密码**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-139">**Password**</span></span>  
 <span data-ttu-id="d9e9c-140">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-140">Enter the password for the login.</span></span> <span data-ttu-id="d9e9c-141">只有在已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接的情况下，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-141">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d9e9c-142">**记住密码**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-142">**Remember password**</span></span>  
 <span data-ttu-id="d9e9c-143">单击此项可使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储您所输入的密码。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-143">Click to have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] store the password you have entered.</span></span> <span data-ttu-id="d9e9c-144">只有在已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-144">This option is only displayed if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d9e9c-145">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-145">**Connect**</span></span>  
 <span data-ttu-id="d9e9c-146">单击此项可连接到在上面选择的服务器。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-146">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="d9e9c-147">**选项**</span><span class="sxs-lookup"><span data-stu-id="d9e9c-147">**Options**</span></span>  
 <span data-ttu-id="d9e9c-148">单击此选项更改对话框并隐藏其他服务器连接选项，例如记住密码。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-148">Click to change the dialog box and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
