---
title: SQL Server Express LocalDB 标头和版本信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 138081852cf505b03265fd9c5f39eae6ed2af39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590822"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a><span data-ttu-id="84be3-102">SQL Server Express LocalDB 标头信息和版本信息</span><span class="sxs-lookup"><span data-stu-id="84be3-102">SQL Server Express LocalDB Header and Version Information</span></span>
  <span data-ttu-id="84be3-103">没有用于 SQL Server Express LocalDB 实例 API 的单独头文件；LocalDB 函数签名和错误代码在 SQL Server Native Client 头文件 (sqlncli.h) 中定义。</span><span class="sxs-lookup"><span data-stu-id="84be3-103">There is no separate header file for the SQL Server Express LocalDB instance API; the LocalDB function signatures and error codes are defined in the SQL Server Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="84be3-104">若要使用 LocalDB 实例 API，必须在项目中包含 sqlncli.h 头文件。</span><span class="sxs-lookup"><span data-stu-id="84be3-104">To use the LocalDB instance API, you must include the sqlncli.h header file in your project.</span></span>  
  
## <a name="localdb-versioning"></a><span data-ttu-id="84be3-105">LocalDB 版本</span><span class="sxs-lookup"><span data-stu-id="84be3-105">LocalDB Versioning</span></span>  
 <span data-ttu-id="84be3-106">对于每个主要 SQL Server 版本，LocalDB 安装将使用单组二进制代码。</span><span class="sxs-lookup"><span data-stu-id="84be3-106">The LocalDB installation uses a single set of binaries per major SQL Server version.</span></span> <span data-ttu-id="84be3-107">这些 LocalDB 版本独立进行维护和修补。</span><span class="sxs-lookup"><span data-stu-id="84be3-107">These LocalDB versions are maintained and patched independently.</span></span> <span data-ttu-id="84be3-108">这意味着，用户必须指定他或她将使用的 LocalDB 基准版本（也即主 SQL Server 版本）。</span><span class="sxs-lookup"><span data-stu-id="84be3-108">This means that the user has to specify which LocalDB baseline release (that is, major SQL Server version) he or she will be using.</span></span> <span data-ttu-id="84be3-109">版本是使用 .NET Framework **system.web**类定义的标准版本格式指定的：</span><span class="sxs-lookup"><span data-stu-id="84be3-109">The version is specified in the standard version format defined by the .NET Framework **System.Version** class:</span></span>  
  
 <span data-ttu-id="84be3-110">*主要. 次要 [. 生成 [. 修订]]*</span><span class="sxs-lookup"><span data-stu-id="84be3-110">*major.minor[.build[.revision]]*</span></span>  
  
 <span data-ttu-id="84be3-111">版本字符串中的前两个数字 (*主要*和*次要*) 是必需的。</span><span class="sxs-lookup"><span data-stu-id="84be3-111">The first two numbers in the version string (*major* and *minor*) are mandatory.</span></span> <span data-ttu-id="84be3-112">版本字符串中的最后两个数字 (*生成*和*修订*) 是可选的，如果用户将其省略，则默认为零。这意味着，如果用户仅指定 "12.2" 作为 LocalDB 版本号，则会将其视为用户指定了 "12.2.0.0"。</span><span class="sxs-lookup"><span data-stu-id="84be3-112">The last two numbers in the version string (*build* and *revision*) are optional and default to zero if the user leaves them out. This means that if the user specifies only "12.2" as the LocalDB version number, it will be treated as if the user specified "12.2.0.0".</span></span>  
  
 <span data-ttu-id="84be3-113">LocalDB 安装的版本在 SQL Server 实例注册表项下的 MSSQLServer\CurrentVersion 注册表项中定义，例如：</span><span class="sxs-lookup"><span data-stu-id="84be3-113">The version for the LocalDB installation is defined in the MSSQLServer\CurrentVersion registry key under the SQL Server instance registry key, for example:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 <span data-ttu-id="84be3-114">并行支持同一工作站上的多个 LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="84be3-114">Multiple LocalDB versions on the same workstation are supported side-by-side.</span></span> <span data-ttu-id="84be3-115">但是，用户代码始终使用本地计算机上的最新可用的**Sqluserinstance.dll** DLL 连接到 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="84be3-115">However, user code always uses the latest available **SQLUserInstance** DLL on the local computer to connect to LocalDB instances.</span></span>  
  
