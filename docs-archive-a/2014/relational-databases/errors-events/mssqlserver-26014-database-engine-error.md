---
title: MSSQLSERVER_26014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8114183b212767d01013eee9387d8b2efa2e0d7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586736"
---
# <a name="mssqlserver_26014"></a><span data-ttu-id="26dbb-102">MSSQLSERVER_26014</span><span class="sxs-lookup"><span data-stu-id="26dbb-102">MSSQLSERVER_26014</span></span>
    
## <a name="details"></a><span data-ttu-id="26dbb-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="26dbb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26dbb-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="26dbb-104">Product Name</span></span>|<span data-ttu-id="26dbb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="26dbb-105">SQL Server</span></span>|  
|<span data-ttu-id="26dbb-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="26dbb-106">Event ID</span></span>|<span data-ttu-id="26dbb-107">26014</span><span class="sxs-lookup"><span data-stu-id="26dbb-107">26014</span></span>|  
|<span data-ttu-id="26dbb-108">事件源</span><span class="sxs-lookup"><span data-stu-id="26dbb-108">Event Source</span></span>|<span data-ttu-id="26dbb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="26dbb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="26dbb-110">组件</span><span class="sxs-lookup"><span data-stu-id="26dbb-110">Component</span></span>|<span data-ttu-id="26dbb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="26dbb-111">SQLEngine</span></span>|  
|<span data-ttu-id="26dbb-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="26dbb-112">Symbolic Name</span></span>|<span data-ttu-id="26dbb-113">SNI_SSL_USER_CERT_FAILURE</span><span class="sxs-lookup"><span data-stu-id="26dbb-113">SNI_SSL_USER_CERT_FAILURE</span></span>|  
|<span data-ttu-id="26dbb-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="26dbb-114">Message Text</span></span>|<span data-ttu-id="26dbb-115">无法加载用户指定的证书 [Cert Hash(sha1) "%hs"]。</span><span class="sxs-lookup"><span data-stu-id="26dbb-115">Unable to load user-specified certificate [Cert Hash(sha1) "%hs"].</span></span> <span data-ttu-id="26dbb-116">服务器将不接受连接。</span><span class="sxs-lookup"><span data-stu-id="26dbb-116">The server will not accept a connection.</span></span> <span data-ttu-id="26dbb-117">您应该验证是否正确安装了证书。</span><span class="sxs-lookup"><span data-stu-id="26dbb-117">You should verify that the certificate is correctly installed.</span></span> <span data-ttu-id="26dbb-118">请参阅联机丛书中的“配置证书以供 SSL 使用”。</span><span class="sxs-lookup"><span data-stu-id="26dbb-118">See "Configuring Certificate for Use by SSL" in Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26dbb-119">说明</span><span class="sxs-lookup"><span data-stu-id="26dbb-119">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="26dbb-120">尝试加载在该消息中指定的证书，但是该操作失败。</span><span class="sxs-lookup"><span data-stu-id="26dbb-120">attempted to load the certificate named in the message but the operation failed.</span></span> <span data-ttu-id="26dbb-121">必须先解决此问题，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 才能使用该证书。</span><span class="sxs-lookup"><span data-stu-id="26dbb-121">This problem must be resolved before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use this certificate.</span></span>  
  
 <span data-ttu-id="26dbb-122">此错误可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="26dbb-122">Possible causes of the error include:</span></span>  
  
-   <span data-ttu-id="26dbb-123">该证书可能已被移动或删除。</span><span class="sxs-lookup"><span data-stu-id="26dbb-123">The certificate could have been moved or deleted.</span></span>  
  
-   <span data-ttu-id="26dbb-124">如果由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的登录名已发生更改，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能无权访问该证书。</span><span class="sxs-lookup"><span data-stu-id="26dbb-124">If the login used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has changed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not have permission to access the certificate.</span></span>  
  
-   <span data-ttu-id="26dbb-125">该证书可能已过期。</span><span class="sxs-lookup"><span data-stu-id="26dbb-125">The certificate may have expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26dbb-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="26dbb-126">User Action</span></span>  
 <span data-ttu-id="26dbb-127">请确保该消息中的命名证书在系统中存在，而且可供访问和使用。</span><span class="sxs-lookup"><span data-stu-id="26dbb-127">Make sure the certificate named in the message exists on the system, is accessible, and it is valid for use.</span></span>  
  
  
