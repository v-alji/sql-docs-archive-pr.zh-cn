---
title: 在 ReadOnly 和 ReadWrite 模式之间切换 Analysis Services 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 757aedd985d969f932deacf5599716078021a1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682405"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a><span data-ttu-id="43549-102">在 ReadOnly 和 ReadWrite 模式之间切换 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="43549-102">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>
  <span data-ttu-id="43549-103">通常情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库管理员 (dba) 需要更改表格的读/写模式或多维数据库。</span><span class="sxs-lookup"><span data-stu-id="43549-103">There are often situations when a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to change the read/write mode of a tabular or multidimensional database.</span></span> <span data-ttu-id="43549-104">根据业务需要（如在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器池中共享数据库以获得更好的用户体验），经常需要进行上述操作。</span><span class="sxs-lookup"><span data-stu-id="43549-104">These situations are often driven by business needs, such as sharing the database among a pool of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers for a better user experience.</span></span>  
  
 <span data-ttu-id="43549-105">可以通过多种方式来切换数据库模式。</span><span class="sxs-lookup"><span data-stu-id="43549-105">A database mode can be switched in many ways.</span></span> <span data-ttu-id="43549-106">本文档介绍下列常见方案：</span><span class="sxs-lookup"><span data-stu-id="43549-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="43549-107">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43549-107">Interactively using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="43549-108">使用 AMO 以编程方式</span><span class="sxs-lookup"><span data-stu-id="43549-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="43549-109">使用 XMLA 借助于脚本</span><span class="sxs-lookup"><span data-stu-id="43549-109">By script using XMLA</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="43549-110">过程</span><span class="sxs-lookup"><span data-stu-id="43549-110">Procedures</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a><span data-ttu-id="43549-111">使用 Management Studio 以交互方式切换数据库的读写模式</span><span class="sxs-lookup"><span data-stu-id="43549-111">To switch the read/write mode of a database interactively using Management Studio</span></span>  
  
1.  <span data-ttu-id="43549-112">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的左窗格或右窗格中找到要切换的数据库。</span><span class="sxs-lookup"><span data-stu-id="43549-112">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="43549-113">右键单击该数据库并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="43549-113">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="43549-114">查找数据库文件夹并记下其位置。</span><span class="sxs-lookup"><span data-stu-id="43549-114">Find the database folder and note the location.</span></span> <span data-ttu-id="43549-115">如果数据库存储位置为空，则表明数据库文件夹位于服务器数据文件夹中。</span><span class="sxs-lookup"><span data-stu-id="43549-115">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="43549-116">在将数据库分离之后， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 就不能再帮助您获取数据库位置。</span><span class="sxs-lookup"><span data-stu-id="43549-116">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="43549-117">右键单击该数据库并选择 "**分离 ...** "</span><span class="sxs-lookup"><span data-stu-id="43549-117">Right-click the database and select **Detach...**</span></span>  
  
4.  <span data-ttu-id="43549-118">为要分离的数据库分配一个密码，然后单击 **“确定”** 执行分离命令。</span><span class="sxs-lookup"><span data-stu-id="43549-118">Assign a password to the database to be detached, and then click **OK** to execute the detach command.</span></span>  
  
