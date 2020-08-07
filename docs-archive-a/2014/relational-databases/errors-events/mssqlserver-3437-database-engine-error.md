---
title: MSSQLSERVER_3437 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed8f2050f6f1b38bc5f3fcb7a9700b80e52f2763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589590"
---
# <a name="mssqlserver_3437"></a><span data-ttu-id="5286a-102">MSSQLSERVER_3437</span><span class="sxs-lookup"><span data-stu-id="5286a-102">MSSQLSERVER_3437</span></span>
    
## <a name="details"></a><span data-ttu-id="5286a-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5286a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5286a-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5286a-104">Product Name</span></span>|<span data-ttu-id="5286a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5286a-105">SQL Server</span></span>|  
|<span data-ttu-id="5286a-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5286a-106">Event ID</span></span>|<span data-ttu-id="5286a-107">3437</span><span class="sxs-lookup"><span data-stu-id="5286a-107">3437</span></span>|  
|<span data-ttu-id="5286a-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5286a-108">Event Source</span></span>|<span data-ttu-id="5286a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5286a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5286a-110">组件</span><span class="sxs-lookup"><span data-stu-id="5286a-110">Component</span></span>|<span data-ttu-id="5286a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5286a-111">SQLEngine</span></span>|  
|<span data-ttu-id="5286a-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5286a-112">Symbolic Name</span></span>|<span data-ttu-id="5286a-113">NODTC</span><span class="sxs-lookup"><span data-stu-id="5286a-113">NODTC</span></span>|  
|<span data-ttu-id="5286a-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5286a-114">Message Text</span></span>|<span data-ttu-id="5286a-115">在恢复数据库 '%.\*ls' 时出错。</span><span class="sxs-lookup"><span data-stu-id="5286a-115">An error occurred while recovering database '%.\*ls'.</span></span> <span data-ttu-id="5286a-116">无法连接到 Microsoft 分布式事务处理协调器 (MS DTC) 以检查事务 %S_XID 的完成状态。</span><span class="sxs-lookup"><span data-stu-id="5286a-116">Unable to connect to Microsoft Distributed Transaction Coordinator (MS DTC) to check the completion status of transaction %S_XID.</span></span> <span data-ttu-id="5286a-117">请修复 MS DTC，然后再次运行恢复操作。</span><span class="sxs-lookup"><span data-stu-id="5286a-117">Fix MS DTC, and run recovery again.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5286a-118">说明</span><span class="sxs-lookup"><span data-stu-id="5286a-118">Explanation</span></span>  
 <span data-ttu-id="5286a-119">在数据库关闭时，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 的一项或多项分布式事务尚未完成。</span><span class="sxs-lookup"><span data-stu-id="5286a-119">One or more distributed transactions that were using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) were incomplete when the database was shut down.</span></span> <span data-ttu-id="5286a-120">由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不能连接到 MS DTC 以完成或回退事务，所以该数据库的恢复失败。</span><span class="sxs-lookup"><span data-stu-id="5286a-120">Recovery of this database failed because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot connect to MS DTC to complete or roll back the transactions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5286a-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="5286a-121">User Action</span></span>  
 <span data-ttu-id="5286a-122">若要恢复该数据库，必须首先解决 MS DTC 存在的问题。</span><span class="sxs-lookup"><span data-stu-id="5286a-122">To recover this database, you must first resolve the problem with MS DTC.</span></span> <span data-ttu-id="5286a-123">若要调查 MS DTC 存在的问题，请检查 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="5286a-123">To investigate the problem with MS DTC, examine the Windows event logs.</span></span> <span data-ttu-id="5286a-124">如果无法解决 MS DTC 问题和恢复数据库，请还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="5286a-124">If you cannot resolve the problem with MS DTC and recover the database, restore a backup of database.</span></span>  
  
  
