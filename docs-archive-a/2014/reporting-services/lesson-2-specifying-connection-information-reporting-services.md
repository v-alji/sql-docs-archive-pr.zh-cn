---
title: 第 2 课：指定连接信息 (Reporting Services)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689287"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a><span data-ttu-id="b01f9-102">第 2 课：指定连接信息 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b01f9-102">Lesson 2: Specifying Connection Information (Reporting Services)</span></span>
  <span data-ttu-id="b01f9-103">向“教程”项目添加报表之后，需要定义数据源\*\*，它是报表从关系数据库、多维数据库或其他资源访问数据所使用的连接信息。</span><span class="sxs-lookup"><span data-stu-id="b01f9-103">After you add a report to the Tutorial project, you need to define a *data source*, which is connection information the report uses to access data from either a relational database, multidimensional database, or other resource.</span></span>  
  
 <span data-ttu-id="b01f9-104">在本课中，您将使用 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 示例数据库作为数据源。</span><span class="sxs-lookup"><span data-stu-id="b01f9-104">In this lesson, you will use the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database as your data source.</span></span> <span data-ttu-id="b01f9-105">本教程假定此数据库位于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 本地计算机上安装的的默认实例中。</span><span class="sxs-lookup"><span data-stu-id="b01f9-105">This tutorial assumes that this database is located in a default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed on your local computer.</span></span>  
  
### <a name="to-set-up-a-connection"></a><span data-ttu-id="b01f9-106">设置连接</span><span class="sxs-lookup"><span data-stu-id="b01f9-106">To set up a connection</span></span>  
  
1.  <span data-ttu-id="b01f9-107">在 "**报表数据**" 窗格中，单击 "**新建**"，然后单击 "**数据源 ...**"。</span><span class="sxs-lookup"><span data-stu-id="b01f9-107">In the **Report Data** pane, click **New** and then click **Data Source...**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b01f9-108">如果“报表数据”\*\*\*\* 窗格不可见，请单击“视图”\*\*\*\* 菜单上的“报表数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b01f9-108">If the **Report Data** pane is not visible, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="b01f9-109">在 **“名称”** 中，键入 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b01f9-109">In **Name**, type [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].</span></span>  
  
3.  <span data-ttu-id="b01f9-110">确保已选中“嵌入连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b01f9-110">Make sure **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="b01f9-111">在“类型”中，选择 Microsoft SQL Server\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b01f9-111">In **Type**, select **Microsoft SQL Server**.</span></span>  
  
5.  <span data-ttu-id="b01f9-112">在“连接字符串”中，键入以下文本\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="b01f9-112">In **Connection string**, type the following:</span></span>  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     <span data-ttu-id="b01f9-113">该连接字符串假定 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、报表服务器和 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库都已安装在本地计算机中，并且你拥有登录 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="b01f9-113">This connection string assumes that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the report server, and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database are all installed on the local computer and that you have permission to log on to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b01f9-114">如果使用的是带高级服务的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 或命名实例，则连接字符串必须包括实例信息：</span><span class="sxs-lookup"><span data-stu-id="b01f9-114">If you are using [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services or a named instance, the connection string must include instance information:</span></span>  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  <span data-ttu-id="b01f9-115">有关连接字符串的详细信息，请参阅 "Reporting Services 和[数据源属性" 对话框](data-source-properties-dialog-box-general.md)中的 "[数据连接、数据源和连接字符串](data-connections-data-sources-and-connection-strings-in-reporting-services.md)"。</span><span class="sxs-lookup"><span data-stu-id="b01f9-115">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) and [Data Source Properties Dialog Box, General](data-source-properties-dialog-box-general.md).</span></span>  
  
6.  <span data-ttu-id="b01f9-116">在左窗格中单击“凭据”\*\*\*\*，然后单击“使用 Windows 身份验证(集成安全性)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b01f9-116">Click **Credentials** in the left pane and click **Use Windows Authentication (integrated security)**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="b01f9-117">数据源 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] 将添加到 "**报表数据**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="b01f9-117">data source [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] is added to the **Report Data** pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="b01f9-118">下一个任务</span><span class="sxs-lookup"><span data-stu-id="b01f9-118">Next Task</span></span>  
 <span data-ttu-id="b01f9-119">已成功定义了到 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 示例数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="b01f9-119">You have successfully defined a connection to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b01f9-120">下一步，将创建报表。</span><span class="sxs-lookup"><span data-stu-id="b01f9-120">Next, you will create the report.</span></span> <span data-ttu-id="b01f9-121">请参阅[第 3 课：为表报表定义数据集 (Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b01f9-121">See [Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01f9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b01f9-122">See Also</span></span>  
 [<span data-ttu-id="b01f9-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b01f9-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
