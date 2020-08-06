---
title: 导出已注册的服务器信息
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportregisteredservers.f1
helpviewer_keywords:
- Registered Servers [SQL Server], exporting
- exporting registered server information
- transferring registered server information
ms.assetid: b65e168f-b6bf-489c-b8ad-3b8644acf0b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03092de2d722e8f8b807dbb3d23c4b4e2b91f6f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692079"
---
# <a name="export-registered-server-information-sql-server-management-studio"></a><span data-ttu-id="190f5-102">导出已注册服务器信息 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="190f5-102">Export Registered Server Information (SQL Server Management Studio)</span></span>
  <span data-ttu-id="190f5-103">本主题说明如何保存和导出 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的已注册服务器信息并将其分发到其他雇员或服务器。</span><span class="sxs-lookup"><span data-stu-id="190f5-103">This topic describes how to save and export registered server information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]and distribute it to other employees or servers.</span></span> <span data-ttu-id="190f5-104">您可以使用此导出功能在多台计算机上显示一致的用户界面。</span><span class="sxs-lookup"><span data-stu-id="190f5-104">You can use this export feature to present a consistent user interface on multiple computers.</span></span>  
  
 <span data-ttu-id="190f5-105">通过导出再导入已注册服务器的相关文件，可以便捷地为多台计算机配置与“已注册的服务器”中相同服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="190f5-105">Exporting and then importing Registered Server files lets you easily configure several computers with the same servers in Registered Servers.</span></span> <span data-ttu-id="190f5-106">当从不同位置的计算机管理大量服务器，或希望为不熟练的用户配置基本的连接设置时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="190f5-106">This is useful when managing a large number of servers from computers in several locations, or when you want to configure a less experienced user with basic connection settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="190f5-107">使用 SQL Server 身份验证的服务器注册按用户来存储密码。</span><span class="sxs-lookup"><span data-stu-id="190f5-107">Server registrations that use SQL Server Authentication store passwords on a per-user basis.</span></span> <span data-ttu-id="190f5-108">在导出并导入服务器注册信息后，用户在首次连接时必须输入每台服务器的密码，以便将密码存储在该用户的已注册服务器列表中。</span><span class="sxs-lookup"><span data-stu-id="190f5-108">After exporting and importing the server registrations, users must enter the password for each server the first time they connect, storing the passwords in their lists of registered servers.</span></span> <span data-ttu-id="190f5-109">对于使用 Windows 身份验证进行注册的服务器，则不需要如此操作。</span><span class="sxs-lookup"><span data-stu-id="190f5-109">This is not necessary for servers registered using Windows Authentication.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-export-registered-server-information"></a><span data-ttu-id="190f5-110">导出已注册服务器信息</span><span class="sxs-lookup"><span data-stu-id="190f5-110">To export registered server information</span></span>  
  
1.  <span data-ttu-id="190f5-111">在已注册的服务器上，右键单击服务器组，再单击“导出”  。</span><span class="sxs-lookup"><span data-stu-id="190f5-111">In Registered Servers, right-click a server group, and then click **Export**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="190f5-112">您可以导出单个服务器、所有已注册服务器树或已注册服务器树的子集。</span><span class="sxs-lookup"><span data-stu-id="190f5-112">You can export an individual server, all of the registered server tree, or a subset of the registered server tree.</span></span>  
  
