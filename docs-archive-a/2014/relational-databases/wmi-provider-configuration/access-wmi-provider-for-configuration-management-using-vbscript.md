---
title: 使用 VBScript 修改 SQL Server 服务高级属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cf722b00a31723b77624c33fef81a82ff0cb926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591155"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a><span data-ttu-id="b88cd-102">使用 VBScript 修改 SQL Server 服务高级属性</span><span class="sxs-lookup"><span data-stu-id="b88cd-102">Modify SQL Server Service Advanced Properties using VBScript</span></span>
  <span data-ttu-id="b88cd-103">本部分介绍如何创建一个 VBScript 程序，用于列出 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 计算机上运行的已安装实例的版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b88cd-103">This section describes how to create a VBScript program that lists the version of installed instances of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are running on a computer.</span></span>  
  
 <span data-ttu-id="b88cd-104">代码示例列出了运行在计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例及其版本。</span><span class="sxs-lookup"><span data-stu-id="b88cd-104">The code example lists the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer and its version.</span></span>  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a><span data-ttu-id="b88cd-105">列出 SQL Server 的已安装实例的名称和版本</span><span class="sxs-lookup"><span data-stu-id="b88cd-105">Listing name and version of installed instances of SQL Server</span></span>  
  
1.  <span data-ttu-id="b88cd-106">在文本编辑器（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 记事本）中，打开一个新文档。</span><span class="sxs-lookup"><span data-stu-id="b88cd-106">Open a new document in a text editor, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Notepad.</span></span> <span data-ttu-id="b88cd-107">复制采用此过程的代码，并用 .vbs 扩展名保存该文件。</span><span class="sxs-lookup"><span data-stu-id="b88cd-107">Copy the code that follows this procedure and save the file with a .vbs extension.</span></span> <span data-ttu-id="b88cd-108">此示例名为 test.vbs。</span><span class="sxs-lookup"><span data-stu-id="b88cd-108">This example is called test.vbs.</span></span>  
  
2.  <span data-ttu-id="b88cd-109">连接到 WMI 提供程序的实例，以便使用 VBScript `GetObject` 函数进行计算机管理。</span><span class="sxs-lookup"><span data-stu-id="b88cd-109">Connect to an instance of the WMI Provider for Computer Management with the VBScript `GetObject` function.</span></span> <span data-ttu-id="b88cd-110">此示例连接到名为 mpc 的远程计算机，但在连接本地计算机时省略了计算机名称 winmgmts:root\Microsoft\SqlServer\ComputerManagement。</span><span class="sxs-lookup"><span data-stu-id="b88cd-110">This example connects to a remote computer named mpc, but omit the computer name to connect to the local computer: winmgmts:root\Microsoft\SqlServer\ComputerManagement.</span></span> <span data-ttu-id="b88cd-111">有关 `GetObject` 函数的详细信息，请参阅 VBScript 参考。</span><span class="sxs-lookup"><span data-stu-id="b88cd-111">For more information about the `GetObject` function, see the VBScript reference.</span></span>  
  
3.  <span data-ttu-id="b88cd-112">使用 `InstancesOf` 方法枚举一组服务。</span><span class="sxs-lookup"><span data-stu-id="b88cd-112">Use the `InstancesOf` method to enumerate a list of the services.</span></span> <span data-ttu-id="b88cd-113">还可以使用简单的 WQL 查询和 `ExecQuery` 方法代替 `InstancesOf` 方法枚举这些服务。</span><span class="sxs-lookup"><span data-stu-id="b88cd-113">The services can also be enumerated by using a simple WQL query and an `ExecQuery` method instead of the `InstancesOf` method.</span></span>  
  
4.  <span data-ttu-id="b88cd-114">使用 `ExecQuery` 方法和 WQL 查询检索 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已安装实例的名称和版本。</span><span class="sxs-lookup"><span data-stu-id="b88cd-114">Use the `ExecQuery` method and a WQL query to retrieve the name and version of the installed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="b88cd-115">保存文件。</span><span class="sxs-lookup"><span data-stu-id="b88cd-115">Save the file.</span></span>  
  
6.  <span data-ttu-id="b88cd-116">`cscript test.vbs`在命令提示符处键入以运行脚本。</span><span class="sxs-lookup"><span data-stu-id="b88cd-116">Run the script by typing `cscript test.vbs` at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b88cd-117">示例</span><span class="sxs-lookup"><span data-stu-id="b88cd-117">Example</span></span>  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
