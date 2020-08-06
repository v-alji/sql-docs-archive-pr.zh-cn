---
title: SqlErrorLogFile 类 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d73f97ebddd7a1d18c73a2cbce7fe79dafc17a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687620"
---
# <a name="sqlerrorlogfile-class"></a><span data-ttu-id="6b2c0-102">SqlErrorLogFile 类</span><span class="sxs-lookup"><span data-stu-id="6b2c0-102">SqlErrorLogFile Class</span></span>
  <span data-ttu-id="6b2c0-103">提供用于查看与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件有关的信息的属性。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-103">Provides properties for viewing information about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2c0-104">语法</span><span class="sxs-lookup"><span data-stu-id="6b2c0-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="6b2c0-105">属性</span><span class="sxs-lookup"><span data-stu-id="6b2c0-105">Properties</span></span>  
 <span data-ttu-id="6b2c0-106">SQLErrorLogFile 类定义以下属性。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-106">The SQLErrorLogFile class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b2c0-107">ArchiveNumber</span><span class="sxs-lookup"><span data-stu-id="6b2c0-107">ArchiveNumber</span></span>|<span data-ttu-id="6b2c0-108">数据类型：`uint32`</span><span class="sxs-lookup"><span data-stu-id="6b2c0-108">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="6b2c0-109">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="6b2c0-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="6b2c0-110">日志文件的存档号。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-110">The archive number for the log file.</span></span>|  
|<span data-ttu-id="6b2c0-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="6b2c0-111">InstanceName</span></span>|<span data-ttu-id="6b2c0-112">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="6b2c0-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="6b2c0-113">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="6b2c0-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="6b2c0-114">限定符：键</span><span class="sxs-lookup"><span data-stu-id="6b2c0-114">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="6b2c0-115">日志文件所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="6b2c0-116">LastModified</span><span class="sxs-lookup"><span data-stu-id="6b2c0-116">LastModified</span></span>|<span data-ttu-id="6b2c0-117">数据类型：`datetime`</span><span class="sxs-lookup"><span data-stu-id="6b2c0-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="6b2c0-118">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="6b2c0-118">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="6b2c0-119">上次修改日志文件的日期。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-119">The date that the log file was last modified.</span></span>|  
|<span data-ttu-id="6b2c0-120">LogFileSize</span><span class="sxs-lookup"><span data-stu-id="6b2c0-120">LogFileSize</span></span>|<span data-ttu-id="6b2c0-121">数据类型：`uint32`</span><span class="sxs-lookup"><span data-stu-id="6b2c0-121">Data type: `uint32`</span></span><br /><br /> <span data-ttu-id="6b2c0-122">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="6b2c0-122">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="6b2c0-123">日志文件大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-123">The log file size, in bytes.</span></span>|  
|<span data-ttu-id="6b2c0-124">名称</span><span class="sxs-lookup"><span data-stu-id="6b2c0-124">Name</span></span>|<span data-ttu-id="6b2c0-125">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="6b2c0-125">Data type: `string`</span></span><br /><br /> <span data-ttu-id="6b2c0-126">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="6b2c0-126">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="6b2c0-127">限定符：键</span><span class="sxs-lookup"><span data-stu-id="6b2c0-127">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="6b2c0-128">日志文件名。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-128">The name of the log file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b2c0-129">备注</span><span class="sxs-lookup"><span data-stu-id="6b2c0-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b2c0-130">MOF</span><span class="sxs-lookup"><span data-stu-id="6b2c0-130">MOF</span></span>|<span data-ttu-id="6b2c0-131">Sqlmgmprovider xpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="6b2c0-131">Sqlmgmprovider xpsp2up.mof</span></span>|  
|<span data-ttu-id="6b2c0-132">DLL</span><span class="sxs-lookup"><span data-stu-id="6b2c0-132">DLL</span></span>|<span data-ttu-id="6b2c0-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="6b2c0-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="6b2c0-134">命名空间</span><span class="sxs-lookup"><span data-stu-id="6b2c0-134">Namespace</span></span>|<span data-ttu-id="6b2c0-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="6b2c0-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b2c0-136">示例</span><span class="sxs-lookup"><span data-stu-id="6b2c0-136">Example</span></span>  
 <span data-ttu-id="6b2c0-137">下面的示例检索与指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件有关的信息。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-137">The following example retrieves information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6b2c0-138">若要运行该示例，请将替换 \<*Instance_Name*> 为该实例的名称，例如 "Instance1"。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-138">To run the example, replace \<*Instance_Name*> with the name of the instance, for example, 'Instance1'.</span></span>  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a><span data-ttu-id="6b2c0-139">注释</span><span class="sxs-lookup"><span data-stu-id="6b2c0-139">Comments</span></span>  
 <span data-ttu-id="6b2c0-140">如果 WQL 语句中未提供*InstanceName* ，则查询将返回默认实例的信息。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-140">When *InstanceName* is not provided in the WQL statement, the query will return information for the default instance.</span></span> <span data-ttu-id="6b2c0-141">例如，以下 WQL 语句将返回与来自默认实例 (MSSQLSERVER) 的所有日志文件有关的信息。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-141">For example, the following WQL statement will return information about all log files from the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a><span data-ttu-id="6b2c0-142">安全性</span><span class="sxs-lookup"><span data-stu-id="6b2c0-142">Security</span></span>  
 <span data-ttu-id="6b2c0-143">若要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过 WMI 连接到日志文件，您必须在本地和远程计算机上都具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="6b2c0-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="6b2c0-144">对**Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空间的读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="6b2c0-145">默认情况下，每个人都可以通过“启用帐户”权限获得读取权限。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b2c0-146">有关如何验证 WMI 权限的信息，请参阅主题中的 "[查看脱机日志文件](../logs/view-offline-log-files.md)" 的 "安全性" 部分。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-146">For information about how to verify WMI permissions, see the Security section of the topic [View Offline Log Files](../logs/view-offline-log-files.md).</span></span>  
  
-   <span data-ttu-id="6b2c0-147">包含错误日志的文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-147">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="6b2c0-148">默认情况下，错误日志位于以下路径中 (其中 \<*Drive> \* 表示你安装的驱动器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， \<*InstanceName*> 是) 实例的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="6b2c0-148">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="6b2c0-149">\*\* \<Drive> ： \PROGRAM Files\Microsoft SQL Server\MSSQL11\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="6b2c0-149">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL11** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="6b2c0-150">如果您在通过防火墙进行连接，则请确保在防火墙中针对远程目标计算机上的 WMI 设置例外。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-150">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="6b2c0-151">有关详细信息，请参阅[从 Windows Vista 远程连接到 WMI](https://go.microsoft.com/fwlink/?LinkId=178848)。</span><span class="sxs-lookup"><span data-stu-id="6b2c0-151">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2c0-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b2c0-152">See Also</span></span>  
 <span data-ttu-id="6b2c0-153">[SqlErrorLogEvent 类](sqlerrorlogevent-class.md) </span><span class="sxs-lookup"><span data-stu-id="6b2c0-153">[SqlErrorLogEvent Class](sqlerrorlogevent-class.md) </span></span>  
 [<span data-ttu-id="6b2c0-154">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="6b2c0-154">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
