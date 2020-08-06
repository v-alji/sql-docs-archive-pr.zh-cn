---
title: SQL Server Compact Edition 目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfeb0bfce54c9ebefb5c526656be6b736dc0d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589810"
---
# <a name="sql-server-compact-edition-destination"></a><span data-ttu-id="85e6b-102">SQL Server Compact Edition 目标</span><span class="sxs-lookup"><span data-stu-id="85e6b-102">SQL Server Compact Edition Destination</span></span>
  <span data-ttu-id="85e6b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标可将数据写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库。</span><span class="sxs-lookup"><span data-stu-id="85e6b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination writes data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85e6b-104">在 64 位计算机上，必须以 32 位模式运行连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据源的包。</span><span class="sxs-lookup"><span data-stu-id="85e6b-104">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="85e6b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 数据源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider 只在 32 位版本中提供。</span><span class="sxs-lookup"><span data-stu-id="85e6b-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
 <span data-ttu-id="85e6b-106">可以通过指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标要向其中插入数据的表的名称来配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标。</span><span class="sxs-lookup"><span data-stu-id="85e6b-106">You configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination by specifying the name of the table into which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination inserts the data.</span></span> <span data-ttu-id="85e6b-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标的自定义属性 TableName 包含此表名称。</span><span class="sxs-lookup"><span data-stu-id="85e6b-107">The custom property TableName of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination contains the table name.</span></span>  
  
 <span data-ttu-id="85e6b-108">此目标使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器连接到数据源，而此连接管理器指定要使用的 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="85e6b-108">This destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="85e6b-109">有关详细信息，请参阅 [SQL Server Compact Edition 连接管理器](../connection-manager/sql-server-compact-edition-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="85e6b-109">For more information, see [SQL Server Compact Edition Connection Manager](../connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
 <span data-ttu-id="85e6b-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标包括 TableName 自定义属性，该属性可以在加载包时通过属性表达式进行更新。</span><span class="sxs-lookup"><span data-stu-id="85e6b-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination includes the TableName custom property, which can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="85e6b-111">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../expressions/use-property-expressions-in-packages.md)和 [SQL Server Compact Edition 目标自定义属性](sql-server-compact-edition-destination-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="85e6b-111">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [SQL Server Compact Edition Destination Custom Properties](sql-server-compact-edition-destination-custom-properties.md).</span></span>  
  
 <span data-ttu-id="85e6b-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标具有一个输入，并且不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="85e6b-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination has one input and does not support an error output.</span></span>  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a><span data-ttu-id="85e6b-113">SQL Server Compact Edition 目标的配置</span><span class="sxs-lookup"><span data-stu-id="85e6b-113">Configuration of the SQL Server Compact Edition Destination</span></span>  
 <span data-ttu-id="85e6b-114">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="85e6b-114">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="85e6b-115">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="85e6b-115">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="85e6b-116">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="85e6b-116">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="85e6b-117">Common Properties</span><span class="sxs-lookup"><span data-stu-id="85e6b-117">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="85e6b-118">SQL Server 目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="85e6b-118">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="85e6b-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="85e6b-119">Related Tasks</span></span>  
 <span data-ttu-id="85e6b-120">有关如何设置数据流组件的属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="85e6b-120">For more information about how to set properties of this component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e6b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85e6b-121">See Also</span></span>  
 [<span data-ttu-id="85e6b-122">数据流</span><span class="sxs-lookup"><span data-stu-id="85e6b-122">Data Flow</span></span>](data-flow.md)  
  
  
