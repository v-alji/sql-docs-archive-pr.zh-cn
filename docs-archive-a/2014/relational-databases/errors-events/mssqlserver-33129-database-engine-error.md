---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da7735889dce8bfc33e624115e8245f8a02f46b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581250"
---
# <a name="mssqlserver_33129"></a><span data-ttu-id="979e4-102">MSSQLSERVER_33129</span><span class="sxs-lookup"><span data-stu-id="979e4-102">MSSQLSERVER_33129</span></span>
    
## <a name="details"></a><span data-ttu-id="979e4-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="979e4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="979e4-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="979e4-104">Product Name</span></span>|<span data-ttu-id="979e4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="979e4-105">SQL Server</span></span>|  
|<span data-ttu-id="979e4-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="979e4-106">Event ID</span></span>|<span data-ttu-id="979e4-107">33129</span><span class="sxs-lookup"><span data-stu-id="979e4-107">33129</span></span>|  
|<span data-ttu-id="979e4-108">事件源</span><span class="sxs-lookup"><span data-stu-id="979e4-108">Event Source</span></span>|<span data-ttu-id="979e4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="979e4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="979e4-110">组件</span><span class="sxs-lookup"><span data-stu-id="979e4-110">Component</span></span>|<span data-ttu-id="979e4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="979e4-111">SQLEngine</span></span>|  
|<span data-ttu-id="979e4-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="979e4-112">Symbolic Name</span></span>|<span data-ttu-id="979e4-113">SEC_CANNOT_DISABLE_WIN_GROUP</span><span class="sxs-lookup"><span data-stu-id="979e4-113">SEC_CANNOT_DISABLE_WIN_GROUP</span></span>|  
|<span data-ttu-id="979e4-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="979e4-114">Message Text</span></span>|<span data-ttu-id="979e4-115">不能使用带 DISABLE 参数的 ALTER_LOGIN 来拒绝对 Windows 组的访问。</span><span class="sxs-lookup"><span data-stu-id="979e4-115">Cannot use ALTER_LOGIN with the DISABLE argument to deny access to a Windows group.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="979e4-116">说明</span><span class="sxs-lookup"><span data-stu-id="979e4-116">Explanation</span></span>  
 <span data-ttu-id="979e4-117">尝试禁用某一 Windows 组的登录名时，会出现此消息。</span><span class="sxs-lookup"><span data-stu-id="979e4-117">This message occurs when attempting to disable the login of a Windows Group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="979e4-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="979e4-118">User Action</span></span>  
 <span data-ttu-id="979e4-119">Windows 组的登录名不能禁用。</span><span class="sxs-lookup"><span data-stu-id="979e4-119">The login of a Windows Group cannot be disabled.</span></span> <span data-ttu-id="979e4-120">若要暂时删除对某一 Windows 组授予的访问权限，则使用 REVOKE 命令吊销对 Windows 组的该登录名的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="979e4-120">To temporarily remove access permission granted to a Windows Group, REVOKE the CONNECT permission of the login for the Windows Group.</span></span> <span data-ttu-id="979e4-121">Windows 用户仍可能通过其单独的登录名或通过另一个 Windows 组具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="979e4-121">Windows users might still have access through their individual login or through another Windows Group.</span></span> <span data-ttu-id="979e4-122">下面的示例吊销 WESTCOAST 域的 Accounting 组的连接权限。</span><span class="sxs-lookup"><span data-stu-id="979e4-122">The following example revokes the connect permission to the Accounting Group of the WESTCOAST domain.</span></span>  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
