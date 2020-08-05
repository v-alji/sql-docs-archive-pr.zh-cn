---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8461069a3fceb7bdca318b82a522f7f51af83d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581230"
---
# <a name="mssqlserver_948"></a><span data-ttu-id="ceb2c-102">MSSQLSERVER_948</span><span class="sxs-lookup"><span data-stu-id="ceb2c-102">MSSQLSERVER_948</span></span>
    
## <a name="details"></a><span data-ttu-id="ceb2c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ceb2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ceb2c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ceb2c-104">Product Name</span></span>|<span data-ttu-id="ceb2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ceb2c-105">SQL Server</span></span>|  
|<span data-ttu-id="ceb2c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ceb2c-106">Event ID</span></span>|<span data-ttu-id="ceb2c-107">948</span><span class="sxs-lookup"><span data-stu-id="ceb2c-107">948</span></span>|  
|<span data-ttu-id="ceb2c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="ceb2c-108">Event Source</span></span>|<span data-ttu-id="ceb2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ceb2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ceb2c-110">组件</span><span class="sxs-lookup"><span data-stu-id="ceb2c-110">Component</span></span>|<span data-ttu-id="ceb2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ceb2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="ceb2c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="ceb2c-112">Symbolic Name</span></span>|<span data-ttu-id="ceb2c-113">NA</span><span class="sxs-lookup"><span data-stu-id="ceb2c-113">NA</span></span>|  
|<span data-ttu-id="ceb2c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="ceb2c-114">Message Text</span></span>|<span data-ttu-id="ceb2c-115">数据库 '%.\*ls' 的版本为 %d，无法打开。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-115">The database '%.\*ls' cannot be opened because it is version %d.</span></span> <span data-ttu-id="ceb2c-116">此服务器支持 %d 版及更低版本。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-116">This server supports version %d and earlier.</span></span> <span data-ttu-id="ceb2c-117">不支持降级路径。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-117">A downgrade path is not supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ceb2c-118">说明</span><span class="sxs-lookup"><span data-stu-id="ceb2c-118">Explanation</span></span>  
 <span data-ttu-id="ceb2c-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的某些功能会影响数据库文件的结构。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="ceb2c-120">将数据库附加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的另一个实例时，文件格式可能与不同版本的[!INCLUDE[ssDE](../../includes/ssde-md.md)]不兼容。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-120">When you attach a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="ceb2c-121">例如，如果在较高版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 vardecimal 存储格式，并尝试在低于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 的版本中附加数据库文件，便可能导致此错误。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-121">For example, this error can be caused by using the vardecimal storage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to attach the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ceb2c-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="ceb2c-122">User Action</span></span>  
 <span data-ttu-id="ceb2c-123">确定在发起服务器上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="ceb2c-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，右键单击服务器，然后单击 "**属性**"，或 `SELECT @@VERSION` 在查询窗口中键入。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="ceb2c-125">通过使用原始版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 打开数据库。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ceb2c-126">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中调查已在原始数据库中启用的功能。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ceb2c-127">修改这些设置以适用于将在其中附加数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="ceb2c-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be attached.</span></span>  
  
  
