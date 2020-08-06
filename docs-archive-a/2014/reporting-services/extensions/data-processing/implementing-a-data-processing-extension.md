---
title: 实现数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5a1b7668f2319e742dcf3f1969fc3c5cc85cd7eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693633"
---
# <a name="implementing-a-data-processing-extension"></a><span data-ttu-id="e3aed-102">实现数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="e3aed-102">Implementing a Data Processing Extension</span></span>
  <span data-ttu-id="e3aed-103">借助于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的数据处理扩展插件，您可以连接到数据源并检索数据。</span><span class="sxs-lookup"><span data-stu-id="e3aed-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="e3aed-104">它们还可以充当数据源和数据集之间的桥梁。</span><span class="sxs-lookup"><span data-stu-id="e3aed-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e3aed-105">数据处理扩展插件是模仿 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 数据提供程序接口的子集创建的。</span><span class="sxs-lookup"><span data-stu-id="e3aed-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3aed-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="e3aed-106">In This Section</span></span>  
 [<span data-ttu-id="e3aed-107">数据处理扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="e3aed-107">Data Processing Extensions Overview</span></span>](data-processing-extensions-overview.md)  
 <span data-ttu-id="e3aed-108">介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 编写自定义数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e3aed-108">Introduces how to write a custom data processing extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e3aed-109">准备实现数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="e3aed-109">Preparing to Implement a Data Processing Extension</span></span>](preparing-to-implement-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-110">介绍在实现 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件时可用的接口以及何时要求实现特定接口。</span><span class="sxs-lookup"><span data-stu-id="e3aed-110">Describes the interfaces available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, as well as when you are required to implement a particular interface.</span></span>  
  
 [<span data-ttu-id="e3aed-111">创建数据处理扩展插件库</span><span class="sxs-lookup"><span data-stu-id="e3aed-111">Creating a Data Processing Extension Library</span></span>](creating-a-data-processing-extension-library.md)  
 <span data-ttu-id="e3aed-112">介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件分配命名空间以及如何将数据处理扩展插件编译成库 DLL。</span><span class="sxs-lookup"><span data-stu-id="e3aed-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension and compiling your data processing extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="e3aed-113">为数据处理扩展插件实现 Connection 类</span><span class="sxs-lookup"><span data-stu-id="e3aed-113">Implementing a Connection Class for a Data Processing Extension</span></span>](implementing-a-connection-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-114">介绍连接的属性以及如何为数据处理扩展插件实现你自己的 Connection 类  。</span><span class="sxs-lookup"><span data-stu-id="e3aed-114">Describes the attributes of a connection and how to implement your own **Connection** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="e3aed-115">为数据处理扩展插件实现 Command 类</span><span class="sxs-lookup"><span data-stu-id="e3aed-115">Implementing a Command Class for a Data Processing Extension</span></span>](implementing-a-command-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-116">介绍命令的属性以及如何为数据处理扩展插件实现你自己的 Command 类  。</span><span class="sxs-lookup"><span data-stu-id="e3aed-116">Describes the attributes of a command, and how to implement your own **Command** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="e3aed-117">为数据处理扩展插件实现 DataReader 类</span><span class="sxs-lookup"><span data-stu-id="e3aed-117">Implementing a DataReader Class for a Data Processing Extension</span></span>](implementing-a-datareader-class-for-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-118">介绍数据读取器的属性以及如何为数据处理扩展插件实现自己的 DataReader 类  。</span><span class="sxs-lookup"><span data-stu-id="e3aed-118">Describes the attributes of a data reader and how to implement your own **DataReader** class for your data processing extension.</span></span>  
  
 [<span data-ttu-id="e3aed-119">将外部数据集用于 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e3aed-119">Using an External Dataset with Reporting Services</span></span>](using-an-external-dataset-with-reporting-services.md)  
 <span data-ttu-id="e3aed-120">介绍如何向报表服务器公开自定义 DataSet 对象以供使用  。</span><span class="sxs-lookup"><span data-stu-id="e3aed-120">Describes how to expose your custom **DataSet** objects to the report server for consumption.</span></span>  
  
 [<span data-ttu-id="e3aed-121">部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="e3aed-121">Deploying a Data Processing Extension</span></span>](deploying-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-122">介绍如何部署数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e3aed-122">Describes how to deploy your data processing extension.</span></span>  
  
 [<span data-ttu-id="e3aed-123">调试数据处理扩展插件代码</span><span class="sxs-lookup"><span data-stu-id="e3aed-123">Debugging Data Processing Extension Code</span></span>](debugging-data-processing-extension-code.md)  
 <span data-ttu-id="e3aed-124">介绍如何调试数据处理扩展插件中的代码。</span><span class="sxs-lookup"><span data-stu-id="e3aed-124">Describes how to debug code in your data processing extensions.</span></span>  
  
 [<span data-ttu-id="e3aed-125">删除数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="e3aed-125">Removing a Data Processing Extension</span></span>](removing-a-data-processing-extension.md)  
 <span data-ttu-id="e3aed-126">介绍如何从报表服务器或报表设计器中删除数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e3aed-126">Describes how to remove a data processing extension from a report server or Report Designer.</span></span>  
  
 <span data-ttu-id="e3aed-127">有关完全实现的数据处理扩展插件的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="e3aed-127">For a sample of a fully implemented data processing extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3aed-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3aed-128">See Also</span></span>  
 <span data-ttu-id="e3aed-129">[Reporting Services 扩展](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="e3aed-129">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="e3aed-130">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="e3aed-130">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
