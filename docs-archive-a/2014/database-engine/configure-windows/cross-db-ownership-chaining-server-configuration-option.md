---
title: cross db ownership chaining 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfb768065cc0aa2aaa7aed0f996b18e46f1da7ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587601"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a><span data-ttu-id="91496-102">cross db ownership chaining 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="91496-102">cross db ownership chaining Server Configuration Option</span></span>
  <span data-ttu-id="91496-103">使用 cross db ownership chaining 选项可以为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例配置跨数据库所有权链。</span><span class="sxs-lookup"><span data-stu-id="91496-103">Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="91496-104">此服务器选项使您能够在数据库级别控制跨数据库所有权链接，或者允许在所有数据库中启用跨数据库所有权链接：</span><span class="sxs-lookup"><span data-stu-id="91496-104">This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:</span></span>  
  
-   <span data-ttu-id="91496-105">如果实例的 **cross db ownership chaining** 为关（设置为 0），将禁用所有数据库的跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="91496-105">When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.</span></span>  
  
-   <span data-ttu-id="91496-106">如果实例的 **cross db ownership chaining** 为开（设置为 1），将启用所有数据库的跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="91496-106">When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.</span></span>  
  
-   <span data-ttu-id="91496-107">可以使用 ALTER DATABASE 语句的 SET 子句为各个数据库设置跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="91496-107">You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="91496-108">如果正在创建新的数据库，则可以使用 CREATE DATABASE 语句设置新数据库的跨数据库所有权链接选项。</span><span class="sxs-lookup"><span data-stu-id="91496-108">If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.</span></span>  
  
     <span data-ttu-id="91496-109">建议不要将 **cross db ownership chaining** 设置为 1，除非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例所驻留的所有数据库都必须参与跨数据库所有权链接，并且你了解此设置隐含的安全问题。</span><span class="sxs-lookup"><span data-stu-id="91496-109">Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.</span></span>  
  
## <a name="controlling-cross-database-ownership-chaining"></a><span data-ttu-id="91496-110">控制跨数据库所有权链接</span><span class="sxs-lookup"><span data-stu-id="91496-110">Controlling Cross-Database Ownership Chaining</span></span>  
 <span data-ttu-id="91496-111">在打开或关闭跨数据库所有权链接之前，请注意下列事项：</span><span class="sxs-lookup"><span data-stu-id="91496-111">Before turning cross-database ownership chaining on or off, consider the following:</span></span>  
  
-   <span data-ttu-id="91496-112">只有 **sysadmin** 固定服务器角色成员能够启用或禁用跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="91496-112">You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.</span></span>  
  
-   <span data-ttu-id="91496-113">关闭生产服务器的跨数据库所有权链接之前，应全面测试所有应用程序（包括第三方应用程序）以确保更改不会影响应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="91496-113">Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.</span></span>  
  
-   <span data-ttu-id="91496-114">如果使用 **sp_configure** 指定 RECONFIGURE，则在服务器运行时可以更改 **cross db ownership chaining**选项。</span><span class="sxs-lookup"><span data-stu-id="91496-114">You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.</span></span>  
  
-   <span data-ttu-id="91496-115">如果有数据库需要跨数据库所有权链接，建议使用 **sp_configure** 为实例禁用 **cross db ownership chaining**选项；然后使用 ALTER DATABASE 语句启用需要此功能的各个数据库的跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="91496-115">If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91496-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91496-116">See Also</span></span>  
 <span data-ttu-id="91496-117">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91496-117">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="91496-118">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91496-118">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="91496-119">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91496-119">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="91496-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91496-120">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="91496-121">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="91496-121">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
