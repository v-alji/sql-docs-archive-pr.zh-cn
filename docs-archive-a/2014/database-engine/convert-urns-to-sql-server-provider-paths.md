---
title: 将 URN 转换为 SQL Server 提供程序路径 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 56c2fdb5f84e57fe3f34348108f14418785659a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586965"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a><span data-ttu-id="ccd29-102">将 URN 转换为 SQL Server 提供程序路径</span><span class="sxs-lookup"><span data-stu-id="ccd29-102">Convert URNs to SQL Server Provider Paths</span></span>
  <span data-ttu-id="ccd29-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理对象模型 (SMO) 为其对象生成统一资源名称 (URN)。</span><span class="sxs-lookup"><span data-stu-id="ccd29-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object model (SMO) builds Uniform Resource Names (URN) for its objects.</span></span> <span data-ttu-id="ccd29-104">每个 URN 都唯一标识一个 SMO 对象，并且可通过使用 `Convert-UrnToPath` cmdlet 转换为 SQL Server PowerShell 提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="ccd29-104">Each URN uniquely identifies a SMO object, and can be converted to a SQL Server PowerShell provider path by using the `Convert-UrnToPath` cmdlet.</span></span>  
  
## <a name="converting-urns-to-paths"></a><span data-ttu-id="ccd29-105">将 URN 转换为路径</span><span class="sxs-lookup"><span data-stu-id="ccd29-105">Converting URNs to Paths</span></span>  
 <span data-ttu-id="ccd29-106">每个对象的 URN 都有与其路径相同的信息，但是它们的格式有所不同。</span><span class="sxs-lookup"><span data-stu-id="ccd29-106">Each URN has the same information as a path to the object, but in a different form.</span></span> <span data-ttu-id="ccd29-107">例如，下面是一个表的路径：</span><span class="sxs-lookup"><span data-stu-id="ccd29-107">For example, this is the path to a table:</span></span>  
  
 <span data-ttu-id="ccd29-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span><span class="sxs-lookup"><span data-stu-id="ccd29-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span></span>  
  
 <span data-ttu-id="ccd29-109">下面是同一个对象的 URN：</span><span class="sxs-lookup"><span data-stu-id="ccd29-109">And this is the URN to the same object:</span></span>  
  
 <span data-ttu-id="ccd29-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span><span class="sxs-lookup"><span data-stu-id="ccd29-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span></span>  
  
 <span data-ttu-id="ccd29-111">如果您已在 PowerShell 脚本中创建了一个 SMO 对象，则可以引用 `Urn` 属性以便获取该对象的 URN，然后使用 `Convert-UrnToPath` cmdlet 将 SMO URN 字符串转换为 Windows PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="ccd29-111">If you have created a SMO object in a PowerShell script, you can reference the `Urn` property to get the URN for the object, and then use the `Convert-UrnToPath` cmdlet to convert the SMO URN string to a Windows PowerShell path.</span></span> <span data-ttu-id="ccd29-112">您然后可以使用该提供程序导航到路径上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="ccd29-112">You can then use the provider to navigate to different locations on the path.</span></span>  
  
 <span data-ttu-id="ccd29-113">如果节点名称中包含 Windows PowerShell 路径名称中不支持的扩展字符，`Convert-UrnToPath` 会用这些字符的十六进制表示形式来对它们进行编码。</span><span class="sxs-lookup"><span data-stu-id="ccd29-113">If node names contain extended characters that are not supported in Windows PowerShell path names, `Convert-UrnToPath` encodes them in their hexadecimal representation.</span></span> <span data-ttu-id="ccd29-114">例如，“My:Table”以“My%3ATable”形式返回。</span><span class="sxs-lookup"><span data-stu-id="ccd29-114">For example "My:Table" is returned as "My%3ATable".</span></span>  
  
 <span data-ttu-id="ccd29-115">有关在 Windows PowerShell 中使用 cmdlet 的示例，请运行：</span><span class="sxs-lookup"><span data-stu-id="ccd29-115">For examples of using the cmdlet, in Windows PowerShell, run:</span></span>  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccd29-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccd29-116">See Also</span></span>  
 <span data-ttu-id="ccd29-117">[查询表达式和统一资源名称](../powershell/query-expressions-and-uniform-resource-names.md) </span><span class="sxs-lookup"><span data-stu-id="ccd29-117">[Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md) </span></span>  
 <span data-ttu-id="ccd29-118">[SQL Server PowerShell 提供程序](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="ccd29-118">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="ccd29-119">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccd29-119">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
