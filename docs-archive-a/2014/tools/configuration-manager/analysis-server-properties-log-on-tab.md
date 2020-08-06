---
title: Analysis Server 属性（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: a82e0c98-efaa-4b0b-9582-3c879ee42444
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8db5576e48e7f12ef1733175875d2cd065e376fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693595"
---
# <a name="analysis-server-properties-log-on-tab"></a><span data-ttu-id="e59e6-102">分析服务器属性（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="e59e6-102">Analysis Server Properties (Log On Tab)</span></span>
  <span data-ttu-id="e59e6-103">使用 **“分析服务器属性”** 对话框中的 **“登录”** 选项卡可以指定 [!INCLUDE[ssAS](../../includes/ssas-md.md)] 服务使用的帐户，还可以启动和停止该服务。</span><span class="sxs-lookup"><span data-stu-id="e59e6-103">Use the **Log On** tab of the **Analysis Server Properties** dialog box to specify the account used by the [!INCLUDE[ssAS](../../includes/ssas-md.md)] service, and to start and stop the service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e59e6-104">更改群集实例上的服务使用的 **“帐户名”** 时，新帐户必须是安装期间为待更改服务指定的域组的成员，或者您必须有权添加该组的成员。</span><span class="sxs-lookup"><span data-stu-id="e59e6-104">When changing the **Account Name** used by a service on a clustered instance, the new account must either be a member of the domain group specified during setup for the service being changed, or you must have permission to add members to that group.</span></span> <span data-ttu-id="e59e6-105">如果您无权修改组成员身份，请与域管理员联系。</span><span class="sxs-lookup"><span data-stu-id="e59e6-105">If you do not have permission to modify group membership, contact the domain administrator.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e59e6-106">选项</span><span class="sxs-lookup"><span data-stu-id="e59e6-106">Options</span></span>  
 <span data-ttu-id="e59e6-107">**本地系统帐户**</span><span class="sxs-lookup"><span data-stu-id="e59e6-107">**Local System account**</span></span>  
 <span data-ttu-id="e59e6-108">指定一个不要求输入密码的本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="e59e6-108">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="e59e6-109">不过，本地系统帐户可能会限制该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="e59e6-109">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="e59e6-110">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="e59e6-110">**This account**</span></span>  
 <span data-ttu-id="e59e6-111">指定一个使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e59e6-111">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e59e6-112">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="e59e6-112">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="e59e6-113">有关选择帐户的信息，请在联机丛书中搜索主题“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="e59e6-113">For information about selecting an account, search Books Online for the topic Setting Up Windows Service Accounts.</span></span>  
  
 <span data-ttu-id="e59e6-114">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="e59e6-114">**Account Name**</span></span>  
 <span data-ttu-id="e59e6-115">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="e59e6-115">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="e59e6-116">**密码**</span><span class="sxs-lookup"><span data-stu-id="e59e6-116">**Password**</span></span>  
 <span data-ttu-id="e59e6-117">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="e59e6-117">Type the password of the account.</span></span>  
  
 <span data-ttu-id="e59e6-118">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="e59e6-118">**Confirm password**</span></span>  
 <span data-ttu-id="e59e6-119">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="e59e6-119">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="e59e6-120">**启动**</span><span class="sxs-lookup"><span data-stu-id="e59e6-120">**Start**</span></span>  
 <span data-ttu-id="e59e6-121">启动服务。</span><span class="sxs-lookup"><span data-stu-id="e59e6-121">Start the service.</span></span>  
  
 <span data-ttu-id="e59e6-122">**Stop**</span><span class="sxs-lookup"><span data-stu-id="e59e6-122">**Stop**</span></span>  
 <span data-ttu-id="e59e6-123">停止服务。</span><span class="sxs-lookup"><span data-stu-id="e59e6-123">Stop the service.</span></span>  
  
 <span data-ttu-id="e59e6-124">**暂停**</span><span class="sxs-lookup"><span data-stu-id="e59e6-124">**Pause**</span></span>  
 <span data-ttu-id="e59e6-125">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="e59e6-125">Pause the service.</span></span>  
  
 <span data-ttu-id="e59e6-126">**恢复**</span><span class="sxs-lookup"><span data-stu-id="e59e6-126">**Resume**</span></span>  
 <span data-ttu-id="e59e6-127">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="e59e6-127">Resume a paused service.</span></span>  
  
  
