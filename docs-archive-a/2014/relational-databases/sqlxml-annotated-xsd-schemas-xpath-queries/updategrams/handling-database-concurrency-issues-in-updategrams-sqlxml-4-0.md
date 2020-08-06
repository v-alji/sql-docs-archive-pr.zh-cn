---
title: 处理 Updategram 中的数据库并发问题 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: rothja
ms.author: jroth
ms.openlocfilehash: dd808b2688e8bf05149a5454bee91123878fb2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588445"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a><span data-ttu-id="a19eb-102">在 Updategram 中处理数据库并发问题 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a19eb-102">Handling Database Concurrency Issues in Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="a19eb-103">与其他数据库更新机制一样，updategram 必须处理多用户环境下对数据的并发更新。</span><span class="sxs-lookup"><span data-stu-id="a19eb-103">Like other database update mechanisms, updategrams must deal with concurrent updates to data in a multiuser environment.</span></span> <span data-ttu-id="a19eb-104">Updategram 使用乐观并发控制，该模式将选择字段数据与快照进行比较，以确保要更新的数据自从在数据库中读取后，其他用户应用程序未更改过该数据。</span><span class="sxs-lookup"><span data-stu-id="a19eb-104">Updategrams use the Optimistic Concurrency Control, which uses comparison of select field data as snapshots to ensure that the data to be updated has not been altered by another user application since it was read from the database.</span></span> <span data-ttu-id="a19eb-105">Updategram 在 updategram 的块中包含这些快照值 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-105">Updategrams include these snapshot values in the **\<before>** block of the updategrams.</span></span> <span data-ttu-id="a19eb-106">更新数据库之前，updategram 会根据数据库中当前的值检查在块中指定的值， **\<before>** 以确保更新有效。</span><span class="sxs-lookup"><span data-stu-id="a19eb-106">Before updating the database, the updategram checks the values that are specified in the **\<before>** block against the values currently in the database to ensure that the update is valid.</span></span>  
  
 <span data-ttu-id="a19eb-107">乐观并发控制在 updategram 中提供三种保护级别：低（无）、中间和高。</span><span class="sxs-lookup"><span data-stu-id="a19eb-107">The Optimistic Concurrency Control offers three levels of protection in an updategram: low (none), intermediate, and high.</span></span> <span data-ttu-id="a19eb-108">通过相应指定 updategram，可以确定需要的保护级别。</span><span class="sxs-lookup"><span data-stu-id="a19eb-108">You can decide what level of protection you need by specifying the updategram accordingly.</span></span>  
  