## <a name="locating-the-sqluserinstance-dll"></a><span data-ttu-id="84be3-116">查找 SQLUserInstance DLL</span><span class="sxs-lookup"><span data-stu-id="84be3-116">Locating the SQLUserInstance DLL</span></span>  
 <span data-ttu-id="84be3-117">若要查找**Sqluserinstance.dll** DLL，客户端提供程序使用以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="84be3-117">To locate the **SQLUserInstance** DLL, the client provider uses the following registry key:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 <span data-ttu-id="84be3-118">在此注册表项之下有一个项列表，每个项对应于计算机上安装的每个 LocalDB。</span><span class="sxs-lookup"><span data-stu-id="84be3-118">Under this key there is a list of keys, one for each version of LocalDB installed on the computer.</span></span> <span data-ttu-id="84be3-119">其中每个键都命名为带有格式的 LocalDB 版本号 *\<major-version>* 。*\<minor-version>*</span><span class="sxs-lookup"><span data-stu-id="84be3-119">Each of these keys is named with the LocalDB version number in the format *\<major-version>*.*\<minor-version>*</span></span> <span data-ttu-id="84be3-120">例如， (的密钥名为 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 12.0) 。</span><span class="sxs-lookup"><span data-stu-id="84be3-120">(for example, the key for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is named 12.0).</span></span> <span data-ttu-id="84be3-121">在每个版本项之下都有一个 `InstanceAPIPath` 名称-值对，用于定义指向随该版本一起安装的 SQLUserInstance.dll 文件的完全路径。</span><span class="sxs-lookup"><span data-stu-id="84be3-121">Under each version key there is an `InstanceAPIPath` name-value pair that defines the full path to the SQLUserInstance.dll file installed with that version.</span></span> <span data-ttu-id="84be3-122">下面的示例显示一个安装了 LocalDB 版本 11.0 和 12.0 的计算机的注册表项：</span><span class="sxs-lookup"><span data-stu-id="84be3-122">The following example shows the registry entries for a computer that has LocalDB versions 11.0 and 12.0 installed:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 <span data-ttu-id="84be3-123">客户端提供程序必须在所有已安装的版本中找到最新版本，并从关联的值加载**Sqluserinstance.dll** DLL 文件 `InstanceAPIPath` 。</span><span class="sxs-lookup"><span data-stu-id="84be3-123">The client provider must find the latest version among all installed versions and load the **SQLUserInstance** DLL file from the associated `InstanceAPIPath` value.</span></span>  
  
