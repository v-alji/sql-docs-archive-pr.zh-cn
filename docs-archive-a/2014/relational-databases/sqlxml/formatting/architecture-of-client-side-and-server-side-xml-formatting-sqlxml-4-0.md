---
title: " (SQLXML 4.0) 的客户端和服务器端 XML 格式的体系结构 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: rothja
ms.author: jroth
ms.openlocfilehash: ae1a9c60a7a7966f4eff2a08b4557487f5aec58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588414"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="86597-102">客户端和服务器端 XML 格式的体系结构 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="86597-102">Architecture of Client-side and Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="86597-103">下图显示服务器端的 XML 格式的体系结构。</span><span class="sxs-lookup"><span data-stu-id="86597-103">The following illustration shows the architecture of XML formatting on the server side.</span></span>  
  
 <span data-ttu-id="86597-104">![服务器端 XML 格式的体系结构。](../../../database-engine/dev-guide/media/serversidexml.gif "服务器端 XML 格式的体系结构。")</span><span class="sxs-lookup"><span data-stu-id="86597-104">![Architecture of XML formatting on the server side.](../../../database-engine/dev-guide/media/serversidexml.gif "Architecture of XML formatting on the server side.")</span></span>  
  
 <span data-ttu-id="86597-105">在该示例中，在客户端上指定的命令将发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="86597-105">In this example, the command that is specified on the client is sent to the server.</span></span> <span data-ttu-id="86597-106">服务器生成 XML 文档，并将它返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="86597-106">The server produces an XML document and returns it to the client.</span></span> <span data-ttu-id="86597-107">在这种情况下，服务器有一个实例 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="86597-107">In this case, the server has an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="86597-108">利用服务器端 XML 格式，可以使用 SQLXMLOLEDB 访问接口或 SQLOLEDB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="86597-108">With server-side XML formatting, you can use either the SQLXMLOLEDB provider or the SQLOLEDB provider.</span></span>  <span data-ttu-id="86597-109">SQLXMLOLEDB 访问接口使用 Sqlxml4.dll，后者包含在 SQLXML 4.0 中。</span><span class="sxs-lookup"><span data-stu-id="86597-109">The SQLXMLOLEDB provider uses Sqlxml4.dll, which is included in SQLXML 4.0.</span></span> <span data-ttu-id="86597-110">使用 SQLOLEDB 访问接口时，默认情况下您将获得由 Sqlxmlx.dll 提供的 SQLXML 功能，该 DLL 随 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 提供或者随附在 Microsoft 数据访问组件 (MDAC) 2.6 或更高版本中。</span><span class="sxs-lookup"><span data-stu-id="86597-110">When you use the SQLOLEDB provider, by default you get the SQLXML functionality provided by Sqlxmlx.dll, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows or in Microsoft Data Access Components (MDAC) 2.6 or later.</span></span> <span data-ttu-id="86597-111">若要将 Sqlxml4.dll 与 SQLOLEDB 一起使用，必须将 SQLOLEDB 版本属性设置为 SQLOLEDB 连接对象上的 "SQLXML. 4.0"。</span><span class="sxs-lookup"><span data-stu-id="86597-111">To use Sqlxml4.dll with SQLOLEDB, you must set the SQLXML Version property to "SQLXML.4.0" on the SQLOLEDB Connection object.</span></span> <span data-ttu-id="86597-112">在这两种情况下，服务器都将生成 XML 文档，并将它发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="86597-112">In either case, the server produces the XML document and sends it to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86597-113">XPath 查询和 Updategram 将在客户端上进行分析。</span><span class="sxs-lookup"><span data-stu-id="86597-113">XPath queries and updategrams are parsed on the client.</span></span> <span data-ttu-id="86597-114">若要获得 SQLXML 4.0 中的 XPath 模板或 Updategram 功能，请使用 Sqlxml4.dll。</span><span class="sxs-lookup"><span data-stu-id="86597-114">To get the XPath template or updategram functionality in SQLXML 4.0, use Sqlxml4.dll.</span></span>  
  
 <span data-ttu-id="86597-115">下图显示客户端的 XML 格式的体系结构：</span><span class="sxs-lookup"><span data-stu-id="86597-115">The following illustration shows the architecture of XML formatting on the client side.</span></span>  
  
 <span data-ttu-id="86597-116">![客户端 XML 格式的体系结构。](../../../database-engine/dev-guide/media/clientsidexml.gif "客户端 XML 格式的体系结构。")</span><span class="sxs-lookup"><span data-stu-id="86597-116">![Architecture of XML formatting on the client side.](../../../database-engine/dev-guide/media/clientsidexml.gif "Architecture of XML formatting on the client side.")</span></span>  
  
 <span data-ttu-id="86597-117">在该示例中，客户端使用 SQLXMLOLEDB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="86597-117">In this example, the client uses the SQLXMLOLEDB provider.</span></span> <span data-ttu-id="86597-118">在连接字符串中，数据访问接口属性必须设置为 SQLOLEDB。</span><span class="sxs-lookup"><span data-stu-id="86597-118">In the connection string, the Data Provider property must be set to SQLOLEDB.</span></span> <span data-ttu-id="86597-119"> (这是 SQLXML 4.0 中唯一接受的值。 ) 在客户端上执行的命令将发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="86597-119">(This is the only value accepted in SQLXML 4.0.) The command that is executed on the client is sent to the server.</span></span> <span data-ttu-id="86597-120">在服务器上生成的行集则发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="86597-120">The rowset that is generated on the server is sent to the client.</span></span> <span data-ttu-id="86597-121">由行集转换至 XML 文档的格式设置操作将在客户端上执行。</span><span class="sxs-lookup"><span data-stu-id="86597-121">The formatting of the XML document from the rowset is performed on the client.</span></span>  
  
 <span data-ttu-id="86597-122">在 SQLXML 4.0 中，可以将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) 或 SQLOLEDB 访问接口用作数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="86597-122">In SQLXML 4.0, either the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) or the SQLOLEDB provider can be used as the data provider.</span></span> <span data-ttu-id="86597-123">您应当可以访问任何数据源。</span><span class="sxs-lookup"><span data-stu-id="86597-123">You can potentially access any data source.</span></span> <span data-ttu-id="86597-124">只要查询返回单个行集，就可以在客户端应用 XML 转换。</span><span class="sxs-lookup"><span data-stu-id="86597-124">As long as the query returns a single rowset, the XML transformation can be applied on the client.</span></span>  
  
  
