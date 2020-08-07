---
title: 管理 CLR 集成程序集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 191ccd73ca42ef4c26291e6de88f5f2b0cf565ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691236"
---
# <a name="managing-clr-integration-assemblies"></a><span data-ttu-id="e9af9-102">管理 CLR 集成程序集</span><span class="sxs-lookup"><span data-stu-id="e9af9-102">Managing CLR Integration Assemblies</span></span>
  <span data-ttu-id="e9af9-103">托管代码在被编译后部署在称作程序集的单元中。</span><span class="sxs-lookup"><span data-stu-id="e9af9-103">Managed code is compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="e9af9-104">程序集将打包为 DLL 或可执行 (.exe) 文件。</span><span class="sxs-lookup"><span data-stu-id="e9af9-104">An assembly is packaged as a DLL or executable (.exe) file.</span></span> <span data-ttu-id="e9af9-105">尽管可执行文件可以自动运行，但 DLL 必须在现有应用程序中承载。</span><span class="sxs-lookup"><span data-stu-id="e9af9-105">While an executable file can run on its own, a DLL must be hosted in an existing application.</span></span> <span data-ttu-id="e9af9-106">托管的 DLL 程序集可以加载到中并由其承载 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9af9-106">Managed DLL assemblies can be loaded into and hosted by [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="e9af9-107">使用 CREATE ASSEMBLY 语句的数据库，然后才能将其加载到进程中并使用它。</span><span class="sxs-lookup"><span data-stu-id="e9af9-107">database using the CREATE ASSEMBLY statement, before it can be loaded in the process and used.</span></span> <span data-ttu-id="e9af9-108">还可以使用 ALTER ASSEMBLY 语句从更新的版本更新程序集，或者使用 DROP ASSEMBLY 语句从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中删除程序集。</span><span class="sxs-lookup"><span data-stu-id="e9af9-108">Assemblies can also be updated from a more recent version using the ALTER ASSEMBLY statement, or removed from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the DROP ASSEMBLY statement.</span></span>  
  
 <span data-ttu-id="e9af9-109">程序集信息存储在安装了程序集的数据库的 `sys.assembly_files` 表中。</span><span class="sxs-lookup"><span data-stu-id="e9af9-109">Assembly information is stored in the `sys.assembly_files` table in the database where the assembly has been installed.</span></span> <span data-ttu-id="e9af9-110">`sys.assembly_files` 表包含以下列。</span><span class="sxs-lookup"><span data-stu-id="e9af9-110">The `sys.assembly_files` table contains the following columns.</span></span>  
  
|<span data-ttu-id="e9af9-111">列</span><span class="sxs-lookup"><span data-stu-id="e9af9-111">Column</span></span>|<span data-ttu-id="e9af9-112">说明</span><span class="sxs-lookup"><span data-stu-id="e9af9-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e9af9-113">assembly_id</span><span class="sxs-lookup"><span data-stu-id="e9af9-113">assembly_id</span></span>|<span data-ttu-id="e9af9-114">为程序集定义的标识符。</span><span class="sxs-lookup"><span data-stu-id="e9af9-114">The identifier defined for the assembly.</span></span> <span data-ttu-id="e9af9-115">此编号分配到与同一程序集相关的所有对象。</span><span class="sxs-lookup"><span data-stu-id="e9af9-115">This number is assigned to all objects relating to the same assembly.</span></span>|  
|<span data-ttu-id="e9af9-116">name</span><span class="sxs-lookup"><span data-stu-id="e9af9-116">name</span></span>|<span data-ttu-id="e9af9-117">对象的名称。</span><span class="sxs-lookup"><span data-stu-id="e9af9-117">The name of the object.</span></span>|  
|<span data-ttu-id="e9af9-118">file_id</span><span class="sxs-lookup"><span data-stu-id="e9af9-118">file_id</span></span>|<span data-ttu-id="e9af9-119">标识每个对象的编号，对于与给定的 `assembly_id` 关联的第一个对象，该值为 1。</span><span class="sxs-lookup"><span data-stu-id="e9af9-119">A number identifying each object, with the first object associated with a given `assembly_id` being given the value of 1.</span></span> <span data-ttu-id="e9af9-120">如果有多个对象与同一个 `assembly_id` 关联，则后续的每个对象的 `file_id` 值依次递增 1。</span><span class="sxs-lookup"><span data-stu-id="e9af9-120">If multiple objects are associated with the same `assembly_id`, then each subsequent `file_id` value is incremented by 1.</span></span>|  
|<span data-ttu-id="e9af9-121">内容</span><span class="sxs-lookup"><span data-stu-id="e9af9-121">content</span></span>|<span data-ttu-id="e9af9-122">程序集或文件的十六进制表示形式。</span><span class="sxs-lookup"><span data-stu-id="e9af9-122">The hexadecimal representation of the assembly or file.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="e9af9-123">本节内容</span><span class="sxs-lookup"><span data-stu-id="e9af9-123">In This Section</span></span>  
 [<span data-ttu-id="e9af9-124">创建程序集</span><span class="sxs-lookup"><span data-stu-id="e9af9-124">Creating an Assembly</span></span>](creating-an-assembly.md)  
 <span data-ttu-id="e9af9-125">介绍如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中创建 SAFE、EXTERNAL_ACCESS 和 UNSAFE CLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="e9af9-125">Discusses creating SAFE, EXTERNAL_ACCESS, and UNSAFE CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e9af9-126">改变程序集</span><span class="sxs-lookup"><span data-stu-id="e9af9-126">Altering an Assembly</span></span>](altering-an-assembly.md)  
 <span data-ttu-id="e9af9-127">介绍如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中更新 CLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="e9af9-127">Describes updating CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e9af9-128">删除程序集</span><span class="sxs-lookup"><span data-stu-id="e9af9-128">Dropping an Assembly</span></span>](dropping-an-assembly.md)  
 <span data-ttu-id="e9af9-129">介绍如何从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中删除 CLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="e9af9-129">Discusses dropping CLR assemblies from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9af9-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9af9-130">See Also</span></span>  
 <span data-ttu-id="e9af9-131">[CLR 集成安全性](../security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="e9af9-131">[CLR Integration Security](../security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="e9af9-132">CLR 集成代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="e9af9-132">CLR Integration Code Access Security</span></span>](../security/clr-integration-code-access-security.md)  
  
  
