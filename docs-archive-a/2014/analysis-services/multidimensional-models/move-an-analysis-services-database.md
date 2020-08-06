---
title: 移动 Analysis Services 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- moving databases [Anlysis Services]
- moving databases
- operations [Analysis Services - multidimensional data]
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd9b099ad6765d9caccb9b0af6622eb4aa77d38c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693129"
---
# <a name="move-an-analysis-services-database"></a><span data-ttu-id="37f67-102">移动 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="37f67-102">Move an Analysis Services Database</span></span>
  <span data-ttu-id="37f67-103">很多情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库管理员 (dba) 希望将多维或表格模型数据库移到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="37f67-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to move a multidimensional or tabular model database to a different location.</span></span> <span data-ttu-id="37f67-104">根据业务需要（例如，将数据库移到另一个磁盘以获得更好的性能、为数据库扩容获取空间或升级产品），经常需要进行上述操作。</span><span class="sxs-lookup"><span data-stu-id="37f67-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span>  
  
 <span data-ttu-id="37f67-105">可以通过多种方式来移动数据库。</span><span class="sxs-lookup"><span data-stu-id="37f67-105">A database can be moved in many ways.</span></span> <span data-ttu-id="37f67-106">本文档介绍下列常见方案：</span><span class="sxs-lookup"><span data-stu-id="37f67-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="37f67-107">使用 SSMS 以交互方式</span><span class="sxs-lookup"><span data-stu-id="37f67-107">Interactively using SSMS</span></span>  
  
-   <span data-ttu-id="37f67-108">使用 AMO 以编程方式</span><span class="sxs-lookup"><span data-stu-id="37f67-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="37f67-109">使用 XMLA 借助于脚本</span><span class="sxs-lookup"><span data-stu-id="37f67-109">By script using XMLA</span></span>  
  
 <span data-ttu-id="37f67-110">所有方案都要求用户能够访问数据库文件夹并使用某种方法将文件移到所需的最终目标。</span><span class="sxs-lookup"><span data-stu-id="37f67-110">All scenarios require the user to access the database folder and to use a method for moving the files to the desired final destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37f67-111">在不向数据库分配密码的情况下分离数据库会使该数据库处于不安全状态。</span><span class="sxs-lookup"><span data-stu-id="37f67-111">Detaching a database without assigning a password to it leaves the database in an unsecured state.</span></span> <span data-ttu-id="37f67-112">我们建议您为数据库分配密码以保护机密信息。</span><span class="sxs-lookup"><span data-stu-id="37f67-112">We recommend assigning a password to the database to protect confidential information.</span></span> <span data-ttu-id="37f67-113">还要向数据库文件夹、子文件夹和文件应用相应的访问安全性以防止对它们进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="37f67-113">Also, the corresponding access security should be applied to the database folder, sub-folders, and files to prevent unauthorized access to them.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="37f67-114">过程</span><span class="sxs-lookup"><span data-stu-id="37f67-114">Procedures</span></span>  
  
#### <a name="moving-a-database-interactively-using-ssms"></a><span data-ttu-id="37f67-115">使用 SSMS 以交互方式移动数据库</span><span class="sxs-lookup"><span data-stu-id="37f67-115">Moving a database interactively using SSMS</span></span>  
  
1.  <span data-ttu-id="37f67-116">在 SSMS 的左窗格或右窗格中找到要移动的数据库。</span><span class="sxs-lookup"><span data-stu-id="37f67-116">Locate the database to be moved in the left or right pane of SSMS.</span></span>  
  
2.  <span data-ttu-id="37f67-117">右键单击该数据库并选择 "**分离 ...** "</span><span class="sxs-lookup"><span data-stu-id="37f67-117">Right-click on the database and select **Detach...**</span></span>  
  
3.  <span data-ttu-id="37f67-118">为要分离的数据库分配一个密码，然后单击 **“确定”** 执行分离命令。</span><span class="sxs-lookup"><span data-stu-id="37f67-118">Assign a password to the database to be detached, then click **OK** to execute the detach command.</span></span>  
  
4.  <span data-ttu-id="37f67-119">使用可用来移动文件的任何操作系统机制或标准方法，将数据库文件夹移到新位置。</span><span class="sxs-lookup"><span data-stu-id="37f67-119">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
5.  <span data-ttu-id="37f67-120">在 SSMS 的左窗格或右窗格中找到 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="37f67-120">Locate the **Databases** folder in the left or right pane of SSMS.</span></span>  
  
