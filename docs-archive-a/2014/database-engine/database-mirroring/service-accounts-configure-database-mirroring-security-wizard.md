---
title: 服务帐户（配置数据库镜像安全向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58e49467a28e816c6592b1ded212b5aea0e6bc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690101"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a><span data-ttu-id="b6306-102">服务帐户（配置数据库镜像安全向导）</span><span class="sxs-lookup"><span data-stu-id="b6306-102">Service Accounts (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="b6306-103">使用 Windows 身份验证时，如果服务器实例使用若干个不同的帐户，请为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b6306-103">When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b6306-104">这些服务帐户必须都是域帐户（在相同域或可信域中）。</span><span class="sxs-lookup"><span data-stu-id="b6306-104">These service accounts must all be domain accounts (in the same or trusted domains).</span></span>  
  
 <span data-ttu-id="b6306-105">如果所有服务器实例都使用同一域帐户或使用基于证书的身份验证，则请将这些字段留空。</span><span class="sxs-lookup"><span data-stu-id="b6306-105">If all the server instances use the same domain account or use certificate-based authentication, leave the fields blank.</span></span> <span data-ttu-id="b6306-106">只需单击 **“完成”**，向导将根据当前向导的帐户自动配置帐户。</span><span class="sxs-lookup"><span data-stu-id="b6306-106">Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b6306-107">如果将服务器实例的数据库镜像端点配置为使用证书，您必须将服务帐户字段保留为空。</span><span class="sxs-lookup"><span data-stu-id="b6306-107">If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.</span></span>  
  
 <span data-ttu-id="b6306-108">**使用 SQL Server Management Studio 配置数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="b6306-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="b6306-109">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b6306-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="b6306-110">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="b6306-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="b6306-111">选项</span><span class="sxs-lookup"><span data-stu-id="b6306-111">Options</span></span>  
 <span data-ttu-id="b6306-112">**主体**</span><span class="sxs-lookup"><span data-stu-id="b6306-112">**Principal**</span></span>  
 <span data-ttu-id="b6306-113">指定主体服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b6306-113">Specify the service account of the principal server instance.</span></span> <span data-ttu-id="b6306-114">以大写形式输入域名：</span><span class="sxs-lookup"><span data-stu-id="b6306-114">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="b6306-115">*DOMAINNAME* \\*用户名*</span><span class="sxs-lookup"><span data-stu-id="b6306-115">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="b6306-116">**镜像**</span><span class="sxs-lookup"><span data-stu-id="b6306-116">**Mirror**</span></span>  
 <span data-ttu-id="b6306-117">指定镜像服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b6306-117">Specify the service account of the mirror server instance.</span></span> <span data-ttu-id="b6306-118">以大写形式输入域名：</span><span class="sxs-lookup"><span data-stu-id="b6306-118">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="b6306-119">*DOMAINNAME* \\*用户名*</span><span class="sxs-lookup"><span data-stu-id="b6306-119">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="b6306-120">**见证**</span><span class="sxs-lookup"><span data-stu-id="b6306-120">**Witness**</span></span>  
 <span data-ttu-id="b6306-121">指定见证服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="b6306-121">Specify the service account of the witness server instance.</span></span> <span data-ttu-id="b6306-122">以大写形式输入域名：</span><span class="sxs-lookup"><span data-stu-id="b6306-122">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="b6306-123">*DOMAINNAME* \\*用户名*</span><span class="sxs-lookup"><span data-stu-id="b6306-123">*DOMAINNAME*\\*username*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6306-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6306-124">See Also</span></span>  
 <span data-ttu-id="b6306-125">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="b6306-125">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="b6306-126">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="b6306-126">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="b6306-127">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6306-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="b6306-128">设置用于数据库镜像或 AlwaysOn 可用性组 &#40;SQL Server 的登录帐户&#41;</span><span class="sxs-lookup"><span data-stu-id="b6306-128">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
