---
title: SetDatabaseConnection 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5c62777edd1fab2b0cb3babc13ab09f7bcf32a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692192"
---
# <a name="setdatabaseconnection-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9093a-102">SetDatabaseConnection 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9093a-102">SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9093a-103">设置与特定报表服务器数据库的报表服务器数据库连接。</span><span class="sxs-lookup"><span data-stu-id="9093a-103">Sets the report server database connection to a particular report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9093a-104">语法</span><span class="sxs-lookup"><span data-stu-id="9093a-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9093a-105">parameters</span><span class="sxs-lookup"><span data-stu-id="9093a-105">Parameters</span></span>  
 <span data-ttu-id="9093a-106">*Server*</span><span class="sxs-lookup"><span data-stu-id="9093a-106">*Server*</span></span>  
 <span data-ttu-id="9093a-107">用于托管报表服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称。</span><span class="sxs-lookup"><span data-stu-id="9093a-107">The name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is used to host the report server database.</span></span>  
  
 <span data-ttu-id="9093a-108">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="9093a-108">*DatabaseName*</span></span>  
 <span data-ttu-id="9093a-109">报表服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="9093a-109">The name of the report server database.</span></span>  
  
 <span data-ttu-id="9093a-110">*CredentialsType*</span><span class="sxs-lookup"><span data-stu-id="9093a-110">*CredentialsType*</span></span>  
 <span data-ttu-id="9093a-111">用于连接的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="9093a-111">The type of credentials to use for the connection.</span></span> <span data-ttu-id="9093a-112">值可以是：</span><span class="sxs-lookup"><span data-stu-id="9093a-112">Values can be:</span></span>  
  
-   <span data-ttu-id="9093a-113">0 - Windows</span><span class="sxs-lookup"><span data-stu-id="9093a-113">0 - Windows</span></span>  
  
-   <span data-ttu-id="9093a-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9093a-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="9093a-115">2 - Windows 服务</span><span class="sxs-lookup"><span data-stu-id="9093a-115">2 - Windows Service</span></span>  
  
 <span data-ttu-id="9093a-116">*UserName*</span><span class="sxs-lookup"><span data-stu-id="9093a-116">*UserName*</span></span>  
 <span data-ttu-id="9093a-117">连接报表服务器数据库时所用的帐户名。</span><span class="sxs-lookup"><span data-stu-id="9093a-117">The account name used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="9093a-118">*密码*</span><span class="sxs-lookup"><span data-stu-id="9093a-118">*Password*</span></span>  
 <span data-ttu-id="9093a-119">连接报表服务器数据库时所用的密码。</span><span class="sxs-lookup"><span data-stu-id="9093a-119">The password used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="9093a-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9093a-120">*HRESULT*</span></span>  
 <span data-ttu-id="9093a-121">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="9093a-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9093a-122">返回值</span><span class="sxs-lookup"><span data-stu-id="9093a-122">Return Value</span></span>  
 <span data-ttu-id="9093a-123">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="9093a-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="9093a-124">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="9093a-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="9093a-125">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="9093a-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9093a-126">备注</span><span class="sxs-lookup"><span data-stu-id="9093a-126">Remarks</span></span>  
 <span data-ttu-id="9093a-127">当 CredentialsType 参数设置为 0 (Windows) 时，必须设置 UserName 和 Password 参数    。</span><span class="sxs-lookup"><span data-stu-id="9093a-127">When the *CredentialsType* parameter is set to 0 (Windows), the *UserName* and *Password* parameters must be set.</span></span> <span data-ttu-id="9093a-128">UserName 参数的格式必须为“domain\username”，相应的值必须代表有效的 Windows 登录名  。</span><span class="sxs-lookup"><span data-stu-id="9093a-128">The *UserName* parameter must be in the form "domain\username", and the value must represent a valid Windows logon.</span></span>  
  
 <span data-ttu-id="9093a-129">如果将 CredentialsType 参数设置为 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])，则 UserName 参数传递的值必须符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的要求\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9093a-129">When the *CredentialsType* parameter is set to 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), the value passed in the *UserName* parameter must conform to the requirements of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login name.</span></span>  
  
 <span data-ttu-id="9093a-130">如果将 CredentialsType 参数设置为 2（Windows 服务），则报表服务器将使用集成安全性连接到报表服务器数据库，并且忽略 UserName 和 Password 参数    。</span><span class="sxs-lookup"><span data-stu-id="9093a-130">When the *CredentialsType* parameter is set to 2 (Windows Service), the report server uses integrated security to connect to the report server database and the *UserName* and *Password* parameters are ignored.</span></span> <span data-ttu-id="9093a-131">报告服务器 Web 服务将使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帐户或应用程序池的帐户及 Windows 服务帐户访问报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="9093a-131">The Reporting Server Web service will use either the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account or an application pool's account and the Windows service account to access the report server database.</span></span>  
  
 <span data-ttu-id="9093a-132">调用后，SetDatabaseConnection 方法将加密凭据和数据库信息并将它们存储在指定报表服务器的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="9093a-132">When called, the SetDatabaseConnection method encrypts and stores the credentials and database information in the configuration file for the specified report server.</span></span>  
  
 <span data-ttu-id="9093a-133">SetDatabaseConnection 方法不会检查报表服务器是否可以使用指定的数据连接到报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="9093a-133">The SetDatabaseConnection method does not check that the report server can connect to the report server database using the data specified.</span></span>  
  
 <span data-ttu-id="9093a-134">在第一次设置时，将根据以下处理器来设置 ConnectionPoolSize 属性：ConnectionPoolSize = #Processors \* 75。</span><span class="sxs-lookup"><span data-stu-id="9093a-134">When set for the first time, the ConnectionPoolSize property is set based on the following processors: ConnectionPoolSize = #Processors \* 75.</span></span>  
  
 <span data-ttu-id="9093a-135">SetDatabaseConnection 方法不会向指定的帐户授予权限。</span><span class="sxs-lookup"><span data-stu-id="9093a-135">The SetDatabaseConnection method does not grant permissions to the specified account(s).</span></span> <span data-ttu-id="9093a-136">您必须为需要访问报表服务器数据库的每一帐户调用 [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) 方法，然后运行所生成的脚本。</span><span class="sxs-lookup"><span data-stu-id="9093a-136">You must call the [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) method for each account that requires access to the report server database and run the resulting script.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9093a-137">要求</span><span class="sxs-lookup"><span data-stu-id="9093a-137">Requirements</span></span>  
 <span data-ttu-id="9093a-138">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9093a-138">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9093a-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9093a-139">See Also</span></span>  
 [<span data-ttu-id="9093a-140">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="9093a-140">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
