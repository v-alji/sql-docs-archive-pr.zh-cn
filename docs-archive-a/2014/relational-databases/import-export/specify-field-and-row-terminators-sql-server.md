---
title: 指定字段终止符和行终止符 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], terminators
- field terminators [SQL Server]
- data formats [SQL Server], terminators
- row terminators [SQL Server]
- terminators [SQL Server]
ms.assetid: f68b6782-f386-4947-93c4-e89110800704
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 548beeae68f5585c5cf2ba56b67027532ab43b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693359"
---
# <a name="specify-field-and-row-terminators-sql-server"></a><span data-ttu-id="1b44c-102">指定字段终止符和行终止符 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1b44c-102">Specify Field and Row Terminators (SQL Server)</span></span>
  <span data-ttu-id="1b44c-103">对于字符数据字段，可选的终止字符允许在数据文件中使用“字段终止符”  标记每个字段的结尾，以及使用“行终止符”  标记每行的结尾。</span><span class="sxs-lookup"><span data-stu-id="1b44c-103">For character data fields, optional terminating characters allow you to mark the end of each field in a data file with a *field terminator* and the end of each row with a *row terminator*.</span></span> <span data-ttu-id="1b44c-104">终止字符是为读取数据文件的程序指明一个字段或行的结束位置和另一个字段或行的开始位置的一种方式。</span><span class="sxs-lookup"><span data-stu-id="1b44c-104">Terminating characters are one way to indicate to programs that read the data file where one field or row ends and another field or row begins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1b44c-105">使用本机格式或 Unicode 本机格式时，请使用长度前缀而不要使用字段终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-105">When you use native or Unicode native format, use length prefixes rather than field terminators.</span></span> <span data-ttu-id="1b44c-106">本机格式数据可能与终止符冲突，因为本机格式的数据文件是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部二进制数据格式存储的。</span><span class="sxs-lookup"><span data-stu-id="1b44c-106">Native format data can conflict with terminators because a native-format data file is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format.</span></span>  
  
## <a name="characters-supported-as-terminators"></a><span data-ttu-id="1b44c-107">可用作终止符的字符</span><span class="sxs-lookup"><span data-stu-id="1b44c-107">Characters Supported As Terminators</span></span>  
 <span data-ttu-id="1b44c-108">**bcp** 命令、BULK INSERT 语句和 OPENROWSET 大容量行集提供程序支持多种字符作为字段终止符或行终止符，并始终查找每个终止符的第一个实例。</span><span class="sxs-lookup"><span data-stu-id="1b44c-108">The **bcp** command, BULK INSERT statement, and the OPENROWSET bulk rowset provider support a variety of characters as field or row terminators and always look for the first instance of each terminator.</span></span> <span data-ttu-id="1b44c-109">下表列出了支持的终止符字符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-109">The following table lists the supported characters for terminators.</span></span>  
  
