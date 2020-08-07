---
title: bcp_control |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ea5d60da8069707a53f3bdf2de53345cd11090f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576729"
---
# <a name="bcp_control"></a><span data-ttu-id="a92b8-102">bcp_control</span><span class="sxs-lookup"><span data-stu-id="a92b8-102">bcp_control</span></span>
  <span data-ttu-id="a92b8-103">更改用于在文件和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之间进行大容量复制的各种控制参数的默认设置。</span><span class="sxs-lookup"><span data-stu-id="a92b8-103">Changes the default settings for various control parameters for a bulk copy between a file and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a92b8-104">语法</span><span class="sxs-lookup"><span data-stu-id="a92b8-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a92b8-105">自变量</span><span class="sxs-lookup"><span data-stu-id="a92b8-105">Arguments</span></span>  
 <span data-ttu-id="a92b8-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="a92b8-106">*hdbc*</span></span>  
 <span data-ttu-id="a92b8-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="a92b8-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="a92b8-108">*eOption*</span><span class="sxs-lookup"><span data-stu-id="a92b8-108">*eOption*</span></span>  
 <span data-ttu-id="a92b8-109">可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="a92b8-109">Is one of the following:</span></span>  
  
 <span data-ttu-id="a92b8-110">BCPABORT</span><span class="sxs-lookup"><span data-stu-id="a92b8-110">BCPABORT</span></span>  
 <span data-ttu-id="a92b8-111">停止正在进行的大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="a92b8-111">Stops a bulk-copy operation that is already in progress.</span></span> <span data-ttu-id="a92b8-112">从另一个线程调用*eOption*为 BCPABORT 的**bcp_control** ，停止正在运行的大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="a92b8-112">Call **bcp_control** with an *eOption* of BCPABORT from another thread to stop a running bulk copy operation.</span></span> <span data-ttu-id="a92b8-113">忽略*iValue*参数。</span><span class="sxs-lookup"><span data-stu-id="a92b8-113">The *iValue* parameter is ignored.</span></span>  
  
 <span data-ttu-id="a92b8-114">BCPBATCH</span><span class="sxs-lookup"><span data-stu-id="a92b8-114">BCPBATCH</span></span>  
 <span data-ttu-id="a92b8-115">每批的行数。</span><span class="sxs-lookup"><span data-stu-id="a92b8-115">Is the number of rows per batch.</span></span> <span data-ttu-id="a92b8-116">默认值为 0，当提取数据时，该默认值表示表中的所有行；将数据复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，则表示用户数据文件中的所有行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-116">The default is 0, which indicates either all rows in a table, when data is being extracted, or all rows in the user data file, when data is being copied to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a92b8-117">值小于 1 则将 BCPBATCH 重置为默认值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-117">A value less than 1 resets BCPBATCH to the default.</span></span>  
  
 <span data-ttu-id="a92b8-118">BCPDELAYREADFMT</span><span class="sxs-lookup"><span data-stu-id="a92b8-118">BCPDELAYREADFMT</span></span>  
 <span data-ttu-id="a92b8-119">如果设置为 true，则布尔值将导致[bcp_readfmt](bcp-readfmt.md)在执行时读取。</span><span class="sxs-lookup"><span data-stu-id="a92b8-119">A Boolean, if set to true, will cause [bcp_readfmt](bcp-readfmt.md) to read at execution.</span></span> <span data-ttu-id="a92b8-120">如果为 false (默认) ，bcp_readfmt 将立即读取格式化文件。</span><span class="sxs-lookup"><span data-stu-id="a92b8-120">If false (the default), bcp_readfmt will immediately read the format file.</span></span> <span data-ttu-id="a92b8-121">如果 BCPDELAYREADFMT 为 true 并且您调用 bcp_columns 或 bcp_setcolfmt，则会发生序列错误。</span><span class="sxs-lookup"><span data-stu-id="a92b8-121">A sequence error will occur if BCPDELAYREADFMT is true and you call bcp_columns or bcp_setcolfmt.</span></span>  
  
 <span data-ttu-id="a92b8-122">如果在 `bcp_control(hdbc,` `, (void *)FALSE)` 调用 `bcp_control(hdbc,` BCPDELAYREADFMT 和 bcp_writefmt 后调用 BCPDELAYREADFMT `, (void *)TRUE)` ，也会发生序列错误。</span><span class="sxs-lookup"><span data-stu-id="a92b8-122">A sequence error will also occur if you call `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` after calling `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` and bcp_writefmt.</span></span>  
  
 <span data-ttu-id="a92b8-123">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="a92b8-123">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="a92b8-124">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="a92b8-124">BCPFILECP</span></span>  
 <span data-ttu-id="a92b8-125">*iValue*包含数据文件的代码页的编号。</span><span class="sxs-lookup"><span data-stu-id="a92b8-125">*iValue* contains the number of the code page for the data file.</span></span> <span data-ttu-id="a92b8-126">可以指定代码页的标号，例如 1252 或 850，或者采用以下值之一：</span><span class="sxs-lookup"><span data-stu-id="a92b8-126">You can specify the number of the code page, such as 1252 or 850, or one of these values:</span></span>  
  
 <span data-ttu-id="a92b8-127">BCPFILE_ACP：文件中的数据位于 Microsoft Windows？？</span><span class="sxs-lookup"><span data-stu-id="a92b8-127">BCPFILE_ACP: data in the file is in the Microsoft Windows??</span></span> <span data-ttu-id="a92b8-128">客户端的代码页。</span><span class="sxs-lookup"><span data-stu-id="a92b8-128">code page of the client.</span></span>  
  
 <span data-ttu-id="a92b8-129">BCPFILE_OEMCP：文件中的数据位于客户端的 OEM 代码页中（默认值）。</span><span class="sxs-lookup"><span data-stu-id="a92b8-129">BCPFILE_OEMCP: data in the file is in the OEM code page of the client (default).</span></span>  
  
 <span data-ttu-id="a92b8-130">BCPFILE_RAW：文件中的数据位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的代码页中。</span><span class="sxs-lookup"><span data-stu-id="a92b8-130">BCPFILE_RAW: data in the file is in the code page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a92b8-131">BCPFILEFMT</span><span class="sxs-lookup"><span data-stu-id="a92b8-131">BCPFILEFMT</span></span>  
 <span data-ttu-id="a92b8-132">数据文件格式的版本号。</span><span class="sxs-lookup"><span data-stu-id="a92b8-132">The version number of the data file format.</span></span> <span data-ttu-id="a92b8-133">这可能是 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]) 、90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]) 、100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]) 、110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 或 120 () [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a92b8-133">This can be 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), or 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="a92b8-134">120 是默认值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-134">120 is the default.</span></span> <span data-ttu-id="a92b8-135">对于采用服务器早期版本所支持的格式的数据，该选项对导出和导入这样的数据非常有用。</span><span class="sxs-lookup"><span data-stu-id="a92b8-135">This is useful for exporting and importing data in formats that were supported by earlier version of the server.</span></span> <span data-ttu-id="a92b8-136">例如，若要将从服务器中的文本列获取的数据导入 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 到或更高版本的服务器中的\*\*varchar (max) \*\*列 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，则应指定80。</span><span class="sxs-lookup"><span data-stu-id="a92b8-136">For example, to import data that was obtained from a text column in a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server into a **varchar(max)** column in a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later server, you should specify 80.</span></span> <span data-ttu-id="a92b8-137">同样，如果在从\*\*varchar (max) \*\*列导出数据时指定80，则将像保存文本列那样保存它 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ，并且可以将其导入到服务器的文本列 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a92b8-137">Similarly, if you specify 80 when exporting data from a **varchar(max)** column, it will be saved just like text columns are saved in the [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] format, and can be imported into a text column of a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server.</span></span>  
  
 <span data-ttu-id="a92b8-138">BCPFIRST</span><span class="sxs-lookup"><span data-stu-id="a92b8-138">BCPFIRST</span></span>  
 <span data-ttu-id="a92b8-139">要复制的文件或表的第一行数据。</span><span class="sxs-lookup"><span data-stu-id="a92b8-139">Is the first row of data to file or table to copy.</span></span> <span data-ttu-id="a92b8-140">默认值为 1；值小于 1 则将此选项重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-140">The default is 1; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="a92b8-141">BCPFIRSTEX</span><span class="sxs-lookup"><span data-stu-id="a92b8-141">BCPFIRSTEX</span></span>  
 <span data-ttu-id="a92b8-142">对于 BCP out 操作，指定要复制到数据文件的数据库表的第一行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-142">For BCP out operations, specifies the first row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="a92b8-143">对于 BCP in 操作，指定要复制到数据库表的数据文件的第一行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-143">For BCP in operations, specifies the first row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="a92b8-144">*IValue*参数应为包含值的已签名64位整数的地址。</span><span class="sxs-lookup"><span data-stu-id="a92b8-144">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="a92b8-145">可传递给 BCPFIRSTEX 的最大值为 2 ^ 63-1。</span><span class="sxs-lookup"><span data-stu-id="a92b8-145">The maximum value that can be passed to BCPFIRSTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="a92b8-146">BCPFMTXML</span><span class="sxs-lookup"><span data-stu-id="a92b8-146">BCPFMTXML</span></span>  
 <span data-ttu-id="a92b8-147">指定生成的格式化文件应采用 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="a92b8-147">Specifies that the format file generated should be in XML format.</span></span> <span data-ttu-id="a92b8-148">默认情况下将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="a92b8-148">It is off by default.</span></span>  
  
 <span data-ttu-id="a92b8-149">XML 格式化文件提供了更大的灵活性，但有一些限制。</span><span class="sxs-lookup"><span data-stu-id="a92b8-149">XML format files provide greater flexibility but with some added constraints.</span></span> <span data-ttu-id="a92b8-150">例如，不能同时为字段指定前缀和终止符，这是在较旧的格式化文件中。</span><span class="sxs-lookup"><span data-stu-id="a92b8-150">For example, you can not specify the prefix and terminator for a field simultaneously, which was possible in older format files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92b8-151">只有当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 一起安装后，才支持 XML 格式化文件。</span><span class="sxs-lookup"><span data-stu-id="a92b8-151">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed along with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="a92b8-152">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="a92b8-152">BCPHINTS</span></span>  
 <span data-ttu-id="a92b8-153">*iValue*包含一个 SQLTCHAR 字符串指针。</span><span class="sxs-lookup"><span data-stu-id="a92b8-153">*iValue* contains an SQLTCHAR character string pointer.</span></span> <span data-ttu-id="a92b8-154">寻址的字符串指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量复制处理提示或返回结果集的 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="a92b8-154">The string addressed specifies either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-copy processing hints or a Transact-SQL statement that returns a result set.</span></span> <span data-ttu-id="a92b8-155">如果指定的 Transact-SQL 语句返回多个结果集，则忽略第一个结果集之后的所有结果集。</span><span class="sxs-lookup"><span data-stu-id="a92b8-155">If a Transact-SQL statement is specified that returns more than one result set, all result sets after the first are ignored.</span></span> <span data-ttu-id="a92b8-156">有关大容量复制处理提示的详细信息，请参阅[Bcp 实用工具](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a92b8-156">For more information about bulk-copy processing hints, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="a92b8-157">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="a92b8-157">BCPKEEPIDENTITY</span></span>  
 <span data-ttu-id="a92b8-158">当*iValue*为 TRUE 时，指定大容量复制函数插入为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用标识约束定义的列提供的数据值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-158">When *iValue* is TRUE, specifies that bulk copy functions insert data values supplied for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns defined with an identity constraint.</span></span> <span data-ttu-id="a92b8-159">输入文件必须提供标识列的值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-159">The input file must supply values for the identity columns.</span></span> <span data-ttu-id="a92b8-160">如果未进行设置，则为插入的行生成新标识值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-160">If this is not set, new identity values are generated for the inserted rows.</span></span> <span data-ttu-id="a92b8-161">忽略文件的标识列中所存在的任何数据。</span><span class="sxs-lookup"><span data-stu-id="a92b8-161">Any data present in the file for the identity columns is ignored.</span></span>  
  
 <span data-ttu-id="a92b8-162">BCPKEEPNULLS</span><span class="sxs-lookup"><span data-stu-id="a92b8-162">BCPKEEPNULLS</span></span>  
 <span data-ttu-id="a92b8-163">指定是否会将文件中的空数据值转换为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-163">Specifies whether empty data values in the file will be converted to NULL values in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="a92b8-164">当*iValue*为 TRUE 时，空值将转换为表中的 NULL 值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a92b8-164">When *iValue* is TRUE, empty values will be converted to NULL in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="a92b8-165">默认情况下会将空值转换为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的列的默认值（如果存在默认值）。</span><span class="sxs-lookup"><span data-stu-id="a92b8-165">The default is for empty values to be converted to a default value for the column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table if a default exists.</span></span>  
  
 <span data-ttu-id="a92b8-166">BCPLAST</span><span class="sxs-lookup"><span data-stu-id="a92b8-166">BCPLAST</span></span>  
 <span data-ttu-id="a92b8-167">要复制的最后一行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-167">Is the last row to copy.</span></span> <span data-ttu-id="a92b8-168">默认值为复制所有行；值小于 1 则将此选项重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-168">The default is to copy all rows; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="a92b8-169">BCPLASTEX</span><span class="sxs-lookup"><span data-stu-id="a92b8-169">BCPLASTEX</span></span>  
 <span data-ttu-id="a92b8-170">对于 BCP out 操作，指定要复制到数据文件的数据库表的最后一行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-170">For BCP out operations, specifies the last row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="a92b8-171">对于 BCP in 操作，指定要复制到数据库表的数据文件的最后一行。</span><span class="sxs-lookup"><span data-stu-id="a92b8-171">For BCP in operations, specifies the last row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="a92b8-172">*IValue*参数应为包含值的已签名64位整数的地址。</span><span class="sxs-lookup"><span data-stu-id="a92b8-172">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="a92b8-173">可以传递到 BCPLASTEX 的最大值为 2^63-1。</span><span class="sxs-lookup"><span data-stu-id="a92b8-173">The maximum value that can be passed to BCPLASTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="a92b8-174">BCPMAXERRS</span><span class="sxs-lookup"><span data-stu-id="a92b8-174">BCPMAXERRS</span></span>  
 <span data-ttu-id="a92b8-175">大容量复制操作失败之前允许的错误数。</span><span class="sxs-lookup"><span data-stu-id="a92b8-175">Is the number of errors allowed before the bulk copy operation fails.</span></span> <span data-ttu-id="a92b8-176">默认值为 10;如果值小于1，则将此选项重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-176">The default is 10; a value less than 1 resets this option to its default.</span></span> <span data-ttu-id="a92b8-177">大容量复制将最大错误数限制为 65,535 个。</span><span class="sxs-lookup"><span data-stu-id="a92b8-177">Bulk copy imposes a maximum of 65,535 errors.</span></span> <span data-ttu-id="a92b8-178">如果尝试将该选项设置为大于 65,535 的值，将导致该选项设置为 65,535。</span><span class="sxs-lookup"><span data-stu-id="a92b8-178">An attempt to set this option to a value larger than 65,535 results in the option being set to 65,535.</span></span>  
  
 <span data-ttu-id="a92b8-179">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="a92b8-179">BCPODBC</span></span>  
 <span data-ttu-id="a92b8-180">如果为 TRUE，则指定以字符格式保存的**datetime**和**smalldatetime**值将使用 ODBC 时间戳转义序列前缀和后缀。</span><span class="sxs-lookup"><span data-stu-id="a92b8-180">When TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will use the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="a92b8-181">BCPODBC 选项仅适用于 BCP_OUT。</span><span class="sxs-lookup"><span data-stu-id="a92b8-181">The BCPODBC option only applies to BCP_OUT.</span></span>  
  
 <span data-ttu-id="a92b8-182">为 FALSE 时，表示1997年1月1日的**日期时间**值将转换为字符串： 1997-01-01 00：00：00.000。</span><span class="sxs-lookup"><span data-stu-id="a92b8-182">When FALSE, a **datetime** value representing January 1, 1997 is converted to the character string: 1997-01-01 00:00:00.000.</span></span> <span data-ttu-id="a92b8-183">如果为 TRUE，则将相同的**日期时间**值表示为： {ts ' 1997-01-01 00：00： 00.000 '}。</span><span class="sxs-lookup"><span data-stu-id="a92b8-183">When TRUE, the same **datetime** value is represented as: {ts '1997-01-01 00:00:00.000'}.</span></span>  
  
 <span data-ttu-id="a92b8-184">BCPROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="a92b8-184">BCPROWCOUNT</span></span>  
 <span data-ttu-id="a92b8-185">返回当前（或上一次）BCP 操作所影响的行数。</span><span class="sxs-lookup"><span data-stu-id="a92b8-185">Returns the number of rows affected by the current (or last) BCP operation.</span></span>  
  
 <span data-ttu-id="a92b8-186">BCPTEXTFILE</span><span class="sxs-lookup"><span data-stu-id="a92b8-186">BCPTEXTFILE</span></span>  
 <span data-ttu-id="a92b8-187">如果为 TRUE，则指定数据文件为文本文件，而非二进制文件。</span><span class="sxs-lookup"><span data-stu-id="a92b8-187">When TRUE, specifies that the data file is a text file, rather than a binary file.</span></span> <span data-ttu-id="a92b8-188">如果该文件为文本文件，BCP 将通过检查数据文件的前两个字节中的 Unicode 字节标记来确定该文件是否是 Unicode 文件。</span><span class="sxs-lookup"><span data-stu-id="a92b8-188">If the file is a text file, BCP determines whether or not it is Unicode by checking the Unicode byte marker in the first two bytes of the data file.</span></span>  
  
 <span data-ttu-id="a92b8-189">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="a92b8-189">BCPUNICODEFILE</span></span>  
 <span data-ttu-id="a92b8-190">如果为 TRUE，则指定输入文件是 Unicode 文件。</span><span class="sxs-lookup"><span data-stu-id="a92b8-190">When TRUE, specifies the input file is a Unicode file.</span></span>  
  
 <span data-ttu-id="a92b8-191">*iValue*</span><span class="sxs-lookup"><span data-stu-id="a92b8-191">*iValue*</span></span>  
 <span data-ttu-id="a92b8-192">指定的*eOption*的值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-192">Is the value for the specified *eOption*.</span></span> <span data-ttu-id="a92b8-193">*iValue*是一个整数 (LONGLONG) 值强制转换为 void 指针，以允许将来扩展到64位值。</span><span class="sxs-lookup"><span data-stu-id="a92b8-193">*iValue* is an integer (LONGLONG) value cast to a void pointer to allow for future expansion to 64 bit values.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a92b8-194">返回</span><span class="sxs-lookup"><span data-stu-id="a92b8-194">Returns</span></span>  
 <span data-ttu-id="a92b8-195">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="a92b8-195">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a92b8-196">备注</span><span class="sxs-lookup"><span data-stu-id="a92b8-196">Remarks</span></span>  
 <span data-ttu-id="a92b8-197">此函数设置用于大容量复制操作的各种控制参数，其中包括取消大容量复制之前允许的错误数、要从数据文件中复制的第一批和最后一批的行数和批大小。</span><span class="sxs-lookup"><span data-stu-id="a92b8-197">This function sets various control parameters for bulk-copy operations, including the number of errors allowed before canceling a bulk copy, the numbers of the first and last rows to copy from a data file, and the batch size.</span></span>  
  
 <span data-ttu-id="a92b8-198">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量复制 SELECT 的结果集时，此函数还可用于指定 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="a92b8-198">This function is also used to specify the SELECT statement when bulk copying out from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] the result set of a SELECT.</span></span> <span data-ttu-id="a92b8-199">将*eOption*设置为 BCPHINTS，并将*iValue*设置为具有指向包含 SELECT 语句的 SQLTCHAR 字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="a92b8-199">Set *eOption* to BCPHINTS and set *iValue* to have a pointer to an SQLTCHAR string containing the SELECT statement.</span></span>  
  
 <span data-ttu-id="a92b8-200">仅当在用户文件和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表之间进行复制时，这些控制参数才有意义。</span><span class="sxs-lookup"><span data-stu-id="a92b8-200">These control parameters are only meaningful when copying between a user file and an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="a92b8-201">控制参数设置对使用 bcp_sendrow 复制到的行没有影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="a92b8-201">Control parameter settings have no effect on rows copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a92b8-202">示例</span><span class="sxs-lookup"><span data-stu-id="a92b8-202">Example</span></span>  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="a92b8-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a92b8-203">See Also</span></span>  
 [<span data-ttu-id="a92b8-204">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="a92b8-204">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
