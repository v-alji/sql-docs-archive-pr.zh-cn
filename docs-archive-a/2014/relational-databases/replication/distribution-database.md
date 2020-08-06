---
title: 分发数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d98a80be52ae77cbdaf1581a5b3397f9d11af4fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578116"
---
# <a name="distribution-database"></a><span data-ttu-id="8af53-102">分发数据库</span><span class="sxs-lookup"><span data-stu-id="8af53-102">Distribution Database</span></span>
  <span data-ttu-id="8af53-103">分发数据库用于存储所有类型复制的元数据和历史记录数据，并存储事务复制的事务。</span><span class="sxs-lookup"><span data-stu-id="8af53-103">The distribution database stores metadata and history data for all types of replication, and transactions for transactional replication.</span></span>  
  
 <span data-ttu-id="8af53-104">在许多情况下，单个分发数据库就能够满足需要。</span><span class="sxs-lookup"><span data-stu-id="8af53-104">In many cases, a single distribution database is sufficient.</span></span> <span data-ttu-id="8af53-105">不过，如果多个发布服务器使用单个分发服务器，则应考虑为每个发布服务器都创建一个分发数据库。</span><span class="sxs-lookup"><span data-stu-id="8af53-105">However, if multiple Publishers use a single Distributor, consider creating a distribution database for each Publisher.</span></span> <span data-ttu-id="8af53-106">这样可确保通过每个分发数据库的数据流是不同的。</span><span class="sxs-lookup"><span data-stu-id="8af53-106">Doing so ensures that the data flowing through each distribution database is distinct.</span></span> <span data-ttu-id="8af53-107">使用配置分发向导可以为分发服务器指定一个分发数据库。</span><span class="sxs-lookup"><span data-stu-id="8af53-107">You can specify one distribution database for the Distributor using the Configure Distribution Wizard.</span></span> <span data-ttu-id="8af53-108">如果需要，可以在 **“分发服务器属性”** 对话框中指定其他分发数据库。</span><span class="sxs-lookup"><span data-stu-id="8af53-108">If necessary, specify additional distribution databases in the **Distributor Properties** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8af53-109">选项</span><span class="sxs-lookup"><span data-stu-id="8af53-109">Options</span></span>  
 <span data-ttu-id="8af53-110">**分发数据库名称**</span><span class="sxs-lookup"><span data-stu-id="8af53-110">**Distribution database name**</span></span>  
 <span data-ttu-id="8af53-111">为分发数据库输入名称。</span><span class="sxs-lookup"><span data-stu-id="8af53-111">Enter a name for the distribution database.</span></span> <span data-ttu-id="8af53-112">分发数据库的默认名称为“distribution”。</span><span class="sxs-lookup"><span data-stu-id="8af53-112">The default name for the distribution database is 'distribution'.</span></span> <span data-ttu-id="8af53-113">如果指定名称，名称最多可包含 128 个字符，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中必须是唯一的，并且必须符合标识符的规则。</span><span class="sxs-lookup"><span data-stu-id="8af53-113">If you specify a name, the name can be a maximum of 128 characters, must be unique within an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and must conform to the rules for identifiers.</span></span> <span data-ttu-id="8af53-114">有关详细信息，请参阅 [Database Identifiers](../databases/database-identifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="8af53-114">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
 <span data-ttu-id="8af53-115">**分发数据库文件的文件夹** / **分发数据库日志文件的文件夹**</span><span class="sxs-lookup"><span data-stu-id="8af53-115">**Folder for the distribution database file** and **Folder for the distribution database log file**</span></span>  
 <span data-ttu-id="8af53-116">输入分发数据库和日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="8af53-116">Enter the path for the distribution database and log files.</span></span> <span data-ttu-id="8af53-117">这些路径必须指向分发服务器的本地磁盘，并以本地驱动器号和冒号（如 C：）开头。</span><span class="sxs-lookup"><span data-stu-id="8af53-117">Paths must refer to disks that are local to the Distributor and begin with a local drive letter and colon (for example, C:).</span></span> <span data-ttu-id="8af53-118">映射的驱动器号和网络路径无效。</span><span class="sxs-lookup"><span data-stu-id="8af53-118">Mapped drive letters and network paths are not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8af53-119">通过将分发数据库日志放置在与分发数据库不同的磁盘驱动器上，可以减少事务写入操作所需的时间并提高复制的性能。</span><span class="sxs-lookup"><span data-stu-id="8af53-119">You can decrease the time it takes to write transactions and improve the performance of replication by placing the distribution database log on a separate disk drive from the distribution database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af53-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8af53-120">See Also</span></span>  
 <span data-ttu-id="8af53-121">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="8af53-121">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="8af53-122">[配置发布和分发](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="8af53-122">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 [<span data-ttu-id="8af53-123">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="8af53-123">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)  
  
  
