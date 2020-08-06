---
title: 在表格模式下安装 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688327"
---
# <a name="install-analysis-services-in-tabular-mode"></a><span data-ttu-id="333e5-102">在表格模式下安装 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="333e5-102">Install Analysis Services in Tabular Mode</span></span>
  <span data-ttu-id="333e5-103">如果您要安装 Analysis Services 以便使用新增的表格建模功能，则必须在支持这种模型的服务器模式下安装 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="333e5-103">If you are installing Analysis Services to use the new tabular modeling features, you must install Analysis Services in a server mode that supports that type of model.</span></span> <span data-ttu-id="333e5-104">服务器是表格模式，在安装过程中配置。</span><span class="sxs-lookup"><span data-stu-id="333e5-104">The server mode is Tabular, and it is configured during installation.</span></span>  
  
 <span data-ttu-id="333e5-105">在这种模式下安装了服务器后，可以用它来承载在表格模型设计器中构建的解决方案。</span><span class="sxs-lookup"><span data-stu-id="333e5-105">After you install the server in this mode, you can use it host solutions that you build in tabular model designer.</span></span> <span data-ttu-id="333e5-106">如果您想通过网络来访问表格模型数据，则需要表格模式服务器。</span><span class="sxs-lookup"><span data-stu-id="333e5-106">A tabular mode server is required if you want tabular model data access over the network.</span></span>  
  
 <span data-ttu-id="333e5-107">可在安装向导或命令行安装程序中指定表格模式。</span><span class="sxs-lookup"><span data-stu-id="333e5-107">You can specify Tabular mode in the Installation Wizard or in a command line setup.</span></span> <span data-ttu-id="333e5-108">以下部分介绍了各种方法。</span><span class="sxs-lookup"><span data-stu-id="333e5-108">The following sections describe each approach.</span></span>  
  
## <a name="installation-wizard"></a><span data-ttu-id="333e5-109">安装向导</span><span class="sxs-lookup"><span data-stu-id="333e5-109">Installation Wizard</span></span>  
 <span data-ttu-id="333e5-110">下面的列表显示了 SQL Server 安装向导中的哪些页用来在表格模式下安装 Analysis Services：</span><span class="sxs-lookup"><span data-stu-id="333e5-110">The following list shows you which pages in the SQL Server Installation wizard are used to install Analysis Services in Tabular mode:</span></span>  
  
