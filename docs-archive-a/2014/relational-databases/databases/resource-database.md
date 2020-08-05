---
title: Resource 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581288"
---
# <a name="resource-database"></a><span data-ttu-id="365d5-102">Resource 数据库</span><span class="sxs-lookup"><span data-stu-id="365d5-102">Resource Database</span></span>
  <span data-ttu-id="365d5-103">Resource 数据库为只读数据库，它包含了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的所有系统对象。</span><span class="sxs-lookup"><span data-stu-id="365d5-103">The Resource database is a read-only database that contains all the system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="365d5-104">系统对象（如 sys.objects）在物理上保留在 Resource 数据库中，但在逻辑上却显示在每个数据库的 sys 架构中。</span><span class="sxs-lookup"><span data-stu-id="365d5-104">system objects, such as sys.objects, are physically persisted in the Resource database, but they logically appear in the sys schema of every database.</span></span> <span data-ttu-id="365d5-105">Resource 数据库不包含用户数据或用户元数据。</span><span class="sxs-lookup"><span data-stu-id="365d5-105">The Resource database does not contain user data or user metadata.</span></span>  
  
 <span data-ttu-id="365d5-106">Resource 数据库可比较轻松快捷地升级到新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="365d5-106">The Resource database makes upgrading to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an easier and faster procedure.</span></span> <span data-ttu-id="365d5-107">在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，进行升级需要删除和创建系统对象。</span><span class="sxs-lookup"><span data-stu-id="365d5-107">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], upgrading required dropping and creating system objects.</span></span> <span data-ttu-id="365d5-108">由于 Resource 数据库文件包含所有系统对象，因此，现在仅通过将单个 Resource 数据库文件复制到本地服务器便可完成升级。</span><span class="sxs-lookup"><span data-stu-id="365d5-108">Because the Resource database file contains all system objects, an upgrade is now accomplished simply by copying the single Resource database file to the local server.</span></span>  
  
## <a name="physical-properties-of-resource"></a><span data-ttu-id="365d5-109">Resource 的物理属性</span><span class="sxs-lookup"><span data-stu-id="365d5-109">Physical Properties of Resource</span></span>  
 <span data-ttu-id="365d5-110">Resource 数据库的物理文件名为 mssqlsystemresource.mdf 和 mssqlsystemresource.ldf。</span><span class="sxs-lookup"><span data-stu-id="365d5-110">The physical file names of the Resource database are mssqlsystemresource.mdf and mssqlsystemresource.ldf.</span></span> <span data-ttu-id="365d5-111">这些文件位于 \<*drive*>:\Program Files\Microsoft SQL Server \MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ 中，不应移动。</span><span class="sxs-lookup"><span data-stu-id="365d5-111">These files are located in \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ and should not be moved.</span></span> <span data-ttu-id="365d5-112">每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都具有一个（也是唯一的一个）关联的 mssqlsystemresource.mdf 文件，并且实例间不共享此文件。</span><span class="sxs-lookup"><span data-stu-id="365d5-112">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one and only one associated mssqlsystemresource.mdf file, and instances do not share this file.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="365d5-113">有时，升级和服务包会提供安装到 BINN 文件夹的新资源数据库。</span><span class="sxs-lookup"><span data-stu-id="365d5-113">Upgrades and service packs sometimes provide a new resource database which is installed to the BINN folder.</span></span> <span data-ttu-id="365d5-114">不支持或建议更改资源数据库的位置。</span><span class="sxs-lookup"><span data-stu-id="365d5-114">Changing the location of the resource database is not supported or recommended.</span></span>  
  
