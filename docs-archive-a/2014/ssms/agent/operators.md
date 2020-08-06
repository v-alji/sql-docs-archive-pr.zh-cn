---
title: 操作员 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- operators (users) [Database Engine]
- fail-safe operator [SQL Server]
- aliases [SQL Server], operators
- SQL Server Agent alerts, operators
- contact information [SQL Server Agent]
- net send [SQL Server]
- e-mail [SQL Server], SQL Server Agent operators
- pager notifications [SQL Server Agent]
- mail [SQL Server], SQL Server Agent operators
- operators (users) [Database Engine], defining
- jobs [SQL Server Agent], operators
- alerts [SQL Server], operators
ms.assetid: 38e8488f-2669-4cea-b9c3-5f394a663678
author: stevestein
ms.author: sstein
ms.openlocfilehash: d141a2db9a69603701200bc50dcac57ef402968a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691492"
---
# <a name="operators"></a><span data-ttu-id="0a80d-102">运算符</span><span class="sxs-lookup"><span data-stu-id="0a80d-102">Operators</span></span>
  <span data-ttu-id="0a80d-103">操作员是在完成作业或出现警报时可以接收电子通知的人员或组的别名。</span><span class="sxs-lookup"><span data-stu-id="0a80d-103">Operators are aliases for people or groups that can receive electronic notification when jobs have completed or alerts have been raised.</span></span> <span data-ttu-id="0a80d-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务支持通过操作员通知管理员的功能。</span><span class="sxs-lookup"><span data-stu-id="0a80d-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service supports the notification of administrators through operators.</span></span> <span data-ttu-id="0a80d-105">运算员可以通知和监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的功能。</span><span class="sxs-lookup"><span data-stu-id="0a80d-105">Operators enable notification and monitoring capabilities of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="operator-attributes-and-concepts"></a><span data-ttu-id="0a80d-106">运算符属性和概念</span><span class="sxs-lookup"><span data-stu-id="0a80d-106">Operator Attributes and Concepts</span></span>  
 <span data-ttu-id="0a80d-107">操作员的主要属性如下：</span><span class="sxs-lookup"><span data-stu-id="0a80d-107">The primary attributes of an operator are:</span></span>  
  
-   <span data-ttu-id="0a80d-108">操作员名称</span><span class="sxs-lookup"><span data-stu-id="0a80d-108">Operator name</span></span>  
  
-   <span data-ttu-id="0a80d-109">联系信息</span><span class="sxs-lookup"><span data-stu-id="0a80d-109">Contact information</span></span>  
  
### <a name="naming-an-operator"></a><span data-ttu-id="0a80d-110">命名操作员</span><span class="sxs-lookup"><span data-stu-id="0a80d-110">Naming an Operator</span></span>  
 <span data-ttu-id="0a80d-111">每个操作员都必须有一个名称。</span><span class="sxs-lookup"><span data-stu-id="0a80d-111">Every operator must have a name.</span></span> <span data-ttu-id="0a80d-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中，操作员名称必须是唯一的，并且长度不得超过 **128** 个字符。</span><span class="sxs-lookup"><span data-stu-id="0a80d-112">Operator names must be unique within the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and can be no longer than **128** characters.</span></span>  
  
### <a name="contact-information"></a><span data-ttu-id="0a80d-113">联系信息</span><span class="sxs-lookup"><span data-stu-id="0a80d-113">Contact Information</span></span>  
 <span data-ttu-id="0a80d-114">操作员的联系信息决定了通知该操作员的方式。</span><span class="sxs-lookup"><span data-stu-id="0a80d-114">An operator's contact information defines how the operator is notified.</span></span> <span data-ttu-id="0a80d-115">可以通过电子邮件、寻呼程序或 **net send** ：</span><span class="sxs-lookup"><span data-stu-id="0a80d-115">Operators can be notified by e-mail, pager, or through the **net send** command:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a80d-116">在 **的未来版本中，将从** 代理中删除寻呼程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="0a80d-116">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a80d-117">请避免在新的开发工作中使用这些功能，并考虑修改当前使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a80d-117">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="0a80d-118">**电子邮件通知**</span><span class="sxs-lookup"><span data-stu-id="0a80d-118">**E-mail notification**</span></span>  
  
     <span data-ttu-id="0a80d-119">电子邮件通知是向操作员发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="0a80d-119">E-mail notification sends an e-mail message to the operator.</span></span> <span data-ttu-id="0a80d-120">对于电子邮件通知，需要提供操作员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0a80d-120">For e-mail notification, you provide the e-mail address for the operator.</span></span>  
  
