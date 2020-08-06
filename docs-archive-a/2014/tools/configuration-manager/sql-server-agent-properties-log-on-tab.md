---
title: SQL Server 代理属性（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 01fc6329-5d6b-4186-9565-395f375477bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd899e8824adacd07fa1d8d7d51b2143d10cadd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586033"
---
# <a name="sql-server-agent-properties-log-on-tab"></a><span data-ttu-id="bc7e9-102">SQL Server 代理属性（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="bc7e9-102">SQL Server Agent Properties (Log On Tab)</span></span>
  <span data-ttu-id="bc7e9-103">使用 **“SQL Server 代理属性”** 对话框中的 **“登录”** 选项卡，可以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务使用的帐户，还可以启动和停止该服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-103">Use the **Log On** tab of the **SQL Server Agent Properties** dialog box to specify the account used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and to start and stop the service.</span></span> <span data-ttu-id="bc7e9-104">对帐户密码的更改立即生效，无需重新启动服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-104">Changing the password of an account takes effect immediately without restarting the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc7e9-105">更改群集实例的服务使用的帐户名时，新帐户必须是安装期间为待更改服务指定的域组的成员，或者您必须具有向该组添加成员的权限。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-105">When changing the account name used by a service on a clustered instance, the new account must be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="bc7e9-106">如果您无权修改组成员身份，请与域管理员联系。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-106">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bc7e9-107">选项</span><span class="sxs-lookup"><span data-stu-id="bc7e9-107">Options</span></span>  
 <span data-ttu-id="bc7e9-108">**本地系统帐户**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-108">**Local System account**</span></span>  
 <span data-ttu-id="bc7e9-109">指定一个不要求输入密码的本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-109">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="bc7e9-110">不过，本地系统帐户可能会限制该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-110">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="bc7e9-111">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-111">**This account**</span></span>  
 <span data-ttu-id="bc7e9-112">指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-112">Specify a local or domain user account that uses Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="bc7e9-113">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-113">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="bc7e9-114">有关选择帐户的信息，请在联机丛书中搜索“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-114">For information about selecting an account, search Books Online for "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="bc7e9-115">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-115">**Account Name**</span></span>  
 <span data-ttu-id="bc7e9-116">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-116">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="bc7e9-117">**密码**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-117">**Password**</span></span>  
 <span data-ttu-id="bc7e9-118">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-118">Type the password of the account.</span></span>  
  
 <span data-ttu-id="bc7e9-119">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-119">**Confirm password**</span></span>  
 <span data-ttu-id="bc7e9-120">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-120">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="bc7e9-121">**启动**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-121">**Start**</span></span>  
 <span data-ttu-id="bc7e9-122">启动服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-122">Start the service.</span></span>  
  
 <span data-ttu-id="bc7e9-123">**Stop**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-123">**Stop**</span></span>  
 <span data-ttu-id="bc7e9-124">停止服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-124">Stop the service.</span></span>  
  
 <span data-ttu-id="bc7e9-125">**暂停**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-125">**Pause**</span></span>  
 <span data-ttu-id="bc7e9-126">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-126">Pause the service.</span></span>  
  
 <span data-ttu-id="bc7e9-127">**恢复**</span><span class="sxs-lookup"><span data-stu-id="bc7e9-127">**Resume**</span></span>  
 <span data-ttu-id="bc7e9-128">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="bc7e9-128">Resume a paused service.</span></span>  
  
  
