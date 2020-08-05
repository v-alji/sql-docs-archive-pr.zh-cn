---
title: SAP BW 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 06b166a1-a9df-48ea-a0e8-9b8d6979c0a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3bb32c4895c6ec8fbcf31d57e8685c74de32dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579005"
---
# <a name="sap-bw-connection-manager"></a><span data-ttu-id="f2ac4-102">SAP BW 连接管理器</span><span class="sxs-lookup"><span data-stu-id="f2ac4-102">SAP BW Connection Manager</span></span>
  <span data-ttu-id="f2ac4-103">SAP BW 连接管理器是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的连接管理器组件。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-103">The SAP BW connection manager is the connection manager component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="f2ac4-104">因此，SAP BW 连接管理器提供 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的源组件和目标组件所需的与 SAP Netweaver BW 版本 7 系统连接的能力。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-104">Thus, the SAP BW connection manager provides the connectivity to an SAP Netweaver BW version 7 system that the source and destination components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW need.</span></span> <span data-ttu-id="f2ac4-105">（SAP BW 源组件和目标组件作为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 包的一部分，是唯一采用 SAP BW 连接管理器的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件。）</span><span class="sxs-lookup"><span data-stu-id="f2ac4-105">(The SAP BW source and destination that are part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package are the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that use the SAP BW connection manager.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f2ac4-106">针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="f2ac4-107">有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="f2ac4-108">当将 SAP BW 连接管理器添加到包中时，连接管理器的 `ConnectionManagerType` 属性被设为 `SAPBI`。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-108">When you add an SAP BW connection manager to a package, the `ConnectionManagerType` property of the connection manager is set to `SAPBI`.</span></span>  
  
## <a name="configuring-the-sap-bw-connection-manager"></a><span data-ttu-id="f2ac4-109">配置 SAP BW 连接管理器</span><span class="sxs-lookup"><span data-stu-id="f2ac4-109">Configuring the SAP BW Connection Manager</span></span>  
 <span data-ttu-id="f2ac4-110">可以按下列方式配置 SAP BW 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="f2ac4-110">You can configure the SAP BW connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="f2ac4-111">输入连接的客户端、用户名、密码和语言。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-111">Provide the client, user name, password, and language for the connection.</span></span>  
  
-   <span data-ttu-id="f2ac4-112">选择连接单个应用程序服务器还是连接一组负载平衡服务器。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-112">Choose whether to connect to a single application server or to a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="f2ac4-113">如果是单个应用程序服务器，需提供主机和系统编号，如果是一组负载平衡的服务器，需提供消息服务器、组和 SID。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-113">Provide the host and system number for a single application server, or provide the message server, group, and SID for a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="f2ac4-114">启用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 组件的 RFC 函数调用自定义日志记录。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-114">Enable custom logging of RFC function calls for the components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="f2ac4-115">（此日志记录与可对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包启用的可选日志记录是分开进行的。）要启用 RFC 函数调用日志记录，可以指定一个目录用来存储每次 RFC 函数调用前后创建的日志文件。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-115">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) To enable logging of RFC function calls, you specify a directory in which to store the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="f2ac4-116">（此日志记录功能会创建许多个 XML 格式的日志文件。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-116">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="f2ac4-117">这些日志文件还包含传输的所有数据行，因此可能会消耗大量的磁盘空间。）如果不选择日志目录，则不启用日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-117">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.) If you do not select a log directory, logging is not enabled.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f2ac4-118">如果传输的数据包含敏感信息，日志文件中也会包含该敏感信息。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-118">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
-   <span data-ttu-id="f2ac4-119">使用您输入的值来测试连接。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-119">Use the values that you have entered to test the connection.</span></span>  
  
 <span data-ttu-id="f2ac4-120">如果您不知道配置连接管理器所需的所有值，可能需要询问您的 SAP 管理员。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-120">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="f2ac4-121">有关演示如何配置和使用 SAP BW 连接管理器、源和目标的演练，请参阅白皮书 [将 SQL Server 2008 Integration Services 与 SAP BI 7.0 一起使用](https://go.microsoft.com/fwlink/?LinkID=137090)。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-121">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="f2ac4-122">此白皮书还说明如何在 SAP BW 中配置所需的对象。</span><span class="sxs-lookup"><span data-stu-id="f2ac4-122">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="f2ac4-123">使用 SSIS 设计器配置源</span><span class="sxs-lookup"><span data-stu-id="f2ac4-123">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="f2ac4-124">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的 SAP BW 连接管理器属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="f2ac4-124">For more information about the properties of the SAP BW connection manager that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="f2ac4-125">SAP BW 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="f2ac4-125">SAP BW Connection Manager Editor</span></span>](../sap-bw-connection-manager-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2ac4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2ac4-126">See Also</span></span>  
 [<span data-ttu-id="f2ac4-127">Microsoft Connector 1.1 for SAP BW 组件</span><span class="sxs-lookup"><span data-stu-id="f2ac4-127">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
