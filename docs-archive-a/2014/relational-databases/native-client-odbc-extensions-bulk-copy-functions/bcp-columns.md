---
title: bcp_columns |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: rothja
ms.author: jroth
ms.openlocfilehash: 028bb80e88a29b366e3a489abae06c8b3b30cdf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688897"
---
# <a name="bcp_columns"></a><span data-ttu-id="46716-102">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="46716-102">bcp_columns</span></span>
  <span data-ttu-id="46716-103">用于设置在以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作为源或目标执行大容量复制时所用的用户文件中找到的列的总数。</span><span class="sxs-lookup"><span data-stu-id="46716-103">Sets the total number of columns found in the user file for use with a bulk copy into or out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46716-104">可以使用[bcp_setbulkmode](bcp-setbulkmode.md) ，而不是 bcp_columns 和[bcp_colfmt](bcp-colfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="46716-104">[bcp_setbulkmode](bcp-setbulkmode.md) can be used instead of bcp_columns and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46716-105">语法</span><span class="sxs-lookup"><span data-stu-id="46716-105">Syntax</span></span>  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="46716-106">参数</span><span class="sxs-lookup"><span data-stu-id="46716-106">Arguments</span></span>  
 <span data-ttu-id="46716-107">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="46716-107">*hdbc*</span></span>  
 <span data-ttu-id="46716-108">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="46716-108">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="46716-109">*nColumns*</span><span class="sxs-lookup"><span data-stu-id="46716-109">*nColumns*</span></span>  
 <span data-ttu-id="46716-110">用户文件中的列的总数。</span><span class="sxs-lookup"><span data-stu-id="46716-110">Is the total number of columns in the user file.</span></span> <span data-ttu-id="46716-111">即使您准备将数据从用户文件大容量复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表，并且不想复制用户文件中的所有列，仍必须将*nColumns*设置为用户文件列总数。</span><span class="sxs-lookup"><span data-stu-id="46716-111">Even if you are preparing to bulk copy data from the user file to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and do not intend to copy all columns in the user file, you must still set *nColumns* to the total number of user-file columns.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="46716-112">返回</span><span class="sxs-lookup"><span data-stu-id="46716-112">Returns</span></span>  
 <span data-ttu-id="46716-113">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="46716-113">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46716-114">备注</span><span class="sxs-lookup"><span data-stu-id="46716-114">Remarks</span></span>  
 <span data-ttu-id="46716-115">仅当使用有效的文件名调用[bcp_init](bcp-init.md)之后，才能调用此函数。</span><span class="sxs-lookup"><span data-stu-id="46716-115">This function can be called only after [bcp_init](bcp-init.md) has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="46716-116">仅当您要使用不同于默认设置的用户文件格式时，才应当调用该函数。</span><span class="sxs-lookup"><span data-stu-id="46716-116">You should call this function only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="46716-117">有关默认用户文件格式的说明的详细信息，请参阅**bcp_init**。</span><span class="sxs-lookup"><span data-stu-id="46716-117">For more information about a description of the default user-file format, see **bcp_init**.</span></span>  
  
 <span data-ttu-id="46716-118">调用后 `bcp_columns` ，必须对用户文件中的每个列调用[bcp_colfmt](bcp-colfmt.md)以完全定义自定义文件格式。</span><span class="sxs-lookup"><span data-stu-id="46716-118">After calling `bcp_columns`, you must call [bcp_colfmt](bcp-colfmt.md)for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46716-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46716-119">See Also</span></span>  
 [<span data-ttu-id="46716-120">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="46716-120">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
