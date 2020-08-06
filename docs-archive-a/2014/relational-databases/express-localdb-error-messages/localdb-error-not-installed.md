---
title: LOCALDB_ERROR_NOT_INSTALLED |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: e7912885-1c14-409b-9022-83ad4c36f3bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c64dcfc42522b8252edb94237bd4acc7c246083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590824"
---
# <a name="localdb_error_not_installed"></a><span data-ttu-id="dc99c-102">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="dc99c-102">LOCALDB_ERROR_NOT_INSTALLED</span></span>
    
## <a name="details"></a><span data-ttu-id="dc99c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="dc99c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc99c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="dc99c-104">Product Name</span></span>|<span data-ttu-id="dc99c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dc99c-105">SQL Server</span></span>|  
|<span data-ttu-id="dc99c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dc99c-106">Event ID</span></span>|<span data-ttu-id="dc99c-107">278</span><span class="sxs-lookup"><span data-stu-id="dc99c-107">278</span></span>|  
|<span data-ttu-id="dc99c-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="dc99c-108">Event Source</span></span>|<span data-ttu-id="dc99c-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="dc99c-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="dc99c-110">组件</span><span class="sxs-lookup"><span data-stu-id="dc99c-110">Component</span></span>|<span data-ttu-id="dc99c-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="dc99c-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="dc99c-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="dc99c-112">Message Text</span></span>|<span data-ttu-id="dc99c-113">**注意：** 消息文本为空，因为此消息意味着整个 LocalDB API (包括将 HRESULT 映射到消息文本) 不可用的 FormatMessage 函数。</span><span class="sxs-lookup"><span data-stu-id="dc99c-113">**Note:**  The message text is empty, because this message means that the entire LocalDB API (including the FormatMessage function that maps HRESULTS into message text) is not available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dc99c-114">说明</span><span class="sxs-lookup"><span data-stu-id="dc99c-114">Explanation</span></span>  
 <span data-ttu-id="dc99c-115">计算机上没有安装本地数据库运行时。</span><span class="sxs-lookup"><span data-stu-id="dc99c-115">The Local Database Runtime is not installed on the computer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dc99c-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="dc99c-116">User Action</span></span>  
 <span data-ttu-id="dc99c-117">安装本地数据库运行时，然后重试操作。</span><span class="sxs-lookup"><span data-stu-id="dc99c-117">Install the Local Database Runtime and try the operation again.</span></span>  
  
  
