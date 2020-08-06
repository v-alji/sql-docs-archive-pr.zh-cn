---
title: SQL Server XML 大容量加载对象模型 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: rothja
ms.author: jroth
ms.openlocfilehash: 364515afaea17ce403f8eb38cb10bbe6003dfe2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682775"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a><span data-ttu-id="caaf8-102">SQL Server XML 大容量加载对象模型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="caaf8-102">SQL Server XML Bulk Load Object Model (SQLXML 4.0)</span></span>
  <span data-ttu-id="caaf8-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 大容量加载对象模型由 SQLXMLBulkLoad 对象组成。</span><span class="sxs-lookup"><span data-stu-id="caaf8-103">The Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML Bulk Load object model consists of the SQLXMLBulkLoad object.</span></span> <span data-ttu-id="caaf8-104">该对象支持以下方法和属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-104">This object supports the following methods and properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caaf8-105">方法</span><span class="sxs-lookup"><span data-stu-id="caaf8-105">Methods</span></span>  
 <span data-ttu-id="caaf8-106">执行</span><span class="sxs-lookup"><span data-stu-id="caaf8-106">Execute</span></span>  
 <span data-ttu-id="caaf8-107">通过使用作为参数提供的架构文件和数据文件（或流），大容量加载数据。</span><span class="sxs-lookup"><span data-stu-id="caaf8-107">Bulk loads the data by using the schema file and data file (or stream) that are provided as parameters.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="caaf8-108">属性</span><span class="sxs-lookup"><span data-stu-id="caaf8-108">Properties</span></span>  
 <span data-ttu-id="caaf8-109">BulkLoad</span><span class="sxs-lookup"><span data-stu-id="caaf8-109">BulkLoad</span></span>  
 <span data-ttu-id="caaf8-110">指定是否应执行大容量加载。</span><span class="sxs-lookup"><span data-stu-id="caaf8-110">Specifies whether a Bulk Load should be performed.</span></span> <span data-ttu-id="caaf8-111">如果只想生成架构 (查看) 的 SchemaGen、SGDropTables 和 SGUseID 属性，而不是执行大容量加载，则此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="caaf8-111">This property is useful if you want to generate only the schemas (see the SchemaGen, SGDropTables, and SGUseID properties that follow) and not perform a bulk load.</span></span> <span data-ttu-id="caaf8-112">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-112">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-113">当此属性设置为 TRUE 时，XML 大容量加载将执行。</span><span class="sxs-lookup"><span data-stu-id="caaf8-113">When the property is set to TRUE, XML Bulk Load executes.</span></span> <span data-ttu-id="caaf8-114">当此属性设置为 FALSE 时，XML 大容量加载将不执行。</span><span class="sxs-lookup"><span data-stu-id="caaf8-114">When it is set to FALSE, XML Bulk Load does not execute.</span></span>  
  
 <span data-ttu-id="caaf8-115">默认值为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-115">The default value is TRUE.</span></span>  
  
 <span data-ttu-id="caaf8-116">CheckConstraints</span><span class="sxs-lookup"><span data-stu-id="caaf8-116">CheckConstraints</span></span>  
 <span data-ttu-id="caaf8-117">指定在 XML 大容量加载将数据插入列时是否应检查对该列指定的约束（例如，由于列之间的主键/外键关系而产生的约束）。</span><span class="sxs-lookup"><span data-stu-id="caaf8-117">Specifies whether the constraints (such as constraints due to the primary key/foreign key relationship among columns) that are specified on the column should be checked when XML Bulk Load inserts data into the columns.</span></span> <span data-ttu-id="caaf8-118">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-118">This is a Boolean property.</span></span>  
  
 <span data-ttu-id="caaf8-119">在此属性设置为 TRUE 时，XML 大容量加载检查每个插入的值的约束（这意味着约束冲突将导致错误）。</span><span class="sxs-lookup"><span data-stu-id="caaf8-119">When the property is set to TRUE, XML Bulk Load checks the constraints for each value inserted (which means that a constraint violation results in an error).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caaf8-120">若要将此属性保留为 "FALSE"，您必须对目标表具有**ALTER TABLE**权限。</span><span class="sxs-lookup"><span data-stu-id="caaf8-120">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="caaf8-121">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="caaf8-121">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="caaf8-122">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-122">The default value is FALSE.</span></span> <span data-ttu-id="caaf8-123">在该值设置为 FALSE 时，XML 大容量加载在插入操作期间将忽略这些约束。</span><span class="sxs-lookup"><span data-stu-id="caaf8-123">When it is set to FALSE, XML Bulk Load ignores the constraints during an insert operation.</span></span> <span data-ttu-id="caaf8-124">在当前实现中，您必须按照映射架构中的主键和外键关系的顺序定义表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-124">In the current implementation, you must define the tables in the order of primary key and foreign key relationships in the mapping schema.</span></span> <span data-ttu-id="caaf8-125">也就是说，具有主键的表必须在具有外键的相应表之前定义；否则，XML 大容量加载将失败。</span><span class="sxs-lookup"><span data-stu-id="caaf8-125">That is, a table with a primary key must be defined before the corresponding table with the foreign key; otherwise, XML Bulk Load fails.</span></span>  
  
 <span data-ttu-id="caaf8-126">请注意，如果 ID 传播正在进行，则此选项不适用并且约束检查将保持。</span><span class="sxs-lookup"><span data-stu-id="caaf8-126">Note that if ID Propagation is being done, then this option does not apply and constraint checking will be left on.</span></span> <span data-ttu-id="caaf8-127">这将在 `KeepIdentity=False` 并且存在定义的关系（即，父级是标识字段并且在生成子级时值将提供给子级）发生。</span><span class="sxs-lookup"><span data-stu-id="caaf8-127">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="caaf8-128">ConnectionCommand</span><span class="sxs-lookup"><span data-stu-id="caaf8-128">ConnectionCommand</span></span>  
 <span data-ttu-id="caaf8-129">标识现有连接对象 (例如，XML 大容量加载应使用的 ADO 或 ICommand 命令对象) 。</span><span class="sxs-lookup"><span data-stu-id="caaf8-129">Identifies an existing connection object (for example, the ADO or ICommand command object) that XML Bulk Load should use.</span></span> <span data-ttu-id="caaf8-130">可以使用 ConnectionCommand 属性，而不是使用 ConnectionString 属性指定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="caaf8-130">You can use the ConnectionCommand property instead of specifying a connection string with the ConnectionString property.</span></span> <span data-ttu-id="caaf8-131">如果使用 ConnectionCommand，则必须将 Transaction 属性设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-131">The Transaction property must be set to TRUE if you use ConnectionCommand.</span></span>  
  
 <span data-ttu-id="caaf8-132">如果同时使用 ConnectionString 和 ConnectionCommand 属性，则 XML 大容量加载将使用最后一个指定的属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-132">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="caaf8-133">默认值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="caaf8-133">The default value is NULL.</span></span>  
  
 <span data-ttu-id="caaf8-134">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="caaf8-134">ConnectionString</span></span>  
 <span data-ttu-id="caaf8-135">标识 OLE DB 连接字符串，该字符串提供建立与数据库实例的连接所必需的信息。</span><span class="sxs-lookup"><span data-stu-id="caaf8-135">Identifies the OLE DB connection string that provides the necessary information to establish a connection to an instance of the database.</span></span> <span data-ttu-id="caaf8-136">如果同时使用 ConnectionString 和 ConnectionCommand 属性，则 XML 大容量加载将使用最后一个指定的属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-136">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="caaf8-137">默认值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="caaf8-137">The default value is NULL.</span></span>  
  
 <span data-ttu-id="caaf8-138">ErrorLogFile</span><span class="sxs-lookup"><span data-stu-id="caaf8-138">ErrorLogFile</span></span>  
 <span data-ttu-id="caaf8-139">指定 XML 大容量加载将错误和消息记录到的文件名。</span><span class="sxs-lookup"><span data-stu-id="caaf8-139">Specifies the file name into which the XML Bulk Load logs errors and messages.</span></span> <span data-ttu-id="caaf8-140">默认值为空字符串，在此情况下将不发生日志记录。</span><span class="sxs-lookup"><span data-stu-id="caaf8-140">The default is an empty string, in which case no logging takes place.</span></span>  
  
 <span data-ttu-id="caaf8-141">FireTriggers</span><span class="sxs-lookup"><span data-stu-id="caaf8-141">FireTriggers</span></span>  
 <span data-ttu-id="caaf8-142">指定在大容量加载操作期间是否应引发对目标表定义的触发器。</span><span class="sxs-lookup"><span data-stu-id="caaf8-142">Specifies if triggers defined on target tables should fire during the Bulk Load operation.</span></span> <span data-ttu-id="caaf8-143">默认值为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-143">The default is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-144">在设置为 TRUE 时，在插入操作期间触发器将照常触发。</span><span class="sxs-lookup"><span data-stu-id="caaf8-144">When set to TRUE, triggers will fire as per normal during insert operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caaf8-145">若要将此属性保留为 "FALSE"，您必须对目标表具有**ALTER TABLE**权限。</span><span class="sxs-lookup"><span data-stu-id="caaf8-145">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="caaf8-146">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="caaf8-146">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="caaf8-147">请注意，如果 ID 传播正在进行，则此选项不适用并且触发器将保持。</span><span class="sxs-lookup"><span data-stu-id="caaf8-147">Note that if ID Propagation is being done, then this option does not apply and triggers will be left on.</span></span> <span data-ttu-id="caaf8-148">这将在 `KeepIdentity=False` 并且存在定义的关系（即，父级是标识字段并且在生成子级时值将提供给子级）发生。</span><span class="sxs-lookup"><span data-stu-id="caaf8-148">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="caaf8-149">ForceTableLock</span><span class="sxs-lookup"><span data-stu-id="caaf8-149">ForceTableLock</span></span>  
 <span data-ttu-id="caaf8-150">指定在大容量加载期间，XML 大容量加载将数据复制到的表是否应被锁定。</span><span class="sxs-lookup"><span data-stu-id="caaf8-150">Specifies whether the tables into which XML Bulk Load copies data should be locked for the duration of the Bulk Load.</span></span> <span data-ttu-id="caaf8-151">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-151">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-152">在此属性设置为 TRUE 时，XML 大容量加载要求在大容量加载期间执行表锁定。</span><span class="sxs-lookup"><span data-stu-id="caaf8-152">When the property is set to TRUE, XML Bulk Load acquires table locks for the duration of the Bulk Load.</span></span> <span data-ttu-id="caaf8-153">在此属性设置为 FALSE 时，XML 大容量加载在每次将记录插入到表中时要求表锁定。</span><span class="sxs-lookup"><span data-stu-id="caaf8-153">When it is set to FALSE, XML Bulk Load acquires a table lock each time it inserts a record into a table.</span></span>  
  
 <span data-ttu-id="caaf8-154">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-154">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-155">IgnoreDuplicateKeys</span><span class="sxs-lookup"><span data-stu-id="caaf8-155">IgnoreDuplicateKeys</span></span>  
 <span data-ttu-id="caaf8-156">指定尝试在某一键列中插入重复值时应采取什么后续操作。</span><span class="sxs-lookup"><span data-stu-id="caaf8-156">Specifies what to do if an attempt is made to insert duplicate values in a key column.</span></span> <span data-ttu-id="caaf8-157">如果此属性设置为 TRUE 并且尝试在某一键列中插入具有重复值的记录，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将不插入该记录。</span><span class="sxs-lookup"><span data-stu-id="caaf8-157">If this property is set to TRUE and an attempt is made to insert a record with a duplicate value in a key column, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not insert that record.</span></span> <span data-ttu-id="caaf8-158">但它将插入随后的记录；这样，大容量加载操作将不会失败。</span><span class="sxs-lookup"><span data-stu-id="caaf8-158">But it does insert the subsequent record; thus, the Bulk Load operation does not fail.</span></span> <span data-ttu-id="caaf8-159">如果此属性设置为 FALSE，则尝试在某一键列中插入重复值时大容量加载将失败。</span><span class="sxs-lookup"><span data-stu-id="caaf8-159">If this property is set to FALSE, Bulk Load fails when an attempt is made to insert a duplicate value in a key column.</span></span>  
  
 <span data-ttu-id="caaf8-160">当 IgnoreDuplicateKeys 属性设置为 TRUE 时，将为表中插入的每个记录发出 COMMIT 语句。</span><span class="sxs-lookup"><span data-stu-id="caaf8-160">When the IgnoreDuplicateKeys property is set to TRUE, a COMMIT statement is issued for every record inserted in the table.</span></span> <span data-ttu-id="caaf8-161">这将降低性能。</span><span class="sxs-lookup"><span data-stu-id="caaf8-161">This slows down the performance.</span></span> <span data-ttu-id="caaf8-162">仅当 Transaction 属性设置为 FALSE 时，才能将属性设置为 TRUE，因为事务行为是使用文件实现的。</span><span class="sxs-lookup"><span data-stu-id="caaf8-162">The property can be set to TRUE only when the Transaction property is set to FALSE, because the transactional behavior is implemented using files.</span></span>  
  
 <span data-ttu-id="caaf8-163">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-163">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-164">KeepIdentity</span><span class="sxs-lookup"><span data-stu-id="caaf8-164">KeepIdentity</span></span>  
 <span data-ttu-id="caaf8-165">指定如何处理源文件中标识类型列的值。</span><span class="sxs-lookup"><span data-stu-id="caaf8-165">Specifies how to deal with the values for an Identity type column in the source file.</span></span> <span data-ttu-id="caaf8-166">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-166">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-167">在此属性设置为 TRUE 时，XML 大容量加载将在源文件中指定的值分配给标识列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-167">When the property is set to TRUE, XML Bulk Load assigns the values that are specified in the source file to the identity column.</span></span> <span data-ttu-id="caaf8-168">在该属性设置为 FALSE 时，大容量加载操作将忽略在源文件中指定的标识列值。</span><span class="sxs-lookup"><span data-stu-id="caaf8-168">When the property is set to FALSE, the bulk-load operation ignores the identity-column values that are specified in the source.</span></span> <span data-ttu-id="caaf8-169">在此情况下，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将某一值分配给标识列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-169">In this case, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns a value to the identity column.</span></span>  
  
 <span data-ttu-id="caaf8-170">如果大容量加载涉及作为外键的列，该外键引用存储 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 生成的值的标识列，则大容量加载会相应将这些标识值传播到外键列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-170">If the Bulk Load involves a column that is a foreign key referring to an identity column in which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-generated values are stored, Bulk Load appropriately propagates these identity values to the foreign key column.</span></span>  
  
 <span data-ttu-id="caaf8-171">此属性的值适用于在大容量加载中涉及的所有列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-171">The value of this property applies to all columns involved in the bulk load.</span></span> <span data-ttu-id="caaf8-172">默认值为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-172">The default value is TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caaf8-173">若要将此属性保留为 TRUE，您必须对目标表具有**ALTER TABLE**权限。</span><span class="sxs-lookup"><span data-stu-id="caaf8-173">To leave this property as TRUE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="caaf8-174">否则，它必须设置为 FALSE 的值。</span><span class="sxs-lookup"><span data-stu-id="caaf8-174">Otherwise, it must be set to a value of FALSE.</span></span> <span data-ttu-id="caaf8-175">有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="caaf8-175">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="caaf8-176">KeepNulls</span><span class="sxs-lookup"><span data-stu-id="caaf8-176">KeepNulls</span></span>  
 <span data-ttu-id="caaf8-177">指定哪些值将用于在 XML 文档中缺少相应属性或子元素的列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-177">Specifies what value to use for a column that is missing a corresponding attribute or child element in the XML document.</span></span> <span data-ttu-id="caaf8-178">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-178">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-179">当此属性设置为 TRUE 时，XML 大容量加载将 Null 值分配给该列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-179">When the property is set to TRUE, XML Bulk Load assigns a null value to the column.</span></span> <span data-ttu-id="caaf8-180">它并不分配在服务器上设置的该列的默认值（如果有）。</span><span class="sxs-lookup"><span data-stu-id="caaf8-180">It does not assign the column's default value, if any, as set on the server.</span></span> <span data-ttu-id="caaf8-181">此属性的值适用于在大容量加载中涉及的所有列。</span><span class="sxs-lookup"><span data-stu-id="caaf8-181">The value of this property applies to all columns involved in the bulk load.</span></span>  
  
 <span data-ttu-id="caaf8-182">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-182">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-183">SchemaGen</span><span class="sxs-lookup"><span data-stu-id="caaf8-183">SchemaGen</span></span>  
 <span data-ttu-id="caaf8-184">指定是否在执行大容量加载操作前创建必需的表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-184">Specifies whether to create the required tables before performing a Bulk Load operation.</span></span> <span data-ttu-id="caaf8-185">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-185">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-186">如果该属性设置为 TRUE，则创建在映射架构中标识的表（数据库必须存在）。</span><span class="sxs-lookup"><span data-stu-id="caaf8-186">If this property is set to TRUE, the tables identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="caaf8-187">如果数据库中已存在一个或多个表，则 SGDropTables 属性将确定是否删除并重新创建这些预先存在的表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-187">If one or more of the tables already exist in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="caaf8-188">SchemaGen 属性的默认值为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-188">The default value for the SchemaGen property is FALSE.</span></span> <span data-ttu-id="caaf8-189">SchemaGen 不会对新创建的表创建 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="caaf8-189">SchemaGen does not create PRIMARY KEY constraints on the newly created tables.</span></span> <span data-ttu-id="caaf8-190">但是，如果在映射架构中可以找到匹配的 `sql:relationship` 和 `sql:key-fields` 批注并且键字段由单个列构成，则 SchemaGen 会在数据库中创建 FOREIGN KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="caaf8-190">SchemaGen does, however, create FOREIGN KEY constraints in the database if it can find matching `sql:relationship` and `sql:key-fields` annotations in the mapping schema and if the key field consists of a single column.</span></span>  
  
 <span data-ttu-id="caaf8-191">请注意，如果将 SchemaGen 属性设置为 TRUE，则 XML 大容量加载将执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="caaf8-191">Note that if you set the SchemaGen property to TRUE, XML Bulk Load does the following:</span></span>  
  
