---
title: 报表管理器) 上传文件页 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bb3166f-9374-4449-b66a-ffb77298507d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de03c6c6bd03cbe083d5e1edfd320264d2cc3bde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691030"
---
# <a name="upload-file-page-report-manager"></a><span data-ttu-id="22fe0-102">“上载文件”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="22fe0-102">Upload File Page (Report Manager)</span></span>
  <span data-ttu-id="22fe0-103">使用“上载文件”页可以将文件从文件系统发布到报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="22fe0-103">Use the Upload File page to publish a file from the file system into the report server database.</span></span> <span data-ttu-id="22fe0-104">上载的文件将显示为报表服务器文件夹层次结构中的项。</span><span class="sxs-lookup"><span data-stu-id="22fe0-104">Uploaded files are represented as items in the report server folder hierarchy.</span></span>  
  
-   <span data-ttu-id="22fe0-105">上载的 .rdl 文件将以报表形式发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="22fe0-105">Uploaded .rdl files are published to a report server as reports.</span></span>  
  
-   <span data-ttu-id="22fe0-106">如果上载的 .smdl 文件包含数据源视图信息，则这些文件将作为报表模型发布。</span><span class="sxs-lookup"><span data-stu-id="22fe0-106">Uploaded .smdl files are published as report models if they contain data source view information.</span></span> <span data-ttu-id="22fe0-107">如果这些文件缺少数据源视图引用，则上载时将出现错误。</span><span class="sxs-lookup"><span data-stu-id="22fe0-107">If they are missing a data source view reference, an error occurs during the upload.</span></span> <span data-ttu-id="22fe0-108">如果上传 [!INCLUDE[msCoName](../includes/msconame-md.md)] 报表模型项目中的 .smdl 文件，可能缺少数据源视图信息 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="22fe0-108">Data source view information might be missing if you upload an .smdl file from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] report model project.</span></span> <span data-ttu-id="22fe0-109">在报表模型项目中，数据源视图信息存储在 .smdl 文件之外的单独文件中。</span><span class="sxs-lookup"><span data-stu-id="22fe0-109">In report model projects, data source view information is stored in a separate file rather than in the .smdl file itself.</span></span>  
  
     <span data-ttu-id="22fe0-110">包含数据源视图信息（因此能够成功上载）的模型文件是以前已发布到报表服务器、之后又从该服务器保存到文件系统上某文件的那些文件。</span><span class="sxs-lookup"><span data-stu-id="22fe0-110">Model files that do contain data source view information (and can therefore be successfully uploaded) are those that have been previously published to a report server and then saved from the server to a file on the file system.</span></span> <span data-ttu-id="22fe0-111">如果打开某模型的“常规属性”页，再单击 **“编辑”** 来打开该模型，则可以将该模型保存到文件，再将该文件作为新模型上载到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="22fe0-111">If you open the General Properties page of a model and click **Edit** to open the model, you can save it to a file and then upload it as a new model on the report server.</span></span> <span data-ttu-id="22fe0-112">随后上载的 .smdl 文件将包含发布模型所需的所有信息。</span><span class="sxs-lookup"><span data-stu-id="22fe0-112">The .smdl file that you subsequently upload will have all of information that is necessary for model publication.</span></span>  
  
