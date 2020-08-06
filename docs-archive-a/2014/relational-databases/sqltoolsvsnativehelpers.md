---
title: SqlToolsVSNativeHelpers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84f8a3a3408b68cb8c389b05b417f391a1f86c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694404"
---
# <a name="sqltoolsvsnativehelpers"></a><span data-ttu-id="b2c32-102">SqlToolsVSNativeHelpers</span><span class="sxs-lookup"><span data-stu-id="b2c32-102">SqlToolsVSNativeHelpers</span></span>
  <span data-ttu-id="b2c32-103">在 Visual Studio 中支持 SQL Server 功能的库。</span><span class="sxs-lookup"><span data-stu-id="b2c32-103">Library that supports SQL Server functionality in Visual Studio.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c32-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2c32-104">Syntax</span></span>  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a><span data-ttu-id="b2c32-105">返回值</span><span class="sxs-lookup"><span data-stu-id="b2c32-105">Return Value</span></span>  
 <span data-ttu-id="b2c32-106">一个布尔值，如果 DLL 入口点正确初始化，则为 `True`，否则为 `False`。</span><span class="sxs-lookup"><span data-stu-id="b2c32-106">A Boolean value, `True` if the DLL entry point initialized properly, otherwise `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c32-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2c32-107">See Also</span></span>  
 [<span data-ttu-id="b2c32-108">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="b2c32-108">FrameWindowVisible</span></span>](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
