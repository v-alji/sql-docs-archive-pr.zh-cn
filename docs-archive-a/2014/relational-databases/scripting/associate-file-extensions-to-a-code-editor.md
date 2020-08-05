---
title: 将文件扩展名与代码编辑器关联
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e8cfbc89892a99971e985ffd3ff10b99f89fe53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580658"
---
# <a name="associate-file-extensions-to-a-code-editor"></a><span data-ttu-id="3f394-102">将文件扩展名与代码编辑器关联</span><span class="sxs-lookup"><span data-stu-id="3f394-102">Associate File Extensions to a Code Editor</span></span>
  <span data-ttu-id="3f394-103">将文件扩展名与特定代码编辑器相关联使您可以通过在 Windows 资源管理器中双击文件，使用相应的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 代码编辑器打开文件。</span><span class="sxs-lookup"><span data-stu-id="3f394-103">Associating file extensions to a specific code editor allows you to open a file with the appropriate [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] code editor when you double-click a file in Windows Explorer.</span></span> <span data-ttu-id="3f394-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的常用扩展名（例如 .sql 和 .mdx）是在安装过程中关联的。</span><span class="sxs-lookup"><span data-stu-id="3f394-104">The extensions commonly used by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], such as .sql and .mdx, are associated during installation.</span></span> <span data-ttu-id="3f394-105">新的文件扩展名也必须在文件系统中与 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 相关联。</span><span class="sxs-lookup"><span data-stu-id="3f394-105">New file extensions must also be associated to [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the file system.</span></span> <span data-ttu-id="3f394-106">使用此功能可以打开通过其他编辑器创建的文件，也可以打开重命名的文件，例如重命名为 .bak 的 .sql 文件的备份。</span><span class="sxs-lookup"><span data-stu-id="3f394-106">You can use this feature to open files created with other editors, or to open files you have renamed, such as backups of .sql files that were renamed .bak.</span></span>  
  
 <span data-ttu-id="3f394-107">关联过程分为两步。</span><span class="sxs-lookup"><span data-stu-id="3f394-107">There are two steps in the process.</span></span> <span data-ttu-id="3f394-108">首先将扩展名与 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]相关联，然后将扩展名与特定代码编辑器相关联。</span><span class="sxs-lookup"><span data-stu-id="3f394-108">First associate the extension with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then associate the extension with a specific code editor.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a><span data-ttu-id="3f394-109">将新的文件扩展名与 SQL Server Management Studio 相关联</span><span class="sxs-lookup"><span data-stu-id="3f394-109">To associate a new file extension with SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="3f394-110">在 **“开始”** 菜单中，指向 **“所有程序”** ，指向 **“附件”** ，再单击 **“Windows 资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="3f394-111">在 Windows 资源管理器的 **“工具”** 菜单上，单击 **“文件夹选项”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-111">In Windows Explorer, on the **Tools** menu, click **Folder Options**.</span></span>  
  
3.  <span data-ttu-id="3f394-112">在 **“文件夹选项”** 对话框的 **“文件类型”** 选项卡上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-112">In the **Folder Options** dialog box, on the **File Types** tab, click **New**.</span></span>  
  
4.  <span data-ttu-id="3f394-113">在 **“新建扩展名”** 对话框的 **“文件扩展名”** 框中，键入要关联的新文件扩展名，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-113">In the **Create New Extension** dialog box, in the **File Extension** box, type the new file extension that you want to associate, and then click **OK**.</span></span> <span data-ttu-id="3f394-114">扩展名不要以句点开头。</span><span class="sxs-lookup"><span data-stu-id="3f394-114">Do not start the extension with a period.</span></span>  
  
5.  <span data-ttu-id="3f394-115">在 **“已注册的文件类型”** 框，单击新的扩展名，再单击 **“更改”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-115">In the **Registered file** types box, click on your new extension, and then click **Change**.</span></span>  
  
6.  <span data-ttu-id="3f394-116">在“打开方式”对话框中，单击“SSMS - SQL Server Management Studio”，再单击“确定”    。</span><span class="sxs-lookup"><span data-stu-id="3f394-116">In the **Open With** dialog box, click **SSMS - SQL Server Management Studio**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3f394-117">单击 **“关闭”** 关闭 **“文件夹选项”** 对话框，然后关闭 Windows 资源管理器。</span><span class="sxs-lookup"><span data-stu-id="3f394-117">Click **Close** to close the **Folder Options** dialog box, and then close Windows Explorer.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a><span data-ttu-id="3f394-118">在 SQL Server Management Studio 中将新文件扩展名与代码编辑器相关联</span><span class="sxs-lookup"><span data-stu-id="3f394-118">To associate a new file extension with a code editor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="3f394-119">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **“工具”** 菜单中，单击 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-119">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="3f394-120">在 **“选项”** 对话框中，单击 **“文本编辑器”** ，再单击 **“文件扩展名”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-120">In the **Options** dialog box, click **Text Editor**, and then click **File Extension**.</span></span>  
  
3.  <span data-ttu-id="3f394-121">在 **“扩展名”** 框中，键入新的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="3f394-121">In the **Extension** box, type your new file extension.</span></span>  
  
4.  <span data-ttu-id="3f394-122">在 **“编辑器”** 框中，单击要用于打开此文件类型的代码编辑器，单击 **“添加”** ，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3f394-122">In the **Editor** box, click the code editor that you wish to use to open this file type, click **Add**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f394-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f394-123">See Also</span></span>  
 [<span data-ttu-id="3f394-124">Ssms 实用工具</span><span class="sxs-lookup"><span data-stu-id="3f394-124">Ssms Utility</span></span>](../../ssms/ssms-utility.md)  
  
  
