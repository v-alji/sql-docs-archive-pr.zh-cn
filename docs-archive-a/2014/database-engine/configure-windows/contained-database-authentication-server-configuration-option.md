---
title: contained database authentication 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf5bf07c8b0913ff81f31ff0ca64a18eee0f2ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588021"
---
# <a name="contained-database-authentication-server-configuration-option"></a><span data-ttu-id="54a33-102">contained database authentication 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="54a33-102">contained database authentication Server Configuration Option</span></span>
  <span data-ttu-id="54a33-103">使用 **contained database authentication** 选项对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例启用包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="54a33-103">Use the **contained database authentication** option to enable contained databases on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="54a33-104">此服务器选项允许您控制 **contained database authentication**。</span><span class="sxs-lookup"><span data-stu-id="54a33-104">This server option allows you to control **contained database authentication**.</span></span>  
  
-   <span data-ttu-id="54a33-105">如果 **contained database authentication** 对实例关闭 (0)，则无法创建包含的数据库或将其附加到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="54a33-105">When **contained database authentication** is off (0) for the instance, contained databases cannot be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="54a33-106">如果 **contained database authentication** 对实例打开 (1)，则可以创建包含的数据库或将其附加到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="54a33-106">When **contained database authentication** is on (1) for the instance, contained databases can be created, or attached to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="54a33-107">包含的数据库包括定义数据库所需的所有数据库设置和元数据，它与安装数据库的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例没有配置依赖关系。</span><span class="sxs-lookup"><span data-stu-id="54a33-107">A contained database includes all database settings and metadata required to define the database and has no configuration dependencies on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] where the database is installed.</span></span> <span data-ttu-id="54a33-108">用户可以连接到数据库而无需在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 级别对登录名进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="54a33-108">Users can connect to the database without authenticating a login at the [!INCLUDE[ssDE](../../includes/ssde-md.md)] level.</span></span> <span data-ttu-id="54a33-109">将数据库与数据库引擎隔离可以轻松地将数据库移到另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="54a33-109">Isolating the database from the Database Engine makes it possible to easily move the database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54a33-110">在数据库中包括所有数据库设置有利于数据库所有者管理数据库的所有配置设置。</span><span class="sxs-lookup"><span data-stu-id="54a33-110">Including all the database settings in the database enables database owners to manage all the configuration settings for the database.</span></span> <span data-ttu-id="54a33-111">有关包含的数据库的详细信息，请参阅 [Contained Databases](../../relational-databases/databases/contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="54a33-111">For more information about contained databases, see [Contained Databases](../../relational-databases/databases/contained-databases.md).</span></span>  
  
 <span data-ttu-id="54a33-112">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例具有包含数据库，则可以使用 **RECONFIGURE WITH OVERRIDE** 语句将 **contained database authentication** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="54a33-112">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has any contained databases the **contained database authentication** setting can be set to 0 by using the **RECONFIGURE WITH OVERRIDE** statement.</span></span> <span data-ttu-id="54a33-113">将 **contained database authentication** 设置为 0 将禁用包含数据库的包含数据库身份验证。</span><span class="sxs-lookup"><span data-stu-id="54a33-113">Setting **contained database authentication** to 0 will disable contained database authentication for the contained databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="54a33-114">启用包含的数据库时，具有 ALTER ANY USER 权限的数据库用户（如 db_owner 和 db_accessadmin 数据库角色的成员）可以授予对数据库的访问权限，并由此授予对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="54a33-114">When contained databases are enabled, database users with the ALTER ANY USER permission, such as members of the db_owner and db_accessadmin database roles, can grant access to databases and by doing so, grant access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54a33-115">这意味着控制对服务器的访问权限不再限于 sysadmin 和 securityadmin 固定服务器角色的成员以及具有服务器级别 CONTROL SERVER 和 ALTER ANY LOGIN 权限的登录。</span><span class="sxs-lookup"><span data-stu-id="54a33-115">This means that control over access to the server is no longer limited to members of the sysadmin and securityadmin fixed server role, and logins with the server level CONTROL SERVER and ALTER ANY LOGIN permission.</span></span> <span data-ttu-id="54a33-116">在允许包含的数据库之前，应了解与包含的数据库相关的风险。</span><span class="sxs-lookup"><span data-stu-id="54a33-116">Before allowing contained databases, you should understand the risks associated with contained databases.</span></span> <span data-ttu-id="54a33-117">有关详细信息，请参阅 [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="54a33-117">For more information, see [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="54a33-118">示例</span><span class="sxs-lookup"><span data-stu-id="54a33-118">Examples</span></span>  
 <span data-ttu-id="54a33-119">下面的示例对 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例启用包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="54a33-119">The following example enables contained databases on the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="54a33-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54a33-120">See Also</span></span>  
 <span data-ttu-id="54a33-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54a33-121">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="54a33-122">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54a33-122">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 [<span data-ttu-id="54a33-123">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="54a33-123">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