|<span data-ttu-id="1b44c-110">终止字符</span><span class="sxs-lookup"><span data-stu-id="1b44c-110">Terminating character</span></span>|<span data-ttu-id="1b44c-111">表示方法</span><span class="sxs-lookup"><span data-stu-id="1b44c-111">Indicated by</span></span>|  
|---------------------------|------------------|  
|<span data-ttu-id="1b44c-112">选项卡</span><span class="sxs-lookup"><span data-stu-id="1b44c-112">Tab</span></span>|<span data-ttu-id="1b44c-113">\t</span><span class="sxs-lookup"><span data-stu-id="1b44c-113">\t</span></span><br /><br /> <span data-ttu-id="1b44c-114">这是默认的字段终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-114">This is the default field terminator.</span></span>|  
|<span data-ttu-id="1b44c-115">换行符</span><span class="sxs-lookup"><span data-stu-id="1b44c-115">Newline character</span></span>|<span data-ttu-id="1b44c-116">\n</span><span class="sxs-lookup"><span data-stu-id="1b44c-116">\n</span></span><br /><br /> <span data-ttu-id="1b44c-117">这是默认的行终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-117">This is the default row terminator.</span></span>|  
|<span data-ttu-id="1b44c-118">回车符/换行符</span><span class="sxs-lookup"><span data-stu-id="1b44c-118">Carriage return/line feed</span></span>|<span data-ttu-id="1b44c-119">\r</span><span class="sxs-lookup"><span data-stu-id="1b44c-119">\r</span></span>|  
|<span data-ttu-id="1b44c-120">反斜杠<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1b44c-120">Backslash<sup>1</sup></span></span>|\\\|  
|<span data-ttu-id="1b44c-121">空终止符 (不可见终止符) <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="1b44c-121">Null terminator (nonvisible terminator)<sup>2</sup></span></span>|<span data-ttu-id="1b44c-122">\0</span><span class="sxs-lookup"><span data-stu-id="1b44c-122">\0</span></span>|  
|<span data-ttu-id="1b44c-123">任何可打印的字符（控制字符是不可打印的，除空值、制表符、换行符和回车之外）</span><span class="sxs-lookup"><span data-stu-id="1b44c-123">Any printable character (control characters are not printable, except null, tab, newline, and carriage return)</span></span>|<span data-ttu-id="1b44c-124">（\*、A、t、l 等）</span><span class="sxs-lookup"><span data-stu-id="1b44c-124">(\*, A, t, l, and so on)</span></span>|  
|<span data-ttu-id="1b44c-125">最长可达 10 个可打印字符的字符串，包括上面列出的部分或全部终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-125">String of up to 10 printable characters, including some or all of the terminators listed earlier</span></span>|<span data-ttu-id="1b44c-126">（\*\*\t\*\*、end、!!!!!!!!!!、\t-\n 等）</span><span class="sxs-lookup"><span data-stu-id="1b44c-126">(\*\*\t\*\*, end, !!!!!!!!!!, \t-\n, and so on)</span></span>|  
  
 <span data-ttu-id="1b44c-127"><sup>1</sup>只有 t、n、r、0和 ' \ 0 ' 字符与反斜杠转义字符一起使用才能生成控制字符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-127"><sup>1</sup> Only the t, n, r, 0 and '\0' characters work with the backslash escape character to produce a control character.</span></span>  
  
 <span data-ttu-id="1b44c-128"><sup>2</sup>即使在打印时 null 控制字符 ( \ 0) ，它也是数据文件中的非重复字符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-128"><sup>2</sup> Even though the null control character (\0) is not visible when printed, it is a distinct character in the data file.</span></span> <span data-ttu-id="1b44c-129">这表示使用空控制字符作为字段终止符或行终止符与根本没有字段终止符或行终止符是不同的。</span><span class="sxs-lookup"><span data-stu-id="1b44c-129">This means that using the null control character as a field or row terminator is different than having no field or row terminator at all.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1b44c-130">如果数据中出现终止符字符，则它被视为终止符（而非数据），并且该字符后的数据被视为属于下一个字段或记录。</span><span class="sxs-lookup"><span data-stu-id="1b44c-130">If a terminator character occurs within the data, it is interpreted as a terminator, not as data, and the data after that character is interpreted as belonging to the next field or record.</span></span> <span data-ttu-id="1b44c-131">因此，请仔细选择您的终止符，以确保它们从未出现在您的数据中。</span><span class="sxs-lookup"><span data-stu-id="1b44c-131">Therefore, choose your terminators carefully to make sure that they never appear in your data.</span></span> <span data-ttu-id="1b44c-132">例如，如果数据中包含某个低代理项，则低代理项字段终止符并不是一个好的选择。</span><span class="sxs-lookup"><span data-stu-id="1b44c-132">For example, a low surrogate field terminator would not be a good choice for a field terminator if the data contains that low surrogate.</span></span>  
  