## <a name="lowest-level-of-protection"></a><span data-ttu-id="a19eb-109">最低保护级别</span><span class="sxs-lookup"><span data-stu-id="a19eb-109">Lowest Level of Protection</span></span>  
 <span data-ttu-id="a19eb-110">此级别为盲目更新，它不参照自上次读取数据库后已进行的其他更新来处理更新。</span><span class="sxs-lookup"><span data-stu-id="a19eb-110">This level is a blind update, in which the update is processed without reference to other updates that have been made since the database was last read.</span></span> <span data-ttu-id="a19eb-111">在这种情况下，只在块中指定主键列 (s) **\<before>** 来标识记录，并在块中指定更新后的信息 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-111">In such a case, you specify only the primary key column(s) in the **\<before>** block to identify the record, and you specify the updated information in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="a19eb-112">例如，无论以前的电话号码是什么，以下 updategram 中的新联系人电话号码都是正确的。</span><span class="sxs-lookup"><span data-stu-id="a19eb-112">For example, the new contact phone number in the following updategram is correct, regardless of what the phone number was previously.</span></span> <span data-ttu-id="a19eb-113">请注意 **\<before>** 块如何仅指定主键列 (ContactID) 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-113">Notice how the **\<before>** block specifies only the primary key column (ContactID).</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a><span data-ttu-id="a19eb-114">中间保护级别</span><span class="sxs-lookup"><span data-stu-id="a19eb-114">Intermediate Level of Protection</span></span>  
 <span data-ttu-id="a19eb-115">在此保护级别中，updategram 将要更新的数据的当前值与数据库列中的值进行比较，以确保自您的事务读取记录后，这（个）些值未被任何其他事务更改过。</span><span class="sxs-lookup"><span data-stu-id="a19eb-115">In this level of protection, the updategram compares the current value(s) of the data being updated with the value(s) in the database column(s) to ensure that the values have not been changed by some other transaction since the record was read by your transaction.</span></span>  
  
 <span data-ttu-id="a19eb-116">您可以通过指定主键列 (s) 以及要在块中更新的列 () 来获取此级别的保护 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-116">You can get this level of protection by specifying the primary key column(s) and the column(s) that you are updating in the **\<before>** block.</span></span>  
  
 <span data-ttu-id="a19eb-117">例如，此 updategram 为 ContactID 是 1 的联系人更新 Person.Contact 表的 Phone 列中的值。</span><span class="sxs-lookup"><span data-stu-id="a19eb-117">For example, this updategram changes the value in the Phone column of the Person.Contact table for the contact with ContactID of 1.</span></span> <span data-ttu-id="a19eb-118">**\<before>** 块指定**电话**属性，以确保在应用更新的值之前此属性值与数据库中相应列的值匹配。</span><span class="sxs-lookup"><span data-stu-id="a19eb-118">The **\<before>** block specifies the **Phone** attribute to ensure that this attribute value matches the value in the corresponding column in the database before applying the updated value.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a><span data-ttu-id="a19eb-119">高保护级别</span><span class="sxs-lookup"><span data-stu-id="a19eb-119">High Level of Protection</span></span>  
 <span data-ttu-id="a19eb-120">高保护级别确保自您的应用程序上次读取该记录后该记录没有变化（即自您的应用程序读取记录后，该记录未被任何其他事务更改过）。</span><span class="sxs-lookup"><span data-stu-id="a19eb-120">A high level of protection ensures that the record remains the same since your application last read that record (that is, since your application has read the record, it has not been changed by any other transaction).</span></span>  
  
 <span data-ttu-id="a19eb-121">可以通过两种方法实现针对并发更新的此类高保护级别：</span><span class="sxs-lookup"><span data-stu-id="a19eb-121">There are two ways you can get this high level of protection against concurrent updates:</span></span>  
  
-   <span data-ttu-id="a19eb-122">指定块中的表中的其他列 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-122">Specify additional columns in the table in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="a19eb-123">如果在块中指定其他列 **\<before>** ，则在应用更新之前，updategram 会将为这些列指定的值与数据库中的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="a19eb-123">If you specify additional columns in the **\<before>** block, the updategram compares the values that are specified for these columns with the values that were in the database before applying the update.</span></span> <span data-ttu-id="a19eb-124">如果自您的事务读取记录后有记录列被更改过，updategram 将不执行更新。</span><span class="sxs-lookup"><span data-stu-id="a19eb-124">If any of the record columns has changed since your transaction read the record, the updategram does not perform the update.</span></span>  
  
     <span data-ttu-id="a19eb-125">例如，以下 updategram 更新了 shift 名称，但指定了 (StartTime、EndTime) 在块中的其他列 **\<before>** ，从而请求对并发更新的更高保护级别。</span><span class="sxs-lookup"><span data-stu-id="a19eb-125">For example, the following updategram updates the shift name, but specifies additional columns (StartTime,EndTime) in the **\<before>** block, thereby requesting a higher level of protection against concurrent updates.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="a19eb-126">此示例通过指定块中记录的所有列值来指定最高保护级别 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-126">This example specifies the highest level of protection by specifying all column values for the record in the **\<before>** block.</span></span>  
  
