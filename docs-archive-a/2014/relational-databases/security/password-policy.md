---
title: 密码策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 902c46b4609a32139450843414a3c4d97b52fcf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578752"
---
# <a name="password-policy"></a><span data-ttu-id="45ae4-102">密码策略</span><span class="sxs-lookup"><span data-stu-id="45ae4-102">Password Policy</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="45ae4-103">可以使用 Windows 密码策略机制。</span><span class="sxs-lookup"><span data-stu-id="45ae4-103">can use Windows password policy mechanisms.</span></span> <span data-ttu-id="45ae4-104">密码策略应用于使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的登录名，并且应用于具有密码的包含数据库用户。</span><span class="sxs-lookup"><span data-stu-id="45ae4-104">The password policy applies to a login that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, and to a contained database user with password.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="45ae4-105">可以对在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部使用的密码应用在 Windows 中使用的相同复杂性策略和过期策略。</span><span class="sxs-lookup"><span data-stu-id="45ae4-105">can apply the same complexity and expiration policies used in Windows to passwords used inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="45ae4-106">此功能取决于 `NetValidatePasswordPolicy` API。</span><span class="sxs-lookup"><span data-stu-id="45ae4-106">This functionality depends on the `NetValidatePasswordPolicy` API.</span></span>  
  
## <a name="password-complexity"></a><span data-ttu-id="45ae4-107">密码复杂性</span><span class="sxs-lookup"><span data-stu-id="45ae4-107">Password Complexity</span></span>  
 <span data-ttu-id="45ae4-108">密码复杂性策略通过增加可能密码的数量来阻止强力攻击。</span><span class="sxs-lookup"><span data-stu-id="45ae4-108">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="45ae4-109">实施密码复杂性策略时，新密码必须符合以下原则：</span><span class="sxs-lookup"><span data-stu-id="45ae4-109">When password complexity policy is enforced, new passwords must meet the following guidelines:</span></span>  
  
-   <span data-ttu-id="45ae4-110">密码不得包含用户的帐户名。</span><span class="sxs-lookup"><span data-stu-id="45ae4-110">The password does not contain the account name of the user.</span></span>  
  
-   <span data-ttu-id="45ae4-111">密码长度至少为八个字符。</span><span class="sxs-lookup"><span data-stu-id="45ae4-111">The password is at least eight characters long.</span></span>  
  
