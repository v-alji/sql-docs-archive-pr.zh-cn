---
title: " (常规 \"选项卡上新建或编辑服务器注册)  (Reporting Services) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 195756498dcefe4686d4b06e758dba9919c0b304
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590360"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a><span data-ttu-id="bfb3e-102">新建或编辑服务器注册（“常规”选项卡）(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="bfb3e-102">New or Edit Server Registration (General Tab) (Reporting Services)</span></span>
  <span data-ttu-id="bfb3e-103">在注册 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 实例时，使用此选项卡可以指定选项。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-103">Use this tab to specify options when registering an instance of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bfb3e-104">若要访问此页，请在已注册的服务器中，在“已注册的服务器”\*\*\*\* 工具栏上单击“Reporting Services”\*\*\*\*，右键单击任意已注册的服务器组（如“Reporting Services”\*\*\*\*），指向“新建”\*\*\*\*，再单击“服务器注册”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-104">To access this page, in Registered Servers, click **Reporting Services** on the **Registered Servers** toolbar, right-click any registered servers group such as **Reporting Services**, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfb3e-105">选项</span><span class="sxs-lookup"><span data-stu-id="bfb3e-105">Options</span></span>  
 <span data-ttu-id="bfb3e-106">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-106">**Server type**</span></span>  
 <span data-ttu-id="bfb3e-107">从已注册的服务器注册服务器时，"**服务器类型**" 框是只读的，并且与 "**已注册的服务器**" 窗格中显示的服务器类型匹配。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-107">When a server is registered from Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in the **Registered Servers** pane.</span></span> <span data-ttu-id="bfb3e-108">若要注册其他类型的服务器，请在开始注册新服务器之前，在 **“已注册的服务器”** 工具栏上单击所需的服务器。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-108">To register a different type of server, click the server you want on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="bfb3e-109">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-109">**Server name**</span></span>  
 <span data-ttu-id="bfb3e-110">指定要连接到的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-110">Specify the report server instance to connect to.</span></span> <span data-ttu-id="bfb3e-111">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中，可以通过报表服务器的实例名访问该服务器。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], you can access a report server through its instance name.</span></span> <span data-ttu-id="bfb3e-112">您安装的每个 SQL Server 实例都可以有一个报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-112">You can have one report server instance for each SQL Server instance that you install.</span></span> <span data-ttu-id="bfb3e-113">如果使用默认实例，请键入 SQL Server 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-113">If you are using the default instance, type the name of the SQL Server instance.</span></span> <span data-ttu-id="bfb3e-114">如果使用命名实例，请以 MSSQL$InstanceName 格式指定要连接到报表服务器的命名实例。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-114">If you are using a named instance, specify the named instance to connect to the report server in the format MSSQL$InstanceName.</span></span>  
  
 <span data-ttu-id="bfb3e-115">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-115">**Authentication**</span></span>  
 <span data-ttu-id="bfb3e-116">连接到报表服务器时进行的身份验证是通过 Internet 信息服务 (IIS) 完成的。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-116">Authentication to a report server is made through Internet Information Services (IIS).</span></span> <span data-ttu-id="bfb3e-117">请从以下身份验证模式中选择一个，以便在连接到 Reporting Services 时使用：</span><span class="sxs-lookup"><span data-stu-id="bfb3e-117">Select from one of the following authentication modes when connecting to Reporting Services:</span></span>  
  
 <span data-ttu-id="bfb3e-118">**Windows 身份验证模式（Windows 身份验证）**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-118">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="bfb3e-119">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 凭据连接到报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-119">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="bfb3e-120">**基本身份验证**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-120">**Basic Authentication**</span></span>  
 <span data-ttu-id="bfb3e-121">如果将 Reporting Services 安装配置为使用基本身份验证，则使用“基本身份验证”\*\*\*\* 进行连接。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-121">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="bfb3e-122">**窗体身份验证**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-122">**Forms Authentication**</span></span>  
 <span data-ttu-id="bfb3e-123">如果将 Reporting Services 安装配置为使用自定义身份验证扩展插件，则使用“窗体身份验证”\*\*\*\* 进行连接。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-123">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="bfb3e-124">**用户名**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-124">**User Name**</span></span>  
 <span data-ttu-id="bfb3e-125">输入用于连接的登录名。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-125">Enter the login name to use for the connection.</span></span> <span data-ttu-id="bfb3e-126">只有在选择了 **“基本身份验证”** 或 **“窗体身份验证”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-126">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="bfb3e-127">**密码**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-127">**Password**</span></span>  
 <span data-ttu-id="bfb3e-128">输入用户名的密码。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-128">Enter the password for the user name.</span></span> <span data-ttu-id="bfb3e-129">只有在选择了 **“基本身份验证”** 或 **“窗体身份验证”** 时，此选项才可编辑。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-129">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="bfb3e-130">**记住密码**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-130">**Remember password**</span></span>  
 <span data-ttu-id="bfb3e-131">存储已经输入的密码。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-131">Store the password you have entered.</span></span> <span data-ttu-id="bfb3e-132">只有在单击了 **“基本身份验证”** 或 **“窗体身份验证”** 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-132">This option is only available if you have clicked **Basic** or **Forms Authentication**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfb3e-133">如果已存储了密码并想要停止存储密码，则清除此复选框，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-133">If you have stored the password and want to stop storing it, clear this check box and then click **Save**.</span></span>  
  
 <span data-ttu-id="bfb3e-134">**已注册的服务器名称**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-134">**Registered server name**</span></span>  
 <span data-ttu-id="bfb3e-135">希望在“已注册的服务器”中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-135">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="bfb3e-136">此名称不必与 **“服务器名称”** 框中的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-136">This name does not have to match the name in the **Server name** box.</span></span>  
  
 <span data-ttu-id="bfb3e-137">**已注册的服务器说明**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-137">**Registered server description**</span></span>  
 <span data-ttu-id="bfb3e-138">输入服务器的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-138">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="bfb3e-139">**Test**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-139">**Test**</span></span>  
 <span data-ttu-id="bfb3e-140">单击此项可测试与“服务器名称”\*\*\*\* 中所选服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-140">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="bfb3e-141">**保存**</span><span class="sxs-lookup"><span data-stu-id="bfb3e-141">**Save**</span></span>  
 <span data-ttu-id="bfb3e-142">单击此项可保存已注册服务器的设置。</span><span class="sxs-lookup"><span data-stu-id="bfb3e-142">Click to save the registered server settings.</span></span>  
  
  
