---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b13d9c1c17eddb34648bc4a536e2fccf371b99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586721"
---
# <a name="mssqlserver_3169"></a><span data-ttu-id="b8463-102">MSSQLSERVER_3169</span><span class="sxs-lookup"><span data-stu-id="b8463-102">MSSQLSERVER_3169</span></span>
    
## <a name="details"></a><span data-ttu-id="b8463-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b8463-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8463-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b8463-104">Product Name</span></span>|<span data-ttu-id="b8463-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b8463-105">SQL Server</span></span>|  
|<span data-ttu-id="b8463-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b8463-106">Event ID</span></span>|<span data-ttu-id="b8463-107">3169</span><span class="sxs-lookup"><span data-stu-id="b8463-107">3169</span></span>|  
|<span data-ttu-id="b8463-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b8463-108">Event Source</span></span>|<span data-ttu-id="b8463-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b8463-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b8463-110">组件</span><span class="sxs-lookup"><span data-stu-id="b8463-110">Component</span></span>|<span data-ttu-id="b8463-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b8463-111">SQLEngine</span></span>|  
|<span data-ttu-id="b8463-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b8463-112">Symbolic Name</span></span>|<span data-ttu-id="b8463-113">NA</span><span class="sxs-lookup"><span data-stu-id="b8463-113">NA</span></span>|  
|<span data-ttu-id="b8463-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b8463-114">Message Text</span></span>|<span data-ttu-id="b8463-115">该数据库是在运行版本 %ls 的服务器上备份的。</span><span class="sxs-lookup"><span data-stu-id="b8463-115">The database was backed up on a server running version %ls.</span></span> <span data-ttu-id="b8463-116">该版本与此服务器(运行版本 %ls)不兼容。</span><span class="sxs-lookup"><span data-stu-id="b8463-116">That version is incompatible with this server, which is running version %ls.</span></span> <span data-ttu-id="b8463-117">请在支持该备份的服务器上还原该数据库，或者使用与此服务器兼容的备份。</span><span class="sxs-lookup"><span data-stu-id="b8463-117">Either restore the database on a server that supports the backup, or use a backup that is compatible with this server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b8463-118">说明</span><span class="sxs-lookup"><span data-stu-id="b8463-118">Explanation</span></span>  
 <span data-ttu-id="b8463-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的某些功能会影响数据库文件的结构。</span><span class="sxs-lookup"><span data-stu-id="b8463-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="b8463-120">将数据库还原到另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时，文件格式可能会与不同版本的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]不兼容。</span><span class="sxs-lookup"><span data-stu-id="b8463-120">When you restore a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b8463-121">例如，如果在较高版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 vardecimal 存储格式，然后尝试在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 之前的版本中还原数据库文件，便可能导致此错误。</span><span class="sxs-lookup"><span data-stu-id="b8463-121">For example, this error can be caused by using the vardecimalstorage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to restore the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b8463-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="b8463-122">User Action</span></span>  
 <span data-ttu-id="b8463-123">确定在发起服务器上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="b8463-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="b8463-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，右键单击服务器，然后单击 "**属性**"，或 `SELECT @@VERSION` 在查询窗口中键入。</span><span class="sxs-lookup"><span data-stu-id="b8463-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="b8463-125">通过使用原始版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 打开数据库。</span><span class="sxs-lookup"><span data-stu-id="b8463-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b8463-126">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中调查已在原始数据库中启用的功能。</span><span class="sxs-lookup"><span data-stu-id="b8463-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b8463-127">修改这些设置以使该设置能用于数据库要在其中进行还原的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="b8463-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be restored.</span></span>  
  
  
