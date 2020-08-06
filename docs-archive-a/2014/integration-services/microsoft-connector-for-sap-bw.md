---
title: 用于 SAP BW 的 Microsoft Connector 1.1 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ec5cfe83b201976be0512c54b77bc79f8aa824b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691793"
---
# <a name="microsoft-connector-11-for-sap-bw"></a><span data-ttu-id="b851f-102">Microsoft Connector 1.1 for SAP BW</span><span class="sxs-lookup"><span data-stu-id="b851f-102">Microsoft Connector 1.1 for SAP BW</span></span>
  <span data-ttu-id="b851f-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]连接器 1.1 for SAP BW 包含一组三个组件，可让你从 SAP Netweaver BW 版本7系统中提取数据或将数据加载到 SAP BW 版本7系统。</span><span class="sxs-lookup"><span data-stu-id="b851f-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW consists of a set of three components that let you extract data from, or load data into, an SAP Netweaver BW version 7 system.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b851f-104">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="b851f-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="b851f-105">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="b851f-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b851f-106">从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。</span><span class="sxs-lookup"><span data-stu-id="b851f-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="b851f-107">请向 SAP 核实以便确认这些要求。</span><span class="sxs-lookup"><span data-stu-id="b851f-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="components"></a><span data-ttu-id="b851f-108">组件</span><span class="sxs-lookup"><span data-stu-id="b851f-108">Components</span></span>  
 <span data-ttu-id="b851f-109">[!INCLUDE[msCoName](../includes/msconame-md.md)]SAP BW 的连接器1.1 具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="b851f-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following components:</span></span>  
  
-   <span data-ttu-id="b851f-110">**SAP BW 源** - SAP BW 源是一个数据流源组件，用于从 SAP Netweaver BW 版本 7 系统中提取数据。</span><span class="sxs-lookup"><span data-stu-id="b851f-110">**SAP BW Source**-The SAP BW source is a data flow source component that lets you extract data from an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="b851f-111">**SAP BW 目标** - SAP BW 目标是一个数据流目标组件，用于将数据加载到 SAP Netweaver BW 版本 7 系统中。</span><span class="sxs-lookup"><span data-stu-id="b851f-111">**SAP BW Destination**-The SAP BW destination is a data flow destination component that lets you load data into an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="b851f-112">**SAP BW 连接管理器** - SAP BW 连接管理器将 SAP BW 源或 SAP BW 目标连接到 SAP Netweaver BW 版本 7 系统。</span><span class="sxs-lookup"><span data-stu-id="b851f-112">**SAP BW Connection Manager**-The SAP BW connection manager connects either an SAP BW source or SAP BW destination to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="b851f-113">有关演示如何配置和使用 SAP BW 连接管理器、源和目标的演练，请参阅白皮书 [将 SQL Server Integration Services 与 SAP BI 7.0 一起使用](https://go.microsoft.com/fwlink/?LinkId=301897)。</span><span class="sxs-lookup"><span data-stu-id="b851f-113">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897).</span></span> <span data-ttu-id="b851f-114">此白皮书还说明如何在 SAP BW 中配置所需的对象。</span><span class="sxs-lookup"><span data-stu-id="b851f-114">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
## <a name="documentation"></a><span data-ttu-id="b851f-115">文档</span><span class="sxs-lookup"><span data-stu-id="b851f-115">Documentation</span></span>  
 <span data-ttu-id="b851f-116">适用于 SAP BW 连接器1.1 的此帮助文件 [!INCLUDE[msCoName](../includes/msconame-md.md)] 包含以下主题和部分：</span><span class="sxs-lookup"><span data-stu-id="b851f-116">This Help file for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW contains the following topics and sections:</span></span>  
  
 [<span data-ttu-id="b851f-117">安装 Microsoft Connector for 1.1 SAP BW</span><span class="sxs-lookup"><span data-stu-id="b851f-117">Installing the Microsoft Connector for 1.1 SAP BW</span></span>](installing-the-microsoft-connector-for-sap-bw.md)  
 <span data-ttu-id="b851f-118">介绍 [!INCLUDE[msCoName](../includes/msconame-md.md)] SAP BW 连接器1.1 的安装要求。</span><span class="sxs-lookup"><span data-stu-id="b851f-118">Describes the installation requirements for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="b851f-119">Microsoft Connector 1.1 for SAP BW 组件</span><span class="sxs-lookup"><span data-stu-id="b851f-119">Microsoft Connector 1.1 for SAP BW Components</span></span>](microsoft-connector-for-sap-bw-components.md)  
 <span data-ttu-id="b851f-120">介绍 SAP BW 的连接器1.1 的每个组件 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b851f-120">Describes each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="b851f-121">Microsoft Connector 1.1 for SAP BW F1 帮助</span><span class="sxs-lookup"><span data-stu-id="b851f-121">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
 <span data-ttu-id="b851f-122">介绍 SAP BW 的连接器1.1 的每个组件的用户界面 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b851f-122">Describes the user interface of each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
  
