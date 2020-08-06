---
title: 运行存储过程 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e6ce951f343002feea5aa793d0cc2092422b819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692345"
---
# <a name="running-stored-procedures-ole-db"></a><span data-ttu-id="26011-102">运行存储过程 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="26011-102">Running Stored Procedures (OLE DB)</span></span>
  <span data-ttu-id="26011-103">执行语句时，对数据源调用存储过程（而不是直接在客户端应用程序中执行或准备语句）可以：</span><span class="sxs-lookup"><span data-stu-id="26011-103">When executing statements, calling a stored procedure on the data source (instead of executing or preparing a statement in the client application directly) can provide:</span></span>  
  
-   <span data-ttu-id="26011-104">提高性能。</span><span class="sxs-lookup"><span data-stu-id="26011-104">Higher performance.</span></span>  
  
-   <span data-ttu-id="26011-105">降低网络开销。</span><span class="sxs-lookup"><span data-stu-id="26011-105">Reduced network overhead.</span></span>  
  
-   <span data-ttu-id="26011-106">提供更好的一致性。</span><span class="sxs-lookup"><span data-stu-id="26011-106">Better consistency.</span></span>  
  
-   <span data-ttu-id="26011-107">提高准确性。</span><span class="sxs-lookup"><span data-stu-id="26011-107">Better accuracy.</span></span>  
  
-   <span data-ttu-id="26011-108">增加功能。</span><span class="sxs-lookup"><span data-stu-id="26011-108">Added functionality.</span></span>  
  
 <span data-ttu-id="26011-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 存储过程用于返回数据的三个机制：</span><span class="sxs-lookup"><span data-stu-id="26011-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports three of the mechanisms that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures use to return data:</span></span>  
  
-   <span data-ttu-id="26011-110">过程中的每一条 SELECT 语句都生成一个结果集。</span><span class="sxs-lookup"><span data-stu-id="26011-110">Every SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="26011-111">过程可以通过输出参数返回数据。</span><span class="sxs-lookup"><span data-stu-id="26011-111">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="26011-112">过程可以具有整数返回代码。</span><span class="sxs-lookup"><span data-stu-id="26011-112">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="26011-113">应用程序必须能够处理来自存储过程的所有这些输出。</span><span class="sxs-lookup"><span data-stu-id="26011-113">The application must be able to handle all of these outputs from stored procedures.</span></span>  
  
 <span data-ttu-id="26011-114">在结果处理期间，不同的 OLE DB 访问接口返回输出参数和返回值的时间不同。</span><span class="sxs-lookup"><span data-stu-id="26011-114">Different OLE DB providers return output parameters and return values at different times during result processing.</span></span> <span data-ttu-id="26011-115">对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序，在使用者检索或取消存储过程返回的结果集之前，不会提供输出参数和返回代码。</span><span class="sxs-lookup"><span data-stu-id="26011-115">In case of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the output parameters and return codes are not supplied until after the consumer has retrieved or canceled the result sets returned by the stored procedure.</span></span> <span data-ttu-id="26011-116">返回代码和输出参数在最后一个来自服务器的 TDS 数据包中返回。</span><span class="sxs-lookup"><span data-stu-id="26011-116">The return codes and the output parameters are returned in the last TDS packet from the server.</span></span>  
  
 <span data-ttu-id="26011-117">访问接口返回输出参数和返回值时，使用 DBPROP_OUTPUTPARAMETERAVAILABILITY 属性进行报告。</span><span class="sxs-lookup"><span data-stu-id="26011-117">Providers use the DBPROP_OUTPUTPARAMETERAVAILABILITY property to report when it returns output parameters and return values.</span></span> <span data-ttu-id="26011-118">此属性位于 DBPROPSET_DATASOURCEINFO 属性集中。</span><span class="sxs-lookup"><span data-stu-id="26011-118">This property is in the DBPROPSET_DATASOURCEINFO property set.</span></span>  
  
 <span data-ttu-id="26011-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序将 DBPROP_OUTPUTPARAMETERAVAILABILITY 属性设置为 DBPROPVAL_OA_ATROWRELEASE，以指示在处理或释放结果集之前，不会返回返回代码和输出参数。</span><span class="sxs-lookup"><span data-stu-id="26011-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets the DBPROP_OUTPUTPARAMETERAVAILABILITY property to DBPROPVAL_OA_ATROWRELEASE to indicate that return codes and output parameters are not returned until the result set is processed or released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26011-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26011-120">See Also</span></span>  
 [<span data-ttu-id="26011-121">存储过程</span><span class="sxs-lookup"><span data-stu-id="26011-121">Stored Procedures</span></span>](stored-procedures.md)  
  
  
