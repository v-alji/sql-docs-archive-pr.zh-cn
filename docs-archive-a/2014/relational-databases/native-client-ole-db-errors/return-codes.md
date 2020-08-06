---
title: 返回代码 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: rothja
ms.author: jroth
ms.openlocfilehash: dd033d16b1e95773d2cab1c4e1fca733dc491b96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589538"
---
# <a name="return-codes"></a><span data-ttu-id="932bb-102">返回代码</span><span class="sxs-lookup"><span data-stu-id="932bb-102">Return Codes</span></span>
  <span data-ttu-id="932bb-103">在最基本的级别上，成员函数要么成功，要么失败。</span><span class="sxs-lookup"><span data-stu-id="932bb-103">At the most basic level, a member function either succeeds or fails.</span></span> <span data-ttu-id="932bb-104">在稍微精确一些的级别上，函数可能会成功，但是它的成功可能并不是应用程序开发人员想要的成功。</span><span class="sxs-lookup"><span data-stu-id="932bb-104">At a somewhat more precise level, a function can succeed, but its success may not be what the application developer intended.</span></span>  
  
 <span data-ttu-id="932bb-105">有关 OLE DB 返回代码的详细信息，请参阅 [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631)（返回代码 (OLE DB)）。</span><span class="sxs-lookup"><span data-stu-id="932bb-105">For more information about OLE DB return codes, see [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).</span></span>  
  
 <span data-ttu-id="932bb-106">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序成员函数返回 S_OK 时，该函数将成功。</span><span class="sxs-lookup"><span data-stu-id="932bb-106">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function returns S_OK, the function succeeded.</span></span>  
  
 <span data-ttu-id="932bb-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序成员函数未返回 S_OK，则 OLE/COM HRESULT 解压缩失败，IS_ERROR 宏可以确定函数的总体成功或失败。</span><span class="sxs-lookup"><span data-stu-id="932bb-107">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function does not return S_OK, the OLE/COM HRESULT-unpacking FAILED and IS_ERROR macros can determine the overall success or failure of a function.</span></span>  
  
 <span data-ttu-id="932bb-108">如果 FAILED 或 IS_ERROR 返回 TRUE，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者可确保成员函数执行失败。</span><span class="sxs-lookup"><span data-stu-id="932bb-108">If FAILED or IS_ERROR returns TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that member function execution failed.</span></span> <span data-ttu-id="932bb-109">如果失败或 IS_ERROR 返回 FALSE，并且 HRESULT 不等于 S_OK，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用者可确保函数在某种程度上成功。</span><span class="sxs-lookup"><span data-stu-id="932bb-109">When FAILED or IS_ERROR return FALSE and the HRESULT does not equal S_OK, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that the function succeeded in some sense.</span></span> <span data-ttu-id="932bb-110">使用者可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序错误接口返回有关此 "包含信息成功" 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="932bb-110">The consumer can retrieve detailed information on this "success with information" return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span> <span data-ttu-id="932bb-111">此外，如果函数明显失败 (则失败的宏将返回 TRUE) ，从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序错误接口可以获得扩展的错误信息。</span><span class="sxs-lookup"><span data-stu-id="932bb-111">Also, in the case where a function clearly fails (the FAILED macro returns TRUE), extended error information is available from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="932bb-112">Native Client OLE DB 提供者通常会遇到 "信息成功" HRESULT 返回 DB_S_ERRORSOCCURRED。</span><span class="sxs-lookup"><span data-stu-id="932bb-112">Native Client OLE DB provider consumers commonly encounter the DB_S_ERRORSOCCURRED "success with information" HRESULT return.</span></span> <span data-ttu-id="932bb-113">通常，返回 DB_S_ERRORSOCCURRED 的成员函数会定义一个或多个将状态值传递给使用者的参数。</span><span class="sxs-lookup"><span data-stu-id="932bb-113">Typically, member functions that return DB_S_ERRORSOCCURRED define one or more parameters that deliver status values to the consumer.</span></span> <span data-ttu-id="932bb-114">除了在状态值参数中返回的错误信息之外，使用者无法获得其他任何错误信息，因此使用者应将应用程序逻辑实现为在有可用的状态值时检索这些状态值。</span><span class="sxs-lookup"><span data-stu-id="932bb-114">No error information may be available to the consumer other than that returned in status-value parameters, so consumers should implement application logic to retrieve status values when they are available.</span></span>  
  
 <span data-ttu-id="932bb-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序成员函数不会返回成功代码 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="932bb-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions do not return the success code S_FALSE.</span></span> <span data-ttu-id="932bb-116">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序成员函数始终返回 S_OK 以指示成功。</span><span class="sxs-lookup"><span data-stu-id="932bb-116">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions always return S_OK to indicate success.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="932bb-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="932bb-117">See Also</span></span>  
 [<span data-ttu-id="932bb-118">错误</span><span class="sxs-lookup"><span data-stu-id="932bb-118">Errors</span></span>](errors.md)  
  
  
