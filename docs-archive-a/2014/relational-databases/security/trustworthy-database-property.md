---
title: TRUSTWORTHY 数据库属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23391fe48037d4cd7f69aef7df6649949301a0f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688699"
---
# <a name="trustworthy-database-property"></a><span data-ttu-id="6d208-102">TRUSTWORTHY 数据库属性</span><span class="sxs-lookup"><span data-stu-id="6d208-102">TRUSTWORTHY Database Property</span></span>
  <span data-ttu-id="6d208-103">TRUSTWORTHY 数据库属性用于指明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例是否信任该数据库以及其中的内容。</span><span class="sxs-lookup"><span data-stu-id="6d208-103">The TRUSTWORTHY database property is used to indicate whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the database and the contents within it.</span></span> <span data-ttu-id="6d208-104">默认情况下，此设置为 OFF，但是可以使用 ALTER DATABASE 语句将其设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="6d208-104">By default, this setting is OFF, but can be set to ON by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="6d208-105">例如，`ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`。</span><span class="sxs-lookup"><span data-stu-id="6d208-105">For example, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d208-106">必须是 **sysadmin** 固定服务器角色的成员才能设置此选项。</span><span class="sxs-lookup"><span data-stu-id="6d208-106">To set this option, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="6d208-107">此属性可用于减少附加数据库所带来的某些隐患，该数据库包含下列对象之一：</span><span class="sxs-lookup"><span data-stu-id="6d208-107">This property can be used to reduce certain threats that can exist as a result of attaching a database that contains one of the following objects:</span></span>  
  
-   <span data-ttu-id="6d208-108">带有 EXTERNAL_ACCESS 或 UNSAFE 权限设置的有害程序集。</span><span class="sxs-lookup"><span data-stu-id="6d208-108">Malicious assemblies with an EXTERNAL_ACCESS or UNSAFE permission setting.</span></span> <span data-ttu-id="6d208-109">有关详细信息，请参阅 [CLR Integration Security](../clr-integration/security/clr-integration-security.md)。</span><span class="sxs-lookup"><span data-stu-id="6d208-109">For more information, see [CLR Integration Security](../clr-integration/security/clr-integration-security.md).</span></span>  
  
-   <span data-ttu-id="6d208-110">所定义的、作为高特权用户执行的有害模块。</span><span class="sxs-lookup"><span data-stu-id="6d208-110">Malicious modules that are defined to execute as high privileged users.</span></span> <span data-ttu-id="6d208-111">有关详细信息，请参阅 [EXECUTE AS 子句 (Transact-SQL)](/sql/t-sql/statements/execute-as-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6d208-111">For more information, see [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="6d208-112">这两种情况均要求具有特定程度的权限，并且在已附加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的数据库的上下文中使用这两种情况时，应采取相应的机制保护这两种情况。</span><span class="sxs-lookup"><span data-stu-id="6d208-112">Both of these situations require a specific degree of privileges and are protected against by appropriate mechanisms when they are used in the context of a database that is already attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6d208-113">但是，如果数据库脱机，则对数据库文件具有访问权限的用户可能会将其附加到其选择的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，并将有害内容添加到数据库中。</span><span class="sxs-lookup"><span data-stu-id="6d208-113">However, if the database is taken offline, a user that has access to the database file can potentially attach it to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of his or her choice and add malicious content to the database.</span></span> <span data-ttu-id="6d208-114">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中分离和附加数据库时，将对限制访问数据库文件的数据和日志文件设置某些权限。</span><span class="sxs-lookup"><span data-stu-id="6d208-114">When databases are detached and attached in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certain permissions are set on the data and log files that restrict access to the database files.</span></span>  
  
 <span data-ttu-id="6d208-115">因为无法立即信任附加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的数据库，所以不允许数据库访问超出数据库范围的资源，直到数据库已显式标记为可信。</span><span class="sxs-lookup"><span data-stu-id="6d208-115">Because a database that is attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be immediately trusted, the database is not allowed to access resources beyond the scope of the database until the database is explicitly marked trustworthy.</span></span> <span data-ttu-id="6d208-116">此外，旨在访问数据库以外资源的模块和带有 EXTERNAL_ACCESS 或 UNSAFE 权限设置的程序集还需要其他条件才能成功运行。</span><span class="sxs-lookup"><span data-stu-id="6d208-116">Also, modules that are designed to access resources outside the database, and assemblies with either the EXTERNAL_ACCESS and UNSAFE permission setting, have additional requirements in order to run successfully.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="6d208-117">相关内容</span><span class="sxs-lookup"><span data-stu-id="6d208-117">Related Content</span></span>  
 [<span data-ttu-id="6d208-118">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="6d208-118">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="6d208-119">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6d208-119">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
