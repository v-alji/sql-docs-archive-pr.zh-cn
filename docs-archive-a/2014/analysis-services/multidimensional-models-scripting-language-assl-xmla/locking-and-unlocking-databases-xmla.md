---
title: " (XMLA) 锁定和解锁数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691351"
---
# <a name="locking-and-unlocking-databases-xmla"></a><span data-ttu-id="a9792-102">锁定数据库和解除数据库锁定 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="a9792-102">Locking and Unlocking Databases (XMLA)</span></span>
  <span data-ttu-id="a9792-103">您可以分别使用 (XMLA) XML for Analysis 中的 "[锁定](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)" 和 "[解锁](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)" 命令锁定和解锁数据库。</span><span class="sxs-lookup"><span data-stu-id="a9792-103">You can lock and unlock databases using, respectively, the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) and [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commands in XML for Analysis (XMLA).</span></span> <span data-ttu-id="a9792-104">通常，其他 XMLA 命令会在执行期间根据需要自动锁定对象和解除对象锁定，从而完成命令。</span><span class="sxs-lookup"><span data-stu-id="a9792-104">Typically, other XMLA commands automatically lock and unlock objects as needed to complete the command during execution.</span></span> <span data-ttu-id="a9792-105">可以显式锁定或解锁数据库，以便在单个事务中执行多个命令，例如[批处理](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)命令，同时防止其他应用程序将写入事务提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="a9792-105">You can explicitly lock or unlock a database to perform multiple commands within a single transaction, such as a [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command, while preventing other applications from committing a write transaction to the database.</span></span>  
  
## <a name="locking-databases"></a><span data-ttu-id="a9792-106">锁定数据库</span><span class="sxs-lookup"><span data-stu-id="a9792-106">Locking Databases</span></span>  
 <span data-ttu-id="a9792-107">`Lock` 命令锁定当前活动事务上下文中的对象，该锁可为共享锁或排他锁。</span><span class="sxs-lookup"><span data-stu-id="a9792-107">The `Lock` command locks an object, either for shared or exclusive use, within the context of the currently active transaction.</span></span> <span data-ttu-id="a9792-108">对象上的锁将阻止提交事务，直到删除该锁为止。</span><span class="sxs-lookup"><span data-stu-id="a9792-108">A lock on an object prevents transactions from committing until the lock is removed.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a9792-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支持两种类型的锁：共享锁和排他锁。</span><span class="sxs-lookup"><span data-stu-id="a9792-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports two types of locks, shared locks and exclusive locks.</span></span> <span data-ttu-id="a9792-110">有关支持的锁类型的详细信息 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，请参阅[Mode 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="a9792-110">For more information about the lock types supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Mode Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a9792-111">仅允许锁定数据库。</span><span class="sxs-lookup"><span data-stu-id="a9792-111">allows only databases to be locked.</span></span> <span data-ttu-id="a9792-112">[Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)元素必须包含对数据库的对象引用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a9792-112">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) element must contain an object reference to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="a9792-113">如果未指定 `Object` 元素或 `Object` 元素引用数据库以外的对象，则将引发错误。</span><span class="sxs-lookup"><span data-stu-id="a9792-113">If the `Object` element is not specified or if the `Object` element refers to an object other than a database, an error occurs.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a9792-114">只有数据库管理员或服务器管理员可以显式发出 `Lock` 命令。</span><span class="sxs-lookup"><span data-stu-id="a9792-114">Only database administrators or server administrators can explicitly issue a `Lock` command.</span></span>  
  
 <span data-ttu-id="a9792-115">其他命令将对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库隐式发出 `Lock` 命令。</span><span class="sxs-lookup"><span data-stu-id="a9792-115">Other commands implicitly issue a `Lock` command on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="a9792-116">任何从数据库读取数据或元数据的操作（例如任何[发现](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)方法或运行[语句](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)命令的[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法）都隐式发出数据库上的共享锁。</span><span class="sxs-lookup"><span data-stu-id="a9792-116">Any operation that reads data or metadata from a database, such as any [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method or an [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method running a [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command, implicitly issues a shared lock on the database.</span></span> <span data-ttu-id="a9792-117">将数据或元数据的更改提交到数据库中的对象（ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 例如 `Execute` 运行[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)命令的方法）的任何事务都隐式发出数据库上的排他锁。</span><span class="sxs-lookup"><span data-stu-id="a9792-117">Any transaction that commits changes in data or metadata to an object on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as an `Execute` method running an [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command, implicitly issues an exclusive lock on the database.</span></span>  
  
## <a name="unlocking-objects"></a><span data-ttu-id="a9792-118">解锁对象</span><span class="sxs-lookup"><span data-stu-id="a9792-118">Unlocking Objects</span></span>  
 <span data-ttu-id="a9792-119">`Unlock` 命令可删除在当前活动事务的上下文中建立的锁。</span><span class="sxs-lookup"><span data-stu-id="a9792-119">The `Unlock` command removes a lock established within the context of the currently active transaction.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a9792-120">只有数据库管理员或服务器管理员可以显式发出 `Unlock` 命令。</span><span class="sxs-lookup"><span data-stu-id="a9792-120">Only database administrators or server administrators can explicitly issue an `Unlock` command.</span></span>  
  
 <span data-ttu-id="a9792-121">所有锁都位于当前事务的上下文中。</span><span class="sxs-lookup"><span data-stu-id="a9792-121">All locks are held in the context of the current transaction.</span></span> <span data-ttu-id="a9792-122">当提交或回滚当前事务时，事务中定义的所有锁都将自动释放。</span><span class="sxs-lookup"><span data-stu-id="a9792-122">When the current transaction is committed or rolled back, all locks defined within the transaction are automatically released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9792-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9792-123">See Also</span></span>  
 <span data-ttu-id="a9792-124">[&#40;XMLA&#41;锁定元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="a9792-124">[Lock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 <span data-ttu-id="a9792-125">[&#40;XMLA&#41;解锁元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="a9792-125">[Unlock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 [<span data-ttu-id="a9792-126">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="a9792-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
