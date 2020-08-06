---
title: GenerateDatabaseRightsScript 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 768e73d13d3b06f7913c3c816fded1b28c56199f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692201"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e4d93-102">GenerateDatabaseRightsScript 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e4d93-102">GenerateDatabaseRightsScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e4d93-103">生成一个 SQL 脚本，用来向用户授予运行报表服务器所需的报表服务器数据库和其他数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="e4d93-103">Generates a SQL Script that can be used to grant a user rights to the report server database and other databases required for a report server to run.</span></span> <span data-ttu-id="e4d93-104">调用者需要能够连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库服务器并能够执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="e4d93-104">The caller is expected to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and execute the script.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d93-105">语法</span><span class="sxs-lookup"><span data-stu-id="e4d93-105">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d93-106">parameters</span><span class="sxs-lookup"><span data-stu-id="e4d93-106">Parameters</span></span>  
 <span data-ttu-id="e4d93-107">*UserName*</span><span class="sxs-lookup"><span data-stu-id="e4d93-107">*UserName*</span></span>  
 <span data-ttu-id="e4d93-108">通过此脚本授予权限时作为授予对象的用户的用户名或 Windows 安全标识符 (SID)。</span><span class="sxs-lookup"><span data-stu-id="e4d93-108">The user name or Windows security identifier (SID) of the user to which the script will grant rights.</span></span>  
  
 <span data-ttu-id="e4d93-109">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="e4d93-109">*DatabaseName*</span></span>  
 <span data-ttu-id="e4d93-110">脚本要向用户授予访问权限的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e4d93-110">The database name to which the script will grant access to the user.</span></span>  
  
 <span data-ttu-id="e4d93-111">*IsRemote*</span><span class="sxs-lookup"><span data-stu-id="e4d93-111">*IsRemote*</span></span>  
 <span data-ttu-id="e4d93-112">一个布尔值，指示对于报表服务器而言数据库是否为远程数据库。</span><span class="sxs-lookup"><span data-stu-id="e4d93-112">A Boolean value to indicating whether the database is remote from the report server.</span></span>  
  
 <span data-ttu-id="e4d93-113">*IsWindowsUser*</span><span class="sxs-lookup"><span data-stu-id="e4d93-113">*IsWindowsUser*</span></span>  
 <span data-ttu-id="e4d93-114">一个布尔值，指示指定用户名是 Windows 用户还是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。</span><span class="sxs-lookup"><span data-stu-id="e4d93-114">A Boolean value indicating whether the specified user name is a Windows user or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="e4d93-115">*脚本*</span><span class="sxs-lookup"><span data-stu-id="e4d93-115">*Script*</span></span>  
 <span data-ttu-id="e4d93-116">[out] 包含所生成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本的字符串。</span><span class="sxs-lookup"><span data-stu-id="e4d93-116">[out] A string containing the generated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span>  
  
 <span data-ttu-id="e4d93-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="e4d93-117">*HRESULT*</span></span>  
 <span data-ttu-id="e4d93-118">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="e4d93-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4d93-119">返回值</span><span class="sxs-lookup"><span data-stu-id="e4d93-119">Return Value</span></span>  
 <span data-ttu-id="e4d93-120">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="e4d93-120">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="e4d93-121">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="e4d93-121">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="e4d93-122">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="e4d93-122">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d93-123">备注</span><span class="sxs-lookup"><span data-stu-id="e4d93-123">Remarks</span></span>  
 <span data-ttu-id="e4d93-124">如果 *DatabaseName* 为空，则忽略 *IsRemote* ，并且数据库名称使用报表服务器配置文件中的值。</span><span class="sxs-lookup"><span data-stu-id="e4d93-124">If *DatabaseName* is empty then *IsRemote* is ignored and the report server configuration file value is used for the database name.</span></span>  
  
 <span data-ttu-id="e4d93-125">如果将*如果 iswindowsuser*设置为 `true` ，*用户名*的格式应为 \<domain> \\<用户名 \> 。</span><span class="sxs-lookup"><span data-stu-id="e4d93-125">If *IsWindowsUser* is set to `true`, *UserName* should be in the format \<domain>\\<username\>.</span></span>  
  
 <span data-ttu-id="e4d93-126">如果将*如果 iswindowsuser*设置为 `true` ，则生成的脚本将向用户授予登录权限 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，将 Report Server 数据库设置为默认数据库，并授予对 Report Server 数据库、Report Server 临时数据库、master 数据库和 MSDB 系统数据库的**RSExec**角色。</span><span class="sxs-lookup"><span data-stu-id="e4d93-126">When *IsWindowsUser* is set to `true`, the generated script grants login rights to the user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], setting the report server database as the default database, and grants the **RSExec** role on the report server database, the report server temporary database, the master database and the MSDB system database.</span></span>  
  
 <span data-ttu-id="e4d93-127">当*如果 iswindowsuser*设置为时 `true` ，该方法接受标准 Windows sid 作为输入。</span><span class="sxs-lookup"><span data-stu-id="e4d93-127">When *IsWindowsUser* is set to `true`, the method accepts standard Windows SIDs as input.</span></span> <span data-ttu-id="e4d93-128">在提供标准的 Windows SID 或服务帐户名后，它们会转换为用户名字符串。</span><span class="sxs-lookup"><span data-stu-id="e4d93-128">When a standard Windows SID or service account name is supplied, it is translated to a user name string.</span></span> <span data-ttu-id="e4d93-129">如果数据库是本地数据库，相应帐户会正确转换为帐户的本地化表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4d93-129">If the database is local, the account is translated to the correct localized representation of the account.</span></span> <span data-ttu-id="e4d93-130">如果数据库是远程数据库，则相应帐户会表示为该计算机的帐户。</span><span class="sxs-lookup"><span data-stu-id="e4d93-130">If the database is remote, the account is represented as the computer's account.</span></span>  
  
 <span data-ttu-id="e4d93-131">下表显示了转换后的帐户及其远程表示形式。</span><span class="sxs-lookup"><span data-stu-id="e4d93-131">The following table shows accounts that are translated and their remote representation.</span></span>  
  
