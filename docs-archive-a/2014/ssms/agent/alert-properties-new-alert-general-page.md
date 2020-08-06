---
title: 警报属性-新建警报 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471b0062ecc805e83020495e422f8914baec5f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692112"
---
# <a name="alert-properties-new-alert-general-page"></a><span data-ttu-id="d7ee1-102">警报属性-新建警报 (常规页) </span><span class="sxs-lookup"><span data-stu-id="d7ee1-102">Alert Properties-New Alert (General Page)</span></span>
  <span data-ttu-id="d7ee1-103">使用此页可以查看和修改代理警报的常规属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d7ee1-104">选项</span><span class="sxs-lookup"><span data-stu-id="d7ee1-104">Options</span></span>  
 <span data-ttu-id="d7ee1-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-105">**Name**</span></span>  
 <span data-ttu-id="d7ee1-106">更改警报的名称。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-106">Change the name of the alert.</span></span>  
  
 <span data-ttu-id="d7ee1-107">**启用**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-107">**Enable**</span></span>  
 <span data-ttu-id="d7ee1-108">启用警报。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-108">Enable the alert.</span></span> <span data-ttu-id="d7ee1-109">如果未启用警报，则警报中指定的操作将不会发生。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-109">When the alert is not enabled, the actions specified in the alert do not occur.</span></span>  
  
 <span data-ttu-id="d7ee1-110">**Type**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-110">**Type**</span></span>  
 <span data-ttu-id="d7ee1-111">选择警报的类型：</span><span class="sxs-lookup"><span data-stu-id="d7ee1-111">Select the type of alert:</span></span>  
  
-   <span data-ttu-id="d7ee1-112">**SQL Server 事件警报** ，该警报用于响应 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 事件日志中的消息。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-112">**SQL Server event alert** responds to messages in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span>  
  
-   <span data-ttu-id="d7ee1-113">**SQL Server 性能条件警报** ，该警报用于响应性能计数器中的特定条件。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-113">**SQL Server performance condition alert** responds to a specific condition in a performance counter.</span></span>  
  
-   <span data-ttu-id="d7ee1-114">**WMI 事件警报** ，该警报用于响应 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-114">**WMI event alert** responds to a Windows Management Instrumentation (WMI) event.</span></span>  
  
## <a name="sql-server-event-alert-options"></a><span data-ttu-id="d7ee1-115">SQL Server 事件警报选项</span><span class="sxs-lookup"><span data-stu-id="d7ee1-115">SQL Server Event Alert Options</span></span>  
 <span data-ttu-id="d7ee1-116">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-116">**Database name**</span></span>  
 <span data-ttu-id="d7ee1-117">为该事件指定一个数据库，或者指定“所有数据库”\*\*\*\*，这样不管在哪一个数据库中发生该事件，都会对消息作出响应。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-117">Specify a database for the event, or **all databases** to respond to a message regardless of the database where the event occurs.</span></span>  
  
 <span data-ttu-id="d7ee1-118">**错误号**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-118">**Error number**</span></span>  
 <span data-ttu-id="d7ee1-119">指定此事件将用于响应错误，并指定错误号。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-119">Specify that this event responds to an error, and specify the error number.</span></span>  
  
 <span data-ttu-id="d7ee1-120">**严重性**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-120">**Severity**</span></span>  
 <span data-ttu-id="d7ee1-121">指定此事件将用于响应特定严重级别的所有消息，并指定严重级别。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-121">Specify that this event responds to any message with a specific severity level, and specify the severity level.</span></span>  
  
 <span data-ttu-id="d7ee1-122">**当消息包含以下内容时触发警报**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-122">**Raise alert when message contains**</span></span>  
 <span data-ttu-id="d7ee1-123">按特定字符串筛选事件。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-123">Filter events by a specific string.</span></span> <span data-ttu-id="d7ee1-124">选中此选项时，该警报只对包含特定字符串的事件作出响应。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-124">When this option is selected, the alert only responds to events that contain a specific string.</span></span>  
  
 <span data-ttu-id="d7ee1-125">**消息正文**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-125">**Message text**</span></span>  
 <span data-ttu-id="d7ee1-126">指定要用于筛选事件的字符串。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-126">Specify the string to use to filter events.</span></span>  
  
