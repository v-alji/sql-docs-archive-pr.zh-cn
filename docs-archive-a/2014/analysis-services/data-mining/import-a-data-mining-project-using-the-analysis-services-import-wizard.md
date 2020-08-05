---
title: 使用 Analysis Services 导入向导导入数据挖掘项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b39062cc5bc5401a1746f35e98ea643db2d16c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580464"
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a><span data-ttu-id="f02b1-102">使用 Analysis Services 导入向导导入数据挖掘项目</span><span class="sxs-lookup"><span data-stu-id="f02b1-102">Import a Data Mining Project using the Analysis Services Import Wizard</span></span>
  <span data-ttu-id="f02b1-103">本主题介绍如何通过使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的模板“从服务器导入（多维和数据挖掘）项目”\*\*\*\* 从另一台服务器上的现有数据挖掘项目导入元数据，来创建新的数据挖掘项目。</span><span class="sxs-lookup"><span data-stu-id="f02b1-103">This topic describes how to create a new data mining project by importing the metadata from an existing data mining project on another server, using the template, **Import from Server (Multidimensional and Data Mining) Project**, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a><span data-ttu-id="f02b1-104">从现有数据挖掘项目导入数据源、挖掘结构和挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f02b1-104">Import data sources, mining structures, and mining models from an existing data mining project</span></span>  
 <span data-ttu-id="f02b1-105">使用模板时，**从服务器 (多维和数据挖掘) 项目中导入**， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 创建新的数据挖掘项目，然后从指定的数据挖掘项目复制元数据。</span><span class="sxs-lookup"><span data-stu-id="f02b1-105">When you use the template, **Import from Server (Multidimensional and Data Mining) Project**, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates a new data mining project, and then copies the metadata from the specified data mining project.</span></span> <span data-ttu-id="f02b1-106">该新项目包含与从中进行导入的 ssASnoversion 数据库相同的数据源、数据源视图、挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f02b1-106">The new project contains the same data sources, data source views, mining structures, and mining models as the ssASnoversion database that you imported from.</span></span> <span data-ttu-id="f02b1-107">但是，在您更新特定属性并处理对象之前将无法使用该项目，如下所述：</span><span class="sxs-lookup"><span data-stu-id="f02b1-107">However, the project cannot be used until you have updated certain properties and processed the objects as described:</span></span>  
  
-   <span data-ttu-id="f02b1-108">数据本身不会从源服务器复制到新的数据挖掘项目-仅导入数据源和数据源视图的定义。</span><span class="sxs-lookup"><span data-stu-id="f02b1-108">The data itself is not copied from the source server to the new data mining project-only the definitions of the data sources and data source views are imported.</span></span> <span data-ttu-id="f02b1-109">因此，在完成导入过程并创建对象后，您必须通过定型挖掘结构和依赖模型来用数据填充对象。</span><span class="sxs-lookup"><span data-stu-id="f02b1-109">Therefore, after the import process has completed, and the objects have been created, you must populate the objects with data by training the mining structures and dependent models.</span></span> <span data-ttu-id="f02b1-110">可以在数据挖掘设计器中使用命令 **“全部处理”** 来定型模型和结构。</span><span class="sxs-lookup"><span data-stu-id="f02b1-110">You can use the command **Process All** in Data Mining Designer to train the models and structures.</span></span>  
  
-   <span data-ttu-id="f02b1-111">如果您导入的是已在早期版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中创建的项目，则数据源可能会使用项目要导入到的服务器上未安装的访问接口。</span><span class="sxs-lookup"><span data-stu-id="f02b1-111">If you are importing a project that was created in a previous version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the data source might use providers that are not installed on the server to which you are importing the project.</span></span> <span data-ttu-id="f02b1-112">如果处理导入的挖掘结构时出错，请右键单击每个数据源并选择“打开设计器”\*\*\*\* 以编辑连接字符串和查看提供程序属性。</span><span class="sxs-lookup"><span data-stu-id="f02b1-112">If you encounter errors when processing the imported mining structures, right-click each data source and select **Open Designer** to edit the connection string and review the provider properties.</span></span>  
  
     <span data-ttu-id="f02b1-113">此时，您可能还需要验证要用于处理数据挖掘对象或查询数据挖掘模型的帐户是否具有对数据源的必要权限。</span><span class="sxs-lookup"><span data-stu-id="f02b1-113">At this time, you might also need to verify that the account you are using to process the data mining objects or query data mining models has the necessary permissions on the data source.</span></span>  
  
