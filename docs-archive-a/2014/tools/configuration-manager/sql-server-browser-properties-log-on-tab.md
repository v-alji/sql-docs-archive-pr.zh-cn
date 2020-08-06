---
title: SQL Server Browser 属性（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682559"
---
# <a name="sql-server-browser-properties-log-on-tab"></a><span data-ttu-id="92b10-102">SQL Server 浏览器属性（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="92b10-102">SQL Server Browser Properties (Log On Tab)</span></span>
  <span data-ttu-id="92b10-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="92b10-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92b10-104">浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="92b10-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92b10-105">浏览器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 解析协议 (SSRP) 侦听 UDP 端口，并接受未经身份验证的请求。</span><span class="sxs-lookup"><span data-stu-id="92b10-105">Browser listens on a UDP port and accepts unauthenticated requests using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP).</span></span>  
  
 <span data-ttu-id="92b10-106">对帐户密码的更改立即生效，无需重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-106">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="92b10-107">选项</span><span class="sxs-lookup"><span data-stu-id="92b10-107">Options</span></span>  
 <span data-ttu-id="92b10-108">**本地系统帐户**</span><span class="sxs-lookup"><span data-stu-id="92b10-108">**Local System account**</span></span>  
 <span data-ttu-id="92b10-109">在本地系统帐户的安全上下文中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-109">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service in the security context of the Local System account.</span></span> <span data-ttu-id="92b10-110">请尽可能使用低权限帐户。</span><span class="sxs-lookup"><span data-stu-id="92b10-110">When possible, use a low-permission account instead.</span></span>  
  
 <span data-ttu-id="92b10-111">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="92b10-111">**This account**</span></span>  
 <span data-ttu-id="92b10-112">指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="92b10-112">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="92b10-113">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="92b10-113">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="92b10-114">有关选择帐户的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="92b10-114">For information about selecting an account, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="92b10-115">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="92b10-115">**Browse**</span></span>  
 <span data-ttu-id="92b10-116">浏览用户或内置安全主体。</span><span class="sxs-lookup"><span data-stu-id="92b10-116">Browse for a user or built-in security principal.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="92b10-117">使用低权限帐户。</span><span class="sxs-lookup"><span data-stu-id="92b10-117">Use a low-permission account.</span></span> <span data-ttu-id="92b10-118">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务所需权限的信息，请参阅 [SQL Server Browser 服务](../../../2014/tools/configuration-manager/sql-server-browser-service.md)中的“安全性”部分。</span><span class="sxs-lookup"><span data-stu-id="92b10-118">For information about the permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Service, see the Security section of [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="92b10-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="92b10-119">**Password**</span></span>  
 <span data-ttu-id="92b10-120">输入安全主体的密码。</span><span class="sxs-lookup"><span data-stu-id="92b10-120">Enter the password of the security principal.</span></span>  
  
 <span data-ttu-id="92b10-121">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="92b10-121">**Confirm password**</span></span>  
 <span data-ttu-id="92b10-122">确认安全主体的密码。</span><span class="sxs-lookup"><span data-stu-id="92b10-122">Confirm the password of the security principal.</span></span>  
  
 <span data-ttu-id="92b10-123">**服务状态**</span><span class="sxs-lookup"><span data-stu-id="92b10-123">**Service status**</span></span>  
 <span data-ttu-id="92b10-124">指示此服务是正在运行、已停止还是已禁用。</span><span class="sxs-lookup"><span data-stu-id="92b10-124">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="92b10-125">“...  ”指明状态更改是挂起的。</span><span class="sxs-lookup"><span data-stu-id="92b10-125">"**...**" indicates a state change is pending.</span></span>  
  
 <span data-ttu-id="92b10-126">**启动**</span><span class="sxs-lookup"><span data-stu-id="92b10-126">**Start**</span></span>  
 <span data-ttu-id="92b10-127">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-127">Start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="92b10-128">**Stop**</span><span class="sxs-lookup"><span data-stu-id="92b10-128">**Stop**</span></span>  
 <span data-ttu-id="92b10-129">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-129">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="92b10-130">**暂停**</span><span class="sxs-lookup"><span data-stu-id="92b10-130">**Pause**</span></span>  
 <span data-ttu-id="92b10-131">暂停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-131">Pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="92b10-132">**恢复**</span><span class="sxs-lookup"><span data-stu-id="92b10-132">**Resume**</span></span>  
 <span data-ttu-id="92b10-133">恢复暂停的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。</span><span class="sxs-lookup"><span data-stu-id="92b10-133">Resume a paused [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b10-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92b10-134">See Also</span></span>  
 [<span data-ttu-id="92b10-135">SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="92b10-135">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
