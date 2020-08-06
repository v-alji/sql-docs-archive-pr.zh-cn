---
title: 查找报表定义架构版本 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 413a270a3722ddda1f418c748fa5b7fba50dfeea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689772"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a><span data-ttu-id="17474-102">查找报表定义架构版本 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="17474-102">Find the Report Definition Schema Version (SSRS)</span></span>
  <span data-ttu-id="17474-103">报表定义文件为用于验证 rdl 文件的报表定义架构的版本指定 RDL 命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-103">A report definition file specifies the RDL namespace for the version of the report definition schema that is used to validate the rdl file.</span></span> <span data-ttu-id="17474-104">当在报表创作环境（如 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的报表设计器或报表生成器）中打开某个 .rdl 文件时，如果报表是针对先前命名空间创建的，会自动创建一个备份文件，并将该报表升级到当前命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-104">When you open an .rdl file in a report authoring environment such as Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or Report Builder, if the report was created for a previous namespace, a backup file is automatically created, and the report is upgraded to the current namespace.</span></span> <span data-ttu-id="17474-105">如果保存升级后的报告定义，则同时还会保存转换后的 .rdl 文件。</span><span class="sxs-lookup"><span data-stu-id="17474-105">If you save the upgraded report definition, you have saved the converted .rdl file.</span></span> <span data-ttu-id="17474-106">这是升级报表定义的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="17474-106">This is the only way to upgrade a report definition.</span></span> <span data-ttu-id="17474-107">报表定义本身在报表服务器上不升级。</span><span class="sxs-lookup"><span data-stu-id="17474-107">The report definition itself is not upgraded on a report server.</span></span> <span data-ttu-id="17474-108">已编译的报表在报表服务器上升级。</span><span class="sxs-lookup"><span data-stu-id="17474-108">The compiled report is upgraded on a report server.</span></span> <span data-ttu-id="17474-109">有关更多信息，请参见 [Upgrade Reports](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="17474-109">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a><span data-ttu-id="17474-110">如何确定报表的 RDL 架构版本</span><span class="sxs-lookup"><span data-stu-id="17474-110">How to: Identify the RDL Schema Version of a Report</span></span>  
  
1.  <span data-ttu-id="17474-111">在某个能够查看 xml 的应用程序（如记事本或 XML Notepad 2007）中打开报表 .rdl 文件。</span><span class="sxs-lookup"><span data-stu-id="17474-111">Open the report .rdl file in an application such as Notepad or XML Notepad 2007 in which you can view the xml.</span></span>  
  
     <span data-ttu-id="17474-112">XML REPORT 元素指定架构命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-112">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="17474-113">例如，下面的 Report 元素指定报表设计器的命名空间以及报表定义的命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-113">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="17474-114">以下 URL 指定了报表定义命名空间： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`。</span><span class="sxs-lookup"><span data-stu-id="17474-114">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`.</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a><span data-ttu-id="17474-115">如何确定报表设计器的 RDL 架构版本</span><span class="sxs-lookup"><span data-stu-id="17474-115">How to: Identify the RDL Schema Version of Report Designer</span></span>  
  
1.  <span data-ttu-id="17474-116">打开一个新项目。</span><span class="sxs-lookup"><span data-stu-id="17474-116">Open a new project.</span></span> <span data-ttu-id="17474-117">您选择的项目版本决定 RDL 架构的版本。</span><span class="sxs-lookup"><span data-stu-id="17474-117">The version of the project that you choose determines the version of the RDL schema.</span></span> <span data-ttu-id="17474-118">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，支持多个架构版本。</span><span class="sxs-lookup"><span data-stu-id="17474-118">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], more than one schema version is supported.</span></span> <span data-ttu-id="17474-119">有关详细信息，请参阅 [SQL Server Data Tools 中的部署和版本支持 (SSRS)](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)中。</span><span class="sxs-lookup"><span data-stu-id="17474-119">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="17474-120">在 **“项目”** 菜单上，单击 **“添加新项”**。</span><span class="sxs-lookup"><span data-stu-id="17474-120">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="17474-121">此时将打开“添加新项”对话框。</span><span class="sxs-lookup"><span data-stu-id="17474-121">The **Add New Item** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="17474-122">在 **“模板”** 窗格中，单击 **“报表”**。</span><span class="sxs-lookup"><span data-stu-id="17474-122">In the **Templates** pane, click **Report**.</span></span>  
  
4.  <span data-ttu-id="17474-123">在 **“名称”** 中，键入报表名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="17474-123">In **Name**, type a report name or accept the default.</span></span>  
  
5.  <span data-ttu-id="17474-124">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="17474-124">Click **Add**.</span></span> <span data-ttu-id="17474-125">报表设计器将在“设计”视图中打开一个新的空白报表。</span><span class="sxs-lookup"><span data-stu-id="17474-125">Report Designer opens a new blank report in Design view.</span></span>  
  
6.  <span data-ttu-id="17474-126">在 **“视图”** 菜单上，单击 **“代码”**。</span><span class="sxs-lookup"><span data-stu-id="17474-126">On the **View** menu, click **Code**.</span></span> <span data-ttu-id="17474-127">该报告定义将显示为一个 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="17474-127">The report definition is displayed as an XML file.</span></span>  
  
     <span data-ttu-id="17474-128">XML REPORT 元素指定架构命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-128">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="17474-129">例如，下面的 Report 元素指定报表设计器的命名空间以及报表定义的命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-129">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="17474-130">以下 URL 指定了报表定义命名空间： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="17474-130">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a><span data-ttu-id="17474-131">如何确定报表服务器上的 RDL 架构版本</span><span class="sxs-lookup"><span data-stu-id="17474-131">How to: Identify the RDL Schema Version on the Report Server</span></span>  
  
-   <span data-ttu-id="17474-132">在报表管理器中，键入报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="17474-132">In Report Manager, type the URL for the report server.</span></span> <span data-ttu-id="17474-133">例如，以下 URL 指定一个本地计算机上的报表服务器：</span><span class="sxs-lookup"><span data-stu-id="17474-133">For example, the following URL specifies a report server on the local computer:</span></span>  
  
     `http://localhost/reportserver/reportdefinition.xsd`  
  
     <span data-ttu-id="17474-134">将在浏览器中打开 .xsd 文件。</span><span class="sxs-lookup"><span data-stu-id="17474-134">The .xsd file opens in the browser.</span></span>  
  
     <span data-ttu-id="17474-135">XML schema 元素指定架构命名空间。</span><span class="sxs-lookup"><span data-stu-id="17474-135">The XML schema element specifies the schema namespace.</span></span> <span data-ttu-id="17474-136">例如，下面的架构元素指定三个命名空间：由 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]内部使用的 targetNamespace 引用、架构自身 (xsd) 的 xsd 引用以及报表定义引用。</span><span class="sxs-lookup"><span data-stu-id="17474-136">For example, the following schema element specifies three namespaces: the targetNamespace reference that is used internally by [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the xsd reference for the schema itself (xsd), and the report definition reference.</span></span>  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     <span data-ttu-id="17474-137">以下 URL 指定了报表定义命名空间： `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="17474-137">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17474-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17474-138">See Also</span></span>  
 <span data-ttu-id="17474-139">[升级报表](../install-windows/upgrade-reports.md) </span><span class="sxs-lookup"><span data-stu-id="17474-139">[Upgrade Reports](../install-windows/upgrade-reports.md) </span></span>  
 [<span data-ttu-id="17474-140">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="17474-140">Report Definition Language &#40;SSRS&#41;</span></span>](report-definition-language-ssrs.md)  
  
  
