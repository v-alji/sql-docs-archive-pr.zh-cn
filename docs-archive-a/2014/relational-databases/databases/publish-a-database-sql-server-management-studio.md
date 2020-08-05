---
title: 发布数据库 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 98b2914e-7147-40af-ba7d-87253bbe8bf9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 652f2341d24c19e6c5ce34196b0e1c4dc5b09084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581291"
---
# <a name="publish-a-database-sql-server-management-studio"></a><span data-ttu-id="335d0-102">发布数据库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="335d0-102">Publish a Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="335d0-103">可以使用 **“生成和发布脚本向导”** 向 Web 宿主提供程序发布整个数据库或单独的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="335d0-103">You can use the **Generate and Publish Scripts Wizard** to publish an entire database or individual database objects to a Web hosting provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="335d0-104">本主题中介绍的功能以前往往由“发布数据库向导”提供。</span><span class="sxs-lookup"><span data-stu-id="335d0-104">The functionality described in this topic used to be provided by the Publish Database Wizard.</span></span> <span data-ttu-id="335d0-105">发布功能已添加到“生成和发布脚本向导”，“发布数据库向导”已停止使用。</span><span class="sxs-lookup"><span data-stu-id="335d0-105">The publishing functionality has been added to the Generate and Publish Scripts Wizard, and the Publish Database Wizard has been discontinued.</span></span>  
  
## <a name="generate-and-publish-scripts-wizard"></a><span data-ttu-id="335d0-106">“生成和发布脚本向导”</span><span class="sxs-lookup"><span data-stu-id="335d0-106">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="335d0-107">“生成和发布脚本向导”可用于向 Web 宿主提供程序发布数据库或所选数据库对象。</span><span class="sxs-lookup"><span data-stu-id="335d0-107">The Generate and Publish Scripts Wizard can be used to publish a database or selected database objects to a Web hosting provider.</span></span> <span data-ttu-id="335d0-108">SQL Server Web 宿主提供程序是与 Web 服务之间的连接接口。</span><span class="sxs-lookup"><span data-stu-id="335d0-108">A SQL Server Web hosting provider is a connectivity interface to a Web service.</span></span> <span data-ttu-id="335d0-109">Web 服务是通过使用来自 CodePlex 上的 SQL Server Hosting Toolkit 的 Database Publishing Services 项目生成的。</span><span class="sxs-lookup"><span data-stu-id="335d0-109">The Web service is created by using the Database Publishing Services project from the SQL Server Hosting Toolkit on CodePlex.</span></span> <span data-ttu-id="335d0-110">通过使用“生成和发布脚本向导”，此 Web 服务使 Web 宿主客户能够轻松地将其数据库发布到该服务。</span><span class="sxs-lookup"><span data-stu-id="335d0-110">The Web service makes it easy for the Web hoster customers to publish their databases to the service by using the Generate and Publish Scripts Wizard.</span></span> <span data-ttu-id="335d0-111">有关下载 SQL Server Hosting Toolkit 的详细信息，请参阅 [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025)（SQL Server 数据库发布服务）。</span><span class="sxs-lookup"><span data-stu-id="335d0-111">For more information about downloading the SQL Server Hosting Toolkit, see [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).</span></span>  
  
 <span data-ttu-id="335d0-112">“生成和发布脚本向导”还可用于创建传输数据库的脚本。</span><span class="sxs-lookup"><span data-stu-id="335d0-112">The Generate and Publish Scripts Wizard can also be used to create a script for transferring a database.</span></span>  
  
#### <a name="to-publish-a-database-to-a-web-service"></a><span data-ttu-id="335d0-113">将数据库发布到 Web 服务</span><span class="sxs-lookup"><span data-stu-id="335d0-113">To publish a database to a Web service</span></span>  
  
1.  <span data-ttu-id="335d0-114">在对象资源管理器中，展开“数据库”  ，右键单击某个数据库，指向“任务”  ，然后单击“生成和发布脚本”  。</span><span class="sxs-lookup"><span data-stu-id="335d0-114">In Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Generate and Publish Scripts**.</span></span> <span data-ttu-id="335d0-115">按照向导中的步骤，创建用于发布的数据库对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="335d0-115">Follow the steps in the wizard to script the database objects for publishing.</span></span>  
  
2.  <span data-ttu-id="335d0-116">在 **“选择对象”** 页上，选择要发布到 Web 宿主服务的对象。</span><span class="sxs-lookup"><span data-stu-id="335d0-116">On the **Choose Objects** page, select the objects to be published to the Web hosting service.</span></span>  
  
3.  <span data-ttu-id="335d0-117">在 **“设置脚本编写选项”** 页中，选择 **“发布到 Web 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="335d0-117">On the **Set Scripting Options** page, select **Publish to Web Service**.</span></span>  
  
    1.  <span data-ttu-id="335d0-118">在 **“提供程序”** 框中，指定 Web 服务的提供程序。</span><span class="sxs-lookup"><span data-stu-id="335d0-118">In the **Provider** box, specify the provider for your Web service.</span></span> <span data-ttu-id="335d0-119">如果您尚未配置 Web 宿主提供程序，请选择 **“管理提供程序”** ，然后使用 **“管理提供程序”** 对话框来为您的 Web 服务配置一个提供程序。</span><span class="sxs-lookup"><span data-stu-id="335d0-119">If you have not configured a Web hosting provider, select **Manage Providers** and use the **Manage Providers** dialog box to configure a provider for your Web service.</span></span>  
  
    2.  <span data-ttu-id="335d0-120">若要指定高级发布选项，请选择 **“发布到 Web 服务”** 部分中的 **“高级”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="335d0-120">To specify advanced publishing options, select the **Advanced** button in the **Publish to Web Service** section.</span></span>  
  
4.  <span data-ttu-id="335d0-121">在 **“摘要”** 页上，查看您的选择。</span><span class="sxs-lookup"><span data-stu-id="335d0-121">On the **Summary** page, review your selections.</span></span> <span data-ttu-id="335d0-122">单击 **“上一步”** 以更改您的选择。</span><span class="sxs-lookup"><span data-stu-id="335d0-122">Click **Previous** to change your selections.</span></span> <span data-ttu-id="335d0-123">单击 **“下一步”** 以发布所选的对象。</span><span class="sxs-lookup"><span data-stu-id="335d0-123">Click **Next** to publish the objects you selected.</span></span>  
  
5.  <span data-ttu-id="335d0-124">在 **“保存或发布脚本”** 页上，监视发布的进度。</span><span class="sxs-lookup"><span data-stu-id="335d0-124">On the **Save or Publish Scripts** page, monitor the progress of the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335d0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="335d0-125">See Also</span></span>  
 <span data-ttu-id="335d0-126">[生成脚本 (SQL Server Management Studio)](../scripting/generate-scripts-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="335d0-126">[Generate Scripts &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="335d0-127">将数据库复制到其他服务器</span><span class="sxs-lookup"><span data-stu-id="335d0-127">Copy Databases to Other Servers</span></span>](copy-databases-to-other-servers.md)  
  
  
