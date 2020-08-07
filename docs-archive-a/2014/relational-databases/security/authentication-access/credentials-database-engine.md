---
title: 凭据（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: faa2b5be7cf6918b5d5232763a96ed4dbbc89e51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589476"
---
# <a name="credentials-database-engine"></a><span data-ttu-id="31046-102">凭据（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="31046-102">Credentials (Database Engine)</span></span>
  <span data-ttu-id="31046-103">凭据是包含连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部资源所需的身份验证信息（凭据）的记录。</span><span class="sxs-lookup"><span data-stu-id="31046-103">A credential is a record that contains the authentication information (credentials) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31046-104">此信息由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]在内部使用。</span><span class="sxs-lookup"><span data-stu-id="31046-104">This information is used internally by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31046-105">大多凭据都包含一个 Windows 用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="31046-105">Most credentials contain a Windows user name and password.</span></span>  
  
 <span data-ttu-id="31046-106">利用凭据中存储的信息，通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证方式连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的用户可以访问服务器实例外部的资源。</span><span class="sxs-lookup"><span data-stu-id="31046-106">The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by way of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to access resources outside the server instance.</span></span> <span data-ttu-id="31046-107">如果外部资源为 Windows，则此用户将作为在凭据中指定的 Windows 用户通过身份验证。</span><span class="sxs-lookup"><span data-stu-id="31046-107">When the external resource is Windows, the user is authenticated as the Windows user specified in the credential.</span></span> <span data-ttu-id="31046-108">单个凭据可映射到多个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="31046-108">A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="31046-109">但是，一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名只能映射到一个凭据。</span><span class="sxs-lookup"><span data-stu-id="31046-109">However, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can be mapped to only one credential.</span></span>  
  
 <span data-ttu-id="31046-110">系统凭据是自动创建的，并与特定端点关联，</span><span class="sxs-lookup"><span data-stu-id="31046-110">System credentials are created automatically and are associated with specific endpoints.</span></span> <span data-ttu-id="31046-111">系统凭据名以两个哈希符号 (##) 开头。</span><span class="sxs-lookup"><span data-stu-id="31046-111">Names for system credentials start with two hash signs (##).</span></span>  
  
 <span data-ttu-id="31046-112">有关凭据的详细信息，请参阅[sys.databases](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)目录视图。</span><span class="sxs-lookup"><span data-stu-id="31046-112">For more information about credentials, see the [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) catalog view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="31046-113">相关内容</span><span class="sxs-lookup"><span data-stu-id="31046-113">Related Content</span></span>  
 <span data-ttu-id="31046-114">&#40;Transact-sql[创建凭据](../authentication-access/create-a-credential.md)[创建凭据&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="31046-114">[Create a Credential](../authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span></span>  
  
 [<span data-ttu-id="31046-115">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="31046-115">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
