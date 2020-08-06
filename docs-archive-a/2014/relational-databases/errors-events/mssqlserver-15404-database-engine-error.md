---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beb854c866256728574e06f8c9efb50fb354e15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589646"
---
# <a name="mssqlserver_15404"></a><span data-ttu-id="f80b8-102">MSSQLSERVER_15404</span><span class="sxs-lookup"><span data-stu-id="f80b8-102">MSSQLSERVER_15404</span></span>
    
## <a name="details"></a><span data-ttu-id="f80b8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f80b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f80b8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f80b8-104">Product Name</span></span>|<span data-ttu-id="f80b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f80b8-105">SQL Server</span></span>|  
|<span data-ttu-id="f80b8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f80b8-106">Event ID</span></span>|<span data-ttu-id="f80b8-107">15404</span><span class="sxs-lookup"><span data-stu-id="f80b8-107">15404</span></span>|  
|<span data-ttu-id="f80b8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f80b8-108">Event Source</span></span>|<span data-ttu-id="f80b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f80b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f80b8-110">组件</span><span class="sxs-lookup"><span data-stu-id="f80b8-110">Component</span></span>|<span data-ttu-id="f80b8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f80b8-111">SQLEngine</span></span>|  
|<span data-ttu-id="f80b8-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f80b8-112">Symbolic Name</span></span>|<span data-ttu-id="f80b8-113">SEC_NTGRP_ERROR</span><span class="sxs-lookup"><span data-stu-id="f80b8-113">SEC_NTGRP_ERROR</span></span>|  
|<span data-ttu-id="f80b8-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f80b8-114">Message Text</span></span>|<span data-ttu-id="f80b8-115">无法获取有关 Windows NT 组/用户“*user*”的信息，错误代码 *code*。</span><span class="sxs-lookup"><span data-stu-id="f80b8-115">Could not obtain information about Windows NT group/user '*user*', error code *code*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f80b8-116">说明</span><span class="sxs-lookup"><span data-stu-id="f80b8-116">Explanation</span></span>  
 <span data-ttu-id="f80b8-117">在指定无效主体时，15404 用于身份验证。</span><span class="sxs-lookup"><span data-stu-id="f80b8-117">15404 is used in authentication when an invalid principal is specified.</span></span> <span data-ttu-id="f80b8-118">或者，Windows 帐户的模拟失败，因为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户和 Windows 帐户的域之间没有完全信任关系。</span><span class="sxs-lookup"><span data-stu-id="f80b8-118">Or, impersonation of a Windows account fails because there is no full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f80b8-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="f80b8-119">User Action</span></span>  
 <span data-ttu-id="f80b8-120">检查该 Windows 主体存在且没有拼写错误。</span><span class="sxs-lookup"><span data-stu-id="f80b8-120">Check that the Windows principal exists and is not misspelled.</span></span>  
  
 <span data-ttu-id="f80b8-121">如果此错误是由于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户和 Windows 帐户的域之间缺乏完全信任关系所导致的，则执行以下操作之一可更正该错误：</span><span class="sxs-lookup"><span data-stu-id="f80b8-121">If this error is the result of a lack of a full trust relationship between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the domain of the Windows account, one of the following actions can resolve the error:</span></span>  
  
-   <span data-ttu-id="f80b8-122">使用与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的 Windows 用户处于相同域中的帐户。</span><span class="sxs-lookup"><span data-stu-id="f80b8-122">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="f80b8-123">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在使用 Network Service 或 Local System 之类的计算机帐户，则包含 Windows 用户的域必须信任该计算机。</span><span class="sxs-lookup"><span data-stu-id="f80b8-123">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows User.</span></span>  
  
-   <span data-ttu-id="f80b8-124">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户。</span><span class="sxs-lookup"><span data-stu-id="f80b8-124">Use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
  
