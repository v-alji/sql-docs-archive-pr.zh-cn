---
title: 目标服务器（“目标服务器状态”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.target.status.f1
ms.assetid: 010a4cab-d878-4889-8ac8-7d91db6345d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: be51648a4642d25c59e52be65e43037844ec0909
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689231"
---
# <a name="target-servers-target-server-status-tab"></a><span data-ttu-id="c3c44-102">目标服务器（“目标服务器状态”选项卡）</span><span class="sxs-lookup"><span data-stu-id="c3c44-102">Target Servers (Target Server Status Tab)</span></span>
  <span data-ttu-id="c3c44-103">使用此页可查看此主服务器的目标服务器的状态。</span><span class="sxs-lookup"><span data-stu-id="c3c44-103">Use this page to view the status of the target servers for this master server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3c44-104">选项</span><span class="sxs-lookup"><span data-stu-id="c3c44-104">Options</span></span>  
 <span data-ttu-id="c3c44-105">**目标服务器**</span><span class="sxs-lookup"><span data-stu-id="c3c44-105">**Target Server**</span></span>  
 <span data-ttu-id="c3c44-106">查看目标服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="c3c44-106">View the name of the target server.</span></span>  
  
 <span data-ttu-id="c3c44-107">**本地时间**</span><span class="sxs-lookup"><span data-stu-id="c3c44-107">**Local time**</span></span>  
 <span data-ttu-id="c3c44-108">按照目标服务器所在的时区来查看其日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c3c44-108">View the date and time of the target server in the local time zone for that server.</span></span>  
  
 <span data-ttu-id="c3c44-109">**上次轮询时间**</span><span class="sxs-lookup"><span data-stu-id="c3c44-109">**Last polled**</span></span>  
 <span data-ttu-id="c3c44-110">查看目标服务器上一次轮询主服务器的本地日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c3c44-110">View the local date and time that the target server last polled the master.</span></span>  
  
 <span data-ttu-id="c3c44-111">**未读指令**</span><span class="sxs-lookup"><span data-stu-id="c3c44-111">**Unread instructions**</span></span>  
 <span data-ttu-id="c3c44-112">查看目标服务器尚未收到的指令数。</span><span class="sxs-lookup"><span data-stu-id="c3c44-112">View the number of instructions that the target server has not yet received.</span></span>  
  
 <span data-ttu-id="c3c44-113">**Status**</span><span class="sxs-lookup"><span data-stu-id="c3c44-113">**Status**</span></span>  
 <span data-ttu-id="c3c44-114">查看目标服务器的状态。</span><span class="sxs-lookup"><span data-stu-id="c3c44-114">View the status of the target server.</span></span>  
  
 <span data-ttu-id="c3c44-115">**强制轮询**</span><span class="sxs-lookup"><span data-stu-id="c3c44-115">**Force Poll**</span></span>  
 <span data-ttu-id="c3c44-116">单击此按钮可强制所选的目标服务器轮询主服务器。</span><span class="sxs-lookup"><span data-stu-id="c3c44-116">Click this button to force the selected target servers to poll the master server.</span></span>  
  
 <span data-ttu-id="c3c44-117">**强制脱离**</span><span class="sxs-lookup"><span data-stu-id="c3c44-117">**Force Defection**</span></span>  
 <span data-ttu-id="c3c44-118">单击此按钮可强制所选的目标服务器脱离主服务器。</span><span class="sxs-lookup"><span data-stu-id="c3c44-118">Click this button to force the selected target servers to defect from the master server.</span></span>  
  
 <span data-ttu-id="c3c44-119">**发布指令**</span><span class="sxs-lookup"><span data-stu-id="c3c44-119">**Post Instructions**</span></span>  
 <span data-ttu-id="c3c44-120">将指令发布到所选的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="c3c44-120">Post instructions to the selected target servers.</span></span>  
  
 <span data-ttu-id="c3c44-121">**启用自动刷新**</span><span class="sxs-lookup"><span data-stu-id="c3c44-121">**Enable Auto Refresh**</span></span>  
 <span data-ttu-id="c3c44-122">选择此选项可自动刷新显示的信息。</span><span class="sxs-lookup"><span data-stu-id="c3c44-122">Select this option to automatically refresh the information shown.</span></span>  
  
 <span data-ttu-id="c3c44-123">**刷新间隔**</span><span class="sxs-lookup"><span data-stu-id="c3c44-123">**Refresh every**</span></span>  
 <span data-ttu-id="c3c44-124">指定刷新此页上信息的频率。</span><span class="sxs-lookup"><span data-stu-id="c3c44-124">Specify how often the information on this page is refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c44-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3c44-125">See Also</span></span>  
 [<span data-ttu-id="c3c44-126">企业范围的自动化管理</span><span class="sxs-lookup"><span data-stu-id="c3c44-126">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
