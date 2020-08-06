---
title: 警报属性： "新建警报 (选项" 页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692111"
---
# <a name="alert-properties-new-alert-options-page"></a><span data-ttu-id="d8c10-102">警报属性：新建警报（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="d8c10-102">Alert Properties: New Alert (Options Page)</span></span>
  <span data-ttu-id="d8c10-103">使用此页可以查看和修改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理警报的选项。</span><span class="sxs-lookup"><span data-stu-id="d8c10-103">Use this page to view and modify options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8c10-104">选项</span><span class="sxs-lookup"><span data-stu-id="d8c10-104">Options</span></span>  
 <span data-ttu-id="d8c10-105">**电子邮件**</span><span class="sxs-lookup"><span data-stu-id="d8c10-105">**E-mail**</span></span>  
 <span data-ttu-id="d8c10-106">在电子邮件通知中包括事件错误文本（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="d8c10-106">Include error text from the event, if any, in e-mail notifications.</span></span>  
  
 <span data-ttu-id="d8c10-107">**寻呼程序**</span><span class="sxs-lookup"><span data-stu-id="d8c10-107">**Pager**</span></span>  
 <span data-ttu-id="d8c10-108">在寻呼程序通知中包括事件错误文本（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="d8c10-108">Include error text from the event, if any, in pager notifications.</span></span>  
  
 <span data-ttu-id="d8c10-109">**Net send**</span><span class="sxs-lookup"><span data-stu-id="d8c10-109">**Net send**</span></span>  
 <span data-ttu-id="d8c10-110">在 net send 通知中包括事件错误文本（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="d8c10-110">Include error text from the event, if any, in net send notifications.</span></span>  
  
 <span data-ttu-id="d8c10-111">**要发送的其他通知消息**</span><span class="sxs-lookup"><span data-stu-id="d8c10-111">**Additional notification message to send**</span></span>  
 <span data-ttu-id="d8c10-112">键入要包括在通知消息中的任何其他文本。</span><span class="sxs-lookup"><span data-stu-id="d8c10-112">Type any additional text to include in notification messages.</span></span>  
  
 <span data-ttu-id="d8c10-113">**两次响应之间的延迟时间**</span><span class="sxs-lookup"><span data-stu-id="d8c10-113">**Delay between responses**</span></span>  
 <span data-ttu-id="d8c10-114">为重复发生的事件指定延迟时间。</span><span class="sxs-lookup"><span data-stu-id="d8c10-114">Specify a delay for repeated occurrences of the event.</span></span> <span data-ttu-id="d8c10-115">某些事件可能会在短期内频繁发生。</span><span class="sxs-lookup"><span data-stu-id="d8c10-115">Some events may occur frequently during a short period of time.</span></span> <span data-ttu-id="d8c10-116">在这种情况下，您可能需要知道事件已经发生，但不希望针对每一事件做出响应。</span><span class="sxs-lookup"><span data-stu-id="d8c10-116">In this case, you may want to know that the event has occurred, but you may not want a response for every event.</span></span> <span data-ttu-id="d8c10-117">使用此选项可以指定超时。有一段延迟，在警报响应事件之后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将等待指定的延迟后再次响应，而不管该事件是否在延迟期间发生。</span><span class="sxs-lookup"><span data-stu-id="d8c10-117">Use this option to specify a time-out. With a delay, after the alert responds to an event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for the delay specified before responding again, regardless of whether the event occurs during the delay.</span></span>  
  
 <span data-ttu-id="d8c10-118">**）**</span><span class="sxs-lookup"><span data-stu-id="d8c10-118">**Minutes**</span></span>  
 <span data-ttu-id="d8c10-119">指定延迟时间（分钟）。</span><span class="sxs-lookup"><span data-stu-id="d8c10-119">Specify a delay in minutes.</span></span> <span data-ttu-id="d8c10-120">若要在每次发生事件时均予以响应，请指定 0 分和 0 秒。</span><span class="sxs-lookup"><span data-stu-id="d8c10-120">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
 <span data-ttu-id="d8c10-121">**计算**</span><span class="sxs-lookup"><span data-stu-id="d8c10-121">**Seconds**</span></span>  
 <span data-ttu-id="d8c10-122">指定延迟时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="d8c10-122">Specify a delay in seconds.</span></span> <span data-ttu-id="d8c10-123">若要在每次发生事件时均予以响应，请指定 0 分和 0 秒。</span><span class="sxs-lookup"><span data-stu-id="d8c10-123">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c10-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8c10-124">See Also</span></span>  
 [<span data-ttu-id="d8c10-125">警报</span><span class="sxs-lookup"><span data-stu-id="d8c10-125">Alerts</span></span>](alerts.md)  
  
  
