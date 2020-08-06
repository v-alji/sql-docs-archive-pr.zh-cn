---
title: SQL Server 属性（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 405073fc-eaa3-43c6-bf82-2cd58cacc1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: adec9ed7c69023218baa96ab8f8edbb6f2b365bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587108"
---
# <a name="sql-server-properties-log-on-tab"></a><span data-ttu-id="d7386-102">SQL Server 属性（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="d7386-102">SQL Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="d7386-103">使用 **“SQL Server 属性”** 对话框中的 **“登录”** 选项卡，可以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务使用的帐户，更改帐户密码，还可以启动和停止该服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-103">Use the **Log On** tab of the **SQL Server Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service, to change the password of an account, and to start and stop the service.</span></span> <span data-ttu-id="d7386-104">对帐户密码的更改立即生效。</span><span class="sxs-lookup"><span data-stu-id="d7386-104">Changing the password of an account takes effect immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7386-105">更改群集实例的服务使用的帐户名时，新帐户必须是安装期间为待更改服务指定的域组的成员，或者您必须具有向该组添加成员的权限。</span><span class="sxs-lookup"><span data-stu-id="d7386-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="d7386-106">如果您无权修改组成员身份，请与域管理员联系。</span><span class="sxs-lookup"><span data-stu-id="d7386-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
>   
>  <span data-ttu-id="d7386-107">有关选择帐户以运行服务的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机帮助中的“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="d7386-107">For more information about selecting an account to run the service, see "Setting Up Windows Service Accounts" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7386-108">选项</span><span class="sxs-lookup"><span data-stu-id="d7386-108">Options</span></span>  
 <span data-ttu-id="d7386-109">**内置帐户**</span><span class="sxs-lookup"><span data-stu-id="d7386-109">**Built-in account**</span></span>  
 <span data-ttu-id="d7386-110">**Local System**</span><span class="sxs-lookup"><span data-stu-id="d7386-110">**Local System**</span></span>  
 -   <span data-ttu-id="d7386-111">指定本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="d7386-111">Specify the local system account.</span></span> <span data-ttu-id="d7386-112">该帐户不需要密码。</span><span class="sxs-lookup"><span data-stu-id="d7386-112">This account does not require a password.</span></span> <span data-ttu-id="d7386-113">但是，本地系统帐户可能会阻止该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="d7386-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="d7386-114">**Local Service**</span><span class="sxs-lookup"><span data-stu-id="d7386-114">**Local Service**</span></span>  
 -   <span data-ttu-id="d7386-115">指定本地服务帐户。</span><span class="sxs-lookup"><span data-stu-id="d7386-115">Specify the local service account.</span></span> <span data-ttu-id="d7386-116">该帐户不需要密码。</span><span class="sxs-lookup"><span data-stu-id="d7386-116">This account does not require a password.</span></span> <span data-ttu-id="d7386-117">不过，本地服务帐户可能会阻止该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="d7386-117">However, the local service account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="d7386-118">**Network Service**</span><span class="sxs-lookup"><span data-stu-id="d7386-118">**Network Service**</span></span>  
 -   <span data-ttu-id="d7386-119">建议不要将网络服务帐户用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-119">We recommend that you do not use the Network Service account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services.</span></span> <span data-ttu-id="d7386-120">Local User 帐户或 Domain User 帐户更适用于这些服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-120">Local User or Domain User accounts are more appropriate for these services.</span></span>  
  
 <span data-ttu-id="d7386-121">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="d7386-121">**This account**</span></span>  
 <span data-ttu-id="d7386-122">指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d7386-122">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="d7386-123">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d7386-123">We recommend that you use a domain user account that has minimal rights for services.</span></span>  
  
 <span data-ttu-id="d7386-124">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="d7386-124">**Account Name**</span></span>  
 <span data-ttu-id="d7386-125">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="d7386-125">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="d7386-126">**密码**</span><span class="sxs-lookup"><span data-stu-id="d7386-126">**Password**</span></span>  
 <span data-ttu-id="d7386-127">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="d7386-127">Type the password of the account.</span></span>  
  
 <span data-ttu-id="d7386-128">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="d7386-128">**Confirm password**</span></span>  
 <span data-ttu-id="d7386-129">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="d7386-129">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="d7386-130">**启动**</span><span class="sxs-lookup"><span data-stu-id="d7386-130">**Start**</span></span>  
 <span data-ttu-id="d7386-131">启动服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-131">Start the service.</span></span>  
  
 <span data-ttu-id="d7386-132">**Stop**</span><span class="sxs-lookup"><span data-stu-id="d7386-132">**Stop**</span></span>  
 <span data-ttu-id="d7386-133">停止服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-133">Stop the service.</span></span>  
  
 <span data-ttu-id="d7386-134">**暂停**</span><span class="sxs-lookup"><span data-stu-id="d7386-134">**Pause**</span></span>  
 <span data-ttu-id="d7386-135">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-135">Pause the service.</span></span>  
  
 <span data-ttu-id="d7386-136">**恢复**</span><span class="sxs-lookup"><span data-stu-id="d7386-136">**Resume**</span></span>  
 <span data-ttu-id="d7386-137">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-137">Resume a paused service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d7386-138">默认情况下，只有本地管理员组的成员能够启动、停止、暂停、继续或重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="d7386-138">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="d7386-139">若要向管理员之外的用户授予管理服务的权限，请参阅 [如何授予用户管理 Windows Server 2003 中的服务的权限](https://support.microsoft.com/kb/325349)。</span><span class="sxs-lookup"><span data-stu-id="d7386-139">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="d7386-140">（此过程在其他 Windows 版本上是类似的。）</span><span class="sxs-lookup"><span data-stu-id="d7386-140">(The process is similar on other versions of Windows.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7386-141">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时，如果出现包含短语“未实现 [0x80004001]”的 WMI 错误，则可能指示目标计算机上未安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7386-141">When starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a WMI error containing the phrase "not implemented [0x80004001]" may indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not installed on the target computer.</span></span>  
  
  