5.  <span data-ttu-id="43549-119">在 **的左窗格或右窗格中找到** “数据库” [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]文件夹。</span><span class="sxs-lookup"><span data-stu-id="43549-119">Locate the **Databases** folder in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
6.  <span data-ttu-id="43549-120">右键单击 "**数据库**" 文件夹，然后选择 "**附加 ...** "</span><span class="sxs-lookup"><span data-stu-id="43549-120">Right-click the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="43549-121">在 **“文件夹”** 文本框中，键入数据库文件夹的原始位置。</span><span class="sxs-lookup"><span data-stu-id="43549-121">In the **folder** text box, type the original location of the database folder.</span></span> <span data-ttu-id="43549-122">或者，您可以使用 "浏览" 按钮 (**...** ") 查找数据库文件夹。</span><span class="sxs-lookup"><span data-stu-id="43549-122">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="43549-123">针对该数据库选择读写模式。</span><span class="sxs-lookup"><span data-stu-id="43549-123">Select the read/write mode for the database.</span></span>  
  
9. <span data-ttu-id="43549-124">键入步骤 3 中使用的密码，然后单击 **“确定”** 执行附加命令。</span><span class="sxs-lookup"><span data-stu-id="43549-124">Type the password that was used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a><span data-ttu-id="43549-125">使用 AMO 以编程方式切换数据库的读写模式</span><span class="sxs-lookup"><span data-stu-id="43549-125">To switch the read/write mode to a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="43549-126">在 C# 应用程序中，修改以下示例代码并完成所指示的任务。</span><span class="sxs-lookup"><span data-stu-id="43549-126">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="43549-127">在 C# 应用程序中，用必要的参数调用 `SwitchReadWrite()` 。</span><span class="sxs-lookup"><span data-stu-id="43549-127">In your C# application, invoke `SwitchReadWrite()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="43549-128">编译和执行您的代码以移动该数据库。</span><span class="sxs-lookup"><span data-stu-id="43549-128">Compile and execute your code to move the database.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a><span data-ttu-id="43549-129">使用 XMLA 借助于脚本切换数据库的读写模式</span><span class="sxs-lookup"><span data-stu-id="43549-129">To switch the read/write mode to a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="43549-130">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的左窗格或右窗格中找到要切换的数据库。</span><span class="sxs-lookup"><span data-stu-id="43549-130">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="43549-131">右键单击该数据库并选择 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="43549-131">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="43549-132">查找数据库文件夹并记下其位置。</span><span class="sxs-lookup"><span data-stu-id="43549-132">Find the database folder and note the location.</span></span> <span data-ttu-id="43549-133">如果数据库存储位置为空，则表明数据库文件夹位于服务器数据文件夹中。</span><span class="sxs-lookup"><span data-stu-id="43549-133">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="43549-134">在将数据库分离之后， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 就不能再帮助您获取数据库位置。</span><span class="sxs-lookup"><span data-stu-id="43549-134">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="43549-135">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中打开一个新的 XMLA 选项卡。</span><span class="sxs-lookup"><span data-stu-id="43549-135">Open a new XMLA tab in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="43549-136">复制下面的 XMLA 脚本模板：</span><span class="sxs-lookup"><span data-stu-id="43549-136">Copy the following script template for XMLA:</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="43549-137">将 `%dbName%` 替换为数据库名称，将 `%password%` 替换为您的密码。</span><span class="sxs-lookup"><span data-stu-id="43549-137">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="43549-138">% 字符是模板的一部分，必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="43549-138">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="43549-139">执行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="43549-139">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="43549-140">在新的 XMLA 选项卡中复制下面的 XMLA 脚本模板</span><span class="sxs-lookup"><span data-stu-id="43549-140">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 <span data-ttu-id="43549-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span><span class="sxs-lookup"><span data-stu-id="43549-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span></span>  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="43549-142">将 `%dbFolder%` 替换为数据库文件夹的完整 UNC 路径，将 `%ReadOnlyMode%` 替换为相应值（`ReadOnly` 或 `ReadWrite`），并将 `%password%` 替换为您的密码。</span><span class="sxs-lookup"><span data-stu-id="43549-142">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="43549-143">% 字符是模板的一部分，必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="43549-143">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="43549-144">执行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="43549-144">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43549-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43549-145">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="43549-146">[Microsoft.analysisservices.sharepoint.integration.dll \*。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="43549-146">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="43549-147">[附加和分离 Analysis Services 数据库](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="43549-147">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="43549-148">[数据库存储位置](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="43549-148">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="43549-149">[数据库 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="43549-149">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="43549-150">[附加元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="43549-150">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="43549-151">[分离元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="43549-151">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="43549-152">[ReadWriteMode 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="43549-152">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="43549-153">DbStorageLocation 元素</span><span class="sxs-lookup"><span data-stu-id="43549-153">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
