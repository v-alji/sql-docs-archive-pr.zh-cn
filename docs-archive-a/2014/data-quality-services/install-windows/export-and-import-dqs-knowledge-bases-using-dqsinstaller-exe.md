---
title: 使用 DQSInstaller.exe 导出和导入 DQS 知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 64a8feb7bfded742da7563642b07181166fcbeab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691875"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a><span data-ttu-id="5b583-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span><span class="sxs-lookup"><span data-stu-id="5b583-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span></span>
  <span data-ttu-id="5b583-103">对于现有的 DQS 安装，您可以从命令提示符运行 DQSInstaller.exe 文件，以便一次性将 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中的所有知识库导出到 DQS 备份文件 (.dqsb)，并在稍后使用 .dqsb 文件一次性将所有知识库导入其他 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5b583-103">For an existing installation of DQS, you can export all the knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once, and then later use the .dqsb file to import all the knowledge bases to a different [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="5b583-104">有关从命令提示符运行 DQSInstaller.exe 的详细信息，请参阅 [从命令提示符运行 DQSInstaller.exe](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) 中的 [运行 DQSInstaller.exe 以便完成数据质量服务器安装](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="5b583-104">For more information about running DQSInstaller.exe from the command prompt, see [Run DQSInstaller.exe from Command Prompt](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
 <span data-ttu-id="5b583-105">利用此功能，您可以一次性对 *中的* 所有 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 知识库进行备份，而不必使用 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]单独将每个知识库导出到 .dqs 文件。</span><span class="sxs-lookup"><span data-stu-id="5b583-105">This feature enables you to take a backup of *all* your knowledge bases in [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually export each knowledge base to a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="5b583-106">同样，您可以一次性将 *所有* 知识库从备份文件导入其他 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ，而不必使用 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]从 .dqs 文件单独导入每个知识库。</span><span class="sxs-lookup"><span data-stu-id="5b583-106">Similarly, you can import *all* the knowledge bases from the backup file into another [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually import each knowledge base from a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="5b583-107">当在计算机上卸载 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ，然后将其重新安装到其他计算机上时，此功能对于备份和还原知识库特别有用。</span><span class="sxs-lookup"><span data-stu-id="5b583-107">This is particularly useful for backing up and restoring your knowledge bases when you are uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a computer, and then reinstalling it on a different computer.</span></span> <span data-ttu-id="5b583-108">您可以轻松地将现有 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安装中的所有知识库导出到 DQS 备份文件 (.dqsb)，然后再在其他计算机上安装 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 之后从该备份文件导入所有知识库。</span><span class="sxs-lookup"><span data-stu-id="5b583-108">You can easily export all the knowledge bases in an existing installation of [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), and then import all the knowledge bases from the backup file after installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a different computer.</span></span>  
  
##  <a name="exporting-knowledge-bases-to-dqsb-file"></a><a name="export"></a> <span data-ttu-id="5b583-109">将知识库导出到 .dqsb 文件</span><span class="sxs-lookup"><span data-stu-id="5b583-109">Exporting Knowledge Bases to .dqsb File</span></span>  
 <span data-ttu-id="5b583-110">您可以随时导出或在卸载 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 时导出现有 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]中的所有知识库。</span><span class="sxs-lookup"><span data-stu-id="5b583-110">You can export all the knowledge bases in the existing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at any time or while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span>  
  
-   <span data-ttu-id="5b583-111">若要将 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中的所有知识库导出到 DQS 备份文件 (.dqsb)，请通过命令提示符使用 `exportkbs` 参数并使用要将知识库导出到的位置的完整路径和文件名来运行 DQSInstaller.exe。</span><span class="sxs-lookup"><span data-stu-id="5b583-111">To export all the knowledge bases in a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), run DQSInstaller.exe with the `exportkbs` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="5b583-112">例如，将所有知识库导出到 C: 驱动器中的 DQSBackup.dqsb 文件：</span><span class="sxs-lookup"><span data-stu-id="5b583-112">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive:</span></span>  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b583-113">如果提供的文件名在指定位置已存在，则安装程序会提示您是否要覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="5b583-113">If the provided file name already exists at the specified location, the installer prompts you whether to overwrite the file.</span></span>  
  