2.  <span data-ttu-id="190f5-113">在 **“导出已注册的服务器”** 对话框中，进行以下选择：</span><span class="sxs-lookup"><span data-stu-id="190f5-113">In the **Export Registered Servers** dialog box, make the following selections.</span></span>  
  
     <span data-ttu-id="190f5-114">**服务器组**</span><span class="sxs-lookup"><span data-stu-id="190f5-114">**Server group**</span></span>  
     <span data-ttu-id="190f5-115">指定要导出的服务器组。</span><span class="sxs-lookup"><span data-stu-id="190f5-115">Specify the server group which will be exported.</span></span> <span data-ttu-id="190f5-116">将所有已注册的服务器、特定服务器组中已注册的服务器或单个已注册的服务器导出到导出文件中。</span><span class="sxs-lookup"><span data-stu-id="190f5-116">Export all registered servers, registered servers in a particular server group, or a single registered server to the export file.</span></span> <span data-ttu-id="190f5-117">导出功能是递归的；例如，如果服务器组 A 包含服务器组 B，而服务器组 B 包含服务器组 C 和 D，则导出服务器组 A 会导出 A、B、C 和 D 中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="190f5-117">The export functionality is recursive; for example, if server group A contains server group B, and server group B contains server groups C and D, exporting server group A exports all entries in A, B, C, and D.</span></span>  
  
     <span data-ttu-id="190f5-118">服务器组仅显示当前已注册服务器树的服务器组。</span><span class="sxs-lookup"><span data-stu-id="190f5-118">The server group displays only the server groups of the current registered server tree.</span></span>  
  
     <span data-ttu-id="190f5-119">**导出文件**</span><span class="sxs-lookup"><span data-stu-id="190f5-119">**Export file**</span></span>  
     <span data-ttu-id="190f5-120">在文本框中键入导出文件的名称，或使用“浏览”按钮 ( **...** ) 定位到客户端计算机上的导出文件。</span><span class="sxs-lookup"><span data-stu-id="190f5-120">Type the name of the export file in the text box or use the Browse button (**...**) to locate an export file on the client computer.</span></span> <span data-ttu-id="190f5-121">如果选择现有文件，则已注册服务器的信息将追加到文件末尾。</span><span class="sxs-lookup"><span data-stu-id="190f5-121">If you select an existing file, the registered server information is appended to the file.</span></span> <span data-ttu-id="190f5-122">并使用 .regsrvr 扩展名。</span><span class="sxs-lookup"><span data-stu-id="190f5-122">Use the .regsrvr extension.</span></span> <span data-ttu-id="190f5-123">如果希望其他用户或另一台计算机也可以使用已注册服务器信息，可以将文件保存在网络中。</span><span class="sxs-lookup"><span data-stu-id="190f5-123">If you want your registered server information to be available to other users or another computer, you can save the file on the network.</span></span> <span data-ttu-id="190f5-124">其他用户就可以访问该文件并导入部分或全部已注册服务器信息。</span><span class="sxs-lookup"><span data-stu-id="190f5-124">Other users can access the file and import part or all of the registered server information.</span></span> <span data-ttu-id="190f5-125">如果选择现有文件作为导出文件，该文件的内容将被服务器注册信息覆盖。</span><span class="sxs-lookup"><span data-stu-id="190f5-125">If you select an existing file as your export file, the contents of the file are overwritten with the server registration information.</span></span>  
  
     <span data-ttu-id="190f5-126">**不在导出文件中包括用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="190f5-126">**Do not include user names and passwords in the export file**</span></span>  
     <span data-ttu-id="190f5-127">在导出文件时不包括用户名。</span><span class="sxs-lookup"><span data-stu-id="190f5-127">Exclude user names when exporting the file.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="190f5-128">尽管导出文件已加密，但是，如果该文件中包括用户名和 SQL Server 身份验证密码，则应当仔细控制对该文件的访问。</span><span class="sxs-lookup"><span data-stu-id="190f5-128">Although the export files are encrypted, if user names and SQL Server Authentication passwords are included in the file, access to the file should be carefully controlled.</span></span> <span data-ttu-id="190f5-129">因此，默认情况下，不在导出文件中包括用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="190f5-129">User names and passwords are therefore excluded from the export file by default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190f5-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="190f5-130">See Also</span></span>  
 <span data-ttu-id="190f5-131">[导入已注册的服务器信息 &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [创建新的已注册服务器 &#40;SQL Server Management Studio](create-a-new-registered-server-sql-server-management-studio.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="190f5-131">[Import Registered Server Information &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md) [Create a New Registered Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)</span></span>  
  
  
