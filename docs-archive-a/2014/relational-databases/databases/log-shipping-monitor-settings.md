---
title: 日志传送监视器设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693930"
---
# <a name="log-shipping-monitor-settings"></a><span data-ttu-id="8afb1-102">日志传送监视器设置</span><span class="sxs-lookup"><span data-stu-id="8afb1-102">Log Shipping Monitor Settings</span></span>
  <span data-ttu-id="8afb1-103">使用此页可以配置和修改日志传送监视服务器的属性。</span><span class="sxs-lookup"><span data-stu-id="8afb1-103">Use this page to configure and to modify the properties of the log shipping monitor server.</span></span>  
  
 <span data-ttu-id="8afb1-104">有关日志传送概念的说明，请参阅 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8afb1-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8afb1-105">选项</span><span class="sxs-lookup"><span data-stu-id="8afb1-105">Options</span></span>  
 <span data-ttu-id="8afb1-106">**监视服务器实例**</span><span class="sxs-lookup"><span data-stu-id="8afb1-106">**Monitor server instance**</span></span>  
 <span data-ttu-id="8afb1-107">显示在日志传送配置中当前配置为监视服务器的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8afb1-107">Displays the name of the server instance that is currently configured as the monitor server for the log shipping configuration.</span></span>  
  
 <span data-ttu-id="8afb1-108">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="8afb1-108">**Connect**</span></span>  
 <span data-ttu-id="8afb1-109">选择并连接到用作监视服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8afb1-109">Choose and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be used as the monitor server.</span></span> <span data-ttu-id="8afb1-110">用于连接的帐户必须是辅助服务器实例上 sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="8afb1-110">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="8afb1-111">**模拟作业的代理帐户**</span><span class="sxs-lookup"><span data-stu-id="8afb1-111">**By impersonating the proxy account of the job**</span></span>  
 <span data-ttu-id="8afb1-112">在连接到监视服务器实例时，让日志传送模拟 SQL Server 代理的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="8afb1-112">Have log shipping impersonate the SQL Server Agent proxy account when connecting to the monitor server instance.</span></span> <span data-ttu-id="8afb1-113">备份、复制和还原进程必须能够连接到监视服务器，才可更新日志传送操作的状态。</span><span class="sxs-lookup"><span data-stu-id="8afb1-113">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span>  
  
 <span data-ttu-id="8afb1-114">**使用以下 SQL Server 登录名**</span><span class="sxs-lookup"><span data-stu-id="8afb1-114">**Using the following SQL Server login**</span></span>  
 <span data-ttu-id="8afb1-115">在连接到监视服务器实例时，允许日志传送使用特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="8afb1-115">Allow log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login when connecting to the monitor server instance.</span></span> <span data-ttu-id="8afb1-116">备份、复制和还原进程必须能够连接到监视服务器，才可更新日志传送操作的状态。</span><span class="sxs-lookup"><span data-stu-id="8afb1-116">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span> <span data-ttu-id="8afb1-117">如果希望日志传送使用特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，请选择此选项，然后指定登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="8afb1-117">Choose this option if you want log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and then specify the login and password.</span></span>  
  
 <span data-ttu-id="8afb1-118">**在以下时间后删除历史记录**</span><span class="sxs-lookup"><span data-stu-id="8afb1-118">**Delete history after**</span></span>  
 <span data-ttu-id="8afb1-119">指定在删除日志传送历史记录信息之前，该信息在监视服务器上保留的时间。</span><span class="sxs-lookup"><span data-stu-id="8afb1-119">Specify the amount of time to retain log shipping history information on the monitor server before it is deleted.</span></span>  
  
 <span data-ttu-id="8afb1-120">**作业名称**</span><span class="sxs-lookup"><span data-stu-id="8afb1-120">**Job name**</span></span>  
 <span data-ttu-id="8afb1-121">指示 SQL Server 代理警报作业的名称，日志传送使用该作业在超出备份或还原阈值时发出警报。</span><span class="sxs-lookup"><span data-stu-id="8afb1-121">Indicates the name of the SQL Server Agent alert job used by log shipping to raise alerts when backup or restore thresholds have been exceeded.</span></span> <span data-ttu-id="8afb1-122">首次创建此作业时，可以通过在该框中键入内容来更改名称。</span><span class="sxs-lookup"><span data-stu-id="8afb1-122">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="8afb1-123">**“计划”**</span><span class="sxs-lookup"><span data-stu-id="8afb1-123">**Schedule**</span></span>  
 <span data-ttu-id="8afb1-124">指示 SQL Server 代理警报作业的当前计划。</span><span class="sxs-lookup"><span data-stu-id="8afb1-124">Indicates the current schedule of the SQL Server Agent alert job.</span></span>  
  
 <span data-ttu-id="8afb1-125">**编辑**</span><span class="sxs-lookup"><span data-stu-id="8afb1-125">**Edit**</span></span>  
 <span data-ttu-id="8afb1-126">修改 SQL Server 代理警报作业的参数。</span><span class="sxs-lookup"><span data-stu-id="8afb1-126">Modify the SQL Server Agent alert job parameters.</span></span>  
  
 <span data-ttu-id="8afb1-127">**禁用此作业**</span><span class="sxs-lookup"><span data-stu-id="8afb1-127">**Disable this job**</span></span>  
 <span data-ttu-id="8afb1-128">挂起 SQL Server 代理警报作业。</span><span class="sxs-lookup"><span data-stu-id="8afb1-128">Suspend the SQL Server Agent alert job.</span></span>  
  
  
