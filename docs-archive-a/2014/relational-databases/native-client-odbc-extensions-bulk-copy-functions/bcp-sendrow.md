---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d2f55486ba57101ffc7b1903de5d19ac8eaaca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580240"
---
# <a name="bcp_sendrow"></a><span data-ttu-id="1af19-102">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="1af19-102">bcp_sendrow</span></span>
  <span data-ttu-id="1af19-103">将一行数据从程序变量发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1af19-103">Sends a row of data from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af19-104">语法</span><span class="sxs-lookup"><span data-stu-id="1af19-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1af19-105">参数</span><span class="sxs-lookup"><span data-stu-id="1af19-105">Arguments</span></span>  
 <span data-ttu-id="1af19-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="1af19-106">*hdbc*</span></span>  
 <span data-ttu-id="1af19-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="1af19-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1af19-108">返回</span><span class="sxs-lookup"><span data-stu-id="1af19-108">Returns</span></span>  
 <span data-ttu-id="1af19-109">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="1af19-109">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1af19-110">备注</span><span class="sxs-lookup"><span data-stu-id="1af19-110">Remarks</span></span>  
 <span data-ttu-id="1af19-111">**Bcp_sendrow**函数从程序变量生成行并将其发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1af19-111">The **bcp_sendrow** function builds a row from program variables and sends it to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1af19-112">在调用**bcp_sendrow**之前，必须调用[bcp_bind](bcp-bind.md)以指定包含行数据的程序变量。</span><span class="sxs-lookup"><span data-stu-id="1af19-112">Before calling **bcp_sendrow**, you must make calls to [bcp_bind](bcp-bind.md) to specify the program variables containing row data.</span></span>  
  
 <span data-ttu-id="1af19-113">如果**bcp_bind**指定长度可变的长整型数据类型（例如，SQLTEXT 的*eDataType*参数和非空的*pData*参数），则**bcp_sendrow**发送整型值，正如对任何其他数据类型的情况一样。</span><span class="sxs-lookup"><span data-stu-id="1af19-113">If **bcp_bind** is called specifying a long, variable-length data type, for example, an *eDataType* parameter of SQLTEXT and a nonNULL *pData* parameter, **bcp_sendrow** sends the entiredata value, just as it does for any other data type.</span></span> <span data-ttu-id="1af19-114">但是，如果**bcp_bind**具有 NULL *pData*参数，则**bcp_sendrow**会在将具有指定数据的所有列发送到之后立即将控制权返回给应用程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1af19-114">If, however, **bcp_bind** has a NULL *pData* parameter, **bcp_sendrow** returns control to the application immediately after all columns with data specified are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1af19-115">然后，应用程序可以反复调用[bcp_moretext](bcp-moretext.md)将长的可变长度数据发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，一次发送一个块区。</span><span class="sxs-lookup"><span data-stu-id="1af19-115">The application can then call [bcp_moretext](bcp-moretext.md) repeatedly to send the long, variable-length data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a chunk at a time.</span></span> <span data-ttu-id="1af19-116">有关详细信息，请参阅[bcp_moretext](bcp-moretext.md)。</span><span class="sxs-lookup"><span data-stu-id="1af19-116">For more information, see [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="1af19-117">当使用**bcp_sendrow**将行从程序变量大容量复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中时，仅当用户调用[bcp_batch](bcp-batch.md)或[bcp_done](bcp-done.md)时才提交行。</span><span class="sxs-lookup"><span data-stu-id="1af19-117">When **bcp_sendrow** is used to bulk copy rows from program variables into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, rows are committed only when the user calls [bcp_batch](bcp-batch.md) or [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="1af19-118">用户可以选择每*n*行调用一次**bcp_batch** ，或在传入数据的时间段之间进行趋缓。</span><span class="sxs-lookup"><span data-stu-id="1af19-118">The user can choose to call **bcp_batch** once every *n* rows or when there is a lull between periods of incoming data.</span></span> <span data-ttu-id="1af19-119">如果永远不会调用**bcp_batch** ，则在调用**bcp_done**时将提交行。</span><span class="sxs-lookup"><span data-stu-id="1af19-119">If **bcp_batch** is never called, the rows are committed when **bcp_done** is called.</span></span>  
  
 <span data-ttu-id="1af19-120">有关从开始大容量复制的重大更改的信息 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，请参阅[&#40;ODBC&#41;执行大容量复制操作](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="1af19-120">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af19-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1af19-121">See Also</span></span>  
 [<span data-ttu-id="1af19-122">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="1af19-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
