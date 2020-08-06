---
title: SQL 全文筛选器守护程序启动器（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 13e260f9-a75f-430b-88a3-959ddcead8fe
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb3f23907e96214929617bf2923e46148c0ab1f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590462"
---
# <a name="sql-full-text-filter-daemon-launcher-log-on-tab"></a><span data-ttu-id="8ff98-102">SQL 全文筛选器后台程序启动器（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="8ff98-102">SQL Full-text Filter Daemon Launcher (Log On Tab)</span></span>
  <span data-ttu-id="8ff98-103">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]开始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文搜索将使用 SQL 全文筛选器后台程序启动器 (FDHOST Launcher) 服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search.</span></span> <span data-ttu-id="8ff98-104">如果使用全文搜索，则必须运行此服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="8ff98-105">有关筛选器后台程序主机进程的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“全文搜索体系结构”。</span><span class="sxs-lookup"><span data-stu-id="8ff98-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="8ff98-106">使用 **“SQL 全文筛选器后台程序启动器属性”** 对话框的 **“登录”** 选项卡可以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文服务所使用的帐户，还可以更改帐户的密码以及启动和停止此服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-106">Use the **Log On** tab of the **SQL Full-text Filter Daemon Launcher  Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="8ff98-107">更改帐户的密码将在重新启动此服务后生效。</span><span class="sxs-lookup"><span data-stu-id="8ff98-107">Changing the password of an account takes affect after restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ff98-108">更改群集实例的服务所使用的帐户名时，新帐户必须是安装期间为服务指定的域组的成员，或者您必须具有向该组添加成员的权限。</span><span class="sxs-lookup"><span data-stu-id="8ff98-108">When changing the account name used by a service on a clustered instance, either the new account must be a member of the domain group specified during setup for the service, or you must have permission to add members to that group.</span></span> <span data-ttu-id="8ff98-109">如果您无权修改组成员身份，请与域管理员联系。</span><span class="sxs-lookup"><span data-stu-id="8ff98-109">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="8ff98-110">有关选择帐户以运行服务的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机帮助中的“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="8ff98-110">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ff98-111">选项</span><span class="sxs-lookup"><span data-stu-id="8ff98-111">Options</span></span>  
 <span data-ttu-id="8ff98-112">**内置帐户**</span><span class="sxs-lookup"><span data-stu-id="8ff98-112">**Built-in account**</span></span>  
 <span data-ttu-id="8ff98-113">**Local System**</span><span class="sxs-lookup"><span data-stu-id="8ff98-113">**Local System**</span></span>  
 <span data-ttu-id="8ff98-114">指定本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="8ff98-114">Specify the local system account.</span></span> <span data-ttu-id="8ff98-115">该帐户不需要密码。</span><span class="sxs-lookup"><span data-stu-id="8ff98-115">This account does not require a password.</span></span> <span data-ttu-id="8ff98-116">但是，本地系统帐户可能会阻止该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="8ff98-116">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="8ff98-117">**Local Service**</span><span class="sxs-lookup"><span data-stu-id="8ff98-117">**Local Service**</span></span>  
 <span data-ttu-id="8ff98-118">指定本地服务帐户。</span><span class="sxs-lookup"><span data-stu-id="8ff98-118">Specify the local service account.</span></span> <span data-ttu-id="8ff98-119">该帐户不需要密码。</span><span class="sxs-lookup"><span data-stu-id="8ff98-119">This account does not require a password.</span></span> <span data-ttu-id="8ff98-120">不过，本地服务帐户可能会阻止该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="8ff98-120">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="8ff98-121">**Network Service**</span><span class="sxs-lookup"><span data-stu-id="8ff98-121">**Network Service**</span></span>  
 <span data-ttu-id="8ff98-122">我们建议不要使用 Network Service 帐户运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-122">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="8ff98-123">Local User 帐户或 Domain User 帐户更适用于这些服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-123">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="8ff98-124">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="8ff98-124">**This account**</span></span>  
 <span data-ttu-id="8ff98-125">指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8ff98-125">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="8ff98-126">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="8ff98-126">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="8ff98-127">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="8ff98-127">**Account Name**</span></span>  
 <span data-ttu-id="8ff98-128">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="8ff98-128">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="8ff98-129">**密码**</span><span class="sxs-lookup"><span data-stu-id="8ff98-129">**Password**</span></span>  
 <span data-ttu-id="8ff98-130">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="8ff98-130">Type the password of the account.</span></span>  
  
 <span data-ttu-id="8ff98-131">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="8ff98-131">**Confirm password**</span></span>  
 <span data-ttu-id="8ff98-132">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="8ff98-132">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="8ff98-133">**启动**</span><span class="sxs-lookup"><span data-stu-id="8ff98-133">**Start**</span></span>  
 <span data-ttu-id="8ff98-134">启动服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-134">Start the service.</span></span>  
  
 <span data-ttu-id="8ff98-135">**Stop**</span><span class="sxs-lookup"><span data-stu-id="8ff98-135">**Stop**</span></span>  
 <span data-ttu-id="8ff98-136">停止服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-136">Stop the service.</span></span>  
  
 <span data-ttu-id="8ff98-137">**暂停**</span><span class="sxs-lookup"><span data-stu-id="8ff98-137">**Pause**</span></span>  
 <span data-ttu-id="8ff98-138">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-138">Pause the service.</span></span> <span data-ttu-id="8ff98-139">不可用于此服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-139">Not available for this service.</span></span>  
  
 <span data-ttu-id="8ff98-140">**恢复**</span><span class="sxs-lookup"><span data-stu-id="8ff98-140">**Resume**</span></span>  
 <span data-ttu-id="8ff98-141">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="8ff98-141">Resume a paused service.</span></span>  
  
  
