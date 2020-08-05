---
title: " (基本数据挖掘教程) 创建数据源 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d8d5974c3685476f5d7a5751fb71bfa98384cf36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580482"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a><span data-ttu-id="c27d2-102">创建数据源（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c27d2-102">Creating a Data Source (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c27d2-103">*数据源*是在项目中保存和管理并部署到数据库的数据连接 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c27d2-103">A *data source* is a data connection that is saved and managed in your project and deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="c27d2-104">除了其他所有必需的连接属性外，数据源还包含源数据所在的服务器和数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c27d2-104">The data source contains the names of the server and database where your source data resides, in addition to any other required connection properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c27d2-105">数据库的名称为 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c27d2-105">The name of the database is [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="c27d2-106">如果尚未安装此数据库，请参阅[MICROSOFT SQL 示例数据库](https://go.microsoft.com/fwlink/?LinkId=88417)页。</span><span class="sxs-lookup"><span data-stu-id="c27d2-106">If you have not already installed this database, see the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page.</span></span>  
  
### <a name="to-create-a-data-source"></a><span data-ttu-id="c27d2-107">创建数据源</span><span class="sxs-lookup"><span data-stu-id="c27d2-107">To create a data source</span></span>  
  
1.  <span data-ttu-id="c27d2-108">在**解决方案资源管理器**中，右键单击 "**数据源**" 文件夹，然后选择 "**新建数据源**"。</span><span class="sxs-lookup"><span data-stu-id="c27d2-108">In **Solution Explorer**, right-click the **Data Sources** folder and select **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="c27d2-109">在“欢迎使用数据源向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="c27d2-109">On the **Welcome to the Data Source Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="c27d2-110">在 "**选择如何定义连接"** 页上，单击 "**新建**" 以添加到数据库的连接 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c27d2-110">On the **Select how to define the connection** page, click **New** to add a connection to the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="c27d2-111">在**连接管理器**的 "**提供程序**" 列表中，选择 "**本机 OLE DB\SQL Server native Client 11.0**"。</span><span class="sxs-lookup"><span data-stu-id="c27d2-111">In the **Provider** list in **Connection Manager**, select **Native OLE DB\SQL Server Native Client 11.0**.</span></span>  
  
5.  <span data-ttu-id="c27d2-112">在 "**服务器名称**" 框中，键入或选择安装了的服务器的名称 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c27d2-112">In the **Server name** box, type or select the name of the server on which you installed [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span>  
  
     <span data-ttu-id="c27d2-113">例如，如果在本地服务器上承载该数据库，请键入**localhost** 。</span><span class="sxs-lookup"><span data-stu-id="c27d2-113">For example, type **localhost** if the database is hosted on the local server.</span></span>  
  
6.  <span data-ttu-id="c27d2-114">在 "**登录到服务器**" 组中，选择 "**使用 Windows 身份验证**"。</span><span class="sxs-lookup"><span data-stu-id="c27d2-114">In the **Log onto the server** group, select **Use Windows Authentication**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c27d2-115">实施者应尽可能使用 Windows 身份验证，因为它提供的身份验证方法比 SQL Server 身份验证更加安全。</span><span class="sxs-lookup"><span data-stu-id="c27d2-115">Whenever possible, implementers should use Windows Authentication, as it provides a more secure authentication method than SQL Server Authentication.</span></span> <span data-ttu-id="c27d2-116">而提供 SQL Server 身份验证只是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="c27d2-116">However, SQL Server Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="c27d2-117">有关身份验证方法的详细信息，请参阅[数据库引擎配置-帐户设置](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)。</span><span class="sxs-lookup"><span data-stu-id="c27d2-117">For more information about authentication methods, see [Database Engine Configuration - Account Provisioning](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).</span></span>  
  
7.  <span data-ttu-id="c27d2-118">在 "**选择或输入数据库名称**" 列表中，选择， [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="c27d2-118">In the **Select or enter a database name** list, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c27d2-119">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c27d2-119">Click **Next**.</span></span>  
  
9. <span data-ttu-id="c27d2-120">在 "**模拟信息**" 页上，单击 "**使用服务帐户**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="c27d2-120">On the **Impersonation Information** page, click **Use the service account**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="c27d2-121">在 "**完成向导**" 页上，请注意，默认情况下，数据源名为 "艾德作品 DW 2012"。</span><span class="sxs-lookup"><span data-stu-id="c27d2-121">On the **Completing the Wizard** page, notice that, by default, the data source is named Adventure Works DW 2012.</span></span>  
  
10. <span data-ttu-id="c27d2-122">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="c27d2-122">Click **Finish**.</span></span>  
  
     <span data-ttu-id="c27d2-123">新数据源（艾德公司 DW 2012）出现在解决方案资源管理器的 "**数据源**" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c27d2-123">The new data source, Adventure Works DW 2012, appears in the **Data Sources** folder in Solution Explorer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c27d2-124">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c27d2-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c27d2-125">创建数据源视图 &#40;数据挖掘基础教程&#41;</span><span class="sxs-lookup"><span data-stu-id="c27d2-125">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="c27d2-126">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="c27d2-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="c27d2-127">&#40;数据挖掘基础教程创建 Analysis Services 项目&#41;</span><span class="sxs-lookup"><span data-stu-id="c27d2-127">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c27d2-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c27d2-128">See Also</span></span>  
 <span data-ttu-id="c27d2-129">[&#40;SSAS 多维&#41;创建数据源](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="c27d2-129">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 <span data-ttu-id="c27d2-130">[定义数据源](../analysis-services/lesson-1-2-defining-a-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="c27d2-130">[Defining a Data Source](../analysis-services/lesson-1-2-defining-a-data-source.md) </span></span>  
 [<span data-ttu-id="c27d2-131">设置模拟选项（SSAS - 多维）</span><span class="sxs-lookup"><span data-stu-id="c27d2-131">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  
