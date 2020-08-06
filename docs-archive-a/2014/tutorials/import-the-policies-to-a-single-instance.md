---
title: 将策略导入到单个实例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0464bc6f4dcd6326a4b8f222cb4b3128f21561ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693148"
---
# <a name="import-the-policies-to-a-single-instance"></a><span data-ttu-id="191ee-102">将策略导入到单个实例</span><span class="sxs-lookup"><span data-stu-id="191ee-102">Import the Policies to a Single Instance</span></span>
  <span data-ttu-id="191ee-103">在此任务中，您将要计划的最佳实践策略导入到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的单个实例上的基于策略的管理中。</span><span class="sxs-lookup"><span data-stu-id="191ee-103">In this task, you will import the best practices policies that you want to schedule into Policy-Based Management on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="191ee-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="191ee-104">Prerequisites</span></span>  
 <span data-ttu-id="191ee-105">您必须在运行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更高版本的服务器上执行此过程。</span><span class="sxs-lookup"><span data-stu-id="191ee-105">You must perform this procedure on a server that is running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span>  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a><span data-ttu-id="191ee-106">为数据库引擎导入最佳实践策略</span><span class="sxs-lookup"><span data-stu-id="191ee-106">Import the best practices policies for the Database Engine</span></span>  
  
1.  <span data-ttu-id="191ee-107">启动 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，然后连接到[!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="191ee-107">Start [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="191ee-108">在对象资源管理器中，展开 "**管理**"，然后展开 "**策略管理**"。</span><span class="sxs-lookup"><span data-stu-id="191ee-108">In Object Explorer, expand **Management**, and then expand **Policy Management**.</span></span>  
  
3.  <span data-ttu-id="191ee-109">右键单击 "**策略**"，然后单击 "**导入策略**"。</span><span class="sxs-lookup"><span data-stu-id="191ee-109">Right-click **Policies**, and then click **Import Policy**.</span></span>  
  
4.  <span data-ttu-id="191ee-110">在 "**导**入" 对话框中，在 "**要导入的文件**" 框旁，单击省略号 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="191ee-110">In the **Import** dialog box, next to the **Files to import** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="191ee-111">在 "**查找范围**" 列表中，浏览到包含最佳实践策略的以下文件夹：</span><span class="sxs-lookup"><span data-stu-id="191ee-111">In the **Look in** list, browse to the following folder, which contains the best practices policies:</span></span>  
  
     <span data-ttu-id="191ee-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="191ee-112">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="191ee-113">文件路径可能各不相同，具体取决于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 程序文件的安装位置、运行的操作系统是 32 位还是 64 位以及语言标识符。</span><span class="sxs-lookup"><span data-stu-id="191ee-113">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
6.  <span data-ttu-id="191ee-114">在 "**选择策略**" 对话框中，选择一个或多个策略文件。</span><span class="sxs-lookup"><span data-stu-id="191ee-114">In the **Select Policy** dialog box, select one or more policy files.</span></span>  
  
     <span data-ttu-id="191ee-115">若要选择多个不相邻的文件，请单击一个文件，按住 Ctrl 键，然后单击各个其他文件。</span><span class="sxs-lookup"><span data-stu-id="191ee-115">To select nonadjacent files, click one file, hold down the CTRL key, and then click each additional file.</span></span> <span data-ttu-id="191ee-116">若要选择多个相邻的文件，请单击序列中的第一个文件，按住 Shift 键，然后单击最后一个文件。</span><span class="sxs-lookup"><span data-stu-id="191ee-116">To select adjacent files, click the first file in the sequence, hold down the SHIFT key, and then click the last file.</span></span>  
  
7.  <span data-ttu-id="191ee-117">选择完文件后，单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="191ee-117">When you are finished selecting files, click **Open**.</span></span>  
  
8.  <span data-ttu-id="191ee-118">在 "**导入**" 对话框中，确保 "**策略状态**" 列表设置为 "在默认) 时**保留策略状态**" (，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="191ee-118">In the **Import** dialog box, make sure that the **Policy state** list is set to **Preserve policy state on import** (the default), and then click **OK**.</span></span>  
  
     <span data-ttu-id="191ee-119">策略将导入到 "**策略管理**" 下的 "**策略**" 节点中。</span><span class="sxs-lookup"><span data-stu-id="191ee-119">The policies are imported into the **Policies** node under **Policy Management**.</span></span> <span data-ttu-id="191ee-120">默认情况下，导入的策略设置为“按需”评估模式。</span><span class="sxs-lookup"><span data-stu-id="191ee-120">By default, the imported policies are set to "On demand" evaluation mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="191ee-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="191ee-121">Next Steps</span></span>  
 [<span data-ttu-id="191ee-122">计划策略</span><span class="sxs-lookup"><span data-stu-id="191ee-122">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
  
