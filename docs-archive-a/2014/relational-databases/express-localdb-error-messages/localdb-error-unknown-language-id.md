---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: e71f7b443a1999a5edbb17dc11ee4d578834faf4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587825"
---
# <a name="localdb_error_unknown_language_id"></a><span data-ttu-id="098e1-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="098e1-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>
    
## <a name="details"></a><span data-ttu-id="098e1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="098e1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="098e1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="098e1-104">Product Name</span></span>|<span data-ttu-id="098e1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="098e1-105">SQL Server</span></span>|  
|<span data-ttu-id="098e1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="098e1-106">Event ID</span></span>|<span data-ttu-id="098e1-107">270</span><span class="sxs-lookup"><span data-stu-id="098e1-107">270</span></span>|  
|<span data-ttu-id="098e1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="098e1-108">Event Source</span></span>|<span data-ttu-id="098e1-109">SQL Server 本地数据库运行时 12.0</span><span class="sxs-lookup"><span data-stu-id="098e1-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="098e1-110">组件</span><span class="sxs-lookup"><span data-stu-id="098e1-110">Component</span></span>|<span data-ttu-id="098e1-111">本地数据库运行时 API</span><span class="sxs-lookup"><span data-stu-id="098e1-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="098e1-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="098e1-112">Message Text</span></span>|<span data-ttu-id="098e1-113">获取本地化的错误消息时出错。</span><span class="sxs-lookup"><span data-stu-id="098e1-113">Error getting the localized error message.</span></span> <span data-ttu-id="098e1-114">“语言 ID”参数指定的语言未知。</span><span class="sxs-lookup"><span data-stu-id="098e1-114">The language specified by 'Language ID' parameter is unknown.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="098e1-115">说明</span><span class="sxs-lookup"><span data-stu-id="098e1-115">Explanation</span></span>  
 <span data-ttu-id="098e1-116">本地数据库运行时错误消息的请求的语言未知或不受支持。</span><span class="sxs-lookup"><span data-stu-id="098e1-116">The requested language for the Local Database Runtime error message is unknown or not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="098e1-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="098e1-117">User Action</span></span>  
 <span data-ttu-id="098e1-118">尝试请求本地数据库运行时错误消息的支持的语言之一，或尝试请求默认语言。</span><span class="sxs-lookup"><span data-stu-id="098e1-118">Try requesting one of the supported languages for Local Database Runtime error messages, or a default language.</span></span>  
  
  
