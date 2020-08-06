---
title: ISQLServerErrorInfo (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISQLServerErrorInfo interface
ms.assetid: a8323b5c-686a-4235-a8d2-bda43617b3a1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 222349bcaa88058dea1d9c5302883667c22d4092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694084"
---
# <a name="isqlservererrorinfo-ole-db"></a><span data-ttu-id="5b957-102">ISQLServerErrorInfo (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="5b957-102">ISQLServerErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="5b957-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序定义**ISQLServerErrorInfo**错误接口。</span><span class="sxs-lookup"><span data-stu-id="5b957-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the **ISQLServerErrorInfo** error interface.</span></span> <span data-ttu-id="5b957-104">此接口从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误返回详细信息，包括其严重性和状态。</span><span class="sxs-lookup"><span data-stu-id="5b957-104">This interface returns details from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error, including its severity and state.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b957-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="5b957-105">In This Section</span></span>  
  
|<span data-ttu-id="5b957-106">方法</span><span class="sxs-lookup"><span data-stu-id="5b957-106">Method</span></span>|<span data-ttu-id="5b957-107">说明</span><span class="sxs-lookup"><span data-stu-id="5b957-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b957-108">ISQLServerErrorInfo：： GetErrorInfo &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="5b957-108">ISQLServerErrorInfo::GetErrorInfo &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)|<span data-ttu-id="5b957-109">返回一个指针，该指针指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误详细信息的 Native Client OLE DB provider SSERRORINFO 结构。</span><span class="sxs-lookup"><span data-stu-id="5b957-109">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b957-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b957-110">See Also</span></span>  
 <span data-ttu-id="5b957-111">[接口 &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="5b957-111">[Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="5b957-112">SQL Server 错误详细信息</span><span class="sxs-lookup"><span data-stu-id="5b957-112">SQL Server Error Detail</span></span>](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
  
