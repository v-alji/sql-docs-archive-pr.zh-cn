---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f6bb461b42b66368224fffd2c14f9b4da61abf5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581255"
---
# <a name="mssqlserver_33027"></a><span data-ttu-id="9c25d-102">MSSQLSERVER_33027</span><span class="sxs-lookup"><span data-stu-id="9c25d-102">MSSQLSERVER_33027</span></span>
    
## <a name="details"></a><span data-ttu-id="9c25d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9c25d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c25d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9c25d-104">Product Name</span></span>|<span data-ttu-id="9c25d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c25d-105">SQL Server</span></span>|  
|<span data-ttu-id="9c25d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9c25d-106">Event ID</span></span>|<span data-ttu-id="9c25d-107">33027</span><span class="sxs-lookup"><span data-stu-id="9c25d-107">33027</span></span>|  
|<span data-ttu-id="9c25d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9c25d-108">Event Source</span></span>|<span data-ttu-id="9c25d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9c25d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9c25d-110">组件</span><span class="sxs-lookup"><span data-stu-id="9c25d-110">Component</span></span>|<span data-ttu-id="9c25d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9c25d-111">SQLEngine</span></span>|  
|<span data-ttu-id="9c25d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9c25d-112">Symbolic Name</span></span>|<span data-ttu-id="9c25d-113">SEC_CRYPTOPROV_CANTLOADDLL</span><span class="sxs-lookup"><span data-stu-id="9c25d-113">SEC_CRYPTOPROV_CANTLOADDLL</span></span>|  
|<span data-ttu-id="9c25d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="9c25d-114">Message Text</span></span>|<span data-ttu-id="9c25d-115">由于 Authenticode 签名或文件路径无效，未能加载加密提供程序“%.\*ls”。</span><span class="sxs-lookup"><span data-stu-id="9c25d-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span> <span data-ttu-id="9c25d-116">请检查以前的消息，了解其他失败信息。</span><span class="sxs-lookup"><span data-stu-id="9c25d-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c25d-117">说明</span><span class="sxs-lookup"><span data-stu-id="9c25d-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9c25d-118">无法使用错误消息中列出的加密提供程序，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法加载 DLL。</span><span class="sxs-lookup"><span data-stu-id="9c25d-118">was unable to use the cryptographic provider listed in the error message, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not load the DLL.</span></span> <span data-ttu-id="9c25d-119">原因是名称无效或 Authenticode 签名无效。</span><span class="sxs-lookup"><span data-stu-id="9c25d-119">Either the name is invalid or the Authenticode signature is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c25d-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="9c25d-120">User Action</span></span>  
 <span data-ttu-id="9c25d-121">请检查该文件是否存在以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是否拥有访问该位置的权限。</span><span class="sxs-lookup"><span data-stu-id="9c25d-121">Check that the file is present and that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has permission to access that location.</span></span> <span data-ttu-id="9c25d-122">请查看错误日志以获得其他相关消息。</span><span class="sxs-lookup"><span data-stu-id="9c25d-122">Check the error log for additional related messages.</span></span> <span data-ttu-id="9c25d-123">否则，请联系加密服务供应商以获得详细信息。</span><span class="sxs-lookup"><span data-stu-id="9c25d-123">Otherwise, contact the cryptographic provider for more information.</span></span>  
  
  
