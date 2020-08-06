---
title: 未知的服务 ("登录" 选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e9b35cb5-d8ae-42ea-b59e-deedc99c4823
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0bda49cd95475d4f922f41ebe1701a814c3f60fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578611"
---
# <a name="unknown-service-log-on-tab"></a><span data-ttu-id="c2de2-102">未知服务（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="c2de2-102">Unknown Service (Log On Tab)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c2de2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器无法识别此服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is unable to identify this service.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c2de2-104">配置管理器从运行此服务的计算机上的 WMI 提供程序接收服务信息。</span><span class="sxs-lookup"><span data-stu-id="c2de2-104">Configuration Manager receives service information from the WMI provider on the computer running the service.</span></span> <span data-ttu-id="c2de2-105">读取服务属性时出错，或者服务属性不完整。</span><span class="sxs-lookup"><span data-stu-id="c2de2-105">Either there was an error while reading the service properties, or the service properties are not complete.</span></span> <span data-ttu-id="c2de2-106">若要解决此问题，请尝试关闭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器并将其重新打开，或者检查运行此服务的计算机上的 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c2de2-106">To resolve the problem, try closing and reopening [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or check the WMI provider on the computer running the service.</span></span>  
  
 <span data-ttu-id="c2de2-107">WMI 提供程序是 Windows 组件。</span><span class="sxs-lookup"><span data-stu-id="c2de2-107">The WMI provider is a Windows component.</span></span> <span data-ttu-id="c2de2-108">有关如何检查对 WMI 提供程序的权限的信息，请参阅 SQL Server 联机丛书中的“如何在 SQL Server 工具中将 WMI 配置为显示服务器状态”。</span><span class="sxs-lookup"><span data-stu-id="c2de2-108">For information on how to check permissions on the WMI provider, see "How to: Configure WMI to Show Server Status in SQL Server Tools" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="c2de2-109">如果您认为自己查看的服务是正确的，请使用 **“未知服务属性”** 对话框中的 **“登录”** 选项卡，指定此服务使用的帐户，以及启动和停止此服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-109">If you believe you are viewing the correct service, use the **Log On** tab of the **Unknown Service Properties** dialog box to specify the account used by this service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c2de2-110">选项</span><span class="sxs-lookup"><span data-stu-id="c2de2-110">Options</span></span>  
 <span data-ttu-id="c2de2-111">**本地系统帐户**</span><span class="sxs-lookup"><span data-stu-id="c2de2-111">**Local System account**</span></span>  
 <span data-ttu-id="c2de2-112">指定一个不要求输入密码的本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="c2de2-112">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="c2de2-113">但是，本地系统帐户可能会阻止该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="c2de2-113">However, the local system account may prevent the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="c2de2-114">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="c2de2-114">**This account**</span></span>  
 <span data-ttu-id="c2de2-115">指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c2de2-115">Specify a local or domain user account that uses Windows Authentication.</span></span> <span data-ttu-id="c2de2-116">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c2de2-116">We recommend using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="c2de2-117">有关选择帐户的信息，请参阅 SQL Server 联机丛书中的“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="c2de2-117">For information about selecting an account, "Setting Up Windows Service Accounts" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="c2de2-118">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="c2de2-118">**Account Name**</span></span>  
 <span data-ttu-id="c2de2-119">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="c2de2-119">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="c2de2-120">**密码**</span><span class="sxs-lookup"><span data-stu-id="c2de2-120">**Password**</span></span>  
 <span data-ttu-id="c2de2-121">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="c2de2-121">Type the password of the account.</span></span>  
  
 <span data-ttu-id="c2de2-122">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="c2de2-122">**Confirm password**</span></span>  
 <span data-ttu-id="c2de2-123">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="c2de2-123">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="c2de2-124">**启动**</span><span class="sxs-lookup"><span data-stu-id="c2de2-124">**Start**</span></span>  
 <span data-ttu-id="c2de2-125">启动服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-125">Start the service.</span></span>  
  
 <span data-ttu-id="c2de2-126">**Stop**</span><span class="sxs-lookup"><span data-stu-id="c2de2-126">**Stop**</span></span>  
 <span data-ttu-id="c2de2-127">停止服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-127">Stop the service.</span></span>  
  
 <span data-ttu-id="c2de2-128">**暂停**</span><span class="sxs-lookup"><span data-stu-id="c2de2-128">**Pause**</span></span>  
 <span data-ttu-id="c2de2-129">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-129">Pause the service.</span></span>  
  
 <span data-ttu-id="c2de2-130">**恢复**</span><span class="sxs-lookup"><span data-stu-id="c2de2-130">**Resume**</span></span>  
 <span data-ttu-id="c2de2-131">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="c2de2-131">Resume a paused service.</span></span>  
  
  
