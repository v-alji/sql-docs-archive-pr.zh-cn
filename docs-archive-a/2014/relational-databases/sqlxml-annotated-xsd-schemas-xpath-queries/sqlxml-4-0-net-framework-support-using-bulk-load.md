---
title: 在 .NET 环境中使用 SQLXML 大容量加载 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bd1c44a8b56bc5129aeb9843ed9ba814d45742a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692337"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a><span data-ttu-id="5c1f6-102">在 .NET 环境中使用 SQLXML 大容量加载</span><span class="sxs-lookup"><span data-stu-id="5c1f6-102">Using SQLXML Bulk Load in the .NET Environment</span></span>
  <span data-ttu-id="5c1f6-103">本主题说明如何在 .NET 环境中使用 XML 大容量加载功能。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-103">This topic explains how the XML Bulk Load functionality can be used in the .NET environment.</span></span> <span data-ttu-id="5c1f6-104">有关 XML 大容量加载的详细信息，请参阅[&#40;SQLXML 4.0&#41;执行 Xml 数据的大容量加载](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-104">For detailed information about XML Bulk Load, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="5c1f6-105">若要从托管环境使用 SQLXML 大容量加载 COM 对象，需要添加对此对象的项目引用。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-105">To use the SQLXML Bulk Load COM object from a managed environment, you need to add a project reference to this object.</span></span> <span data-ttu-id="5c1f6-106">这将围绕该大容量加载 COM 对象生成一个托管的包装接口。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-106">This generates a managed wrapper interface around the Bulk Load COM object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c1f6-107">托管的 XML 大容量加载不使用托管流并且要求围绕本机流的包装。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-107">Managed XML Bulk load does not work with managed streams and requires a wrapper around native streams.</span></span> <span data-ttu-id="5c1f6-108">SQLXML 大容量加载组件将不在多线程环境中运行（“[MTAThread]”属性）。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-108">The SQLXML Bulk Load component will not run in a multi-threaded environment ('[MTAThread]' attribute).</span></span> <span data-ttu-id="5c1f6-109">如果尝试在多线程环境中运行大容量加载组件，会收到 InvalidCastException 异常，其中包含以下附加信息： "interface SQLXMLBULKLOADLib. ISQLXMLBulkLoad 的 QueryInterface 失败"。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-109">If you attempt to run the Bulk Load component in a multi-thread environment, you get an InvalidCastException exception with the following additional information: "QueryInterface for interface SQLXMLBULKLOADLib.ISQLXMLBulkLoad failed."</span></span> <span data-ttu-id="5c1f6-110">解决方法是，使用示例) 中所示的 **[STAThread]** 属性，使包含大容量加载对象可访问单线程的对象 (例如。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-110">The workaround is to make the object that contains the Bulk Load object single-thread accessible (for example, by using the **[STAThread]** attribute as shown in the sample).</span></span>  
  
 <span data-ttu-id="5c1f6-111">本主题提供一个 C# 应用程序的工作示例，用于将 XML 数据大容量加载到数据库中。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-111">This topic provides a working C# sample application to bulk load XML data in the database.</span></span> <span data-ttu-id="5c1f6-112">请按照以下步骤创建工作示例：</span><span class="sxs-lookup"><span data-stu-id="5c1f6-112">To create a working sample, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5c1f6-113">创建以下表：</span><span class="sxs-lookup"><span data-stu-id="5c1f6-113">Create the following tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  <span data-ttu-id="5c1f6-114">将以下架构保存在文件 (schema.xml) 中：</span><span class="sxs-lookup"><span data-stu-id="5c1f6-114">Save the following schema in a file (schema.xml):</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="5c1f6-115">将以下示例 XML 文档保存在文件 (data.xml) 中：</span><span class="sxs-lookup"><span data-stu-id="5c1f6-115">Save the following sample XML document in a file (data.xml):</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="5c1f6-116">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-116">Start Visual Studio.</span></span>  
  
5.  <span data-ttu-id="5c1f6-117">创建 C# 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-117">Create a C# console application.</span></span>  
  
6.  <span data-ttu-id="5c1f6-118">从 "**项目**" 菜单中，选择 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-118">From the **Project** menu, select **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="5c1f6-119">在 " **COM** " 选项卡中，选择 " **Microsoft SQLXML Bulkload 4.0 类型库** ( # A0) 并单击 **" 确定 "**。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-119">In the **COM** tab, select **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll) and click **OK**.</span></span> <span data-ttu-id="5c1f6-120">你将看到在项目中创建的**SQLXMLBULKLOADLib**程序集。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-120">You will see the **Interop.SQLXMLBULKLOADLib** assembly created in the project.</span></span>  
  
8.  <span data-ttu-id="5c1f6-121">用下面的代码替换 Main() 方法。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-121">Replace the Main() method with the following code.</span></span> <span data-ttu-id="5c1f6-122">更新**ConnectionString**属性和架构和数据文件的文件路径。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-122">Update the **ConnectionString** property and the file path to the schema and data files.</span></span>  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. <span data-ttu-id="5c1f6-123">若要在您创建的表中加载 XML，请生成并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-123">To load the XML in the table you created, build and run the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c1f6-124">还可以使用 tlbimp.exe 工具添加对大容量加载组件 (xblkld4.dll) 的引用，该工具作为 .NET framework 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-124">The reference to the Bulk Load component (xblkld4.dll) can also be added using the tlbimp.exe tool, which is available as part of .NET framework.</span></span> <span data-ttu-id="5c1f6-125">该工具为本机 DLL (xblkld4.dll) 创建一个托管包装，然后该包装可用于任何 .NET 项目中。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-125">This tool creates a managed wrapper for the native DLL (xblkld4.dll), which can then be used in any .NET project.</span></span> <span data-ttu-id="5c1f6-126">例如：</span><span class="sxs-lookup"><span data-stu-id="5c1f6-126">For example:</span></span>  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     <span data-ttu-id="5c1f6-127">这将创建可用于 .NET Framework 项目中的托管包装 DLL (SQLXMLBULKLOADLib.dll)。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-127">This creates the managed wrapper DLL (SQLXMLBULKLOADLib.dll) that you can use in the .NET Framework project.</span></span> <span data-ttu-id="5c1f6-128">在 .NET Framework 中，您添加对新创建的 DLL 的项目引用。</span><span class="sxs-lookup"><span data-stu-id="5c1f6-128">In the .NET Framework, you add project reference to the newly created DLL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1f6-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c1f6-129">See Also</span></span>  
 [<span data-ttu-id="5c1f6-130">对 XML 数据执行大容量加载 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="5c1f6-130">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
