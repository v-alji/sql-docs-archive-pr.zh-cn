---
title: 将 SQL Server 审核事件写入安全日志 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], Security Log
- server audit [SQL Server]
- audits [SQL Server], writing to Security Log
- security logs [SQL Server]
ms.assetid: 6fabeea3-7a42-4769-a0f3-7e04daada314
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d59134b278f29c9b604208d8cab7e982144b9c9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578764"
---
# <a name="write-sql-server-audit-events-to-the-security-log"></a><span data-ttu-id="9373b-102">将 SQL Server 审核事件写入安全日志</span><span class="sxs-lookup"><span data-stu-id="9373b-102">Write SQL Server Audit Events to the Security Log</span></span>
  <span data-ttu-id="9373b-103">在高度安全环境中，Windows 安全日志是写入记录对象访问的事件的合适位置。</span><span class="sxs-lookup"><span data-stu-id="9373b-103">In a high security environment, the Windows Security log is the appropriate location to write events that record object access.</span></span> <span data-ttu-id="9373b-104">其他审核位置也受支持，但是更易被篡改。</span><span class="sxs-lookup"><span data-stu-id="9373b-104">Other audit locations are supported but are more subject to tampering.</span></span>  
  
 <span data-ttu-id="9373b-105">将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务器审核写入 Windows 安全日志有两个关键要求：</span><span class="sxs-lookup"><span data-stu-id="9373b-105">There are two key requirements for writing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server audits to the Windows Security log:</span></span>  
  
-   <span data-ttu-id="9373b-106">必须配置审核对象访问设置以捕获事件。</span><span class="sxs-lookup"><span data-stu-id="9373b-106">The audit object access setting must be configured to capture the events.</span></span> <span data-ttu-id="9373b-107">审核策略工具 (`auditpol.exe`) 公开了 **审核对象访问** 类别中的多种子策略设置。</span><span class="sxs-lookup"><span data-stu-id="9373b-107">The audit policy tool (`auditpol.exe`) exposes a variety of sub-policies settings in the **audit object access** category.</span></span> <span data-ttu-id="9373b-108">若要允许 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核对象访问，请配置 **应用程序生成的** 设置。</span><span class="sxs-lookup"><span data-stu-id="9373b-108">To allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to audit object access, configure the **application generated** setting.</span></span>  
  
-   <span data-ttu-id="9373b-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务正在其下运行的帐户必须拥有 **生成安全审核** 权限才能写入 Windows 安全日志。</span><span class="sxs-lookup"><span data-stu-id="9373b-109">The account that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running under must have the **generate security audits** permission to write to the Windows Security log.</span></span> <span data-ttu-id="9373b-110">默认情况下，LOCAL SERVICE 和 NETWORK SERVICE 帐户拥有此权限。</span><span class="sxs-lookup"><span data-stu-id="9373b-110">By default, the LOCAL SERVICE and the NETWORK SERVICE accounts have this permission.</span></span> <span data-ttu-id="9373b-111">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 正在其中一个帐户下运行，则不需要此步骤。</span><span class="sxs-lookup"><span data-stu-id="9373b-111">This step is not required if [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running under one of those accounts.</span></span>  
  
 <span data-ttu-id="9373b-112">将 Windows 审核策略配置为写入 Windows 安全日志时，可能会影响 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核，此时若该审核策略配置不正确，就可能导致事件丢失。</span><span class="sxs-lookup"><span data-stu-id="9373b-112">The Windows audit policy can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auditing if it is configured to write to the Windows Security log, with the potential of losing events if the audit policy is incorrectly configured.</span></span> <span data-ttu-id="9373b-113">通常，将 Windows 安全日志设置为覆盖较旧的事件。</span><span class="sxs-lookup"><span data-stu-id="9373b-113">Typically, the Windows Security log is set to overwrite the older events.</span></span> <span data-ttu-id="9373b-114">这样可保留最新的事件。</span><span class="sxs-lookup"><span data-stu-id="9373b-114">This preserves the most recent events.</span></span> <span data-ttu-id="9373b-115">但如果 Windows 安全日志未设置为覆盖较旧的事件，则当安全日志已满时，系统将发出 Windows 事件 1104（日志已满）。</span><span class="sxs-lookup"><span data-stu-id="9373b-115">However, if the Windows Security log is not set to overwrite older events, then if the Security log is full, the system will issue Windows event 1104 (Log is full).</span></span> <span data-ttu-id="9373b-116">此时：</span><span class="sxs-lookup"><span data-stu-id="9373b-116">At that point:</span></span>  
  
