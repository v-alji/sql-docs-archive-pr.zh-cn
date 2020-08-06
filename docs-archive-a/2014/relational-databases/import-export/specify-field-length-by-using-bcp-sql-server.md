---
title: 使用 bcp 指定字段长度 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13343b4f3778df1bbe7ef1c99b3d06338f18631c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687884"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a><span data-ttu-id="77a76-102">使用 bcp 指定字段长度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="77a76-102">Specify Field Length by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="77a76-103">字段长度指示以字符格式表示数据时所要求的最大字符数。</span><span class="sxs-lookup"><span data-stu-id="77a76-103">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="77a76-104">如果数据以本机格式存储，则字段长度就是已知的，例如，`int` 数据类型占 4 个字节。</span><span class="sxs-lookup"><span data-stu-id="77a76-104">The field length is already known if the data is stored in the native format; for example, the `int` data type takes 4 bytes.</span></span> <span data-ttu-id="77a76-105">如果为前缀长度指定了0，则**bcp**命令会提示输入字段长度、默认字段长度以及字段长度对包含数据的数据文件中数据存储的影响 `char` 。</span><span class="sxs-lookup"><span data-stu-id="77a76-105">If you have indicated 0 for the prefix length, the **bcp** command prompts you for field length, the default field lengths, and the impact of field-length on data storage in data files that contain `char` data.</span></span>  
  