## <a name="backing-up-and-restoring-the-resource-database"></a><span data-ttu-id="365d5-115">备份和还原 Resource 数据库</span><span class="sxs-lookup"><span data-stu-id="365d5-115">Backing Up and Restoring the Resource Database</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="365d5-116">不能备份 Resource 数据库。</span><span class="sxs-lookup"><span data-stu-id="365d5-116">cannot back up the Resource database.</span></span> <span data-ttu-id="365d5-117">通过将 mssqlsystemresource.mdf 文件作为二进制 (.EXE) 文件而不是作为数据库文件，可以执行您自己的基于文件的备份或基于磁盘的备份，但是不能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还原所做的备份。</span><span class="sxs-lookup"><span data-stu-id="365d5-117">You can perform your own file-based or a disk-based backup by treating the mssqlsystemresource.mdf file as if it were a binary (.EXE) file, rather than a database file, but you cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to restore your backups.</span></span> <span data-ttu-id="365d5-118">只能手动还原 mssqlsystemresource.mdf 的备份副本，并且必须谨慎，不要使用过时版本或可能不安全的版本覆盖当前的 Resource 数据库。</span><span class="sxs-lookup"><span data-stu-id="365d5-118">Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current Resource database with an out-of-date or potentially insecure version.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="365d5-119">还原 mssqlsystemresource.mdf 的备份之后，必须重新应用所有后续更新。</span><span class="sxs-lookup"><span data-stu-id="365d5-119">After restoring a backup of mssqlsystemresource.mdf, you must reapply any subsequent updates.</span></span>  
  
## <a name="accessing-the-resource-database"></a><span data-ttu-id="365d5-120">访问 Resource 数据库</span><span class="sxs-lookup"><span data-stu-id="365d5-120">Accessing the Resource Database</span></span>  
 <span data-ttu-id="365d5-121">Resource 数据库仅应由 Microsoft 客户支持服务部门 (CSS) 的专家修改或在其指导下进行修改。</span><span class="sxs-lookup"><span data-stu-id="365d5-121">The Resource database should only be modified by or at the direction of a Microsoft Customer Support Services (CSS) specialist.</span></span> <span data-ttu-id="365d5-122">Resource 数据库的 ID 始终为 32767。</span><span class="sxs-lookup"><span data-stu-id="365d5-122">The ID of the Resource database is always 32767.</span></span> <span data-ttu-id="365d5-123">与 Resource 数据库相关联的其他重要值是版本号和数据库的上次更新时间。</span><span class="sxs-lookup"><span data-stu-id="365d5-123">Other important values associated with the Resource database are the version number and the last time that the database was updated.</span></span>  
  
 <span data-ttu-id="365d5-124">**若要确定** Resource **数据库的版本号，请使用**：</span><span class="sxs-lookup"><span data-stu-id="365d5-124">**To determine the version number of the** Resource **database, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 <span data-ttu-id="365d5-125">**若要确定** Resource **数据库的上次升级时间，请使用**：</span><span class="sxs-lookup"><span data-stu-id="365d5-125">**To determine when the** Resource **database was last updated, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 <span data-ttu-id="365d5-126">**若要访问系统对象的 SQL 定义，请使用 OBJECT_DEFINITION 函数：**</span><span class="sxs-lookup"><span data-stu-id="365d5-126">**To access SQL definitions of system objects, use the OBJECT_DEFINITION function:**</span></span>  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="365d5-127">相关内容</span><span class="sxs-lookup"><span data-stu-id="365d5-127">Related Content</span></span>  
 [<span data-ttu-id="365d5-128">系统数据库</span><span class="sxs-lookup"><span data-stu-id="365d5-128">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="365d5-129">用于数据库管理员的诊断连接</span><span class="sxs-lookup"><span data-stu-id="365d5-129">Diagnostic Connection for Database Administrators</span></span>](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [<span data-ttu-id="365d5-130">OBJECT_DEFINITION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="365d5-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [<span data-ttu-id="365d5-131">SERVERPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="365d5-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [<span data-ttu-id="365d5-132">在单用户模式下启动 SQL Server</span><span class="sxs-lookup"><span data-stu-id="365d5-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
