---
title: 导入已注册的服务器信息
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.importregisteredservers.f1
helpviewer_keywords:
- transferring registered server information
- Registered Servers [SQL Server], importing
- importing registered server information
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f2eddb3b83f73253e977316767f2b930bc8ab9ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692080"
---
# <a name="import-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="8ed8e-102">导入已注册服务器信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8ed8e-102">Import Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8ed8e-103">本主题说明如何导入 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中保存的已注册服务器信息。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-103">This topic describes how to import saved registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8ed8e-104">通过导出再导入已注册服务器的相关文件，可以便捷地为多台计算机配置与“已注册的服务器”中相同服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-104">Exporting and then importing registered server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="8ed8e-105">当从不同位置的计算机管理大量服务器，或希望为不熟练的用户配置基本的连接设置时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-105">This is useful when managing a large number of servers from computers in several locations, or when you want to configure basic connection settings for a less-experienced user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ed8e-106">您不能从早期版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中将已注册服务器信息导入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-106">You cannot import registered server information into [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-import-registered-server-information"></a><span data-ttu-id="8ed8e-107">导入已注册的服务器信息</span><span class="sxs-lookup"><span data-stu-id="8ed8e-107">To import registered server information</span></span>  
  
1.  <span data-ttu-id="8ed8e-108">在已注册的服务器中，单击“已注册的服务器”工具栏上的服务器类型。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-108">In Registered Servers, click the server type on the Registered Servers toolbar.</span></span> <span data-ttu-id="8ed8e-109">服务器类型必须与已注册的服务器的导出文件类型一样。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-109">The server type must be the same as the registered server export file type.</span></span> <span data-ttu-id="8ed8e-110">例如，如果您已经导出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已注册服务器信息，则必须在“已注册的服务器”工具栏上单击 **“SQL Server”** 。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-110">For example, if you have exported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registered server information, you must click **SQL Server** on the Registered Servers toolbar.</span></span>  
  
2.  <span data-ttu-id="8ed8e-111">右键单击服务器组，再选择“导入”  。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-111">Right-click a server group, and select **Import**.</span></span>  
  
3.  <span data-ttu-id="8ed8e-112">在 **“导入已注册的服务器”** 对话框中，选择要导入的已注册的服务器文件，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-112">In the **Import Registered Servers** dialog box, select the registered servers file to import, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8ed8e-113">**导入文件**</span><span class="sxs-lookup"><span data-stu-id="8ed8e-113">**Import file**</span></span>  
     <span data-ttu-id="8ed8e-114">在文本框中键入导入文件的名称，或单击“浏览”按钮 ( **...** ) 定位到客户端计算机上的导入文件。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-114">Type the name of the import file in the text box, or click the Browse button (**...**) to locate the import file on the client computer.</span></span> <span data-ttu-id="8ed8e-115">如果选择现有文件，则已注册服务器的信息将追加到文件末尾。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-115">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="8ed8e-116">导入文件只能是以前导出的已注册服务器的文件。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-116">The import file can only be a previously exported registered server file.</span></span> <span data-ttu-id="8ed8e-117">已注册服务器的文件的扩展名为 .regsrvr。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-117">Registered server files have a .regsrvr extension.</span></span>  
  
     <span data-ttu-id="8ed8e-118">**选择要导入到的服务器组**</span><span class="sxs-lookup"><span data-stu-id="8ed8e-118">**Select the server group to import to**</span></span>  
     <span data-ttu-id="8ed8e-119">选择要将文件中的已注册的服务器条目导入到的根节点或特定服务器组。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-119">Select the root node or a particular server group to which the registered server entries in the file will be imported.</span></span> <span data-ttu-id="8ed8e-120">您可以将所有已注册的服务器、特定服务器组中已注册的服务器或单个已注册的服务器导入到导出文件中。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-120">You can import all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="8ed8e-121">导入功能是递归的；例如，如果服务器组 A 包含服务器组 B，而服务器组 B 包含服务器组 C 和 D，则导入服务器组 A 会导出 A、B、C 和 D 中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-121">The import functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, importing server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="8ed8e-122">服务器组仅显示当前已注册服务器树的服务器组。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-122">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="8ed8e-123">如果选择导入某个现有服务器组或服务器，则会显示一条消息，以便您确认是否要覆盖现有服务器或服务器组。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-123">If you select to import an existing server group or server, a message confirms that you want to overwrite the existing server or server group.</span></span>  
  
 <span data-ttu-id="8ed8e-124">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证的服务器注册按用户来存储密码。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-124">Server registrations that use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="8ed8e-125">在导入服务器注册信息后，用户在首次连接时必须输入每台服务器的密码，以便将密码存储在该用户的已注册服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-125">After importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="8ed8e-126">对于通过 Windows 身份验证进行注册的服务器，则不需要如此操作。</span><span class="sxs-lookup"><span data-stu-id="8ed8e-126">This is not necessary for servers registered through Windows Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed8e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ed8e-127">See Also</span></span>  
 <span data-ttu-id="8ed8e-128">[更改服务器的注册 &#40;SQL Server Management Studio&#41;将](change-a-server-s-registration-sql-server-management-studio.md)[注册的服务器信息导出 &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8ed8e-128">[Change a Server's Registration &#40;SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) [Export Registered Server Information &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="8ed8e-129">创建新的已注册的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8ed8e-129">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)  
  
  