-   <span data-ttu-id="22fe0-113">您上载的所有其他文件类型都将作为资源存储。</span><span class="sxs-lookup"><span data-stu-id="22fe0-113">All other file types that you upload are stored as resources.</span></span> <span data-ttu-id="22fe0-114">其中包括含有报表数据源连接信息的 .rds 文件。</span><span class="sxs-lookup"><span data-stu-id="22fe0-114">This includes .rds files that contain report data source connection information.</span></span> <span data-ttu-id="22fe0-115">上载 .rds 文件不会在报表服务器上生成共享数据源项。</span><span class="sxs-lookup"><span data-stu-id="22fe0-115">Uploading an .rds file does not produce a shared data source item on the report server.</span></span>  
  
 <span data-ttu-id="22fe0-116">所上载的项放在当前的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="22fe0-116">When you upload an item, it is placed in the current folder.</span></span> <span data-ttu-id="22fe0-117">完成上载后，可以将该项移动至其他位置。</span><span class="sxs-lookup"><span data-stu-id="22fe0-117">After the upload is complete, you can move the item to a different location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22fe0-118">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="22fe0-118">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22fe0-119">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="22fe0-119">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="22fe0-120">导航</span><span class="sxs-lookup"><span data-stu-id="22fe0-120">Navigation</span></span>  
 <span data-ttu-id="22fe0-121">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="22fe0-121">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-upload-file-page"></a><span data-ttu-id="22fe0-122">打开“上载文件”页</span><span class="sxs-lookup"><span data-stu-id="22fe0-122">To open the Upload File page</span></span>  
  
1.  <span data-ttu-id="22fe0-123">打开报表管理器，导航到要在其中上载文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="22fe0-123">Open Report Manager, and navigate to the folder in which you want to upload a file.</span></span>  
  
2.  <span data-ttu-id="22fe0-124">在工具栏上单击 **“上载文件”**。</span><span class="sxs-lookup"><span data-stu-id="22fe0-124">In the toolbar, click **Upload File**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="22fe0-125">选项</span><span class="sxs-lookup"><span data-stu-id="22fe0-125">Options</span></span>  
 <span data-ttu-id="22fe0-126">**要上载的文件**</span><span class="sxs-lookup"><span data-stu-id="22fe0-126">**File to Upload**</span></span>  
 <span data-ttu-id="22fe0-127">显示要从文件系统复制的文件的全限定路径。</span><span class="sxs-lookup"><span data-stu-id="22fe0-127">Displays the fully qualified path to the file you are copying from the file system.</span></span>  
  
 <span data-ttu-id="22fe0-128">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="22fe0-128">**Browse**</span></span>  
 <span data-ttu-id="22fe0-129">单击此选项可从文件系统中选择文件。</span><span class="sxs-lookup"><span data-stu-id="22fe0-129">Click to choose a file from the file system.</span></span>  
  
 <span data-ttu-id="22fe0-130">**名称**</span><span class="sxs-lookup"><span data-stu-id="22fe0-130">**Name**</span></span>  
 <span data-ttu-id="22fe0-131">键入文件的名称，文件名应与将在报表服务器命名空间中显示的名称一样。</span><span class="sxs-lookup"><span data-stu-id="22fe0-131">Type the name of the file, as it will appear in the report server namespace.</span></span> <span data-ttu-id="22fe0-132">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="22fe0-132">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="22fe0-133">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="22fe0-133">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="22fe0-134">在指定名称时，不得使用字符 ; ?</span><span class="sxs-lookup"><span data-stu-id="22fe0-134">Do not use the characters ; ?</span></span> <span data-ttu-id="22fe0-135">： \@ & = +，$ \* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="22fe0-135">: \@ & = + , $ \* \< > | " or / when specifying an item name.</span></span>  
  
 <span data-ttu-id="22fe0-136">**如果该项已存在，则覆盖该项**</span><span class="sxs-lookup"><span data-stu-id="22fe0-136">**Overwrite item if it exists**</span></span>  
 <span data-ttu-id="22fe0-137">如果希望将现有项替换为更新的版本，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="22fe0-137">Select this check box if you want to replace an existing item with a newer version.</span></span> <span data-ttu-id="22fe0-138">若要覆盖现有版本，新项和现有项的名称必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="22fe0-138">To overwrite an existing version, the name of the new item and the existing item must be an exact match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fe0-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22fe0-139">See Also</span></span>  
 <span data-ttu-id="22fe0-140">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="22fe0-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="22fe0-141">["内容" 页 &#40;报表管理器&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="22fe0-141">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="22fe0-142">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="22fe0-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="22fe0-143">将文件上载到文件夹</span><span class="sxs-lookup"><span data-stu-id="22fe0-143">Upload Files to a Folder</span></span>](report-server/upload-files-to-a-folder.md)  
  
  
