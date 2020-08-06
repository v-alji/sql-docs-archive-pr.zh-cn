---
title: 可更新订阅的登录名 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a5cc9190c77f506b13ba8b5fba0e32d5a925570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692841"
---
# <a name="login-for-updatable-subscriptions"></a><span data-ttu-id="3fc70-102">可更新订阅的登录名</span><span class="sxs-lookup"><span data-stu-id="3fc70-102">Login for Updatable Subscriptions</span></span>
  <span data-ttu-id="3fc70-103">如果在此向导的 **“可更新订阅”** 页上选择 **“复制”** ，则必须在与发布服务器建立连接的订阅服务器上指定一个帐户以立即更新订阅。</span><span class="sxs-lookup"><span data-stu-id="3fc70-103">If you selected **Replicate** on the **Updatable Subscriptions** page of this wizard, you must specify an account at the Subscriber under which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="3fc70-104">连接用于在订阅服务器上激发的触发器，这些触发器用于将更改传播到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="3fc70-104">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="3fc70-105">即使在 **“可更新订阅”** 页上选择 **“对更改进行排队并在可能时提交”** ，也需要使用此帐户，因为默认情况下，新建订阅向导将排队更新配置为在必要时可切换到立即更新。</span><span class="sxs-lookup"><span data-stu-id="3fc70-105">This account is required even if you selected **Queue changes and commit when possible** on the **Updatable Subscriptions** page, because by default the New Subscription Wizard configures queued updating with the ability to switch to immediate updating if required.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3fc70-106">对于指定的连接帐户，只能授予对复制功能在发布数据库中创建的视图插入、更新和删除数据的权限，而不应授予任何其他权限。</span><span class="sxs-lookup"><span data-stu-id="3fc70-106">The account specified for the connection should only be granted permission to insert, update, and delete data on the views that replication creates in the publication database; it should not be given any additional permissions.</span></span> <span data-ttu-id="3fc70-107">对于发布数据库（名称格式为 syncobj_\<HexadecimalNumber>）中的视图，请将其权限授予在每个订阅服务器上配置的帐户。</span><span class="sxs-lookup"><span data-stu-id="3fc70-107">Grant permissions on views in the publication database that are named in the form **syncobj_**_\<HexadecimalNumber>_ to the account you configured at each Subscriber.</span></span>  
  
 <span data-ttu-id="3fc70-108">有三种连接类型可以选择：</span><span class="sxs-lookup"><span data-stu-id="3fc70-108">There are three options available for the type of connection:</span></span>  
  
-   <span data-ttu-id="3fc70-109">已定义的链接服务器或远程服务器。</span><span class="sxs-lookup"><span data-stu-id="3fc70-109">A linked server or remote server that you have already defined.</span></span>  
  
-   <span data-ttu-id="3fc70-110">复制创建的链接服务器；用在此向导中指定的凭据建立连接。</span><span class="sxs-lookup"><span data-stu-id="3fc70-110">A linked server that replication creates; the connection is made with the credentials you specify in this wizard.</span></span>  
  
-   <span data-ttu-id="3fc70-111">复制创建的链接服务器；用在订阅服务器上做更改的用户的凭据建立连接。</span><span class="sxs-lookup"><span data-stu-id="3fc70-111">A linked server that replication creates; the connection is made with the credentials of the user making the change at the Subscriber.</span></span>  
  
 <span data-ttu-id="3fc70-112">可以在此向导中指定前两个选项。</span><span class="sxs-lookup"><span data-stu-id="3fc70-112">The first two options can be specified in this wizard.</span></span> <span data-ttu-id="3fc70-113">最后一个选项只能使用[sp_link_publication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)指定;将参数的值指定为**1** **@security_mode** 。</span><span class="sxs-lookup"><span data-stu-id="3fc70-113">The last option can only be specified using [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql); specify a value of **1** for the parameter **@security_mode**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3fc70-114">选项</span><span class="sxs-lookup"><span data-stu-id="3fc70-114">Options</span></span>  
 <span data-ttu-id="3fc70-115">**创建使用以下 SQL Server 身份验证登录名进行连接的链接服务器：**</span><span class="sxs-lookup"><span data-stu-id="3fc70-115">**Create a linked server that connects using the following SQL Server Authentication login:**</span></span>  
 <span data-ttu-id="3fc70-116">复制使用在 **“登录名”** 和 **“密码”** 字段中指定的凭据创建链接服务器。</span><span class="sxs-lookup"><span data-stu-id="3fc70-116">Replication creates a linked server using the credentials specified in the **Login** and **Password** fields.</span></span>  
  
 <span data-ttu-id="3fc70-117">**登录**</span><span class="sxs-lookup"><span data-stu-id="3fc70-117">**Login**</span></span>  
 <span data-ttu-id="3fc70-118">输入仅具有本主题中所描述权限的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="3fc70-118">Enter a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that has only the permissions described in this topic.</span></span>  
  
 <span data-ttu-id="3fc70-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="3fc70-119">**Password**</span></span>  
 <span data-ttu-id="3fc70-120">为 **“登录名”** 中指定的登录名输入一个强密码。</span><span class="sxs-lookup"><span data-stu-id="3fc70-120">Enter a strong password for the login specified in **Login**.</span></span>  
  
 <span data-ttu-id="3fc70-121">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="3fc70-121">**Confirm Password**</span></span>  
 <span data-ttu-id="3fc70-122">重新输入密码以确认密码输入正确。</span><span class="sxs-lookup"><span data-stu-id="3fc70-122">Re-enter the password to confirm that it was entered correctly.</span></span>  
  
 <span data-ttu-id="3fc70-123">**使用您指定的链接服务器或远程服务器。**</span><span class="sxs-lookup"><span data-stu-id="3fc70-123">**Use a linked server or remote server that you have already defined.**</span></span>  
 <span data-ttu-id="3fc70-124">此选项需要使用您所定义的链接服务器或远程服务器。</span><span class="sxs-lookup"><span data-stu-id="3fc70-124">This option requires a linked server or remote server that you have already defined.</span></span> <span data-ttu-id="3fc70-125">有关详细信息，请参阅[链接服务器（数据库引擎）](../linked-servers/linked-servers-database-engine.md)和[远程服务器](../../database-engine/configure-windows/remote-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="3fc70-125">For more information, see [Linked Servers &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md) and [Remote Servers](../../database-engine/configure-windows/remote-servers.md).</span></span> <span data-ttu-id="3fc70-126">请确保用于链接服务器或远程服务器的登录名具有强密码，并且仅具有本主题中描述的权限。</span><span class="sxs-lookup"><span data-stu-id="3fc70-126">Ensure that the login used for the linked server or remote server has a strong password and has only the permissions described in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc70-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fc70-127">See Also</span></span>  
 <span data-ttu-id="3fc70-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span><span class="sxs-lookup"><span data-stu-id="3fc70-128">[Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md) </span></span>  
 <span data-ttu-id="3fc70-129">[查看和修改复制安全设置](security/view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="3fc70-129">[View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md) </span></span>  
 <span data-ttu-id="3fc70-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3fc70-130">[Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="3fc70-131">订阅发布</span><span class="sxs-lookup"><span data-stu-id="3fc70-131">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
