---
title: 标识和访问控制（复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0ae16d0908efa211a773b278fc8e86b1bf1966d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689858"
---
# <a name="identity-and-access-control-replication"></a><span data-ttu-id="a9c20-102">标识和访问控制（复制）</span><span class="sxs-lookup"><span data-stu-id="a9c20-102">Identity and Access Control (Replication)</span></span>
  <span data-ttu-id="a9c20-103">身份验证是指一个实体（在此上下文中通常是计算机）验证另一实体（也称“主体”  ，通常是另一计算机或用户）是否与其自称的身份相符的过程。</span><span class="sxs-lookup"><span data-stu-id="a9c20-103">Authentication is the process by which an entity (typically a computer in this context) verifies that another entity, also called a *principal*, (typically another computer or user) is who or what it claims to be.</span></span> <span data-ttu-id="a9c20-104">授权是给予通过身份验证的主体对资源（例如，文件系统中的文件或数据库中的表）的访问权限的过程。</span><span class="sxs-lookup"><span data-stu-id="a9c20-104">Authorization is the process by which an authenticated principal is given access to resources, such as a file in the file system, or a table in a database.</span></span>  
  
 <span data-ttu-id="a9c20-105">复制安全性使用身份验证和授权，来控制对复制数据库对象和涉及复制处理的计算机及代理的访问。</span><span class="sxs-lookup"><span data-stu-id="a9c20-105">Replication security uses authentication and authorization to control access to replicated database objects and to the computers and agents involved in replication processing.</span></span> <span data-ttu-id="a9c20-106">这是通过三种机制实现的：</span><span class="sxs-lookup"><span data-stu-id="a9c20-106">This is accomplished through three mechanisms:</span></span>  
  
