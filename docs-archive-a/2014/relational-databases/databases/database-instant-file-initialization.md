---
title: 数据库实例文件初始化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
author: stevestein
ms.author: sstein
ms.openlocfilehash: dedd2c5b8d075dee8aeeb438904137558c664d95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581298"
---
# <a name="database-instant-file-initialization"></a><span data-ttu-id="0e1e1-102">数据库实例文件初始化</span><span class="sxs-lookup"><span data-stu-id="0e1e1-102">Database Instant File Initialization</span></span>
  <span data-ttu-id="0e1e1-103">初始化数据和日志文件以覆盖之前删除的文件遗留在磁盘上的任何现有数据。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-103">Data and log files are initialized to overwrite any existing data left on the disk from previously deleted files.</span></span> <span data-ttu-id="0e1e1-104">执行以下其中一项操作时，应首先通过用零填充数据和日志文件来初始化这些文件：</span><span class="sxs-lookup"><span data-stu-id="0e1e1-104">Data and log files are first initialized by filling the files with zeros when you perform one of the following operations:</span></span>  
  
-   <span data-ttu-id="0e1e1-105">创建数据库。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-105">Create a database.</span></span>  
  
-   <span data-ttu-id="0e1e1-106">向现有数据库中添加文件、日志或数据。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-106">Add files, log or data, to an existing database.</span></span>  
  
-   <span data-ttu-id="0e1e1-107">增大现有文件的大小（包括自动增长操作）。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-107">Increase the size of an existing file (including autogrow operations).</span></span>  
  
-   <span data-ttu-id="0e1e1-108">还原数据库或文件组。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-108">Restore a database or filegroup.</span></span>  
  
 <span data-ttu-id="0e1e1-109">文件初始化会导致这些操作花费更多时间。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-109">File initialization causes these operations to take longer.</span></span> <span data-ttu-id="0e1e1-110">但是，首次将数据写入文件后，操作系统就不必用零来填充文件。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-110">However, when data is written to the files for the first time, the operating system does not have to fill the files with zeros.</span></span>  
  
## <a name="instant-file-initialization"></a><span data-ttu-id="0e1e1-111">即时文件初始化</span><span class="sxs-lookup"><span data-stu-id="0e1e1-111">Instant File Initialization</span></span>  
 <span data-ttu-id="0e1e1-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，可以在瞬间对数据文件进行初始化。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-112">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data files can be initialized instantaneously.</span></span> <span data-ttu-id="0e1e1-113">这样可以快速执行上述文件操作。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-113">This allows for fast execution of the previously mentioned file operations.</span></span> <span data-ttu-id="0e1e1-114">即时文件初始化功能将回收使用的磁盘空间，而无需使用零填充空间。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-114">Instant file initialization reclaims used disk space without filling that space with zeros.</span></span> <span data-ttu-id="0e1e1-115">相反，新数据写入文件时会覆盖磁盘内容。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-115">Instead, disk content is overwritten as new data is written to the files.</span></span> <span data-ttu-id="0e1e1-116">日志文件不能立即初始化。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-116">Log files cannot be initialized instantaneously.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e1e1-117">只有在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] 或 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 或更高版本中才可以使用即时文件初始化功能。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-117">Instant file initialization is available only on [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] or [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="0e1e1-118">即时文件初始化功能仅在向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) 服务帐户授予了 SE_MANAGE_VOLUME_NAME 之后才可用。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-118">Instant file initialization is only available if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) service account has been granted SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="0e1e1-119">Windows Administrator 组的成员拥有此权限，并可以通过将其他用户添加到 **执行卷维护任务** 安全策略中来为其授予此权限。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-119">Members of the Windows Administrator group have this right and can grant it to other users by adding them to the **Perform Volume Maintenance Tasks** security policy.</span></span> <span data-ttu-id="0e1e1-120">有关分配用户权限的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-120">For more information about assigning user rights, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="0e1e1-121">当启用 TDE 时，即时文件初始化功能不可用。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-121">Instant file initialization is not available when TDE is enabled.</span></span>  
  
 <span data-ttu-id="0e1e1-122">要向一个帐户授予 `Perform volume maintenance tasks` 权限：</span><span class="sxs-lookup"><span data-stu-id="0e1e1-122">To grant an account the `Perform volume maintenance tasks` permission:</span></span>  
  
