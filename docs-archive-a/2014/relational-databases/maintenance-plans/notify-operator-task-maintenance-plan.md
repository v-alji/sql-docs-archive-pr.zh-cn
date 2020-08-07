---
title: “通知操作员”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb59622c2a42de67193c75d545a6b8a2a08863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587814"
---
# <a name="notify-operator-task-maintenance-plan"></a><span data-ttu-id="a86c4-102">“通知操作员”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="a86c4-102">Notify Operator Task (Maintenance Plan)</span></span>
  <span data-ttu-id="a86c4-103">使用 **“‘通知操作员’任务”** 对话框可以向此维护计划中添加自动通知。</span><span class="sxs-lookup"><span data-stu-id="a86c4-103">Use the **Notify Operators Task** dialog to add an automatic notification to this maintenance plan.</span></span> <span data-ttu-id="a86c4-104">要使用此任务，必须启用数据库邮件并将 MSDB 正确配置为邮件主机数据库，并且 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作员具有有效的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="a86c4-104">To use this task you must have Database Mail enabled and properly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
 <span data-ttu-id="a86c4-105">此任务使用 sp_notify_operator 存储过程。</span><span class="sxs-lookup"><span data-stu-id="a86c4-105">This task uses the sp_notify_operator stored procedure.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a86c4-106">选项</span><span class="sxs-lookup"><span data-stu-id="a86c4-106">Options</span></span>  
 <span data-ttu-id="a86c4-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="a86c4-107">**Connection**</span></span>  
 <span data-ttu-id="a86c4-108">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="a86c4-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="a86c4-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="a86c4-109">**New**</span></span>  
 <span data-ttu-id="a86c4-110">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="a86c4-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="a86c4-111">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="a86c4-111">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="a86c4-112">**要通知的操作员**</span><span class="sxs-lookup"><span data-stu-id="a86c4-112">**Operators to notify**</span></span>  
 <span data-ttu-id="a86c4-113">指定电子邮件的收件人。</span><span class="sxs-lookup"><span data-stu-id="a86c4-113">Specify the recipient of the e-mail.</span></span>  
  
 <span data-ttu-id="a86c4-114">**通知消息主题**</span><span class="sxs-lookup"><span data-stu-id="a86c4-114">**Notification message subject**</span></span>  
 <span data-ttu-id="a86c4-115">指定要在通知消息主题行中包括的文本。</span><span class="sxs-lookup"><span data-stu-id="a86c4-115">Specify the text to include in the notification message subject line.</span></span>  
  
 <span data-ttu-id="a86c4-116">**通知消息正文**</span><span class="sxs-lookup"><span data-stu-id="a86c4-116">**Notification message body**</span></span>  
 <span data-ttu-id="a86c4-117">指定要在通知消息正文中包括的文本。</span><span class="sxs-lookup"><span data-stu-id="a86c4-117">Specify the text to include in the notification message body.</span></span>  
  
 <span data-ttu-id="a86c4-118">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="a86c4-118">**View T-SQL**</span></span>  
 <span data-ttu-id="a86c4-119">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="a86c4-119">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a86c4-120">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="a86c4-120">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="a86c4-121">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="a86c4-121">New Connection Dialog Box</span></span>  
 <span data-ttu-id="a86c4-122">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="a86c4-122">**Connection name**</span></span>  
 <span data-ttu-id="a86c4-123">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="a86c4-123">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="a86c4-124">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="a86c4-124">**Select or enter a server name**</span></span>  
 <span data-ttu-id="a86c4-125">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="a86c4-125">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="a86c4-126">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="a86c4-126">**Refresh**</span></span>  
 <span data-ttu-id="a86c4-127">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="a86c4-127">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="a86c4-128">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="a86c4-128">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="a86c4-129">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a86c4-129">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="a86c4-130">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="a86c4-130">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="a86c4-131">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 身份验证连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a86c4-131">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="a86c4-132">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="a86c4-132">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="a86c4-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a86c4-133">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="a86c4-134">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="a86c4-134">This option is not available.</span></span>  
  
 <span data-ttu-id="a86c4-135">**用户名**</span><span class="sxs-lookup"><span data-stu-id="a86c4-135">**User name**</span></span>  
 <span data-ttu-id="a86c4-136">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="a86c4-136">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="a86c4-137">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="a86c4-137">This option is not available.</span></span>  
  
 <span data-ttu-id="a86c4-138">**密码**</span><span class="sxs-lookup"><span data-stu-id="a86c4-138">**Password**</span></span>  
 <span data-ttu-id="a86c4-139">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="a86c4-139">Provide a password to use when authenticating.</span></span> <span data-ttu-id="a86c4-140">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="a86c4-140">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86c4-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a86c4-141">See Also</span></span>  
 <span data-ttu-id="a86c4-142">[数据库邮件](../database-mail/database-mail.md) </span><span class="sxs-lookup"><span data-stu-id="a86c4-142">[Database Mail](../database-mail/database-mail.md) </span></span>  
 [<span data-ttu-id="a86c4-143">sp_notify_operator (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a86c4-143">sp_notify_operator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
