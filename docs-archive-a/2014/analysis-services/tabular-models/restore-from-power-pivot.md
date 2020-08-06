---
title: 从 PowerPivot 还原 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dbb0e7867451e67eaa1503c54d7e3da1c276965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692555"
---
# <a name="restore-from-powerpivot"></a><span data-ttu-id="5d90b-102">从 PowerPivot 还原</span><span class="sxs-lookup"><span data-stu-id="5d90b-102">Restore from PowerPivot</span></span>
  <span data-ttu-id="5d90b-103">您可以使用 SQL Server Management Studio 中的“从 PowerPivot 还原”功能针对 Analysis Services 实例（在表格模式下运行）创建新的表格模型数据库，或从 PowerPivot 工作簿 (.xlsx) 还原到现有数据库。</span><span class="sxs-lookup"><span data-stu-id="5d90b-103">You can use the Restore from PowerPivot feature in SQL Server Management Studio to create a new Tabular model database on an Analysis Services instance (running in Tabular mode), or restore to an existing database from a PowerPivot workbook (.xlsx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d90b-104">SQL Server Data Tools 中的“从 PowerPivot 导入”项目模板提供了类似功能。</span><span class="sxs-lookup"><span data-stu-id="5d90b-104">The Import from PowerPivot project template in SQL Server Data Tools provides similar functionality.</span></span> <span data-ttu-id="5d90b-105">有关详细信息，请参阅[从 PowerPivot &#40;SSAS 表格&#41;导入](import-from-power-pivot-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="5d90b-105">For more information, see [Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="5d90b-106">使用“从 PowerPivot 还原”时，请注意下列问题：</span><span class="sxs-lookup"><span data-stu-id="5d90b-106">When using Restore from PowerPivot, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="5d90b-107">为了使用“从 PowerPivot 还原”，您必须以该 Analysis Services 实例上的服务器管理员角色的成员身份登录。</span><span class="sxs-lookup"><span data-stu-id="5d90b-107">In order to use Restore from PowerPivot, you must be logged on as a member of the Server Administrators role on the Analysis Services instance.</span></span>  
  
-   <span data-ttu-id="5d90b-108">该 Analysis Services 实例服务帐户必须对您要还原的工作簿文件具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="5d90b-108">The Analysis Services instance service account must have Read permissions on the workbook file you are restoring from.</span></span>  
  
-   <span data-ttu-id="5d90b-109">默认情况下，当您从 PowerPivot 还原数据库时，表格模型数据库的“数据源模拟信息”属性设置为“默认”，这会指定 Analysis Services 实例服务帐户。</span><span class="sxs-lookup"><span data-stu-id="5d90b-109">By default, when you restore a database from PowerPivot, the Tabular model database Data Source Impersonation Info property is set to Default, which specifies the Analysis Services instance service account.</span></span> <span data-ttu-id="5d90b-110">建议在“数据库属性”中将模拟凭据更改为 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="5d90b-110">It is recommended you change the impersonation credentials to a Windows user account in Database Properties.</span></span> <span data-ttu-id="5d90b-111">有关详细信息，请参阅[模拟（SSAS 表格）](impersonation-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="5d90b-111">For more information, see [Impersonation &#40;SSAS Tabular&#41;](impersonation-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="5d90b-112">PowerPivot 数据模型中的数据将复制到该 Analysis Services 实例上的现有或新的表格模型数据库中。</span><span class="sxs-lookup"><span data-stu-id="5d90b-112">Data in the PowerPivot data model will be copied into an existing or new Tabular model database on the Analysis Services instance.</span></span> <span data-ttu-id="5d90b-113">如果您的 PowerPivot 工作簿包含链接表，则将以不带数据源的表形式来重新创建表，该表与使用“粘贴到新表中”创建的表类似。</span><span class="sxs-lookup"><span data-stu-id="5d90b-113">If your PowerPivot workbook contains linked tables, they will be recreated as a table without a data source, similar to a table created using Paste To New table.</span></span>  
  
### <a name="to-restore-from-powerpivot"></a><span data-ttu-id="5d90b-114">从 PowerPivot 还原</span><span class="sxs-lookup"><span data-stu-id="5d90b-114">To Restore from PowerPivot</span></span>  
  
1.  <span data-ttu-id="5d90b-115">在 SSMS 中要还原到的 Active Directory 实例中，右键单击 "**数据库**"，然后单击 "**从 PowerPivot 还原**"。</span><span class="sxs-lookup"><span data-stu-id="5d90b-115">In SSMS, in the Active Directory instance you want to restore to, right click **Databases**, and then click **Restore from PowerPivot**.</span></span>  
  
2.  <span data-ttu-id="5d90b-116">在 "**从 PowerPivot 还原**" 对话框中的 "**还原源**" 的 "**备份文件**" 中，单击 "**浏览**"，然后选择要从中进行还原的 .abf 或 .xslx 文件。</span><span class="sxs-lookup"><span data-stu-id="5d90b-116">In the **Restore from PowerPivot** dialog box, in **Restore Source**, in **Backup file**, click **Browse**, and then select an .abf or .xslx file to restore from.</span></span>  
  
3.  <span data-ttu-id="5d90b-117">在 **“还原目标”** 中的“ **还原数据库”** 中，键入新数据库或现有数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="5d90b-117">In **Restore Target**, in **Restore database**, type a name for a new database or for an existing database.</span></span> <span data-ttu-id="5d90b-118">如果不指定名称，则使用工作簿的名称。</span><span class="sxs-lookup"><span data-stu-id="5d90b-118">If you do not specify a name, the name of the workbook is used.</span></span>  
  
4.  <span data-ttu-id="5d90b-119">在 **“存储位置”** 中，单击 **“浏览”**，然后选择数据库的存储位置。</span><span class="sxs-lookup"><span data-stu-id="5d90b-119">In **Storage location**, click **Browse**, and then select a location to store the database.</span></span>  
  
5.  <span data-ttu-id="5d90b-120">在 **“选项”** 中，选中 **“包括安全信息”** 。</span><span class="sxs-lookup"><span data-stu-id="5d90b-120">In **Options**, leave **Include security information** checked.</span></span> <span data-ttu-id="5d90b-121">在从 PowerPivot 工作簿还原时，此设置不适用。</span><span class="sxs-lookup"><span data-stu-id="5d90b-121">When restoring from a PowerPivot workbook, this setting does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d90b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d90b-122">See Also</span></span>  
 <span data-ttu-id="5d90b-123">[&#40;SSAS 表格&#41;的表格模型数据库](tabular-model-databases-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5d90b-123">[Tabular Model Databases &#40;SSAS Tabular&#41;](tabular-model-databases-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="5d90b-124">从 PowerPivot &#40;SSAS 表格&#41;导入</span><span class="sxs-lookup"><span data-stu-id="5d90b-124">Import from PowerPivot &#40;SSAS Tabular&#41;</span></span>](import-from-power-pivot-ssas-tabular.md)  
  
  
