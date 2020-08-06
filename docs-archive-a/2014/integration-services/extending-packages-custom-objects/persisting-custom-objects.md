---
title: 使自定义对象持久化 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom objects [Integration Services], persisting
ms.assetid: 97c19716-6447-4c1c-b277-cc2e6c1e6a6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55baa48f1ab0cf4175592b095463c9f12293b83f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590293"
---
# <a name="persisting-custom-objects"></a><span data-ttu-id="7150e-102">使自定义对象持久化</span><span class="sxs-lookup"><span data-stu-id="7150e-102">Persisting Custom Objects</span></span>
  <span data-ttu-id="7150e-103">如果您创建的自定义对象的属性仅使用诸如 `integer` 和 `string` 的简单数据类型，则不需要对这些对象实现自定义持久性。</span><span class="sxs-lookup"><span data-stu-id="7150e-103">You do not need to implement custom persistence for the custom objects that you create as long as their properties use only simple data types such as `integer` and `string`.</span></span> <span data-ttu-id="7150e-104">持久性的默认实现可保存对象的元数据及其所有属性的值。</span><span class="sxs-lookup"><span data-stu-id="7150e-104">The default implementation of persistence saves the metadata for your object along with the values of all its properties.</span></span>  
  
 <span data-ttu-id="7150e-105">但是，如果您的对象具有使用复杂数据类型的属性，或您希望在加载和保存属性值时对其执行自定义处理，则可以实现 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist> 接口及其 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.LoadFromXML%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.SaveToXML%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7150e-105">However, if your object has properties that use complex data types, or if you want to perform custom processing on property values as they are loaded and saved, you can implement the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist> interface and its <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.LoadFromXML%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.SaveToXML%2A> methods.</span></span> <span data-ttu-id="7150e-106">在这些方法中，可以从包的 XML 定义加载包含这些对象属性及其当前值的 XML 片段，或将这些片段保存到包的 XML 定义中。</span><span class="sxs-lookup"><span data-stu-id="7150e-106">In these methods you load from (or save to) the XML definition of the package an XML fragment that contains the properties of your object and their current values.</span></span> <span data-ttu-id="7150e-107">此 XML 片段的格式未定义；只要求必须是格式正确的 XML。</span><span class="sxs-lookup"><span data-stu-id="7150e-107">The format of this XML fragment is not defined; it must only be well-formed XML.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7150e-108">实现自定义持久性时，必须使对象的所有属性持久化，包括继承的属性和添加的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="7150e-108">When you implement custom persistence, you must persist all the properties of the object, including both inherited properties and custom properties that you have added.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7150e-109">示例</span><span class="sxs-lookup"><span data-stu-id="7150e-109">Example</span></span>  
 <span data-ttu-id="7150e-110">尽管 SQL Server 自定义连接管理器示例不要求对其 `string` 类型的三个属性实现自定义持久性，但下面的代码演示了使连接管理器及其属性持久化所需的自定义代码的示例。</span><span class="sxs-lookup"><span data-stu-id="7150e-110">Although the Sql Server Custom Connection Manager Sample does not require custom persistence for its three properties of type `string`, the following code shows an example of the custom code that would be required to persist the connection manager and its properties.</span></span> <span data-ttu-id="7150e-111">包含此代码的类必须实现 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist> 接口。</span><span class="sxs-lookup"><span data-stu-id="7150e-111">The class that contains this code must implement the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist> interface.</span></span>  
  
