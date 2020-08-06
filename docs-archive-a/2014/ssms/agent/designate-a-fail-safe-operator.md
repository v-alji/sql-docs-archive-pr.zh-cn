---
title: 指定防故障操作员 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 714ed78875bd289f2fe2d64a5699c59bce58ced0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692099"
---
# <a name="designate-a-fail-safe-operator"></a><span data-ttu-id="f9248-102">指定防故障操作员</span><span class="sxs-lookup"><span data-stu-id="f9248-102">Designate a Fail-Safe Operator</span></span>
  <span data-ttu-id="f9248-103">防故障操作员是在无法联系到指定的操作员时接收警报的用户。</span><span class="sxs-lookup"><span data-stu-id="f9248-103">A fail-safe operator is a user who receives the alert if the designated operator cannot be reached.</span></span> <span data-ttu-id="f9248-104">本主题说明如何通过使用在中设置防故障操作员以接收 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f9248-104">This topic describes how to set a fail-safe operator to receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f9248-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f9248-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f9248-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f9248-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f9248-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f9248-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f9248-108">安全性</span><span class="sxs-lookup"><span data-stu-id="f9248-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f9248-109">**若要指定防故障操作员，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f9248-109">**To designate a fail-safe operator, using:**</span></span>  
  
     [<span data-ttu-id="f9248-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f9248-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f9248-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="f9248-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f9248-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f9248-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f9248-113">在 **的未来版本中，将从** 代理中删除寻呼程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="f9248-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f9248-114">请避免在新的开发工作中使用这些功能，并考虑修改当前使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f9248-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="f9248-115">请注意，若要向操作员发送电子邮件和寻呼通知，必须将 SQL Server 代理配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="f9248-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="f9248-116">有关详细信息，请参阅 [向操作员分配警报](assign-alerts-to-an-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="f9248-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f9248-117">为管理作业提供了一种图形化的简便方法，建议使用此方法来创建和管理作业基础结构。</span><span class="sxs-lookup"><span data-stu-id="f9248-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f9248-118">Security</span><span class="sxs-lookup"><span data-stu-id="f9248-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f9248-119">权限</span><span class="sxs-lookup"><span data-stu-id="f9248-119">Permissions</span></span>  
 <span data-ttu-id="f9248-120">只有 **sysadmin** 固定服务器角色的成员才能指定防故障操作员。</span><span class="sxs-lookup"><span data-stu-id="f9248-120">Only members of the **sysadmin** fixed server role can designate fail-safe operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f9248-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f9248-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-a-fail-safe-operator"></a><span data-ttu-id="f9248-122">指定防故障操作员</span><span class="sxs-lookup"><span data-stu-id="f9248-122">To designate a fail-safe operator</span></span>  
  
1.  <span data-ttu-id="f9248-123">在“对象资源管理器”\*\*\*\* 中，单击加号以展开服务器，该服务器包含要指定为防故障操作员的 SQL Server 代理操作员。</span><span class="sxs-lookup"><span data-stu-id="f9248-123">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent operator that you want to designate as a fail-safe.</span></span>  
  
2.  <span data-ttu-id="f9248-124">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9248-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="f9248-125">在 " **SQL Server 代理属性-**_server_name_ " 对话框中的 "**选择页**" 下，选择 "**警报系统**"。</span><span class="sxs-lookup"><span data-stu-id="f9248-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Alert System**.</span></span>  
 
4.  <span data-ttu-id="f9248-126">在“防故障操作员”\*\*\*\* 下，选中“启用防故障操作员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9248-126">Under **Fail-safe operator**, select **Enable fail-safe operator**.</span></span>  
  
5.  <span data-ttu-id="f9248-127">在“操作员”\*\*\*\* 列表中，选择想要执行防故障的操作员。</span><span class="sxs-lookup"><span data-stu-id="f9248-127">In the **Operator** list, select the operator that you want to make a fail-safe.</span></span>  
  
6.  <span data-ttu-id="f9248-128">选中以下任何或所有复选框以指定通知操作员的方法：“电子邮件”\*\*\*\*、“寻呼程序”\*\*\*\* 或“Net send”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9248-128">Select either any or all of the following check boxes to specify how the operator will be notified: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="f9248-129">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="f9248-129">When finished, click **OK**.</span></span>  
  
  