-   <span data-ttu-id="caaf8-192">根据元素和属性名称创建必需的表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-192">Creates the necessary tables from the element and attribute names.</span></span> <span data-ttu-id="caaf8-193">因此，不采用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 保留字作为架构中的元素和属性名称十分重要。</span><span class="sxs-lookup"><span data-stu-id="caaf8-193">Therefore, it is important that you do not use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reserved words for element and attribute names in the schema.</span></span>  
  
-   <span data-ttu-id="caaf8-194">为使用[xml 数据类型](/sql/t-sql/xml/xml-transact-sql)格式的[sql：溢出字段](annotation-interpretation-sql-overflow-field.md)指定的任何列返回溢出数据。</span><span class="sxs-lookup"><span data-stu-id="caaf8-194">Returns overflow data for any column designated using the [sql:overflow-field](annotation-interpretation-sql-overflow-field.md) in [xml data type](/sql/t-sql/xml/xml-transact-sql) format.</span></span>  
  
 <span data-ttu-id="caaf8-195">SGDropTables</span><span class="sxs-lookup"><span data-stu-id="caaf8-195">SGDropTables</span></span>  
 <span data-ttu-id="caaf8-196">指定是否应删除并重新创建现有表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-196">Specifies whether existing tables should be dropped and re-created.</span></span> <span data-ttu-id="caaf8-197">当 SchemaGen 属性设置为 TRUE 时，将使用此属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-197">You use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="caaf8-198">如果 SGDropTables 为 FALSE，则保留现有表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-198">If SGDropTables is FALSE, the existing tables are retained.</span></span> <span data-ttu-id="caaf8-199">在此属性为 TRUE 时，将删除并重新创建现有表。</span><span class="sxs-lookup"><span data-stu-id="caaf8-199">When this property is TRUE, the existing tables are deleted and re-created.</span></span>  
  
 <span data-ttu-id="caaf8-200">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-200">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-201">SGUseID</span><span class="sxs-lookup"><span data-stu-id="caaf8-201">SGUseID</span></span>  
 <span data-ttu-id="caaf8-202">指定映射架构中作为 `id` 类型标识的属性是否可用于在创建表时创建 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="caaf8-202">Specifies whether the attribute in the mapping schema that is identified as `id` type can be used in creating a PRIMARY KEY constraint when the table is created.</span></span> <span data-ttu-id="caaf8-203">当 SchemaGen 属性设置为 TRUE 时，使用此属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-203">Use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="caaf8-204">如果 SGUseID 为 TRUE，则 SchemaGen 实用程序会使用一个属性，该属性 `dt:type="id"` 被指定为主键列并在创建表时添加适当的 PRIMARY key 约束。</span><span class="sxs-lookup"><span data-stu-id="caaf8-204">If SGUseID is TRUE, the SchemaGen utility uses an attribute for which `dt:type="id"` is specified as the primary key column and adds the appropriate PRIMARY KEY constraint when creating the table.</span></span>  
  
 <span data-ttu-id="caaf8-205">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-205">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-206">TempFilePath</span><span class="sxs-lookup"><span data-stu-id="caaf8-206">TempFilePath</span></span>  
 <span data-ttu-id="caaf8-207">指定文件路径，该路径中包含 XML 大容量加载为事务性大容量加载创建的临时文件。</span><span class="sxs-lookup"><span data-stu-id="caaf8-207">Specifies the file path where XML Bulk Load creates the temporary files for a transacted bulk load.</span></span> <span data-ttu-id="caaf8-208">仅当 Transaction 属性设置为 TRUE 时， (此属性才有用。 ) 必须确保 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用于 XML 大容量加载的帐户有权访问此路径。</span><span class="sxs-lookup"><span data-stu-id="caaf8-208">(This property is useful only when the Transaction property is set to TRUE.) You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account that is used for XML Bulk Load has access to this path.</span></span> <span data-ttu-id="caaf8-209">如果未设置此属性，XML 大容量加载将 TEMP 环境变量上指定的位置中存储临时文件。</span><span class="sxs-lookup"><span data-stu-id="caaf8-209">If this property is not set, XML Bulk Load stores the temporary files in the location that is specified in the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="caaf8-210">事务</span><span class="sxs-lookup"><span data-stu-id="caaf8-210">Transaction</span></span>  
 <span data-ttu-id="caaf8-211">指定大容量加载是否应作为事务实现，在此情况下，如果大容量加载失败，则确保回滚。</span><span class="sxs-lookup"><span data-stu-id="caaf8-211">Specifies whether the Bulk Load should be done as a transaction, in which case the rollback is guaranteed if the Bulk Load fails.</span></span> <span data-ttu-id="caaf8-212">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-212">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-213">如果此属性设置为 TRUE，则大容量加载将在事务上下文中发生。</span><span class="sxs-lookup"><span data-stu-id="caaf8-213">If the property is set to TRUE, the Bulk Load occurs in a transactional context.</span></span> <span data-ttu-id="caaf8-214">仅当 Transaction 设置为 TRUE 时，TempFilePath 属性才有用。</span><span class="sxs-lookup"><span data-stu-id="caaf8-214">The TempFilePath property is useful only when Transaction is set to TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caaf8-215">如果正在加载二进制数据 (例如，将 bin. hex、bin .xml XML 数据类型加载到二进制文件、图像 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型) ，则必须将 Transaction 属性设置为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-215">If you are loading binary data (such as the bin.hex, bin.base64 XML data types to the binary, image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types), the Transaction property must be set to FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-216">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-216">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="caaf8-217">XMLFragment</span><span class="sxs-lookup"><span data-stu-id="caaf8-217">XMLFragment</span></span>  
 <span data-ttu-id="caaf8-218">指定源数据是否是 XML 片断。</span><span class="sxs-lookup"><span data-stu-id="caaf8-218">Specifies whether the source data is an XML fragment.</span></span> <span data-ttu-id="caaf8-219">XML 片段是没有单个顶级（根）元素的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="caaf8-219">An XML fragment is an XML document with no single, top-level (root) element.</span></span> <span data-ttu-id="caaf8-220">此属性是一个布尔属性。</span><span class="sxs-lookup"><span data-stu-id="caaf8-220">This is a Boolean property.</span></span> <span data-ttu-id="caaf8-221">如果源文件由 XML 片断构成，则此属性必须设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-221">This property must be set to TRUE if the source file consists of an XML fragment.</span></span>  
  
 <span data-ttu-id="caaf8-222">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="caaf8-222">The default value is FALSE.</span></span>  
  
  
