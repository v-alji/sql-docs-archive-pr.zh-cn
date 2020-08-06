---
title: tablediff 实用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a23465a7d2c7db53475a6dca81a8471a3b78b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691428"
---
# <a name="tablediff-utility"></a><span data-ttu-id="e9f5a-102">tablediff 实用工具</span><span class="sxs-lookup"><span data-stu-id="e9f5a-102">tablediff Utility</span></span>
  <span data-ttu-id="e9f5a-103">**tablediff** 实用工具用于比较两个非收敛表中的数据，它对于排除复制拓扑中的非收敛故障非常有用。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-103">The **tablediff** utility is used to compare the data in two tables for non-convergence, and is particularly useful for troubleshooting non-convergence in a replication topology.</span></span> <span data-ttu-id="e9f5a-104">可以从命令提示符或在批处理文件中使用该实用工具执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="e9f5a-104">This utility can be used from the command prompt or in a batch file to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e9f5a-105">在充当复制发布服务器的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中的源表与充当复制订阅服务器的一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中的目标表之间进行逐行比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-105">A row by row comparison between a source table in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as a replication Publisher and the destination table at one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as replication Subscribers.</span></span>  
  
-   <span data-ttu-id="e9f5a-106">通过只比较行数和架构可以执行快速比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-106">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
-   <span data-ttu-id="e9f5a-107">执行列级比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-107">Perform column-level comparisons.</span></span>  
  
-   <span data-ttu-id="e9f5a-108">生成 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本，用以修复目标服务器中的差异，以使源表和目标表实现收敛。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-108">Generate a [!INCLUDE[tsql](../includes/tsql-md.md)] script to fix discrepancies at the destination server to bring the source and destination tables into convergence.</span></span>  
  
