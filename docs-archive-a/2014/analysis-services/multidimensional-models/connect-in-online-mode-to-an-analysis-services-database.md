---
title: 以联机模式连接到 Analysis Services 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 363beb7132eae92907198979fe2d9892c5d07b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691980"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a><span data-ttu-id="2b4c7-102">在联机模式下连接到 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="2b4c7-102">Connect in Online Mode to an Analysis Services Database</span></span>
  <span data-ttu-id="2b4c7-103">您可以直接连接到现有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库并直接修改该数据库中的对象。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-103">You can connect directly to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and directly modify objects within that database.</span></span> <span data-ttu-id="2b4c7-104">直接连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库时，会立即更改对象并且不在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中创建 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-104">When you connect directly to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, changes to objects occur immediately and no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is created within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a><span data-ttu-id="2b4c7-105">使用 SQL Server Data Tools 直接连接到 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="2b4c7-105">To Connect Directly to an Analysis Services Database by using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="2b4c7-106">打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-106">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="2b4c7-107">在 **“文件”** 菜单上，指向 **“打开”** ，然后单击 **“Analysis Services 数据库”**。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-107">On the **File** menu, point to **Open** and then click **Analysis Services Database**.</span></span>  
  
3.  <span data-ttu-id="2b4c7-108">选择 **“连接到现有数据库”**。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-108">Select **Connect to existing database**.</span></span>  
  
4.  <span data-ttu-id="2b4c7-109">指定服务器名称和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-109">Specify the server name and the database name.</span></span>  
  
     <span data-ttu-id="2b4c7-110">可以键入数据库名称，也可以查询服务器以查看服务器上的现有数据库。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-110">You can either type the database name or query the server to view the existing databases on the server.</span></span>  
  
5.  <span data-ttu-id="2b4c7-111">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-111">Click **OK**.</span></span>  
  
     <span data-ttu-id="2b4c7-112">现在可以直接编辑 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="2b4c7-112">You can now directly edit any objects within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4c7-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b4c7-113">See Also</span></span>  
 <span data-ttu-id="2b4c7-114">[在开发阶段使用 Analysis Services 项目和数据库](work-with-analysis-services-projects-and-databases-in-development.md) </span><span class="sxs-lookup"><span data-stu-id="2b4c7-114">[Working with Analysis Services Projects and Databases During the Development Phase](work-with-analysis-services-projects-and-databases-in-development.md) </span></span>  
 [<span data-ttu-id="2b4c7-115">使用 SQL Server Data Tools 创建多维模型 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="2b4c7-115">Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;</span></span>](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
