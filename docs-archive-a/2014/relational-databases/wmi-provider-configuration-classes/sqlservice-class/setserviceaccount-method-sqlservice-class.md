---
title: SetServiceAccount 方法 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6087a531802a7752ea794a44147c79fb7c3fa3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687595"
---
# <a name="setserviceaccount-method-sqlservice-class"></a><span data-ttu-id="02eb8-102">SetServiceAccount 方法（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="02eb8-102">SetServiceAccount Method (SqlService Class)</span></span>
  <span data-ttu-id="02eb8-103">尝试更改运行服务实例时使用的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="02eb8-103">Attempts to change the user name and password that the service instance runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02eb8-104">语法</span><span class="sxs-lookup"><span data-stu-id="02eb8-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="02eb8-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="02eb8-105">Parts</span></span>  
 <span data-ttu-id="02eb8-106">对象</span><span class="sxs-lookup"><span data-stu-id="02eb8-106">*object*</span></span>  
 <span data-ttu-id="02eb8-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="02eb8-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="02eb8-108">参数</span><span class="sxs-lookup"><span data-stu-id="02eb8-108">Parameters</span></span>  
 <span data-ttu-id="02eb8-109">*ServiceStartName*</span><span class="sxs-lookup"><span data-stu-id="02eb8-109">*ServiceStartName*</span></span>  
 <span data-ttu-id="02eb8-110">一个指定运行服务所用帐户名的字符串值。</span><span class="sxs-lookup"><span data-stu-id="02eb8-110">A string value that specifies the account name that the service runs under.</span></span> <span data-ttu-id="02eb8-111">根据不同的服务类型，帐户名可能的格式为“域名\用户名”。</span><span class="sxs-lookup"><span data-stu-id="02eb8-111">Depending on the service type, the account name might be in the form of DomainName\Username.</span></span> <span data-ttu-id="02eb8-112">服务进程运行时，将使用以下两种格式之一登录：</span><span class="sxs-lookup"><span data-stu-id="02eb8-112">When it runs, the service process will be logged using one of two forms:</span></span>  
  
-   <span data-ttu-id="02eb8-113">如果帐户属于内置域，则可以指定“\用户名”。</span><span class="sxs-lookup"><span data-stu-id="02eb8-113">If the account belongs to the built-in domain, \Username can be specified.</span></span>  
  
-   <span data-ttu-id="02eb8-114">如果指定 NULL，则该服务将作为**LocalSystem**帐户登录。</span><span class="sxs-lookup"><span data-stu-id="02eb8-114">If NULL is specified, the service will be logged on as the **LocalSystem** account.</span></span>  
  
 <span data-ttu-id="02eb8-115">对于内核或系统级驱动程序， *StartName*包含驱动程序对象名称（\FileSystem\Rdr 或 \Driver\Xns），i/o 系统使用该名称加载设备驱动程序。</span><span class="sxs-lookup"><span data-stu-id="02eb8-115">For kernel or system-level drivers, *StartName* contains the driver object name, either \FileSystem\Rdr or \Driver\Xns, which the I/O system uses to load the device driver.</span></span> <span data-ttu-id="02eb8-116">如果指定 NULL，驱动程序将以 I/O 系统基于服务名称创建的默认对象名称运行，例如 DWDOM\Admin。</span><span class="sxs-lookup"><span data-stu-id="02eb8-116">If NULL is specified, the driver runs with a default object name created by the I/O system based on the service name, for example, DWDOM\Admin.</span></span>  
  
 <span data-ttu-id="02eb8-117">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="02eb8-117">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="02eb8-118">一个字符串值，该值指定*StartName*参数中的帐户名称的密码。</span><span class="sxs-lookup"><span data-stu-id="02eb8-118">A string value that specifies the password for the account name in the *StartName* parameter.</span></span> <span data-ttu-id="02eb8-119">如果不更改密码，请指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="02eb8-119">Specify NULL if you are not changing the password.</span></span> <span data-ttu-id="02eb8-120">如果服务没有密码，请指定一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="02eb8-120">Specify an empty string if the service has no password.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="02eb8-121">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="02eb8-121">Property Value/Return Value</span></span>  
 <span data-ttu-id="02eb8-122">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1。</span><span class="sxs-lookup"><span data-stu-id="02eb8-122">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="02eb8-123">其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="02eb8-123">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02eb8-124">备注</span><span class="sxs-lookup"><span data-stu-id="02eb8-124">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02eb8-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02eb8-125">See Also</span></span>  
 <span data-ttu-id="02eb8-126">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="02eb8-126">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
