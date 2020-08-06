---
title: 快速信息 (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f173c57438301702a8e51acf4531c655fde0cc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694436"
---
# <a name="quick-info-intellisense"></a><span data-ttu-id="a1077-102">快速信息 (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="a1077-102">Quick Info (IntelliSense)</span></span>
  <span data-ttu-id="a1077-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **“快速信息”** 选项可显示代码中任何标识符的完整声明。</span><span class="sxs-lookup"><span data-stu-id="a1077-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Quick Info** option displays the complete declaration for any identifier in your code.</span></span> <span data-ttu-id="a1077-104">将鼠标指针移到标识符上时，该标识符的声明便会显示在一个黄色的弹出窗口中。</span><span class="sxs-lookup"><span data-stu-id="a1077-104">When you move the mouse pointer over an identifier, its declaration is displayed in a yellow pop-up window.</span></span> <span data-ttu-id="a1077-105">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，数据库引擎和 XML 查询编辑器中都提供 **“快速信息”** 。</span><span class="sxs-lookup"><span data-stu-id="a1077-105">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Quick Info** is available in the Database Engine and XML Query Editors.</span></span>  
  
## <a name="transact-sql-quick-info"></a><span data-ttu-id="a1077-106">Transact-SQL 快速信息</span><span class="sxs-lookup"><span data-stu-id="a1077-106">Transact-SQL Quick Info</span></span>  
 <span data-ttu-id="a1077-107">**“快速信息”** 在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中显示两类信息。</span><span class="sxs-lookup"><span data-stu-id="a1077-107">**Quick Info** displays two types of information in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="a1077-108">如果未处于调试模式， **“快速信息”** 显示表达式声明。</span><span class="sxs-lookup"><span data-stu-id="a1077-108">When not in debug mode, **Quick Info** displays the expression declaration.</span></span> <span data-ttu-id="a1077-109">如果处于调试模式， **“快速信息”** 则会显示表达式的名称及其当前值。</span><span class="sxs-lookup"><span data-stu-id="a1077-109">When in debug mode, **Quick Info** instead displays the name of the expression and its current value.</span></span>  
  
 <span data-ttu-id="a1077-110">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中，只有 IntelliSense 支持的那些 **语法部分才能使用** “快速信息” [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a1077-110">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, **Quick Info** is available only for those parts of the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that IntelliSense supports.</span></span> <span data-ttu-id="a1077-111">例如，如果将鼠标指针移到某个对象的标识符上，但 IntelliSense 不支持该对象的数据类型，则“快速信息”  弹出窗口会包含一条消息，说明不支持该数据类型。</span><span class="sxs-lookup"><span data-stu-id="a1077-111">For example, if you move the mouse pointer over the identifier for an object that has a data type that IntelliSense does not support, the **Quick Info** pop-up window contains a message that states that the data type is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1077-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1077-112">See Also</span></span>  
 [<span data-ttu-id="a1077-113">IntelliSense 支持的 Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="a1077-113">Transact-SQL Syntax Supported by IntelliSense</span></span>](transact-sql-syntax-supported-by-intellisense.md)  
  
  
