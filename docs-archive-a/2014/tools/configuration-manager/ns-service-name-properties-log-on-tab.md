---
title: NS$&lt;服务名称&gt; 属性（“登录”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 5e6816ec-d4c5-4429-8033-b97427584890
author: stevestein
ms.author: sstein
ms.openlocfilehash: b175895f2385717a67642a41a44dc0d47a1d8d92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692054"
---
# <a name="nsltservice-namegt-properties-log-on-tab"></a><span data-ttu-id="da5a7-102">NS$&lt;服务名称&gt; 属性（“登录”选项卡）</span><span class="sxs-lookup"><span data-stu-id="da5a7-102">NS$&lt;service name&gt; Properties (Log On Tab)</span></span>
  <span data-ttu-id="da5a7-103">使用 **“Notification Services 属性”** 对话框中的 **“登录”** 选项卡可以指定 [!INCLUDE[ssNS](../../includes/ssns-md.md)] 服务使用的帐户，还可以启动和停止该服务。</span><span class="sxs-lookup"><span data-stu-id="da5a7-103">Use the **Log On** tab of the **Notification Services Properties** dialog box to specify the account used by the [!INCLUDE[ssNS](../../includes/ssns-md.md)] service, and to start and stop the service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="da5a7-104">选项</span><span class="sxs-lookup"><span data-stu-id="da5a7-104">Options</span></span>  
 <span data-ttu-id="da5a7-105">**本地系统帐户**</span><span class="sxs-lookup"><span data-stu-id="da5a7-105">**Local System account**</span></span>  
 <span data-ttu-id="da5a7-106">指定一个不要求输入密码的本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="da5a7-106">Specify a local system account, which does not require a password.</span></span> <span data-ttu-id="da5a7-107">不过，本地系统帐户可能会限制该服务与其他服务器进行交互，具体取决于该帐户所拥有的权限。</span><span class="sxs-lookup"><span data-stu-id="da5a7-107">However, the local system account may restrict the service from interacting with other servers, depending on the privileges granted to the account.</span></span>  
  
 <span data-ttu-id="da5a7-108">**本帐户**</span><span class="sxs-lookup"><span data-stu-id="da5a7-108">**This account**</span></span>  
 <span data-ttu-id="da5a7-109">指定一个使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证的本地用户帐户或域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="da5a7-109">Specify a local or domain user account that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="da5a7-110">建议使用具有最低服务权限的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="da5a7-110">recommends using a domain user account with minimal rights for services.</span></span> <span data-ttu-id="da5a7-111">有关选择帐户的详细信息，请在联机丛书中搜索主题“设置 Windows 服务帐户”。</span><span class="sxs-lookup"><span data-stu-id="da5a7-111">For information about selecting an account, search Books Online for the topic, "Setting Up Windows Service Accounts."</span></span>  
  
 <span data-ttu-id="da5a7-112">**帐户名**</span><span class="sxs-lookup"><span data-stu-id="da5a7-112">**Account Name**</span></span>  
 <span data-ttu-id="da5a7-113">指定本地用户帐户名或域用户帐户名。</span><span class="sxs-lookup"><span data-stu-id="da5a7-113">Specify the local or domain user account name.</span></span>  
  
 <span data-ttu-id="da5a7-114">**密码**</span><span class="sxs-lookup"><span data-stu-id="da5a7-114">**Password**</span></span>  
 <span data-ttu-id="da5a7-115">键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="da5a7-115">Type the password of the account.</span></span>  
  
 <span data-ttu-id="da5a7-116">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="da5a7-116">**Confirm password**</span></span>  
 <span data-ttu-id="da5a7-117">再次键入帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="da5a7-117">Type the password of the account again.</span></span>  
  
 <span data-ttu-id="da5a7-118">**启动**</span><span class="sxs-lookup"><span data-stu-id="da5a7-118">**Start**</span></span>  
 <span data-ttu-id="da5a7-119">启动服务。</span><span class="sxs-lookup"><span data-stu-id="da5a7-119">Start the service.</span></span>  
  
 <span data-ttu-id="da5a7-120">**Stop**</span><span class="sxs-lookup"><span data-stu-id="da5a7-120">**Stop**</span></span>  
 <span data-ttu-id="da5a7-121">停止服务。</span><span class="sxs-lookup"><span data-stu-id="da5a7-121">Stop the service.</span></span>  
  
 <span data-ttu-id="da5a7-122">**暂停**</span><span class="sxs-lookup"><span data-stu-id="da5a7-122">**Pause**</span></span>  
 <span data-ttu-id="da5a7-123">暂停服务。</span><span class="sxs-lookup"><span data-stu-id="da5a7-123">Pause the service.</span></span>  
  
 <span data-ttu-id="da5a7-124">**恢复**</span><span class="sxs-lookup"><span data-stu-id="da5a7-124">**Resume**</span></span>  
 <span data-ttu-id="da5a7-125">恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="da5a7-125">Resume a paused service.</span></span>  
  
  
