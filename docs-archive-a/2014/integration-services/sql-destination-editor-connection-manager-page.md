---
title: SQL 目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f3a552968cb297de337e1f0c406b444d95dc5a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580788"
---
# <a name="sql-destination-editor-connection-manager-page"></a><span data-ttu-id="31470-102">SQL 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="31470-102">SQL Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="31470-103">可以使用 **“SQL 目标编辑器”** 对话框的 **“连接管理器”** 页，指定数据源信息以及预览结果。</span><span class="sxs-lookup"><span data-stu-id="31470-103">Use the **Connection Manager** page of the **SQL Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="31470-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]目标将数据加载到数据库中的表或视图中 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="31470-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destination loads data into tables or views in a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="31470-105">若要了解有关 SQL Server 目标的详细信息，请参阅 [SQL Server Destination](data-flow/sql-server-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="31470-105">To learn more about the SQL Server destination, see [SQL Server Destination](data-flow/sql-server-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="31470-106">选项</span><span class="sxs-lookup"><span data-stu-id="31470-106">Options</span></span>  
 <span data-ttu-id="31470-107">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="31470-107">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="31470-108">从列表中选择现有连接，或通过单击“新建”\*\*\*\* 创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="31470-108">Select an existing connection from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="31470-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="31470-109">**New**</span></span>  
 <span data-ttu-id="31470-110">通过使用“配置 OLE DB 连接管理器”  对话框创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="31470-110">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="31470-111">**使用表或视图**</span><span class="sxs-lookup"><span data-stu-id="31470-111">**Use a table or view**</span></span>  
 <span data-ttu-id="31470-112">从列表中选择现有的表或视图，或单击“新建”\*\*\*\* 创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="31470-112">Select an existing table or view from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="31470-113">**新建**</span><span class="sxs-lookup"><span data-stu-id="31470-113">**New**</span></span>  
 <span data-ttu-id="31470-114">通过使用“创建表”  对话框创建一个新表。</span><span class="sxs-lookup"><span data-stu-id="31470-114">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31470-115">单击 **“新建”** 时， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="31470-115">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="31470-116">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="31470-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="31470-117">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="31470-117">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="31470-118">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="31470-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="31470-119">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="31470-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="31470-120">**预览**</span><span class="sxs-lookup"><span data-stu-id="31470-120">**Preview**</span></span>  
 <span data-ttu-id="31470-121">使用“预览查询结果”  对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="31470-121">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="31470-122">预览最多可以显示 200 行。</span><span class="sxs-lookup"><span data-stu-id="31470-122">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31470-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31470-123">See Also</span></span>  
 <span data-ttu-id="31470-124">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="31470-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="31470-125">[SQL 目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="31470-125">[SQL Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="31470-126">[SQL 目标编辑器 &#40;高级页面&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="31470-126">[SQL Destination Editor &#40;Advanced Page&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="31470-127">使用 SQL Server 目标大容量加载数据</span><span class="sxs-lookup"><span data-stu-id="31470-127">Bulk Load Data by Using the SQL Server Destination</span></span>](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
