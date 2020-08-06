---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 934683cfca1a9a9c0596071824c21a0045e6ebab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590828"
---
# <a name="localdb_error_insufficient_buffer"></a><span data-ttu-id="5e750-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5e750-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>
    
## <a name="details"></a><span data-ttu-id="5e750-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5e750-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e750-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5e750-104">Product Name</span></span>|<span data-ttu-id="5e750-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5e750-105">SQL Server</span></span>|  
|<span data-ttu-id="5e750-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5e750-106">Event ID</span></span>|<span data-ttu-id="5e750-107">276</span><span class="sxs-lookup"><span data-stu-id="5e750-107">276</span></span>|  
|<span data-ttu-id="5e750-108">事件来源</span><span class="sxs-lookup"><span data-stu-id="5e750-108">Event Source</span></span>|<span data-ttu-id="5e750-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="5e750-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="5e750-110">组件</span><span class="sxs-lookup"><span data-stu-id="5e750-110">Component</span></span>|<span data-ttu-id="5e750-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="5e750-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="5e750-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="5e750-112">Message Text</span></span>|<span data-ttu-id="5e750-113">传递给本地数据库实例 API 方法的缓冲区太小。</span><span class="sxs-lookup"><span data-stu-id="5e750-113">The buffer passed to the Local Database instance API method has insufficient size.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5e750-114">说明</span><span class="sxs-lookup"><span data-stu-id="5e750-114">Explanation</span></span>  
 <span data-ttu-id="5e750-115">输入的缓冲区太小，并且没有要求截断。</span><span class="sxs-lookup"><span data-stu-id="5e750-115">The input buffer is too short, and truncation was not requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e750-116">用户操作</span><span class="sxs-lookup"><span data-stu-id="5e750-116">User Action</span></span>  
 <span data-ttu-id="5e750-117">提供指定大小的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5e750-117">Provide a buffer of the specified size.</span></span>  
  
  