1.  <span data-ttu-id="0e1e1-123">在将要创建备份文件的计算机上打开 `Local Security Policy` 应用程序 (`secpol.msc`)。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-123">On the computer where the backup file will be created, open the `Local Security Policy` application (`secpol.msc`).</span></span>  
  
2.  <span data-ttu-id="0e1e1-124">在左侧窗格中，展开“本地策略” ，然后单击“用户权限指派” 。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-124">In the left pane, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
3.  <span data-ttu-id="0e1e1-125">在右侧窗格中，双击“执行卷维护任务”。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-125">In the right pane, double-click **Perform volume maintenance tasks**.</span></span>  
  
4.  <span data-ttu-id="0e1e1-126">单击“添加用户或组” \*\*\*\* ，添加用于备份的任何用户帐户。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-126">Click **Add User or Group** and add any user accounts that are used for backups.</span></span>  
  
5.  <span data-ttu-id="0e1e1-127">单击 "**应用**"，然后关闭所有 `Local Security Policy` 对话框。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-127">Click **Apply**, and then close all `Local Security Policy` dialog boxes.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="0e1e1-128">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="0e1e1-128">Security Considerations</span></span>  
 <span data-ttu-id="0e1e1-129">因为只有在新数据写入文件中时才覆盖删除的磁盘内容，因此，未授权的主体可能会访问删除的内容。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-129">Because the deleted disk content is overwritten only as new data is written to the files, the deleted content might be accessed by an unauthorized principal.</span></span> <span data-ttu-id="0e1e1-130">当数据库文件连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例之后，可以通过文件中的随机访问控制列表 (DACL) 来降低此信息泄露的风险。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-130">While the database file is attached to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this information disclosure threat is reduced by the discretionary access control list (DACL) on the file.</span></span> <span data-ttu-id="0e1e1-131">此 DACL 仅允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户和本地管理员访问文件。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-131">This DACL allows file access only to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and the local administrator.</span></span> <span data-ttu-id="0e1e1-132">但是，当文件分离以后，可以由不具有 SE_MANAGE_VOLUME_NAME 的用户或服务访问。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-132">However, when the file is detached, it may be accessed by a user or service that does not have SE_MANAGE_VOLUME_NAME.</span></span> <span data-ttu-id="0e1e1-133">在备份数据库时，也存在类似风险。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-133">A similar threat exists when the database is backed up.</span></span> <span data-ttu-id="0e1e1-134">如果未使用适当的 DACL 对备份文件进行保护，则未授权的用户或服务将可以使用删除的内容。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-134">The deleted content can become available to an unauthorized user or service if the backup file is not protected with an appropriate DACL.</span></span>  
  
 <span data-ttu-id="0e1e1-135">如果担心可能会泄漏删除的内容，则应执行以下两种或其中一种操作：</span><span class="sxs-lookup"><span data-stu-id="0e1e1-135">If the potential for disclosing deleted content is a concern, you should do one or both of the following:</span></span>  
  
-   <span data-ttu-id="0e1e1-136">请始终确保所有分离的数据文件和备份文件都具有限制性的 DACL。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-136">Always make sure that any detached data files and backup files have restrictive DACLs.</span></span>  
  
-   <span data-ttu-id="0e1e1-137">通过从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户中撤消 SE_MANAGE_VOLUME_NAME 来禁用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的即时文件初始化功能。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-137">Disable instant file initialization for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by revoking SE_MANAGE_VOLUME_NAME from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e1e1-138">禁用即时文件初始化功能只会影响在用户权限撤消之后创建的文件或其大小增大的文件。</span><span class="sxs-lookup"><span data-stu-id="0e1e1-138">Disabling instant file initialization only affects files that are created or increased in size after the user right is revoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1e1-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e1e1-139">See Also</span></span>  
 [<span data-ttu-id="0e1e1-140">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e1e1-140">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
