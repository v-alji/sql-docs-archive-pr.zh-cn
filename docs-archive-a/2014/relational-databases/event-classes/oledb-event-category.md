---
title: OLEDB 事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB event category
- SQL Server event classes, OLEDB event category
- event classes [SQL Server], OLEDB event category
ms.assetid: cf93e424-3dac-462d-b3da-92e7d0b064d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd55294966448f8976dc20198381918e163cc0d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579594"
---
# <a name="oledb-event-category"></a><span data-ttu-id="f8818-102">OLEDB 事件类别</span><span class="sxs-lookup"><span data-stu-id="f8818-102">OLEDB Event Category</span></span>
  <span data-ttu-id="f8818-103">**OLEDB** 事件类别包含常规 OLEDB 事件。</span><span class="sxs-lookup"><span data-stu-id="f8818-103">The **OLEDB** event category contains general OLEDB events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8818-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="f8818-104">In This Section</span></span>  
  
|<span data-ttu-id="f8818-105">主题</span><span class="sxs-lookup"><span data-stu-id="f8818-105">Topic</span></span>|<span data-ttu-id="f8818-106">说明</span><span class="sxs-lookup"><span data-stu-id="f8818-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f8818-107">OLEDB Call 事件类</span><span class="sxs-lookup"><span data-stu-id="f8818-107">OLEDB Call Event Class</span></span>](oledb-call-event-class.md)|<span data-ttu-id="f8818-108">指示 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已对分布式查询和远程存储过程的 OLE DB 访问程序发出了非数据或非 QueryInterface  调用。</span><span class="sxs-lookup"><span data-stu-id="f8818-108">Indicates that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has made a non-data or non-**QueryInterface** call to an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="f8818-109">OLEDB DataRead 事件类</span><span class="sxs-lookup"><span data-stu-id="f8818-109">OLEDB DataRead Event Class</span></span>](oledb-dataread-event-class.md)|<span data-ttu-id="f8818-110">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已调用分布式查询和远程存储过程的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="f8818-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has called an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="f8818-111">OLEDB Errors 事件类</span><span class="sxs-lookup"><span data-stu-id="f8818-111">OLEDB Errors Event Class</span></span>](oledb-errors-event-class.md)|<span data-ttu-id="f8818-112">指示 OLE DB 访问接口的调用返回了一个错误。</span><span class="sxs-lookup"><span data-stu-id="f8818-112">Indicates that a call to an OLE DB provider returned an error.</span></span>|  
|[<span data-ttu-id="f8818-113">OLEDB Provider Information 事件类</span><span class="sxs-lookup"><span data-stu-id="f8818-113">OLEDB Provider Information Event Class</span></span>](oledb-provider-information-event-class.md)|<span data-ttu-id="f8818-114">指示分布式查询已运行并收集到与提供程序连接对应的信息。</span><span class="sxs-lookup"><span data-stu-id="f8818-114">Indicates that a distributed query has run and has collected information that corresponds to the provider connection.</span></span>|  
|[<span data-ttu-id="f8818-115">OLEDB QueryInterface 事件类</span><span class="sxs-lookup"><span data-stu-id="f8818-115">OLEDB QueryInterface Event Class</span></span>](oledb-queryinterface-event-class.md)|<span data-ttu-id="f8818-116">指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已向分布式查询和远程存储过程发出 OLE DB **QueryInterface** 调用。</span><span class="sxs-lookup"><span data-stu-id="f8818-116">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued an OLE DB **QueryInterface** call for distributed queries and remote stored procedures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8818-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8818-117">See Also</span></span>  
 [<span data-ttu-id="f8818-118">扩展事件</span><span class="sxs-lookup"><span data-stu-id="f8818-118">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
