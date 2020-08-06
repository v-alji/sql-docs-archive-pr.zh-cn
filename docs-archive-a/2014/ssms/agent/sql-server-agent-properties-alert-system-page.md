---
title: SQL Server 代理属性（“警报系统”页）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff203be21efbd99b90f02261cfe94dd49bd0d849
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590009"
---
# <a name="sql-server-agent-properties-alert-system-page"></a><span data-ttu-id="aa3be-102">SQL Server 代理属性（“警报系统”页）</span><span class="sxs-lookup"><span data-stu-id="aa3be-102">SQL Server Agent Properties (Alert System Page)</span></span>
  <span data-ttu-id="aa3be-103">使用此页，可以查看和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报发送的消息的设置。</span><span class="sxs-lookup"><span data-stu-id="aa3be-103">Use this page to view and modify the settings for messages sent by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aa3be-104">选项</span><span class="sxs-lookup"><span data-stu-id="aa3be-104">Options</span></span>  
 <span data-ttu-id="aa3be-105">**邮件会话**</span><span class="sxs-lookup"><span data-stu-id="aa3be-105">**Mail session**</span></span>  
 <span data-ttu-id="aa3be-106">此部分中的选项用于配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理邮件。</span><span class="sxs-lookup"><span data-stu-id="aa3be-106">The options in this section configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span>  
  
 <span data-ttu-id="aa3be-107">**启用邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="aa3be-107">**Enable mail profile**</span></span>  
 <span data-ttu-id="aa3be-108">启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理邮件。</span><span class="sxs-lookup"><span data-stu-id="aa3be-108">Enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail.</span></span> <span data-ttu-id="aa3be-109">默认情况下，不启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理邮件。</span><span class="sxs-lookup"><span data-stu-id="aa3be-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Mail is not enabled.</span></span>  
  
 <span data-ttu-id="aa3be-110">**邮件系统**</span><span class="sxs-lookup"><span data-stu-id="aa3be-110">**Mail System**</span></span>  
 <span data-ttu-id="aa3be-111">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理要使用的邮件系统。</span><span class="sxs-lookup"><span data-stu-id="aa3be-111">Sets the mail system for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="aa3be-112">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="aa3be-112">Database Mail</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3be-113">更改电子邮件系统后，必须重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="aa3be-113">After changing the e-mail system, you must restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service for the change to take effect.</span></span>  
  
 <span data-ttu-id="aa3be-114">**邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="aa3be-114">**Mail Profile**</span></span>  
 <span data-ttu-id="aa3be-115">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理要使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="aa3be-115">Sets the profile for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use.</span></span> <span data-ttu-id="aa3be-116">还可以选择 **\<new Database Mail profile...>** 以便创建新的配置文件。</span><span class="sxs-lookup"><span data-stu-id="aa3be-116">You may also select **\<new Database Mail profile...>** to create a new profile.</span></span>  
  
 <span data-ttu-id="aa3be-117">**寻呼电子邮件**</span><span class="sxs-lookup"><span data-stu-id="aa3be-117">**Pager e-mails**</span></span>  
 <span data-ttu-id="aa3be-118">使用此部分中的选项，可以配置发送给寻呼地址的电子邮件，以便与您的寻呼系统协同工作。</span><span class="sxs-lookup"><span data-stu-id="aa3be-118">The options in this section allow you to configure e-mail messages sent to pager addresses to work with your paging system.</span></span>  
  
 <span data-ttu-id="aa3be-119">**寻呼电子邮件的地址格式**</span><span class="sxs-lookup"><span data-stu-id="aa3be-119">**Address formatting for pager e-mails**</span></span>  
 <span data-ttu-id="aa3be-120">使用此部分选项，可以指定包含在寻呼电子邮件中的地址和主题行的格式。</span><span class="sxs-lookup"><span data-stu-id="aa3be-120">This section allows you to specify the format of the addresses and the subject line included in pager e-mails.</span></span>  
  
 <span data-ttu-id="aa3be-121">**“收件人”行**</span><span class="sxs-lookup"><span data-stu-id="aa3be-121">**To line**</span></span>  
 <span data-ttu-id="aa3be-122">指定邮件的“收件人”  行的选项</span><span class="sxs-lookup"><span data-stu-id="aa3be-122">Specifies the options for the **To** line of the message</span></span>  
  
 <span data-ttu-id="aa3be-123">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="aa3be-123">**Prefix**</span></span>  
 <span data-ttu-id="aa3be-124">对于要发送给寻呼程序的邮件，键入系统要求在“收件人”  行开头显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-124">Type any fixed text that your system requires at the beginning of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-125">**寻呼程序**</span><span class="sxs-lookup"><span data-stu-id="aa3be-125">**Pager**</span></span>  
 <span data-ttu-id="aa3be-126">在前缀和后缀之间包括邮件的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa3be-126">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="aa3be-127">**后缀**</span><span class="sxs-lookup"><span data-stu-id="aa3be-127">**Suffix**</span></span>  
 <span data-ttu-id="aa3be-128">对于要发送给寻呼程序的邮件，键入寻呼系统要求在“收件人”  行末尾显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-128">Type any fixed text that your paging system requires at the end of the **To** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-129">**“抄送”行**</span><span class="sxs-lookup"><span data-stu-id="aa3be-129">**Cc line**</span></span>  
 <span data-ttu-id="aa3be-130">指定邮件的“抄送”  行的选项。</span><span class="sxs-lookup"><span data-stu-id="aa3be-130">Specifies options for the **Cc** line of the message.</span></span>  
  
 <span data-ttu-id="aa3be-131">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="aa3be-131">**Prefix**</span></span>  
 <span data-ttu-id="aa3be-132">对于要发送给寻呼程序的邮件，键入系统要求在“抄送”  行开头显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-132">Type any fixed text that your system requires at the beginning of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-133">**寻呼程序**</span><span class="sxs-lookup"><span data-stu-id="aa3be-133">**Pager**</span></span>  
 <span data-ttu-id="aa3be-134">在前缀和后缀之间包括邮件的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa3be-134">Includes the e-mail address for the message between the prefix and the suffix.</span></span>  
  
 <span data-ttu-id="aa3be-135">**后缀**</span><span class="sxs-lookup"><span data-stu-id="aa3be-135">**Suffix**</span></span>  
 <span data-ttu-id="aa3be-136">对于要发送给寻呼程序的邮件，键入寻呼系统要求在“抄送”  行末尾显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-136">Type any fixed text that your paging system requires at the end of the **Cc** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-137">**主题**</span><span class="sxs-lookup"><span data-stu-id="aa3be-137">**Subject**</span></span>  
 <span data-ttu-id="aa3be-138">指定邮件主题的选项。</span><span class="sxs-lookup"><span data-stu-id="aa3be-138">Specifies the options for the subject of the message.</span></span>  
  
 <span data-ttu-id="aa3be-139">**Prefix**</span><span class="sxs-lookup"><span data-stu-id="aa3be-139">**Prefix**</span></span>  
 <span data-ttu-id="aa3be-140">对于要发送给寻呼程序的邮件，键入寻呼系统要求在“主题”  行开头显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-140">Type any fixed text that your paging system requires at the beginning of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-141">**后缀**</span><span class="sxs-lookup"><span data-stu-id="aa3be-141">**Suffix**</span></span>  
 <span data-ttu-id="aa3be-142">对于要发送给寻呼程序的邮件，键入寻呼系统要求在“主题”  行末尾显示的任何固定文本。</span><span class="sxs-lookup"><span data-stu-id="aa3be-142">Type any fixed text that your paging system requires at the end of the **Subject** line of messages sent to a pager.</span></span>  
  
 <span data-ttu-id="aa3be-143">**在通知消息中包含电子邮件正文**</span><span class="sxs-lookup"><span data-stu-id="aa3be-143">**Include body of e-mail in notification message**</span></span>  
 <span data-ttu-id="aa3be-144">在要发送给寻呼程序的消息中包含电子邮件的正文。</span><span class="sxs-lookup"><span data-stu-id="aa3be-144">Includes the body of the e-mail message in the message sent to the pager.</span></span>  
  
 <span data-ttu-id="aa3be-145">**防故障操作员**</span><span class="sxs-lookup"><span data-stu-id="aa3be-145">**Fail-safe operator**</span></span>  
 <span data-ttu-id="aa3be-146">使用此部分选项，可以指定防故障操作员的选项。</span><span class="sxs-lookup"><span data-stu-id="aa3be-146">This section allows you to specify the options for the fail-safe operator.</span></span>  
  
 <span data-ttu-id="aa3be-147">**启用防故障操作员**</span><span class="sxs-lookup"><span data-stu-id="aa3be-147">**Enable fail-safe operator**</span></span>  
 <span data-ttu-id="aa3be-148">指定防故障操作员。</span><span class="sxs-lookup"><span data-stu-id="aa3be-148">Specifies a fail safe operator.</span></span>  
  
 <span data-ttu-id="aa3be-149">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="aa3be-149">**Operator**</span></span>  
 <span data-ttu-id="aa3be-150">设置要接收防故障通知的操作员的名称。</span><span class="sxs-lookup"><span data-stu-id="aa3be-150">Sets the name of the operator to receive fail-safe notifications.</span></span>  
  
 <span data-ttu-id="aa3be-151">**通知方式**</span><span class="sxs-lookup"><span data-stu-id="aa3be-151">**Notify using**</span></span>  
 <span data-ttu-id="aa3be-152">设置用于通知防故障操作员的方式。</span><span class="sxs-lookup"><span data-stu-id="aa3be-152">Sets the method to use for notifying the fail-safe operator.</span></span>  
  
 <span data-ttu-id="aa3be-153">**标记替换**</span><span class="sxs-lookup"><span data-stu-id="aa3be-153">**Token Replacement**</span></span>  
 <span data-ttu-id="aa3be-154">使用此选项，可以启用作业步骤标记，这些标记能够用于由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报运行的作业。</span><span class="sxs-lookup"><span data-stu-id="aa3be-154">This section allows you to enable job step tokens that can be used in jobs run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="aa3be-155">有关作业步骤标记的详细信息，请参阅 [在作业步骤中使用标记](use-tokens-in-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="aa3be-155">For more information about job step tokens, see [Use Tokens in Job Steps](use-tokens-in-job-steps.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aa3be-156">任何对 Windows 事件日志具有写权限的 Windows 用户都可以访问由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报激活的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="aa3be-156">Any Windows user with write permissions on the Windows Event Log may be able to access job steps that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span> <span data-ttu-id="aa3be-157">为了防范此安全隐患，默认情况下，可以在由警报激活的作业中使用的特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理标记已被禁用。</span><span class="sxs-lookup"><span data-stu-id="aa3be-157">To avoid this security risk, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tokens that can be used in jobs activated by alerts are disabled by default.</span></span> <span data-ttu-id="aa3be-158">这些标记包括： **$(A-DBN)** 、 **$(A-SVR)** 、 **$(A-ERR)** 、 **$(A-SEV)** 和 **$(A-MSG)** 。</span><span class="sxs-lookup"><span data-stu-id="aa3be-158">These tokens are: **$(A-DBN)**, **$(A-SVR)**, **$(A-ERR)**, **$(A-SEV)**, and **$(A-MSG)**.</span></span>  
>   
>  <span data-ttu-id="aa3be-159">如果需要使用这些标记，请在启用它们之前，确保只有可信 Windows 安全组（例如 Administrators 组）的成员具有对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在计算机的事件日志的写权限。</span><span class="sxs-lookup"><span data-stu-id="aa3be-159">If you need to use these tokens, ensure that only members of trusted Windows security groups, such as the Administrators group, have write permissions on the Event Log of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resides before enabling them.</span></span>  
  
 <span data-ttu-id="aa3be-160">**为警报的所有作业响应替换标记**</span><span class="sxs-lookup"><span data-stu-id="aa3be-160">**Replace tokens for all job responses to alerts**</span></span>  
 <span data-ttu-id="aa3be-161">选中此复选框可以为由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 警报激活的作业启用标记替换。</span><span class="sxs-lookup"><span data-stu-id="aa3be-161">Select this check box to enable token replacement for jobs that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3be-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa3be-162">See Also</span></span>  
 <span data-ttu-id="aa3be-163">[运算符](operators.md) </span><span class="sxs-lookup"><span data-stu-id="aa3be-163">[Operators](operators.md) </span></span>  
 <span data-ttu-id="aa3be-164">[将 SQL Server 代理 Mail 配置为使用数据库邮件](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="aa3be-164">[Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md) </span></span>  
 [<span data-ttu-id="aa3be-165">数据库邮件</span><span class="sxs-lookup"><span data-stu-id="aa3be-165">Database Mail</span></span>](../../relational-databases/database-mail/database-mail.md)  
  
  
