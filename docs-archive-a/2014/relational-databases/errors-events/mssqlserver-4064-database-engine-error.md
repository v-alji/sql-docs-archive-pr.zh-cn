---
title: MSSQLSERVER_4064 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 201098aadeb6bd091f0312532138f692ae8079b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590211"
---
# <a name="mssqlserver_4064"></a><span data-ttu-id="206e2-102">MSSQLSERVER_4064</span><span class="sxs-lookup"><span data-stu-id="206e2-102">MSSQLSERVER_4064</span></span>
    
## <a name="details"></a><span data-ttu-id="206e2-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="206e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="206e2-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="206e2-104">Product Name</span></span>|<span data-ttu-id="206e2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="206e2-105">SQL Server</span></span>|  
|<span data-ttu-id="206e2-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="206e2-106">Event ID</span></span>|<span data-ttu-id="206e2-107">4064</span><span class="sxs-lookup"><span data-stu-id="206e2-107">4064</span></span>|  
|<span data-ttu-id="206e2-108">事件源</span><span class="sxs-lookup"><span data-stu-id="206e2-108">Event Source</span></span>|<span data-ttu-id="206e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="206e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="206e2-110">组件</span><span class="sxs-lookup"><span data-stu-id="206e2-110">Component</span></span>|<span data-ttu-id="206e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="206e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="206e2-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="206e2-112">Symbolic Name</span></span>|<span data-ttu-id="206e2-113">DB_UFAIL_FATAL</span><span class="sxs-lookup"><span data-stu-id="206e2-113">DB_UFAIL_FATAL</span></span>|  
|<span data-ttu-id="206e2-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="206e2-114">Message Text</span></span>|<span data-ttu-id="206e2-115">无法打开用户默认数据库。</span><span class="sxs-lookup"><span data-stu-id="206e2-115">Cannot open user default database.</span></span> <span data-ttu-id="206e2-116">登录失败。</span><span class="sxs-lookup"><span data-stu-id="206e2-116">Login failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="206e2-117">说明</span><span class="sxs-lookup"><span data-stu-id="206e2-117">Explanation</span></span>  
 <span data-ttu-id="206e2-118">由于 SQL Server 登录名的默认数据库存在问题，该登录名无法进行连接。</span><span class="sxs-lookup"><span data-stu-id="206e2-118">The SQL Server login was unable to connect because of a problem with its default database.</span></span> <span data-ttu-id="206e2-119">数据库本身无效或登录名缺少数据库的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="206e2-119">Either the database itself is invalid or the login lacks CONNECT permission on the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="206e2-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="206e2-120">User Action</span></span>  
 <span data-ttu-id="206e2-121">使用 ALTER LOGIN 更改登录名的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="206e2-121">Use ALTER LOGIN to change the login's default database.</span></span> <span data-ttu-id="206e2-122">将 CONNECT 权限授予登录名。</span><span class="sxs-lookup"><span data-stu-id="206e2-122">Grant CONNECT permission to the login.</span></span>  
  
  
