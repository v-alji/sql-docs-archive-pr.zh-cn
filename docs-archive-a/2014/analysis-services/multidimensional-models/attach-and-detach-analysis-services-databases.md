---
title: 附加和分离 Analysis Services 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd72277970605691e06f3baacf167ea135343b3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590953"
---
# <a name="attach-and-detach-analysis-services-databases"></a><span data-ttu-id="73c19-102">附加和分离 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="73c19-102">Attach and Detach Analysis Services Databases</span></span>
  <span data-ttu-id="73c19-103">在某些情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库管理员 (dba) 经常需要将数据库脱机一段时间，然后在同一服务器实例或其他服务器实例上将数据库恢复联机。</span><span class="sxs-lookup"><span data-stu-id="73c19-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to take a database offline for a period, and then bring that database back online on the same server instance, or on a different one.</span></span> <span data-ttu-id="73c19-104">根据业务需要（例如，将数据库移到另一个磁盘以获得更好的性能、为数据库扩容获取空间或升级产品），经常需要进行上述操作。</span><span class="sxs-lookup"><span data-stu-id="73c19-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span> <span data-ttu-id="73c19-105">对于所有这些情况和更多情况， `Attach` 和 `Detach` 命令使 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba 能够使数据库脱机，并使其重新联机，只需很少的精力。</span><span class="sxs-lookup"><span data-stu-id="73c19-105">For all those cases and more, the `Attach` and `Detach` commands enable the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba to take the database offline and bring it back online with little effort.</span></span>  
  
## <a name="attach-and-detach-commands"></a><span data-ttu-id="73c19-106">附加和分离命令。</span><span class="sxs-lookup"><span data-stu-id="73c19-106">Attach and Detach commands</span></span>  
 <span data-ttu-id="73c19-107">通过 `Attach` 命令可使已脱机的数据库恢复联机。</span><span class="sxs-lookup"><span data-stu-id="73c19-107">The `Attach` command enables you to bring online a database that was taken offline.</span></span> <span data-ttu-id="73c19-108">可以将该数据库附加到原始的服务器实例，也可以附加到另一个实例。</span><span class="sxs-lookup"><span data-stu-id="73c19-108">You can attach the database to the original server instance, or to another instance.</span></span> <span data-ttu-id="73c19-109">在附加数据库时，用户可以为该数据库指定 **ReadWriteMode** 设置。</span><span class="sxs-lookup"><span data-stu-id="73c19-109">When you attach a database the user can specify the **ReadWriteMode** setting for the database.</span></span> <span data-ttu-id="73c19-110">使用 `Detach` 命令可使数据库与服务器脱机。</span><span class="sxs-lookup"><span data-stu-id="73c19-110">The `Detach` command enables you to take offline a database from the server.</span></span>  
  
## <a name="attach-and-detach-usage"></a><span data-ttu-id="73c19-111">附加和分离命令的用法</span><span class="sxs-lookup"><span data-stu-id="73c19-111">Attach and Detach Usage</span></span>  
 <span data-ttu-id="73c19-112">`Attach` 命令用于使现有数据库结构联机。</span><span class="sxs-lookup"><span data-stu-id="73c19-112">The `Attach` command is used to bring online an existing database structure.</span></span> <span data-ttu-id="73c19-113">如果该数据库是在 `ReadWrite` 模式下附加的，则只能将其附加到服务器实例一次。</span><span class="sxs-lookup"><span data-stu-id="73c19-113">If the database is attached in `ReadWrite` mode, it can be attached only one time to a server instance.</span></span> <span data-ttu-id="73c19-114">但是，如果此数据库是在 `ReadOnly` 模式下附加的，则可以将其多次附加到不同的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="73c19-114">However, if the database is attached in `ReadOnly` mode, it can be attached multiple times to different server instances.</span></span> <span data-ttu-id="73c19-115">但是，不能将同一数据库多次附加到同一服务器实例。</span><span class="sxs-lookup"><span data-stu-id="73c19-115">However, the same database cannot be attached more than one time to the same server instance.</span></span> <span data-ttu-id="73c19-116">即使已将数据复制到不同的文件夹中，在尝试多次附加同一数据库时也会引发错误。</span><span class="sxs-lookup"><span data-stu-id="73c19-116">An error is raised when an attempt is made to attach the same database more than one time, even if the data has been copied to separate folders.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73c19-117">如果分离数据库时需要输入密码，则附加数据库时需要输入相同的密码。</span><span class="sxs-lookup"><span data-stu-id="73c19-117">If a password was required to detach the database, the same password is required to attach the database.</span></span>  
  
 <span data-ttu-id="73c19-118">`Detach` 命令用于使现有数据库结构脱机。</span><span class="sxs-lookup"><span data-stu-id="73c19-118">The `Detach` command is used to take offline an existing database structure.</span></span> <span data-ttu-id="73c19-119">分离数据库时，应提供一个密码来保护机密的元数据。</span><span class="sxs-lookup"><span data-stu-id="73c19-119">When a database is detached, you should provide a password to protect confidential metadata.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73c19-120">若要保护数据文件的内容，应针对文件夹、子文件夹和数据文件使用访问控制列表。</span><span class="sxs-lookup"><span data-stu-id="73c19-120">To protect the content of the data files, you should use an access control list for the folder, subfolders, and data files.</span></span>  
  
 <span data-ttu-id="73c19-121">分离数据库时，服务器会执行下列步骤。</span><span class="sxs-lookup"><span data-stu-id="73c19-121">When you detach a database, the server follows these steps.</span></span>  
  
