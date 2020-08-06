---
title: bcp_colptr |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b725ace58ee1768fbca1a433cdea27e3e0e546e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693844"
---
# <a name="bcp_colptr"></a><span data-ttu-id="ff6a1-102">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="ff6a1-102">bcp_colptr</span></span>
  <span data-ttu-id="ff6a1-103">将当前副本的程序变量数据地址设置到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-103">Sets the program variable data address for the current copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6a1-104">语法</span><span class="sxs-lookup"><span data-stu-id="ff6a1-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff6a1-105">参数</span><span class="sxs-lookup"><span data-stu-id="ff6a1-105">Arguments</span></span>  
 <span data-ttu-id="ff6a1-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="ff6a1-106">*hdbc*</span></span>  
 <span data-ttu-id="ff6a1-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="ff6a1-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="ff6a1-108">*pData*</span></span>  
 <span data-ttu-id="ff6a1-109">指向要复制的数据的指针。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-109">Is a pointer to the data to copy.</span></span> <span data-ttu-id="ff6a1-110">如果绑定数据类型为大值类型 (例如 SQLTEXT 或 SQLIMAGE) ，则*pData*可以为 NULL。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-110">If the bound data type is large value type (such as SQLTEXT or SQLIMAGE), *pData* can be NULL.</span></span> <span data-ttu-id="ff6a1-111">空*pData*表示长数据值将使用[bcp_moretext](bcp-moretext.md)发送到块 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-111">A NULL *pData* indicates long data values will be sent to SQL Server in chunks using [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="ff6a1-112">如果将*pData*设置为 NULL，并且与绑定字段对应的列不是大值类型， **bcp_colptr**会失败。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-112">If *pData* is set to NULL and the column corresponding to the bound field is not a large value type, **bcp_colptr** fails.</span></span>  
  
 <span data-ttu-id="ff6a1-113">有关大值类型的详细信息，请参阅[bcp_bind](bcp-bind.md)**。**</span><span class="sxs-lookup"><span data-stu-id="ff6a1-113">For more information on large value types, see [bcp_bind](bcp-bind.md)**.**</span></span>  
  
 <span data-ttu-id="ff6a1-114">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="ff6a1-114">*idxServerCol*</span></span>  
 <span data-ttu-id="ff6a1-115">数据复制的目标数据库表中的列的序号位置。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-115">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="ff6a1-116">表中的第一列为列 1。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-116">The first column in a table is column 1.</span></span> <span data-ttu-id="ff6a1-117">列的序号位置由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)报告。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-117">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ff6a1-118">返回</span><span class="sxs-lookup"><span data-stu-id="ff6a1-118">Returns</span></span>  
 <span data-ttu-id="ff6a1-119">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff6a1-120">备注</span><span class="sxs-lookup"><span data-stu-id="ff6a1-120">Remarks</span></span>  
 <span data-ttu-id="ff6a1-121">使用**bcp_colptr**函数，可以在将数据复制 SQL Server 到[bcp_sendrow](bcp-sendrow.md)时，更改特定列的源数据地址。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-121">The **bcp_colptr** function allows you to change the address of source data for a particular column when copying data to SQL Server with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="ff6a1-122">最初，指向用户数据的指针通过调用**bcp_bind**设置。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-122">Initially, the pointer to user data is set by a call to **bcp_bind**.</span></span> <span data-ttu-id="ff6a1-123">如果程序变量数据地址在对**bcp_sendrow**的调用之间发生更改，则可以调用**bcp_colptr**来重置指向数据的指针。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-123">If the program variable data address changes between calls to **bcp_sendrow**, you can call **bcp_colptr** to reset the pointer to the data.</span></span> <span data-ttu-id="ff6a1-124">对的下一次调用**bcp_sendrow**会将通过调用来寻址的数据发送到**bcp_colptr**。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-124">The next call to **bcp_sendrow** sends the data addressed by the call to **bcp_colptr**.</span></span>  
  
 <span data-ttu-id="ff6a1-125">对于要修改其数据地址的表中的每一列，都必须有单独的**bcp_colptr**调用。</span><span class="sxs-lookup"><span data-stu-id="ff6a1-125">There must be a separate **bcp_colptr** call for every column in the table whose data address you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6a1-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff6a1-126">See Also</span></span>  
 [<span data-ttu-id="ff6a1-127">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="ff6a1-127">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
