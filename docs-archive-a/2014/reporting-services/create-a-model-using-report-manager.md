---
title: 使用报表管理器创建模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59ce278a22ec9797b001ca37a0bde576483cf5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691126"
---
# <a name="create-a-model-using-report-manager"></a><span data-ttu-id="4e5a3-102">使用报表管理器创建模型</span><span class="sxs-lookup"><span data-stu-id="4e5a3-102">Create a Model Using Report Manager</span></span>
  <span data-ttu-id="4e5a3-103">您可以使用报表管理器从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库或 Oracle 数据库生成模型。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-103">You can generate models from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, or an Oracle database using Report Manager.</span></span> <span data-ttu-id="4e5a3-104">报表模型是从已发布到报表服务器上的共享数据源中生成。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-104">Report models are generated from shared data sources that are published on the report server.</span></span> <span data-ttu-id="4e5a3-105">如果尚未拥有共享数据源，则必须先创建一个。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-105">If you do not already have a shared data source, you must create one.</span></span>  
  
 <span data-ttu-id="4e5a3-106">生成的报表模型完全基于共享数据源的架构。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-106">The report model that you generate is based entirely on the schema of the shared data source.</span></span> <span data-ttu-id="4e5a3-107">您无法选择将数据源的哪些部分包含在模型中，也无法编辑所生成模型的规则或元数据。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-107">You cannot choose which parts of the data source are included in the model, nor can you edit the rules or metadata of a generated model.</span></span> <span data-ttu-id="4e5a3-108">不过，您可以在模型生成之后设置其属性，并定义用来限制访问整个或部分模型的角色分配。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-108">However, you can set properties on the model after it is generated and define role assignments that restrict access to all or part of the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e5a3-109">使用报表管理器或2007生成的基于 Oracle 的模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] [!INCLUDE[SPS2010](../includes/sps2010-md.md)] 将包含数据库对象，这些对象是用于连接到 Oracle 数据源的用户帐户架构的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-109">An Oracle-based model generated using Report Manager or [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] will include database objects that are a part of the schema for the user account used to connect to the Oracle data source.</span></span> <span data-ttu-id="4e5a3-110">该用户帐户名在数据源属性凭据中指定。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-110">The user account name is specified in the data source properties credentials.</span></span>  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a><span data-ttu-id="4e5a3-111">使用报表管理器为报表模型创建新数据源</span><span class="sxs-lookup"><span data-stu-id="4e5a3-111">To create a new data source for a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="4e5a3-112">在 Web 浏览器的地址栏中，键入报表服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-112">In your Web browser, type the URL for your report server in the address bar.</span></span>  
  
2.  <span data-ttu-id="4e5a3-113">单击 **“新建数据源”**。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-113">Click **New Data Source**.</span></span>  
  
3.  <span data-ttu-id="4e5a3-114">在 **“名称”** 框中，为数据源输入名称。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-114">In the **Name** box, enter a name for the data source.</span></span>  
  
4.  <span data-ttu-id="4e5a3-115">根据需要，可以在 **“说明”** 文本框中输入模式的简短说明。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-115">Optionally, enter a brief description of the mode in the **Description** text box.</span></span>  
  
5.  <span data-ttu-id="4e5a3-116">确认选中了 **“启用此数据源”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-116">Verify that the **Enable this data source** check box is selected.</span></span>  
  
6.  <span data-ttu-id="4e5a3-117">在 **“连接类型”** 列表中，选择要连接的数据源类型。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-117">In the **Connection type** list, select the data source type to which you want to connect.</span></span> <span data-ttu-id="4e5a3-118">连接类型必须是以下类型之一： **Oracle**、 **Microsoft SQL Server** 或 **Microsoft SQL Server Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-118">The connection type must be one of the following: **Oracle**, **Microsoft SQL Server** or **Microsoft SQL Server Analysis Services**.</span></span>  
  
7.  <span data-ttu-id="4e5a3-119">在 **“连接字符串”** 框中，输入指向数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-119">In the **Connection string** box, enter the connection string that points to the database.</span></span>  
  
8.  <span data-ttu-id="4e5a3-120">选择报表生成器用户连接数据库需要使用的连接方法。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-120">Select the connection method that Report Builder users will need to use to connect to the database.</span></span>  
  
    -   <span data-ttu-id="4e5a3-121">Windows 身份验证：如果希望操作系统对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用户进行身份验证，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-121">Windows Authentication: Select this option when you want the operating system to authenticate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] users.</span></span> <span data-ttu-id="4e5a3-122">如果选择此选项，则允许 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用 Windows 安全功能（如密码加密）对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-122">This option allows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use Windows security features, such as password encryption, to authenticate users.</span></span> <span data-ttu-id="4e5a3-123">极力建议选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-123">It is strongly recommended that you select this option.</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="4e5a3-124">身份验证：如果希望用户使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 您创建的登录帐户，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-124">Authentication: Select this option when you want users to use a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account that you created.</span></span> <span data-ttu-id="4e5a3-125">用户必须提供有效的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-125">Users must supply a valid [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login name and password.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="4e5a3-126">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-126">Whenever possible, use Windows Authentication.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a><span data-ttu-id="4e5a3-127">使用报表管理器创建报表模型</span><span class="sxs-lookup"><span data-stu-id="4e5a3-127">To create a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="4e5a3-128">在报表管理器中，选择要用于模型的数据源。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-128">In Report Manager, select the data source that you want to use for your model.</span></span>  
  
     <span data-ttu-id="4e5a3-129">此时，将显示“属性”页。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-129">The Properties page is displayed.</span></span>  
  
2.  <span data-ttu-id="4e5a3-130">确保为数据源指定的选项满足需要。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-130">Verify that you want to use the options specified for the data source.</span></span>  
  
3.  <span data-ttu-id="4e5a3-131">单击 **“生成模型”**。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-131">Click **Generate Model**.</span></span>  
  
     <span data-ttu-id="4e5a3-132">此时，将显示数据源的“常规”页。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-132">The General page is displayed for the data source.</span></span>  
  
4.  <span data-ttu-id="4e5a3-133">在 **“名称”** 框中，为报表模型输入名称。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-133">In the **Name** box, enter a name for the report model.</span></span>  
  
5.  <span data-ttu-id="4e5a3-134">在 **“说明”** 框中，输入对模型的简要说明。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-134">In the **Description** box, enter a brief description of the model.</span></span>  
  
6.  <span data-ttu-id="4e5a3-135">若要指定新的位置保存报表模型，请单击 **“更改位置”**。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-135">To specify a new location to save the report model to, click **Change Location**.</span></span>  
  
     <span data-ttu-id="4e5a3-136">默认情况下，报表模型将保存到报表管理器主文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-136">By default, the report model is saved to Report Manager Home.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4e5a3-137">此时，将创建报表模型并会将其保存到您指定的位置。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-137">The report model is created and saved to the location that you specified.</span></span> <span data-ttu-id="4e5a3-138">您可以使用报表管理器分配对此模型的权限。</span><span class="sxs-lookup"><span data-stu-id="4e5a3-138">You can assign permissions to this model by using Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5a3-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e5a3-139">See Also</span></span>  
 <span data-ttu-id="4e5a3-140">[授予对本机模式报表服务器的权限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="4e5a3-140">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="4e5a3-141">[Reporting Services 中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4e5a3-141">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="4e5a3-142">“新建数据源”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="4e5a3-142">New Data Source Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  