```vb  
Private Const PERSIST_ELEMENT As String = "SqlConnectionManager"  
Private Const PERSIST_SERVER As String = "Server"  
Private Const PERSIST_DATABASE As String = "Database"  
Private Const PERSIST_CONNECTIONSTRING As String = "ConnectionString"  
  
Public Sub LoadFromXML(ByVal node As System.Xml.XmlElement, _  
  ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) _  
  Implements Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.LoadFromXML  
  
  Dim propertyNode As XmlNode  
  
  ' Make sure that the correct node is being loaded.  
  If node.Name <> PERSIST_ELEMENT Then  
    Throw New Exception("Persisted element is not of type " & PERSIST_ELEMENT)  
  End If  
  
  ' Load the three properties of the object from XML into variables.  
  For Each propertyNode In node.ChildNodes  
    Select Case propertyNode.Name  
      Case PERSIST_SERVER  
        _serverName = propertyNode.InnerText  
      Case PERSIST_DATABASE  
        _databaseName = propertyNode.InnerText  
      Case PERSIST_CONNECTIONSTRING  
        _connectionString = propertyNode.InnerText  
    End Select  
  Next  
  
End Sub  
  
Public Sub SaveToXML(ByVal doc As System.Xml.XmlDocument, _  
  ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) _  
  Implements Microsoft.SqlServer.Dts.Runtime.IDTSComponentPersist.SaveToXML  
  
  Dim elementRoot As XmlElement  
  Dim propertyNode As XmlNode  
  
  ' Create a new node to persist the object and its properties.  
  elementRoot = doc.CreateElement(String.Empty, PERSIST_ELEMENT, String.Empty)  
  
  ' Save the three properties of the object from variables into XML.  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_SERVER, String.Empty)  
  propertyNode.InnerText = _serverName  
  elementRoot.AppendChild(propertyNode)  
  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_DATABASE, String.Empty)  
  propertyNode.InnerText = _databaseName  
  elementRoot.AppendChild(propertyNode)  
  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_CONNECTIONSTRING, String.Empty)  
  propertyNode.InnerText = _connectionString  
  elementRoot.AppendChild(propertyNode)  
  
  doc.AppendChild(elementRoot)  
  
End Sub  
```  
  
```csharp  
private const string PERSIST_ELEMENT = "SqlConnectionManager";  
private const string PERSIST_SERVER = "Server";  
private const string PERSIST_DATABASE = "Database";  
private const string PERSIST_CONNECTIONSTRING = "ConnectionString";  
  
public void LoadFromXML(System.Xml.XmlElement node,  
  Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  // Make sure that the correct node is being loaded.  
  if (node.Name != PERSIST_ELEMENT)  
  {  
    throw new Exception("Persisted element is not of type " + PERSIST_ELEMENT);  
  }  
  
  // Save the three properties of the object from variables into XML.  
  foreach (XmlNode propertyNode in node.ChildNodes)  
  {  
    switch (propertyNode.Name)  
    {  
      case PERSIST_SERVER:  
        _serverName = propertyNode.InnerText;  
        break;  
      case PERSIST_DATABASE:  
        _databaseName = propertyNode.InnerText;  
        break;  
      case PERSIST_CONNECTIONSTRING:  
        _connectionString = propertyNode.InnerText;  
        break;  
    }  
  }  
  
}  
  
public void SaveToXML(System.Xml.XmlDocument doc,  
  Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  XmlElement elementRoot;  
  XmlNode propertyNode;  
  
  // Create a new node to persist the object and its properties.  
  elementRoot = doc.CreateElement(String.Empty, PERSIST_ELEMENT, String.Empty);  
  
  // Save the three properties of the object from variables into XML.  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_SERVER, String.Empty);  
  propertyNode.InnerText = _serverName;  
  elementRoot.AppendChild(propertyNode);  
  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_DATABASE, String.Empty);  
  propertyNode.InnerText = _databaseName;  
  elementRoot.AppendChild(propertyNode);  
  
  propertyNode = doc.CreateNode(XmlNodeType.Element, PERSIST_CONNECTIONSTRING, String.Empty);  
  propertyNode.InnerText = _connectionString;  
  elementRoot.AppendChild(propertyNode);  
  
  doc.AppendChild(elementRoot);  
  
}  
```  
  
<span data-ttu-id="7150e-112">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7150e-112">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7150e-113">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="7150e-113">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7150e-114">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="7150e-114">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7150e-115">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="7150e-115">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7150e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7150e-116">See Also</span></span>  
 <span data-ttu-id="7150e-117">[开发 Integration Services 的自定义对象](developing-custom-objects-for-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="7150e-117">[Developing Custom Objects for Integration Services](developing-custom-objects-for-integration-services.md) </span></span>  
 [<span data-ttu-id="7150e-118">生成、部署和调试自定义对象</span><span class="sxs-lookup"><span data-stu-id="7150e-118">Building, Deploying, and Debugging Custom Objects</span></span>](building-deploying-and-debugging-custom-objects.md)  
  
  
