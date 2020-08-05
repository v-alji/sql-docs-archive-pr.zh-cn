---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0752220cc20641d9b51a3a66fecc86f9efd63433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581253"
---
# <a name="mssqlserver_33081"></a><span data-ttu-id="a9984-102">MSSQLSERVER_33081</span><span class="sxs-lookup"><span data-stu-id="a9984-102">MSSQLSERVER_33081</span></span>
    
## <a name="details"></a><span data-ttu-id="a9984-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a9984-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9984-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a9984-104">Product Name</span></span>|<span data-ttu-id="a9984-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a9984-105">SQL Server</span></span>|  
|<span data-ttu-id="a9984-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a9984-106">Event ID</span></span>|<span data-ttu-id="a9984-107">33081</span><span class="sxs-lookup"><span data-stu-id="a9984-107">33081</span></span>|  
|<span data-ttu-id="a9984-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a9984-108">Event Source</span></span>|<span data-ttu-id="a9984-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a9984-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a9984-110">组件</span><span class="sxs-lookup"><span data-stu-id="a9984-110">Component</span></span>|<span data-ttu-id="a9984-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a9984-111">SQLEngine</span></span>|  
|<span data-ttu-id="a9984-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a9984-112">Symbolic Name</span></span>|<span data-ttu-id="a9984-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span><span class="sxs-lookup"><span data-stu-id="a9984-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span></span>|  
|<span data-ttu-id="a9984-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a9984-114">Message Text</span></span>|<span data-ttu-id="a9984-115">由于 Authenticode 签名或文件路径无效，未能加载加密提供程序“%.\*ls”。</span><span class="sxs-lookup"><span data-stu-id="a9984-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span>  <span data-ttu-id="a9984-116">请检查以前的消息，了解其他失败信息。</span><span class="sxs-lookup"><span data-stu-id="a9984-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a9984-117">说明</span><span class="sxs-lookup"><span data-stu-id="a9984-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a9984-118">无法加载错误消息中列出的加密提供程序。</span><span class="sxs-lookup"><span data-stu-id="a9984-118">was unable to load the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="a9984-119">几个 Windows API 失败可能导致此错误。</span><span class="sxs-lookup"><span data-stu-id="a9984-119">There are several Win API failures which might cause this error.</span></span> <span data-ttu-id="a9984-120">环形缓冲区包含失败的 API 的名称和 API 返回的 Windows 错误代码。</span><span class="sxs-lookup"><span data-stu-id="a9984-120">The ring buffer contains the name of the failed API and the Windows error code returned by the API.</span></span> <span data-ttu-id="a9984-121">若要获取更多信息，请使用以下查询来查询 sys.dm_os_ring_buffers 视图。</span><span class="sxs-lookup"><span data-stu-id="a9984-121">To get more information, query the sys.dm_os_ring_buffers view using the following query.</span></span>  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a><span data-ttu-id="a9984-122">用户操作</span><span class="sxs-lookup"><span data-stu-id="a9984-122">User Action</span></span>  
 <span data-ttu-id="a9984-123">若要调查问题，请在 MSDN (https://msdn.microsoft.com/) 中搜索该 Windows 错误代码。</span><span class="sxs-lookup"><span data-stu-id="a9984-123">To investigate the problem, search for the Windows error code in MSDN (https://msdn.microsoft.com/).</span></span> <span data-ttu-id="a9984-124">解决该问题，或联系 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户支持服务部门以获得详细信息。</span><span class="sxs-lookup"><span data-stu-id="a9984-124">Resolve the error, or contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS for more information.</span></span> <span data-ttu-id="a9984-125">如果需要与客户支持服务部门联系，请为我们的支持人员收集以下信息。</span><span class="sxs-lookup"><span data-stu-id="a9984-125">If you need to contact CSS, collect the following information for our support staff.</span></span>  
  
-   <span data-ttu-id="a9984-126">错误日志显示无法加载加密提供程序错误。</span><span class="sxs-lookup"><span data-stu-id="a9984-126">The error log showing the failed to load cryptographic provider error.</span></span>  
  
-   <span data-ttu-id="a9984-127">执行以下语句所得到的输出：</span><span class="sxs-lookup"><span data-stu-id="a9984-127">The output from the following statement:</span></span>  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="a9984-128">尝试立即收集环形缓冲区信息，因为重新启动期间该信息会丢失。</span><span class="sxs-lookup"><span data-stu-id="a9984-128">Try to collect the ring buffer information promptly as ring buffer information can be lost during a restart.</span></span>  
  
  
