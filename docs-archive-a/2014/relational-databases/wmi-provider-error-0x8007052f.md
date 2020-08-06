---
title: WMI 错误 0x8007052f | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6e857e0ccaad9b6f34bbdc9b88aea2e6d7291d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694396"
---
# <a name="wmi-error-0x8007052f"></a><span data-ttu-id="3f885-102">WMI 错误 0x8007052f</span><span class="sxs-lookup"><span data-stu-id="3f885-102">WMI Error 0x8007052f</span></span>
    
## <a name="details"></a><span data-ttu-id="3f885-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="3f885-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f885-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3f885-104">Product Name</span></span>|<span data-ttu-id="3f885-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3f885-105">SQL Server</span></span>|  
|<span data-ttu-id="3f885-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3f885-106">Event ID</span></span>|<span data-ttu-id="3f885-107">0x8007052f</span><span class="sxs-lookup"><span data-stu-id="3f885-107">0x8007052f</span></span>|  
|<span data-ttu-id="3f885-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="3f885-108">Event Source</span></span>|<span data-ttu-id="3f885-109">WMI 提供程序错误</span><span class="sxs-lookup"><span data-stu-id="3f885-109">WMI Provider Error</span></span>|  
|<span data-ttu-id="3f885-110">组件</span><span class="sxs-lookup"><span data-stu-id="3f885-110">Component</span></span>|<span data-ttu-id="3f885-111">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="3f885-111">SQL Server Configuration Manager</span></span>|  
|<span data-ttu-id="3f885-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="3f885-112">Symbolic Name</span></span>|<span data-ttu-id="3f885-113">NA</span><span class="sxs-lookup"><span data-stu-id="3f885-113">NA</span></span>|  
|<span data-ttu-id="3f885-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="3f885-114">Message Text</span></span>|<span data-ttu-id="3f885-115">登录失败: 用户帐户限制。</span><span class="sxs-lookup"><span data-stu-id="3f885-115">Logon failure: user account restriction.</span></span> <span data-ttu-id="3f885-116">可能是因为不允许使用空白密码、登录时间限制或者是强制实施策略限制。</span><span class="sxs-lookup"><span data-stu-id="3f885-116">Possible reasons are blank passwords not allowed, login hour restrictions, or a policy restriction has been enforced.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f885-117">说明</span><span class="sxs-lookup"><span data-stu-id="3f885-117">Explanation</span></span>  
 <span data-ttu-id="3f885-118">当 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在 Windows Server 群集或 Windows Server 域控制器上运行时，如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器切换到内置帐户（Network Service、Local Service 或 Local System），则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3f885-118">This error can occur when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager to switch to the built-in accounts (Network Service, Local Service, or Local System) when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="3f885-119">请不要在 Windows Server 群集或 Windows Server 域控制器上以内置帐户运行服务。</span><span class="sxs-lookup"><span data-stu-id="3f885-119">Do not run services under built-in accounts on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="3f885-120">有关服务帐户的建议，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书中的“设置 Windows 服务帐户”主题。</span><span class="sxs-lookup"><span data-stu-id="3f885-120">For recommendations on service accounts, see the topic Setting Up Windows Service Accounts in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f885-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="3f885-121">User Action</span></span>  
 <span data-ttu-id="3f885-122">配置 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以使用域帐户。</span><span class="sxs-lookup"><span data-stu-id="3f885-122">Configure [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use a domain account.</span></span>  
  
  
