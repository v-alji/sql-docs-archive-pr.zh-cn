---
title: 执行异步操作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f7e8f4481923cd7da537f921248865d4fff7280
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688865"
---
# <a name="performing-asynchronous-operations"></a><span data-ttu-id="b5740-102">执行异步操作</span><span class="sxs-lookup"><span data-stu-id="b5740-102">Performing Asynchronous Operations</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="b5740-103">允许应用程序执行异步数据库操作。</span><span class="sxs-lookup"><span data-stu-id="b5740-103">allows applications to perform asynchronous database operations.</span></span> <span data-ttu-id="b5740-104">异步处理将使方法能够立即返回，而不会阻塞调用线程。</span><span class="sxs-lookup"><span data-stu-id="b5740-104">Asynchronous processing enables methods to return immediately without blocking on the calling thread.</span></span> <span data-ttu-id="b5740-105">这使得多线程机制能提供更强大的功能和灵活性，而不需要开发人员显式创建线程或处理同步。</span><span class="sxs-lookup"><span data-stu-id="b5740-105">This allows much of the power and flexibility of multithreading, without requiring the developer to explicitly create threads or handle synchronization.</span></span> <span data-ttu-id="b5740-106">应用程序将在初始化数据库连接时或初始化由执行命令所生成的结果时请求异步处理。</span><span class="sxs-lookup"><span data-stu-id="b5740-106">Applications request asynchronous processing when initializing a database connection, or when initializing the result from the execution of a command.</span></span>  
  
## <a name="opening-and-closing-a-database-connection"></a><span data-ttu-id="b5740-107">打开和关闭数据库连接</span><span class="sxs-lookup"><span data-stu-id="b5740-107">Opening and Closing a Database Connection</span></span>  
 <span data-ttu-id="b5740-108">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序时，旨在异步初始化数据源对象的应用程序可以在调用**IDBInitialize：： initialize**之前设置 DBPROP_INIT_ASYNCH 属性中的 DBPROPVAL_ASYNCH_INITIALIZE 位。</span><span class="sxs-lookup"><span data-stu-id="b5740-108">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, applications designed to initialize a data source object asynchronously can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_INIT_ASYNCH property prior to calling **IDBInitialize::Initialize**.</span></span> <span data-ttu-id="b5740-109">设置此数据时，提供程序立即通过对 Initialize 的调用返回值。如果操作立即完成，则返回 S_OK；如果初始化以异步方式继续进行，则返回 DB_S_ASYNCHRONOUS\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-109">When this property is set, the provider returns immediately from the call to **Initialize** with either S_OK, if the operation has completed immediately, or DB_S_ASYNCHRONOUS, if the initialization is continuing asynchronously.</span></span> <span data-ttu-id="b5740-110">应用程序可以查询数据源对象上的**IDBAsynchStatus**或[ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)接口，然后调用**IDBAsynchStatus：： GetStatus**或[ISSAsynchStatus：： WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)以获取初始化状态。</span><span class="sxs-lookup"><span data-stu-id="b5740-110">Applications can query for the **IDBAsynchStatus** or [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interface on the data source object, and then call **IDBAsynchStatus::GetStatus** or[ISSAsynchStatus::WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) to get the status of the initialization.</span></span>  
  
 <span data-ttu-id="b5740-111">此外，SSPROP_ISSAsynchStatus 属性已添加到 DBPROPSET_SQLSERVERROWSET 属性集。</span><span class="sxs-lookup"><span data-stu-id="b5740-111">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="b5740-112">支持 **ISSAsynchStatus** 接口的提供程序必须使用值 VARIANT_TRUE 实现此属性。</span><span class="sxs-lookup"><span data-stu-id="b5740-112">Providers that support the **ISSAsynchStatus** interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="b5740-113">可调用 IDBAsynchStatus::Abort 或 [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) 来取消 Initialize 异步调用\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-113">**IDBAsynchStatus::Abort** or [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) can be called to cancel the asynchronous **Initialize** call.</span></span> <span data-ttu-id="b5740-114">使用者必须显式请求异步数据源初始化。</span><span class="sxs-lookup"><span data-stu-id="b5740-114">The consumer must explicitly request Asynchronous Data Source Initialization.</span></span> <span data-ttu-id="b5740-115">否则，必须等到数据源对象完全初始化之后，IDBInitialize::Initialize 才返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-115">Otherwise, **IDBInitialize::Initialize** does not return until the data source object is completely initialized.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5740-116">用于连接池的数据源对象无法调用**ISSAsynchStatus** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序中的 ISSAsynchStatus 接口。</span><span class="sxs-lookup"><span data-stu-id="b5740-116">Data source objects used for connection pooling cannot call the **ISSAsynchStatus** interface in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="b5740-117">ISSAsynchStatus 接口不对入池数据源对象公开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-117">The **ISSAsynchStatus** interface is not exposed for pooled data source objects.</span></span>  
