---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11dd1c72c8cae868b7ebcb02e72ef0db81aeafe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689391"
---
# <a name="mssqlserver_2508"></a><span data-ttu-id="4bab1-102">MSSQLSERVER_2508</span><span class="sxs-lookup"><span data-stu-id="4bab1-102">MSSQLSERVER_2508</span></span>
    
## <a name="details"></a><span data-ttu-id="4bab1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="4bab1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bab1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="4bab1-104">Product Name</span></span>|<span data-ttu-id="4bab1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4bab1-105">SQL Server</span></span>|  
|<span data-ttu-id="4bab1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="4bab1-106">Event ID</span></span>|<span data-ttu-id="4bab1-107">2508</span><span class="sxs-lookup"><span data-stu-id="4bab1-107">2508</span></span>|  
|<span data-ttu-id="4bab1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="4bab1-108">Event Source</span></span>|<span data-ttu-id="4bab1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4bab1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4bab1-110">组件</span><span class="sxs-lookup"><span data-stu-id="4bab1-110">Component</span></span>|<span data-ttu-id="4bab1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4bab1-111">SQLEngine</span></span>|  
|<span data-ttu-id="4bab1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="4bab1-112">Symbolic Name</span></span>|<span data-ttu-id="4bab1-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span><span class="sxs-lookup"><span data-stu-id="4bab1-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span></span>|  
|<span data-ttu-id="4bab1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="4bab1-114">Message Text</span></span>|<span data-ttu-id="4bab1-115">具有以下属性的对象的 %.\*ls 计数不正确: 对象 "%.\*ls"、索引 ID %d、分区 ID %I64d、分配单元 ID %I64d (类型 %.\*ls)。</span><span class="sxs-lookup"><span data-stu-id="4bab1-115">The %.\*ls count for object "%.\*ls", index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls) is incorrect.</span></span> <span data-ttu-id="4bab1-116">请运行 DBCC UPDATEUSAGE。</span><span class="sxs-lookup"><span data-stu-id="4bab1-116">Run DBCC UPDATEUSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4bab1-117">说明</span><span class="sxs-lookup"><span data-stu-id="4bab1-117">Explanation</span></span>  
 <span data-ttu-id="4bab1-118">在版本低于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，用于表和索引行计数以及页计数的值可能不正确。</span><span class="sxs-lookup"><span data-stu-id="4bab1-118">In versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the values for the table and index row counts and page counts can become incorrect.</span></span> <span data-ttu-id="4bab1-119">根据 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前的版本创建的数据库可能包含错误的计数。</span><span class="sxs-lookup"><span data-stu-id="4bab1-119">Databases that were created on versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] may contain incorrect counts.</span></span> <span data-ttu-id="4bab1-120">已经对 DBCC CHECKDB 进行了增强，可以检测这些错误并在遇到错误时返回此警告消息。</span><span class="sxs-lookup"><span data-stu-id="4bab1-120">DBCC CHECKDB has been enhanced to detect these errors and returns this warning message when the error encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4bab1-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="4bab1-121">User Action</span></span>  
 <span data-ttu-id="4bab1-122">请针对指定的对象或索引或者针对包含该对象的数据库运行 DBCC UPDATEUSAGE，以更正无效计数。</span><span class="sxs-lookup"><span data-stu-id="4bab1-122">Run DBCC UPDATEUSAGE against the specified object or index, or against the database in which the object is contained to correct the invalid counts.</span></span>  
  
  