-   <span data-ttu-id="0a80d-121">**寻呼通知**</span><span class="sxs-lookup"><span data-stu-id="0a80d-121">**Pager notification**</span></span>  
  
     <span data-ttu-id="0a80d-122">寻呼是通过电子邮件实现的。</span><span class="sxs-lookup"><span data-stu-id="0a80d-122">Paging is implemented by e-mail.</span></span> <span data-ttu-id="0a80d-123">对于寻呼通知，需要提供操作员接收寻呼消息的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0a80d-123">For pager notification, you provide the e-mail address where the operator receives pager messages.</span></span> <span data-ttu-id="0a80d-124">若要设置寻呼通知，必须在邮件服务器上安装软件，处理入站邮件并将其转换为寻呼消息。</span><span class="sxs-lookup"><span data-stu-id="0a80d-124">To set up pager notification, you must install software on the mail server that processes inbound mail and converts it to a pager message.</span></span> <span data-ttu-id="0a80d-125">该软件可以采用若干种方法，其中包括：</span><span class="sxs-lookup"><span data-stu-id="0a80d-125">The software can take one of several approaches, including:</span></span>  
  
    -   <span data-ttu-id="0a80d-126">将邮件转发到寻呼服务提供商站点的远程邮件服务器上。</span><span class="sxs-lookup"><span data-stu-id="0a80d-126">Forwarding the mail to a remote mail server at the site of the pager provider.</span></span>  
  
         <span data-ttu-id="0a80d-127">寻呼服务提供商必须提供这项服务，尽管本地邮件系统上通常都有所需软件。</span><span class="sxs-lookup"><span data-stu-id="0a80d-127">The pager provider must offer this service, although the software required is generally available as part of the local mail system.</span></span> <span data-ttu-id="0a80d-128">有关详细信息，请参阅寻呼文档。</span><span class="sxs-lookup"><span data-stu-id="0a80d-128">For more information, see your pager documentation.</span></span>  
  
    -   <span data-ttu-id="0a80d-129">通过 Internet 将电子邮件传送到寻呼服务提供商站点的电子邮件服务器。</span><span class="sxs-lookup"><span data-stu-id="0a80d-129">Routing the e-mail by way of the Internet to an e-mail server at the pager provider's site.</span></span>  
  
         <span data-ttu-id="0a80d-130">这是第一种方法的变体。</span><span class="sxs-lookup"><span data-stu-id="0a80d-130">This is a variation on the first approach.</span></span>  
  
    -   <span data-ttu-id="0a80d-131">使用附加的调制解调器处理入站电子邮件并拨叫寻呼服务。</span><span class="sxs-lookup"><span data-stu-id="0a80d-131">Processing the inbound e-mail and dialing the pager by using an attached modem.</span></span>  
  
         <span data-ttu-id="0a80d-132">此软件为寻呼服务提供商专有。</span><span class="sxs-lookup"><span data-stu-id="0a80d-132">This software is proprietary to pager service providers.</span></span> <span data-ttu-id="0a80d-133">此软件充当电子邮件客户程序，定期处理收件箱中的邮件，把电子邮件的全部或部分地址信息解释为寻呼号，或将电子邮件名称与转换表中的寻呼号相匹配。</span><span class="sxs-lookup"><span data-stu-id="0a80d-133">The software acts as a e-mail client that periodically processes its inbox either by interpreting all or part of the e-mail address information as a pager number, or by matching the e-mail name to a pager number in a translation table.</span></span>  
  
         <span data-ttu-id="0a80d-134">如果所有操作员共享一个寻呼服务提供商的服务，则可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定寻呼到电子邮件系统需要的任何特殊电子邮件格式。</span><span class="sxs-lookup"><span data-stu-id="0a80d-134">If all of the operators share a pager provider, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to specify any special e-mail formatting that is required by the pager-to-e-mail system.</span></span> <span data-ttu-id="0a80d-135">特殊格式可以是前缀或后缀，可以包含在电子邮件的下列行中：</span><span class="sxs-lookup"><span data-stu-id="0a80d-135">The special formatting can be a prefix or a suffix and can be included in the following lines of the e-mail:</span></span>  
  
         <span data-ttu-id="0a80d-136">**使用者：**</span><span class="sxs-lookup"><span data-stu-id="0a80d-136">**Subject:**</span></span>  
  
         <span data-ttu-id="0a80d-137">**抄送**：</span><span class="sxs-lookup"><span data-stu-id="0a80d-137">**Cc**:</span></span>  
  
         <span data-ttu-id="0a80d-138">**收件人**：</span><span class="sxs-lookup"><span data-stu-id="0a80d-138">**To**:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a80d-139">如果使用的是一个小容量的字母数字寻呼系统，则可以通过从寻呼通知中排除错误文本，缩短发送文本的长度。</span><span class="sxs-lookup"><span data-stu-id="0a80d-139">If you use a low-capacity alphanumeric paging system, you can shorten the text that is sent by excluding the error text from the pager notification.</span></span> <span data-ttu-id="0a80d-140">每页限制在 64 个字符内就是一个小容量的字母数字寻呼系统。</span><span class="sxs-lookup"><span data-stu-id="0a80d-140">An example of a low-capacity alphanumeric paging system is one that is limited to 64 characters per page.</span></span>  
  
