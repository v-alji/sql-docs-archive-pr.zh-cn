---
title: DataReader 目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40cfe5d99c33eb19d415f204173005a64bde7855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694069"
---
# <a name="datareader-destination"></a><span data-ttu-id="a98e2-102">DataReader 目标</span><span class="sxs-lookup"><span data-stu-id="a98e2-102">DataReader Destination</span></span>
  <span data-ttu-id="a98e2-103">DataReader 目标使用 ADO.NET `DataReader` 接口显示数据流中的数据。</span><span class="sxs-lookup"><span data-stu-id="a98e2-103">The DataReader destination exposes the data in a data flow by using the ADO.NET `DataReader` interface.</span></span> <span data-ttu-id="a98e2-104">此数据然后可由其他应用程序占用。</span><span class="sxs-lookup"><span data-stu-id="a98e2-104">The data can then be consumed by other applications.</span></span> <span data-ttu-id="a98e2-105">例如，可以将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表的数据源配置为使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的运行结果。</span><span class="sxs-lookup"><span data-stu-id="a98e2-105">For example, you can configure the data source of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report to use the result of running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="a98e2-106">若要执行此操作，请创建实现 DataReader 目标的数据流。</span><span class="sxs-lookup"><span data-stu-id="a98e2-106">To do this, you create a data flow that implements the DataReader destination.</span></span>  
  
 <span data-ttu-id="a98e2-107">有关以编程方式访问和读取 DataReader 目标中的值的信息，请参阅 [加载本地包的输出](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)。</span><span class="sxs-lookup"><span data-stu-id="a98e2-107">For information about accessing and reading values in the DataReader destination programmatically, see [Loading the Output of a Local Package](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).</span></span>  
  
## <a name="configuration-of-the-datareader-destination"></a><span data-ttu-id="a98e2-108">DataReader 目标的配置</span><span class="sxs-lookup"><span data-stu-id="a98e2-108">Configuration of the DataReader Destination</span></span>  
 <span data-ttu-id="a98e2-109">可以指定 DataReader 目标的超时值，并指示如果发生超时目标是否失败。</span><span class="sxs-lookup"><span data-stu-id="a98e2-109">You can specify a time-out value for the DataReader destination and indicate whether the destination should fail if a time-out occurs.</span></span> <span data-ttu-id="a98e2-110">如果应用程序在指定时间内不请求数据，则出现超时。</span><span class="sxs-lookup"><span data-stu-id="a98e2-110">A time-out occurs if the application does not ask for data within the specified time.</span></span>  
  
 <span data-ttu-id="a98e2-111">DataReader 目标具有一个输入。</span><span class="sxs-lookup"><span data-stu-id="a98e2-111">The DataReader destination has one input.</span></span> <span data-ttu-id="a98e2-112">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="a98e2-112">It does not support an error output.</span></span>  
  
 <span data-ttu-id="a98e2-113">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="a98e2-113">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a98e2-114">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="a98e2-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a98e2-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a98e2-115">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="a98e2-116">DataReader 目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="a98e2-116">DataReader Destination Custom Properties</span></span>](datareader-destination-custom-properties.md)  
  
 <span data-ttu-id="a98e2-117">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a98e2-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
