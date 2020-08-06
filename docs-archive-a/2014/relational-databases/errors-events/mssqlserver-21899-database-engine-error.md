---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb1af04b56685d0e1b5a703b812d08d88909b693
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689394"
---
# <a name="mssqlserver_21899"></a><span data-ttu-id="735fc-102">MSSQLSERVER_21899</span><span class="sxs-lookup"><span data-stu-id="735fc-102">MSSQLSERVER_21899</span></span>
    
## <a name="details"></a><span data-ttu-id="735fc-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="735fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="735fc-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="735fc-104">Product Name</span></span>|<span data-ttu-id="735fc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="735fc-105">SQL Server</span></span>|  
|<span data-ttu-id="735fc-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="735fc-106">Event ID</span></span>|<span data-ttu-id="735fc-107">21899</span><span class="sxs-lookup"><span data-stu-id="735fc-107">21899</span></span>|  
|<span data-ttu-id="735fc-108">事件源</span><span class="sxs-lookup"><span data-stu-id="735fc-108">Event Source</span></span>|<span data-ttu-id="735fc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="735fc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="735fc-110">组件</span><span class="sxs-lookup"><span data-stu-id="735fc-110">Component</span></span>|<span data-ttu-id="735fc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="735fc-111">SQLEngine</span></span>|  
|<span data-ttu-id="735fc-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="735fc-112">Symbolic Name</span></span>|<span data-ttu-id="735fc-113">SQLErrorNum21899</span><span class="sxs-lookup"><span data-stu-id="735fc-113">SQLErrorNum21899</span></span>|  
|<span data-ttu-id="735fc-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="735fc-114">Message Text</span></span>|<span data-ttu-id="735fc-115">重定向发布服务器“%s”中的查询失败，该查询用于确定原始发布服务器“%s”的订阅服务器是否存在 sysserver 条目，失败时错误为“%d”，错误消息为“%s”。</span><span class="sxs-lookup"><span data-stu-id="735fc-115">The query at the redirected publisher '%s' to determine whether there were sysserver entries for the subscribers of the original publisher '%s' failed with error '%d', error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="735fc-116">说明</span><span class="sxs-lookup"><span data-stu-id="735fc-116">Explanation</span></span>  
 <span data-ttu-id="735fc-117">在远程服务器上，`sp_validate_redirected_publisher` 查询发布服务器数据库的订阅元数据表以确定其关联的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="735fc-117">`sp_validate_redirected_publisher` queries the subscription metadata tables of the publisher database at the remote server to determine its associated subscribers.</span></span> <span data-ttu-id="735fc-118">当该查询失败时，会返回错误 21899。</span><span class="sxs-lookup"><span data-stu-id="735fc-118">Error 21899 is returned if this query fails.</span></span> <span data-ttu-id="735fc-119">验证查询要求对重定向发布服务器上的发布数据库具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="735fc-119">The validation query requires access to the published database at the redirected publisher.</span></span> <span data-ttu-id="735fc-120">如果在对原始发布服务器调用 `sp_adddistpublisher` 时指定的登录名无权访问发布的数据库，则会返回错误 21899。</span><span class="sxs-lookup"><span data-stu-id="735fc-120">If the login specified when `sp_adddistpublisher` is called for the original publisher is not authorized to access the published database at the redirected publisher, error 21899 is returned.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="735fc-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="735fc-121">User Action</span></span>  
 <span data-ttu-id="735fc-122">请检查引用的错误消息，以确定失败的原因和采取相应的更正措施</span><span class="sxs-lookup"><span data-stu-id="735fc-122">Review the cited error message to determine the cause of the failure and take appropriate corrective action</span></span>  
  
  
