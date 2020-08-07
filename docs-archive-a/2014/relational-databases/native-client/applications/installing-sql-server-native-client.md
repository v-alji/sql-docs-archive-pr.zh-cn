---
title: 正在安装 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 86a30924dc6dfc0b5b4f4dc176f0186d8f35b2f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587775"
---
# <a name="installing-sql-server-native-client"></a><span data-ttu-id="3c66a-102">安装 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="3c66a-102">Installing SQL Server Native Client</span></span>
  <span data-ttu-id="3c66a-103">在安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]时，将同时安装 Microsoft [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client 11.0。</span><span class="sxs-lookup"><span data-stu-id="3c66a-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 is installed when you install [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="3c66a-104">没有 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="3c66a-104">There is no [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client.</span></span> <span data-ttu-id="3c66a-105">有关详细信息，请参阅[SQL Server Native Client 中的新增功能](../sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="3c66a-105">For more information, see [What's New in SQL Server Native Client](../sql-server-native-client.md).</span></span> <span data-ttu-id="3c66a-106">你还可以从 SQL Server 2012 功能包网页获取 sqlncli.msi。</span><span class="sxs-lookup"><span data-stu-id="3c66a-106">You can also get sqlncli.msi from the SQL Server 2012 Feature Pack web page.</span></span> <span data-ttu-id="3c66a-107">若要下载最新版本的 SQL Server Native Client，请访问[Microsoft？？SQL Server？？2012 SP2 功能包](https://www.microsoft.com/download/details.aspx?id=43339)。</span><span class="sxs-lookup"><span data-stu-id="3c66a-107">To download the most recent version of the SQL Server Native Client, go to [Microsoft?? SQL Server?? 2012 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=43339).</span></span> <span data-ttu-id="3c66a-108">如果计算机上还安装了早于 SQL Server 2012 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的以前版本，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 将与早期版本并行安装。</span><span class="sxs-lookup"><span data-stu-id="3c66a-108">If a previous version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client earlier than SQL Server 2012 is also installed on the computer, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 will be installed side-by-side with the earlier version.</span></span>  
  
 <span data-ttu-id="3c66a-109"> Native Client 文件（sqlncli11.dll、sqlnclir11.rll 和 s11ch_sqlncli.chm）将安装到以下位置：</span><span class="sxs-lookup"><span data-stu-id="3c66a-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client files (sqlncli11.dll, sqlnclir11.rll, and s11ch_sqlncli.chm) are installed to the following location:</span></span>  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  <span data-ttu-id="3c66a-110"> Native Client OLE DB 访问接口和  Native Client ODBC 驱动程序的所有相应注册表设置都将在安装过程中完成。</span><span class="sxs-lookup"><span data-stu-id="3c66a-110">All appropriate registry settings for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="3c66a-111"> Native Client 头文件和库文件（sqlncli.h 和 sqlncli11.lib）安装在以下位置：</span><span class="sxs-lookup"><span data-stu-id="3c66a-111">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files (sqlncli.h and sqlncli11.lib) are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 <span data-ttu-id="3c66a-112">除了作为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装过程的一部分安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 以外，还可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装磁盘的以下位置找到名为 sqlncli.msi 的可再发行安装程序：`%CD%\Setup\`。</span><span class="sxs-lookup"><span data-stu-id="3c66a-112">In addition to installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation, there is also a redistributable installation program named sqlncli.msi, which can be found on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation disk in the following location: `%CD%\Setup\`.</span></span>  
  
 <span data-ttu-id="3c66a-113">您可以通过 sqlncli.msi 分发 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="3c66a-113">You can distribute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client through sqlncli.msi.</span></span> <span data-ttu-id="3c66a-114">在您部署某一应用程序时，可能需要安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="3c66a-114">You might have to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client when you deploy an application.</span></span> <span data-ttu-id="3c66a-115">安装多个包（对于用户而言就像是一次安装）的一种方法就是使用链接器和引导程序技术。</span><span class="sxs-lookup"><span data-stu-id="3c66a-115">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="3c66a-116">有关详细信息，请参阅[为 Visual Studio 2005 创作自定义引导程序包](https://go.microsoft.com/fwlink/?LinkId=115667)和[添加自定义系统必备](https://go.microsoft.com/fwlink/?LinkId=115668)。</span><span class="sxs-lookup"><span data-stu-id="3c66a-116">For more information, see [Authoring a Custom Bootstrapper Package for Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) and [Adding Custom Prerequisites](https://go.microsoft.com/fwlink/?LinkId=115668).</span></span>  
  
 <span data-ttu-id="3c66a-117">sqlncli.msi 的 x64 和 Itanium 版本也会安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的 32 位版。</span><span class="sxs-lookup"><span data-stu-id="3c66a-117">The x64 and Itanium versions of sqlncli.msi also install the 32-bit version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="3c66a-118">如果您的应用程序所针对的目标平台并非其开发时所使用的平台，则可以从 Microsoft 下载中心下载针对 x64、Itanium 和 x86 的 sqlncli.msi 版本。</span><span class="sxs-lookup"><span data-stu-id="3c66a-118">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="3c66a-119">在调用 sqlncli.msi 时，默认情况下只会安装客户端组件。</span><span class="sxs-lookup"><span data-stu-id="3c66a-119">When you invoke sqlncli.msi, only the client components are installed by default.</span></span> <span data-ttu-id="3c66a-120">客户端组件是支持运行使用 Native Client 开发的应用程序的文件 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3c66a-120">The client components are files that support running an application that was developed using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="3c66a-121">若还要安装 SDK 组件，请在命令行中指定 `ADDLOCAL=All`。</span><span class="sxs-lookup"><span data-stu-id="3c66a-121">To also install the SDK components, specify `ADDLOCAL=All` on the command line.</span></span> <span data-ttu-id="3c66a-122">例如：</span><span class="sxs-lookup"><span data-stu-id="3c66a-122">For example:</span></span>  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a><span data-ttu-id="3c66a-123">无提示安装</span><span class="sxs-lookup"><span data-stu-id="3c66a-123">Silent Install</span></span>  
 <span data-ttu-id="3c66a-124">如果您将 /passive、/qn、/qb 或 /qr 选项与 msiexec 一起使用，则必须还指定 IACCEPTSQLNCLILICENSETERMS=YES，以便显式指示您接受最终用户许可协议条款。</span><span class="sxs-lookup"><span data-stu-id="3c66a-124">If you use the /passive, /qn, /qb, or /qr option with msiexec, you must also specify IACCEPTSQLNCLILICENSETERMS=YES, to explicitly indicate that you accept the terms of the end user license.</span></span> <span data-ttu-id="3c66a-125">必须以全大写字母指定此选项。</span><span class="sxs-lookup"><span data-stu-id="3c66a-125">This option must be specified in all capital letters.</span></span>  
  
## <a name="uninstalling-sql-server-native-client"></a><span data-ttu-id="3c66a-126">卸载 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="3c66a-126">Uninstalling SQL Server Native Client</span></span>  
 <span data-ttu-id="3c66a-127">由于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务器和工具等应用程序 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 依赖于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client，因此在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 卸载所有从属应用程序之前，不要卸载 Native client。</span><span class="sxs-lookup"><span data-stu-id="3c66a-127">Because applications such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tools depend on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, it is important not to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client until all dependent applications are uninstalled.</span></span> <span data-ttu-id="3c66a-128">若要向用户提供应用程序依赖于 Native Client 的警告， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 请使用 MSI 中的 APPGUID 安装选项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3c66a-128">To provider users with a warning that your application depends on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, use the APPGUID install option in your MSI, as follows:</span></span>  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 <span data-ttu-id="3c66a-129">传递给 APPGUID 的值是您的特定产品代码。</span><span class="sxs-lookup"><span data-stu-id="3c66a-129">The value passed to APPGUID is your specific product code.</span></span> <span data-ttu-id="3c66a-130">当使用 Microsoft Installer 捆绑应用程序安装程序时，必须创建产品代码。</span><span class="sxs-lookup"><span data-stu-id="3c66a-130">A product code must be created when using Microsoft Installer to bundle your application setup program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c66a-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c66a-131">See Also</span></span>  
 <span data-ttu-id="3c66a-132">[构建具有 SQL Server Native Client 的应用程序](installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="3c66a-132">[Building Applications with SQL Server Native Client](installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="3c66a-133">安装操作指南主题</span><span class="sxs-lookup"><span data-stu-id="3c66a-133">Installation How-to Topics</span></span>](../../../sql-server/install/installation-how-to-topics.md)  
  
  
