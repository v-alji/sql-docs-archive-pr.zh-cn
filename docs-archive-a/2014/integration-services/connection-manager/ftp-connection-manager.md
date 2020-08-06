---
title: FTP 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a402f399ba4b7e69fc1d3cbca9dd64b32217ced1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688120"
---
# <a name="ftp-connection-manager"></a><span data-ttu-id="1fcf4-102">FTP 连接管理器</span><span class="sxs-lookup"><span data-stu-id="1fcf4-102">FTP Connection Manager</span></span>
  <span data-ttu-id="1fcf4-103">FTP 连接管理器使得包可以连接到文件传输协议 (FTP) 服务器。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-103">An FTP connection manager enables a package to connect to a File Transfer Protocol (FTP) server.</span></span> <span data-ttu-id="1fcf4-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的 FTP 任务使用此连接管理器。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-104">The FTP task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="1fcf4-105">将 FTP 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建可以在运行时决定 FTP 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包中的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-105">When you add an FTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that can be resolved as an FTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="1fcf4-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `FTP`。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-106">The `ConnectionManagerType` property of the connection manager is set to `FTP`.</span></span>  
  
 <span data-ttu-id="1fcf4-107">可以按照下列方式配置 FTP 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="1fcf4-107">You can configure the FTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="1fcf4-108">指定服务器名称和服务器端口。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-108">Specify a server name and server port.</span></span>  
  
-   <span data-ttu-id="1fcf4-109">指定采用匿名访问，或者提供用户名和密码以进行基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-109">Specify anonymous access, or provide a user name and a password for basic authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1fcf4-110">FTP 连接管理器仅支持匿名身份验证和基本身份验证，</span><span class="sxs-lookup"><span data-stu-id="1fcf4-110">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="1fcf4-111">而不支持 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="1fcf4-112">设置超时值、重试次数和可以一次复制的数据量。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-112">Set the time-out, number of retries, and the amount of data to copy at a time.</span></span>  
  
-   <span data-ttu-id="1fcf4-113">指示 FTP 连接管理器使用被动还是主动模式。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-113">Indicate whether the FTP connection manager uses passive or active mode.</span></span>  
  
 <span data-ttu-id="1fcf4-114">取决于与 FTP 连接管理器连接的 FTP 站点的配置，可能需要更改连接管理器的以下默认值：</span><span class="sxs-lookup"><span data-stu-id="1fcf4-114">Depending on the configuration of the FTP site to which the FTP connection manager connects, you may need to change the following default values of the connection manager:</span></span>  
  
-   <span data-ttu-id="1fcf4-115">服务器端口设置为 21。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-115">The server port is set to 21.</span></span> <span data-ttu-id="1fcf4-116">应当指定 FTP 站点侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-116">You should specify the port that the FTP site listens to.</span></span>  
  
-   <span data-ttu-id="1fcf4-117">用户名设置为“anonymous”。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-117">The user name is set to "anonymous".</span></span> <span data-ttu-id="1fcf4-118">应当提供 FTP 站点需要的凭据。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-118">You should provide the credentials that the FTP site requires.</span></span>  
  
## <a name="activepassive-modes"></a><span data-ttu-id="1fcf4-119">主动/被动模式</span><span class="sxs-lookup"><span data-stu-id="1fcf4-119">Active/Passive Modes</span></span>  
 <span data-ttu-id="1fcf4-120">FTP 连接管理器可以使用主动模式或被动模式发送和接收文件。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-120">An FTP connection manager can send and receive files using either active mode or passive mode.</span></span> <span data-ttu-id="1fcf4-121">在主动模式下，由服务器初始化数据连接；而在被动模式下，由客户端初始化数据连接。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-121">In active mode, the server initiates the data connection, and in passive mode, the client initiates the data connection.</span></span>  
  
## <a name="configuration-of-the-ftp-connection-manager"></a><span data-ttu-id="1fcf4-122">FTP 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="1fcf4-122">Configuration of the FTP Connection Manager</span></span>  
 <span data-ttu-id="1fcf4-123">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1fcf4-124">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请参阅 [TP 连接管理器编辑器](../ftp-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-124">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [FTP Connection Manager Editor](../ftp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="1fcf4-125">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="1fcf4-125">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fcf4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fcf4-126">See Also</span></span>  
 <span data-ttu-id="1fcf4-127">[FTP 任务](../control-flow/ftp-task.md) </span><span class="sxs-lookup"><span data-stu-id="1fcf4-127">[FTP Task](../control-flow/ftp-task.md) </span></span>  
 [<span data-ttu-id="1fcf4-128">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="1fcf4-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
