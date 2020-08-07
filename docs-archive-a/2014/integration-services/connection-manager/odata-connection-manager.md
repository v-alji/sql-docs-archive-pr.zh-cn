---
title: OData 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587965"
---
# <a name="odata-connection-manager"></a><span data-ttu-id="1fbd7-102">OData 连接管理器</span><span class="sxs-lookup"><span data-stu-id="1fbd7-102">OData Connection Manager</span></span>
  <span data-ttu-id="1fbd7-103">OData 连接管理器允许包连接到 OData 源。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-103">An OData connection manager enables a package to connect to an OData source.</span></span> <span data-ttu-id="1fbd7-104">OData 源组件使用 OData 连接管理器连接到 OData 源并使用来自服务的数据。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-104">An OData Source component connects to an OData source using an OData connection manager and consumes data from the service.</span></span> <span data-ttu-id="1fbd7-105">有关详细信息（包括这些组件的安装说明），请参阅[OData 源](../data-flow/odata-source.md)部分。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-105">See [OData Source](../data-flow/odata-source.md)section for detailed information including the installation instructions for these components.</span></span>  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a><span data-ttu-id="1fbd7-106">向 SSIS 包添加连接管理器</span><span class="sxs-lookup"><span data-stu-id="1fbd7-106">Adding Connection Manager to an SSIS Package</span></span>  
 <span data-ttu-id="1fbd7-107">可以通过三种方式向 SSIS 包添加新 OData 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="1fbd7-107">You can add a new OData Connection Manager to an SSIS package in three ways:</span></span>  
  
-   <span data-ttu-id="1fbd7-108">单击“OData 源编辑器”中的“新建…”按钮  </span><span class="sxs-lookup"><span data-stu-id="1fbd7-108">Click the **New...** button in the **OData Source Editor**</span></span>  
  
-   <span data-ttu-id="1fbd7-109">右键单击 "**解决方案资源管理器**中的"**连接管理**器 "文件夹，然后单击"**新建连接管理器**"。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-109">Right-click **Connection Managers** folder in the **Solution Explorer** and click **New Connection Manager**.</span></span> <span data-ttu-id="1fbd7-110">为 **“连接管理器类型”** 选择 **“ODATA”** 。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-110">Select **ODATA** for **Connection manager type**.</span></span>  
  
-   <span data-ttu-id="1fbd7-111">右键单击包设计器底部的 "**连接管理器**" 窗格，然后选择 "**新建连接 ...**"。为 "**连接管理器类型**" 选择 " **ODATA** "。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-111">Right-click in the **Connection Managers** pane at the bottom of the package designer, and select **New Connection...**. Select **ODATA** for **Connection manager type**.</span></span>  
  
## <a name="connection-manager-authentication"></a><span data-ttu-id="1fbd7-112">连接管理器身份验证</span><span class="sxs-lookup"><span data-stu-id="1fbd7-112">Connection Manager Authentication</span></span>  
 <span data-ttu-id="1fbd7-113">OData 连接管理器支持两种身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-113">The OData Connection Manager supports two modes of authentication.</span></span>  
  
-   <span data-ttu-id="1fbd7-114">Windows 身份验证</span><span class="sxs-lookup"><span data-stu-id="1fbd7-114">Windows Authentication</span></span>  
  
-   <span data-ttu-id="1fbd7-115">基本身份验证（用户名/密码）</span><span class="sxs-lookup"><span data-stu-id="1fbd7-115">Basic Authentication (username/password)</span></span>  
  
 <span data-ttu-id="1fbd7-116">对于匿名访问，请选择“Windows 身份验证”选项</span><span class="sxs-lookup"><span data-stu-id="1fbd7-116">For anonymous access, select the Windows Authentication option</span></span>  
  
### <a name="specifying-and-securing-credentials"></a><span data-ttu-id="1fbd7-117">指定和保护凭据</span><span class="sxs-lookup"><span data-stu-id="1fbd7-117">Specifying and Securing Credentials</span></span>  
 <span data-ttu-id="1fbd7-118">如果 OData 服务需要基本身份验证，则可以在[OData 连接管理器编辑器](../odata-connection-manager-editor.md)中指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-118">If your OData service requires basic authentication, you can specify a username and password in the [OData Connection Manager Editor](../odata-connection-manager-editor.md).</span></span> <span data-ttu-id="1fbd7-119">在编辑器中输入的值保留在包中。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-119">The values you enter in the editor are persisted in the package.</span></span> <span data-ttu-id="1fbd7-120">密码值根据包保护级别进行加密。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-120">The password value is encrypted according to the package protection level.</span></span>  
  
 <span data-ttu-id="1fbd7-121">可通过多种方式外部化/参数化用户名和密码值。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-121">There are multiple ways to externalize/parameterize the username and password values.</span></span> <span data-ttu-id="1fbd7-122">要在 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] 中实现此目的，有两种主要方式，使用参数或在使用 SQL Server Management Studio 运行包时直接设置连接管理器属性。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-122">The two primary ways of doing this in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] are by using parameters, or by setting the connection manager properties directly when you run the package using SQL Server Management Studio.</span></span>  
  
## <a name="odata-connection-manager-properties"></a><span data-ttu-id="1fbd7-123">OData 连接管理器属性</span><span class="sxs-lookup"><span data-stu-id="1fbd7-123">OData Connection Manager Properties</span></span>  
 <span data-ttu-id="1fbd7-124">下面的列表介绍您可能需要更改的部分 OData 连接管理器属性。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-124">The following list describes some of the OData Connection Manager properties that you may want to change.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1fbd7-125">properties</span><span class="sxs-lookup"><span data-stu-id="1fbd7-125">Property</span></span>|<span data-ttu-id="1fbd7-126">说明</span><span class="sxs-lookup"><span data-stu-id="1fbd7-126">Description</span></span>|  
|<span data-ttu-id="1fbd7-127">Url</span><span class="sxs-lookup"><span data-stu-id="1fbd7-127">Url</span></span>|<span data-ttu-id="1fbd7-128">服务文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-128">URL to the service document.</span></span>|  
|<span data-ttu-id="1fbd7-129">UserName</span><span class="sxs-lookup"><span data-stu-id="1fbd7-129">UserName</span></span>|<span data-ttu-id="1fbd7-130">要用于基本身份验证的用户名。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-130">Username to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="1fbd7-131">密码</span><span class="sxs-lookup"><span data-stu-id="1fbd7-131">Password</span></span>|<span data-ttu-id="1fbd7-132">要用于基本身份验证的密码。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-132">Password to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="1fbd7-133">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="1fbd7-133">ConnectionString</span></span>|<span data-ttu-id="1fbd7-134">反映连接管理器的其他属性。</span><span class="sxs-lookup"><span data-stu-id="1fbd7-134">Reflects other properties of the connection manager.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fbd7-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fbd7-135">See Also</span></span>  
 [<span data-ttu-id="1fbd7-136">“OData 连接管理器编辑器”</span><span class="sxs-lookup"><span data-stu-id="1fbd7-136">OData Connection Manager Editor</span></span>](../odata-connection-manager-editor.md)  
  
  
