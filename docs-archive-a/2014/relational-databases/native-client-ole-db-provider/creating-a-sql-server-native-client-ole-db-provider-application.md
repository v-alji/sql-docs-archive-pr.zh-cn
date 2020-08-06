---
title: 创建 SQL Server Native Client OLE DB 提供程序应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: a661f23cdacc4b581dadbe7625cb6e2ea318857f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688885"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a><span data-ttu-id="c7397-102">创建 SQL Server Native Client OLE DB 访问接口应用程序</span><span class="sxs-lookup"><span data-stu-id="c7397-102">Creating a SQL Server Native Client OLE DB Provider Application</span></span>
  <span data-ttu-id="c7397-103">创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序应用程序涉及以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c7397-103">Creating a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider application involves these steps:</span></span>  
  
1.  <span data-ttu-id="c7397-104">建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="c7397-104">Establishing a connection to a data source.</span></span>  
  
2.  <span data-ttu-id="c7397-105">执行命令。</span><span class="sxs-lookup"><span data-stu-id="c7397-105">Executing a command.</span></span>  
  
3.  <span data-ttu-id="c7397-106">结果处理。</span><span class="sxs-lookup"><span data-stu-id="c7397-106">Processing the results.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7397-107">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c7397-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="c7397-108">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="c7397-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="c7397-109">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="c7397-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="c7397-110">如果必须保存凭据，应当用 [Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) 对它们加密。</span><span class="sxs-lookup"><span data-stu-id="c7397-110">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7397-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="c7397-111">In This Section</span></span>  
  
-   [<span data-ttu-id="c7397-112">建立与数据源的连接</span><span class="sxs-lookup"><span data-stu-id="c7397-112">Establishing a Connection to a Data Source</span></span>](establishing-a-connection-to-a-data-source.md)  
  
-   [<span data-ttu-id="c7397-113">执行命令</span><span class="sxs-lookup"><span data-stu-id="c7397-113">Executing a Command</span></span>](executing-a-command.md)  
  
-   [<span data-ttu-id="c7397-114">处理结果</span><span class="sxs-lookup"><span data-stu-id="c7397-114">Processing Results</span></span>](processing-results.md)  
  
-   [<span data-ttu-id="c7397-115">关于 OLE DB 属性</span><span class="sxs-lookup"><span data-stu-id="c7397-115">About OLE DB Properties</span></span>](about-ole-db-properties.md)  
  
-   [<span data-ttu-id="c7397-116">在 SQL Server Native Client 中使用 OUTPUT 子句 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c7397-116">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7397-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7397-117">See Also</span></span>  
 [<span data-ttu-id="c7397-118">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c7397-118">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
