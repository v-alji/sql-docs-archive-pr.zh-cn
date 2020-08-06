---
title: 在 Excel 或 Reporting Services 中使用 BI 语义模型连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 486195ca-530f-49e8-b40d-0f817db159ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: a48ebfc515b97327655e34409bf80ce0c749e04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691923"
---
# <a name="use-a-bi-semantic-model-connection-in-excel-or-reporting-services"></a><span data-ttu-id="93b48-102">在 Excel 或 Reporting Services 中使用 BI 语义模型连接</span><span class="sxs-lookup"><span data-stu-id="93b48-102">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>
  <span data-ttu-id="93b48-103">本主题说明如何使用 BI 语义模型连接，这些连接是使用其他主题中的说明创建的。</span><span class="sxs-lookup"><span data-stu-id="93b48-103">This topic explains how to use the BI semantic model connections you created using instructions in other topics.</span></span> <span data-ttu-id="93b48-104">如果尚未创建 BI 语义模型，请参阅[创建与 PowerPivot 工作簿的 Bi 语义模型连接](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)和[创建与表格模型数据库的 Bi 语义模型连接](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)。</span><span class="sxs-lookup"><span data-stu-id="93b48-104">If you have not yet created a BI semantic model, see [Create a BI Semantic Model Connection to a PowerPivot Workbook](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md) and [Create a BI Semantic Model Connection to a Tabular Model Database](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
##  <a name="connect-from-excel"></a><a name="bkmk_connect"></a> <span data-ttu-id="93b48-105">从 Excel 进行连接</span><span class="sxs-lookup"><span data-stu-id="93b48-105">Connect from Excel</span></span>  
 <span data-ttu-id="93b48-106">您可以将 BI 语义模型连接指定为 Excel 中的数据源或使用 Analysis Services 表格模型数据的任何其他业务应用程序。</span><span class="sxs-lookup"><span data-stu-id="93b48-106">You can specify a BI semantic model connection as a data source in Excel or any other business application that uses Analysis Services tabular model data.</span></span> <span data-ttu-id="93b48-107">本节介绍使用 Excel 连接到 BI 语义模型数据的两种方法。</span><span class="sxs-lookup"><span data-stu-id="93b48-107">This section explains the two approaches for connecting to BI semantic model data using Excel.</span></span>  
  
 <span data-ttu-id="93b48-108">Excel 的 BI 语义模型连接要求在工作站上安装 Excel 2010 和 MSOLAP.5 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="93b48-108">BI semantic model connections from Excel require that you have Excel 2010 and the MSOLAP.5 OLE DB provider installed on your workstation.</span></span> <span data-ttu-id="93b48-109">将在本节中进一步提供有关连接要求的其他信息。</span><span class="sxs-lookup"><span data-stu-id="93b48-109">Additional information about connection requirements is provided further on in this section.</span></span>  
  
 <span data-ttu-id="93b48-110">**从 SharePoint 启动**</span><span class="sxs-lookup"><span data-stu-id="93b48-110">**Starting from SharePoint**</span></span>  
  
-   <span data-ttu-id="93b48-111">右键单击库中的某一 BI 语义模型连接，然后选择“启动 Excel”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="93b48-111">Right-click a BI semantic model connection in a library and select **Launch Excel**.</span></span>  
  
 <span data-ttu-id="93b48-112">![BISM 快速启动命令的屏幕快照](../media/ssas-bism-quicklaunch.gif "BISM 快速启动命令的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="93b48-112">![Screenshot of BISM quick launch command](../media/ssas-bism-quicklaunch.gif "Screenshot of BISM quick launch command")</span></span>  
  
 <span data-ttu-id="93b48-113">系统提示您启用数据连接时单击 **“启用”** 。</span><span class="sxs-lookup"><span data-stu-id="93b48-113">Click **Enable** when prompted to enable data connections.</span></span> <span data-ttu-id="93b48-114">Excel 打开一个工作簿，该工作簿包含使用基础数据源中的字段填充的数据透视表字段列表。</span><span class="sxs-lookup"><span data-stu-id="93b48-114">Excel opens a workbook that contains a PivotTable field list populated with fields from the underlying data source.</span></span>  
  
 <span data-ttu-id="93b48-115">**从 Excel 启动**</span><span class="sxs-lookup"><span data-stu-id="93b48-115">**Starting from Excel**</span></span>  
  
1.  <span data-ttu-id="93b48-116">启动 Excel 并打开工作簿。</span><span class="sxs-lookup"><span data-stu-id="93b48-116">Start Excel and open a workbook.</span></span> <span data-ttu-id="93b48-117">在“数据”选项卡上的“获取外部数据”中，单击 **“从其他源”**。</span><span class="sxs-lookup"><span data-stu-id="93b48-117">On the Data tab, in Get External Data, click **From Other Sources**.</span></span>  
  
2.  <span data-ttu-id="93b48-118">单击 **“从 Analysis Services”** 并且使用数据连接向导导入数据。</span><span class="sxs-lookup"><span data-stu-id="93b48-118">Click **From Analysis Services** and use the Data Connection Wizard to import the data.</span></span>  
  
3.  <span data-ttu-id="93b48-119">输入 BI 语义模型连接文件的 SharePoint URL， (例如\*\* http://mysharepoint/shared Documents/myData\*\*) 。</span><span class="sxs-lookup"><span data-stu-id="93b48-119">Enter the SharePoint URL of the BI semantic model connection file (for example, **http://mysharepoint/shared documents/myData.bism**).</span></span> <span data-ttu-id="93b48-120">接受默认登录凭据选项 **“使用 Windows 身份验证”**。</span><span class="sxs-lookup"><span data-stu-id="93b48-120">Accept the default log on credentials option, **Use Windows Authentication**.</span></span> <span data-ttu-id="93b48-121">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="93b48-121">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="93b48-122">在下一页上，再次单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="93b48-122">On the next page, click **Next** again.</span></span> <span data-ttu-id="93b48-123">尽管系统会提示您选择某个数据库，但您只能使用在 BI 语义模型连接中指定的一个数据库。</span><span class="sxs-lookup"><span data-stu-id="93b48-123">Although you are prompted to select a database, you can only use the one database that is specified in the BI semantic model connection.</span></span>  
  
5.  <span data-ttu-id="93b48-124">在最后一页上，您可以提供友好名称和说明。</span><span class="sxs-lookup"><span data-stu-id="93b48-124">On the last page, you can provide a friendly name and description.</span></span> <span data-ttu-id="93b48-125">单击 **“完成”**，然后在“导入数据”对话框上单击 **“确定”** 以便导入数据。</span><span class="sxs-lookup"><span data-stu-id="93b48-125">Click **Finish**, and then click **OK** on the Import Data dialog box to import the data.</span></span>  
  
 <span data-ttu-id="93b48-126">为使连接成功，您必须在客户端计算机上安装了 Excel 2010 和 MSOLAP.5.dll。</span><span class="sxs-lookup"><span data-stu-id="93b48-126">For connections to succeed you must have Excel 2010 and the MSOLAP.5.dll installed on the client computer.</span></span> <span data-ttu-id="93b48-127">你可以通过安装此版本的当前版本的 PowerPivot for Excel 的版本获取提供程序，也可以从[功能包下载页](https://go.microsoft.com/fwlink/?linkid=214066)仅下载 Analysis Services OLE DB 提供程序。</span><span class="sxs-lookup"><span data-stu-id="93b48-127">You can get the provider by installing the version of PowerPivot for Excel that is current for this release or you can download just the Analysis Services OLE DB provider from the [Feature Pack download page](https://go.microsoft.com/fwlink/?linkid=214066).</span></span>  
  
 <span data-ttu-id="93b48-128">若要确认 MSOLAP.5.dll 是当前版本，请检查注册表中的 `HKEY_CLASSES_ROOT\MSOLAP`。</span><span class="sxs-lookup"><span data-stu-id="93b48-128">To confirm that MSOLAP.5.dll is the current version, check `HKEY_CLASSES_ROOT\MSOLAP` in the registry.</span></span> <span data-ttu-id="93b48-129">`CurVer` 应设置为 MSOLAP.5。</span><span class="sxs-lookup"><span data-stu-id="93b48-129">`CurVer` should be set to MSOLAP.5.</span></span>  
  
 <span data-ttu-id="93b48-130">您还必须对 SharePoint 中的 BI 语义模型文件具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="93b48-130">You must also have Read permissions on the BI semantic model file in SharePoint.</span></span> <span data-ttu-id="93b48-131">读取权限包括下载权限。</span><span class="sxs-lookup"><span data-stu-id="93b48-131">Read permissions include download rights.</span></span> <span data-ttu-id="93b48-132">Excel 从 SharePoint 下载 BI 语义模型连接信息并且通过 `HTTP Get` 打开与数据库的直接连接。</span><span class="sxs-lookup"><span data-stu-id="93b48-132">Excel downloads the BI semantic model connection information from SharePoint and opens a direct connection to the database via `HTTP Get`.</span></span> <span data-ttu-id="93b48-133">一旦在本地存储 BI 语义模型连接信息后，连接请求就不流过 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="93b48-133">Connection requests do not flow through SharePoint once BI semantic model connection information is stored locally.</span></span>  
  
 <span data-ttu-id="93b48-134">如果您正在连接到在 Analysis Services 服务器上运行的表格模型数据库，则 SharePoint 权限是不够的。</span><span class="sxs-lookup"><span data-stu-id="93b48-134">If you are connecting to a tabular model database that runs on an Analysis Services server, SharePoint permissions are not sufficient.</span></span> <span data-ttu-id="93b48-135">您还必须对该服务器具有数据库读取权限。</span><span class="sxs-lookup"><span data-stu-id="93b48-135">You must also have database read permissions on the server.</span></span> <span data-ttu-id="93b48-136">在创建 BI 语义模型连接时，应已执行了此步骤。</span><span class="sxs-lookup"><span data-stu-id="93b48-136">This step should have been performed when you created the BI semantic model connection.</span></span> <span data-ttu-id="93b48-137">有关详细信息，请参阅 [创建与表格模型数据库的 BI 语义模型连接](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)。</span><span class="sxs-lookup"><span data-stu-id="93b48-137">For more information, see [Create a BI Semantic Model Connection to a Tabular Model Database](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).</span></span>  
  
##  <a name="connect-from-reporting-services-in-sharepoint"></a><a name="bkmk_use"></a><span data-ttu-id="93b48-138">从 SharePoint 中的 Reporting Services 连接</span><span class="sxs-lookup"><span data-stu-id="93b48-138">Connect from Reporting Services in SharePoint</span></span>  
 <span data-ttu-id="93b48-139">您可以通过将文件指定为使用数据的文档或工具中的数据源，采用与使用大多数数据源相同的方式使用 BI 语义模型连接。</span><span class="sxs-lookup"><span data-stu-id="93b48-139">You can use a BI semantic model connection the same way you use most data sources, by specifying the file as a data source in the document or tool that uses the data.</span></span> <span data-ttu-id="93b48-140">尽管 BI 语义模型连接指向其他服务器上的物理数据库，但您使用该连接文件就像它已是数据源一样。</span><span class="sxs-lookup"><span data-stu-id="93b48-140">Although a BI semantic model connection points to a physical database on another server, you use the connection file as if it were the data source.</span></span> <span data-ttu-id="93b48-141">BI 语义模型连接的 SharePoint URL 是使用 BI 语义模型数据的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表的有效数据源位置。</span><span class="sxs-lookup"><span data-stu-id="93b48-141">The SharePoint URL of the BI semantic model connection is a valid data source location for [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports that use BI semantic model data.</span></span>  
  
 <span data-ttu-id="93b48-142">对于 SharePoint 中的即席报表设计，创建该报表的用户必须对 BI 语义模型连接 (.bism) 文件以及商业智能语义模型数据库具有 SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="93b48-142">For ad hoc report design in SharePoint, the user who creates the report must have SharePoint permissions on the BI semantic model connection (.bism) file and on the business intelligence semantic model database.</span></span> <span data-ttu-id="93b48-143">该连接的安全上下文是创建该报表的交互式用户。</span><span class="sxs-lookup"><span data-stu-id="93b48-143">The security context of the connection is the interactive user who is creating the report.</span></span>  
  
  
