---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693842"
---
# <a name="bcp_collen"></a><span data-ttu-id="8d28e-102">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="8d28e-102">bcp_collen</span></span>
  <span data-ttu-id="8d28e-103">为目标为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的当前大容量复制设置程序变量中的数据长度。</span><span class="sxs-lookup"><span data-stu-id="8d28e-103">Sets the data length in the program variable for the current bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d28e-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d28e-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d28e-105">参数</span><span class="sxs-lookup"><span data-stu-id="8d28e-105">Arguments</span></span>  
 <span data-ttu-id="8d28e-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="8d28e-106">*hdbc*</span></span>  
 <span data-ttu-id="8d28e-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="8d28e-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="8d28e-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="8d28e-108">*cbData*</span></span>  
 <span data-ttu-id="8d28e-109">程序变量中数据的长度，不包括任何长度指示器或终止符的长度。</span><span class="sxs-lookup"><span data-stu-id="8d28e-109">Is the length of the data in the program variable, not including the length of any length indicator or terminator.</span></span> <span data-ttu-id="8d28e-110">将*cbData*设置为 SQL_NULL_DATA 指示复制到服务器的所有行都包含该列的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="8d28e-110">Setting *cbData* to SQL_NULL_DATA indicates all rows copied to the server contain a NULL value for the column.</span></span> <span data-ttu-id="8d28e-111">设置为 SQL_VARLEN_DATA 则指示使用字符串终止符或其他方法确定复制的数据的长度。</span><span class="sxs-lookup"><span data-stu-id="8d28e-111">Setting it to SQL_VARLEN_DATA indicates that a string terminator or other method is used to determine the length of data copied.</span></span> <span data-ttu-id="8d28e-112">如果同时提供长度指示器和终止符，系统将使用二者中复制数据量较少的一个。</span><span class="sxs-lookup"><span data-stu-id="8d28e-112">If both a length indicator and a terminator exist, the system uses whichever one results in less data being copied.</span></span>  
  
 <span data-ttu-id="8d28e-113">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="8d28e-113">*idxServerCol*</span></span>  
 <span data-ttu-id="8d28e-114">数据复制到的表中的列的序号位置。</span><span class="sxs-lookup"><span data-stu-id="8d28e-114">Is the ordinal position of the column in the table to which the data is copied.</span></span> <span data-ttu-id="8d28e-115">第一列为 1。</span><span class="sxs-lookup"><span data-stu-id="8d28e-115">The first column is 1.</span></span> <span data-ttu-id="8d28e-116">列的序号位置由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)报告。</span><span class="sxs-lookup"><span data-stu-id="8d28e-116">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="8d28e-117">返回</span><span class="sxs-lookup"><span data-stu-id="8d28e-117">Returns</span></span>  
 <span data-ttu-id="8d28e-118">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="8d28e-118">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d28e-119">备注</span><span class="sxs-lookup"><span data-stu-id="8d28e-119">Remarks</span></span>  
 <span data-ttu-id="8d28e-120">使用**bcp_collen**函数，可以在将数据复制到具有 bcp_sendrow 时，更改特定列的程序变量中的数据长度 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="8d28e-120">The **bcp_collen** function allows you to change the data length in the program variable for a particular column when copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="8d28e-121">最初，数据长度是在调用[bcp_bind](bcp-bind.md)时确定的。</span><span class="sxs-lookup"><span data-stu-id="8d28e-121">Initially, the data length is determined when [bcp_bind](bcp-bind.md) is called.</span></span> <span data-ttu-id="8d28e-122">如果数据长度在对**bcp_sendrow**的调用之间发生更改，并且没有使用长度前缀或终止符，则可以调用**bcp_collen**来重置长度。</span><span class="sxs-lookup"><span data-stu-id="8d28e-122">If the data length changes between calls to **bcp_sendrow** and no length prefix or terminator is being used, you can call **bcp_collen** to reset the length.</span></span> <span data-ttu-id="8d28e-123">对**bcp_sendrow**的下一次调用使用由对**bcp_collen**的调用设置的长度。</span><span class="sxs-lookup"><span data-stu-id="8d28e-123">The next call to **bcp_sendrow** uses the length set by the call to **bcp_collen**.</span></span>  
  
 <span data-ttu-id="8d28e-124">您必须对要修改其数据长度的表中的每一列调用一次**bcp_collen** 。</span><span class="sxs-lookup"><span data-stu-id="8d28e-124">You must call **bcp_collen** once for each column in the table whose data length you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d28e-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d28e-125">See Also</span></span>  
 [<span data-ttu-id="8d28e-126">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="8d28e-126">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
