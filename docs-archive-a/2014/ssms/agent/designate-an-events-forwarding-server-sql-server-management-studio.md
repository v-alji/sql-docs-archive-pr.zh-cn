---
title: 指定事件转发服务器 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc5f01507bf893d1bffc682f65a01b9ff48ffa9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692097"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a><span data-ttu-id="b6af4-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b6af4-102">Designate an Events Forwarding Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="b6af4-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用在中指定转发事件的服务器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b6af4-103">This topic describes how to designate a server to which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] forwards events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span></span> <span data-ttu-id="b6af4-104">请注意，事件转发适用于在服务器之间转发的事件，而不适用于在单个计算机上承载的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间转发的事件。</span><span class="sxs-lookup"><span data-stu-id="b6af4-104">Note that event forwarding applies to events forwarded between servers, not to events forwarded between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hosted on a single computer.</span></span> <span data-ttu-id="b6af4-105">此外，还请注意，为了接收转发的事件，警报管理服务器必须是 SQL Server 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="b6af4-105">Also note that in order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
 <span data-ttu-id="b6af4-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b6af4-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6af4-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6af4-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6af4-108">安全性</span><span class="sxs-lookup"><span data-stu-id="b6af4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6af4-109">**若要指定事件转发服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b6af4-109">**To designate an events forwarding server, using:**</span></span>  
  
     [<span data-ttu-id="b6af4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6af4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6af4-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b6af4-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6af4-112">Security</span><span class="sxs-lookup"><span data-stu-id="b6af4-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6af4-113">权限</span><span class="sxs-lookup"><span data-stu-id="b6af4-113">Permissions</span></span>  
 <span data-ttu-id="b6af4-114">要求具有 **sysadmin** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b6af4-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6af4-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6af4-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-designate-an-events-forwarding-server"></a><span data-ttu-id="b6af4-116">指定事件转发服务器</span><span class="sxs-lookup"><span data-stu-id="b6af4-116">To designate an events forwarding server</span></span>  
  
1.  <span data-ttu-id="b6af4-117">在 **“对象资源管理器”** 中，单击加号以展开要将其事件转发到其他服务器的服务器。</span><span class="sxs-lookup"><span data-stu-id="b6af4-117">In **Object Explorer,** click the plus sign to expand the server from which you want to forward events to another server.</span></span>  
  
2.  <span data-ttu-id="b6af4-118">右键单击“SQL Server 代理”\*\*\*\*，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6af4-118">Right-click **SQL Server Agent** and select **Properties**.</span></span>  

3.  <span data-ttu-id="b6af4-119">在“SQL Server 代理属性” –_server_name_ 对话框的“选择页”下，选择“高级”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6af4-119">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Select a page**, select **Advanced**.</span></span>  

4.  <span data-ttu-id="b6af4-120">在 **“SQL Server 事件转发”** 下，选中 **“将事件转发到其他服务器”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="b6af4-120">Under **SQL Server event forwarding**, select the **Forward events to a different server** check box.</span></span>  
  
5.  <span data-ttu-id="b6af4-121">在 **“服务器”** 列表中，选择一台服务器，然后在 **“事件”** 选择下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="b6af4-121">In the **Server** list, select a server, and then, under **Events**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="b6af4-122">选择 **“未处理的事件”** 以仅转发本地警报未处理的事件。</span><span class="sxs-lookup"><span data-stu-id="b6af4-122">Select **Unhandled events** to forward only the events that have not been handled by local alerts.</span></span>  
  
    -   <span data-ttu-id="b6af4-123">选择 **“所有事件”** 以转发所有事件，无论本地警报是否已对事件进行处理。</span><span class="sxs-lookup"><span data-stu-id="b6af4-123">Select **All events** to forward all events regardless of whether they have been handled by local alerts.</span></span>  
  
6.  <span data-ttu-id="b6af4-124">在 **“如果事件的严重性不低于”** 列表中，单击将事件转发到所选服务器时的严重级别。</span><span class="sxs-lookup"><span data-stu-id="b6af4-124">In the **If event has severity at or above** list, click the severity level at which events are forwarded to the selected server.</span></span>  
  
7.  <span data-ttu-id="b6af4-125">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b6af4-125">When finished, click **OK**.</span></span>  
  
  
