---
title: 访问 DQS 操作数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 515b087a8d16e44314d1a21d3dfbd6f13c767f5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690174"
---
# <a name="access-data-for-the-dqs-operations"></a><span data-ttu-id="6d21b-102">访问 DQS 操作数据</span><span class="sxs-lookup"><span data-stu-id="6d21b-102">Access Data for the DQS Operations</span></span>
  <span data-ttu-id="6d21b-103">若要将您的源数据用于 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 操作并导出已处理的数据，您可以执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="6d21b-103">To use your source data for [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) operations, and export your processed data, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="6d21b-104">将您的源数据复制到 DQS_STAGING_DATA 数据库中的某个表/视图，然后再将其用于 DQS 操作。</span><span class="sxs-lookup"><span data-stu-id="6d21b-104">Copy your source data to a table/view in the DQS_STAGING_DATA database, and then use it for DQS operations.</span></span> <span data-ttu-id="6d21b-105">还可以将已处理的数据导出到 DQS_STAGING_DATA 数据库的新表中。</span><span class="sxs-lookup"><span data-stu-id="6d21b-105">You can also export the processed data to a new table in the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="6d21b-106">为此，必须向您的 Windows 用户帐户授予对 DQS_STAGING_DATA 数据库的读/写访问权限。</span><span class="sxs-lookup"><span data-stu-id="6d21b-106">To do so, your Windows user account must be granted read/write access to the DQS_STAGING_DATA database.</span></span>  
  
-   <span data-ttu-id="6d21b-107">使用您自己的数据库作为 DQS 操作的源数据，以及导出已处理的数据的目标。</span><span class="sxs-lookup"><span data-stu-id="6d21b-107">Use your own database as the source data for the DQS operations, and destination for exporting the processed data.</span></span> <span data-ttu-id="6d21b-108">为此，请确保你的数据库与数据质量服务器数据库在同一个 SQL Server 实例中。</span><span class="sxs-lookup"><span data-stu-id="6d21b-108">To do so, ensure that your database is in the same SQL Server instance as the Data Quality Server databases.</span></span> <span data-ttu-id="6d21b-109">否则，该数据库将无法在数据质量客户端中用于 DQS 操作。</span><span class="sxs-lookup"><span data-stu-id="6d21b-109">Otherwise, the database will not be available in the Data Quality Client for DQS operations.</span></span> <span data-ttu-id="6d21b-110">此外，为导出匹配结果，必须向你的 Windows 用户帐户授予对 DQS_STAGING_DATA 数据库的访问权限，因为匹配结果分为两个阶段进行导出：首先，匹配结果导出到 DQS_STAGING_DATA 数据库的临时表中，然后移到你的目标数据库的表中。</span><span class="sxs-lookup"><span data-stu-id="6d21b-110">Also, your Windows user account must be granted access on the DQS_STAGING_DATA database for exporting the matching results because matching results are exported in two phases: first, the matching results are exported to the temporary tables in the DQS_STAGING_DATA database, and then moved to the table in your destination database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d21b-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="6d21b-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="6d21b-112">您必须已通过运行 DQSInstaller.exe 文件完成了 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="6d21b-112">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="6d21b-113">有关详细信息，请参阅 [运行 DQSInstaller.exe 以便完成数据质量服务器安装](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="6d21b-113">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="6d21b-114">为授予/修改对数据库上 SQL 登录名的访问权限，您的 Windows 用户帐户必须是数据库引擎实例中相应固定服务器角色（例如 securityadmin、serveradmin 或 sysadmin）的成员。</span><span class="sxs-lookup"><span data-stu-id="6d21b-114">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) in the database engine instance to grant/modify access to SQL login on databases.</span></span>  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a><span data-ttu-id="6d21b-115">向用户授予对 DQS_STAGING_DATA 数据库的读/写访问权限</span><span class="sxs-lookup"><span data-stu-id="6d21b-115">To grant read/write access to a User on the DQS_STAGING_DATA Database</span></span>  
  
1.  <span data-ttu-id="6d21b-116">启动 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="6d21b-116">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="6d21b-117">在 Microsoft SQL Server Management Studio 中，依次展开您的 SQL Server 实例、 **“安全性”** 和 **“登录名”**。</span><span class="sxs-lookup"><span data-stu-id="6d21b-117">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="6d21b-118">右键单击某一 SQL 登录名，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="6d21b-118">Right-click a SQL login, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="6d21b-119">在 **“登录属性”** 对话框的左侧窗格中，单击 **“用户映射”** 页。</span><span class="sxs-lookup"><span data-stu-id="6d21b-119">In the **Login Properties** dialog box, click the **User Mapping** page in the left pane.</span></span>  
  
5.  <span data-ttu-id="6d21b-120">在右侧窗格中，选中 **DQS_STAGING_DATA** 数据库的 **“映射”** 列下的复选框，然后在 **“数据库角色成员身份: DQS_STAGING_DATA”** 窗格中选择以下角色：</span><span class="sxs-lookup"><span data-stu-id="6d21b-120">In the right pane, select the check box under the **Map** column for the **DQS_STAGING_DATA** database, and then select the following roles in the **Database role membership for: DQS_STAGING_DATA** pane:</span></span>  
  
    -   <span data-ttu-id="6d21b-121">**db_datareader**：从表/视图中读取数据。</span><span class="sxs-lookup"><span data-stu-id="6d21b-121">**db_datareader**: Read data from tables/views.</span></span>  
  
    -   <span data-ttu-id="6d21b-122">**db_datawriter**：在表中添加、删除或更改数据。</span><span class="sxs-lookup"><span data-stu-id="6d21b-122">**db_datawriter**: Add, delete, or change data in tables.</span></span>  
  
    -   <span data-ttu-id="6d21b-123">**db_ddladmin**：创建、修改或删除表/视图。</span><span class="sxs-lookup"><span data-stu-id="6d21b-123">**db_ddladmin**: Create, modify, or delete tables/views.</span></span>  
  
6.  <span data-ttu-id="6d21b-124">在 **“登录属性”** 对话框中，单击 **“确定”** 以应用所做的更改。</span><span class="sxs-lookup"><span data-stu-id="6d21b-124">In the **Login Properties** dialog box, click **OK** to apply the changes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6d21b-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6d21b-125">Next Steps</span></span>  
 <span data-ttu-id="6d21b-126">尝试执行 DQS 操作，这些操作访问数据库来作为 DQS 操作的数据源，然后将处理后的数据导出到数据库。</span><span class="sxs-lookup"><span data-stu-id="6d21b-126">Try performing DQS operations that accesses the database as data source for DQS operation, and then exports the processed data to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d21b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d21b-127">See Also</span></span>  
 [<span data-ttu-id="6d21b-128">安装 Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="6d21b-128">Install Data Quality Services</span></span>](install-data-quality-services.md)  
  
  
