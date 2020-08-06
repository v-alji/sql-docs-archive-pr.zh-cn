---
title: 建立与数据源的连接 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: rothja
ms.author: jroth
ms.openlocfilehash: f88454339ee932c38655819cce475ab52d79975f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589533"
---
# <a name="establishing-a-connection-to-a-data-source"></a><span data-ttu-id="77772-102">建立与数据源的连接</span><span class="sxs-lookup"><span data-stu-id="77772-102">Establishing a Connection to a Data Source</span></span>
  <span data-ttu-id="77772-103">若要访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序，使用者必须首先通过调用**CoCreateInstance**方法创建数据源对象的实例。</span><span class="sxs-lookup"><span data-stu-id="77772-103">To access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer must first create an instance of a data source object by calling the **CoCreateInstance** method.</span></span> <span data-ttu-id="77772-104">每个 OLE DB 访问接口都具有一个唯一的类标识符 (CLSID)。</span><span class="sxs-lookup"><span data-stu-id="77772-104">A unique class identifier (CLSID) identifies each OLE DB provider.</span></span> <span data-ttu-id="77772-105">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序，CLSID_SQLNCLI10 类标识符。</span><span class="sxs-lookup"><span data-stu-id="77772-105">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the class identifier is CLSID_SQLNCLI10.</span></span> <span data-ttu-id="77772-106">您还可以使用符号 SQLNCLI_CLSID，该符号将解析为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您引用的 sqlncli.msi 中使用的 Native Client OLE DB 提供程序。</span><span class="sxs-lookup"><span data-stu-id="77772-106">You can also use the symbol SQLNCLI_CLSID that will resolve to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider that is used in the sqlncli.h that you reference.</span></span>  
  
 <span data-ttu-id="77772-107">数据源对象公开了 IDBProperties 接口，使用者使用该接口提供基本的身份验证信息，如服务器名、数据库名、用户 ID 和密码\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77772-107">The data source object exposes the **IDBProperties** interface, which the consumer uses to provide basic authentication information such as server name, database name, user ID, and password.</span></span> <span data-ttu-id="77772-108">可调用 IDBProperties::SetProperties 方法设置这些属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77772-108">The **IDBProperties::SetProperties** method is called to set these properties.</span></span>  
  
 <span data-ttu-id="77772-109">如果计算机上运行了多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，应以“服务器名称\示例名称”的形式指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="77772-109">If there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer, the server name is specified as ServerName\InstanceName.</span></span>  
  
 <span data-ttu-id="77772-110">数据源对象还公开了 IDBInitialize 接口\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77772-110">The data source object also exposes the **IDBInitialize** interface.</span></span> <span data-ttu-id="77772-111">在设置这些属性之后，可通过调用 IDBInitialize::Initialize 方法建立与数据源的连接\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77772-111">After the properties are set, connection to the data source is established by calling the **IDBInitialize::Initialize** method.</span></span> <span data-ttu-id="77772-112">例如：</span><span class="sxs-lookup"><span data-stu-id="77772-112">For example:</span></span>  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 <span data-ttu-id="77772-113">对**CoCreateInstance**的此调用将创建与 (CLSID_SQLNCLI10 关联的类的单个对象，该类与要用于创建对象) 的数据和代码关联。</span><span class="sxs-lookup"><span data-stu-id="77772-113">This call to **CoCreateInstance** creates a single object of the class associated with CLSID_SQLNCLI10 (CSLID associated with the data and code that will be used to create the object).</span></span> <span data-ttu-id="77772-114">IID_IDBInitialize 引用接口 (IDBInitialize) 的标识符，而该接口用于与对象通信\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77772-114">IID_IDBInitialize is a reference to the identifier of the interface (**IDBInitialize**) to be used to communicate with the object.</span></span>  
  
 <span data-ttu-id="77772-115">以下是一个函数示例，该函数初始化并建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="77772-115">The following is a sample function that initializes and establishes a connection to the data source.</span></span>  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="77772-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77772-116">See Also</span></span>  
 [<span data-ttu-id="77772-117">创建 SQL Server Native Client OLE DB 访问接口应用程序</span><span class="sxs-lookup"><span data-stu-id="77772-117">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