-   <span data-ttu-id="e9f5a-109">将结果记录到输出文件或目标数据库的表中。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-109">Log results to an output file or into a table in the destination database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f5a-110">语法</span><span class="sxs-lookup"><span data-stu-id="e9f5a-110">Syntax</span></span>  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9f5a-111">参数</span><span class="sxs-lookup"><span data-stu-id="e9f5a-111">Arguments</span></span>  
 <span data-ttu-id="e9f5a-112">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-112">[ **-?**</span></span> <span data-ttu-id="e9f5a-113">]</span><span class="sxs-lookup"><span data-stu-id="e9f5a-113">]</span></span>  
 <span data-ttu-id="e9f5a-114">返回支持参数的列表。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-114">Returns the list of supported parameters.</span></span>  
  
 <span data-ttu-id="e9f5a-115">**-sourceserver** *source_server_name*[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="e9f5a-115">**-sourceserver** *source_server_name*[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="e9f5a-116">源服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-116">Is the name of the source server.</span></span> <span data-ttu-id="e9f5a-117">为的默认实例指定_源 \_ 服务器 \_ 名称_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-117">Specify _source\_server\_name_ for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e9f5a-118">为的命名实例指定_源 \_ 服务器 \_ 名称_ **\\** _实例 \_ 名称_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-118">Specify _source\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e9f5a-119">**-sourcedatabase** *source_database*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-119">**-sourcedatabase** *source_database*</span></span>  
 <span data-ttu-id="e9f5a-120">源数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-120">Is the name of the source database.</span></span>  
  
 <span data-ttu-id="e9f5a-121">**-sourcetable** *source_table_name*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-121">**-sourcetable** *source_table_name*</span></span>  
 <span data-ttu-id="e9f5a-122">正在检查的源表的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-122">Is the name of the source table being checked.</span></span>  
  
 <span data-ttu-id="e9f5a-123">**-sourceschema** *source_schema_name*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-123">**-sourceschema** *source_schema_name*</span></span>  
 <span data-ttu-id="e9f5a-124">源表的架构所有者。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-124">The schema owner of the source table.</span></span> <span data-ttu-id="e9f5a-125">默认情况下，表所有者假定为 dbo。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-125">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="e9f5a-126">**-sourcepassword** *source_password*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-126">**-sourcepassword** *source_password*</span></span>  
 <span data-ttu-id="e9f5a-127">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到源服务器时所使用的登录帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-127">Is the password for the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e9f5a-128">可能的话，请在运行时提供安全凭据。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-128">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="e9f5a-129">如果必须在脚本文件中存储凭据，则应保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-129">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="e9f5a-130">**-sourceuser** *source_login*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-130">**-sourceuser** *source_login*</span></span>  
 <span data-ttu-id="e9f5a-131">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到源服务器时所使用的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-131">Is the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e9f5a-132">如果未提供 *source_login* ，则连接到源服务器时使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-132">If *source_login* is not supplied, then Windows Authentication is used when connecting to the source server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="e9f5a-133">**-sourcelocked**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-133">**-sourcelocked**</span></span>  
 <span data-ttu-id="e9f5a-134">在使用 TABLOCK 和 HOLDLOCK 表提示的比较过程中锁定源表。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-134">The source table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="e9f5a-135">**-destinationserver** *destination_server_name*[ **\\** _实例 \_ 名称_]</span><span class="sxs-lookup"><span data-stu-id="e9f5a-135">**-destinationserver** *destination_server_name*[**\\**_instance\_name_]</span></span>  
 <span data-ttu-id="e9f5a-136">目标服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-136">Is the name of the destination server.</span></span> <span data-ttu-id="e9f5a-137">指定 *destination_server_name* source_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-137">Specify *destination_server_name* for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e9f5a-138">为的命名实例指定_目标 \_ 服务器 \_ 名称_ **\\** _实例 \_ 名称_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-138">Specify _destination\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e9f5a-139">**-destinationdatabase** *subscription_database*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-139">**-destinationdatabase** *subscription_database*</span></span>  
 <span data-ttu-id="e9f5a-140">目标数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-140">Is the name of the destination database.</span></span>  
  
 <span data-ttu-id="e9f5a-141">**-destinationtable** *destination_table*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-141">**-destinationtable** *destination_table*</span></span>  
 <span data-ttu-id="e9f5a-142">目标表的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-142">Is the name of the destination table.</span></span>  
  
 <span data-ttu-id="e9f5a-143">**-destinationschema** *destination_schema_name*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-143">**-destinationschema** *destination_schema_name*</span></span>  
 <span data-ttu-id="e9f5a-144">目标表的架构所有者。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-144">The schema owner of the destination table.</span></span> <span data-ttu-id="e9f5a-145">默认情况下，表所有者假定为 dbo。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-145">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="e9f5a-146">**-destinationpassword** *destination_password*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-146">**-destinationpassword** *destination_password*</span></span>  
 <span data-ttu-id="e9f5a-147">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到目标服务器时所使用的登录帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-147">Is the password for the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e9f5a-148">可能的话，请在运行时提供安全凭据。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-148">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="e9f5a-149">如果必须在脚本文件中存储凭据，则应保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-149">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="e9f5a-150">**-destinationuser** *destination_login*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-150">**-destinationuser** *destination_login*</span></span>  
 <span data-ttu-id="e9f5a-151">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接到目标服务器时所使用的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-151">Is the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e9f5a-152">如果未提供 *destination_login* ，则连接到该服务器时使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-152">If *destination_login* is not supplied, then Windows Authentication is used when connecting to the server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="e9f5a-153">**-destinationlocked**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-153">**-destinationlocked**</span></span>  
 <span data-ttu-id="e9f5a-154">在使用 TABLOCK 和 HOLDLOCK 表提示的比较过程中锁定目标表。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-154">The destination table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="e9f5a-155">**-b** *large_object_bytes*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-155">**-b** *large_object_bytes*</span></span>  
 <span data-ttu-id="e9f5a-156">大型对象数据类型列中要比较的字节数，这些数据类型包括：`text`、`ntext`、`image`、`varchar(max)`、`nvarchar(max)` 和 `varbinary(max)`。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-156">Is the number of bytes to compare for large object data type columns, which includes: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` and `varbinary(max)`.</span></span> <span data-ttu-id="e9f5a-157">*large_object_bytes* 默认为列的大小。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-157">*large_object_bytes* defaults to the size of the column.</span></span> <span data-ttu-id="e9f5a-158">任何大于 *large_object_bytes* 的数据不会进行比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-158">Any data above *large_object_bytes* will not be compared.</span></span>  
  
 <span data-ttu-id="e9f5a-159">**-bf**  *number_of_statements*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-159">**-bf**  *number_of_statements*</span></span>  
 <span data-ttu-id="e9f5a-160">使用 [!INCLUDE[tsql](../includes/tsql-md.md)] -f [!INCLUDE[tsql](../includes/tsql-md.md)] 选项时要写入到当前 **脚本文件中的** 语句数。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-160">Is the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements to write to the current [!INCLUDE[tsql](../includes/tsql-md.md)] script file when the **-f** option is used.</span></span> <span data-ttu-id="e9f5a-161">当 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句数超过 *number_of_statements*时，将创建一个新的 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-161">When the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements exceeds *number_of_statements*, a new [!INCLUDE[tsql](../includes/tsql-md.md)] script file is created.</span></span>  
  
 <span data-ttu-id="e9f5a-162">**-c**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-162">**-c**</span></span>  
 <span data-ttu-id="e9f5a-163">比较列级差异。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-163">Compare column-level differences.</span></span>  
  
 <span data-ttu-id="e9f5a-164">**-dt**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-164">**-dt**</span></span>  
 <span data-ttu-id="e9f5a-165">删除 *table_name*指定的结果表（如果该表已经存在）。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-165">Drop the result table specified by *table_name*, if the table already exists.</span></span>  
  
 <span data-ttu-id="e9f5a-166">**-et** *table_name*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-166">**-et** *table_name*</span></span>  
 <span data-ttu-id="e9f5a-167">指定要创建的结果表的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-167">Specifies the name of the result table to create.</span></span> <span data-ttu-id="e9f5a-168">如果该表已经存在，则必须使用 **-DT** ，否则操作将失败。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-168">If this table already exists, **-DT** must be used or the operation will fail.</span></span>  
  
 <span data-ttu-id="e9f5a-169">**-f** [ *file_name* ]</span><span class="sxs-lookup"><span data-stu-id="e9f5a-169">**-f** [ *file_name* ]</span></span>  
 <span data-ttu-id="e9f5a-170">生成 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本，以使目标服务器中的表与源服务器中的表实现收敛。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-170">Generates a [!INCLUDE[tsql](../includes/tsql-md.md)] script to bring the table at the destination server into convergence with the table at the source server.</span></span> <span data-ttu-id="e9f5a-171">（可选）可以指定生成的 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本文件的名称和路径。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-171">You can optionally specify a name and path for the generated [!INCLUDE[tsql](../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="e9f5a-172">如果未指定 *file_name* ，则会在运行实用工具的目录中生成 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-172">If *file_name* is not specified, the [!INCLUDE[tsql](../includes/tsql-md.md)] script file is generated in the directory where the utility runs.</span></span>  
  
 <span data-ttu-id="e9f5a-173">**-o** *output_file_name*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-173">**-o** *output_file_name*</span></span>  
 <span data-ttu-id="e9f5a-174">输出文件的完整名称和路径。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-174">Is the full name and path of the output file.</span></span>  
  
 <span data-ttu-id="e9f5a-175">**-q**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-175">**-q**</span></span>  
 <span data-ttu-id="e9f5a-176">通过只比较行数和架构可以执行快速比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-176">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
 <span data-ttu-id="e9f5a-177">**-rc** *number_of_retries*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-177">**-rc** *number_of_retries*</span></span>  
 <span data-ttu-id="e9f5a-178">实用工具重试失败操作的次数。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-178">Number of times that the utility retries a failed operation.</span></span>  
  
 <span data-ttu-id="e9f5a-179">**-ri**  *retry_interval*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-179">**-ri**  *retry_interval*</span></span>  
 <span data-ttu-id="e9f5a-180">两次重试之间的等待间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-180">Interval, in seconds, to wait between retries.</span></span>  
  
 <span data-ttu-id="e9f5a-181">**-strict**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-181">**-strict**</span></span>  
 <span data-ttu-id="e9f5a-182">对源架构和目标架构进行严格比较。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-182">Source and destination schema are strictly compared.</span></span>  
  
 <span data-ttu-id="e9f5a-183">**-t** *connection_timeouts*</span><span class="sxs-lookup"><span data-stu-id="e9f5a-183">**-t** *connection_timeouts*</span></span>  
 <span data-ttu-id="e9f5a-184">设置与源服务器和目标服务器连接时的连接超时时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-184">Sets the connection timeout period, in seconds, for connections to the source server and destination server.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9f5a-185">返回值</span><span class="sxs-lookup"><span data-stu-id="e9f5a-185">Return Value</span></span>  
  
|<span data-ttu-id="e9f5a-186">值</span><span class="sxs-lookup"><span data-stu-id="e9f5a-186">Value</span></span>|<span data-ttu-id="e9f5a-187">说明</span><span class="sxs-lookup"><span data-stu-id="e9f5a-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9f5a-188">**0**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-188">**0**</span></span>|<span data-ttu-id="e9f5a-189">Success</span><span class="sxs-lookup"><span data-stu-id="e9f5a-189">Success</span></span>|  
|<span data-ttu-id="e9f5a-190">**1**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-190">**1**</span></span>|<span data-ttu-id="e9f5a-191">严重错误</span><span class="sxs-lookup"><span data-stu-id="e9f5a-191">Critical error</span></span>|  
|<span data-ttu-id="e9f5a-192">**2**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-192">**2**</span></span>|<span data-ttu-id="e9f5a-193">存在表差异</span><span class="sxs-lookup"><span data-stu-id="e9f5a-193">Table differences</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f5a-194">备注</span><span class="sxs-lookup"><span data-stu-id="e9f5a-194">Remarks</span></span>  
 <span data-ttu-id="e9f5a-195">**Tablediff**实用工具不能用于非 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-195">The **tablediff** utility cannot be used with non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="e9f5a-196">不支持包含 `sql_variant` 数据类型列的表。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-196">Tables with `sql_variant` data type columns are not supported.</span></span>  
  
 <span data-ttu-id="e9f5a-197">默认情况下， **tablediff** 实用工具支持源列和目标列之间的以下数据类型映射。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-197">By default, the **tablediff** utility supports the following data type mappings between source and destination columns.</span></span>  
  
|<span data-ttu-id="e9f5a-198">源数据类型</span><span class="sxs-lookup"><span data-stu-id="e9f5a-198">Source data type</span></span>|<span data-ttu-id="e9f5a-199">目标数据类型</span><span class="sxs-lookup"><span data-stu-id="e9f5a-199">Destination data type</span></span>|  
|----------------------|---------------------------|  
|`tinyint`|<span data-ttu-id="e9f5a-200">`smallint`、`int` 或 `bigint`</span><span class="sxs-lookup"><span data-stu-id="e9f5a-200">`smallint`, `int`, or `bigint`</span></span>|  
|`smallint`|<span data-ttu-id="e9f5a-201">`int` 或 `bigint`</span><span class="sxs-lookup"><span data-stu-id="e9f5a-201">`int` or `bigint`</span></span>|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 <span data-ttu-id="e9f5a-202">使用 **-strict** 选项可禁止这些映射，并执行严格验证。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-202">Use the **-strict** option to disallow these mappings and perform a strict validation.</span></span>  
  
 <span data-ttu-id="e9f5a-203">进行比较的源表必须至少包含一个主键、标识或 ROWGUID 列。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-203">The source table in the comparison must contain at least one primary key, identity, or ROWGUID column.</span></span> <span data-ttu-id="e9f5a-204">使用 **-strict** 选项时，目标表也必须具有一个主键、标识或 ROWGUID 列。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-204">When you use the **-strict** option, the destination table must also have a primary key, identity, or ROWGUID column.</span></span>  
  
 <span data-ttu-id="e9f5a-205">所生成的使目标表实现收敛的 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本不包括下列数据类型：</span><span class="sxs-lookup"><span data-stu-id="e9f5a-205">The [!INCLUDE[tsql](../includes/tsql-md.md)] script generated to bring the destination table into convergence does not include the following data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   <span data-ttu-id="e9f5a-206">**xml**</span><span class="sxs-lookup"><span data-stu-id="e9f5a-206">**xml**</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a><span data-ttu-id="e9f5a-207">权限</span><span class="sxs-lookup"><span data-stu-id="e9f5a-207">Permissions</span></span>  
 <span data-ttu-id="e9f5a-208">若要比较表，您必须有要比较的表对象的 SELECT ALL 权限。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-208">To compare tables, you need SELECT ALL permissions on the table objects being compared.</span></span>  
  
 <span data-ttu-id="e9f5a-209">若要使用 **-et** 选项，必须是 db_owner 固定数据库角色的成员，或者在订阅数据库中至少拥有 CREATE TABLE 权限，并且对目标服务器中的目标所有者架构拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-209">To use the **-et** option, you must be a member of the db_owner fixed database role, or at least have CREATE TABLE permission in the subscription database and ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="e9f5a-210">若要使用 **-dt** 选项，必须是 db_owner 固定数据库角色的成员，或者至少对目标服务器中的目标所有者架构拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-210">To use the **-dt** option, you must be a member of the db_owner fixed database role, or at least have ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="e9f5a-211">若要使用 **-o** 或 **-f** 选项，必须对指定的文件目录位置拥有写入权限。</span><span class="sxs-lookup"><span data-stu-id="e9f5a-211">To use the **-o** or **-f** options, you must have write permissions to the specified file directory location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f5a-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9f5a-212">See Also</span></span>  
 [<span data-ttu-id="e9f5a-213">比较所复制表的差异（复制编程）</span><span class="sxs-lookup"><span data-stu-id="e9f5a-213">Compare Replicated Tables for Differences &#40;Replication Programming&#41;</span></span>](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
