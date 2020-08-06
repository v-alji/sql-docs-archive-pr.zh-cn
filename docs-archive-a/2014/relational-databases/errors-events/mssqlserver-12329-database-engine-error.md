---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7576e32946ce0a453637273c449bbff20e5b6fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586743"
---
# <a name="mssqlserver_12329"></a><span data-ttu-id="1e481-102">MSSQLSERVER_12329</span><span class="sxs-lookup"><span data-stu-id="1e481-102">MSSQLSERVER_12329</span></span>
    
## <a name="details"></a><span data-ttu-id="1e481-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="1e481-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e481-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1e481-104">Product Name</span></span>|<span data-ttu-id="1e481-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e481-105">SQL Server</span></span>|  
|<span data-ttu-id="1e481-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1e481-106">Event ID</span></span>|<span data-ttu-id="1e481-107">12329</span><span class="sxs-lookup"><span data-stu-id="1e481-107">12329</span></span>|  
|<span data-ttu-id="1e481-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1e481-108">Event Source</span></span>|<span data-ttu-id="1e481-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1e481-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1e481-110">组件</span><span class="sxs-lookup"><span data-stu-id="1e481-110">Component</span></span>|<span data-ttu-id="1e481-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1e481-111">SQLEngine</span></span>|  
|<span data-ttu-id="1e481-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="1e481-112">Symbolic Name</span></span>|<span data-ttu-id="1e481-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="1e481-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span></span>|  
|<span data-ttu-id="1e481-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="1e481-114">Message Text</span></span>|<span data-ttu-id="1e481-115">*construct* 不支持排序规则中代码页不是 1252 的数据类型 char(n) 和 varchar(n)。</span><span class="sxs-lookup"><span data-stu-id="1e481-115">The data types char(n) and varchar(n) using a collation that has a code page other than 1252 are not supported with  *construct*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e481-116">说明</span><span class="sxs-lookup"><span data-stu-id="1e481-116">Explanation</span></span>  
 <span data-ttu-id="1e481-117">请勿使用排序规则中代码页不是 1252 的数据类型 char(n) 和 varchar(n)。</span><span class="sxs-lookup"><span data-stu-id="1e481-117">Do not use the data types char(n) and varchar(n) using a collation that has a code page other than 1252.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e481-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="1e481-118">User Action</span></span>  
 <span data-ttu-id="1e481-119">可能生成此错误的一种意外情况是：</span><span class="sxs-lookup"><span data-stu-id="1e481-119">One unexpected situation that can generate this error is:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 <span data-ttu-id="1e481-120">请改用：</span><span class="sxs-lookup"><span data-stu-id="1e481-120">Use this instead:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  