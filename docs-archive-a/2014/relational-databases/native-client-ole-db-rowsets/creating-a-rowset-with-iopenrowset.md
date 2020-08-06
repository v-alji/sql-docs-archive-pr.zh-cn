---
title: 使用 IOpenRowset 创建行集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692883"
---
# <a name="creating-a-rowset-with-iopenrowset"></a><span data-ttu-id="0fc74-102">使用 IOpenRowset 创建行集</span><span class="sxs-lookup"><span data-stu-id="0fc74-102">Creating a Rowset with IOpenRowset</span></span>
  <span data-ttu-id="0fc74-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持**IOpenRowset：： OpenRowset**方法，但有以下限制：</span><span class="sxs-lookup"><span data-stu-id="0fc74-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the **IOpenRowset::OpenRowset** method with the following restrictions:</span></span>  
  
-   <span data-ttu-id="0fc74-104">必须在 pTableID 参数指向的数据库 ID (DBID) 结构中指定基表或视图\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fc74-104">A base table or view must be specified in a database ID (DBID) structure that the *pTableID* parameter points to.</span></span>  
  
-   <span data-ttu-id="0fc74-105">DBID eKind 成员必须指示 DBKIND_NAME\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fc74-105">The DBID *eKind* member must indicate DBKIND_NAME.</span></span>  
  
-   <span data-ttu-id="0fc74-106">DBID uName 成员必须将现有基表或视图的名称指定为 Unicode 字符串\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fc74-106">The DBID *uName* member must specify the name of an existing base table or a view as a Unicode character string.</span></span>  
  
-   <span data-ttu-id="0fc74-107">OpenRowset 的 pIndexID 参数必须为 NULL\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fc74-107">The *pIndexID* parameter of **OpenRowset** must be NULL.</span></span>  
  
 <span data-ttu-id="0fc74-108">IOpenRowset::OpenRowset 的结果集包含单个行集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fc74-108">The result set of **IOpenRowset::OpenRowset** contains a single rowset.</span></span> <span data-ttu-id="0fc74-109">游标可以支持包含单个行集的结果集 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0fc74-109">Result sets that contain a single rowset can be supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursors.</span></span> <span data-ttu-id="0fc74-110">游标支持允许开发人员使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并发控制机制。</span><span class="sxs-lookup"><span data-stu-id="0fc74-110">Cursor support allows the developer to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concurrency mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc74-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fc74-111">See Also</span></span>  
 [<span data-ttu-id="0fc74-112">行集</span><span class="sxs-lookup"><span data-stu-id="0fc74-112">Rowsets</span></span>](rowsets.md)  
  
  