|<span data-ttu-id="73c19-122">分离读/写数据库</span><span class="sxs-lookup"><span data-stu-id="73c19-122">Detaching a read/write database</span></span>|<span data-ttu-id="73c19-123">分离只读数据库</span><span class="sxs-lookup"><span data-stu-id="73c19-123">Detaching a read-only database</span></span>|  
|--------------------------------------|-------------------------------------|  
|<span data-ttu-id="73c19-124">1) 服务器会对数据库上的 CommitExclusive 锁发出请求</span><span class="sxs-lookup"><span data-stu-id="73c19-124">1) The server issues a request for a CommitExclusive Lock on the database</span></span><br /><span data-ttu-id="73c19-125">2) 服务器会等待，直到提交或回滚所有正在进行的事务</span><span class="sxs-lookup"><span data-stu-id="73c19-125">2) The server waits until all ongoing transactions are either committed or rolled back</span></span><br /><span data-ttu-id="73c19-126">3) 服务器会构建分离数据库必须具备的所有元数据</span><span class="sxs-lookup"><span data-stu-id="73c19-126">3) The server builds all the metadata that it must have to detach the database</span></span><br /><span data-ttu-id="73c19-127">4) 将数据库标记为已删除</span><span class="sxs-lookup"><span data-stu-id="73c19-127">4) The database is marked as deleted</span></span><br /><span data-ttu-id="73c19-128">5) 服务器提交事务</span><span class="sxs-lookup"><span data-stu-id="73c19-128">5) The server commits the transaction</span></span>|<span data-ttu-id="73c19-129">1) 将数据库标记为已删除</span><span class="sxs-lookup"><span data-stu-id="73c19-129">1) The database is marked as deleted</span></span><br /><span data-ttu-id="73c19-130">2) 服务器提交事务</span><span class="sxs-lookup"><span data-stu-id="73c19-130">2) The server commits the transaction</span></span><br /><br /> <br /><br /> <span data-ttu-id="73c19-131">注意：不能更改只读数据库的分离密码。</span><span class="sxs-lookup"><span data-stu-id="73c19-131">Note: The detaching password cannot be changed for a read-only database.</span></span> <span data-ttu-id="73c19-132">如果为已包含密码的附加数据库提供密码参数，则会产生错误。</span><span class="sxs-lookup"><span data-stu-id="73c19-132">An error is raised if the password parameter is provided for an attached database that already contains a password.</span></span>|  
  
 <span data-ttu-id="73c19-133"> 和  命令必须作为单独的操作执行。</span><span class="sxs-lookup"><span data-stu-id="73c19-133">The `Attach` and `Detach` commands must be executed as single operations.</span></span> <span data-ttu-id="73c19-134">在同一事务中，不能将它们与其他操作一起执行。</span><span class="sxs-lookup"><span data-stu-id="73c19-134">They cannot be combined with other operations in the same transaction.</span></span> <span data-ttu-id="73c19-135">此外， `Attach` 和 `Detach` 命令都是原子事务命令。</span><span class="sxs-lookup"><span data-stu-id="73c19-135">Also, the `Attach` and `Detach` commands are atomic transactional commands.</span></span> <span data-ttu-id="73c19-136">这意味着操作只有成功或失败两种情况。</span><span class="sxs-lookup"><span data-stu-id="73c19-136">This means the operation will either succeed or fail.</span></span> <span data-ttu-id="73c19-137">数据库不会处于未完成的状态。</span><span class="sxs-lookup"><span data-stu-id="73c19-137">No database will be left in an uncompleted state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73c19-138">执行 `Detach` 命令需要服务器或数据库管理员权限。</span><span class="sxs-lookup"><span data-stu-id="73c19-138">Server or database administrator privileges are required to execute the `Detach` command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73c19-139">执行 `Attach` 命令需要服务器管理员权限。</span><span class="sxs-lookup"><span data-stu-id="73c19-139">Server administrator privileges are required to execute the `Attach` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c19-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73c19-140">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="73c19-141">[Microsoft.analysisservices.sharepoint.integration.dll \*。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="73c19-141">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="73c19-142">[移动 Analysis Services 数据库](move-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="73c19-142">[Move an Analysis Services Database](move-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="73c19-143">[数据库 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="73c19-143">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="73c19-144">[在 ReadOnly 和 ReadWrite 模式之间切换 Analysis Services 数据库](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span><span class="sxs-lookup"><span data-stu-id="73c19-144">[Switch an Analysis Services database between ReadOnly and ReadWrite modes](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span></span>  
 <span data-ttu-id="73c19-145">[分离元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="73c19-145">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 [<span data-ttu-id="73c19-146">附加元素</span><span class="sxs-lookup"><span data-stu-id="73c19-146">Attach Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
