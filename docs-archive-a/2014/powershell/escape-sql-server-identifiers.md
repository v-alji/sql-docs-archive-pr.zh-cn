---
title: 对 SQL Server 标识符进行转义 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586757"
---
# <a name="escape-sql-server-identifiers"></a><span data-ttu-id="6f416-102">对 SQL Server 标识符进行转义</span><span class="sxs-lookup"><span data-stu-id="6f416-102">Escape SQL Server Identifiers</span></span>
  <span data-ttu-id="6f416-103">通常，可以使用 Windows PowerShell 反引号转义符 (\`) 来对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 分隔标识符中允许使用但是 Windows PowerShell 路径名称中不允许使用的字符进行转义。</span><span class="sxs-lookup"><span data-stu-id="6f416-103">You can often use the Windows PowerShell back-tick escape character (\`) to escape characters that are allowed in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] delimited identifiers but not Windows PowerShell path names.</span></span> <span data-ttu-id="6f416-104">但是，对于某些字符，不能对其进行转义。</span><span class="sxs-lookup"><span data-stu-id="6f416-104">Some characters, however, cannot be escaped.</span></span> <span data-ttu-id="6f416-105">例如，不能对 Windows PowerShell 中的冒号字符 (:) 进行转义。</span><span class="sxs-lookup"><span data-stu-id="6f416-105">For example, you cannot escape the colon character (:) in Windows PowerShell.</span></span> <span data-ttu-id="6f416-106">必须对包含该字符的标识符进行编码。</span><span class="sxs-lookup"><span data-stu-id="6f416-106">Identifiers with that character must be encoded.</span></span> <span data-ttu-id="6f416-107">由于编码适用于所有字符，因此编码比转义可靠。</span><span class="sxs-lookup"><span data-stu-id="6f416-107">Encoding is more reliable than escaping because encoding works for all characters.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="6f416-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="6f416-108">Before You Begin</span></span>  
 <span data-ttu-id="6f416-109">反引号字符 (\`) 键通常位于键盘左上角 ESC 键的下方。</span><span class="sxs-lookup"><span data-stu-id="6f416-109">The back-tick character (\`) is usually on the key in the upper left of the keyboard, under the ESC key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6f416-110">示例</span><span class="sxs-lookup"><span data-stu-id="6f416-110">Examples</span></span>  
 <span data-ttu-id="6f416-111">下面是对 # 字符进行转义的示例：</span><span class="sxs-lookup"><span data-stu-id="6f416-111">This is an example of escaping a # character:</span></span>  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 <span data-ttu-id="6f416-112">下面是在（本地）指定为计算机名称时对括号进行转义的示例：</span><span class="sxs-lookup"><span data-stu-id="6f416-112">This is an example of escaping the parenthesis when specifying (local) as a computer name:</span></span>  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f416-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f416-113">See Also</span></span>  
 <span data-ttu-id="6f416-114">[SQL Server PowerShell 中的标识符](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="6f416-114">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="6f416-115">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="6f416-115">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="6f416-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f416-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
