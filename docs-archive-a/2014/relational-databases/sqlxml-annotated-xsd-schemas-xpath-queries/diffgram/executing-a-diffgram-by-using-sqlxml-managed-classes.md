---
title: 使用 SQLXML 托管类执行 DiffGram |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: rothja
ms.author: jroth
ms.openlocfilehash: f36127c37eea73a2872d4bf0aef7172a88e430a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587291"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a><span data-ttu-id="df221-102">使用 SQLXML 托管类执行 DiffGram</span><span class="sxs-lookup"><span data-stu-id="df221-102">Executing a DiffGram by Using SQLXML Managed Classes</span></span>
  <span data-ttu-id="df221-103">此示例演示如何在 .NET Framework 环境中执行 DiffGram 文件 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ，以便 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用 Sqlxml 托管类 () 将数据更新应用到表。</span><span class="sxs-lookup"><span data-stu-id="df221-103">This example shows how to execute a DiffGram file in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment to apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables using SQLXML Managed Classes (Microsoft.Data.SqlXml).</span></span>  
  
 <span data-ttu-id="df221-104">在本示例中，DiffGram 更新客户 ALFKI 的客户信息（CompanyName 和 ContactName）。</span><span class="sxs-lookup"><span data-stu-id="df221-104">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
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
  
 <span data-ttu-id="df221-105">**\<before>** 块包括 **\<Customer>** 元素 (**diffgr： Id = "Customer1"**) 。</span><span class="sxs-lookup"><span data-stu-id="df221-105">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="df221-106">**\<DataInstance>** 该块包含 **\<Customer>** 具有相同**id**的对应元素。**\<customer>** 中的元素 **\<NewDataSet>** 还指定了**diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="df221-106">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="df221-107">这指示一个更新操作，而且 Cust 表中的客户记录也会相应地更新。</span><span class="sxs-lookup"><span data-stu-id="df221-107">This indicates an update operation, and the customer record in the Cust table is updated accordingly.</span></span> <span data-ttu-id="df221-108">请注意，如果未指定**diffgr： hasChanges**属性，DiffGram 处理逻辑将忽略此元素，并且不执行任何更新。</span><span class="sxs-lookup"><span data-stu-id="df221-108">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
 <span data-ttu-id="df221-109">下面是 c # 教程应用程序的代码，该应用程序演示如何使用 SQLXML 托管类来执行上述 DiffGram，并 (用户、Ord) 也在**tempdb**数据库中创建的两个表进行更新。</span><span class="sxs-lookup"><span data-stu-id="df221-109">The following is code for a C# tutorial application that shows how to use the SQLXML Managed Classes to execute the above DiffGram and update two tables (Cust, Ord) you will also create in the **tempdb** database.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="df221-110">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="df221-110">To test the application</span></span>  
  
1.  <span data-ttu-id="df221-111">确保已在计算机上安装了 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="df221-111">Ensure that the .NET Framework is installed on your computer.</span></span>  
  
2.  <span data-ttu-id="df221-112">将以下 XSD 架构 (DiffGramSchema.xml) 保存在某个文件夹中：</span><span class="sxs-lookup"><span data-stu-id="df221-112">Save the following XSD schema (DiffGramSchema.xml) in a folder:</span></span>  
  
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
  
3.  <span data-ttu-id="df221-113">在**tempdb**数据库中创建这些表。</span><span class="sxs-lookup"><span data-stu-id="df221-113">Create these tables in the **tempdb** database.</span></span>  
  
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
  
4.  <span data-ttu-id="df221-114">添加以下示例数据：</span><span class="sxs-lookup"><span data-stu-id="df221-114">Add this sample data:</span></span>  
  
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
  
5.  <span data-ttu-id="df221-115">复制上面的 DiffGram，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="df221-115">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="df221-116">在与步骤 1 中所使用文件夹相同的文件夹中将文件另存为 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="df221-116">Save the file as MyDiffGram.xml in the same folder used in step 1.</span></span>  
  
6.  <span data-ttu-id="df221-117">将上面提供的 C# 代码 (DiffgramSample.cs) 保存到先前步骤中用于保存 DiffGramSchema.xml 和 MyDiffGram.xml 的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="df221-117">Save the C# code (DiffgramSample.cs) that is provided above in the same folder in which the DiffGramSchema.xml and MyDiffGram.xml were stored in previous steps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df221-118">您需要将连接字符串中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称从“`MyServer`”更新为所安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的实际名称。</span><span class="sxs-lookup"><span data-stu-id="df221-118">You will need to update the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the connection string from '`MyServer`' to the actual name of your installed instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="df221-119">如果将该文件存储在不同文件夹中，则必须编辑代码，为映射架构指定相应的目录路径。</span><span class="sxs-lookup"><span data-stu-id="df221-119">If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.</span></span>  
  
7.  <span data-ttu-id="df221-120">编译代码。</span><span class="sxs-lookup"><span data-stu-id="df221-120">Compile the code.</span></span> <span data-ttu-id="df221-121">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="df221-121">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     <span data-ttu-id="df221-122">这将创建一个可执行文件 (DiffgramSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="df221-122">This creates an executable (DiffgramSample.exe).</span></span>  
  
8.  <span data-ttu-id="df221-123">在命令提示符下，执行 DiffgramSample.exe。</span><span class="sxs-lookup"><span data-stu-id="df221-123">At the command prompt, execute DiffgramSample.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df221-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df221-124">See Also</span></span>  
 [<span data-ttu-id="df221-125">&#40;SQLXML 4.0&#41;的 DiffGram 示例</span><span class="sxs-lookup"><span data-stu-id="df221-125">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
  
  
