---
title: 更改服务器身份验证模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8bda31ca7d0c5949173a9a3e5ea656c1757c04f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693097"
---
# <a name="change-server-authentication-mode"></a><span data-ttu-id="5bb07-102">更改服务器身份验证模式</span><span class="sxs-lookup"><span data-stu-id="5bb07-102">Change Server Authentication Mode</span></span>
  <span data-ttu-id="5bb07-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中更改服务器身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="5bb07-103">This topic describes how to change the server authentication mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5bb07-104">安装过程中， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 设置为 **“Windows 身份验证模式”** 或 **“SQL Server 和 Windows 身份验证模式”** 。</span><span class="sxs-lookup"><span data-stu-id="5bb07-104">During installation, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] is set to either **Windows Authentication mode** or **SQL Server and Windows Authentication mode**.</span></span> <span data-ttu-id="5bb07-105">安装完成后，您可以随时更改身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="5bb07-105">After installation, you can change the authentication mode at any time.</span></span>  
  
 <span data-ttu-id="5bb07-106">如果在安装过程中选择了“Windows 身份验证模式”，则 sa 登录名将被禁用，安装程序会分配一个密码。</span><span class="sxs-lookup"><span data-stu-id="5bb07-106">If **Windows Authentication mode** is selected during installation, the sa login is disabled and a password is assigned by setup.</span></span> <span data-ttu-id="5bb07-107">如果稍后将身份验证模式更改为“SQL Server 和 Windows 身份验证模式”，则 sa 登录名仍处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="5bb07-107">If you later change authentication mode to **SQL Server and Windows Authentication mode**, the sa login remains disabled.</span></span> <span data-ttu-id="5bb07-108">若要使用 sa 登录名，请使用 ALTER LOGIN 语句启用 sa 登录名并分配一个新密码。</span><span class="sxs-lookup"><span data-stu-id="5bb07-108">To use the sa login, use the ALTER LOGIN statement to enable the sa login and assign a new password.</span></span> <span data-ttu-id="5bb07-109">sa 登录名只能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="5bb07-109">The sa login can only connect to the server by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="5bb07-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="5bb07-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5bb07-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="5bb07-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5bb07-112">安全性</span><span class="sxs-lookup"><span data-stu-id="5bb07-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5bb07-113">**若要更改服务器身份验证模式，请使用：**</span><span class="sxs-lookup"><span data-stu-id="5bb07-113">**To change server authentication mode, using:**</span></span>  
  
     [<span data-ttu-id="5bb07-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5bb07-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5bb07-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5bb07-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5bb07-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="5bb07-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5bb07-117">Security</span><span class="sxs-lookup"><span data-stu-id="5bb07-117">Security</span></span>  
 <span data-ttu-id="5bb07-118">sa 帐户是一个广为人知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，并且经常成为恶意用户的攻击目标。</span><span class="sxs-lookup"><span data-stu-id="5bb07-118">The sa account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="5bb07-119">除非您的应用程序需要使用 sa 帐户，否则请不要启用它。</span><span class="sxs-lookup"><span data-stu-id="5bb07-119">Do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="5bb07-120">为 sa 登录名使用一个强密码非常重要。</span><span class="sxs-lookup"><span data-stu-id="5bb07-120">It is very important that you use a strong password for the sa login.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5bb07-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5bb07-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-security-authentication-mode"></a><span data-ttu-id="5bb07-122">更改安全身份验证模式</span><span class="sxs-lookup"><span data-stu-id="5bb07-122">To change security authentication mode</span></span>  
  
1.  <span data-ttu-id="5bb07-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中，右键单击服务器，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="5bb07-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click the server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5bb07-124">在 **“安全性”** 页上的 **“服务器身份验证”** 下，选择新的服务器身份验证模式，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="5bb07-124">On the **Security** page, under **Server authentication**, select the new server authentication mode, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5bb07-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对话框中，单击 **“确定”** 以确认需要重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5bb07-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialog box, click **OK** to acknowledge the requirement to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="5bb07-126">在“对象资源管理器”中，右键单击服务器，并单击“重新启动”。</span><span class="sxs-lookup"><span data-stu-id="5bb07-126">In Object Explorer, right-click your server, and then click **Restart**.</span></span> <span data-ttu-id="5bb07-127">如果运行有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，则也必须重新启动该代理。</span><span class="sxs-lookup"><span data-stu-id="5bb07-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, it must also be restarted.</span></span>  
  
#### <a name="to-enable-the-sa-login"></a><span data-ttu-id="5bb07-128">启用 sa 登录名</span><span class="sxs-lookup"><span data-stu-id="5bb07-128">To enable the sa login</span></span>  
  
1.  <span data-ttu-id="5bb07-129">在对象资源管理器中，展开 "**安全性**"，展开 "登录名"，右键单击 `sa` ，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="5bb07-129">In Object Explorer, expand **Security**, expand Logins, right-click `sa`, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5bb07-130">在 **“常规”** 页上，您可能需要为登录名创建密码并确认该密码。</span><span class="sxs-lookup"><span data-stu-id="5bb07-130">On the **General** page, you might have to create and confirm a password for the  login.</span></span>  
  
3.  <span data-ttu-id="5bb07-131">在 **“状态”** 页上的 **“登录”** 部分，单击 **“启用”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="5bb07-131">On the **Status** page, in the **Login** section, click **Enabled**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5bb07-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5bb07-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="5bb07-133">**启用 sa 登录名**</span><span class="sxs-lookup"><span data-stu-id="5bb07-133">**To enable the sa login**</span></span>  
  
1.  <span data-ttu-id="5bb07-134">在“对象资源管理器”中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="5bb07-134">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5bb07-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="5bb07-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5bb07-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="5bb07-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5bb07-137">下面的示例启用 sa 登录名并设置一个新密码。</span><span class="sxs-lookup"><span data-stu-id="5bb07-137">The following example enables the sa login and sets a new password.</span></span>  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5bb07-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5bb07-138">See Also</span></span>  
 <span data-ttu-id="5bb07-139">[强密码](../../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="5bb07-139">[Strong Passwords](../../relational-databases/security/strong-passwords.md) </span></span>  
 <span data-ttu-id="5bb07-140">[SQL Server 安装的安全注意事项](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="5bb07-140">[Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="5bb07-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5bb07-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 [<span data-ttu-id="5bb07-142">在系统管理员被锁定时连接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="5bb07-142">Connect to SQL Server When System Administrators Are Locked Out</span></span>](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
