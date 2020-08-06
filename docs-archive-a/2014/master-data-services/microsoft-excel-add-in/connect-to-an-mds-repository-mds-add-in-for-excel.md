---
title: 连接 MDS 存储库 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c1db0594f07da7ff8a78642e4b2de0eb9e507164
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688971"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a><span data-ttu-id="d7ff4-102">连接 MDS 存储库（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="d7ff4-102">Connect to an MDS Repository (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="d7ff4-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，你必须先连接到 MDS 存储库，然后才能加载或发布数据。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must connect to an MDS repository before you can load or publish data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d7ff4-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="d7ff4-104">Prerequisites</span></span>  
 <span data-ttu-id="d7ff4-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d7ff4-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d7ff4-106">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-connect-to-an-mds-repository"></a><span data-ttu-id="d7ff4-107">连接 MDS 存储库</span><span class="sxs-lookup"><span data-stu-id="d7ff4-107">To connect to an MDS repository</span></span>  
  
1.  <span data-ttu-id="d7ff4-108">在 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中的 **“主数据”** 选项卡上的 **“连接并加载”** 组中，单击 **“连接”** 按钮下的箭头，然后单击 **“管理连接”**。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-108">In the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], on the **Master Data** tab, in the **Connect and Load** group, click the arrow under the **Connect** button and click **Manage Connections**.</span></span>  
  
2.  <span data-ttu-id="d7ff4-109">在 **“管理连接”** 对话框上的 **“新建连接”** 部分中，单击 **“创建新连接”**。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-109">On the **Manage Connections** dialog box, in the **New connection** section, click **Create a new connection**.</span></span>  
  
3.  <span data-ttu-id="d7ff4-110">单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-110">Click **New**.</span></span>  
  
4.  <span data-ttu-id="d7ff4-111">在 **“添加新连接”** 对话框的 **“描述”** 字段中，键入您的连接说明。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-111">On the **Add New Connection** dialog box, in the **Description** field, type a description for your connection.</span></span> <span data-ttu-id="d7ff4-112">在您单击工具栏上的 **“连接”** 按钮后将显示此连接。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-112">This connection will be displayed when you click the arrow under the **Connect** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="d7ff4-113">在“MDS 服务器地址”框中，键入 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序的 URL，例如 http://contoso/mds\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-113">In the **MDS server address** box, type the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7ff4-114">确保使用计算机名称；而不要使用“localhost”。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-114">Ensure that you use the computer name; do not use "localhost".</span></span>  
  
6.  <span data-ttu-id="d7ff4-115">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-115">Click **OK**.</span></span> <span data-ttu-id="d7ff4-116">名称将显示在 **“现有连接”** 部分中。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-116">The name is displayed in the **Existing Connections** section.</span></span>  
  
7.  <span data-ttu-id="d7ff4-117">还可以单击 **“测试”** 对连接进行测试。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-117">Optionally, click **Test** to test the connection.</span></span> <span data-ttu-id="d7ff4-118">将显示一个确认或错误对话框。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-118">A confirmation or error dialog is displayed.</span></span> <span data-ttu-id="d7ff4-119">单击 **“确定”** 将其关闭。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-119">Click **OK** to close it.</span></span>  
  
8.  <span data-ttu-id="d7ff4-120">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-120">Click **Connect**.</span></span> <span data-ttu-id="d7ff4-121">随即显示 **Master Data Services** 窗格。</span><span class="sxs-lookup"><span data-stu-id="d7ff4-121">The **Master Data Services** pane is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d7ff4-122">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d7ff4-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="d7ff4-123">将数据从 MDS 加载到 Excel</span><span class="sxs-lookup"><span data-stu-id="d7ff4-123">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)  
  
-   [<span data-ttu-id="d7ff4-124">在加载 &#40;MDS Add-in for Excel 前筛选数据&#41;</span><span class="sxs-lookup"><span data-stu-id="d7ff4-124">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7ff4-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7ff4-125">See Also</span></span>  
 [<span data-ttu-id="d7ff4-126">连接（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="d7ff4-126">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
  