-   <span data-ttu-id="45ae4-112">密码包含以下四类字符中的三类：</span><span class="sxs-lookup"><span data-stu-id="45ae4-112">The password contains characters from three of the following four categories:</span></span>  
  
    -   <span data-ttu-id="45ae4-113">拉丁文大写字母 (A - Z)</span><span class="sxs-lookup"><span data-stu-id="45ae4-113">Latin uppercase letters (A through Z)</span></span>  
  
    -   <span data-ttu-id="45ae4-114">拉丁文小写字母 (a - z)</span><span class="sxs-lookup"><span data-stu-id="45ae4-114">Latin lowercase letters (a through z)</span></span>  
  
    -   <span data-ttu-id="45ae4-115">10 个基本数字 (0 - 9)</span><span class="sxs-lookup"><span data-stu-id="45ae4-115">Base 10 digits (0 through 9)</span></span>  
  
    -   <span data-ttu-id="45ae4-116">非字母数字字符，如感叹号 (!)、美元符号 ($)、数字符号 (#) 或百分号 (%)。</span><span class="sxs-lookup"><span data-stu-id="45ae4-116">Non-alphanumeric characters such as: exclamation point (!), dollar sign ($), number sign (#), or percent (%).</span></span>  
  
 <span data-ttu-id="45ae4-117">密码可最长为 128 个字符。</span><span class="sxs-lookup"><span data-stu-id="45ae4-117">Passwords can be up to 128 characters long.</span></span> <span data-ttu-id="45ae4-118">使用的密码应尽可能长，尽可能复杂。</span><span class="sxs-lookup"><span data-stu-id="45ae4-118">You should use passwords that are as long and complex as possible.</span></span>  
  
## <a name="password-expiration"></a><span data-ttu-id="45ae4-119">密码过期</span><span class="sxs-lookup"><span data-stu-id="45ae4-119">Password Expiration</span></span>  
 <span data-ttu-id="45ae4-120">密码过期策略用于管理密码的使用期限。</span><span class="sxs-lookup"><span data-stu-id="45ae4-120">Password expiration policies are used to manage the lifespan of a password.</span></span> <span data-ttu-id="45ae4-121">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实施密码过期策略，则系统将提醒用户更改旧密码，并禁用带有过期密码的帐户。</span><span class="sxs-lookup"><span data-stu-id="45ae4-121">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enforces password expiration policy, users are reminded to change old passwords, and accounts that have expired passwords are disabled.</span></span>  
  
## <a name="policy-enforcement"></a><span data-ttu-id="45ae4-122">策略实施</span><span class="sxs-lookup"><span data-stu-id="45ae4-122">Policy Enforcement</span></span>  
 <span data-ttu-id="45ae4-123">可为每个 SQL Server 登录名单独配置密码策略实施。</span><span class="sxs-lookup"><span data-stu-id="45ae4-123">The enforcement of password policy can be configured separately for each SQL Server login.</span></span> <span data-ttu-id="45ae4-124">使用 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) 来配置 SQL Server 登录名的密码策略选项。</span><span class="sxs-lookup"><span data-stu-id="45ae4-124">Use [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy options of a SQL Server login.</span></span> <span data-ttu-id="45ae4-125">配置密码策略实施时，适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="45ae4-125">The following rules apply to the configuration of password policy enforcement:</span></span>  
  
-   <span data-ttu-id="45ae4-126">如果 CHECK_POLICY 改为 ON，则将出现以下行为：</span><span class="sxs-lookup"><span data-stu-id="45ae4-126">When CHECK_POLICY is changed to ON, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="45ae4-127">除非将 CHECK_EXPIRATION 显式设置为 OFF，否则也会将其设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="45ae4-127">CHECK_EXPIRATION is also set to ON unless it is explicitly set to OFF.</span></span>  
  
    -   <span data-ttu-id="45ae4-128">用当前的密码哈希值初始化密码历史记录。</span><span class="sxs-lookup"><span data-stu-id="45ae4-128">The password history is initialized with the value of the current password hash.</span></span>  
  
    -   <span data-ttu-id="45ae4-129">还将启用**帐户锁定时间**, **帐户锁定阈值**和 **在此后重置帐户锁定计数器** 。</span><span class="sxs-lookup"><span data-stu-id="45ae4-129">**Account lockout duration**, **account lockout threshold**, and **reset account lockout counter after** are also enabled.</span></span>  
  
-   <span data-ttu-id="45ae4-130">如果 CHECK_POLICY 改为 OFF，则将出现以下行为：</span><span class="sxs-lookup"><span data-stu-id="45ae4-130">When CHECK_POLICY is changed to OFF, the following behaviors occur:</span></span>  
  
    -   <span data-ttu-id="45ae4-131">CHECK_EXPIRATION 也设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="45ae4-131">CHECK_EXPIRATION is also set to OFF.</span></span>  
  
    -   <span data-ttu-id="45ae4-132">清除密码历史记录。</span><span class="sxs-lookup"><span data-stu-id="45ae4-132">The password history is cleared.</span></span>  
  
    -   <span data-ttu-id="45ae4-133">`lockout_time` 的值被重置。</span><span class="sxs-lookup"><span data-stu-id="45ae4-133">The value of `lockout_time` is reset.</span></span>  
  
 <span data-ttu-id="45ae4-134">不支持策略选项的某些组合。</span><span class="sxs-lookup"><span data-stu-id="45ae4-134">Some combinations of policy options are not supported.</span></span>  
  
-   <span data-ttu-id="45ae4-135">如果指定 MUST_CHANGE，则 CHECK_EXPIRATION 和 CHECK_POLICY 必须设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="45ae4-135">If MUST_CHANGE is specified, CHECK_EXPIRATION and CHECK_POLICY must be set to ON.</span></span> <span data-ttu-id="45ae4-136">否则，该语句将失败。</span><span class="sxs-lookup"><span data-stu-id="45ae4-136">Otherwise, the statement will fail.</span></span>  
  
-   <span data-ttu-id="45ae4-137">如果 CHECK_POLICY 设置为 OFF，则 CHECK_EXPIRATION 不能设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="45ae4-137">If CHECK_POLICY is set to OFF, CHECK_EXPIRATION cannot be set to ON.</span></span> <span data-ttu-id="45ae4-138">包含此选项组合的 ALTER LOGIN 语句将失败。</span><span class="sxs-lookup"><span data-stu-id="45ae4-138">An ALTER LOGIN statement that has this combination of options will fail.</span></span>  
  
 <span data-ttu-id="45ae4-139">设置 CHECK_POLICY = ON 将禁止创建以下类型的密码：</span><span class="sxs-lookup"><span data-stu-id="45ae4-139">Setting CHECK_POLICY = ON will prevent the creation of passwords that are:</span></span>  
  
-   <span data-ttu-id="45ae4-140">为 NULL 或空</span><span class="sxs-lookup"><span data-stu-id="45ae4-140">Null or empty</span></span>  
  
-   <span data-ttu-id="45ae4-141">与计算机名或登录名相同</span><span class="sxs-lookup"><span data-stu-id="45ae4-141">Same as name of computer or login</span></span>  
  
-   <span data-ttu-id="45ae4-142">下列任意项：“password”、“admin”、“administrator”、“sa”、“sysadmin”</span><span class="sxs-lookup"><span data-stu-id="45ae4-142">Any of the following: "password", "admin", "administrator", "sa", "sysadmin"</span></span>  
  
 <span data-ttu-id="45ae4-143">可以在 Windows 中设置安全策略，也可以从域接收安全策略。</span><span class="sxs-lookup"><span data-stu-id="45ae4-143">The security policy might be set in Windows, or might be received from the domain.</span></span> <span data-ttu-id="45ae4-144">若要查看计算机上的密码策略，请使用本地安全策略 MMC 管理单元 (**secpol.msc**)。</span><span class="sxs-lookup"><span data-stu-id="45ae4-144">To view the password policy on the computer, use the Local Security Policy MMC snap-in (**secpol.msc**).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="45ae4-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="45ae4-145">Related Tasks</span></span>  
 [<span data-ttu-id="45ae4-146">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45ae4-146">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
 [<span data-ttu-id="45ae4-147">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="45ae4-147">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [<span data-ttu-id="45ae4-148">CREATE USER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="45ae4-148">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
 [<span data-ttu-id="45ae4-149">ALTER USER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="45ae4-149">ALTER USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [<span data-ttu-id="45ae4-150">创建登录名</span><span class="sxs-lookup"><span data-stu-id="45ae4-150">Create a Login</span></span>](authentication-access/create-a-login.md)  
  
 [<span data-ttu-id="45ae4-151">创建数据库用户</span><span class="sxs-lookup"><span data-stu-id="45ae4-151">Create a Database User</span></span>](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a><span data-ttu-id="45ae4-152">相关内容</span><span class="sxs-lookup"><span data-stu-id="45ae4-152">Related Content</span></span>  
 [<span data-ttu-id="45ae4-153">强密码</span><span class="sxs-lookup"><span data-stu-id="45ae4-153">Strong Passwords</span></span>](strong-passwords.md)  
  
  
