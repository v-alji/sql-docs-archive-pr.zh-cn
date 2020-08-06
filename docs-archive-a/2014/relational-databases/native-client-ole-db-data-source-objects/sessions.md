---
title: 会话 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 3a980816-675c-4fba-acc9-429297d85bbd
author: rothja
ms.author: jroth
ms.openlocfilehash: 545f301a9a73691dd19bb11476d005219b2f982f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591879"
---
# <a name="sessions"></a><span data-ttu-id="916c5-102">会话</span><span class="sxs-lookup"><span data-stu-id="916c5-102">Sessions</span></span>
  <span data-ttu-id="916c5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序会话表示到实例的单个连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="916c5-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session represents a single connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="916c5-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序要求会话分隔数据源的事务空间。</span><span class="sxs-lookup"><span data-stu-id="916c5-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requires that sessions delimit transaction space for a data source.</span></span> <span data-ttu-id="916c5-105">通过某一特定会话对象创建的所有命令对象均参与该会话对象的本地事务或分布式事务。</span><span class="sxs-lookup"><span data-stu-id="916c5-105">All command objects created from a specific session object participate in the local or distributed transaction of the session object.</span></span>  
  
 <span data-ttu-id="916c5-106">在已初始化数据源上创建的第一个会话对象接收在初始化期间建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接。</span><span class="sxs-lookup"><span data-stu-id="916c5-106">The first session object created on the initialized data source receives the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection established at initialization.</span></span> <span data-ttu-id="916c5-107">当释放该会话对象的接口上的所有引用时，在该数据源上创建的其他会话对象即可使用与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="916c5-107">When all references on the interfaces of the session object are released, the connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] becomes available to another session object created on the data source.</span></span>  
  
 <span data-ttu-id="916c5-108">在数据源上创建的其他会话对象建立其自身到该数据源指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="916c5-108">An additional session object created on the data source establishes its own connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as specified by the data source.</span></span> <span data-ttu-id="916c5-109">当应用程序释放对创建该会话的对象的所有引用时，将删除与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="916c5-109">The connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is dropped when the application releases all references to objects created that session.</span></span>  
  
 <span data-ttu-id="916c5-110">下面的示例演示如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库：</span><span class="sxs-lookup"><span data-stu-id="916c5-110">The following example demonstrates how to use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:</span></span>  
  