-   <span data-ttu-id="a9c20-107">代理安全性：通过复制代理安全模式，可以对运行复制代理和建立连接所用的帐户进行精细的控制。</span><span class="sxs-lookup"><span data-stu-id="a9c20-107">Agent security:  The replication agent security model allows fine-grained control over the accounts under which replication agents run and make connections.</span></span> <span data-ttu-id="a9c20-108">有关代理安全模式的详细信息，请参阅 [Replication Agent Security Model](replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-108">For detailed information about the agent security model, see [Replication Agent Security Model](replication-agent-security-model.md).</span></span> <span data-ttu-id="a9c20-109">有关为代理设置登录名和密码的信息，请参阅[管理复制中的登录名和密码](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-109">For information about setting logins and passwords for agents, see [Manage Logins and Passwords in Replication](identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication).</span></span>  
  
-   <span data-ttu-id="a9c20-110">管理角色：确保使用正确的服务器和数据库角色进行复制设置、维护和处理。</span><span class="sxs-lookup"><span data-stu-id="a9c20-110">Administration roles:  Ensure that the correct server and database roles are used for replication setup, maintenance, and processing.</span></span> <span data-ttu-id="a9c20-111">有关详细信息，请参阅 [Security Role Requirements for Replication](security-role-requirements-for-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-111">For more information, see [Security Role Requirements for Replication](security-role-requirements-for-replication.md).</span></span>  
  
-   <span data-ttu-id="a9c20-112">发布访问列表 (PAL) ：通过 PAL 授予对发布的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a9c20-112">The publication access list (PAL): Grant access to publications through the PAL.</span></span> <span data-ttu-id="a9c20-113">PAL 的功能与 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 的访问控制列表相似。</span><span class="sxs-lookup"><span data-stu-id="a9c20-113">The PAL functions similarly to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows access control list.</span></span> <span data-ttu-id="a9c20-114">当有订阅服务器连接到发布服务器或分发服务器并请求访问发布时，将对照 PAL 检查代理传递的身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="a9c20-114">When a Subscriber connects to the Publisher or Distributor and requests access to a publication, the authentication information passed by the agent is checked against the PAL.</span></span> <span data-ttu-id="a9c20-115">有关 PAL 的详细信息和最佳做法，请参阅[保护发布服务器](secure-the-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-115">For more information and best practices for the PAL, see [Secure the Publisher](secure-the-publisher.md).</span></span>  
  
## <a name="filtering-published-data"></a><span data-ttu-id="a9c20-116">筛选已发布数据</span><span class="sxs-lookup"><span data-stu-id="a9c20-116">Filtering Published Data</span></span>  
 <span data-ttu-id="a9c20-117">除了使用身份验证和授权来控制对被复制的数据和对象的访问之外，复制还包含两个选项，用来控制订阅服务器上哪些数据可用：列筛选和行筛选。</span><span class="sxs-lookup"><span data-stu-id="a9c20-117">In addition to using authentication and authorization to control access to replicated data and objects, replication includes two options to control what data is available at a Subscriber: column filtering and row filtering.</span></span> <span data-ttu-id="a9c20-118">有关筛选的详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-118">For more information about filtering, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
 <span data-ttu-id="a9c20-119">定义项目时，可以只发布那些发布所必需的列，而省略那些不必要或包含敏感数据的行。</span><span class="sxs-lookup"><span data-stu-id="a9c20-119">When you define an article, you can publish only those columns that are necessary for the publication, and omit those that are unnecessary or contain sensitive data.</span></span> <span data-ttu-id="a9c20-120">例如，从 Adventure Works 数据库向现场销售代表发布 **Customer** 表时，可以省略 **AnnualSales** 列，该列可能仅与公司的高层管理者有关。</span><span class="sxs-lookup"><span data-stu-id="a9c20-120">For example, when publishing the **Customer** table from the Adventure Works database to sales representatives in the field, you can omit the **AnnualSales** column, which might be relevant only to executives at the company.</span></span>  
  
 <span data-ttu-id="a9c20-121">通过筛选已发布数据，可以限制对数据的访问，并可指定订阅服务器上的可用数据。</span><span class="sxs-lookup"><span data-stu-id="a9c20-121">Filtering published data allows you to restrict access to data and allows you to specify the data that is available at the Subscriber.</span></span> <span data-ttu-id="a9c20-122">例如，可以筛选 **Customer** 表，以使公司合作伙伴们只收到其 **ShareInfo** 列的值为“yes”的客户的信息。</span><span class="sxs-lookup"><span data-stu-id="a9c20-122">For example, you can filter the **Customer** table so that corporate partners only receive information about those customers whose **ShareInfo** column has a value of "yes."</span></span> <span data-ttu-id="a9c20-123">对于合并复制，如果使用包括 HOST_NAME() 的参数化筛选器，则需要考虑安全问题。</span><span class="sxs-lookup"><span data-stu-id="a9c20-123">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="a9c20-124">有关详细信息，请参阅 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)中“使用 HOST_NAME() 筛选”部分。</span><span class="sxs-lookup"><span data-stu-id="a9c20-124">For more, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  

## <a name="manage-logins-and-passwords-in-replication"></a><span data-ttu-id="a9c20-125">管理复制中的登录名和密码</span><span class="sxs-lookup"><span data-stu-id="a9c20-125">Manage Logins and Passwords in Replication</span></span>
  <span data-ttu-id="a9c20-126">在配置复制时，为复制代理指定登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="a9c20-126">Specify the logins and passwords for replication agents when you configure replication.</span></span> <span data-ttu-id="a9c20-127">配置复制后，可以更改登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="a9c20-127">After configuring replication, you can change logins and passwords.</span></span> <span data-ttu-id="a9c20-128">有关详细信息，请参阅 [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-128">For more information, see [View and Modify Replication Security Settings](view-and-modify-replication-security-settings.md).</span></span> <span data-ttu-id="a9c20-129">若要更改复制代理所使用的帐户的密码，请执行 [sp_changereplicationserverpasswords (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a9c20-129">If you change the password for an account used by a replication agent, execute [sp_changereplicationserverpasswords &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c20-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9c20-130">See Also</span></span>  
 <span data-ttu-id="a9c20-131">[复制代理安全模式](replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="a9c20-131">[Replication Agent Security Model](replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="a9c20-132">[Replication Security Best Practices](replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="a9c20-132">[Replication Security Best Practices](replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="a9c20-133">[SQL Server 复制安全性](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="a9c20-133">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="a9c20-134">复制威胁和漏洞缓解</span><span class="sxs-lookup"><span data-stu-id="a9c20-134">Replication Threat and Vulnerability Mitigation</span></span>](threat-and-vulnerability-mitigation-replication.md)   

  
  
