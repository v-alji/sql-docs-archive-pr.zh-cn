---
title: 设置作业执行关闭 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e60807676c3c54faf1d44de318ff0a31c2e20b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590014"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a><span data-ttu-id="3d00f-102">Set Job Execution Shutdown (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3d00f-102">Set Job Execution Shutdown (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3d00f-103">本主题介绍如何设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过使用在中完成前等待执行作业的时间 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3d00f-103">This topic describes how to set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="3d00f-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="3d00f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3d00f-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3d00f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3d00f-106">安全性</span><span class="sxs-lookup"><span data-stu-id="3d00f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3d00f-107">**若要设置 SQL Server 代理作业的关闭时间，可使用：**</span><span class="sxs-lookup"><span data-stu-id="3d00f-107">**To set a shutdown time for a SQL Server Agent job, using:**</span></span>  
  
     [<span data-ttu-id="3d00f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d00f-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d00f-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="3d00f-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d00f-110">Security</span><span class="sxs-lookup"><span data-stu-id="3d00f-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d00f-111">权限</span><span class="sxs-lookup"><span data-stu-id="3d00f-111">Permissions</span></span>  
 <span data-ttu-id="3d00f-112">默认情况下，sysadmin\*\*\*\* 固定服务器角色的成员可设置在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理自己结束之前，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理等待作业执行完的时间。</span><span class="sxs-lookup"><span data-stu-id="3d00f-112">By default, members of the **sysadmin** fixed server role can set the time that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span> <span data-ttu-id="3d00f-113">其他用户必须被授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **数据库中下列** 代理固定数据库角色的权限之一：</span><span class="sxs-lookup"><span data-stu-id="3d00f-113">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="3d00f-114">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="3d00f-114">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="3d00f-115">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="3d00f-115">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="3d00f-116">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="3d00f-116">**SQLAgentOperatorRole**</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d00f-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d00f-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-execution-shutdown"></a><span data-ttu-id="3d00f-118">设置作业执行关闭</span><span class="sxs-lookup"><span data-stu-id="3d00f-118">To set job execution shutdown</span></span>  
  
1.  <span data-ttu-id="3d00f-119">在 **“对象资源管理器”** 中，单击加号以展开要设置作业执行关闭间隔的服务器。</span><span class="sxs-lookup"><span data-stu-id="3d00f-119">In **Object Explorer,** , click the plus sign to expand the server where you want to set a job execution shutdown interval.</span></span>  
  
2.  <span data-ttu-id="3d00f-120">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3d00f-120">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3d00f-121">在 **“选择页”** 下，选择 **“作业系统”**。</span><span class="sxs-lookup"><span data-stu-id="3d00f-121">Under **Select a page**, select **Job System**.</span></span>  
  
4.  <span data-ttu-id="3d00f-122">设置“关闭超时间隔(秒)”\*\*\*\* 以延长或缩短关闭超时间隔。</span><span class="sxs-lookup"><span data-stu-id="3d00f-122">Set the **Shutdown time-out interval** in seconds to increase or decrease the shutdown time-out interval.</span></span> <span data-ttu-id="3d00f-123">这决定了在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理本身结束之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理等待作业执行完成的时间长度。</span><span class="sxs-lookup"><span data-stu-id="3d00f-123">This determines how long [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will wait for executing jobs to finish before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent itself finishes.</span></span>  
  
  
