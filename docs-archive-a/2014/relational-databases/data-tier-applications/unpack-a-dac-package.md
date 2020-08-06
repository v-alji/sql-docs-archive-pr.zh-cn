---
title: 解压缩 DAC 包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- wizard [DAC], unpack
- data-tier application [SQL Server], unpack
- How to [DAC], unpack
- unpack DAC
ms.assetid: 697b69b3-f157-4e22-ac4e-f65c5fc2d0ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ba0930f79a47696a6c9a9c1bfe028316601f64b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591376"
---
# <a name="unpack-a-dac-package"></a><span data-ttu-id="23a7e-102">解压缩 DAC 包</span><span class="sxs-lookup"><span data-stu-id="23a7e-102">Unpack a DAC Package</span></span>
  <span data-ttu-id="23a7e-103">使用“解压缩数据层应用程序”对话框可以从数据层应用程序 (DAC) 包解压缩脚本和文件。</span><span class="sxs-lookup"><span data-stu-id="23a7e-103">Use the Unpack Data-tier Application dialog box to unzip the scripts and files from a data-tier application (DAC) package.</span></span> <span data-ttu-id="23a7e-104">这些脚本和文件放置在一个文件夹中，您可以在使用该 DAC 包将 DAC 部署到生产系统中之前查看该文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-104">The scripts and files are placed in a folder where they can be reviewed before the package is used to deploy the DAC into a production system.</span></span> <span data-ttu-id="23a7e-105">一个 DAC 的内容也可与解压缩到其他文件夹中的其他包的内容进行比较。</span><span class="sxs-lookup"><span data-stu-id="23a7e-105">The contents of one DAC can also be compared with the contents of another package unpacked to another folder.</span></span>  
  
