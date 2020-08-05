---
title: SqlErrorLogEvent 类 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 358b6906e422be2984f2ebdbde636ad0b8376993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581154"
---
# <a name="sqlerrorlogevent-class"></a><span data-ttu-id="fab9d-102">SqlErrorLogEvent 类</span><span class="sxs-lookup"><span data-stu-id="fab9d-102">SqlErrorLogEvent Class</span></span>
  <span data-ttu-id="fab9d-103">提供用于查看指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件中的事件的属性。</span><span class="sxs-lookup"><span data-stu-id="fab9d-103">Provides properties for viewing events in a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab9d-104">语法</span><span class="sxs-lookup"><span data-stu-id="fab9d-104">Syntax</span></span>  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a><span data-ttu-id="fab9d-105">属性</span><span class="sxs-lookup"><span data-stu-id="fab9d-105">Properties</span></span>  
 <span data-ttu-id="fab9d-106">SQLErrorLogEvent 类定义以下属性。</span><span class="sxs-lookup"><span data-stu-id="fab9d-106">The SQLErrorLogEvent class defines the following properties.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fab9d-107">FileName</span><span class="sxs-lookup"><span data-stu-id="fab9d-107">FileName</span></span>|<span data-ttu-id="fab9d-108">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="fab9d-108">Data type: `string`</span></span><br /><br /> <span data-ttu-id="fab9d-109">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="fab9d-109">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="fab9d-110">错误日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="fab9d-110">The name of the error log file.</span></span>|  
|<span data-ttu-id="fab9d-111">InstanceName</span><span class="sxs-lookup"><span data-stu-id="fab9d-111">InstanceName</span></span>|<span data-ttu-id="fab9d-112">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="fab9d-112">Data type: `string`</span></span><br /><br /> <span data-ttu-id="fab9d-113">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="fab9d-113">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="fab9d-114">限定符：键</span><span class="sxs-lookup"><span data-stu-id="fab9d-114">Qualifiers: Key</span></span><br /><br /> <span data-ttu-id="fab9d-115">日志文件所在的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="fab9d-115">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the log file resides.</span></span>|  
|<span data-ttu-id="fab9d-116">LogDate</span><span class="sxs-lookup"><span data-stu-id="fab9d-116">LogDate</span></span>|<span data-ttu-id="fab9d-117">数据类型：`datetime`</span><span class="sxs-lookup"><span data-stu-id="fab9d-117">Data type: `datetime`</span></span><br /><br /> <span data-ttu-id="fab9d-118">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="fab9d-118">Access type: Read-only</span></span><br /><br /> <span data-ttu-id="fab9d-119">限定符：键</span><span class="sxs-lookup"><span data-stu-id="fab9d-119">Qualifiers: Key</span></span><br /><br /> <br /><br /> <span data-ttu-id="fab9d-120">在日志文件中记录该事件的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="fab9d-120">The date and time that the event was recorded in the log file.</span></span>|  
|<span data-ttu-id="fab9d-121">Message</span><span class="sxs-lookup"><span data-stu-id="fab9d-121">Message</span></span>|<span data-ttu-id="fab9d-122">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="fab9d-122">Data type: `string`</span></span><br /><br /> <span data-ttu-id="fab9d-123">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="fab9d-123">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="fab9d-124">事件消息。</span><span class="sxs-lookup"><span data-stu-id="fab9d-124">The event message.</span></span>|  
|<span data-ttu-id="fab9d-125">ProcessInfo</span><span class="sxs-lookup"><span data-stu-id="fab9d-125">ProcessInfo</span></span>|<span data-ttu-id="fab9d-126">数据类型：`string`</span><span class="sxs-lookup"><span data-stu-id="fab9d-126">Data type: `string`</span></span><br /><br /> <span data-ttu-id="fab9d-127">访问类型：只读</span><span class="sxs-lookup"><span data-stu-id="fab9d-127">Access type: Read-only</span></span><br /><br /> <br /><br /> <span data-ttu-id="fab9d-128">与事件的源服务器进程 ID (SPID) 有关的信息。</span><span class="sxs-lookup"><span data-stu-id="fab9d-128">Information about the source server process ID (SPID) for the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fab9d-129">备注</span><span class="sxs-lookup"><span data-stu-id="fab9d-129">Remarks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fab9d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="fab9d-130">MOF</span></span>|<span data-ttu-id="fab9d-131">Sqlmgmproviderxpsp2up.mof</span><span class="sxs-lookup"><span data-stu-id="fab9d-131">Sqlmgmproviderxpsp2up.mof</span></span>|  
|<span data-ttu-id="fab9d-132">DLL</span><span class="sxs-lookup"><span data-stu-id="fab9d-132">DLL</span></span>|<span data-ttu-id="fab9d-133">Sqlmgmprovider.dll</span><span class="sxs-lookup"><span data-stu-id="fab9d-133">Sqlmgmprovider.dll</span></span>|  
|<span data-ttu-id="fab9d-134">命名空间</span><span class="sxs-lookup"><span data-stu-id="fab9d-134">Namespace</span></span>|<span data-ttu-id="fab9d-135">\root\Microsoft\SqlServer\ComputerManagement10</span><span class="sxs-lookup"><span data-stu-id="fab9d-135">\root\Microsoft\SqlServer\ComputerManagement10</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fab9d-136">示例</span><span class="sxs-lookup"><span data-stu-id="fab9d-136">Example</span></span>  
 <span data-ttu-id="fab9d-137">下面的示例显示如何检索指定的日志文件中所有记录的事件的值。</span><span class="sxs-lookup"><span data-stu-id="fab9d-137">The following example shows how to retrieve values for all logged events in a specified log file.</span></span> <span data-ttu-id="fab9d-138">若要运行该示例，请将替换 \<*Instance_Name*> 为实例的名称（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 例如 "Instance1"），并将 "File_Name" 替换为错误日志文件的名称，如 "错误日志 1"。</span><span class="sxs-lookup"><span data-stu-id="fab9d-138">To run the example, replace \<*Instance_Name*> with the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as 'Instance1', and replace 'File_Name' with the name of the error log file, such as 'ERRORLOG.1'.</span></span>  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a><span data-ttu-id="fab9d-139">注释</span><span class="sxs-lookup"><span data-stu-id="fab9d-139">Comments</span></span>  
 <span data-ttu-id="fab9d-140">如果 WQL 语句中未提供*InstanceName*或*FileName* ，则查询将返回默认实例和当前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件的信息。</span><span class="sxs-lookup"><span data-stu-id="fab9d-140">When *InstanceName* or *FileName* are not provided in the WQL statement, the query will return information for the default instance and the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file.</span></span> <span data-ttu-id="fab9d-141">例如，以下 WQL 语句将返回与来自默认实例 (MSSQLSERVER) 上当前日志文件 (ERRORLOG) 的所有日志事件有关的信息。</span><span class="sxs-lookup"><span data-stu-id="fab9d-141">For example, the following WQL statement will return all log events from the current log file (ERRORLOG) on the default instance (MSSQLSERVER).</span></span>  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a><span data-ttu-id="fab9d-142">安全性</span><span class="sxs-lookup"><span data-stu-id="fab9d-142">Security</span></span>  
 <span data-ttu-id="fab9d-143">若要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过 WMI 连接到日志文件，您必须在本地和远程计算机上都具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="fab9d-143">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log file through WMI, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="fab9d-144">对**Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空间的读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="fab9d-144">Read access to the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace.</span></span> <span data-ttu-id="fab9d-145">默认情况下，每个人都可以通过“启用帐户”权限获得读取权限。</span><span class="sxs-lookup"><span data-stu-id="fab9d-145">By default, everyone has read access through the Enable Account permission.</span></span>  
  
