---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b945350d9c7a862d4274f464afbd7fc5472f732c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689401"
---
# <a name="mssqlserver_21862"></a><span data-ttu-id="53911-102">MSSQLSERVER_21862</span><span class="sxs-lookup"><span data-stu-id="53911-102">MSSQLSERVER_21862</span></span>
    
## <a name="details"></a><span data-ttu-id="53911-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="53911-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53911-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="53911-104">Product Name</span></span>|<span data-ttu-id="53911-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53911-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53911-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="53911-106">Event ID</span></span>|<span data-ttu-id="53911-107">21862</span><span class="sxs-lookup"><span data-stu-id="53911-107">21862</span></span>|  
|<span data-ttu-id="53911-108">事件源</span><span class="sxs-lookup"><span data-stu-id="53911-108">Event Source</span></span>|<span data-ttu-id="53911-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53911-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53911-110">组件</span><span class="sxs-lookup"><span data-stu-id="53911-110">Component</span></span>|<span data-ttu-id="53911-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="53911-111">SQLEngine</span></span>|  
|<span data-ttu-id="53911-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="53911-112">Symbolic Name</span></span>|<span data-ttu-id="53911-113">SQLErrorNum21862</span><span class="sxs-lookup"><span data-stu-id="53911-113">SQLErrorNum21862</span></span>|  
|<span data-ttu-id="53911-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="53911-114">Message Text</span></span>|<span data-ttu-id="53911-115">无法使用同步方法 'database snapshot' 或 'database snapshot character' 在发布中发布 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="53911-115">FILESTREAM columns cannot be published in a publication by using a synchronization method of either 'database snapshot' or 'database snapshot character'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53911-116">说明</span><span class="sxs-lookup"><span data-stu-id="53911-116">Explanation</span></span>  
 <span data-ttu-id="53911-117">由于无法通过数据库快照访问 FILESTREAM 数据，因此，为发布的同步方法指定 *database snapshot* 或 *database_snapshot_character* 参数时，快照代理将无法读取 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="53911-117">Because FILESTREAM data cannot be accessed through a database snapshot, the snapshot agent will be unable to read FILESTREAM data when either the *database snapshot* or *database_snapshot_character* parameter is specified for the synchronization method of the publication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53911-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="53911-118">User Action</span></span>  
 <span data-ttu-id="53911-119">将发布的同步方法更改为 *database snapshot* 或 *database_snapshot_character* 以外的参数，或者只是在发布中排除 FILESTREAM 列。</span><span class="sxs-lookup"><span data-stu-id="53911-119">Change the publication synchronization method to something other than *database snapshot* or *database_snapshot_character*, or just exclude the FILESTREAM column from the publication.</span></span>  
  
  