>   
>  <span data-ttu-id="b5740-118">如果应用程序显式强制使用游标引擎，则 IOpenRowset::OpenRowset 和 IMultipleResults::GetResult 不支持异步处理\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-118">If an application explicitly forces use of the cursor engine, **IOpenRowset::OpenRowset** and **IMultipleResults::GetResult** will not support asynchronous processing.</span></span>  
>   
>  <span data-ttu-id="b5740-119">此外，MDAC 2.8) 中 (的远程处理代理/存根 dll 无法调用 Native Client 中的**ISSAsynchStatus**接口 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b5740-119">In addition, the remoting proxy/stub dll (in MDAC 2.8) cannot call the **ISSAsynchStatus** interface in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="b5740-120">ISSAsynchStatus 接口不通过远程公开\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-120">The **ISSAsynchStatus** interface is not exposed through remoting.</span></span>  
>   
>  <span data-ttu-id="b5740-121">服务组件不支持 ISSAsynchStatus\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-121">Service Components do not support **ISSAsynchStatus**.</span></span>  
  
## <a name="execution-and-rowset-initialization"></a><span data-ttu-id="b5740-122">执行和行集初始化</span><span class="sxs-lookup"><span data-stu-id="b5740-122">Execution and Rowset Initialization</span></span>  
 <span data-ttu-id="b5740-123">被设计成以异步方式打开由执行命令所生成的结果的应用程序可以设置 DBPROP_ROWSET_ASYNCH 属性中的 DBPROPVAL_ASYNCH_INITIALIZE 位。</span><span class="sxs-lookup"><span data-stu-id="b5740-123">Applications designed to asynchronously open the result from the execution of a command can set the DBPROPVAL_ASYNCH_INITIALIZE bit in the DBPROP_ROWSET_ASYNCH property.</span></span> <span data-ttu-id="b5740-124">在调用 IDBInitialize::Initialize、ICommand::Execute、IOpenRowset::OpenRowset 或 IMultipleResults::GetResult 之前设置该位时，必须将 riid 参数设置为 IID_IDBAsynchStatus、IID_ISSAsynchStatus 或 IID_IUnknown\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-124">When setting this bit prior to calling **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** or **IMultipleResults::GetResult**, the *riid* argument must be set to IID_IDBAsynchStatus, IID_ISSAsynchStatus, or IID_IUnknown.</span></span>  
  
 <span data-ttu-id="b5740-125">该方法立即返回值，且 ppRowset 设置为行集上的请求接口。如果行集初始化立即完成，则返回 S_OK；如果行集继续异步初始化，则返回 DB_S_ASYNCHRONOUS\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-125">The method returns immediately with S_OK if the rowset initialization completes immediately, or with DB_S_ASYNCHRONOUS if the rowset continues initializing asynchronously, with *ppRowset* set to the requested interface on the rowset.</span></span> <span data-ttu-id="b5740-126">对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序，此接口只能是**IDBAsynchStatus**或**ISSAsynchStatus**。</span><span class="sxs-lookup"><span data-stu-id="b5740-126">For the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, this interface can only be **IDBAsynchStatus** or **ISSAsynchStatus**.</span></span> <span data-ttu-id="b5740-127">在行集完全初始化之前，该接口的行为如同处于挂起状态一样，而且对 IID_IDBAsynchStatus 或 IID_ISSAsynchStatus 以外的接口调用 QueryInterface 可能返回 E_NOINTERFACE\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-127">Until the rowset is fully initialized, this interface behaves as if it were in a suspended state, and calling **QueryInterface** for interfaces other than **IID_IDBAsynchStatus** or **IID_ISSAsynchStatus** may return E_NOINTERFACE.</span></span> <span data-ttu-id="b5740-128">除非使用者显式请求异步处理，否则行集将以同步方式执行初始化。</span><span class="sxs-lookup"><span data-stu-id="b5740-128">Unless the consumer explicitly requests asynchronous processing, the rowset is initialized synchronously.</span></span> <span data-ttu-id="b5740-129">如果 IDBAsynchStaus::GetStatus 或 ISSAsynchStatus::WaitForAsynchCompletion 返回的内容指示异步操作已完成，则请求的所有接口均可用\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-129">All requested interfaces are available when **IDBAsynchStaus::GetStatus** or **ISSAsynchStatus::WaitForAsynchCompletion** returns with the indication that asynchronous operation is complete.</span></span> <span data-ttu-id="b5740-130">这不一定意味着行集已完全填充，但它是完整的，且功能齐全。</span><span class="sxs-lookup"><span data-stu-id="b5740-130">This does not necessarily mean that the rowset is fully populated, but it is complete and fully functional.</span></span>  
  
 <span data-ttu-id="b5740-131">即使执行的命令未返回行集，它仍会立即返回支持 IDBAsynchStatus 的对象\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-131">If the executed command does not return a rowset, it still returns immediately with an object that supports **IDBAsynchStatus**.</span></span>  
  
 <span data-ttu-id="b5740-132">如果需要获得由异步命令执行所产生的多个结果，则应当：</span><span class="sxs-lookup"><span data-stu-id="b5740-132">If you need to get multiple results from asynchronous command execution, you should:</span></span>  
  
-   <span data-ttu-id="b5740-133">在执行命令之前，设置 DBPROP_ROWSET_ASYNCH 属性的 DBPROPVAL_ASYNCH_INITIALIZE 位。</span><span class="sxs-lookup"><span data-stu-id="b5740-133">Set the DBPROPVAL_ASYNCH_INITIALIZE bit of the DBPROP_ROWSET_ASYNCH property, before executing the command.</span></span>  
  
-   <span data-ttu-id="b5740-134">调用 ICommand::Execute，并请求 IMultipleResults\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-134">Call **ICommand::Execute**, and request **IMultipleResults**.</span></span>  
  
 <span data-ttu-id="b5740-135">然后，可通过 QueryInterface 查询多个结果接口，从而获得 IDBAsynchStatus 和 ISSAsynchStatus 接口\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-135">The **IDBAsynchStatus** and **ISSAsynchStatus** interfaces can then be obtained by querying the multiple results interface using **QueryInterface**.</span></span>  
  
 <span data-ttu-id="b5740-136">命令执行完毕后，可照常使用 IMultipleResults，但同步时有一个例外，即可能返回 DB_S_ASYNCHRONOUS，此情况下可使用 IDBAsynchStatus 或 ISSAsynchStatus 确定操作的完成时间\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-136">When the command has finished executing, **IMultipleResults** can be used as normal, with one exception from the synchronous case: DB_S_ASYNCHRONOUS may be returned, in which case **IDBAsynchStatus** or **ISSAsynchStatus** can be used to determine when the operation is complete.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b5740-137">示例</span><span class="sxs-lookup"><span data-stu-id="b5740-137">Examples</span></span>  
 <span data-ttu-id="b5740-138">在以下示例中，应用程序调用非阻止方法，执行一些其他处理，然后返回以处理结果。</span><span class="sxs-lookup"><span data-stu-id="b5740-138">In the following example, the application calls a non-blocking method, does some other processing, and then returns to process the results.</span></span> <span data-ttu-id="b5740-139">ISSAsynchStatus::WaitForAsynchCompletion 等待内部事件对象，直到异步执行操作完成，或超过了 dwMilisecTimeOut 指定的时间\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-139">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the amount of time specified by *dwMilisecTimeOut* is passed.</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="b5740-140">ISSAsynchStatus::WaitForAsynchCompletion 等待内部事件对象，直到异步执行操作完成，或传递了 dwMilisecTimeOut 值\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b5740-140">**ISSAsynchStatus::WaitForAsynchCompletion** waits on the internal event object until the asynchronously executing operation is done or the *dwMilisecTimeOut* value is passed.</span></span>  
  
 <span data-ttu-id="b5740-141">以下示例显示有多个结果集的异步处理：</span><span class="sxs-lookup"><span data-stu-id="b5740-141">The following example shows asynchronous processing with multiple result sets:</span></span>  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 <span data-ttu-id="b5740-142">若要阻止阻塞，客户端可以检查异步操作的运行状态，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b5740-142">To prevent blocking, the client can check the status of a running asynchronous operation, as in the following example:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 <span data-ttu-id="b5740-143">以下示例演示如何才能取消当前正在运行的异步操作：</span><span class="sxs-lookup"><span data-stu-id="b5740-143">The following example demonstrates how you can cancel the currently running asynchronous operation:</span></span>  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5740-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5740-144">See Also</span></span>  
 <span data-ttu-id="b5740-145">[SQL Server Native Client 功能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="b5740-145">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 <span data-ttu-id="b5740-146">[行集属性和行为](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span><span class="sxs-lookup"><span data-stu-id="b5740-146">[Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md) </span></span>  
 [<span data-ttu-id="b5740-147">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b5740-147">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
