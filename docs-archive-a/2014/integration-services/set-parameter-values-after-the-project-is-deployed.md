---
title: 在部署项目后设置参数值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694034"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a><span data-ttu-id="f9ea0-102">在部署项目后设置参数值</span><span class="sxs-lookup"><span data-stu-id="f9ea0-102">Set Parameter Values After the Project Is Deployed</span></span>
  <span data-ttu-id="f9ea0-103">通过部署向导，您可以在将项目部署到目录时设置服务器默认参数值。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-103">The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog.</span></span> <span data-ttu-id="f9ea0-104">在您的项目处于目录中后，您可以使用 SQL Server Management Studio (SSMS) 对象资源管理器或 Transact-SQL 来设置服务器默认值。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-104">After your project is in the catalog, you can use SQL Server Management Studio (SSMS) Object Explorer or Transact-SQL to set server default values.</span></span>  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a><span data-ttu-id="f9ea0-105">使用 SSMS 对象资源管理器设置服务器默认值：</span><span class="sxs-lookup"><span data-stu-id="f9ea0-105">To set server defaults with SSMS Object Explorer:</span></span>  
  
1.  <span data-ttu-id="f9ea0-106">选择并右键单击“集成服务”节点下的项目。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f9ea0-106">Select and right-click the project under the **Integration Services** node.</span></span>  
  
2.  <span data-ttu-id="f9ea0-107">单击 **“属性”** 以便打开 **“项目属性”** 对话框窗口。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-107">Click **Properties** to open the **Project Properties** dialog window.</span></span>  
  
3.  <span data-ttu-id="f9ea0-108">通过在 **“选择页”** 之下单击 **“参数”**，打开参数页。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-108">Open the parameters page by clicking **Parameters** under **Select a page**.</span></span>  
  
4.  <span data-ttu-id="f9ea0-109">在 **“参数”** 列表中选择所需参数。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-109">Select the desired parameter in the **Parameters** list.</span></span> <span data-ttu-id="f9ea0-110">注意： **“容器”** 列将帮助区分项目参数和包参数。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-110">Note: The **Container** column helps distinguish project parameters from package parameters.</span></span>  
  
5.  <span data-ttu-id="f9ea0-111">在 **“值”** 列中，指定所需的服务器默认参数值。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-111">In the **Value** column, specify the desired server default parameter value.</span></span>  
  
 <span data-ttu-id="f9ea0-112">若要使用 TRANSACT-SQL 设置服务器默认值，请使用 [catalog.set_object_parameter_value（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database)存储过程。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-112">To set server defaults with Transact-SQL, use the [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) stored procedure.</span></span> <span data-ttu-id="f9ea0-113">若要查看当前服务器默认值，请查询 [catalog.object_parameters（SSISDB 数据库）](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database)视图。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-113">To view current server defaults, query the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span> <span data-ttu-id="f9ea0-114">若要清除服务器默认值，请使用 [catalog.clear_object_parameter_value（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database)存储过程。</span><span class="sxs-lookup"><span data-stu-id="f9ea0-114">To clear a server default value, use the [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ea0-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9ea0-115">See Also</span></span>  
 [<span data-ttu-id="f9ea0-116">&#40;SSIS&#41; 参数 Integration Services</span><span class="sxs-lookup"><span data-stu-id="f9ea0-116">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
