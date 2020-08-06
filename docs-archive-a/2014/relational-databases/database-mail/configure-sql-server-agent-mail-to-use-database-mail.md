---
title: 配置 SQL Server 代理邮件以使用数据库邮件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31d116c0bc8d7e148fc2ef6d2e344400516ad923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682883"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a><span data-ttu-id="2cb7c-102">配置 SQL Server 代理邮件以使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="2cb7c-102">Configure SQL Server Agent Mail to Use Database Mail</span></span>
  <span data-ttu-id="2cb7c-103">本主题说明如何配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理以使用数据库邮件通过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 发送 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的通知和警报。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-103">This topic describes how to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to use Database Mail to send notification and alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="2cb7c-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2cb7c-104">**Before you begin:**</span></span>  
  
-   [<span data-ttu-id="2cb7c-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="2cb7c-105">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="2cb7c-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2cb7c-106">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="2cb7c-107">使用 SQL Server Management Studio 配置 SQL Server 代理以使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="2cb7c-107">To Configure SQL Server Agent to use Database Mail, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="2cb7c-108">跟进任务</span><span class="sxs-lookup"><span data-stu-id="2cb7c-108">Follow-up Tasks</span></span>](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2cb7c-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="2cb7c-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="2cb7c-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="2cb7c-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="2cb7c-111">启用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-111">Enable Database Mail.</span></span>  
  
-   <span data-ttu-id="2cb7c-112">创建供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户使用的数据库邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-112">Create a Database Mail account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use.</span></span>  
  
-   <span data-ttu-id="2cb7c-113">创建供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户使用的数据库邮件配置文件，并将用户添加到 **msdb** 数据库的 **DatabaseMailUserRole** 中。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-113">Create a Database Mail profile for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account to use and add the user to the **DatabaseMailUserRole** in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="2cb7c-114">将该配置文件设置为 **msdb** 数据库的默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-114">Set the profile as the default profile for the **msdb** database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2cb7c-115">Security</span><span class="sxs-lookup"><span data-stu-id="2cb7c-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2cb7c-116">权限</span><span class="sxs-lookup"><span data-stu-id="2cb7c-116">Permissions</span></span>  
 <span data-ttu-id="2cb7c-117">创建配置文件帐户和执行存储过程的用户应是 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-117">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2cb7c-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2cb7c-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2cb7c-119">**配置 SQL Server 代理邮件以使用数据库邮件**</span><span class="sxs-lookup"><span data-stu-id="2cb7c-119">**To configure SQL Server Agent to use Database Mail**</span></span>  
  
-   <span data-ttu-id="2cb7c-120">在对象资源管理器中，展开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-120">In Object Explorer, expand a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="2cb7c-121">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-121">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="2cb7c-122">单击 **“警报系统”**。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-122">Click **Alert System**.</span></span>  
  
-   <span data-ttu-id="2cb7c-123">选择 **“启用邮件配置文件”**。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-123">Select **Enable Mail Profile**.</span></span>  
  
-   <span data-ttu-id="2cb7c-124">在 **“邮件系统”** 列表中，选择 **“数据库邮件”**。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-124">In the **Mail system** list, select **Database Mail**.</span></span>  
  
-   <span data-ttu-id="2cb7c-125">在 **“邮件配置文件列表”** 中，为数据库邮件选择一个邮件配置文件。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-125">In the **Mail profile list**, select a mail profile for Database Mail.</span></span>  
  
-   <span data-ttu-id="2cb7c-126">重新启动 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-126">Restart SQL Server Agent.</span></span>  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> <span data-ttu-id="2cb7c-127">后续任务</span><span class="sxs-lookup"><span data-stu-id="2cb7c-127">Follow-up Tasks</span></span>  
 <span data-ttu-id="2cb7c-128">需要执行下列任务以完成对发送警报和通知的代理配置。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-128">The following tasks are necessary to complete the configuration of Agent to send alerts and notifications.</span></span>  
  
-   [<span data-ttu-id="2cb7c-129">警报</span><span class="sxs-lookup"><span data-stu-id="2cb7c-129">Alerts</span></span>](../../ssms/agent/alerts.md)  
  
     <span data-ttu-id="2cb7c-130">可以配置警报，将特定数据库事件或操作系统情况通知操作员。</span><span class="sxs-lookup"><span data-stu-id="2cb7c-130">Alerts can be configured to notify an operator of a particular database event or operating system condition.</span></span>  
  
-   [<span data-ttu-id="2cb7c-131">运算符</span><span class="sxs-lookup"><span data-stu-id="2cb7c-131">Operators</span></span>](../../ssms/agent/operators.md)  
  
     <span data-ttu-id="2cb7c-132">操作员是可以接收电子通知的人员或组的别名</span><span class="sxs-lookup"><span data-stu-id="2cb7c-132">Operators are aliases for people or groups that can receive electronic notification</span></span>  
  
  
