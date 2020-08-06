---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7195311fefe3f0f1b7b4d6d789aa8d8487bc3bfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694081"
---
# <a name="issabort-ole-db"></a><span data-ttu-id="4548d-102">ISSAbort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="4548d-102">ISSAbort (OLE DB)</span></span>
  <span data-ttu-id="4548d-103">在**ISSAbort** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序中公开的 ISSAbort 接口提供[ISSAbort：： Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)方法，该方法用于取消当前行集以及使用最初生成了行集的命令进行批处理，并且尚未完成执行的任何命令。</span><span class="sxs-lookup"><span data-stu-id="4548d-103">The **ISSAbort** interface, which is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, provides the [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) method that is used to cancel the current rowset plus any commands batched with the command that initially generated the rowset, and that have not yet completed execution.</span></span>  
  
 <span data-ttu-id="4548d-104">**ISSAbort**是一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 种特定于 Native Client 提供程序的接口，可通过对**ICommand：： Execute**或**IOpenRowset：： OpenRowset**返回的**IMultipleResults**对象使用**QueryInterface** 。</span><span class="sxs-lookup"><span data-stu-id="4548d-104">**ISSAbort** is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider-specific interface available by using **QueryInterface** on the **IMultipleResults** object returned by **ICommand::Execute** or **IOpenRowset::OpenRowset**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4548d-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="4548d-105">In This Section</span></span>  
  
|<span data-ttu-id="4548d-106">方法</span><span class="sxs-lookup"><span data-stu-id="4548d-106">Method</span></span>|<span data-ttu-id="4548d-107">说明</span><span class="sxs-lookup"><span data-stu-id="4548d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4548d-108">ISSAbort：： Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4548d-108">ISSAbort::Abort &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|<span data-ttu-id="4548d-109">取消当前行集以及与当前命令关联的任何批处理命令。</span><span class="sxs-lookup"><span data-stu-id="4548d-109">Cancels the current rowset plus any batched commands associated with the current command.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4548d-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4548d-110">See Also</span></span>  
 [<span data-ttu-id="4548d-111">接口 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="4548d-111">Interfaces &#40;OLE DB&#41;</span></span>](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