|<span data-ttu-id="e4d93-132">被转换的帐户/SID</span><span class="sxs-lookup"><span data-stu-id="e4d93-132">Account / SID that is translated</span></span>|<span data-ttu-id="e4d93-133">公用名</span><span class="sxs-lookup"><span data-stu-id="e4d93-133">Common Name</span></span>|<span data-ttu-id="e4d93-134">远程名称</span><span class="sxs-lookup"><span data-stu-id="e4d93-134">Remote Name</span></span>|  
|---------------------------------------|-----------------|-----------------|  
|<span data-ttu-id="e4d93-135">(S-1-5-18)</span><span class="sxs-lookup"><span data-stu-id="e4d93-135">(S-1-5-18)</span></span>|<span data-ttu-id="e4d93-136">Local System</span><span class="sxs-lookup"><span data-stu-id="e4d93-136">Local System</span></span>|<span data-ttu-id="e4d93-137">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-137">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-138">.\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="e4d93-138">.\LocalSystem</span></span>|<span data-ttu-id="e4d93-139">Local System</span><span class="sxs-lookup"><span data-stu-id="e4d93-139">Local System</span></span>|<span data-ttu-id="e4d93-140">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-140">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-141">ComputerName\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="e4d93-141">ComputerName\LocalSystem</span></span>|<span data-ttu-id="e4d93-142">Local System</span><span class="sxs-lookup"><span data-stu-id="e4d93-142">Local System</span></span>|<span data-ttu-id="e4d93-143">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-143">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-144">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="e4d93-144">LocalSystem</span></span>|<span data-ttu-id="e4d93-145">Local System</span><span class="sxs-lookup"><span data-stu-id="e4d93-145">Local System</span></span>|<span data-ttu-id="e4d93-146">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-146">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-147">(S-1-5-20)</span><span class="sxs-lookup"><span data-stu-id="e4d93-147">(S-1-5-20)</span></span>|<span data-ttu-id="e4d93-148">Network Service</span><span class="sxs-lookup"><span data-stu-id="e4d93-148">Network Service</span></span>|<span data-ttu-id="e4d93-149">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-149">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-150">NT AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="e4d93-150">NT AUTHORITY\NetworkService</span></span>|<span data-ttu-id="e4d93-151">Network Service</span><span class="sxs-lookup"><span data-stu-id="e4d93-151">Network Service</span></span>|<span data-ttu-id="e4d93-152">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="e4d93-152">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="e4d93-153">(S-1-5-19)</span><span class="sxs-lookup"><span data-stu-id="e4d93-153">(S-1-5-19)</span></span>|<span data-ttu-id="e4d93-154">Local Service</span><span class="sxs-lookup"><span data-stu-id="e4d93-154">Local Service</span></span>|<span data-ttu-id="e4d93-155">错误 - 参见下方内容。</span><span class="sxs-lookup"><span data-stu-id="e4d93-155">Error - see below.</span></span>|  
|<span data-ttu-id="e4d93-156">NT AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="e4d93-156">NT AUTHORITY\LocalService</span></span>|<span data-ttu-id="e4d93-157">Local Service</span><span class="sxs-lookup"><span data-stu-id="e4d93-157">Local Service</span></span>|<span data-ttu-id="e4d93-158">错误 - 参见下方内容。</span><span class="sxs-lookup"><span data-stu-id="e4d93-158">Error - see below.</span></span>|  
  
 <span data-ttu-id="e4d93-159">在 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]上，如果使用的是内置帐户，且报表服务器数据库是远程数据库，将返回错误。</span><span class="sxs-lookup"><span data-stu-id="e4d93-159">On [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], if you are using a built-in account and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="e4d93-160">如果指定了 `LocalService` 内置帐户，且报表服务器数据库是远程数据库，将返回错误。</span><span class="sxs-lookup"><span data-stu-id="e4d93-160">If the `LocalService` built-in account is specified and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="e4d93-161">如果 *IsWindowsUser* 为 true，且 *UserName* 中提供的值需要转换，则 WMI 提供程序会确定报表服务器数据库是位于同一计算机上还是远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="e4d93-161">When *IsWindowsUser* is true and the value supplied in *UserName* needs to be translated, the WMI provider determines whether the report server database is located on the same computer or on a remote computer.</span></span> <span data-ttu-id="e4d93-162">为了确定该数据库是否安装在本地，WMI 提供程序会将 DatabaseServerName 属性与下面的值列表进行对比评估。</span><span class="sxs-lookup"><span data-stu-id="e4d93-162">To determine if the installation is local, the WMI provider evaluates the DatabaseServerName property against the following list of values.</span></span> <span data-ttu-id="e4d93-163">如果发现结果匹配，则数据库为本地数据库。</span><span class="sxs-lookup"><span data-stu-id="e4d93-163">If a match is found, the database is local.</span></span> <span data-ttu-id="e4d93-164">否则，为远程数据库。</span><span class="sxs-lookup"><span data-stu-id="e4d93-164">Otherwise, it is remote.</span></span> <span data-ttu-id="e4d93-165">比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e4d93-165">The comparison is case-insensitive.</span></span>  
  