-   <span data-ttu-id="0a80d-141">**net sendnotification**</span><span class="sxs-lookup"><span data-stu-id="0a80d-141">**net sendnotification**</span></span>  
  
     <span data-ttu-id="0a80d-142">此方式通过 **net send** 命令向操作员发送消息。</span><span class="sxs-lookup"><span data-stu-id="0a80d-142">This sends a message to the operator by means of the **net send** command.</span></span> <span data-ttu-id="0a80d-143">对于 **net send**，需要指定网络消息的收件人（计算机或用户）。</span><span class="sxs-lookup"><span data-stu-id="0a80d-143">For **net send**, specify the recipient (computer or user) of a network message.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a80d-144">**net send** 命令使用 Microsoft Windows Messenger。</span><span class="sxs-lookup"><span data-stu-id="0a80d-144">The **net send** command uses Microsoft Windows Messenger.</span></span> <span data-ttu-id="0a80d-145">若要成功发送警报，此服务必须同时在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机和操作员使用的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="0a80d-145">To successfully send alerts, this service must be running on both the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running and the computer that the operator uses.</span></span>  
  
## <a name="alerting-and-fail-safe-operators"></a><span data-ttu-id="0a80d-146">警报和防故障操作员</span><span class="sxs-lookup"><span data-stu-id="0a80d-146">Alerting and Fail-Safe Operators</span></span>  
 <span data-ttu-id="0a80d-147">可以选择在发生警报时要通知的操作员。</span><span class="sxs-lookup"><span data-stu-id="0a80d-147">You can choose which operators are to be notified in response to an alert.</span></span> <span data-ttu-id="0a80d-148">例如，可以通过计划警报来指定操作员轮流接收通知，</span><span class="sxs-lookup"><span data-stu-id="0a80d-148">For example, you can assign rotating responsibilities for operator notification by scheduling alerts.</span></span> <span data-ttu-id="0a80d-149">如果星期一、星期三和星期五出现警报，则通知操作员 A；如果星期二、星期四和星期六出现警报，则通知操作员 B；</span><span class="sxs-lookup"><span data-stu-id="0a80d-149">For example, Individual A is notified of alerts that occur on Monday, Wednesday, or Friday, and Individual B is notified of alerts that occur on Tuesday, Thursday, or Saturday.</span></span>  
  
 <span data-ttu-id="0a80d-150">向指定操作员发送的所有寻呼通知失败后，防故障操作员将收到警报通知。</span><span class="sxs-lookup"><span data-stu-id="0a80d-150">The fail-safe operator receives an alert notification after all pager notifications to the designated operators have failed.</span></span> <span data-ttu-id="0a80d-151">例如，如果定义了三个接收寻呼通知的操作员，但无法呼叫到任一指定操作员，则将通知防故障操作员。</span><span class="sxs-lookup"><span data-stu-id="0a80d-151">For example, if you have defined three operators for pager notifications and none of the designated operators can be paged, the fail-safe operator is notified.</span></span>  
  
 <span data-ttu-id="0a80d-152">在下列情况下将通知防故障操作员：</span><span class="sxs-lookup"><span data-stu-id="0a80d-152">The fail-safe operator is notified when:</span></span>  
  