## <a name="the-bcp-prompt-for-field-length"></a><span data-ttu-id="77a76-106">bcp 提示输入字段长度</span><span class="sxs-lookup"><span data-stu-id="77a76-106">The bcp Prompt for Field Length</span></span>  
 <span data-ttu-id="77a76-107">如果某个交互式 **bcp** 命令包含不带格式化文件开关 ( **-f**) 或数据格式开关（ **-n**、 **-c**、 **-w** 或 **-N**）的 **in** 或 **out** 选项，则该命令会提示输入每个数据字段的字段长度，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77a76-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the field length of each data field, as follows:</span></span>  
  
 `Enter length of field <field_name> [<default>]:`  
  
 <span data-ttu-id="77a76-108">有关在上下文中显示此提示符的示例，请参阅[在使用 bcp 时指定数据格式以获得兼容性 (SQL Server)](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77a76-108">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77a76-109">在你以交互方式指定 **bcp** 命令中的所有字段后，该命令会提示你将自己对每个字段的响应保存到一个非 XML 格式化文件中。</span><span class="sxs-lookup"><span data-stu-id="77a76-109">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="77a76-110">有关非 XML 格式文件的详细信息，请参阅[ 非 XML 格式化文件 (SQL Server)](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77a76-110">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 <span data-ttu-id="77a76-111">**bcp** 命令是否提示输入字段长度取决于若干因素，如下所示：</span><span class="sxs-lookup"><span data-stu-id="77a76-111">Whether a **bcp** command prompts for field length depends on several factors, as follows:</span></span>  
  
-   <span data-ttu-id="77a76-112">当复制非固定长度的数据类型并指定前缀长度为 0 时， **bcp** 命令会提示输入字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-112">When you copy data types that are not of fixed length and you specify a prefix length of 0, **bcp** prompts for a field length.</span></span>  
  
-   <span data-ttu-id="77a76-113">当将非字符数据转换为字符数据时， **bcp** 会建议一个足以存储该数据的默认字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-113">When converting noncharacter data to character data, **bcp** suggests a default field length large enough to store the data.</span></span>  
  
-   <span data-ttu-id="77a76-114">如果文件存储类型为非字符类型，则 **bcp** 命令不会提示输入字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-114">If the file storage type is noncharacter, the **bcp** command does not prompt for a field length.</span></span> <span data-ttu-id="77a76-115">数据将以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机数据表示形式（本机格式）存储。</span><span class="sxs-lookup"><span data-stu-id="77a76-115">The data is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data representation (native format).</span></span>  
  
## <a name="using-default-field-lengths"></a><span data-ttu-id="77a76-116">使用默认字段长度</span><span class="sxs-lookup"><span data-stu-id="77a76-116">Using Default Field Lengths</span></span>  
 <span data-ttu-id="77a76-117">通常， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 会建议你接受 **bcp**建议的默认字段长度值。</span><span class="sxs-lookup"><span data-stu-id="77a76-117">Generally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you accept the **bcp**-suggested default values for the field length.</span></span> <span data-ttu-id="77a76-118">如果已创建了字符模式数据文件，则使用默认字段长度可确保数据不会被截断，并且不会发生数字溢出错误。</span><span class="sxs-lookup"><span data-stu-id="77a76-118">When a character mode data file is created, using the default field length ensures that data is not truncated and that numeric overflow errors do not occur.</span></span>  
  
 <span data-ttu-id="77a76-119">如果指定的字段长度不正确，可能会发生问题。</span><span class="sxs-lookup"><span data-stu-id="77a76-119">If you specify a field length that is incorrect, problems can occur.</span></span> <span data-ttu-id="77a76-120">例如，当复制数字数据并且为该数据指定的字段长度过短时， **bcp** 实用工具将显示一条溢出消息而不复制数据。</span><span class="sxs-lookup"><span data-stu-id="77a76-120">For instance, if you copy numeric data and you specify a field length that is too short for the data, the **bcp** utility prints an overflow message and does not copy the data.</span></span> <span data-ttu-id="77a76-121">此外，如果导出 `datetime` 数据并为字符串指定小于26个字节的字段长度， **bcp**实用工具将截断数据而不会出现错误消息。</span><span class="sxs-lookup"><span data-stu-id="77a76-121">Also, if you export `datetime` data and specify a field length of less than 26 bytes for the character string, the **bcp** utility truncates the data without an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="77a76-122">使用默认大小选项时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 需要读取整个字符串。</span><span class="sxs-lookup"><span data-stu-id="77a76-122">When the default size option is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expects to read an entire string.</span></span> <span data-ttu-id="77a76-123">在某些情况下，使用默认字段长度可能导致“意外的文件结尾”错误。</span><span class="sxs-lookup"><span data-stu-id="77a76-123">In some situations, use of a default field length can lead to an "unexpected end of file" error.</span></span> <span data-ttu-id="77a76-124">通常情况下， `money` `datetime` 如果数据文件中只出现了所需字段的一部分，则与和数据类型发生此错误; 例如，如果 `datetime` 指定的值不是时间部分，而是指定*的值* / *dd* / *yy*小于格式的值的预期24个字符长度 `datetime` `char` 。</span><span class="sxs-lookup"><span data-stu-id="77a76-124">Typically, this error occurs with the `money` and `datetime` data types when only part of the expected field occurs in the data file; for example, when a `datetime` value of *mm*/*dd*/*yy* is specified without the time component and is, therefore, shorter than the expected 24 character length of a `datetime` value in `char` format.</span></span> <span data-ttu-id="77a76-125">若要避免此类错误，请使用字段终止符或具有固定长度的数据字段，或者通过指定其他值来更改默认字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-125">To avoid this type of error, use field terminators or fixed-length data fields, or change the default field length by specifying another value.</span></span>  
  
### <a name="default-field-lengths-for-character-file-storage"></a><span data-ttu-id="77a76-126">字符文件存储的默认字段长度</span><span class="sxs-lookup"><span data-stu-id="77a76-126">Default Field Lengths for Character File Storage</span></span>  
 <span data-ttu-id="77a76-127">下表列出了要存储为字符文件存储类型的数据的默认字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-127">The following table lists the default field lengths for data to be stored as a character-file storage type.</span></span> <span data-ttu-id="77a76-128">可为空值的数据与非空数据的长度相同。</span><span class="sxs-lookup"><span data-stu-id="77a76-128">Nullable data is the same length as nonnull data.</span></span>  
  
|<span data-ttu-id="77a76-129">数据类型</span><span class="sxs-lookup"><span data-stu-id="77a76-129">Data type</span></span>|<span data-ttu-id="77a76-130">默认长度（字符数）</span><span class="sxs-lookup"><span data-stu-id="77a76-130">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`char`|<span data-ttu-id="77a76-131">定义的列长度</span><span class="sxs-lookup"><span data-stu-id="77a76-131">Length defined for the column</span></span>|  
|`varchar`|<span data-ttu-id="77a76-132">定义的列长度</span><span class="sxs-lookup"><span data-stu-id="77a76-132">Length defined for the column</span></span>|  
|`nchar`|<span data-ttu-id="77a76-133">定义的列长度的两倍</span><span class="sxs-lookup"><span data-stu-id="77a76-133">Twice the length defined for the column</span></span>|  
|`nvarchar`|<span data-ttu-id="77a76-134">定义的列长度的两倍</span><span class="sxs-lookup"><span data-stu-id="77a76-134">Twice the length defined for the column</span></span>|  
|`Text`|<span data-ttu-id="77a76-135">0</span><span class="sxs-lookup"><span data-stu-id="77a76-135">0</span></span>|  
|`ntext`|<span data-ttu-id="77a76-136">0</span><span class="sxs-lookup"><span data-stu-id="77a76-136">0</span></span>|  
|`bit`|<span data-ttu-id="77a76-137">1</span><span class="sxs-lookup"><span data-stu-id="77a76-137">1</span></span>|  
|`binary`|<span data-ttu-id="77a76-138">定义的列长度的两倍 + 1</span><span class="sxs-lookup"><span data-stu-id="77a76-138">Twice the length defined for the column + 1</span></span>|  
|`varbinary`|<span data-ttu-id="77a76-139">定义的列长度的两倍 + 1</span><span class="sxs-lookup"><span data-stu-id="77a76-139">Twice the length defined for the column + 1</span></span>|  
|`image`|<span data-ttu-id="77a76-140">0</span><span class="sxs-lookup"><span data-stu-id="77a76-140">0</span></span>|  
|`datetime`|<span data-ttu-id="77a76-141">24</span><span class="sxs-lookup"><span data-stu-id="77a76-141">24</span></span>|  
|`smalldatetime`|<span data-ttu-id="77a76-142">24</span><span class="sxs-lookup"><span data-stu-id="77a76-142">24</span></span>|  
|`float`|<span data-ttu-id="77a76-143">30</span><span class="sxs-lookup"><span data-stu-id="77a76-143">30</span></span>|  
|`real`|<span data-ttu-id="77a76-144">30</span><span class="sxs-lookup"><span data-stu-id="77a76-144">30</span></span>|  
|`int`|<span data-ttu-id="77a76-145">12</span><span class="sxs-lookup"><span data-stu-id="77a76-145">12</span></span>|  
|`bigint`|<span data-ttu-id="77a76-146">19</span><span class="sxs-lookup"><span data-stu-id="77a76-146">19</span></span>|  
|`smallint`|<span data-ttu-id="77a76-147">7</span><span class="sxs-lookup"><span data-stu-id="77a76-147">7</span></span>|  
|`tinyint`|<span data-ttu-id="77a76-148">5</span><span class="sxs-lookup"><span data-stu-id="77a76-148">5</span></span>|  
|`money`|<span data-ttu-id="77a76-149">30</span><span class="sxs-lookup"><span data-stu-id="77a76-149">30</span></span>|  
|`smallmoney`|<span data-ttu-id="77a76-150">30</span><span class="sxs-lookup"><span data-stu-id="77a76-150">30</span></span>|  
|`decimal`|<span data-ttu-id="77a76-151">41\*</span><span class="sxs-lookup"><span data-stu-id="77a76-151">41\*</span></span>|  
|`numeric`|<span data-ttu-id="77a76-152">41\*</span><span class="sxs-lookup"><span data-stu-id="77a76-152">41\*</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="77a76-153">37</span><span class="sxs-lookup"><span data-stu-id="77a76-153">37</span></span>|  
|`timestamp`|<span data-ttu-id="77a76-154">17</span><span class="sxs-lookup"><span data-stu-id="77a76-154">17</span></span>|  
|`varchar(max)`|<span data-ttu-id="77a76-155">0</span><span class="sxs-lookup"><span data-stu-id="77a76-155">0</span></span>|  
|`varbinary(max)`|<span data-ttu-id="77a76-156">0</span><span class="sxs-lookup"><span data-stu-id="77a76-156">0</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="77a76-157">0</span><span class="sxs-lookup"><span data-stu-id="77a76-157">0</span></span>|  
|<span data-ttu-id="77a76-158">UDT</span><span class="sxs-lookup"><span data-stu-id="77a76-158">UDT</span></span>|<span data-ttu-id="77a76-159">用户定义的字词 (UDT) 列长度</span><span class="sxs-lookup"><span data-stu-id="77a76-159">Length of the user-defined term (UDT) column</span></span>|  
|<span data-ttu-id="77a76-160">XML</span><span class="sxs-lookup"><span data-stu-id="77a76-160">XML</span></span>|<span data-ttu-id="77a76-161">0</span><span class="sxs-lookup"><span data-stu-id="77a76-161">0</span></span>|  
  
 <span data-ttu-id="77a76-162">\*有关 `decimal` 和数据类型的详细信息 `numeric` ，请参阅[decimal 和 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="77a76-162">\*For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77a76-163">`tinyint` 类型的列的值介于 0 到 255 之间；表示该范围内的任意数值所需的最大字符数是三（用于表示 100 到 255 之间的值）。</span><span class="sxs-lookup"><span data-stu-id="77a76-163">A column of type `tinyint` can have values from 0 through 255; the maximum number of characters that are needed to represent any number in that range is three (representing values 100 through 255).</span></span>  
  
### <a name="default-field-lengths-for-native-file-storage"></a><span data-ttu-id="77a76-164">本机文件存储的默认字段长度</span><span class="sxs-lookup"><span data-stu-id="77a76-164">Default Field Lengths for Native File Storage</span></span>  
 <span data-ttu-id="77a76-165">下表列出了要存储为本机文件存储类型的数据的默认字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-165">The following table lists the default field lengths for data to be stored as native file storage type.</span></span> <span data-ttu-id="77a76-166">可为空值的数据与非空数据的长度相同，并且字符数据始终以字符格式存储。</span><span class="sxs-lookup"><span data-stu-id="77a76-166">Nullable data is the same length as nonnull data, and character data is always stored in character format.</span></span>  
  
|<span data-ttu-id="77a76-167">数据类型</span><span class="sxs-lookup"><span data-stu-id="77a76-167">Data type</span></span>|<span data-ttu-id="77a76-168">默认长度（字符数）</span><span class="sxs-lookup"><span data-stu-id="77a76-168">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`bit`|<span data-ttu-id="77a76-169">1</span><span class="sxs-lookup"><span data-stu-id="77a76-169">1</span></span>|  
|`binary`|<span data-ttu-id="77a76-170">定义的列长度</span><span class="sxs-lookup"><span data-stu-id="77a76-170">Length defined for the column</span></span>|  
|`varbinary`|<span data-ttu-id="77a76-171">定义的列长度</span><span class="sxs-lookup"><span data-stu-id="77a76-171">Length defined for the column</span></span>|  
|`image`|<span data-ttu-id="77a76-172">0</span><span class="sxs-lookup"><span data-stu-id="77a76-172">0</span></span>|  
|`datetime`|<span data-ttu-id="77a76-173">8</span><span class="sxs-lookup"><span data-stu-id="77a76-173">8</span></span>|  
|`smalldatetime`|<span data-ttu-id="77a76-174">4</span><span class="sxs-lookup"><span data-stu-id="77a76-174">4</span></span>|  
|`float`|<span data-ttu-id="77a76-175">8</span><span class="sxs-lookup"><span data-stu-id="77a76-175">8</span></span>|  
|`real`|<span data-ttu-id="77a76-176">4</span><span class="sxs-lookup"><span data-stu-id="77a76-176">4</span></span>|  
|`int`|<span data-ttu-id="77a76-177">4</span><span class="sxs-lookup"><span data-stu-id="77a76-177">4</span></span>|  
|`bigint`|<span data-ttu-id="77a76-178">8</span><span class="sxs-lookup"><span data-stu-id="77a76-178">8</span></span>|  
|`smallint`|<span data-ttu-id="77a76-179">2</span><span class="sxs-lookup"><span data-stu-id="77a76-179">2</span></span>|  
|`tinyint`|<span data-ttu-id="77a76-180">1</span><span class="sxs-lookup"><span data-stu-id="77a76-180">1</span></span>|  
|`money`|<span data-ttu-id="77a76-181">8</span><span class="sxs-lookup"><span data-stu-id="77a76-181">8</span></span>|  
|`smallmoney`|<span data-ttu-id="77a76-182">4</span><span class="sxs-lookup"><span data-stu-id="77a76-182">4</span></span>|  
|<span data-ttu-id="77a76-183">`decimal` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="77a76-183">`decimal` <sup>1</sup></span></span>|<sup>*</sup>|  
|<span data-ttu-id="77a76-184">`numeric` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="77a76-184">`numeric` <sup>1</sup></span></span>|<sup>*</sup>|  
|`uniqueidentifier`|<span data-ttu-id="77a76-185">16</span><span class="sxs-lookup"><span data-stu-id="77a76-185">16</span></span>|  
|`timestamp`|<span data-ttu-id="77a76-186">8</span><span class="sxs-lookup"><span data-stu-id="77a76-186">8</span></span>|  
  
 <span data-ttu-id="77a76-187"><sup>1</sup>有关 `decimal` 和数据类型的详细信息 `numeric` ，请参阅[decimal 和 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="77a76-187"><sup>1</sup> For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
 <span data-ttu-id="77a76-188">在上述所有情况中，若要创建日后要重新加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的数据文件并使存储空间保持最小，请使用长度前缀，以及默认文件存储类型和默认字段长度。</span><span class="sxs-lookup"><span data-stu-id="77a76-188">In all of the preceding cases, to create a data file for later reloading into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that keeps the storage space to a minimum, use a length prefix with the default file storage type and the default field length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a76-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77a76-189">See Also</span></span>  
 <span data-ttu-id="77a76-190">[bcp 实用工具](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="77a76-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="77a76-191">[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77a76-191">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="77a76-192">[指定字段终止符和行终止符 (SQL Server)](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="77a76-192">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 <span data-ttu-id="77a76-193">[使用 bcp 指定数据文件中的前缀长度 (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="77a76-193">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="77a76-194">[使用 bcp 指定文件存储类型 (SQL Server)](specify-file-storage-type-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="77a76-194">[Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="77a76-195">在批量导入期间保留 Null 或使用默认值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="77a76-195">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
