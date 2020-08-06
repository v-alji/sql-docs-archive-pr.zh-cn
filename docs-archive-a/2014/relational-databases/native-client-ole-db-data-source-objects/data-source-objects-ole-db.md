---
title: 数据源对象 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cf3f0b0308d655b50149c174547c19966f550ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682824"
---
# <a name="data-source-objects-ole-db"></a><span data-ttu-id="1167b-102">数据源对象 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1167b-102">Data Source Objects (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1167b-103">Native Client 对用于建立到数据存储的链接的一组 OLE DB 接口使用术语 "数据源"，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1167b-103">Native Client uses the term data source for the set of OLE DB interfaces used to establish a link to a data store, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1167b-104">创建提供程序的数据源对象的实例是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端使用者的第一个任务。</span><span class="sxs-lookup"><span data-stu-id="1167b-104">Creating an instance of the data source object of the provider is the first task of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consumer.</span></span>  
  
 <span data-ttu-id="1167b-105">每个 OLE DB 访问接口都为自身声明一个类标识符 (CLSID)。</span><span class="sxs-lookup"><span data-stu-id="1167b-105">Every OLE DB provider declares a class identifier (CLSID) for itself.</span></span> <span data-ttu-id="1167b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序的 CLSID 是 C/c + + GUID CLSID_SQLNCLI10 (符号 SQLNCLI_CLSID 会解析为引用) 的 sqlncli.msi 文件中的正确 progid。</span><span class="sxs-lookup"><span data-stu-id="1167b-106">The CLSID for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider is the C/C++ GUID CLSID_SQLNCLI10 (the symbol SQLNCLI_CLSID will resolve to the correct progid in the sqlncli.h file that you reference).</span></span> <span data-ttu-id="1167b-107">通过 CLSID，使用者使用 OLE CoCreateInstance 函数生成数据源对象的实例\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1167b-107">With the CLSID, the consumer uses the OLE **CoCreateInstance** function to manufacture an instance of the data source object.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1167b-108">Native Client 是进程内服务器。</span><span class="sxs-lookup"><span data-stu-id="1167b-108">Native Client is an in-process server.</span></span> <span data-ttu-id="1167b-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用 CLSCTX_INPROC_SERVER 宏创建 Native Client OLE DB 提供程序对象的实例以指示可执行上下文。</span><span class="sxs-lookup"><span data-stu-id="1167b-109">Instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider objects are created using the CLSCTX_INPROC_SERVER macro to indicate the executable context.</span></span>  
  
 <span data-ttu-id="1167b-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序数据源对象公开 OLE DB 初始化接口，该接口允许使用者连接到现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="1167b-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object exposes the OLE DB initialization interfaces that allow the consumer to connect to existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="1167b-111">通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序建立的每个连接都会自动设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="1167b-111">Every connection made through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets these options automatically:</span></span>  
  
-   <span data-ttu-id="1167b-112">SET ANSI_WARNINGS ON</span><span class="sxs-lookup"><span data-stu-id="1167b-112">SET ANSI_WARNINGS ON</span></span>  
  
-   <span data-ttu-id="1167b-113">SET ANSI_NULLS ON</span><span class="sxs-lookup"><span data-stu-id="1167b-113">SET ANSI_NULLS ON</span></span>  
  
-   <span data-ttu-id="1167b-114">SET ANSI_PADDING ON</span><span class="sxs-lookup"><span data-stu-id="1167b-114">SET ANSI_PADDING ON</span></span>  
  
-   <span data-ttu-id="1167b-115">SET ANSI_NULL_DFLT_ON ON</span><span class="sxs-lookup"><span data-stu-id="1167b-115">SET ANSI_NULL_DFLT_ON ON</span></span>  
  
-   <span data-ttu-id="1167b-116">SET QUOTED_IDENTIFIER ON</span><span class="sxs-lookup"><span data-stu-id="1167b-116">SET QUOTED_IDENTIFIER ON</span></span>  
  
-   <span data-ttu-id="1167b-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span><span class="sxs-lookup"><span data-stu-id="1167b-117">SET CONCAT_OF_NULL_YIELDS_NULL ON</span></span>  
  
 <span data-ttu-id="1167b-118">此示例使用类标识符宏来创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序数据源对象并获取对其**IDBInitialize**接口的引用。</span><span class="sxs-lookup"><span data-stu-id="1167b-118">This example uses the class identifier macro to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object and get a reference to its **IDBInitialize** interface.</span></span>  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 <span data-ttu-id="1167b-119">成功创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端的实例 OLE DB 提供程序数据源对象后，使用者应用程序可以通过初始化数据源并创建会话来继续。</span><span class="sxs-lookup"><span data-stu-id="1167b-119">With successful creation of an instance of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source object, the consumer application can continue by initializing the data source and creating sessions.</span></span> <span data-ttu-id="1167b-120">OLE DB 会话提供允许数据访问和操作的接口。</span><span class="sxs-lookup"><span data-stu-id="1167b-120">OLE DB sessions present the interfaces that allow data access and manipulation.</span></span>  
  
 <span data-ttu-id="1167b-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 成功完成数据源初始化的过程中，使其第一次连接到指定的实例。</span><span class="sxs-lookup"><span data-stu-id="1167b-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider makes its first connection to a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as part of a successful data source initialization.</span></span> <span data-ttu-id="1167b-122">只要保持对数据源初始化接口的引用，或者在调用 IDBInitialize::Uninitialize 方法前，这一连接会一直保持\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1167b-122">The connection is maintained as long as a reference is maintained on any data source initialization interface, or until the **IDBInitialize::Uninitialize** method is called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1167b-123">本节内容</span><span class="sxs-lookup"><span data-stu-id="1167b-123">In This Section</span></span>  
  
-   [<span data-ttu-id="1167b-124">数据源属性 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1167b-124">Data Source Properties &#40;OLE DB&#41;</span></span>](data-source-properties-ole-db.md)  
  
-   [<span data-ttu-id="1167b-125">数据源信息属性</span><span class="sxs-lookup"><span data-stu-id="1167b-125">Data Source Information Properties</span></span>](data-source-information-properties.md)  
  
-   [<span data-ttu-id="1167b-126">初始化和授权属性</span><span class="sxs-lookup"><span data-stu-id="1167b-126">Initialization and Authorization Properties</span></span>](initialization-and-authorization-properties.md)  
  
-   [<span data-ttu-id="1167b-127">会话</span><span class="sxs-lookup"><span data-stu-id="1167b-127">Sessions</span></span>](sessions.md)  
  
-   [<span data-ttu-id="1167b-128">会话属性</span><span class="sxs-lookup"><span data-stu-id="1167b-128">Session Properties</span></span>](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [<span data-ttu-id="1167b-129">持久化数据源对象</span><span class="sxs-lookup"><span data-stu-id="1167b-129">Persisted Data Source Objects</span></span>](persisted-data-source-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="1167b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1167b-130">See Also</span></span>  
 [<span data-ttu-id="1167b-131">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1167b-131">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