|<span data-ttu-id="e4d93-166">DatabaseServerName 的值</span><span class="sxs-lookup"><span data-stu-id="e4d93-166">Value of DatabaseServerName</span></span>|<span data-ttu-id="e4d93-167">示例</span><span class="sxs-lookup"><span data-stu-id="e4d93-167">Example</span></span>|  
|---------------------------------|-------------|  
|<span data-ttu-id="e4d93-168">"."</span><span class="sxs-lookup"><span data-stu-id="e4d93-168">"."</span></span>||  
|<span data-ttu-id="e4d93-169">"(local)"</span><span class="sxs-lookup"><span data-stu-id="e4d93-169">"(local)"</span></span>||  
|<span data-ttu-id="e4d93-170">"LOCAL"</span><span class="sxs-lookup"><span data-stu-id="e4d93-170">"LOCAL"</span></span>||  
|<span data-ttu-id="e4d93-171">localhost</span><span class="sxs-lookup"><span data-stu-id="e4d93-171">localhost</span></span>||  
|\<Machinename>|<span data-ttu-id="e4d93-172">testlab14</span><span class="sxs-lookup"><span data-stu-id="e4d93-172">testlab14</span></span>|  
|\<MachineFQDN>|<span data-ttu-id="e4d93-173">example.redmond.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="e4d93-173">example.redmond.microsoft.com</span></span>|  
|\<IPAddress>|<span data-ttu-id="e4d93-174">180.012.345,678</span><span class="sxs-lookup"><span data-stu-id="e4d93-174">180.012.345,678</span></span>|  
  
 <span data-ttu-id="e4d93-175">如果将*如果 iswindowsuser*设置为 `true` ，则 WMI 提供程序会调用 LookupAccountName 来获取该帐户的 SID，然后调用 LookupAccountSID 来获取要放入脚本中的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e4d93-175">When *IsWindowsUser* is set to `true`, the WMI provider calls LookupAccountName to get the SID for the account and then calls LookupAccountSID to get the name to put in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span> <span data-ttu-id="e4d93-176">这样便可确保所使用的帐户名可通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 验证。</span><span class="sxs-lookup"><span data-stu-id="e4d93-176">This ensures that the account name used will pass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validation.</span></span>  
  
 <span data-ttu-id="e4d93-177">当*如果 iswindowsuser*设置为时 `false` ，生成的脚本将授予对 Report Server 数据库的**RSExec**角色、Report Server 临时数据库和 MSDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="e4d93-177">When *IsWindowsUser* is set to `false`, the generated script grants the **RSExec** role on the report server database, the report server temporary database, and the MSDB database.</span></span>  
  
 <span data-ttu-id="e4d93-178">当*如果 iswindowsuser*设置为时 `false` ，中的 SQL Server 用户必须已经存在于上才能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 成功运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="e4d93-178">When *IsWindowsUser* is set to `false`, the SQL Server user must already exist on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the script to run successfully.</span></span>  
  
 <span data-ttu-id="e4d93-179">如果报表服务器没有指定的报表服务器数据库，调用 GrantRightsToDatabaseUser 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="e4d93-179">If the report server does not have a report server database specified, calling GrantRightsToDatabaseUser returns an error.</span></span>  
  
 <span data-ttu-id="e4d93-180">生成的脚本支持 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e4d93-180">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d93-181">要求</span><span class="sxs-lookup"><span data-stu-id="e4d93-181">Requirements</span></span>  
 <span data-ttu-id="e4d93-182">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d93-182">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d93-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4d93-183">See Also</span></span>  
 [<span data-ttu-id="e4d93-184">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="e4d93-184">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