-   <span data-ttu-id="0a80d-153">无法通过寻呼呼叫负责警报的操作员。</span><span class="sxs-lookup"><span data-stu-id="0a80d-153">The operators responsible for the alert could not be paged.</span></span>  
  
     <span data-ttu-id="0a80d-154">无法到达主要操作员的原因包括寻呼地址错误和操作员不在岗位。</span><span class="sxs-lookup"><span data-stu-id="0a80d-154">Reasons for failure to reach primary operators include incorrect pager addresses and off-duty operators.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0a80d-155">代理无法访问 **msdb** 数据库中的系统表。</span><span class="sxs-lookup"><span data-stu-id="0a80d-155">Agent cannot access system tables in the **msdb** database.</span></span>  
  
     <span data-ttu-id="0a80d-156">**sysnotifications** 系统表可指定负责警报的操作员。</span><span class="sxs-lookup"><span data-stu-id="0a80d-156">The **sysnotifications** system table specifies operator responsibilities for alerts.</span></span>  
  
 <span data-ttu-id="0a80d-157">防故障操作员是一种安全性能。</span><span class="sxs-lookup"><span data-stu-id="0a80d-157">The fail-safe operator is a security feature.</span></span> <span data-ttu-id="0a80d-158">在未将防故障职责重新分配给其他操作员或未完全删除防故障分配的情况下，无法删除已分配防故障职责的操作员。</span><span class="sxs-lookup"><span data-stu-id="0a80d-158">You cannot delete the operator assigned to fail-safe duty without reassigning fail-safe duty to another operator, or deleting the fail-safe assignment altogether.</span></span>  
  
## <a name="notifying-an-operator"></a><span data-ttu-id="0a80d-159">通知操作员</span><span class="sxs-lookup"><span data-stu-id="0a80d-159">Notifying an Operator</span></span>  
 <span data-ttu-id="0a80d-160">为了通知操作员，必须设置以下一种或多种方式：</span><span class="sxs-lookup"><span data-stu-id="0a80d-160">You must set up one or more of the following in order to notify an operator:</span></span>  
  
-   <span data-ttu-id="0a80d-161">若要使用数据库邮件功能发送电子邮件，必须具有访问支持 SMTP 的电子邮件服务器的权限。</span><span class="sxs-lookup"><span data-stu-id="0a80d-161">To send e-mail with Database Mail functionality, you must have access to an e-mail server that supports SMTP.</span></span>  
  
-   <span data-ttu-id="0a80d-162">对于寻呼，必须具有第三方的寻呼到电子邮件软件和/或硬件。</span><span class="sxs-lookup"><span data-stu-id="0a80d-162">For paging, you must have third-party pager-to-e-mail software and/or hardware.</span></span>  
  
-   <span data-ttu-id="0a80d-163">若要使用 **net send**，操作员必须登录到指定计算机，并且该指定计算机必须允许使用 Windows Messenger 的消息。</span><span class="sxs-lookup"><span data-stu-id="0a80d-163">To use **net send**, the operator must be logged on to the specified computer, and the specified computer must allow messages from Windows Messenger.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0a80d-164">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0a80d-164">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a80d-165">**任务**</span><span class="sxs-lookup"><span data-stu-id="0a80d-165">**Tasks**</span></span>|<span data-ttu-id="0a80d-166">**主题**</span><span class="sxs-lookup"><span data-stu-id="0a80d-166">**Topic**</span></span>|  
|<span data-ttu-id="0a80d-167">与创建操作员相关的任务</span><span class="sxs-lookup"><span data-stu-id="0a80d-167">Tasks related to creating an operator</span></span>|[<span data-ttu-id="0a80d-168">创建操作员</span><span class="sxs-lookup"><span data-stu-id="0a80d-168">Create an Operator</span></span>](create-an-operator.md)<br /><br /> [<span data-ttu-id="0a80d-169">Designate a Fail-Safe Operator</span><span class="sxs-lookup"><span data-stu-id="0a80d-169">Designate a Fail-Safe Operator</span></span>](designate-a-fail-safe-operator.md)|  
|<span data-ttu-id="0a80d-170">与分配警报相关的任务</span><span class="sxs-lookup"><span data-stu-id="0a80d-170">Tasks related to assigning alerts</span></span>|[<span data-ttu-id="0a80d-171">向操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="0a80d-171">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)<br /><br /> [<span data-ttu-id="0a80d-172">定义对警报的响应 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0a80d-172">Define the Response to an Alert &#40;SQL Server Management Studio&#41;</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)<br /><br /> [<span data-ttu-id="0a80d-173">sp_add_notification &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0a80d-173">sp_add_notification &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)<br /><br /> [<span data-ttu-id="0a80d-174">向操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="0a80d-174">Assign Alerts to an Operator</span></span>](assign-alerts-to-an-operator.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0a80d-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a80d-175">See Also</span></span>  
 [<span data-ttu-id="0a80d-176">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="0a80d-176">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