## <a name="using-row-terminators"></a><span data-ttu-id="1b44c-133">使用行终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-133">Using Row Terminators</span></span>  
 <span data-ttu-id="1b44c-134">行终止符可以与最后一个字段的终止符相同。</span><span class="sxs-lookup"><span data-stu-id="1b44c-134">The row terminator can be the same character as the terminator for the last field.</span></span> <span data-ttu-id="1b44c-135">但是，通常来说，非重复的终止符是很有用的。</span><span class="sxs-lookup"><span data-stu-id="1b44c-135">Generally, however, a distinct row terminator is useful.</span></span> <span data-ttu-id="1b44c-136">例如，若要生成表格格式的输出，可用换行符 (\n) 终止每行的最后一个字段，并用制表符 (\t) 终止所有其他字段。</span><span class="sxs-lookup"><span data-stu-id="1b44c-136">For example, to produce tabular output, terminate the last field in each row with the newline character (\n) and all other fields with the tab character (\t).</span></span> <span data-ttu-id="1b44c-137">若要将每个数据记录放置在数据文件中的各自的行上，请指定 \r\n 组合作为行终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-137">To place each data record on its own line in the data file, specify the combination \r\n as the row terminator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b44c-138">交互使用 **bcp** 并指定 \n（换行符）作为行终止符时， **bcp** 将自动以 \r（回车符）作为前缀，从而形成行终止符 \r\n。</span><span class="sxs-lookup"><span data-stu-id="1b44c-138">When you use **bcp** interactively and specify \n (newline) as the row terminator, **bcp** automatically prefixes it with a \r (carriage return) character, which results in a row terminator of \r\n.</span></span>  
  
## <a name="specifying-terminators-for-bulk-export"></a><span data-ttu-id="1b44c-139">指定大容量导出的终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-139">Specifying Terminators for Bulk Export</span></span>  
 <span data-ttu-id="1b44c-140">大容量导出 `char` 或 `nchar` 数据，并且希望使用非默认终止符时，必须为**bcp**命令指定终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-140">When you bulk export `char` or `nchar` data, and want to use a non-default terminator, you must specify the terminator to the **bcp** command.</span></span> <span data-ttu-id="1b44c-141">可以用下列任一方式指定终止符：</span><span class="sxs-lookup"><span data-stu-id="1b44c-141">You can specify terminators in any of the following ways:</span></span>  
  
