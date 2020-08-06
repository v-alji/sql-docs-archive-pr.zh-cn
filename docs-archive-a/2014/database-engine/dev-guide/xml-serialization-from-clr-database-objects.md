---
title: 从 CLR 数据库对象进行 XML 序列化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee93ee4b7bf9cba3f11b329244d4523636cb7704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690061"
---
# <a name="xml-serialization-from-clr-database-objects"></a><span data-ttu-id="2a396-102">从 CLR 数据库对象进行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="2a396-102">XML Serialization from CLR Database Objects</span></span>
  <span data-ttu-id="2a396-103">XML 序列化是以下两种情况所必需的：</span><span class="sxs-lookup"><span data-stu-id="2a396-103">XML serialization is required for two scenarios:</span></span>  
  
-   <span data-ttu-id="2a396-104">从公共语言运行时 (CLR) 对象调用 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="2a396-104">Invoking Web Services from common language runtime (CLR) objects.</span></span>  
  
-   <span data-ttu-id="2a396-105">将用户定义类型 (UDT) 转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="2a396-105">Converting a user-defined type (UDT) to XML.</span></span>  
  
 <span data-ttu-id="2a396-106">通过调用 `XmlSerializer` 类执行 XML 序列化通常将生成一个附加的序列化程序集，该程序集将重载到具有源程序集的项目中。</span><span class="sxs-lookup"><span data-stu-id="2a396-106">Performing XML serialization by invoking the `XmlSerializer` class normally generates an additional serialization assembly that is overloaded into the project with the source assembly.</span></span> <span data-ttu-id="2a396-107">但出于安全原因，此重载在 CLR 中被禁用。</span><span class="sxs-lookup"><span data-stu-id="2a396-107">However, for security purposes, this overload is disabled in the CLR.</span></span> <span data-ttu-id="2a396-108">因此，若要调用 web 服务或执行从 UDT 到 XML 的转换 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，必须使用一个名为 .NET Framework **Sgen.exe**的工具手动创建该程序集，该工具可生成所需的序列化程序集。</span><span class="sxs-lookup"><span data-stu-id="2a396-108">Therefore, to call a web service or perform conversion from UDT to XML inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly must be created manually using a tool called **Sgen.exe** provided with the .NET Framework that generates the necessary serialization assemblies.</span></span> <span data-ttu-id="2a396-109">在调用 `XmlSerializer` 时，必须通过以下步骤手动创建序列化程序集：</span><span class="sxs-lookup"><span data-stu-id="2a396-109">When invoking `XmlSerializer`, the serialization assembly must be created manually by following these steps:</span></span>  
  
1.  <span data-ttu-id="2a396-110">运行与 .NET Framework SDK 一起提供的**Sgen.exe**工具，以创建包含源程序集的 XML 序列化程序的程序集。</span><span class="sxs-lookup"><span data-stu-id="2a396-110">Run the **Sgen.exe** tool that is provided with the .NET Framework SDK to create the assembly containing the XML serializers for the source assembly.</span></span>  
  
2.  <span data-ttu-id="2a396-111">使用 `CREATE ASSEMBLY` 语句在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中注册生成的程序集。</span><span class="sxs-lookup"><span data-stu-id="2a396-111">Register the generated assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the `CREATE ASSEMBLY` statement.</span></span>  
  
 <span data-ttu-id="2a396-112">有关在执行 XML 序列化时可能收到的错误的信息，请参阅以下 Microsoft 支持部门文章： ["无法加载动态生成的序列化程序集"](https://support.microsoft.com/kb/913668)。</span><span class="sxs-lookup"><span data-stu-id="2a396-112">For information about errors that you may receive when performing XML serialization, see the following Microsoft Support article: ["Cannot load dynamically generated serialization assembly"](https://support.microsoft.com/kb/913668).</span></span>  
  
 <span data-ttu-id="2a396-113">有关 XML 序列化程序不支持的数据类型的信息，请参阅 .NET Framework 文档中的“.NET Framework 中 XML 架构的绑定支持”。</span><span class="sxs-lookup"><span data-stu-id="2a396-113">For information on data types that are not supported by XMLSerializer, see XML Schema Binding Support in the .NET Framework in the .NET Framework documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a396-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a396-114">See Also</span></span>  
 <span data-ttu-id="2a396-115">[从 CLR 数据库对象进行数据访问](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2a396-115">[Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="2a396-116">CREATE ASSEMBLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a396-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
