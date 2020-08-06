---
title: “选择源”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 535d211d6827477fcf029accc27a9000e8c695c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693265"
---
# <a name="select-source-dialog-box"></a><span data-ttu-id="1c9bf-102">“选择源”对话框</span><span class="sxs-lookup"><span data-stu-id="1c9bf-102">Select Source Dialog Box</span></span>
  <span data-ttu-id="1c9bf-103">此对话框用于选择要运行的策略的来源。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-103">Use this dialog box to select the source of the policies to be run.</span></span> <span data-ttu-id="1c9bf-104">若要选择一个或多个包含策略的 XML 文件，请选择 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-104">To select one or more XML files that contain policies, select **Files**.</span></span> <span data-ttu-id="1c9bf-105">若要运行位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上的策略，请选择 **“服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-105">To run the policies that are found on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select **Server**.</span></span>  
  
 <span data-ttu-id="1c9bf-106">打开此对话框有以下几种不同的方法。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-106">You can open this dialog box in several ways.</span></span>  
  
 <span data-ttu-id="1c9bf-107">**打开此对话框**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-107">**To open this dialog box**</span></span>  
  
-   <span data-ttu-id="1c9bf-108">在“已注册的服务器”中，右键单击“本地服务器组”  或“本地服务器组”  下面的任一服务器，或右键单击“中央管理服务器”  下面的任一服务器，然后选择“评估策略”  。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-108">In Registered Servers, right-click **Local Server Groups** or any server under **Local Server Groups**, or any server under **Central Management Servers**, and then select **Evaluate Policies**.</span></span> <span data-ttu-id="1c9bf-109">在“评估策略”对话框的“策略选择”页上单击“浏览”( **...** ) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-109">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="1c9bf-110">在对象资源管理器中，依次展开“管理”  和“策略管理”  ，右键单击“策略”  ，然后选择“导入策略”  。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-110">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and select **Import Policy**.</span></span> <span data-ttu-id="1c9bf-111">在“导入”  对话框中，单击“浏览”( **...** ) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-111">In the **Import** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="1c9bf-112">在对象资源管理器中，右键单击某个服务器、数据库或数据库对象，然后依次选择“策略”  和“评估”  。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-112">In Object Explorer, right-click a server, database, or database object, select **Policies**, and then select **Evaluate**.</span></span> <span data-ttu-id="1c9bf-113">在“评估策略”对话框的“策略选择”页上单击“浏览”( **...** ) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-113">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c9bf-114">选项</span><span class="sxs-lookup"><span data-stu-id="1c9bf-114">Options</span></span>  
 <span data-ttu-id="1c9bf-115">**文件**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-115">**Files**</span></span>  
 <span data-ttu-id="1c9bf-116">选择一个或多个包含策略的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-116">Select one or more XML files that contain policies.</span></span>  
  
 <span data-ttu-id="1c9bf-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-117">**Server**</span></span>  
 <span data-ttu-id="1c9bf-118">用于选择包含要运行的策略的服务器。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-118">Enables you to select a server that contains the policies that you want to run.</span></span>  
  
 <span data-ttu-id="1c9bf-119">**服务器类型**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-119">**Server type**</span></span>  
 <span data-ttu-id="1c9bf-120">仅 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务器包含策略。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-120">Only [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers contain policies.</span></span> <span data-ttu-id="1c9bf-121">此框是只读的。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-121">This box is read-only.</span></span>  
  
 <span data-ttu-id="1c9bf-122">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-122">**Server name**</span></span>  
 <span data-ttu-id="1c9bf-123">选择要连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-123">Select the server instance to connect to.</span></span> <span data-ttu-id="1c9bf-124">默认情况下，显示上次连接到的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-124">By default, the server instance last connected to is displayed.</span></span>  
  
 <span data-ttu-id="1c9bf-125">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-125">**Authentication**</span></span>  
 <span data-ttu-id="1c9bf-126">在连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例时，可以使用两种身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-126">Two authentication modes are available when you connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="1c9bf-127">**Windows 身份验证模式（Windows 身份验证）**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="1c9bf-128">Windows 身份验证模式允许用户通过 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-128">Windows Authentication mode allows for a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="1c9bf-129">**SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="1c9bf-130">当用户使用指定的登录名和密码通过不可信连接进行连接时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将自行进行身份验证，即检查是否已设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户以及指定的密码是否与以前记录的密码相匹配。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-130">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="1c9bf-131">如果未设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录帐户，则身份验证失败，并且用户会收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1c9bf-132">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="1c9bf-133">**用户名**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-133">**User name**</span></span>  
 <span data-ttu-id="1c9bf-134">输入连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-134">Enter the user name to connect with.</span></span> <span data-ttu-id="1c9bf-135">仅当已选择使用 Windows 身份验证进行连接时，才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-135">This option is available only if you have selected to connect by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="1c9bf-136">**登录**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-136">**Login**</span></span>  
 <span data-ttu-id="1c9bf-137">输入连接所用的登录名。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-137">Enter the login to connect with.</span></span> <span data-ttu-id="1c9bf-138">仅当已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-138">This option is available only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="1c9bf-139">**密码**</span><span class="sxs-lookup"><span data-stu-id="1c9bf-139">**Password**</span></span>  
 <span data-ttu-id="1c9bf-140">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-140">Enter the password for the login.</span></span> <span data-ttu-id="1c9bf-141">仅当已选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，才能编辑此选项。</span><span class="sxs-lookup"><span data-stu-id="1c9bf-141">This option is editable only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c9bf-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c9bf-142">See Also</span></span>  
 <span data-ttu-id="1c9bf-143">[策略管理节点（对象资源管理器）](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="1c9bf-143">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="1c9bf-144">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="1c9bf-144">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