6.  <span data-ttu-id="37f67-121">右键单击 "**数据库**" 文件夹，然后选择 "**附加 ...** "</span><span class="sxs-lookup"><span data-stu-id="37f67-121">Right-click on the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="37f67-122">在 **“文件夹”** 文本框中，键入数据库文件夹的新位置。</span><span class="sxs-lookup"><span data-stu-id="37f67-122">In the **folder** text box, type the new location of the database folder.</span></span> <span data-ttu-id="37f67-123">或者，您可以使用 "浏览" 按钮 (**...** ") 查找数据库文件夹。</span><span class="sxs-lookup"><span data-stu-id="37f67-123">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="37f67-124">选择 `ReadWrite` 数据库的模式。</span><span class="sxs-lookup"><span data-stu-id="37f67-124">Select the `ReadWrite` mode for the database.</span></span>  
  
9. <span data-ttu-id="37f67-125">键入步骤 3 中使用的密码，然后单击 **“确定”** 执行附加命令。</span><span class="sxs-lookup"><span data-stu-id="37f67-125">Type the password used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="moving-a-database-programmatically-using-amo"></a><span data-ttu-id="37f67-126">使用 AMO 以编程方式移动数据库</span><span class="sxs-lookup"><span data-stu-id="37f67-126">Moving a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="37f67-127">在 C# 应用程序中，修改以下示例代码并完成所指示的任务。</span><span class="sxs-lookup"><span data-stu-id="37f67-127">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="37f67-128">在 C# 应用程序中，用必要的参数调用 `MoveDb()` 。</span><span class="sxs-lookup"><span data-stu-id="37f67-128">In your C# application, invoke `MoveDb()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="37f67-129">编译和执行您的代码以移动该数据库。</span><span class="sxs-lookup"><span data-stu-id="37f67-129">Compile and execute your code to move the database.</span></span>  
  
#### <a name="moving-a-database-by-script-using-xmla"></a><span data-ttu-id="37f67-130">使用 XMLA 借助于脚本移动数据库</span><span class="sxs-lookup"><span data-stu-id="37f67-130">Moving a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="37f67-131">在 SSMS 中打开一个新的 XMLA 选项卡。</span><span class="sxs-lookup"><span data-stu-id="37f67-131">Open a new XMLA tab in SSMS.</span></span>  
  
2.  <span data-ttu-id="37f67-132">复制下面的 XMLA 脚本模板</span><span class="sxs-lookup"><span data-stu-id="37f67-132">Copy the following script template for XMLA</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="37f67-133">将 `%dbName%` 替换为数据库名称，将 `%password%` 替换为您的密码。</span><span class="sxs-lookup"><span data-stu-id="37f67-133">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="37f67-134">% 字符是模板的一部分，必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="37f67-134">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="37f67-135">执行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="37f67-135">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="37f67-136">使用可用来移动文件的任何操作系统机制或标准方法，将数据库文件夹移到新位置。</span><span class="sxs-lookup"><span data-stu-id="37f67-136">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
4.  <span data-ttu-id="37f67-137">在新的 XMLA 选项卡中复制下面的 XMLA 脚本模板</span><span class="sxs-lookup"><span data-stu-id="37f67-137">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="37f67-138">将 `%dbFolder%` 替换为数据库文件夹的完整 UNC 路径，将 `%ReadOnlyMode%` 替换为相应值（`ReadOnly` 或 `ReadWrite`），并将 `%password%` 替换为您的密码。</span><span class="sxs-lookup"><span data-stu-id="37f67-138">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="37f67-139">% 字符是模板的一部分，必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="37f67-139">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="37f67-140">执行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="37f67-140">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f67-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="37f67-141">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="37f67-142">[Microsoft.analysisservices.sharepoint.integration.dll \*。](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="37f67-142">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="37f67-143">[附加和分离 Analysis Services 数据库](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="37f67-143">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="37f67-144">[数据库存储位置](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="37f67-144">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="37f67-145">[数据库 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="37f67-145">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="37f67-146">[附加元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="37f67-146">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="37f67-147">[分离元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="37f67-147">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="37f67-148">[ReadWriteMode 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="37f67-148">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="37f67-149">DbStorageLocation 元素</span><span class="sxs-lookup"><span data-stu-id="37f67-149">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