### <a name="wow64-mode-on-64-bit-windows"></a><span data-ttu-id="84be3-124">64 位 Windows 上的 WOW64 模式</span><span class="sxs-lookup"><span data-stu-id="84be3-124">WOW64 Mode on 64-bit Windows</span></span>  
 <span data-ttu-id="84be3-125">64 位 LocalDB 安装将有一组附加注册表项，以允许在 Windows 64 位上的 Windows 32 位 (WOW64) 模式下运行的 32 位应用程序使用 LocalDB。</span><span class="sxs-lookup"><span data-stu-id="84be3-125">64-bit installations of LocalDB will have an additional set of registry keys to allow 32-bit applications running in Windows-32-on-Windows-64 (WOW64) mode to use LocalDB.</span></span> <span data-ttu-id="84be3-126">具体而言，在 64 位 Windows 上，LocalDB MSI 将创建以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="84be3-126">Specifically, on 64-bit Windows, the LocalDB MSI will create the following registry keys:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 <span data-ttu-id="84be3-127">64位程序读取 `Installed Versions` 密钥将显示指向**sqluserinstance.dll** DLL 的64位版本的值，而32位程序 (在 WOW64 模式下的64位 Windows 上运行) 将自动重定向到 `Installed Versions` hive 下的某个注册表项 `Wow6432Node` 。</span><span class="sxs-lookup"><span data-stu-id="84be3-127">64-bit programs reading the `Installed Versions` key will see values pointing to 64-bit versions of the **SQLUserInstance** DLL, while 32-bit programs (running on 64-bit Windows in WOW64 mode) will be automatically redirected to an `Installed Versions` key located under the `Wow6432Node` hive.</span></span> <span data-ttu-id="84be3-128">此项包含指向**Sqluserinstance.dll** DLL 32 位版本的值。</span><span class="sxs-lookup"><span data-stu-id="84be3-128">This key contains values pointing to 32-bit versions of the **SQLUserInstance** DLL.</span></span>  
  
## <a name="using-localdb_define_proxy_functions"></a><span data-ttu-id="84be3-129">使用 LOCALDB_DEFINE_PROXY_FUNCTIONS</span><span class="sxs-lookup"><span data-stu-id="84be3-129">Using LOCALDB_DEFINE_PROXY_FUNCTIONS</span></span>  
 <span data-ttu-id="84be3-130">LocalDB 实例 API 定义了一个名为 LOCALDB_DEFINE_PROXY_FUNCTIONS 的常量，该常量可自动发现和加载**Sqluserinstance.dll** DLL。</span><span class="sxs-lookup"><span data-stu-id="84be3-130">The LocalDB instance API defines a constant named LOCALDB_DEFINE_PROXY_FUNCTIONS that automates the discovery and loading of the **SqlUserInstance** DLL.</span></span>  
  
 <span data-ttu-id="84be3-131">该常量启用的代码部分为每个 LocalDB API 提供代理的实现。</span><span class="sxs-lookup"><span data-stu-id="84be3-131">The section of code enabled by this constant provides an implementation of proxies for each of the LocalDB APIs.</span></span> <span data-ttu-id="84be3-132">代理实现使用公用函数绑定到最新安装的**Sqluserinstance.dll** DLL 中的入口点，然后转发请求。</span><span class="sxs-lookup"><span data-stu-id="84be3-132">The proxy implementations use a common function to bind to entry points in the latest installed **SqlUserInstance** DLL, and then forward the requests.</span></span>  
  
 <span data-ttu-id="84be3-133">只有在包含 sqlncli.h 之前，在用户代码中定义常量 LOCALDB_DEFINE_PROXY_FUNCTION 时，才启用代理函数。</span><span class="sxs-lookup"><span data-stu-id="84be3-133">The proxy functions are enabled only if the constant LOCALDB_DEFINE_PROXY_FUNCTIONS is defined in the user code before including the sqlncli.h file.</span></span> <span data-ttu-id="84be3-134">只应在一个源模块（.cpp 文件）中定义常量，因为该常量为所有 API 入口点定义外部函数名称。</span><span class="sxs-lookup"><span data-stu-id="84be3-134">The constant should be defined in only one source module (.cpp file) because it defines external function names for all of the API entry points.</span></span> <span data-ttu-id="84be3-135">它为每个 LocalDB API 提供代理的实现。</span><span class="sxs-lookup"><span data-stu-id="84be3-135">It provides an implementation of proxies for each of the LocalDB APIs.</span></span>  
  
 <span data-ttu-id="84be3-136">下面的代码示例演示如何使用本机 C++ 代码中的宏：</span><span class="sxs-lookup"><span data-stu-id="84be3-136">The following code example shows how to use the macro from the native C++ code:</span></span>  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
