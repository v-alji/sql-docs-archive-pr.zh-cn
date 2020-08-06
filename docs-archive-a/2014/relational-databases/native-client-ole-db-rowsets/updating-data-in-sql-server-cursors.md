---
title: 更新 SQL Server 游标中的数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
author: rothja
ms.author: jroth
ms.openlocfilehash: 42e6221a85c30e3adb97df3a11c9cbdc49216b4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579565"
---
# <a name="updating-data-in-sql-server-cursors"></a><span data-ttu-id="da74d-102">更新 SQL Server 游标中的数据</span><span class="sxs-lookup"><span data-stu-id="da74d-102">Updating Data in SQL Server Cursors</span></span>
  <span data-ttu-id="da74d-103">通过游标提取和更新数据时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者应用程序将受到与应用于任何其他客户端应用程序相同的注意事项和约束的约束。</span><span class="sxs-lookup"><span data-stu-id="da74d-103">When fetching and updating data through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer application is bound by the same considerations and constraints that apply to any other client application.</span></span>  
  
 <span data-ttu-id="da74d-104">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 游标中的行才参与并发数据访问控制。</span><span class="sxs-lookup"><span data-stu-id="da74d-104">Only rows in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors participate in concurrent data-access control.</span></span> <span data-ttu-id="da74d-105">当使用者请求可修改的行集时，并发控制是通过 DBPROP_LOCKMODE 控制的。</span><span class="sxs-lookup"><span data-stu-id="da74d-105">When the consumer requests a modifiable rowset, the concurrency control is controlled by DBPROP_LOCKMODE.</span></span> <span data-ttu-id="da74d-106">若要修改并发访问控制的级别，使用者应在打开该行集之前设置 DBPROP_LOCKMODE 属性。</span><span class="sxs-lookup"><span data-stu-id="da74d-106">To modify the level of concurrent access control, the consumer sets the DBPROP_LOCKMODE property before opening the rowset.</span></span>  
  
 <span data-ttu-id="da74d-107">如果客户端应用程序设计使事务长时间保持打开状态，事务隔离级别在定位行时可能造成严重滞后。</span><span class="sxs-lookup"><span data-stu-id="da74d-107">Transaction isolation levels can cause significant lags in row positioning if client application design lets transactions remain open for long periods of time.</span></span> <span data-ttu-id="da74d-108">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用由 DBPROPVAL_TI_READCOMMITTED 指定的已提交读隔离级别。</span><span class="sxs-lookup"><span data-stu-id="da74d-108">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the read-committed isolation level specified by DBPROPVAL_TI_READCOMMITTED.</span></span> <span data-ttu-id="da74d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当行集并发为只读时，Native Client OLE DB 提供程序支持脏读隔离。</span><span class="sxs-lookup"><span data-stu-id="da74d-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports dirty read isolation when the rowset concurrency is read-only.</span></span> <span data-ttu-id="da74d-110">因此，使用者可以在可修改行集中请求更高级别的隔离，但是不能成功请求任何更低级别。</span><span class="sxs-lookup"><span data-stu-id="da74d-110">Therefore, the consumer can request a higher level of isolation in a modifiable rowset but cannot request any lower level successfully.</span></span>  
  
## <a name="immediate-and-delayed-update-modes"></a><span data-ttu-id="da74d-111">立即更新模式和延迟更新模式</span><span class="sxs-lookup"><span data-stu-id="da74d-111">Immediate and Delayed Update Modes</span></span>  
 <span data-ttu-id="da74d-112">在立即更新模式中，对 IRowsetChange::SetData 的每次调用均导致与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之间发生一次往返\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da74d-112">In immediate update mode, each call to **IRowsetChange::SetData** causes a round trip to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="da74d-113">如果使用者对一个行进行了多次更改，通过一个 SetData 调用提交所有更改将更有效\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da74d-113">If the consumer makes multiple changes to a single row, it is more efficient to submit all changes with a single **SetData** call.</span></span>  
  
 <span data-ttu-id="da74d-114">在延迟更新模式中，针对 IRowsetUpdate::Update 的 cRows 和 rghRows 参数中指示的每个行执行一次与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之间的往返\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="da74d-114">In delayed update mode, a roundtrip is made to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for each row indicated in the *cRows* and *rghRows* parameters of **IRowsetUpdate::Update**.</span></span>  
  
 <span data-ttu-id="da74d-115">无论哪种模式，往返表示当未针对行集打开事务对象时的不同事务。</span><span class="sxs-lookup"><span data-stu-id="da74d-115">In either mode, a roundtrip represents a distinct transaction when no transaction object is open for the rowset.</span></span>  
  
 <span data-ttu-id="da74d-116">使用**IRowsetUpdate：： Update**时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将尝试处理每个指示的行。</span><span class="sxs-lookup"><span data-stu-id="da74d-116">When you are using **IRowsetUpdate::Update**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider tries to process each indicated row.</span></span> <span data-ttu-id="da74d-117">出现错误是因为任何行的数据无效、长度或状态值不会停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序处理。</span><span class="sxs-lookup"><span data-stu-id="da74d-117">An error occurring because of invalid data, length, or status values for any row does not stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processing.</span></span> <span data-ttu-id="da74d-118">可能修改参与更新的所有其他行，也可能不修改这些行。</span><span class="sxs-lookup"><span data-stu-id="da74d-118">All or none of the other rows participating in the update may be modified.</span></span> <span data-ttu-id="da74d-119">当*prgRowStatus* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序返回 DB_S_ERRORSOCCURRED 时，使用者必须检查返回的 prgRowStatus 数组，以确定任何特定行的失败。</span><span class="sxs-lookup"><span data-stu-id="da74d-119">The consumer must examine the returned *prgRowStatus* array to determine failure for any specific row when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns DB_S_ERRORSOCCURRED.</span></span>  
  
 <span data-ttu-id="da74d-120">使用者不应假定行以任意特定顺序处理。</span><span class="sxs-lookup"><span data-stu-id="da74d-120">A consumer should not assume that rows are processed in any specific order.</span></span> <span data-ttu-id="da74d-121">如果使用者要求按顺序处理基于多个行的数据修改，使用者应在应用程序逻辑中建立该顺序，并打开一个事务以包含该过程。</span><span class="sxs-lookup"><span data-stu-id="da74d-121">If a consumer requires ordered processing of data modification over more than a single row, the consumer should establish that order in the application logic and open a transaction to enclose the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da74d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da74d-122">See Also</span></span>  
 [<span data-ttu-id="da74d-123">更新行集中的数据</span><span class="sxs-lookup"><span data-stu-id="da74d-123">Updating Data in Rowsets</span></span>](updating-data-in-rowsets.md)  
  
  
