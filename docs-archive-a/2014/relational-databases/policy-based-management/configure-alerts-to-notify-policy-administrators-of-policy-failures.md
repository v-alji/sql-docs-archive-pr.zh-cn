---
title: 配置警报以通知策略管理员策略失败情况 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9eb84ced3bb6313dd5920deaf479925556f08fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682818"
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a><span data-ttu-id="2296e-102">配置警报以通知策略管理员策略失败情况</span><span class="sxs-lookup"><span data-stu-id="2296e-102">Configure Alerts to Notify Policy Administrators of Policy Failures</span></span>
  <span data-ttu-id="2296e-103">在使用三种自动评估模式之一的模式执行基于策略的管理策略时，如果发生违反策略的情况，则会在事件日志中写入消息。</span><span class="sxs-lookup"><span data-stu-id="2296e-103">When Policy-Based Management policies are executed in one of the three automated evaluation modes, if a policy violation occurs, a message is written to the event log.</span></span> <span data-ttu-id="2296e-104">若要在事件日志中写入此消息时得到通知，您可以创建一个警报以检测此消息并执行操作。</span><span class="sxs-lookup"><span data-stu-id="2296e-104">To be notified when this message is written to the event log, you can create an alert to detect the message and perform an action.</span></span> <span data-ttu-id="2296e-105">该警报应检测下表所示的消息。</span><span class="sxs-lookup"><span data-stu-id="2296e-105">The alert should detect the messages as shown in the following table.</span></span>  
  
|<span data-ttu-id="2296e-106">执行模式</span><span class="sxs-lookup"><span data-stu-id="2296e-106">Execution mode</span></span>|<span data-ttu-id="2296e-107">消息号</span><span class="sxs-lookup"><span data-stu-id="2296e-107">Message number</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="2296e-108">更改时: 禁止</span><span class="sxs-lookup"><span data-stu-id="2296e-108">On change: prevent</span></span><br /><br /> <span data-ttu-id="2296e-109">（如果为自动）</span><span class="sxs-lookup"><span data-stu-id="2296e-109">(if automatic)</span></span>|<span data-ttu-id="2296e-110">34050</span><span class="sxs-lookup"><span data-stu-id="2296e-110">34050</span></span>|  
|<span data-ttu-id="2296e-111">更改时: 禁止</span><span class="sxs-lookup"><span data-stu-id="2296e-111">On change: prevent</span></span><br /><br /> <span data-ttu-id="2296e-112">（如果为按需）</span><span class="sxs-lookup"><span data-stu-id="2296e-112">(if On demand)</span></span>|<span data-ttu-id="2296e-113">34051</span><span class="sxs-lookup"><span data-stu-id="2296e-113">34051</span></span>|  
|<span data-ttu-id="2296e-114">按计划</span><span class="sxs-lookup"><span data-stu-id="2296e-114">On schedule</span></span>|<span data-ttu-id="2296e-115">34052</span><span class="sxs-lookup"><span data-stu-id="2296e-115">34052</span></span>|  
|<span data-ttu-id="2296e-116">更改时</span><span class="sxs-lookup"><span data-stu-id="2296e-116">On change</span></span>|<span data-ttu-id="2296e-117">34053</span><span class="sxs-lookup"><span data-stu-id="2296e-117">34053</span></span>|  
  
 <span data-ttu-id="2296e-118">若要设置警报以响应基于策略的管理错误消息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2296e-118">To set up an alert to respond to the Policy-Based Management error messages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2296e-119">创建操作员</span><span class="sxs-lookup"><span data-stu-id="2296e-119">Create an Operator</span></span>](../../ssms/agent/create-an-operator.md)  
  
-   [<span data-ttu-id="2296e-120">使用错误号创建警报</span><span class="sxs-lookup"><span data-stu-id="2296e-120">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="2296e-121">向操作员分配警报</span><span class="sxs-lookup"><span data-stu-id="2296e-121">Assign Alerts to an Operator</span></span>](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## <a name="permissions"></a><span data-ttu-id="2296e-122">权限</span><span class="sxs-lookup"><span data-stu-id="2296e-122">Permissions</span></span>  
 <span data-ttu-id="2296e-123">在按需评估策略时，将会在用户的安全上下文中执行这些策略。</span><span class="sxs-lookup"><span data-stu-id="2296e-123">When policies are evaluated on demand, they execute in the security context of the user.</span></span> <span data-ttu-id="2296e-124">若要写入错误日志，用户必须具有 ALTER TRACE 权限或者是 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="2296e-124">To write to the error log, the user must have ALTER TRACE permissions or be a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="2296e-125">具有更低权限的用户评估的策略不会写入事件日志，并且不会触发警报。</span><span class="sxs-lookup"><span data-stu-id="2296e-125">Policies that are evaluated by a user that has less privileges will not write to the event log, and will not fire an alert.</span></span>  
  
 <span data-ttu-id="2296e-126">自动执行模式是以 sysadmin 角色成员的身份执行的。</span><span class="sxs-lookup"><span data-stu-id="2296e-126">The automated execution modes execute as a member of the sysadmin role.</span></span> <span data-ttu-id="2296e-127">这样，策略便可以写入错误日志并引发警报。</span><span class="sxs-lookup"><span data-stu-id="2296e-127">This allows the policy to write to the error log and raise an alert.</span></span>  
  
## <a name="additional-considerations-about-alerts"></a><span data-ttu-id="2296e-128">有关警报的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="2296e-128">Additional Considerations About Alerts</span></span>  
 <span data-ttu-id="2296e-129">请注意下面有关警报的其他注意事项：</span><span class="sxs-lookup"><span data-stu-id="2296e-129">Be aware of the following additional considerations about alerts:</span></span>  
  
-   <span data-ttu-id="2296e-130">仅为启用的策略引发警报。</span><span class="sxs-lookup"><span data-stu-id="2296e-130">Alerts are raised only for policies that are enabled.</span></span> <span data-ttu-id="2296e-131">由于无法启用 **“按需”** 策略，因此，不会为按需执行的策略引发警报。</span><span class="sxs-lookup"><span data-stu-id="2296e-131">Because **On demand** policies cannot be enabled, alerts are not raised for policies that are executed on demand.</span></span>  
  
-   <span data-ttu-id="2296e-132">如果要执行的操作包括发送电子邮件，您必须配置邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="2296e-132">If the action you want to take includes sending an e-mail message, you must configure a mail account.</span></span> <span data-ttu-id="2296e-133">建议您使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="2296e-133">We recommend that you use Database Mail.</span></span> <span data-ttu-id="2296e-134">有关如何设置数据库邮件的详细信息，请参阅 [创建数据库邮件帐户](../database-mail/create-a-database-mail-account.md)。</span><span class="sxs-lookup"><span data-stu-id="2296e-134">For more information about how to set up Database Mail, see [Create a Database Mail Account](../database-mail/create-a-database-mail-account.md).</span></span>  
  
  
