---
title: Excel 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7561361c6d4ab7e22282b25367906aa4b75e5bc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585938"
---
# <a name="excel-connection-manager"></a><span data-ttu-id="3d6b2-102">Excel 连接管理器</span><span class="sxs-lookup"><span data-stu-id="3d6b2-102">Excel Connection Manager</span></span>
  <span data-ttu-id="3d6b2-103">Excel 连接管理器使包可以连接到现有的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 工作簿文件。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-103">An Excel connection manager enables a package to connect to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbook file.</span></span> <span data-ttu-id="3d6b2-104">包含的 excel 源和 excel 目标 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用 excel 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-104">The Excel source and the Excel destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include use the Excel connection manager.</span></span>  
  
 <span data-ttu-id="3d6b2-105">将 Excel 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定 Excel 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-105">When you add an Excel connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an Excel connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="3d6b2-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `EXCEL`。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-106">The `ConnectionManagerType` property of the connection manager is set to `EXCEL`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d6b2-107">无法连接到受密码保护的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-107">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="configuration-of-the-excel-connection-manager"></a><span data-ttu-id="3d6b2-108">Excel 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="3d6b2-108">Configuration of the Excel Connection Manager</span></span>  
 <span data-ttu-id="3d6b2-109">可以按照下列方式配置 Excel 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="3d6b2-109">You can configure the Excel connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="3d6b2-110">指定 Excel 工作簿文件的路径。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-110">Specify the path of the Excel workbook file.</span></span>  
  
-   <span data-ttu-id="3d6b2-111">指定用于创建文件的 Excel 的版本。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-111">Specify the version of Excel that was used to create the file.</span></span>  
  
-   <span data-ttu-id="3d6b2-112">指示所选工作表或范围中的第一行被访问数据是否包含列名称。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-112">Indicate whether the first row of accessed data in the selected worksheets or ranges contains column names.</span></span>  
  
 <span data-ttu-id="3d6b2-113">如果 Excel 源使用 Excel 连接管理器，则被提取的数据将附带列名称。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-113">If the Excel connection manager is used by an Excel source, the column names are included with the extracted data.</span></span> <span data-ttu-id="3d6b2-114">如果 Excel 目标使用它，则列名称包括在被写入的数据中。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-114">If it is used by an Excel destination, the column names are included in the written data.</span></span>  
  
 <span data-ttu-id="3d6b2-115">Excel 连接管理器使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet 4.0 的 OLE DB 提供程序及其支持的 EXCEL ISAM (索引顺序访问方法) 驱动程序来连接 excel 数据源并对其进行读取和写入。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-115">The Excel connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span> <span data-ttu-id="3d6b2-116">有关与 Excel 源和 Excel 目标结合使用时，此提供程序和驱动程序的行为的详细信息，请参阅[Excel 源](../data-flow/excel-source.md)和[excel 目标](../data-flow/excel-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-116">For more information about the behavior of this provider and driver when used with Excel sources and Excel destinations, see [Excel Source](../data-flow/excel-source.md) and [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
 <span data-ttu-id="3d6b2-117">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3d6b2-118">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [Excel 连接管理器编辑器](../excel-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Excel Connection Manager Editor](../excel-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="3d6b2-119">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
 <span data-ttu-id="3d6b2-120">有关循环遍历 Excel 文件中的某个组的信息，请参阅 [使用 Foreach 循环容器，循环遍历 Excel 文件和表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="3d6b2-120">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3d6b2-121">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3d6b2-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3d6b2-122">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="3d6b2-122">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="3d6b2-123">使用 SQL Server Integration Services (SSIS) 将数据导入 Excel 或从 Excel 导出数据</span><span class="sxs-lookup"><span data-stu-id="3d6b2-123">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)
  
  