1.  <span data-ttu-id="333e5-111">从安装程序的功能树中选择 **“Analysis Services”** 。</span><span class="sxs-lookup"><span data-stu-id="333e5-111">Select **Analysis Services** from the Feature Tree in Setup.</span></span>  
  
     <span data-ttu-id="333e5-112">![设置显示 Analsyis Services 的功能树](../../../sql-server/install/media/ssas-setupas.gif "设置显示 Analsyis Services 的功能树")</span><span class="sxs-lookup"><span data-stu-id="333e5-112">![Setup feature tree showing Analsyis Services](../../../sql-server/install/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")</span></span>  
  
2.  <span data-ttu-id="333e5-113">在 "Analysis Services 配置" 页上，确保选择 "**表格模式**"。</span><span class="sxs-lookup"><span data-stu-id="333e5-113">On the Analysis Services Configuration page, be sure to select **Tabular Mode**.</span></span>  
  
     <span data-ttu-id="333e5-114">![包含 Analysis Services 配置选项的“设置”页](../../../sql-server/install/media/ssas-setupasconfig.gif "包含 Analysis Services 配置选项的“设置”页")</span><span class="sxs-lookup"><span data-stu-id="333e5-114">![Setup page with Analysis Services config options](../../../sql-server/install/media/ssas-setupasconfig.gif "Setup page with Analysis Services config options")</span></span>  
  
 <span data-ttu-id="333e5-115">表格模式使用 xVelocity 内存中分析引擎 (VertiPaq)，该引擎是部署到 Analysis Services 的表格模型的默认存储器。</span><span class="sxs-lookup"><span data-stu-id="333e5-115">Tabular mode uses the xVelocity in-memory analytics engine (VertiPaq), which is the default storage for tabular models that you deploy to Analysis Services.</span></span> <span data-ttu-id="333e5-116">将表格模型解决方案部署到服务器之后，可以有选择性地配置表格解决方案，以便将 DirectQuery 磁盘存储作为受内存限制的存储的替代项。</span><span class="sxs-lookup"><span data-stu-id="333e5-116">After you deploy tabular model solutions to the server, you can selectively configure tabular solutions to use DirectQuery disk storage as an alternative to memory-bound storage.</span></span>  
  
## <a name="command-line-setup"></a><span data-ttu-id="333e5-117">命令行安装程序</span><span class="sxs-lookup"><span data-stu-id="333e5-117">Command Line Setup</span></span>  
 <span data-ttu-id="333e5-118">SQL Server 安装程序包含一个用来指定服务器模式的新参数 (`ASSERVERMODE`)。</span><span class="sxs-lookup"><span data-stu-id="333e5-118">SQL Server Setup includes a new parameter (`ASSERVERMODE`) that specifies the server mode.</span></span> <span data-ttu-id="333e5-119">下面的示例说明了用来在表格服务器模式下安装 Analysis Services 的命令行安装程序。</span><span class="sxs-lookup"><span data-stu-id="333e5-119">The following example illustrates a command line setup that installs Analysis Services in Tabular server mode.</span></span>  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="333e5-120">`INSTANCENAME` 必须少于 17 个字符。</span><span class="sxs-lookup"><span data-stu-id="333e5-120">`INSTANCENAME` must be less than 17 characters.</span></span>  
  
 <span data-ttu-id="333e5-121">所有占位符帐户的值必须替换为有效的帐户和密码。</span><span class="sxs-lookup"><span data-stu-id="333e5-121">All placeholder account values must be replaced with valid accounts and password.</span></span>  
  
 <span data-ttu-id="333e5-122">未使用提供的示例命令行语法安装工具（例如 SQL Server Management Studio 或 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]）。</span><span class="sxs-lookup"><span data-stu-id="333e5-122">Tools such as SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] are not installed using the example command line syntax that is provided.</span></span> <span data-ttu-id="333e5-123">有关添加功能的详细信息，请参阅[从命令提示符安装 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="333e5-123">For more information about adding features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
 <span data-ttu-id="333e5-124">`ASSERVERMODE` 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="333e5-124">`ASSERVERMODE` is case-sensitive.</span></span>  <span data-ttu-id="333e5-125">所有值必须以大写形式表示。</span><span class="sxs-lookup"><span data-stu-id="333e5-125">All values must be expressed in upper case.</span></span> <span data-ttu-id="333e5-126">下表对 `ASSERVERMODE` 的有效值进行了说明。</span><span class="sxs-lookup"><span data-stu-id="333e5-126">The following table describes the valid values for `ASSERVERMODE`.</span></span>  
  
|<span data-ttu-id="333e5-127">值</span><span class="sxs-lookup"><span data-stu-id="333e5-127">Value</span></span>|<span data-ttu-id="333e5-128">说明</span><span class="sxs-lookup"><span data-stu-id="333e5-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="333e5-129">MULTIDIMENSIONAL</span><span class="sxs-lookup"><span data-stu-id="333e5-129">MULTIDIMENSIONAL</span></span>|<span data-ttu-id="333e5-130">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="333e5-130">This is the default value.</span></span> <span data-ttu-id="333e5-131">如果不设置 `ASSERVERMODE`，则服务器将在多维服务器模式下安装。</span><span class="sxs-lookup"><span data-stu-id="333e5-131">If you do not set `ASSERVERMODE`, the server is installed in Multidimensional server mode.</span></span>|  
|<span data-ttu-id="333e5-132">POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="333e5-132">POWERPIVOT</span></span>|<span data-ttu-id="333e5-133">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="333e5-133">This value is optional.</span></span> <span data-ttu-id="333e5-134">实际上，如果设置 `ROLE` 参数，服务器模式就会自动设置为 1，从而使得 `ASSERVERMODE` 成为 PowerPivot for SharePoint 安装的可选项。</span><span class="sxs-lookup"><span data-stu-id="333e5-134">In practice, if you set the `ROLE` parameter, the server mode is automatically set to 1, making `ASSERVERMODE` optional for a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="333e5-135">有关详细信息，请参阅[从命令提示符安装 PowerPivot](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="333e5-135">For more information, see [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).</span></span>|  
|<span data-ttu-id="333e5-136">TABULAR</span><span class="sxs-lookup"><span data-stu-id="333e5-136">TABULAR</span></span>|<span data-ttu-id="333e5-137">如果是在使用命令行安装程序在表格模式下安装 Analysis Services，则此值是必需的。</span><span class="sxs-lookup"><span data-stu-id="333e5-137">This value is required if you are installing Analysis Services in Tabular mode using command line setup.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="333e5-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="333e5-138">See Also</span></span>  
 <span data-ttu-id="333e5-139">[确定 Analysis Services 实例的服务器模式](../determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="333e5-139">[Determine the Server Mode of an Analysis Services Instance](../determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="333e5-140">[为表格模型数据库配置内存中或 DirectQuery 访问](../../tabular-models/enable-directquery-mode-in-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="333e5-140">[Configure In-Memory or DirectQuery Access for a Tabular Model Database](../../tabular-models/enable-directquery-mode-in-ssms.md) </span></span>  
 [<span data-ttu-id="333e5-141">&#40;SSAS 表格&#41;的表格建模</span><span class="sxs-lookup"><span data-stu-id="333e5-141">Tabular Modeling &#40;SSAS Tabular&#41;</span></span>](../../tabular-models/tabular-models-ssas.md)  
  
  
