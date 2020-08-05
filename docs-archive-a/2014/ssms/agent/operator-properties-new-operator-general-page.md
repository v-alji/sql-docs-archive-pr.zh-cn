---
title: 操作员属性和新操作员 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ffd4a604275153a2bfe7071c442cc110815f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580523"
---
# <a name="operator-properties-and-new-operator-general-page"></a><span data-ttu-id="a2f1e-102">操作员属性和新建操作员（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="a2f1e-102">Operator Properties and New Operator (General Page)</span></span>
  <span data-ttu-id="a2f1e-103">使用此页可以查看和修改代理操作员的常规属性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a2f1e-104">选项</span><span class="sxs-lookup"><span data-stu-id="a2f1e-104">Options</span></span>  
 <span data-ttu-id="a2f1e-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-105">**Name**</span></span>  
 <span data-ttu-id="a2f1e-106">更改操作员的名称。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-106">Change the name of the operator.</span></span>  
  
 <span data-ttu-id="a2f1e-107">**已启用**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-107">**Enabled**</span></span>  
 <span data-ttu-id="a2f1e-108">启用操作员。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-108">Enable the operator.</span></span> <span data-ttu-id="a2f1e-109">在未启用时，不会向操作员发送通知。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-109">When not enabled, no notifications are sent to the operator.</span></span>  
  
 <span data-ttu-id="a2f1e-110">**电子邮件名称**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-110">**E-mail name**</span></span>  
 <span data-ttu-id="a2f1e-111">指定操作员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-111">Specifies the e-mail address for the operator.</span></span>  
  
 <span data-ttu-id="a2f1e-112">**Net send 地址**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-112">**Net send address**</span></span>  
 <span data-ttu-id="a2f1e-113">指定用于 **net send**的地址。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-113">Specify the address to use for **net send**.</span></span>  
  
 <span data-ttu-id="a2f1e-114">**寻呼电子邮件名称**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-114">**Pager e-mail name**</span></span>  
 <span data-ttu-id="a2f1e-115">指定用于操作员的寻呼程序的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-115">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
 <span data-ttu-id="a2f1e-116">**寻呼值班计划**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-116">**Pager on duty schedule**</span></span>  
 <span data-ttu-id="a2f1e-117">设置寻呼程序处于活动状态的时间。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-117">Sets the times at which the pager is active.</span></span>  
  
 <span data-ttu-id="a2f1e-118">**星期一 - 星期日**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-118">**Monday - Sunday**</span></span>  
 <span data-ttu-id="a2f1e-119">选择寻呼程序在一周中的哪些天处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-119">Select the days that the pager is active.</span></span>  
  
 <span data-ttu-id="a2f1e-120">**工作日开始**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-120">**Workday begin**</span></span>  
 <span data-ttu-id="a2f1e-121">选择一天之中的特定时间， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在该时间之后才可向寻呼程序发送消息。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-121">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
 <span data-ttu-id="a2f1e-122">**工作日结束**</span><span class="sxs-lookup"><span data-stu-id="a2f1e-122">**Workday end**</span></span>  
 <span data-ttu-id="a2f1e-123">选择一天之中的特定时间， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在该时间之后不再向寻呼程序发送消息。</span><span class="sxs-lookup"><span data-stu-id="a2f1e-123">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f1e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2f1e-124">See Also</span></span>  
 [<span data-ttu-id="a2f1e-125">运算符</span><span class="sxs-lookup"><span data-stu-id="a2f1e-125">Operators</span></span>](operators.md)  
  
  
