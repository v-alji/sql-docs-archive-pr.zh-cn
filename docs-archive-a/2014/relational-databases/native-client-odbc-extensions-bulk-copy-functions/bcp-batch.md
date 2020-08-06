---
title: bcp_batch |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: rothja
ms.author: jroth
ms.openlocfilehash: 24cdf6e2934c2b80a55d8fa1fcc572a976b636ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586636"
---
# <a name="bcp_batch"></a><span data-ttu-id="cd546-102">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="cd546-102">bcp_batch</span></span>
  <span data-ttu-id="cd546-103">将以前从程序变量大容量复制的所有行提交 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 到[bcp_sendrow](bcp-sendrow.md)。</span><span class="sxs-lookup"><span data-stu-id="cd546-103">Commits all rows previously bulk copied from program variables and sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd546-104">语法</span><span class="sxs-lookup"><span data-stu-id="cd546-104">Syntax</span></span>  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd546-105">参数</span><span class="sxs-lookup"><span data-stu-id="cd546-105">Arguments</span></span>  
 <span data-ttu-id="cd546-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="cd546-106">*hdbc*</span></span>  
 <span data-ttu-id="cd546-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="cd546-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cd546-108">返回</span><span class="sxs-lookup"><span data-stu-id="cd546-108">Returns</span></span>  
 <span data-ttu-id="cd546-109">在最后一次调用**bcp_batch**之后保存的行数; 如果出现错误，则为-1。</span><span class="sxs-lookup"><span data-stu-id="cd546-109">The number of rows saved after the last call to **bcp_batch**, or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd546-110">备注</span><span class="sxs-lookup"><span data-stu-id="cd546-110">Remarks</span></span>  
 <span data-ttu-id="cd546-111">大容量复制批处理定义事务。</span><span class="sxs-lookup"><span data-stu-id="cd546-111">Bulk copy batches define transactions.</span></span> <span data-ttu-id="cd546-112">当应用程序使用[bcp_bind](bcp-bind.md)和**bcp_sendrow**将行从程序变量大容量复制到 SQL Server 表时，只在程序调用**bcp_batch**或[bcp_done](bcp-done.md)时才提交行。</span><span class="sxs-lookup"><span data-stu-id="cd546-112">When an application uses [bcp_bind](bcp-bind.md) and **bcp_sendrow** to bulk copy rows from program variables to SQL Server tables, the rows are committed only when the program calls **bcp_batch** or [bcp_done](bcp-done.md).</span></span>  
  
 <span data-ttu-id="cd546-113">可以在每*n*行调用一次 bcp_batch，也可以在传入数据 (时调用**bcp_batch** ，就像在遥测应用程序) 中一样。</span><span class="sxs-lookup"><span data-stu-id="cd546-113">You can call **bcp_batch** once every *n* rows or when there is a lull in incoming data (as in a telemetry application).</span></span> <span data-ttu-id="cd546-114">如果应用程序不调用**bcp_batch**仅当调用**bcp_done**时才提交大容量复制的行。</span><span class="sxs-lookup"><span data-stu-id="cd546-114">If an application does not call **bcp_batch** the bulk copied rows are committed only when **bcp_done** is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd546-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd546-115">See Also</span></span>  
 [<span data-ttu-id="cd546-116">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="cd546-116">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
