---
title: 强制目标服务器轮询主服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: stevestein
ms.author: sstein
ms.openlocfilehash: b37bf19bfe8e8fb55c29c8d94c28a341d06df5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577210"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a><span data-ttu-id="94870-102">Force a Target Server to Poll the Master Server</span><span class="sxs-lookup"><span data-stu-id="94870-102">Force a Target Server to Poll the Master Server</span></span>
  <span data-ttu-id="94870-103">本主题说明如何强制目标服务器轮询主服务器。</span><span class="sxs-lookup"><span data-stu-id="94870-103">This topic describes how to force a target server to poll the master server.</span></span> <span data-ttu-id="94870-104">目标服务器必须是主服务器上的已注册服务器。</span><span class="sxs-lookup"><span data-stu-id="94870-104">The target server must be a registered server on the master server.</span></span>  
  
 <span data-ttu-id="94870-105">作业是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理执行的一系列指定操作。</span><span class="sxs-lookup"><span data-stu-id="94870-105">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="94870-106">多服务器作业是主服务器在一台或多台目标服务器上运行的作业。</span><span class="sxs-lookup"><span data-stu-id="94870-106">A multiserver job is a job that a master server runs on one or more target servers.</span></span> <span data-ttu-id="94870-107">每个目标服务器一次只能运行一个相同作业的实例。</span><span class="sxs-lookup"><span data-stu-id="94870-107">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="94870-108">每台目标服务器会定期轮询主服务器，下载分配给目标服务器的任何新作业的一个副本，然后断开连接。</span><span class="sxs-lookup"><span data-stu-id="94870-108">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="94870-109">目标服务器在本地运行作业，然后重新连接到主服务器以上载作业结果状态。</span><span class="sxs-lookup"><span data-stu-id="94870-109">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94870-110">如果在目标服务器试图上载作业状态时无法访问主服务器，则作业将处于假脱机状态，直到可以访问主服务器。</span><span class="sxs-lookup"><span data-stu-id="94870-110">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
-   <span data-ttu-id="94870-111">**开始之前：** [限制和局限](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="94870-111">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="94870-112">**若要强制目标服务器轮询主服务器，使用：**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="94870-112">**To force a target server to poll the master server, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="94870-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="94870-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="94870-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="94870-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="94870-115">目标服务器必须是主服务器上的已注册服务器。</span><span class="sxs-lookup"><span data-stu-id="94870-115">The target server must be a registered server on the master server.</span></span> <span data-ttu-id="94870-116">您必须从主服务器中运行本主题中给出的说明。</span><span class="sxs-lookup"><span data-stu-id="94870-116">You must run the instructions given in this topic from the master server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="94870-117">Security</span><span class="sxs-lookup"><span data-stu-id="94870-117">Security</span></span>  
 <span data-ttu-id="94870-118">有关详细信息，请参阅 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 和 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)。</span><span class="sxs-lookup"><span data-stu-id="94870-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="94870-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="94870-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="94870-120">**强制目标服务器轮询主服务器**</span><span class="sxs-lookup"><span data-stu-id="94870-120">**To force a target server to poll the master server**</span></span>  
  
1.  <span data-ttu-id="94870-121">在 **对象资源管理器**中，展开主服务器。</span><span class="sxs-lookup"><span data-stu-id="94870-121">In **Object Explorer**, expand the master server.</span></span>  
  
2.  <span data-ttu-id="94870-122">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，再单击“管理目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94870-122">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="94870-123">单击目标服务器，再单击 **“强制轮询”**。</span><span class="sxs-lookup"><span data-stu-id="94870-123">Click a target server, and then click **Force Poll**.</span></span>  
  
  
