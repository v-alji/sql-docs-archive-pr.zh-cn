---
title: 设置会话语言 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
ms.openlocfilehash: da8d6adce66ac5b97e533b5afaefabda40e4b966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591400"
---
# <a name="set-a-session-language"></a><span data-ttu-id="f73d1-102">设置会话语言</span><span class="sxs-lookup"><span data-stu-id="f73d1-102">Set a Session Language</span></span>
  <span data-ttu-id="f73d1-103">根据语言和区域性首选项，可用会话语言设置下列元素在服务器上显示的方式：</span><span class="sxs-lookup"><span data-stu-id="f73d1-103">The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:</span></span>  
  
-   <span data-ttu-id="f73d1-104">用于显示错误和其他系统消息的语言。</span><span class="sxs-lookup"><span data-stu-id="f73d1-104">The language that will be used for error and other system messages.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f73d1-105">可用的所有语言中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持所有系统错误字符串和系统错误消息拥有多个副本。</span><span class="sxs-lookup"><span data-stu-id="f73d1-105">supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is available.</span></span> <span data-ttu-id="f73d1-106">可以在 [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) 目录视图中查看这些消息。</span><span class="sxs-lookup"><span data-stu-id="f73d1-106">These messages can be viewed in the [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) catalog view.</span></span> <span data-ttu-id="f73d1-107">安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地化版本时，这些系统消息被翻译成所安装的语言版本。</span><span class="sxs-lookup"><span data-stu-id="f73d1-107">When you install a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], these system messages are translated for the language version that you install.</span></span> <span data-ttu-id="f73d1-108">默认情况下，也可以获得这些消息的美国英语集。</span><span class="sxs-lookup"><span data-stu-id="f73d1-108">By default, you also obtain the U.S. English set of these messages.</span></span> <span data-ttu-id="f73d1-109">此外，可以使用 [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)添加特定语言的用户定义消息。</span><span class="sxs-lookup"><span data-stu-id="f73d1-109">Additionally, you can add user-defined messages in a specific language by using [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span></span>  
  
-   <span data-ttu-id="f73d1-110">日期和时间数据的格式。</span><span class="sxs-lookup"><span data-stu-id="f73d1-110">The format of date and time data.</span></span>  
  
-   <span data-ttu-id="f73d1-111">日和月的名称，包括缩写。</span><span class="sxs-lookup"><span data-stu-id="f73d1-111">The names of days and months, including abbreviations.</span></span>  
  
-   <span data-ttu-id="f73d1-112">周的第一天。</span><span class="sxs-lookup"><span data-stu-id="f73d1-112">The first day of the week.</span></span>  
  
-   <span data-ttu-id="f73d1-113">货币数据。</span><span class="sxs-lookup"><span data-stu-id="f73d1-113">Currency data.</span></span>  
  
 <span data-ttu-id="f73d1-114">有 33 种语言可用于会话设置。</span><span class="sxs-lookup"><span data-stu-id="f73d1-114">There are 33 languages available for use as session settings.</span></span> <span data-ttu-id="f73d1-115">有关语言列表，请参阅 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f73d1-115">For a list of languages, see [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-server"></a><span data-ttu-id="f73d1-116">从服务器设置会话语言</span><span class="sxs-lookup"><span data-stu-id="f73d1-116">Setting the Session Language from the Server</span></span>  
 <span data-ttu-id="f73d1-117">若要从服务器设置会话语言，请使用 [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f73d1-117">To set the session language from the server side, use [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-client"></a><span data-ttu-id="f73d1-118">从客户端设置会话语言</span><span class="sxs-lookup"><span data-stu-id="f73d1-118">Setting the Session Language from the Client</span></span>  
 <span data-ttu-id="f73d1-119">可以用 OLE DB、ODBC 或 ADO.NET 在客户端设置会话语言。</span><span class="sxs-lookup"><span data-stu-id="f73d1-119">The session language can be set on the client side by using OLE DB, ODBC or ADO.NET.</span></span> <span data-ttu-id="f73d1-120">对于 OLE DB，请使用 SSPROP_INIT_CURRENTLANGUAGE 属性。</span><span class="sxs-lookup"><span data-stu-id="f73d1-120">For OLE DB, use the SSPROP_INIT_CURRENTLANGUAGE property.</span></span> <span data-ttu-id="f73d1-121">有关详细信息，请参阅 [初始化和授权属性](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f73d1-121">For more information, see [Initialization and Authorization Properties](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).</span></span>  
  
 <span data-ttu-id="f73d1-122">对于 ODBC，请使用语言关键字。</span><span class="sxs-lookup"><span data-stu-id="f73d1-122">For ODBC, use the Language keyword.</span></span> <span data-ttu-id="f73d1-123">有关详细信息，请参阅 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)。</span><span class="sxs-lookup"><span data-stu-id="f73d1-123">For more information, see [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="f73d1-124">对于 ADO.NET，请使用 **ConnectionString** 对象的 **Current Language** 参数。</span><span class="sxs-lookup"><span data-stu-id="f73d1-124">For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object.</span></span> <span data-ttu-id="f73d1-125">有关详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) 软件开发包 (SDK) 文档。</span><span class="sxs-lookup"><span data-stu-id="f73d1-125">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) software development kit (SDK) documentation.</span></span>  
  
  