## <a name="sql-server-performance-condition-alerts"></a><span data-ttu-id="d7ee1-127">SQL Server 性能条件警报</span><span class="sxs-lookup"><span data-stu-id="d7ee1-127">SQL Server Performance Condition Alerts</span></span>  
 <span data-ttu-id="d7ee1-128">**Object**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-128">**Object**</span></span>  
 <span data-ttu-id="d7ee1-129">指定要监视的性能对象。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-129">Specify the performance object to monitor.</span></span>  
  
 <span data-ttu-id="d7ee1-130">**计数器**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-130">**Counter**</span></span>  
 <span data-ttu-id="d7ee1-131">指定位于要监视的性能对象内的计数器。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-131">Specify the counter within the performance object to monitor.</span></span>  
  
 <span data-ttu-id="d7ee1-132">**实例**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-132">**Instance**</span></span>  
 <span data-ttu-id="d7ee1-133">指定要监视的计数器实例。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-133">Specify the instance of the counter to monitor.</span></span>  
  
 <span data-ttu-id="d7ee1-134">**计数器满足以下条件时触发警报**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-134">**Alert if counter**</span></span>  
 <span data-ttu-id="d7ee1-135">指定警报响应的计数器的行为。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-135">Specify the behavior of the counter that the alert responds to.</span></span> <span data-ttu-id="d7ee1-136">例如，可能希望警报响应 **Free space in tempdb (KB)** 计数器的值低于特定值的条件，或者希望警报响应 **SQL Compilations/sec** 高于特定值的条件。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-136">For example, you may want the alert to respond to a condition where the value of the **Free space in tempdb (KB)** counter falls below a certain value, or you may want the alert to respond to a condition where the **SQL Compilations/sec** rises above a certain value.</span></span>  
  
 <span data-ttu-id="d7ee1-137">**值**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-137">**Value**</span></span>  
 <span data-ttu-id="d7ee1-138">指定计数器的值。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-138">Specify a value for the counter.</span></span>  
  
## <a name="wmi-event-alert-options"></a><span data-ttu-id="d7ee1-139">WMI 事件警报选项</span><span class="sxs-lookup"><span data-stu-id="d7ee1-139">WMI Event Alert Options</span></span>  
 <span data-ttu-id="d7ee1-140">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-140">**Namespace**</span></span>  
 <span data-ttu-id="d7ee1-141">指定用于 WMI 查询语言 (WQL) 语句的命名空间。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-141">Specify the namespace to use for the WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="d7ee1-142">仅支持运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的计算机上的命名空间。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-142">Only namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
 <span data-ttu-id="d7ee1-143">**查询**</span><span class="sxs-lookup"><span data-stu-id="d7ee1-143">**Query**</span></span>  
 <span data-ttu-id="d7ee1-144">指定用于标识该警报所响应事件的 WQL 语句。</span><span class="sxs-lookup"><span data-stu-id="d7ee1-144">Specify the WQL statement that identifies the event that the alert responds to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ee1-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7ee1-145">See Also</span></span>  
 <span data-ttu-id="d7ee1-146">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="d7ee1-146">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="d7ee1-147">[将 WQL 与 WMI Provider for Server Events 结合使用](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span><span class="sxs-lookup"><span data-stu-id="d7ee1-147">[Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span></span>  
 <span data-ttu-id="d7ee1-148">[使用错误号创建警报](create-an-alert-using-an-error-number.md) </span><span class="sxs-lookup"><span data-stu-id="d7ee1-148">[Create an Alert Using an Error Number](create-an-alert-using-an-error-number.md) </span></span>  
 [<span data-ttu-id="d7ee1-149">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="d7ee1-149">Create an Alert Using Severity Level</span></span>](create-an-alert-using-severity-level.md)  
  
  