1.  <span data-ttu-id="23a7e-106">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="23a7e-106">**Before you begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="23a7e-107">**若要解压缩 DAC，请使用：** [“解压缩数据层应用程序”对话框](#UnpackDACDial)、[检查 DAC 包的内容](#ExamDACPack)</span><span class="sxs-lookup"><span data-stu-id="23a7e-107">**To unpack a DAC, using:**  [Unpack Data-tier Application Dialog](#UnpackDACDial), [Examine the Contents of a DAC Package](#ExamDACPack)</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="23a7e-108">Security</span><span class="sxs-lookup"><span data-stu-id="23a7e-108">Security</span></span>  
 <span data-ttu-id="23a7e-109">建议您不要从未知或不可信源部署 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="23a7e-109">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="23a7e-110">此类 DAC 可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构导致错误。</span><span class="sxs-lookup"><span data-stu-id="23a7e-110">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="23a7e-111">在使用来自未知或不可信源的 DAC 之前，请将其部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的一个独立的测试实例中，解压缩该 DAC 并检查代码，例如存储过程或者其他用户定义的代码。</span><span class="sxs-lookup"><span data-stu-id="23a7e-111">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
##  <a name="unpack-data-tier-application-dialog"></a><a name="UnpackDACDial"></a> <span data-ttu-id="23a7e-112">“解压缩数据层应用程序”对话框</span><span class="sxs-lookup"><span data-stu-id="23a7e-112">Unpack Data-tier Application Dialog</span></span>  
 <span data-ttu-id="23a7e-113">**解压缩 DAC 包文件**</span><span class="sxs-lookup"><span data-stu-id="23a7e-113">**To Unpack a DAC Package File**</span></span>  
  
-   <span data-ttu-id="23a7e-114">在 **Windows 资源管理器**中，导航到 DAC 包 (.dacpac) 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="23a7e-114">In **Windows Explorer**, navigate to the location of a DAC package (.dacpac) file.</span></span>  
  
-   <span data-ttu-id="23a7e-115">使用以下两种方法之一可打开“解压缩数据层应用程序”对话框：</span><span class="sxs-lookup"><span data-stu-id="23a7e-115">Use one of these two methods to open the Unpack Data-tier Application dialog:</span></span>  
  
    1.  <span data-ttu-id="23a7e-116">右键单击该 DAC 包 (.dacpac) 文件，然后选择“解压缩”  。</span><span class="sxs-lookup"><span data-stu-id="23a7e-116">Right-click the DAC package (.dacpac) file and select **Unpack**.</span></span>  
  
    2.  <span data-ttu-id="23a7e-117">双击该 DAC 包文件。</span><span class="sxs-lookup"><span data-stu-id="23a7e-117">Double-click the DAC package file.</span></span>  
  
-   <span data-ttu-id="23a7e-118">完成对话框：</span><span class="sxs-lookup"><span data-stu-id="23a7e-118">Complete the dialogs:</span></span>  
  
    -   [<span data-ttu-id="23a7e-119">解压缩 Microsoft SQL Server DAC 包文件</span><span class="sxs-lookup"><span data-stu-id="23a7e-119">Unpack Microsoft SQL Server DAC Package File</span></span>](#Unpack)  
  
    -   [<span data-ttu-id="23a7e-120">查找文件夹</span><span class="sxs-lookup"><span data-stu-id="23a7e-120">Browse for Folder</span></span>](#Browse)  
  
###  <a name="unpack-microsoft-sql-server-dac-package-file"></a><a name="Unpack"></a> <span data-ttu-id="23a7e-121">解压缩 Microsoft SQL Server DAC 包文件</span><span class="sxs-lookup"><span data-stu-id="23a7e-121">Unpack Microsoft SQL Server DAC Package File</span></span>  
 <span data-ttu-id="23a7e-122">使用此页可指定用来放置解压缩文件的目标文件夹，然后运行解压缩操作。</span><span class="sxs-lookup"><span data-stu-id="23a7e-122">Use this page to specify the destination folder in which to place the unpacked files, and then run the unpack operation.</span></span>  
  
 <span data-ttu-id="23a7e-123">**文件将解压缩到此文件夹：** - 指定解压缩文件所在文件夹的完整路径。</span><span class="sxs-lookup"><span data-stu-id="23a7e-123">**Files will be unpacked to this folder:** - Specify the full path to the folder for the unpacked files.</span></span> <span data-ttu-id="23a7e-124">如果该文件夹存在并且您知道完整路径，请在框中键入该路径。</span><span class="sxs-lookup"><span data-stu-id="23a7e-124">If the folder exists and you know the full path, type the path in the box.</span></span> <span data-ttu-id="23a7e-125">如果该文件夹不存在或者您不知道完整路径，请单击 **“浏览”** 以导航到某一文件夹或者创建一个新文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-125">If not, click the **Browse** button to navigate to a folder or create a new folder.</span></span>  
  
 <span data-ttu-id="23a7e-126">**浏览** - 打开“浏览文件夹”  页，从中可以通过导航文件层次结构选择一个文件夹，或者创建一个新文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-126">**Browse** - Opens the **Browse for Folder** page where you can choose a folder by navigating the file hierarchy, or create a new folder.</span></span>  
  
 <span data-ttu-id="23a7e-127">**解压缩** - 启动解压缩操作。</span><span class="sxs-lookup"><span data-stu-id="23a7e-127">**Unpack** - Starts the unpack operation.</span></span>  
  
 <span data-ttu-id="23a7e-128">**取消** - 终止该对话框且不解压缩 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="23a7e-128">**Cancel** - Terminates the dialog box without unpacking the DAC package.</span></span>  
  
###  <a name="browse-for-folder"></a><a name="Browse"></a> <span data-ttu-id="23a7e-129">查找文件夹</span><span class="sxs-lookup"><span data-stu-id="23a7e-129">Browse for Folder</span></span>  
 <span data-ttu-id="23a7e-130">使用此页可选择解压缩操作的目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-130">Use this page to choose the destination folder for the unpack operation.</span></span> <span data-ttu-id="23a7e-131">或者，也可以创建一个新文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-131">Optionally, you can also create a new folder.</span></span>  
  
 <span data-ttu-id="23a7e-132">**文件夹列表** - 显示计算机的文件层次结构。</span><span class="sxs-lookup"><span data-stu-id="23a7e-132">**Folder list** - Displays the file hierarchy for your computer.</span></span> <span data-ttu-id="23a7e-133">展开节点以导航到要将 DAC 包解压缩到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-133">Expand the nodes to navigate to the folder in which to unpack the DAC package.</span></span> <span data-ttu-id="23a7e-134">单击该文件夹，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="23a7e-134">Click on the folder and then click **OK**.</span></span>  
  
 <span data-ttu-id="23a7e-135">**新建文件夹** - 打开一个对话框，从中可以指定要在文件夹层次结构中当前选择的文件夹中创建的新文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="23a7e-135">**Make New Folder** - Opens a dialog in which you can specify the name for a new folder to be created in the folder you have currently selected in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="23a7e-136">**确定** - 放置你在“解压缩 DAC 包文件”  页的“文件将解包到此文件夹”  框中选择的文件夹的路径，并且返回到该页。</span><span class="sxs-lookup"><span data-stu-id="23a7e-136">**OK** - Places the path to the folder you selected in the **Files will be unpacked to this folder** box of the **Unpack DAC Package File** page and returns you to that page.</span></span>  
  
 <span data-ttu-id="23a7e-137">**取消** - 终止该对话框且未选择文件夹。</span><span class="sxs-lookup"><span data-stu-id="23a7e-137">**Cancel** - Terminates the dialog box without selecting a folder.</span></span>  
  
##  <a name="examine-the-contents-of-a-dac-package"></a><a name="ExamDACPack"></a> <span data-ttu-id="23a7e-138">检查 DAC 包的内容</span><span class="sxs-lookup"><span data-stu-id="23a7e-138">Examine the Contents of a DAC Package</span></span>  
 <span data-ttu-id="23a7e-139">对包解压缩后，可以检查由“解压缩数据层应用程序”  对话框生成的文件。</span><span class="sxs-lookup"><span data-stu-id="23a7e-139">After unpacking the package, you can examine the files produced by the **Unpack Data-tier Application** dialog.</span></span> <span data-ttu-id="23a7e-140">该对话框在所选目标文件夹中生成以下文件：</span><span class="sxs-lookup"><span data-stu-id="23a7e-140">The dialog box builds the following files in the selected destination folder:</span></span>  
  
1.  <span data-ttu-id="23a7e-141">一个 Transact-SQL 脚本，包含用于创建在该 DAC 中定义的对象的语句。</span><span class="sxs-lookup"><span data-stu-id="23a7e-141">A Transact-SQL script that contains the statements for creating the objects defined in the DAC.</span></span> <span data-ttu-id="23a7e-142">该文件名是 *DACName*.sql，其中， *DACName* 是 DAC 的名称。</span><span class="sxs-lookup"><span data-stu-id="23a7e-142">The file name is *DACName*.sql, where *DACName* is the name of the DAC.</span></span>  
  
2.  <span data-ttu-id="23a7e-143">包中的所有 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="23a7e-143">All XML files from the package.</span></span>  
  
3.  <span data-ttu-id="23a7e-144">来自 DAC 的“附加文件”部分的所有文件，例如 DAC 预部署文件或部署后文件。</span><span class="sxs-lookup"><span data-stu-id="23a7e-144">All files from the Extra Files section of the DAC, such as the DAC pre-deployment or post-deployment files.</span></span>  
  
 <span data-ttu-id="23a7e-145">有关详细信息，请参阅 [Validate a DAC Package](validate-a-dac-package.md)。</span><span class="sxs-lookup"><span data-stu-id="23a7e-145">For more information, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a7e-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23a7e-146">See Also</span></span>  
 <span data-ttu-id="23a7e-147">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="23a7e-147">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="23a7e-148">[部署数据层应用程序](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="23a7e-148">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="23a7e-149">升级数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="23a7e-149">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
  
  
