---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5762f160e119012f4fdc0ca1a205ba0ecf690378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591285"
---
# <a name="mssql_eng020572"></a><span data-ttu-id="3fe79-102">MSSQL_ENG020572</span><span class="sxs-lookup"><span data-stu-id="3fe79-102">MSSQL_ENG020572</span></span>
    
## <a name="message-details"></a><span data-ttu-id="3fe79-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="3fe79-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3fe79-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3fe79-104">Product Name</span></span>|<span data-ttu-id="3fe79-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3fe79-105">SQL Server</span></span>|  
|<span data-ttu-id="3fe79-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3fe79-106">Event ID</span></span>|<span data-ttu-id="3fe79-107">20572</span><span class="sxs-lookup"><span data-stu-id="3fe79-107">20572</span></span>|  
|<span data-ttu-id="3fe79-108">事件源</span><span class="sxs-lookup"><span data-stu-id="3fe79-108">Event Source</span></span>|<span data-ttu-id="3fe79-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3fe79-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3fe79-110">组件</span><span class="sxs-lookup"><span data-stu-id="3fe79-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="3fe79-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="3fe79-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3fe79-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="3fe79-112">Message Text</span></span>|<span data-ttu-id="3fe79-113">在验证失败之后，订阅服务器“%s”对发布“%s”中项目“%s”的订阅已被重新初始化。</span><span class="sxs-lookup"><span data-stu-id="3fe79-113">Subscriber '%s' subscription to article '%s' in publication '%s' has been reinitialized after a validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3fe79-114">说明</span><span class="sxs-lookup"><span data-stu-id="3fe79-114">Explanation</span></span>  
 <span data-ttu-id="3fe79-115">根据发布服务器上的数据对订阅服务器上的数据进行验证，数据不匹配；因此验证失败。</span><span class="sxs-lookup"><span data-stu-id="3fe79-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="3fe79-116">在指定应该执行的验证时，选择了如果验证失败则应重新初始化订阅的选项。</span><span class="sxs-lookup"><span data-stu-id="3fe79-116">When you specified that validation should be performed, you selected the option that a subscription should be reinitialized if validation failed.</span></span> <span data-ttu-id="3fe79-117">重新初始化订阅包括在订阅服务器上应用新的快照。</span><span class="sxs-lookup"><span data-stu-id="3fe79-117">Reinitializing a subscription involves applying a new snapshot at the Subscriber.</span></span> <span data-ttu-id="3fe79-118">有关验证的详细信息，请参阅 [Validate Replicated Data](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe79-118">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3fe79-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="3fe79-119">User Action</span></span>  
 <span data-ttu-id="3fe79-120">在订阅服务器上应用了新的快照后，发布服务器和订阅服务器上的数据将会匹配。</span><span class="sxs-lookup"><span data-stu-id="3fe79-120">Data at the Publisher and Subscriber will match after the new snapshot is applied at the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe79-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fe79-121">See Also</span></span>  
 [<span data-ttu-id="3fe79-122">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="3fe79-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