```  
int main()  
{  
    // Interfaces used in the example.  
    IDBInitialize*      pIDBInitialize      = NULL;  
    IDBCreateSession*   pIDBCreateSession   = NULL;  
    IDBCreateCommand*   pICreateCmd1        = NULL;  
    IDBCreateCommand*   pICreateCmd2        = NULL;  
    IDBCreateCommand*   pICreateCmd3        = NULL;  
  
    // Initialize COM.  
    if (FAILED(CoInitialize(NULL)))  
    {  
        // Display error from CoInitialize.  
        return (-1);  
    }  
  
    // Get the memory allocator for this task.  
    if (FAILED(CoGetMalloc(MEMCTX_TASK, &g_pIMalloc)))  
    {  
        // Display error from CoGetMalloc.  
        goto EXIT;  
    }  
  
    // Create an instance of the data source object.  
    if (FAILED(CoCreateInstance(CLSID_SQLNCLI10, NULL,  
        CLSCTX_INPROC_SERVER, IID_IDBInitialize, (void**)  
        &pIDBInitialize)))  
    {  
        // Display error from CoCreateInstance.  
        goto EXIT;  
    }  
  
    // The InitFromPersistedDS function   
    // performs IDBInitialize->Initialize() establishing  
    // the first application connection to the instance of SQL Server.  
    if (FAILED(InitFromPersistedDS(pIDBInitialize, L"MyDataSource",  
        NULL, NULL)))  
    {  
        goto EXIT;  
    }  
  
    // The IDBCreateSession interface is implemented on the data source  
    // object. Maintaining the reference received maintains the   
    // connection of the data source to the instance of SQL Server.  
    if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,  
        (void**) &pIDBCreateSession)))  
    {  
        // Display error from pIDBInitialize.  
        goto EXIT;  
    }  
  
    // Releasing this has no effect on the SQL Server connection  
    // of the data source object because of the reference maintained by  
    // pIDBCreateSession.  
    pIDBInitialize->Release();  
    pIDBInitialize = NULL;  
  
    // The session created next receives the SQL Server connection of  
    // the data source object. No new connection is established.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd1)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // A new connection to the instance of SQL Server is established to support the  
    // next session object created. On successful completion, the  
    // application has two active connections on the SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd2)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
    // pICreateCmd1 has the data source connection. Because the  
    // reference on the IDBCreateSession interface of the data source  
    // has not been released, releasing the reference on the session  
    // object does not terminate a connection to the instance of SQL Server.  
    // However, the connection of the data source object is now   
    // available to another session object. After a successful call to   
    // Release, the application still has two active connections to the   
    // instance of SQL Server.  
    pICreateCmd1->Release();  
    pICreateCmd1 = NULL;  
  
    // The next session created gets the SQL Server connection  
    // of the data source object. The application has two active  
    // connections to the instance of SQL Server.  
    if (FAILED(pIDBCreateSession->CreateSession(NULL,  
        IID_IDBCreateCommand, (IUnknown**) &pICreateCmd3)))  
    {  
        // Display error from pIDBCreateSession.  
        goto EXIT;  
    }  
  
EXIT:  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd1 has the connection of the data source   
    // object.  
    if (pICreateCmd1 != NULL)  
        pICreateCmd1->Release();  
  
    // Releasing the reference on pICreateCmd2 terminates the SQL  
    // Server connection supporting the session object. The application  
    // now has only a single active connection on the instance of SQL Server.  
    if (pICreateCmd2 != NULL)  
        pICreateCmd2->Release();  
  
    // Even on error, this does not terminate a SQL Server connection   
    // because pICreateCmd3 has the connection of the   
    // data source object.  
    if (pICreateCmd3 != NULL)  
        pICreateCmd3->Release();  
  
    // On release of the last reference on a data source interface, the  
    // connection of the data source object to the instance of SQL Server is broken.  
    // The example application now has no SQL Server connections active.  
    if (pIDBCreateSession != NULL)  
        pIDBCreateSession->Release();  
  
    // Called only if an error occurred while attempting to get a   
    // reference on the IDBCreateSession interface of the data source.  
    // If so, the call to IDBInitialize::Uninitialize terminates the   
    // connection of the data source object to the instance of SQL Server.  
    if (pIDBInitialize != NULL)  
    {  
        if (FAILED(pIDBInitialize->Uninitialize()))  
        {  
            // Uninitialize is not required, but it fails if an  
            // interface has not been released. Use it for  
            // debugging.  
        }  
        pIDBInitialize->Release();  
    }  
  
    if (g_pIMalloc != NULL)  
        g_pIMalloc->Release();  
  
    CoUninitialize();  
  
    return (0);  
}  
```  
  
 <span data-ttu-id="916c5-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]将 Native Client OLE DB 提供程序会话对象连接到的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能会导致持续创建和释放会话对象的应用程序产生很大的开销。</span><span class="sxs-lookup"><span data-stu-id="916c5-111">Connecting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session objects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can generate significant overhead for applications that continually create and release session objects.</span></span> <span data-ttu-id="916c5-112">可以通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有效地管理 Native Client OLE DB 提供程序会话对象来最大程度地降低开销。</span><span class="sxs-lookup"><span data-stu-id="916c5-112">The overhead can be minimized by managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session objects efficiently.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="916c5-113">Native Client OLE DB 提供程序应用程序可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过在对象的至少一个接口上维护引用来保持会话对象的连接处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="916c5-113">Native Client OLE DB provider applications can keep the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection of a session object active by maintaining a reference on at least one interface of the object.</span></span>  
  
 <span data-ttu-id="916c5-114">例如，维护命令创建对象引用池将保持该池中这些会话对象的活动连接。</span><span class="sxs-lookup"><span data-stu-id="916c5-114">For example, maintaining a pool of command creation object references keeps active connections for those session objects in the pool.</span></span> <span data-ttu-id="916c5-115">由于需要会话对象，因此，池维护代码将向需要会话的应用程序方法传递有效的 IDBCreateCommand\*\*\*\* 接口指针。</span><span class="sxs-lookup"><span data-stu-id="916c5-115">As session objects are required, the pool maintenance code passes a valid **IDBCreateCommand** interface pointer to the application method requiring the session.</span></span> <span data-ttu-id="916c5-116">当应用程序方法不再需要该会话时，该方法将接口指针返回到池维护代码，而不是释放应用程序对命令创建对象的引用。</span><span class="sxs-lookup"><span data-stu-id="916c5-116">When the application method no longer requires the session, the method returns the interface pointer back to the pool maintenance code rather than releasing the application's reference to the command creation object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="916c5-117">在前面的示例中，使用 IDBCreateCommand\*\*\*\* 接口的原因在于 ICommand\*\*\*\* 接口实现 GetDBSession\*\*\*\* 方法，该方法是命令或行集作用域中允许对象确定创建其会话的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="916c5-117">In the preceding example, the **IDBCreateCommand** interface is used because the **ICommand** interface implements the **GetDBSession** method, the only method in command or rowset scope that allows an object to determine the session on which it was created.</span></span> <span data-ttu-id="916c5-118">因此，只有命令对象才允许应用程序检索可创建其他会话的数据源对象指针。</span><span class="sxs-lookup"><span data-stu-id="916c5-118">Therefore, a command object, and only a command object, allows an application to retrieve a data source object pointer from which additional sessions can be created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916c5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="916c5-119">See Also</span></span>  
 [<span data-ttu-id="916c5-120">数据源对象 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="916c5-120">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
