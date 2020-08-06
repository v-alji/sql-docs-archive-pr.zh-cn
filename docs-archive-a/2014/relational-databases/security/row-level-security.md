---
title: 行级安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- row level security described
- row level security
- access control predicates
- security [SQL Server], predicate based access control
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c67f84723e79b66d0454fb509f2fa9ced03dac7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688746"
---
# <a name="row-level-security"></a><span data-ttu-id="3e1f7-102">行级安全性</span><span class="sxs-lookup"><span data-stu-id="3e1f7-102">Row-Level Security</span></span>
  <span data-ttu-id="3e1f7-103">行级别安全性使客户能够根据执行查询的用户的特征（例如，组成员身份或执行上下文），控制对数据库表中的行的访问。</span><span class="sxs-lookup"><span data-stu-id="3e1f7-103">Row-Level Security enables customers to control access to rows in a database table based on the characteristics of the user executing a query (e.g., group membership or execution context).</span></span> <span data-ttu-id="3e1f7-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 中现在提供行级别安全性。</span><span class="sxs-lookup"><span data-stu-id="3e1f7-104">Row-Level Security is now available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016.</span></span> <span data-ttu-id="3e1f7-105">有关此功能的当前描述，请参阅当前文档中的 [行级别安全性](https://msdn.microsoft.com/library/dn765131.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="3e1f7-105">See [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) in the current documentation for the current description of this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e1f7-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e1f7-106">See Also</span></span>  
 <span data-ttu-id="3e1f7-107">[&#40;Azure SQL 数据库创建安全策略&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-107">[CREATE SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="3e1f7-108">[&#40;Azure SQL 数据库&#41;更改安全策略](/sql/t-sql/statements/alter-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-108">[ALTER SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="3e1f7-109">[&#40;Azure SQL 数据库中删除安全策略&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-109">[DROP SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="3e1f7-110">[CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 <span data-ttu-id="3e1f7-111">[security_policies &#40;Azure SQL 数据库&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-111">[sys.security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span></span>  
 <span data-ttu-id="3e1f7-112">[security_predicates &#40;Azure SQL 数据库&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3e1f7-112">[sys.security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span></span>  
 [<span data-ttu-id="3e1f7-113">创建用户定义函数（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="3e1f7-113">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  
