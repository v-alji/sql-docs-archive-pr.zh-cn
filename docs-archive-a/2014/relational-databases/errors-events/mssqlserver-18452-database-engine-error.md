---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5786d5de4748f6bbf59d2bd4acecd7ca77977f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587845"
---
# <a name="mssqlserver_18452"></a><span data-ttu-id="61094-102">MSSQLSERVER_18452</span><span class="sxs-lookup"><span data-stu-id="61094-102">MSSQLSERVER_18452</span></span>
    
## <a name="details"></a><span data-ttu-id="61094-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="61094-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61094-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="61094-104">Product Name</span></span>|<span data-ttu-id="61094-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="61094-105">SQL Server</span></span>|  
|<span data-ttu-id="61094-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="61094-106">Event ID</span></span>|<span data-ttu-id="61094-107">18452</span><span class="sxs-lookup"><span data-stu-id="61094-107">18452</span></span>|  
|<span data-ttu-id="61094-108">事件源</span><span class="sxs-lookup"><span data-stu-id="61094-108">Event Source</span></span>|<span data-ttu-id="61094-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="61094-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="61094-110">组件</span><span class="sxs-lookup"><span data-stu-id="61094-110">Component</span></span>|<span data-ttu-id="61094-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="61094-111">SQLEngine</span></span>|  
|<span data-ttu-id="61094-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="61094-112">Symbolic Name</span></span>|<span data-ttu-id="61094-113">LOGON_INVALID_CONNECT</span><span class="sxs-lookup"><span data-stu-id="61094-113">LOGON_INVALID_CONNECT</span></span>|  
|<span data-ttu-id="61094-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="61094-114">Message Text</span></span>|<span data-ttu-id="61094-115">用户 "%.\*ls" 登录失败。</span><span class="sxs-lookup"><span data-stu-id="61094-115">Login failed for user '%.\*ls'.</span></span> <span data-ttu-id="61094-116">该登录名为 SQL Server 登录名，不能与 Windows 身份验证一起使用。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="61094-116">The login is a SQL Server login and cannot be used with Windows Authentication.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61094-117">说明</span><span class="sxs-lookup"><span data-stu-id="61094-117">Explanation</span></span>  
 <span data-ttu-id="61094-118">用户尝试使用无法验证的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="61094-118">The user attempted to login with credentials that cannot be validated.</span></span> <span data-ttu-id="61094-119">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="61094-119">Possible causes are:</span></span>  
  
-   <span data-ttu-id="61094-120">此登录可能为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录，但服务器仅接受 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="61094-120">The login may be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login but the server only accepts Windows Authentication.</span></span>  
  
-   <span data-ttu-id="61094-121">您尝试使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上不存在所用登录名。</span><span class="sxs-lookup"><span data-stu-id="61094-121">You are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but the login used does not exist on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="61094-122">登录可能使用 Windows 身份验证，但登录名是无法识别的 Windows 主体。</span><span class="sxs-lookup"><span data-stu-id="61094-122">The login may use Windows Authentication but the login is an unrecognized Windows principal.</span></span> <span data-ttu-id="61094-123">无法识别的 Windows 主体表示 Windows 无法验证此登录名。</span><span class="sxs-lookup"><span data-stu-id="61094-123">An unrecognized Windows principal means that the login cannot be verified by Windows.</span></span> <span data-ttu-id="61094-124">这可能是由于此 Windows 登录名来自不可信的域。</span><span class="sxs-lookup"><span data-stu-id="61094-124">This could be because the Windows login is from an untrusted domain.</span></span>  
  
 <span data-ttu-id="61094-125">类似问题可能导致出现更一般性的错误 18456。</span><span class="sxs-lookup"><span data-stu-id="61094-125">Similar problems can cause the less-specific error 18456.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61094-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="61094-126">User Action</span></span>  
 <span data-ttu-id="61094-127">如果您尝试使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接，请验证是否将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用混合身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="61094-127">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="61094-128">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接，请验证此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名是否存在。</span><span class="sxs-lookup"><span data-stu-id="61094-128">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists.</span></span>  
  
 <span data-ttu-id="61094-129">如果尝试使用 Windows 身份验证进行连接，请验证您是否正确地登录到相应的域。</span><span class="sxs-lookup"><span data-stu-id="61094-129">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
  