-   <span data-ttu-id="a19eb-127">指定时间戳列 (在块中) 可用 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-127">Specify the timestamp column (if available) in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="a19eb-128">`<before`如果表中有一个) ，并且块中的主键列 () ，则只需 (指定> 块中的所有记录列 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="a19eb-128">Instead of specifying all the record columns in the `<before`> block, you can just specify the timestamp column (if the table has one) along with the primary key column(s) in the **\<before>** block.</span></span> <span data-ttu-id="a19eb-129">在每次更新记录后，数据库将时间戳列更新为唯一值。</span><span class="sxs-lookup"><span data-stu-id="a19eb-129">The database updates the timestamp column to a unique value after each update of the record.</span></span> <span data-ttu-id="a19eb-130">在这种情况下，updategram 将时间戳的值与数据库中的相应值进行比较。</span><span class="sxs-lookup"><span data-stu-id="a19eb-130">In this case, the updategram compares the value of the timestamp with the corresponding value in the database.</span></span> <span data-ttu-id="a19eb-131">在数据库中存储的时间戳值为二进制值。</span><span class="sxs-lookup"><span data-stu-id="a19eb-131">The timestamp value stored in the database is a binary value.</span></span> <span data-ttu-id="a19eb-132">因此，必须在架构中将时间戳列指定为 `dt:type="bin.hex"`、`dt:type="bin.base64"` 或 `sql:datatype="timestamp"`。</span><span class="sxs-lookup"><span data-stu-id="a19eb-132">Therefore, the timestamp column must be specified in the schema as `dt:type="bin.hex"`, `dt:type="bin.base64"`, or `sql:datatype="timestamp"`.</span></span> <span data-ttu-id="a19eb-133"> (可以指定 `xml` 数据类型或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型。 ) </span><span class="sxs-lookup"><span data-stu-id="a19eb-133">(You can specify either the `xml` data type or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.)</span></span>  
  
#### <a name="to-test-the-updategram"></a><span data-ttu-id="a19eb-134">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="a19eb-134">To test the updategram</span></span>  
  
1.  <span data-ttu-id="a19eb-135">在**tempdb**数据库中创建此表：</span><span class="sxs-lookup"><span data-stu-id="a19eb-135">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  <span data-ttu-id="a19eb-136">添加此示例记录：</span><span class="sxs-lookup"><span data-stu-id="a19eb-136">Add this sample record:</span></span>  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  <span data-ttu-id="a19eb-137">复制以下 XSD 架构并将其粘贴到记事本中。</span><span class="sxs-lookup"><span data-stu-id="a19eb-137">Copy the following XSD schema and paste it into Notepad.</span></span> <span data-ttu-id="a19eb-138">将其另存为 ConcurrencySampleSchema.xml：</span><span class="sxs-lookup"><span data-stu-id="a19eb-138">Save it as ConcurrencySampleSchema.xml:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  <span data-ttu-id="a19eb-139">将以下 updategram 代码复制到记事本中，然后在保存上一步中创建的架构的相同目录中将其保存为 ConcurrencySampleTemplate.xml。</span><span class="sxs-lookup"><span data-stu-id="a19eb-139">Copy the following updategram code into Notepad and save it as ConcurrencySampleTemplate.xml in the same directory where you saved the schema created in the previous step.</span></span> <span data-ttu-id="a19eb-140">（请注意下面 LastUpdated 的时间戳值将不同于示例 Customer 表中的值，因此从表中复制 LastUpdated 的实际值并将其粘贴到 updategram。）</span><span class="sxs-lookup"><span data-stu-id="a19eb-140">(Note the timestamp value below for LastUpdated will differ in your example Customer table, so copy the actual value for LastUpdated from the table and paste it into the updategram.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="a19eb-141">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="a19eb-141">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a19eb-142">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="a19eb-142">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a19eb-143">这是等效的 XDR 架构：</span><span class="sxs-lookup"><span data-stu-id="a19eb-143">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a19eb-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a19eb-144">See Also</span></span>  
 [<span data-ttu-id="a19eb-145">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="a19eb-145">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
