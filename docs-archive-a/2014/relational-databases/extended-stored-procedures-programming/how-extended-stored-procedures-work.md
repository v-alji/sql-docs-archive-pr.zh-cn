---
title: 扩展存储过程的工作方式 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589092"
---
# <a name="how-extended-stored-procedures-work"></a><span data-ttu-id="4989c-102">扩展存储过程的工作方式</span><span class="sxs-lookup"><span data-stu-id="4989c-102">How Extended Stored Procedures Work</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="4989c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="4989c-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="4989c-104">扩展存储过程的工作流程是：</span><span class="sxs-lookup"><span data-stu-id="4989c-104">The process by which an extended stored procedure works is:</span></span>  
  
1.  <span data-ttu-id="4989c-105">当客户端执行扩展存储过程时，请求将以表格格式数据流 (TDS) 或简单对象访问协议 (SOAP) 格式从客户端应用程序传输到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4989c-105">When a client executes an extended stored procedure, the request is transmitted in tabular data stream (TDS) or Simple Object Access Protocol (SOAP) format from the client application to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4989c-106">搜索与扩展存储过程关联的 DLL 并加载此 DLL（如果尚未加载）。</span><span class="sxs-lookup"><span data-stu-id="4989c-106">searches for the DLL associated with the extended stored procedure, and loads the DLL if it is not already loaded.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4989c-107">调用请求的扩展存储过程（在 DLL 内部作为函数实现）。</span><span class="sxs-lookup"><span data-stu-id="4989c-107">calls the requested extended stored procedure (implemented as a function inside the DLL).</span></span>  
  
4.  <span data-ttu-id="4989c-108">扩展存储过程通过扩展存储过程 API 传递结果集，并将参数返回给服务器。</span><span class="sxs-lookup"><span data-stu-id="4989c-108">The extended stored procedure passes result sets and return parameters back to the server by through the Extended Stored Procedure API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4989c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4989c-109">See Also</span></span>  
 [<span data-ttu-id="4989c-110">数据库引擎扩展存储过程编程</span><span class="sxs-lookup"><span data-stu-id="4989c-110">Database Engine Extended Stored Procedure Programming</span></span>](../database-engine-extended-stored-procedure-programming.md)  
  
  