-   <span data-ttu-id="fab9d-146">包含错误日志的文件夹的读取权限。</span><span class="sxs-lookup"><span data-stu-id="fab9d-146">Read permission to the folder that contains the error logs.</span></span> <span data-ttu-id="fab9d-147">默认情况下，错误日志位于以下路径中 (其中 \<*Drive> \* 表示你安装的驱动器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， \<*InstanceName*> 是) 实例的名称 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="fab9d-147">By default the error logs are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="fab9d-148">\*\* \<Drive> ： \PROGRAM Files\Microsoft SQL Server\MSSQL12\*\* **。 \<InstanceName>\MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="fab9d-148">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12** **.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="fab9d-149">如果您在通过防火墙进行连接，则请确保在防火墙中针对远程目标计算机上的 WMI 设置例外。</span><span class="sxs-lookup"><span data-stu-id="fab9d-149">If you are connecting through a firewall, ensure that an exception is set in the firewall for WMI on remote target computers.</span></span> <span data-ttu-id="fab9d-150">有关详细信息，请参阅[从 Windows Vista 远程连接到 WMI](https://go.microsoft.com/fwlink/?LinkId=178848)。</span><span class="sxs-lookup"><span data-stu-id="fab9d-150">For more information, see [Connecting to WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab9d-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fab9d-151">See Also</span></span>  
 <span data-ttu-id="fab9d-152">[SqlErrorLogFile 类](sqlerrorlogfile-class.md) </span><span class="sxs-lookup"><span data-stu-id="fab9d-152">[SqlErrorLogFile Class](sqlerrorlogfile-class.md) </span></span>  
 [<span data-ttu-id="fab9d-153">查看脱机日志文件</span><span class="sxs-lookup"><span data-stu-id="fab9d-153">View Offline Log Files</span></span>](../logs/view-offline-log-files.md)  
  
  