-   <span data-ttu-id="9373b-117">不再记录其他安全事件</span><span class="sxs-lookup"><span data-stu-id="9373b-117">No further security events will be recorded</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9373b-118">将无法检测系统是否能够在安全日志中记录事件，从而导致可能丢失审核事件</span><span class="sxs-lookup"><span data-stu-id="9373b-118">will not be able to detect that the system is not able to record the events in the Security log, resulting in the potential loss of audit events</span></span>  
  
-   <span data-ttu-id="9373b-119">Box 管理员修复安全日志后，日志记录行为将恢复正常。</span><span class="sxs-lookup"><span data-stu-id="9373b-119">After the box administrator fixes the Security log, the logging behavior will return to normal.</span></span>  
  
 <span data-ttu-id="9373b-120">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="9373b-120">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9373b-121">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9373b-121">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9373b-122">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9373b-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9373b-123">安全性</span><span class="sxs-lookup"><span data-stu-id="9373b-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9373b-124">**若要将 SQL Server 审核事件写入安全日志，请使用：**</span><span class="sxs-lookup"><span data-stu-id="9373b-124">**To write SQL Server audit events to the Security Log:**</span></span>  
  
     [<span data-ttu-id="9373b-125">在 Windows 中使用 auditpol 配置审核对象访问设置</span><span class="sxs-lookup"><span data-stu-id="9373b-125">Configure the audit object access setting in Windows using auditpol</span></span>](#auditpolAccess)  
  
     [<span data-ttu-id="9373b-126">在 Windows 中使用 secpol 配置审核对象访问设置</span><span class="sxs-lookup"><span data-stu-id="9373b-126">Configure the audit object access setting in Windows using secpol</span></span>](#secpolAccess)  
  
     [<span data-ttu-id="9373b-127">使用 secpol 将生成安全审核权限授予帐户</span><span class="sxs-lookup"><span data-stu-id="9373b-127">Grant the generate security audits permission to an account using secpol</span></span>](#secpolPermission)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9373b-128">开始之前</span><span class="sxs-lookup"><span data-stu-id="9373b-128">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9373b-129">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9373b-129">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9373b-130">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 计算机的管理员应了解安全日志的本地设置可能会被域策略覆盖。</span><span class="sxs-lookup"><span data-stu-id="9373b-130">Administrators of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer should understand that local settings for the Security log can be overwritten by a domain policy.</span></span> <span data-ttu-id="9373b-131">在这种情况下，域策略可能会覆盖子类别设置 (**auditpol /get /subcategory:"application generated"** )。</span><span class="sxs-lookup"><span data-stu-id="9373b-131">In this case, the domain policy might overwrite the subcategory setting (**auditpol /get /subcategory:"application generated"**).</span></span> <span data-ttu-id="9373b-132">这可能会影响 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在无法检测 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 尝试审核的事件是否将不被记录的情况下记录事件的能力。</span><span class="sxs-lookup"><span data-stu-id="9373b-132">This can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ability to log events without having any way to detect that the events that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is trying to audit are not going to be recorded.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9373b-133">Security</span><span class="sxs-lookup"><span data-stu-id="9373b-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9373b-134">权限</span><span class="sxs-lookup"><span data-stu-id="9373b-134">Permissions</span></span>  
 <span data-ttu-id="9373b-135">您必须是 Windows 管理员，才能配置这些设置。</span><span class="sxs-lookup"><span data-stu-id="9373b-135">You must be a Windows administrator to configure these settings.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-auditpol"></a><a name="auditpolAccess"></a> <span data-ttu-id="9373b-136">在 Windows 中使用 auditpol 配置审核对象访问设置</span><span class="sxs-lookup"><span data-stu-id="9373b-136">To configure the audit object access setting in Windows using auditpol</span></span>  
  
1.  <span data-ttu-id="9373b-137">使用管理权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="9373b-137">Open a command prompt with administrative permissions.</span></span>  
  
    1.  <span data-ttu-id="9373b-138">在“开始”菜单中，依次指向“所有程序”、“附件”，右键单击“命令提示符”，然后单击“以管理员身份运行”。</span><span class="sxs-lookup"><span data-stu-id="9373b-138">On the **Start** menu, point to **All Programs**, point to **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="9373b-139">在 **“用户帐户控制”** 对话框打开时，单击 **“继续”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-139">If the **User Account Control** dialog box opens, click **Continue**.</span></span>  
  
2.  <span data-ttu-id="9373b-140">执行以下语句以从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]启用审核。</span><span class="sxs-lookup"><span data-stu-id="9373b-140">Execute the following statement to enable auditing from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
    ```  
    auditpol /set /subcategory:"application generated" /success:enable /failure:enable  
    ```  
  
3.  <span data-ttu-id="9373b-141">关闭命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="9373b-141">Close the command prompt window.</span></span>  
  
##  <a name="to-grant-the-generate-security-audits-permission-to-an-account-using-secpol"></a><a name="secpolAccess"></a> <span data-ttu-id="9373b-142">使用 secpol 将生成安全审核权限授予帐户</span><span class="sxs-lookup"><span data-stu-id="9373b-142">To grant the generate security audits permission to an account using secpol</span></span>  
  
1.  <span data-ttu-id="9373b-143">对于任何 Windows 操作系统，在 **“开始”** 菜单上单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-143">For any Windows operating system, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="9373b-144">键入 **secpol.msc** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-144">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="9373b-145">在显示 **“用户访问控制”** 对话框时，单击 **“继续”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-145">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="9373b-146">在“本地安全策略”工具中，依次展开 **“安全设置”** 、 **“本地策略”** ，然后单击 **“用户权限分配”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-146">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
4.  <span data-ttu-id="9373b-147">在结果窗格中，双击“生成安全审核”。</span><span class="sxs-lookup"><span data-stu-id="9373b-147">In the results pane, double-click **Generate security audits**.</span></span>  
  
5.  <span data-ttu-id="9373b-148">在 **“本地安全设置”** 选项卡上，单击 **“添加用户或组”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-148">On the **Local Security Setting** tab, click **Add User or Group**.</span></span>  
  
6.  <span data-ttu-id="9373b-149">在“选择用户、计算机或组”对话框中，键入用户帐户的名称，例如 **domain1\user1**，然后单击“确定”，或单击“高级”并搜索帐户。</span><span class="sxs-lookup"><span data-stu-id="9373b-149">In the **Select Users, Computers, or Groups** dialog box, either type the name of the user account, such as **domain1\user1** and then click **OK**, or click **Advanced** and search for the account.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="9373b-150">关闭安全策略工具。</span><span class="sxs-lookup"><span data-stu-id="9373b-150">Close the Security Policy tool.</span></span>  
  
9. <span data-ttu-id="9373b-151">重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以便启用此设置。</span><span class="sxs-lookup"><span data-stu-id="9373b-151">Restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to enable this setting.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-secpol"></a><a name="secpolPermission"></a> <span data-ttu-id="9373b-152">在 Windows 中使用 secpol 配置审核对象访问设置</span><span class="sxs-lookup"><span data-stu-id="9373b-152">To configure the audit object access setting in Windows using secpol</span></span>  
  
1.  <span data-ttu-id="9373b-153">如果操作系统的版本早于 [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] 或 Windows Server 2008，则在 **“开始”** 菜单上单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-153">If the operating system is earlier than [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] or Windows Server 2008, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="9373b-154">键入 **secpol.msc** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-154">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="9373b-155">在显示 **“用户访问控制”** 对话框时，单击 **“继续”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-155">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="9373b-156">在“本地安全策略”工具中，依次展开 **“安全设置”** 、 **“本地策略”** ，然后单击 **“审核策略”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-156">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.</span></span>  
  
4.  <span data-ttu-id="9373b-157">在结果窗格中，双击“审核对象访问”。</span><span class="sxs-lookup"><span data-stu-id="9373b-157">In the results pane, double-click **Audit object access**.</span></span>  
  
5.  <span data-ttu-id="9373b-158">在 **“本地安全设置”** 选项卡上的 **“审核这些操作”** 区域中，选择 **“成功”** 和 **“失败”** 。</span><span class="sxs-lookup"><span data-stu-id="9373b-158">On the **Local Security Setting** tab, in the **Audit these attempts** area, select both **Success** and **Failure**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="9373b-159">关闭安全策略工具。</span><span class="sxs-lookup"><span data-stu-id="9373b-159">Close the Security Policy tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9373b-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9373b-160">See Also</span></span>  
 [<span data-ttu-id="9373b-161">SQL Server Audit（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="9373b-161">SQL Server Audit &#40;Database Engine&#41;</span></span>](sql-server-audit-database-engine.md)  
  
  