-   <span data-ttu-id="f02b1-114">默认情况下，在导入项目时，工作区数据库会设置为本地主机，或者任意默认实例会在 **中配置为** “默认目标服务器” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f02b1-114">By default, when you import a project, the workspace database is set to localhost, or whatever default instance is configured as the **Default Target Server** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f02b1-115">若要设置此属性，请从 **“选项”** 菜单中依次选择 **“商业智能设计器”**、 **“Analysis Services”** 和 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="f02b1-115">To set this property, from the **Options** menu, select **Business Intelligence Designers**, select **Analysis Services**, and then select **General**.</span></span>  
  
     <span data-ttu-id="f02b1-116">请注意， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中还包含一个单独选项，可设置此选项以便为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格模型项目配置默认部署服务器。</span><span class="sxs-lookup"><span data-stu-id="f02b1-116">Note that, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], there is another, separate option that you can set to configure the default deployment server for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular model projects.</span></span> <span data-ttu-id="f02b1-117">**“默认部署服务器”** 设置可确定表格模型项目的默认工作区数据库。</span><span class="sxs-lookup"><span data-stu-id="f02b1-117">The setting, **Default Deployment Server**, determines the default workspace database for tabular model projects.</span></span> <span data-ttu-id="f02b1-118">不能对数据挖掘项目使用支持表格模型的实例</span><span class="sxs-lookup"><span data-stu-id="f02b1-118">You cannot use instances that support tabular models for data mining projects</span></span>  
  
     <span data-ttu-id="f02b1-119">如果无法更改默认部署数据库以使用在多维或数据挖掘模式下运行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，则可始终通过使用 **“项目属性”** 对话框来指定部署数据库。</span><span class="sxs-lookup"><span data-stu-id="f02b1-119">If you cannot change the default deployment database to use an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running in multidimensional or data mining mode, you can always specify the deployment database by using the **Project Properties** dialog box.</span></span>  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a><span data-ttu-id="f02b1-120">通过导入现有数据挖掘项目来创建新的数据挖掘项目</span><span class="sxs-lookup"><span data-stu-id="f02b1-120">To create a new data mining project by importing an existing data mining project</span></span>  
  
1.  <span data-ttu-id="f02b1-121">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="f02b1-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f02b1-122">在“新建项目”\*\*\*\* 对话框中，在“已安装的模板”\*\*\*\* 下，依次单击“商业智能”\*\*\*\*、“Analysis Services”\*\*\*\* 和“从服务器导入（多维/数据挖掘）”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f02b1-122">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, click **Analysis Services**, and then click **Import from Server (Multidimensional/Data Mining)**.</span></span>  
  
3.  <span data-ttu-id="f02b1-123">在 **“名称”** 中，键入项目的名称，然后指定位置和解决方案名称，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="f02b1-123">For **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f02b1-124">这将启动 **“导入 Analysis Services 数据库向导”** 。</span><span class="sxs-lookup"><span data-stu-id="f02b1-124">The **Import Analysis Services Database wizard** starts.</span></span> <span data-ttu-id="f02b1-125">单击“欢迎使用”页面上的“确定”以继续。</span><span class="sxs-lookup"><span data-stu-id="f02b1-125">Click OK on the Welcome page to proceed.</span></span>  
  
4.  <span data-ttu-id="f02b1-126">在该页上的 **“选择源数据库”** 中，对于 **“服务器”**，指定包含要导入的解决方案的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f02b1-126">On the page, **Select Source Database**, for **Server**, specify the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that contains the solution you want to import.</span></span>  
  
     <span data-ttu-id="f02b1-127">对于 **“数据库”**，选择包含要导入的数据挖掘对象的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="f02b1-127">For **Database**, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the data mining objects you want to import.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="f02b1-128">无法指定要导入的对象；在选择现有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库时，会导入所有多维和数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="f02b1-128">You cannot specify the objects you want to import; when you choose an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, all multidimensional and data mining objects are imported.</span></span>  
  
     <span data-ttu-id="f02b1-129">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f02b1-129">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="f02b1-130">**“完成向导”** 页将显示导入操作的进度。</span><span class="sxs-lookup"><span data-stu-id="f02b1-130">The page, **Completing the Wizard**, displays the progress of the import operation.</span></span> <span data-ttu-id="f02b1-131">无法取消该操作或更改正在导入的对象。</span><span class="sxs-lookup"><span data-stu-id="f02b1-131">You cannot cancel the operation or change the objects that are being imported.</span></span> <span data-ttu-id="f02b1-132">完成操作后，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="f02b1-132">Click **Finish** when done.</span></span>  
  
     <span data-ttu-id="f02b1-133">这将自动使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]打开新对象。</span><span class="sxs-lookup"><span data-stu-id="f02b1-133">The new project is automatically opened using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f02b1-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f02b1-134">See Also</span></span>  
 [<span data-ttu-id="f02b1-135">项目属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="f02b1-135">Project Properties &#40;SSAS Tabular&#41;</span></span>](../tabular-models/properties-ssas-tabular.md)  
  
  
