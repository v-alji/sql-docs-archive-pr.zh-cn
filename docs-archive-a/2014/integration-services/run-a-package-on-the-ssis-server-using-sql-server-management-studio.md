---
title: 使用 SQL Server Management Studio 在 SSIS 服务器上运行包 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d17009988dea54621d4fd7ef542cf452bfe95c6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687960"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a><span data-ttu-id="0b10c-102">使用 SQL Server Management Studio 在 SSIS 服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="0b10c-102">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>
  <span data-ttu-id="0b10c-103">在将您的项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器中之后，可以在该服务器上运行此包。</span><span class="sxs-lookup"><span data-stu-id="0b10c-103">After you deploy your project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can run the package on the server.</span></span>  
  
 <span data-ttu-id="0b10c-104">您可以使用操作报告查看有关服务器上已运行或当前正在运行的包的信息。</span><span class="sxs-lookup"><span data-stu-id="0b10c-104">You can use operations reports to view information about packages that have run, or are currently running, on the server.</span></span> <span data-ttu-id="0b10c-105">有关详细信息，请参阅 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0b10c-105">For more information, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a><span data-ttu-id="0b10c-106">使用 SQL Server Management Studio 在服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="0b10c-106">To run a package on the server using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0b10c-107">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 目录的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="0b10c-107">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
2.  <span data-ttu-id="0b10c-108">在对象资源管理器中，展开 **“Integration Services 目录”** 节点，再展开 **“SSISDB”** 节点，然后导航到包含在您部署的项目中的包。</span><span class="sxs-lookup"><span data-stu-id="0b10c-108">In Object Explorer, expand the **Integration Services Catalogs** node, expand the **SSISDB** node, and navigate to the package contained in the project you deployed.</span></span>  
  
3.  <span data-ttu-id="0b10c-109">右键单击包名称，然后选择“执行”  。</span><span class="sxs-lookup"><span data-stu-id="0b10c-109">Right-click the package name and select **Execute**.</span></span>  
  
4.  <span data-ttu-id="0b10c-110">使用 **“执行包”** 对话框中的 **“参数”** 、 **“连接管理器”** 和 **“高级”** 选项卡上的设置来配置包执行。</span><span class="sxs-lookup"><span data-stu-id="0b10c-110">Configure the package execution by using the settings on the **Parameters**, **Connection Managers**, and **Advanced** tabs in the **Execute Package** dialog box.</span></span>  
  
5.  <span data-ttu-id="0b10c-111">单击 **“确定”** 运行包。</span><span class="sxs-lookup"><span data-stu-id="0b10c-111">Click **OK** to run the package.</span></span>  
  
     <span data-ttu-id="0b10c-112">-或-</span><span class="sxs-lookup"><span data-stu-id="0b10c-112">-or-</span></span>  
  
     <span data-ttu-id="0b10c-113">使用存储过程来运行包。</span><span class="sxs-lookup"><span data-stu-id="0b10c-113">Use stored procedures to run the package.</span></span> <span data-ttu-id="0b10c-114">单击“脚本”  生成创建执行实例并启动执行实例的 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="0b10c-114">Click **Script** to generate the Transact-SQL statement that creates an instance of the execution and starts an instance of the execution.</span></span> <span data-ttu-id="0b10c-115">该语句包含对 catalog.create_execution、catalog.set_execution_parameter_value 和 catalog.start_execution 存储过程的调用。</span><span class="sxs-lookup"><span data-stu-id="0b10c-115">The statement includes a call to the catalog.create_execution, catalog.set_execution_parameter_value, and catalog.start_execution stored procedures.</span></span> <span data-ttu-id="0b10c-116">有关这些存储过程的详细信息，请参阅 [catalog.create_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)、[catalog.set_execution_parameter_value（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)和 [catalog.start_execution（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="0b10c-116">For more information about these stored procedures, see [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database), and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
  