-   <span data-ttu-id="1b44c-142">使用格式化文件逐个字段指定终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-142">With a format file that specifies the terminator on a field-by-field basis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1b44c-143">有关如何使用格式化文件的详细信息，请参阅[导入或导出数据的格式化文件 (SQL Server)](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-143">For information about how to use format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1b44c-144">不使用格式化文件，但有下列可选方式：</span><span class="sxs-lookup"><span data-stu-id="1b44c-144">Without a format file, the following alternatives exist:</span></span>  
  
    -   <span data-ttu-id="1b44c-145">使用 **-t** 开关为行中的所有字段（除最后一个字段以外）指定行终止符，并使用 **-r** 开关指定行终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-145">Using the **-t** switch to specify the row terminator for all the fields except the last field in the row and using the **-r** switch to specify a row terminator.</span></span>  
  
    -   <span data-ttu-id="1b44c-146">使用字符格式开关 **-c** 或 **-w**（而不是 **-t** 开关）将字段终止符设置为制表符 \t。</span><span class="sxs-lookup"><span data-stu-id="1b44c-146">Using a character-format switch (**-c** or **-w**) without the **-t** switch, which sets the field terminator to the tab character, \t.</span></span> <span data-ttu-id="1b44c-147">这与指定 **-t**\t 的作用相同。</span><span class="sxs-lookup"><span data-stu-id="1b44c-147">This is the same as specifying **-t**\t.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1b44c-148">如果指定了 **-n** （本机数据）或 **-N** （Unicode 本机）开关，则不会插入终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-148">If you specify the **-n** (native data) or **-N** (Unicode native) switch, terminators are not inserted.</span></span>  
  
    -   <span data-ttu-id="1b44c-149">如果交互 **bcp** 命令包含 **in** 或 **out** 选项，而不包含格式化文件开关 ( **-f**) 或数据格式开关（ **-n**、 **-c**、 **-w**或 **-N**），并且选择不指定前缀长度和字段长度，则每个字段的字段终止符的命令提示符默认为无：</span><span class="sxs-lookup"><span data-stu-id="1b44c-149">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), and you have chosen not to specify prefix length and field length, the command prompts for the field terminator of each field, with a default of none:</span></span>  
  
         `Enter field terminator [none]:`  
  
         <span data-ttu-id="1b44c-150">通常，默认设置是适当的选择。</span><span class="sxs-lookup"><span data-stu-id="1b44c-150">Generally, the default is a suitable choice.</span></span> <span data-ttu-id="1b44c-151">但是，有关 `char` 或 `nchar` 数据字段，请参阅下一节“使用终止符指南”。</span><span class="sxs-lookup"><span data-stu-id="1b44c-151">However, for `char` or `nchar` data fields, see the following subsection, "Guidelines for Using Terminators."</span></span> <span data-ttu-id="1b44c-152">有关在上下文中显示此提示符的示例，请参阅[在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-152">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1b44c-153">在你以交互方式指定 **bcp** 命令中的所有字段后，该命令会提示你将自己对每个字段的响应保存到一个非 XML 格式化文件中。</span><span class="sxs-lookup"><span data-stu-id="1b44c-153">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="1b44c-154">有关非 XML 格式文件的详细信息，请参阅[非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-154">For more information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="guidelines-for-using-terminators"></a><span data-ttu-id="1b44c-155">使用终止符指南</span><span class="sxs-lookup"><span data-stu-id="1b44c-155">Guidelines for Using Terminators</span></span>  
 <span data-ttu-id="1b44c-156">在某些情况下，终止符对 `char` 或 `nchar` 数据字段是很有用的。</span><span class="sxs-lookup"><span data-stu-id="1b44c-156">In some situations, a terminator is useful for a `char` or `nchar` data field.</span></span> <span data-ttu-id="1b44c-157">例如：</span><span class="sxs-lookup"><span data-stu-id="1b44c-157">For example:</span></span>  
  
-   <span data-ttu-id="1b44c-158">对于数据文件中包含 null 值的数据列，将不会被导入到不能理解前缀长度信息的程序中。</span><span class="sxs-lookup"><span data-stu-id="1b44c-158">For a data column that contains a null value in a data file that will be imported into a program that does not understand the prefix length information.</span></span>  
  
     <span data-ttu-id="1b44c-159">包含 null 值的任何数据列都被认为是可变长度。</span><span class="sxs-lookup"><span data-stu-id="1b44c-159">Any data column that contains a null value is considered variable length.</span></span> <span data-ttu-id="1b44c-160">如果缺少前缀长度，则需要一个终止符来确定 null 字段的结尾，同时确保正确地解释数据。</span><span class="sxs-lookup"><span data-stu-id="1b44c-160">In the absence of prefix lengths, a terminator is necessary to identify the end of a null field, making sure that the data is correctly interpreted.</span></span>  
  
-   <span data-ttu-id="1b44c-161">对于其空间只被许多行部分占用的固定长度的长列。</span><span class="sxs-lookup"><span data-stu-id="1b44c-161">For a long fixed-length column whose space is only partially used by many rows.</span></span>  
  
     <span data-ttu-id="1b44c-162">在这种情况下，指定一个终止符可以最大限度地减少存储空间，同时可以将字段视为可变长度字段。</span><span class="sxs-lookup"><span data-stu-id="1b44c-162">In this situation, specifying a terminator can minimize storage space allowing the field to be treated as a variable-length field.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1b44c-163">示例</span><span class="sxs-lookup"><span data-stu-id="1b44c-163">Examples</span></span>  
 <span data-ttu-id="1b44c-164">此示例使用字符格式将 `AdventureWorks``HumanResources.Department` 表中的数据批量导出至 `Department-c-t.txt` 数据文件，其中将逗号用作字段终止符，将换行符 (\n) 用作行终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-164">This example bulk exports the data from the `AdventureWorks``HumanResources.Department` table to the `Department-c-t.txt` data file using character format, with a comma as a field terminator and the newline character (\n) as the row terminator.</span></span>  
  
 <span data-ttu-id="1b44c-165">**bcp** 命令包含以下开关。</span><span class="sxs-lookup"><span data-stu-id="1b44c-165">The **bcp** command contains the following switches.</span></span>  
  
|<span data-ttu-id="1b44c-166">开关</span><span class="sxs-lookup"><span data-stu-id="1b44c-166">Switch</span></span>|<span data-ttu-id="1b44c-167">说明</span><span class="sxs-lookup"><span data-stu-id="1b44c-167">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1b44c-168">**-c**</span><span class="sxs-lookup"><span data-stu-id="1b44c-168">**-c**</span></span>|<span data-ttu-id="1b44c-169">指定将数据字段作为字符数据加载。</span><span class="sxs-lookup"><span data-stu-id="1b44c-169">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="1b44c-170">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="1b44c-170">**-t** `,`</span></span>|<span data-ttu-id="1b44c-171">指定逗号 (,) 作为字段终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-171">Specifies a comma (,) as the field terminator.</span></span>|  
|<span data-ttu-id="1b44c-172">**-r** \n</span><span class="sxs-lookup"><span data-stu-id="1b44c-172">**-r** \n</span></span>|<span data-ttu-id="1b44c-173">指定行终止符作为换行符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-173">Specifies the row terminator as a newline character.</span></span> <span data-ttu-id="1b44c-174">这是默认的行终止符，因此将其指定为可选。</span><span class="sxs-lookup"><span data-stu-id="1b44c-174">This is the default row terminator, so specifying it is optional.</span></span>|  
|<span data-ttu-id="1b44c-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="1b44c-175">**-T**</span></span>|<span data-ttu-id="1b44c-176">指定 **bcp** 实用工具通过使用集成安全性的受信任连接连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1b44c-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="1b44c-177">如果未指定 **-T** ，则需要指定 **-U** 和 **-P** 才能成功登录。</span><span class="sxs-lookup"><span data-stu-id="1b44c-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="1b44c-178">有关详细信息，请参阅 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-178">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="1b44c-179">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="1b44c-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out C:\myDepartment-c-t.txt -c -t, -r \n -T  
```  
  
 <span data-ttu-id="1b44c-180">这创建了 `Department-c-t.txt`，其中包含 16 条记录，每条记录有四个字段。</span><span class="sxs-lookup"><span data-stu-id="1b44c-180">This creates `Department-c-t.txt`, which contains 16 records with four fields each.</span></span> <span data-ttu-id="1b44c-181">这些字段由逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="1b44c-181">The fields are separated by a comma.</span></span>  
  
## <a name="specifying-terminators-for-bulk-import"></a><span data-ttu-id="1b44c-182">为大容量导入指定终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-182">Specifying Terminators for Bulk Import</span></span>  
 <span data-ttu-id="1b44c-183">大容量导入 `char` 或 `nchar` 数据时，大容量导入命令必须识别数据文件中使用的终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-183">When you bulk import `char` or `nchar` data, the bulk-import command must recognize the terminators that are used in the data file.</span></span> <span data-ttu-id="1b44c-184">如何指定终止符依赖于大容量导入命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1b44c-184">How terminators can be specified depends on the bulk-import command, as follows:</span></span>  
  
-   <span data-ttu-id="1b44c-185">**bcp**</span><span class="sxs-lookup"><span data-stu-id="1b44c-185">**bcp**</span></span>  
  
     <span data-ttu-id="1b44c-186">为导入操作指定终止符与为导出操作指定终止符的语法相同。</span><span class="sxs-lookup"><span data-stu-id="1b44c-186">Specifying terminators for an import operation uses the same syntax as for an export operation.</span></span> <span data-ttu-id="1b44c-187">有关详细信息，请参阅本主题前面的“为大容量导出指定终止符”。</span><span class="sxs-lookup"><span data-stu-id="1b44c-187">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
-   <span data-ttu-id="1b44c-188">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="1b44c-188">BULK INSERT</span></span>  
  
     <span data-ttu-id="1b44c-189">使用下表中列出的限定符可以为格式化文件中的各个字段或为整个数据文件指定终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-189">Terminators can be specified for individual fields in a format file or for the whole data file by using the qualifiers shown in the following table.</span></span>  
  
    |<span data-ttu-id="1b44c-190">Qualifier</span><span class="sxs-lookup"><span data-stu-id="1b44c-190">Qualifier</span></span>|<span data-ttu-id="1b44c-191">说明</span><span class="sxs-lookup"><span data-stu-id="1b44c-191">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="1b44c-192">FIELDTERMINATOR **= ' *`field_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="1b44c-192">FIELDTERMINATOR **='*`field_terminator`*'**</span></span>|<span data-ttu-id="1b44c-193">指定用于字符和 Unicode 字符数据文件的字段终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-193">Specifies the field terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="1b44c-194">默认的字段终止符是 \t（制表符）。</span><span class="sxs-lookup"><span data-stu-id="1b44c-194">The default is \t (tab character).</span></span>|  
    |<span data-ttu-id="1b44c-195">ROWTERMINATOR **= ' *`row_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="1b44c-195">ROWTERMINATOR **='*`row_terminator`*'**</span></span>|<span data-ttu-id="1b44c-196">指定用于字符和 Unicode 字符数据文件的行终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-196">Specifies the row terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="1b44c-197">默认的行终止符是 \n（换行符）。</span><span class="sxs-lookup"><span data-stu-id="1b44c-197">The default is \n (newline character).</span></span>|  
  
     <span data-ttu-id="1b44c-198">有关详细信息，请参阅 [BULK INSERT (Transact SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-198">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="1b44c-199">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="1b44c-199">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
     <span data-ttu-id="1b44c-200">对于 OPENROWSET 大容量行集提供程序，仅可以在格式化文件中指定终止符（这是必需的，除大型对象数据类型以外）。</span><span class="sxs-lookup"><span data-stu-id="1b44c-200">For the OPENROWSET bulk rowset provider, terminators can be specified only in the format file (which is required except for large-object data types).</span></span> <span data-ttu-id="1b44c-201">如果字符数据文件使用非默认终止符，则必须在格式化文件中定义该非默认终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-201">If a character data file uses a non-default terminator, it must be defined in the format file.</span></span> <span data-ttu-id="1b44c-202">有关详细信息，请参阅[创建格式化文件 (SQL Server)](create-a-format-file-sql-server.md) 和[使用格式化文件批量导入数据 (SQL Server)](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-202">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) and [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
     <span data-ttu-id="1b44c-203">有关 OPENROWSET BULK 子句的详细信息，请参阅 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1b44c-203">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="1b44c-204">示例</span><span class="sxs-lookup"><span data-stu-id="1b44c-204">Examples</span></span>  
 <span data-ttu-id="1b44c-205">本部分的示例将字符数据从上述示例中创建的 `Department-c-t.txt` 数据文件大容量导入到 `myDepartment` 示例数据库的 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 表中。</span><span class="sxs-lookup"><span data-stu-id="1b44c-205">The examples in this section bulk import character data form the `Department-c-t.txt` data file created in the preceding example into the `myDepartment` table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample database.</span></span> <span data-ttu-id="1b44c-206">必须先创建此表，才能运行这些示例。</span><span class="sxs-lookup"><span data-stu-id="1b44c-206">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="1b44c-207">若要在 **dbo** 架构下创建此表，请在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中执行以下代码：</span><span class="sxs-lookup"><span data-stu-id="1b44c-207">To create this table under the **dbo** schema, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DROP TABLE myDepartment;  
CREATE TABLE myDepartment   
(DepartmentID smallint,  
Name nvarchar(50),  
GroupName nvarchar(50) NULL,  
ModifiedDate datetime not NULL CONSTRAINT DF_AddressType_ModifiedDate DEFAULT (GETDATE())  
);  
GO  
  
```  
  
#### <a name="a-using-bcp-to-interactively-specify-terminators"></a><span data-ttu-id="1b44c-208">A.</span><span class="sxs-lookup"><span data-stu-id="1b44c-208">A.</span></span> <span data-ttu-id="1b44c-209">使用 bcp 交互指定终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-209">Using bcp to interactively specify terminators</span></span>  
 <span data-ttu-id="1b44c-210">以下示例使用 `Department-c-t.txt` 命令大容量导入 `bcp` 数据文件。</span><span class="sxs-lookup"><span data-stu-id="1b44c-210">The following example bulk imports the `Department-c-t.txt` data file using a `bcp` command.</span></span> <span data-ttu-id="1b44c-211">该命令与大容量导出命令使用相同的命令开关。</span><span class="sxs-lookup"><span data-stu-id="1b44c-211">This command uses the same command switches as the bulk export command.</span></span> <span data-ttu-id="1b44c-212">有关详细信息，请参阅本主题前面的“为大容量导出指定终止符”。</span><span class="sxs-lookup"><span data-stu-id="1b44c-212">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
 <span data-ttu-id="1b44c-213">在 Windows 命令提示符下输入：</span><span class="sxs-lookup"><span data-stu-id="1b44c-213">At the Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks..myDepartment in C:\myDepartment-c-t.txt -c -t , -r \n -T  
```  
  
#### <a name="b-using-bulk-insert-to-interactively-specify-terminators"></a><span data-ttu-id="1b44c-214">B.</span><span class="sxs-lookup"><span data-stu-id="1b44c-214">B.</span></span> <span data-ttu-id="1b44c-215">使用 BULK INSERT 交互指定终止符</span><span class="sxs-lookup"><span data-stu-id="1b44c-215">Using BULK INSERT to interactively specify terminators</span></span>  
 <span data-ttu-id="1b44c-216">以下示例使用 `Department-c-t.txt` 语句大容量导入 `BULK INSERT` 数据文件，该语句使用了下表中所示的限定符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-216">The following example bulk imports the `Department-c-t.txt` data file using a `BULK INSERT` statement that uses the qualifiers shown in the following table.</span></span>  
  
|<span data-ttu-id="1b44c-217">选项</span><span class="sxs-lookup"><span data-stu-id="1b44c-217">Option</span></span>|<span data-ttu-id="1b44c-218">Attribute</span><span class="sxs-lookup"><span data-stu-id="1b44c-218">Attribute</span></span>|  
|------------|---------------|  
|<span data-ttu-id="1b44c-219">DATAFILETYPE **= ' `char` '**</span><span class="sxs-lookup"><span data-stu-id="1b44c-219">DATAFILETYPE **='`char`'**</span></span>|<span data-ttu-id="1b44c-220">指定将数据字段作为字符数据加载。</span><span class="sxs-lookup"><span data-stu-id="1b44c-220">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="1b44c-221">FIELDTERMINATOR **='** `,` **'**</span><span class="sxs-lookup"><span data-stu-id="1b44c-221">FIELDTERMINATOR **='**`,`**'**</span></span>|<span data-ttu-id="1b44c-222">将逗号 (`,`) 指定为字段终止符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-222">Specifies a comma (`,`) as the field terminator.</span></span>|  
|<span data-ttu-id="1b44c-223">ROWTERMINATOR **='** `\n` **'**</span><span class="sxs-lookup"><span data-stu-id="1b44c-223">ROWTERMINATOR **='**`\n`**'**</span></span>|<span data-ttu-id="1b44c-224">指定行终止符作为换行符。</span><span class="sxs-lookup"><span data-stu-id="1b44c-224">Specifies the row terminator as a newline character.</span></span>|  
  
 <span data-ttu-id="1b44c-225">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查询编辑器中，执行以下代码：</span><span class="sxs-lookup"><span data-stu-id="1b44c-225">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myDepartment FROM 'C:\myDepartment-c-t.txt'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      ROWTERMINATOR = '\n'  
);  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b44c-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b44c-226">See Also</span></span>  
 <span data-ttu-id="1b44c-227">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1b44c-227">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="1b44c-228">[BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b44c-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="1b44c-229">[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b44c-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="1b44c-230">[使用 bcp 指定字段长度 (SQL Server)](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1b44c-230">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="1b44c-231">[使用 bcp 指定数据文件中的前缀长度 (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1b44c-231">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="1b44c-232">使用 bcp 指定文件存储类型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1b44c-232">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
