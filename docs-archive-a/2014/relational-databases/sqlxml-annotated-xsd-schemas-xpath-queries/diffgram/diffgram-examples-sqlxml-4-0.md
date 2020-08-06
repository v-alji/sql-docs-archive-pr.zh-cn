---
title: " (SQLXML 4.0) 的 DiffGram 示例 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], examples
- examples [SQLXML], DiffGram
- diffgr:parentID
- parentID annotation
ms.assetid: fc148583-dfd3-4efb-a413-f47b150b0975
author: rothja
ms.author: jroth
ms.openlocfilehash: 04fb355af01f9853149a84af72471375d9135468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587299"
---
# <a name="diffgram-examples-sqlxml-40"></a><span data-ttu-id="3bf30-102">DiffGram 示例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3bf30-102">DiffGram Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="3bf30-103">本主题中的示例包括用于对数据库执行插入、更新和删除操作的多个 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3bf30-103">The examples in this topic consist of DiffGrams that perform insert, update, and delete operations to the database.</span></span> <span data-ttu-id="3bf30-104">在使用这些示例前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="3bf30-104">Before using the examples, note the following:</span></span>  
  
-   <span data-ttu-id="3bf30-105">示例中使用两个表（Cust 和 Ord）；要测试 DiffGram 示例，必须创建这两个表：</span><span class="sxs-lookup"><span data-stu-id="3bf30-105">The examples use two tables (Cust and Ord) that must be created if you want to test the DiffGram examples:</span></span>  
  
    ```  
    Cust(CustomerID, CompanyName, ContactName)  
    Ord(OrderID, CustomerID)  
    ```  
  
