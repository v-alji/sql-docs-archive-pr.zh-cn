---
title: 创建和管理远程分区 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bd44775a579cc8f770f088594653bb65000407f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577010"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a><span data-ttu-id="530bd-102">创建和管理远程分区 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="530bd-102">Create and Manage a Remote Partition (Analysis Services)</span></span>
  <span data-ttu-id="530bd-103">对度量值组进行分区时，可将远程 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上的辅助数据库配置为分区存储。</span><span class="sxs-lookup"><span data-stu-id="530bd-103">When partitioning a measure group, you can configure a secondary database on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance as partition storage.</span></span>  
  
 <span data-ttu-id="530bd-104">多维数据集（称作主数据库）的远程分区存储于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的远程实例上的专用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库（称作辅助数据库）中。</span><span class="sxs-lookup"><span data-stu-id="530bd-104">Remote partitions for a cube (called the master database) are stored in a dedicated [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (called the secondary database).</span></span>  
  
 <span data-ttu-id="530bd-105">专用辅助数据库可存储一个（且仅一个）主数据库的远程分区，但主数据库可使用多个辅助数据库，条件是所有辅助数据库都在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的同一个远程实例上。</span><span class="sxs-lookup"><span data-stu-id="530bd-105">A dedicated secondary database can store remote partitions for one and only one master database, but the master database can use multiple secondary databases, as long as all the secondary databases are on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="530bd-106">数据库中专用于远程分区的维度作为链接维度创建。</span><span class="sxs-lookup"><span data-stu-id="530bd-106">Dimensions in a database dedicated to remote partitions are created as linked dimensions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="530bd-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="530bd-107">Prerequisites</span></span>  
 <span data-ttu-id="530bd-108">在创建远程分区之前，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="530bd-108">Before you create a remote partition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="530bd-109">您必须有第二个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例和专用数据库才能存储分区。</span><span class="sxs-lookup"><span data-stu-id="530bd-109">You must have a second [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and dedicated database to store the partitions.</span></span> <span data-ttu-id="530bd-110">辅助数据库只有一个用途：它提供主数据库的远程分区存储。</span><span class="sxs-lookup"><span data-stu-id="530bd-110">The secondary database is single-purpose; it provides storage of remote partitions for a master database.</span></span>  
  
-   <span data-ttu-id="530bd-111">两个服务器实例必须是相同版本。</span><span class="sxs-lookup"><span data-stu-id="530bd-111">Both server instances must be the same version.</span></span> <span data-ttu-id="530bd-112">两个数据库应该具有相同功能级别。</span><span class="sxs-lookup"><span data-stu-id="530bd-112">Both databases should be the same functional level.</span></span>  
  
-   <span data-ttu-id="530bd-113">两个实例都必须配置为进行 TCP 连接。</span><span class="sxs-lookup"><span data-stu-id="530bd-113">Both instances must be configured for TCP connections.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="530bd-114">不支持通过使用 HTTP 协议创建远程分区。</span><span class="sxs-lookup"><span data-stu-id="530bd-114">does not support creation of remote partitions by using the HTTP protocol.</span></span>  
  
-   <span data-ttu-id="530bd-115">两个计算机上的防火墙设置都必须设置为接受外部连接。</span><span class="sxs-lookup"><span data-stu-id="530bd-115">Firewall settings on both computers must be set to accept outside connections.</span></span> <span data-ttu-id="530bd-116">有关设置防火墙的详细信息，请参阅 [将 Windows 防火墙配置为允许 Analysis Services 访问](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="530bd-116">For information about setting the firewall, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="530bd-117">运行主数据库的实例的服务帐户必须具有对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的远程实例的管理访问权限。</span><span class="sxs-lookup"><span data-stu-id="530bd-117">The service account for the instance running the master database must have administrative access to the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="530bd-118">如果该服务帐户更改，您必须更新对服务器和数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="530bd-118">If the service account changes, you must update permissions on both the server and database.</span></span>  
  
-   <span data-ttu-id="530bd-119">您必须是两个计算机上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员。</span><span class="sxs-lookup"><span data-stu-id="530bd-119">You must be an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator on both computers.</span></span>  
  
-   <span data-ttu-id="530bd-120">您必须确保灾难恢复计划适合远程分区的备份和还原。</span><span class="sxs-lookup"><span data-stu-id="530bd-120">You must ensure your disaster recovery plan accommodates backup and restore of the remote partitions.</span></span> <span data-ttu-id="530bd-121">使用远程分区可能使备份和还原操作变得复杂。</span><span class="sxs-lookup"><span data-stu-id="530bd-121">Using remote partitions can complicate backup and restore operations.</span></span> <span data-ttu-id="530bd-122">请确保仔细测试您的计划，以确保能够还原必需的数据。</span><span class="sxs-lookup"><span data-stu-id="530bd-122">Be sure to test your plan thoroughly to be sure you can restore the necessary data.</span></span>  
  
## <a name="configure-remote-partitions"></a><span data-ttu-id="530bd-123">配置远程分区</span><span class="sxs-lookup"><span data-stu-id="530bd-123">Configure remote partitions</span></span>  
 <span data-ttu-id="530bd-124">运行实例的两个单独的计算机 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 都是创建远程分区方式所必需的，它将一个计算机指定为主服务器，将另一台计算机指定为从属服务器。</span><span class="sxs-lookup"><span data-stu-id="530bd-124">Two separate computers that are running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are each required to create a remote partition arrangement that designates one computer as the master server and the other computer as the subordinate server.</span></span>  
  
 <span data-ttu-id="530bd-125">以下过程假定您有两个服务器实例，且在主服务器上部署了多维数据集数据库。</span><span class="sxs-lookup"><span data-stu-id="530bd-125">The following procedure assumes that you have two server instances, with a cube database deployed on the master server.</span></span> <span data-ttu-id="530bd-126">为了实现此过程的目的，我们将多维数据集数据库称为 db-master。</span><span class="sxs-lookup"><span data-stu-id="530bd-126">For the purposes of this procedure, the cube database is referred to as db-master.</span></span> <span data-ttu-id="530bd-127">将包含远程分区的存储数据库称为 db-storage。</span><span class="sxs-lookup"><span data-stu-id="530bd-127">The storage database containing remote partitions is referred to as db-storage.</span></span>  
  
 <span data-ttu-id="530bd-128">您将使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 来完成此过程。</span><span class="sxs-lookup"><span data-stu-id="530bd-128">You will use both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to complete this procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="530bd-129">远程分区只能与其他远程分区进行合并。</span><span class="sxs-lookup"><span data-stu-id="530bd-129">Remote partitions can be merged only with other remote partitions.</span></span> <span data-ttu-id="530bd-130">如果您在结合使用本地和远程分区，则也可以创建包括组合数据的新分区，删除不再使用的分区。</span><span class="sxs-lookup"><span data-stu-id="530bd-130">If you are using a combination of local and remote partitions, an alternative approach is to create new partitions that include the combined data, deleting the partitions you no longer use.</span></span>  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a><span data-ttu-id="530bd-131">为多维数据集部署指定有效服务器名称（在 SSDT 中）。</span><span class="sxs-lookup"><span data-stu-id="530bd-131">Specify valid server names for cube deployment (in SSDT)</span></span>  
  
1.  <span data-ttu-id="530bd-132">在主服务器上：在解决方案资源管理器中，右键单击解决方案名称，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="530bd-132">On the master server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="530bd-133">在 **“属性”** 对话框中，单击 **“配置属性”**，然后依次单击 **“部署”** 和 **“服务器”** ，并设置主服务器名称。</span><span class="sxs-lookup"><span data-stu-id="530bd-133">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the master server's name.</span></span>  
  
2.  <span data-ttu-id="530bd-134">在从属服务器上：在解决方案资源管理器中，右键单击解决方案名称，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="530bd-134">On the subordinate server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="530bd-135">在 **“属性”** 对话框中，单击 **“配置属性”**，然后依次单击 **“部署”** 和 **“服务器”** ，并设置从属服务器名称。</span><span class="sxs-lookup"><span data-stu-id="530bd-135">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the subordinate server's name.</span></span>  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a><span data-ttu-id="530bd-136">创建并部署辅助数据库（在 SSDT 中）</span><span class="sxs-lookup"><span data-stu-id="530bd-136">Create and deploy a secondary database (in SSDT)</span></span>  
  
1.  <span data-ttu-id="530bd-137">在从属服务器上：为存储数据库创建一个新 Analysis Services 项目。</span><span class="sxs-lookup"><span data-stu-id="530bd-137">On the subordinate server: Create a new Analysis Services project for the storage database.</span></span>  
  
2.  <span data-ttu-id="530bd-138">在从属服务器上：在解决方案资源管理器中创建一个指向多维数据集数据库 db-master 的新数据源。</span><span class="sxs-lookup"><span data-stu-id="530bd-138">On the subordinate server: In Solution Explorer, create a new data source pointing to the cube database, db-master.</span></span> <span data-ttu-id="530bd-139">使用访问接口“本机 OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="530bd-139">Use the provider **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="530bd-140">在从属服务器上：部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="530bd-140">On the subordinate server: Deploy the solution.</span></span>  
  
#### <a name="enable-features-in-ssms"></a><span data-ttu-id="530bd-141">启用功能（在 SSMS 中）</span><span class="sxs-lookup"><span data-stu-id="530bd-141">Enable features (in SSMS)</span></span>  
  
1.  <span data-ttu-id="530bd-142">在从属服务器上：在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击对象资源管理器中已连接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="530bd-142">On the subordinate server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="530bd-143">将“功能\LinkToOtherInstanceEnabled”\*\*\*\* 和“功能\LinkFromOtherInstanceEnabled”\*\*\*\* 都设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="530bd-143">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
2.  <span data-ttu-id="530bd-144">在从属服务器上：在对象资源管理器中右键单击服务器名称并选择“重新启动”\*\*\*\*，以重启服务器。</span><span class="sxs-lookup"><span data-stu-id="530bd-144">On the subordinate server: Restart the server by right-clicking the server name in Object Explorer and selecting **Restart**.</span></span>  
  
3.  <span data-ttu-id="530bd-145">在主服务器上：在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，右键单击对象资源管理器中已连接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="530bd-145">On the master server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="530bd-146">将“功能\LinkToOtherInstanceEnabled”\*\*\*\* 和“功能\LinkFromOtherInstanceEnabled”\*\*\*\* 都设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="530bd-146">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
4.  <span data-ttu-id="530bd-147">在主服务器上：在对象资源管理器中右键单击服务器名称并选择“重新启动”\*\*\*\*，以重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="530bd-147">On the master server: To restart the server, right-click the server name in Object Explorer and select **Restart**.</span></span>  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a><span data-ttu-id="530bd-148">设置远程服务器上的 MasterDataSourceID 数据库属性（在 SSMS 中）</span><span class="sxs-lookup"><span data-stu-id="530bd-148">Set the MasterDataSourceID database property on the remote server (in SSMS)</span></span>  
  
1.  <span data-ttu-id="530bd-149">在从属服务器上：右键单击存储数据库 "数据库存储"，指向 "**编写数据库脚本为**"，  |  **将其更改为**  |  **新的查询编辑器窗口**。</span><span class="sxs-lookup"><span data-stu-id="530bd-149">On the subordinate server: Right-click the storage database, db-storage, point to **Script Database as** | **ALTER To** | **New Query Editor Window**.</span></span>  
  
2.  <span data-ttu-id="530bd-150">将 **MasterDataSourceID** 添加到 XMLA，然后将多维数据集数据库 db-master 的 ID 指定为值。</span><span class="sxs-lookup"><span data-stu-id="530bd-150">Add **MasterDataSourceID** to the XMLA, and then specify the cube database, db-master, ID as the value.</span></span> <span data-ttu-id="530bd-151">XMLA 应类似以下示例。</span><span class="sxs-lookup"><span data-stu-id="530bd-151">The XMLA should look similar to the following.</span></span>  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  <span data-ttu-id="530bd-152">按 F5 执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="530bd-152">Press F5 to execute the script.</span></span>  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a><span data-ttu-id="530bd-153">设置远程分区（在 SSDT 中）</span><span class="sxs-lookup"><span data-stu-id="530bd-153">Set up the remote partition (in SSDT)</span></span>  
  
1.  <span data-ttu-id="530bd-154">在主服务器上：在多维数据集设计器中打开多维数据集，然后单击 "**分区**" 选项卡。展开度量值组。</span><span class="sxs-lookup"><span data-stu-id="530bd-154">On the master server: Open the cube in Cube Designer and click **Partitions** tab. Expand the measure group.</span></span> <span data-ttu-id="530bd-155">如果已为多个分区配置了度量值组，则单击“新建分区”\*\*\*\*，或单击“源”列中的浏览 (.</span><span class="sxs-lookup"><span data-stu-id="530bd-155">Click **New Partition** if the measure group is already configured for multiple partitions, or click the browse (.</span></span> <span data-ttu-id="530bd-156">.</span><span class="sxs-lookup"><span data-stu-id="530bd-156">.</span></span> <span data-ttu-id="530bd-157">.) 按钮编辑现有分区。</span><span class="sxs-lookup"><span data-stu-id="530bd-157">) button in the Source column to edit the existing partition.</span></span>  
  
2.  <span data-ttu-id="530bd-158">在分区向导的 **“指定源信息”** 中，选择初始数据源视图和事实数据表。</span><span class="sxs-lookup"><span data-stu-id="530bd-158">In the Partition Wizard, in **Specify Source Information**, select the original Data Source View and fact table.</span></span>  
  
3.  <span data-ttu-id="530bd-159">如果正在使用查询绑定，请提供将要创建的新分区的数据进行分段的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="530bd-159">If using a query binding, provide a WHERE clause that segments the data for the new partition you are creating.</span></span>  
  
4.  <span data-ttu-id="530bd-160">在“处理和存储位置”\*\*\*\* 中，在“处理位置”\*\*\*\* 下选择“远程 Analysis Services 数据源”\*\*\*\*，并单击“新建”\*\*\*\* 以创建指向从属数据库 db-storage 的新数据源。</span><span class="sxs-lookup"><span data-stu-id="530bd-160">In **Processing and Storage Locations**, under **Processing Location**, choose **Remote Analysis Services data source** and click **New** to create a new data source that points to your subordinate database, db-storage.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="530bd-161">如果收到错误，指示数据源在集合中不存在，则必须打开存储数据库 db-storage 的项目，并创建指向主数据库 db-master 的数据源。</span><span class="sxs-lookup"><span data-stu-id="530bd-161">If you get an error indicating the data source does not exist in the collection, you must open the project of the storage database, db-storage, and create a data source that points to the master database, db-master.</span></span>  
  
5.  <span data-ttu-id="530bd-162">在主服务器上：在解决方案资源管理器中右键单击多维数据集名称，选择“处理”\*\*\*\*，全面处理该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="530bd-162">On the master server: Right-click the cube name in Solution Explorer, select **Process** and fully process the cube.</span></span>  
  
## <a name="administering-remote-partitions"></a><span data-ttu-id="530bd-163">管理远程分区</span><span class="sxs-lookup"><span data-stu-id="530bd-163">Administering remote partitions</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="530bd-164">支持远程分区的并行处理和顺序处理。</span><span class="sxs-lookup"><span data-stu-id="530bd-164">supports both parallel and sequential processing of remote partitions.</span></span> <span data-ttu-id="530bd-165">定义了分区的主数据库将在参与多维数据集分区处理的所有实例之间协调事务。</span><span class="sxs-lookup"><span data-stu-id="530bd-165">The master database, where the partitions were defined, coordinates the transactions among all the instances that participate in processing the partitions of a cube.</span></span> <span data-ttu-id="530bd-166">然后，将处理报表发送给处理了某一分区的所有实例。</span><span class="sxs-lookup"><span data-stu-id="530bd-166">Processing reports are then sent to all instances that processed a partition.</span></span>  
  
 <span data-ttu-id="530bd-167">包含远程分区的多维数据集可与其在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的单个实例上的分区一起管理。</span><span class="sxs-lookup"><span data-stu-id="530bd-167">A cube that contains remote partitions can be administered together with its partitions on a single instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="530bd-168">但是，只能在定义了分区及其父多维数据集的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上查看和更新远程分区的元数据。</span><span class="sxs-lookup"><span data-stu-id="530bd-168">However, the metadata for the remote partition can be viewed and updated only on the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube were defined.</span></span> <span data-ttu-id="530bd-169">无法在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的远程实例上查看或更新远程分区。</span><span class="sxs-lookup"><span data-stu-id="530bd-169">The remote partition cannot be viewed or updated on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="530bd-170">尽管不向架构行集公开专用于存储远程分区的数据库，但使用分析管理对象 (AMO) 的应用程序仍可以通过使用 XML for Analysis Discover 命令来发现专用数据库。</span><span class="sxs-lookup"><span data-stu-id="530bd-170">Although databases dedicated to storage of remote partitions are not exposed to schema rowsets, applications that use Analysis Management Objects (AMO) can still discover a dedicated database by using the XML for Analysis Discover command.</span></span> <span data-ttu-id="530bd-171">通过使用 TCP 或 HTTP 客户端直接发送到专用数据库的所有 CREATE 或 DELETE 命令都将成功，但服务器将返回一个警告，指示该操作可能会损害这一紧密管理的数据库。</span><span class="sxs-lookup"><span data-stu-id="530bd-171">Any CREATE or DELETE command that is sent directly to a dedicated database by using a TCP or HTTP client will succeed, but the server will return a warning indicating that the action may damage this closely managed database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="530bd-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="530bd-172">See Also</span></span>  
 [<span data-ttu-id="530bd-173">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="530bd-173">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