-   <span data-ttu-id="5b583-114">若要在卸载 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]时将所有知识库导出到 DQS 备份文件，请通过命令提示符使用 `uninstall` 并使用要将知识库导出到的位置的完整路径和文件名来运行 DQSInstaller.exe。</span><span class="sxs-lookup"><span data-stu-id="5b583-114">To export all the knowledge bases to a DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], run DQSInstaller.exe with the `uninstall` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="5b583-115">例如，将所有知识库导出到 C: 驱动器中的 DQSBackup.dqsb 文件，然后卸载 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="5b583-115">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive, and then uninstall [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]:</span></span>  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b583-116">如果在使用 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 参数从命令提示符卸载 `uninstall` 时未指定 DQS 备份文件的完整路径和文件名，则会显示一条声明将删除所有知识库的消息，并允许您选择是否继续执行卸载过程。</span><span class="sxs-lookup"><span data-stu-id="5b583-116">If you do not specify the full path and file name of the DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from the command prompt using the `uninstall` parameter, a message is displayed stating that all the knowledge bases will be deleted, and allows you to choose whether to continue with the uninstall process.</span></span>  
  
##  <a name="importing-knowledge-bases-from-dqsb-file"></a><a name="import"></a> <span data-ttu-id="5b583-117">从 .dqsb 文件导入知识库</span><span class="sxs-lookup"><span data-stu-id="5b583-117">Importing Knowledge Bases from .dqsb File</span></span>  
 <span data-ttu-id="5b583-118">完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安装后，您可以从 DQS 备份文件 (.dqsb) 导入所有知识库。</span><span class="sxs-lookup"><span data-stu-id="5b583-118">You can import all the knowledge bases from a DQS backup file (.dqsb) after completing the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation.</span></span> <span data-ttu-id="5b583-119">若要导入知识库，您必须具有有效的 DQS 备份文件 (.dqsb)。</span><span class="sxs-lookup"><span data-stu-id="5b583-119">To import knowledge bases, you must have a valid DQS backup file (.dqsb).</span></span>  
  
 <span data-ttu-id="5b583-120">通过命令提示符使用 `importkbs` 参数并使用要从中导入知识库的位置的完整路径和文件名来运行 DQSInstaller.exe 文件。</span><span class="sxs-lookup"><span data-stu-id="5b583-120">Run the DQSInstaller.exe file with the `importkbs` parameter from the command prompt, along with the full path and file name from where you want to import the knowledge bases.</span></span> <span data-ttu-id="5b583-121">例如，从 C: 驱动器中的 DQSBackup.dqsb 文件导入所有知识库：</span><span class="sxs-lookup"><span data-stu-id="5b583-121">For example, to import all the knowledge bases from the DQSBackup.dqsb file in the C: drive:</span></span>  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 <span data-ttu-id="5b583-122">如果 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中存在使用要导入的知识库的名称的知识库，则导入的知识库名称将追加一条下划线 (_)，后跟从 1 开始的整数值。</span><span class="sxs-lookup"><span data-stu-id="5b583-122">If there are existing knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] with the same name as the ones you are importing, the names of the imported knowledge bases will be appended with an underscore (_) followed by an integer value starting with 1.</span></span> <span data-ttu-id="5b583-123">例如，如果“CompanyName”域重复，则导入的域名称将为“CompanyName_1”。</span><span class="sxs-lookup"><span data-stu-id="5b583-123">For example, if the "CompanyName" domain is duplicate, the imported domain name will be "CompanyName_1."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b583-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b583-124">See Also</span></span>  
 <span data-ttu-id="5b583-125">[运行 DQSInstaller.exe 以完成数据质量服务器安装](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="5b583-125">[Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span></span>  
 <span data-ttu-id="5b583-126">[安装 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="5b583-126">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 <span data-ttu-id="5b583-127">[将知识库导出到 dqs 文件](../export-a-knowledge-base-to-a-dqs-file.md) </span><span class="sxs-lookup"><span data-stu-id="5b583-127">[Export a Knowledge Base to a .dqs File](../export-a-knowledge-base-to-a-dqs-file.md) </span></span>  
 [<span data-ttu-id="5b583-128">从 .dqs 文件导入知识库</span><span class="sxs-lookup"><span data-stu-id="5b583-128">Import a Knowledge Base from a .dqs File</span></span>](../import-a-knowledge-base-from-a-dqs-file.md)  
  
  