-   <span data-ttu-id="3bf30-106">本主题中的多数示例都使用以下 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="3bf30-106">Most of the examples in this topic use the following XSD Schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
    <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
    <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
    </xsd:element>  
  
    </xsd:schema>     
    ```  
  
     <span data-ttu-id="3bf30-107">将此架构另存为 DiffGramSchema.xml，并与示例中所用的其他文件保存在相同的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-107">Save this schema as DiffGramSchema.xml in the same folder where you save other files used in the examples.</span></span>  
  
## <a name="a-deleting-a-record-by-using-a-diffgram"></a><span data-ttu-id="3bf30-108">A.</span><span class="sxs-lookup"><span data-stu-id="3bf30-108">A.</span></span> <span data-ttu-id="3bf30-109">使用 DiffGram 删除记录</span><span class="sxs-lookup"><span data-stu-id="3bf30-109">Deleting a record by using a DiffGram</span></span>  
 <span data-ttu-id="3bf30-110">本示例中的 DiffGram 从 Cust 表中删除一条客户记录（CustomerID 为 ALFKI），并且从 Ord 表中删除相应的订单记录（OrderID 为 1）。</span><span class="sxs-lookup"><span data-stu-id="3bf30-110">The DiffGram in this example deletes a customer (whose CustomerID is ALFKI) record from the Cust table and deletes the corresponding order record (whose OrderID is 1) from the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance/>  
  
    <diffgr:before>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI"   
               OrderID="1"/>  
        <Customer diffgr:id="Customer1"   
                  msdata:rowOrder="0"   
                  CustomerID="ALFKI">  
           <CompanyName>Alfreds Futterkiste</CompanyName>  
           <ContactName>Maria Anders</ContactName>  
        </Customer>  
    </diffgr:before>  
    <msdata:errors/>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="3bf30-111">在 **\<before>** 块中，有一个 **\<Order>** 元素 (**diffgr： Id = "Order1"**) 和 **\<Customer>** 元素 (**diffgr： id = "Customer1"**) 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-111">In the **\<before>** block, there is an **\<Order>** element (**diffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="3bf30-112">这些元素表示数据库中的现有记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-112">These elements represent existing records in the database.</span></span> <span data-ttu-id="3bf30-113">**\<DataInstance>** 元素没有 (具有相同**diffgr： id**) 的相应记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-113">The **\<DataInstance>** element does not have the corresponding records (with the same **diffgr:id**).</span></span> <span data-ttu-id="3bf30-114">这指示一个删除操作。</span><span class="sxs-lookup"><span data-stu-id="3bf30-114">This indicates a delete operation.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="3bf30-115">测试 DiffGram</span><span class="sxs-lookup"><span data-stu-id="3bf30-115">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="3bf30-116">在**tempdb**数据库中创建这些表。</span><span class="sxs-lookup"><span data-stu-id="3bf30-116">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="3bf30-117">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="3bf30-117">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="3bf30-118">复制上面的 DiffGram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-118">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="3bf30-119">在上一步所使用的文件夹中将该文件另存为 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-119">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="3bf30-120">复制本主题上文所提供的 DiffGramSchema，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-120">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="3bf30-121">将该文件另存为 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-121">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="3bf30-122">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3bf30-122">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="3bf30-123">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf30-123">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="b-inserting-a-record-by-using-a-diffgram"></a><span data-ttu-id="3bf30-124">B.</span><span class="sxs-lookup"><span data-stu-id="3bf30-124">B.</span></span> <span data-ttu-id="3bf30-125">使用 DiffGram 插入记录</span><span class="sxs-lookup"><span data-stu-id="3bf30-125">Inserting a record by using a DiffGram</span></span>  
 <span data-ttu-id="3bf30-126">在本示例中，DiffGram 在 Cust 表和 Ord 表中各插入一条记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-126">In this example, the DiffGram inserts a record in the Cust table and a record in the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"   
      sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
          xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
          xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
       <Customer diffgr:id="Customer1" msdata:rowOrder="0"    
                 diffgr:hasChanges="inserted" CustomerID="ALFKI">  
        <CompanyName>C3Company</CompanyName>  
        <ContactName>C3Contact</ContactName>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"  
               diffgr:hasChanges="inserted"   
               CustomerID="ALFKI" OrderID="1"/>  
      </Customer>  
    </DataInstance>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="3bf30-127">在此 DiffGram 中， **\<before>** 未指定块 () 找不到任何现有的数据库记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-127">In this DiffGram the **\<before>** block is not specified (no existing database records identified).</span></span> <span data-ttu-id="3bf30-128">有两个记录实例 (由 **\<Customer>** **\<Order>**) 块中的和元素标识， **\<DataInstance>** 分别映射到 "Ord" 和 "" 表。</span><span class="sxs-lookup"><span data-stu-id="3bf30-128">There are two record instances (identified by the **\<Customer>** and **\<Order>** elements in the **\<DataInstance>** block) that map to Cust and Ord tables, respectively.</span></span> <span data-ttu-id="3bf30-129">这两个元素都指定了**diffgr： hasChanges**属性 (**hasChanges = "insert"**) 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-129">Both of these elements specify the **diffgr:hasChanges** attribute (**hasChanges="inserted"**).</span></span> <span data-ttu-id="3bf30-130">这指示一个插入操作。</span><span class="sxs-lookup"><span data-stu-id="3bf30-130">This indicates an insert operation.</span></span> <span data-ttu-id="3bf30-131">在此 DiffGram 中，如果指定**hasChanges = "modified"**，则表明要修改不存在的记录，这将导致错误。</span><span class="sxs-lookup"><span data-stu-id="3bf30-131">In this DiffGram, if you specify **hasChanges="modified"**, you are indicating that you want to modify a record that does not exist, which results in an error.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="3bf30-132">测试 DiffGram</span><span class="sxs-lookup"><span data-stu-id="3bf30-132">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="3bf30-133">在**tempdb**数据库中创建这些表。</span><span class="sxs-lookup"><span data-stu-id="3bf30-133">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="3bf30-134">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="3bf30-134">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="3bf30-135">复制上面的 DiffGram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-135">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="3bf30-136">在上一步所使用的文件夹中将该文件另存为 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-136">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="3bf30-137">复制本主题上文所提供的 DiffGramSchema，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-137">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="3bf30-138">将该文件另存为 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-138">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="3bf30-139">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3bf30-139">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="3bf30-140">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf30-140">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="c-updating-an-existing-record-by-using-a-diffgram"></a><span data-ttu-id="3bf30-141">C.</span><span class="sxs-lookup"><span data-stu-id="3bf30-141">C.</span></span> <span data-ttu-id="3bf30-142">使用 DiffGram 更新现有记录</span><span class="sxs-lookup"><span data-stu-id="3bf30-142">Updating an existing record by using a DiffGram</span></span>  
 <span data-ttu-id="3bf30-143">在本示例中，DiffGram 更新客户 ALFKI 的客户信息（CompanyName 和 ContactName）。</span><span class="sxs-lookup"><span data-stu-id="3bf30-143">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="3bf30-144">**\<before>** 块包括 **\<Customer>** 元素 (**diffgr： Id = "Customer1"**) 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-144">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="3bf30-145">**\<DataInstance>** 该块包含 **\<Customer>** 具有相同**id**的对应元素。**\<customer>** 中的元素 **\<NewDataSet>** 还指定了**diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="3bf30-145">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="3bf30-146">这表示更新操作，**客户表中的客户**记录将相应更新。</span><span class="sxs-lookup"><span data-stu-id="3bf30-146">This indicates an update operation, and the customer record in the **Cust** table is updated accordingly.</span></span> <span data-ttu-id="3bf30-147">请注意，如果未指定**diffgr： hasChanges**属性，DiffGram 处理逻辑将忽略此元素，并且不执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="3bf30-147">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="3bf30-148">测试 DiffGram</span><span class="sxs-lookup"><span data-stu-id="3bf30-148">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="3bf30-149">在**tempdb**数据库中创建这些表。</span><span class="sxs-lookup"><span data-stu-id="3bf30-149">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="3bf30-150">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="3bf30-150">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="3bf30-151">复制上面的 DiffGram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-151">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="3bf30-152">在上一步所使用的文件夹中将该文件另存为 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-152">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="3bf30-153">复制本主题上文所提供的 DiffGramSchema，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-153">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="3bf30-154">将该文件另存为 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-154">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="3bf30-155">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3bf30-155">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="3bf30-156">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf30-156">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="d-inserting-updating-and-deleting-records-by-using-a-diffgram"></a><span data-ttu-id="3bf30-157">D.</span><span class="sxs-lookup"><span data-stu-id="3bf30-157">D.</span></span> <span data-ttu-id="3bf30-158">使用 DiffGram 插入、更新和删除记录</span><span class="sxs-lookup"><span data-stu-id="3bf30-158">Inserting, updating, and deleting records by using a DiffGram</span></span>  
 <span data-ttu-id="3bf30-159">在本示例中，使用一个较为复杂的 DiffGram 执行插入、更新和删除操作。</span><span class="sxs-lookup"><span data-stu-id="3bf30-159">In this example, a relatively complex DiffGram is used to perform insert, update, and delete operations.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                diffgr:hasChanges="modified"   
                CustomerID="ANATR">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Elizabeth Lincoln</ContactName>  
          <Order diffgr:id="Order2" msdata:rowOrder="1"   
               msdata:hiddenCustomerID="ANATR"   
               CustomerID="ANATR" OrderID="2"/>  
      </Customer>  
  
      <Customer diffgr:id="Customer3" msdata:rowOrder="2"   
                CustomerID="ANTON">  
         <CompanyName>Chop-suey Chinese</CompanyName>  
         <ContactName>Yang Wang</ContactName>  
         <Order diffgr:id="Order3" msdata:rowOrder="2"   
               msdata:hiddenCustomerID="ANTON"   
               CustomerID="ANTON" OrderID="3"/>  
      </Customer>  
      <Customer diffgr:id="Customer4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                CustomerID="AROUT">  
         <CompanyName>Around the Horn</CompanyName>  
         <ContactName>Thomas Hardy</ContactName>  
         <Order diffgr:id="Order4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                msdata:hiddenCustomerID="AROUT"   
               CustomerID="AROUT" OrderID="4"/>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
      <Order diffgr:id="Order1" msdata:rowOrder="0"   
             msdata:hiddenCustomerID="ALFKI"   
             CustomerID="ALFKI" OrderID="1"/>  
      <Customer diffgr:id="Customer1" msdata:rowOrder="0"   
                CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                CustomerID="ANATR">  
        <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
        <ContactName>Ana Trujillo</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="3bf30-160">DiffGram 逻辑按如下方式处理此 DiffGram：</span><span class="sxs-lookup"><span data-stu-id="3bf30-160">The DiffGram logic processes this DiffGram as follows:</span></span>  
  
-   <span data-ttu-id="3bf30-161">根据 DiffGram 处理逻辑，块中的所有顶级元素都 **\<before>** 映射到相应的表，如映射架构中所述。</span><span class="sxs-lookup"><span data-stu-id="3bf30-161">In accordance with DiffGram processing logic, all the top-level elements in the **\<before>** block map to corresponding tables, as described in the mapping schema.</span></span>  
  
-   <span data-ttu-id="3bf30-162">**\<before>** 块具有 **\<Order>** 元素 (**dffgr： Id = "Order1"**) 和 **\<Customer>** 元素 (**diffgr： id = "Customer1"**) ，该元素在块中没有对应的元素 (**\<DataInstance>** 具有相同的 id。</span><span class="sxs-lookup"><span data-stu-id="3bf30-162">The **\<before>** block has an **\<Order>** element (**dffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**) for which there is no corresponding element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="3bf30-163">这指示一个删除操作，将从 Cust 表和 Ord 表中删除记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-163">This indicates a delete operation, and the records are deleted from the Cust and Ord tables.</span></span>  
  
-   <span data-ttu-id="3bf30-164">**\<before>** 块具有 **\<Customer>** 元素 (**diffgr： Id = "Customer2"**) ，该元素 **\<Customer>** 在 **\<DataInstance>** 块 (具有相同 id) 中具有相应的元素。</span><span class="sxs-lookup"><span data-stu-id="3bf30-164">The **\<before>** block has a **\<Customer>** element (**diffgr:id="Customer2"**) for which there is a corresponding **\<Customer>** element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="3bf30-165">块中的元素 **\<DataInstance>** 指定**Diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="3bf30-165">The element in the **\<DataInstance>** block specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="3bf30-166">这是一项更新操作，在该操作中，客户 ANATR 使用在块中指定的值在 customer 表中更新公司名称和联系人信息 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-166">This is an update operation in which for customer ANATR, the CompanyName and ContactName information is updated in the Cust table using values that are specified in the **\<DataInstance>** block.</span></span>  
  
-   <span data-ttu-id="3bf30-167">**\<DataInstance>** 块具有 **\<Customer>** 元素 (**diffgr： Id = "Customer3"**) 和 **\<Order>** 元素 (**diffgr： id = "Order3"**) 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-167">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer3"**) and an **\<Order>** element (**diffgr:id="Order3"**).</span></span> <span data-ttu-id="3bf30-168">这两个元素都不指定**diffgr： hasChanges**属性。</span><span class="sxs-lookup"><span data-stu-id="3bf30-168">Neither of these elements specify the **diffgr:hasChanges** attribute.</span></span> <span data-ttu-id="3bf30-169">因此，DiffGram 处理逻辑将忽略这些元素。</span><span class="sxs-lookup"><span data-stu-id="3bf30-169">Therefore, the DiffGram processing logic ignores these elements.</span></span>  
  
-   <span data-ttu-id="3bf30-170">**\<DataInstance>** 块具有 **\<Customer>** 元素 (**diffgr： Id = "Customer4"**) 和 **\<Order>** 元素 (**diffgr： id = "Order4"**) ，该元素在块中没有相应的元素 \<before> 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-170">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer4"**) and an **\<Order>** element (**diffgr:id="Order4"**) for which there are no corresponding elements in the \<before> block.</span></span> <span data-ttu-id="3bf30-171">块中的这些元素 **\<DataInstance>** 指定**Diffgr： hasChanges = "insert"**。</span><span class="sxs-lookup"><span data-stu-id="3bf30-171">These elements in the **\<DataInstance>** block specify **diffgr:hasChanges="inserted"**.</span></span> <span data-ttu-id="3bf30-172">因此，将在 Cust 表和 Ord 表中添加一条新记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-172">Therefore, a new record is added in the Cust table and in the Ord table.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="3bf30-173">测试 DiffGram</span><span class="sxs-lookup"><span data-stu-id="3bf30-173">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="3bf30-174">在**tempdb**数据库中创建以下表。</span><span class="sxs-lookup"><span data-stu-id="3bf30-174">Create the following tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="3bf30-175">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="3bf30-175">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="3bf30-176">复制上面的 DiffGram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-176">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="3bf30-177">在上一步所使用的文件夹中将该文件另存为 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-177">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="3bf30-178">复制本主题上文所提供的 DiffGramSchema，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3bf30-178">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="3bf30-179">将该文件另存为 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="3bf30-179">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="3bf30-180">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="3bf30-180">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="3bf30-181">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf30-181">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="e-applying-updates-by-using-a-diffgram-with-the-diffgrparentid-annotation"></a><span data-ttu-id="3bf30-182">E.</span><span class="sxs-lookup"><span data-stu-id="3bf30-182">E.</span></span> <span data-ttu-id="3bf30-183">通过使用带有 diffgr:parentID 批注的 DiffGram 应用更新</span><span class="sxs-lookup"><span data-stu-id="3bf30-183">Applying updates by using a DiffGram with the diffgr:parentID annotation</span></span>  
 <span data-ttu-id="3bf30-184">此示例演示如何在应用更新时使用在 DiffGram 的块中指定的**parentID**批注 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="3bf30-184">This example illustrates how the **parentID** annotation that is specified in the **\<before>** block of the DiffGram is used in applying the updates.</span></span>  
  
```  
<NewDataSet />  
<diffgr:before>  
   <Order diffgr:id="Order1" msdata:rowOrder="0" OrderID="2" />  
   <Order diffgr:id="Order3" msdata:rowOrder="2" OrderID="4" />  
  
   <OrderDetail diffgr:id="OrderDetail1"   
                diffgr:parentId="Order1"   
                msdata:rowOrder="0"   
                ProductID="13"   
                OrderID="2" />  
   <OrderDetail diffgr:id="OrderDetail3"   
                diffgr:parentId="Order3"  
                ProductID="77"  
                OrderID="4"/>  
</diffgr:before>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="3bf30-185">此 DiffGram 指定删除操作，因为只有一个 **\<before>** 块。</span><span class="sxs-lookup"><span data-stu-id="3bf30-185">This DiffGram specifies a delete operation because there is only a **\<before>** block.</span></span> <span data-ttu-id="3bf30-186">在 DiffGram 中， **parentID**批注用于指定订单和订单详细信息之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="3bf30-186">In the DiffGram, the **parentID** annotation is used to specify a parent-child relationship between the orders and order details.</span></span> <span data-ttu-id="3bf30-187">当 SQLXML 删除记录时，它先从此关系标识的子表中删除记录，然后从相应的父表中删除记录。</span><span class="sxs-lookup"><span data-stu-id="3bf30-187">When SQLXML deletes the records, it deletes records from the child table that is identified by this relationship and then deletes the records from the corresponding parent table.</span></span>  
  
  
