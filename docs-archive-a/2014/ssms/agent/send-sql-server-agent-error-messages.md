---
title: 发送 SQL Server 代理错误消息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e38b02188eaced65a86b22ed4f22cb6984ce0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588233"
---
# <a name="send-sql-server-agent-error-messages"></a><span data-ttu-id="3d12b-102">Send SQL Server Agent Error Messages</span><span class="sxs-lookup"><span data-stu-id="3d12b-102">Send SQL Server Agent Error Messages</span></span>
  <span data-ttu-id="3d12b-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过使用在中将代理配置为通过网络发送方式发送其错误消息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3d12b-103">This topic describes how to how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send its error messages by way of net send in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3d12b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3d12b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3d12b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3d12b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3d12b-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3d12b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3d12b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3d12b-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="3d12b-108">使用 SQL Server Management Studio 发送 SQL Server 代理错误消息</span><span class="sxs-lookup"><span data-stu-id="3d12b-108">To send SQL Server Agent error messages using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d12b-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="3d12b-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3d12b-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="3d12b-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3d12b-111">“对象资源管理器”仅在您拥有使用权限时才显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理节点。</span><span class="sxs-lookup"><span data-stu-id="3d12b-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="3d12b-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger 服务必须正在运行，才能接收 net send 事件。</span><span class="sxs-lookup"><span data-stu-id="3d12b-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger service must be running to receive net send events.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d12b-113">Security</span><span class="sxs-lookup"><span data-stu-id="3d12b-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d12b-114">权限</span><span class="sxs-lookup"><span data-stu-id="3d12b-114">Permissions</span></span>  
 <span data-ttu-id="3d12b-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，必须将 **代理配置为使用** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定服务器角色的成员帐户的凭据，才能执行其功能。</span><span class="sxs-lookup"><span data-stu-id="3d12b-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3d12b-116">该帐户必须拥有以下 Windows 权限：</span><span class="sxs-lookup"><span data-stu-id="3d12b-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="3d12b-117">以服务身份登录 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="3d12b-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="3d12b-118">替换进程级别标记 (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3d12b-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="3d12b-119">跳过遍历检查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3d12b-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="3d12b-120">调整进程的内存配额 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="3d12b-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="3d12b-121">有关代理服务帐户所需的 Windows 权限的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅为[SQL Server 代理服务选择帐户](select-an-account-for-the-sql-server-agent-service.md)和[配置 Windows 服务帐户和权限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="3d12b-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d12b-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d12b-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-send-sql-server-agent-error-messages"></a><span data-ttu-id="3d12b-123">发送 SQL Server 代理错误消息</span><span class="sxs-lookup"><span data-stu-id="3d12b-123">To send SQL Server Agent error messages</span></span>  
  
1.  <span data-ttu-id="3d12b-124">在 **“对象资源管理器”** 中，单击加号以展开包含要通过 net send 从其发送错误消息的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志的服务器。</span><span class="sxs-lookup"><span data-stu-id="3d12b-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log from which you want to send error messages via net send.</span></span>  
  
2.  <span data-ttu-id="3d12b-125">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d12b-125">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3d12b-126">在 " **SQL Server 代理属性-**_server_name_ " 对话框中的 "**常规**" 页上的 "**错误日志**" 下，在 " **Net send 收件人**" 框中键入要向其发送错误消息的用户名或计算机名。</span><span class="sxs-lookup"><span data-stu-id="3d12b-126">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, , type the user name or computer name to which you want to send error messages in the **Net send recipient** box.</span></span>  
  
4.  <span data-ttu-id="3d12b-127">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3d12b-127">Click **OK**.</span></span>  
  
  
