---
title: Transact-SQL 中的 OLE 自动化对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f36846565bb60fbf875e9babdabbb6d1667f5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591864"
---
# <a name="ole-automation-objects-in-transact-sql"></a><span data-ttu-id="e85ff-102">Transact-SQL 中的 OLE 自动化对象</span><span class="sxs-lookup"><span data-stu-id="e85ff-102">OLE Automation Objects in Transact-SQL</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e85ff-103">包括一些系统存储过程，这些存储过程允许在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理、存储过程和触发器中引用 OLE 自动化对象。</span><span class="sxs-lookup"><span data-stu-id="e85ff-103">includes several system stored procedures that allow OLE Automation objects to be referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, stored procedures, and triggers.</span></span> <span data-ttu-id="e85ff-104">这些系统存储过程作为扩展存储过程运行，而且通过存储过程执行的 OLE 自动化对象在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例的地址空间中的运行方式与扩展存储过程的运行方式相同。</span><span class="sxs-lookup"><span data-stu-id="e85ff-104">These system stored procedures run as extended stored procedures, and the OLE Automation objects that are executed through the stored procedures run in the address space of an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in the same way that an extended stored procedure runs.</span></span>  
  
 <span data-ttu-id="e85ff-105">OLE 自动化存储过程使 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批处理能够引用 SQL-DMO 对象和自定义 OLE 自动化对象，例如公开 **IDispatch** 接口的对象。</span><span class="sxs-lookup"><span data-stu-id="e85ff-105">The OLE Automation stored procedures enable [!INCLUDE[tsql](../../includes/tsql-md.md)] batches to reference SQL-DMO objects and custom OLE Automation objects, such as objects that expose the **IDispatch** interface.</span></span> <span data-ttu-id="e85ff-106">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 创建的自定义进程内 OLE 服务器必须有一个用于“Class_Initialize”和“Class_Terminate”子例程的错误处理程序（使用“On Error GoTo”语句指定） 。</span><span class="sxs-lookup"><span data-stu-id="e85ff-106">A custom in-process OLE server that is created by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] must have an error handler (specified with the **On Error GoTo** statement) for the **Class_Initialize** and **Class_Terminate** subroutines.</span></span> <span data-ttu-id="e85ff-107">**Class_Initialize** 子例程和 **Class_Terminate** 子例程中未处理的错误可能导致不可预知的错误，例如 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的访问冲突。</span><span class="sxs-lookup"><span data-stu-id="e85ff-107">Unhandled errors in the **Class_Initialize** and **Class_Terminate** subroutines can cause unpredictable errors, such as an access violation in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e85ff-108">建议其他子例程也有错误处理程序。</span><span class="sxs-lookup"><span data-stu-id="e85ff-108">Error handlers for other subroutines are also recommended.</span></span>  
  
 <span data-ttu-id="e85ff-109">当使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的 OLE 自动化对象时的第一个步骤就是调用 **sp_OACreate** 系统存储过程在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的地址空间中创建对象实例。</span><span class="sxs-lookup"><span data-stu-id="e85ff-109">The first step when using an OLE Automation object in [!INCLUDE[tsql](../../includes/tsql-md.md)] is to call the **sp_OACreate** system stored procedure to create an instance of the object in the address space of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="e85ff-110">创建了对象实例后，调用下列存储过程以使用与该对象相关的属性、方法和错误信息：</span><span class="sxs-lookup"><span data-stu-id="e85ff-110">After an instance of the object has been created, call the following stored procedures to work with the properties, methods, and error information related to the object:</span></span>  
  
-   <span data-ttu-id="e85ff-111">**sp_OAGetProperty** ，获取属性值。</span><span class="sxs-lookup"><span data-stu-id="e85ff-111">**sp_OAGetProperty** obtains the value of a property.</span></span>  
  
-   <span data-ttu-id="e85ff-112">**sp_OASetProperty** ，设置属性值。</span><span class="sxs-lookup"><span data-stu-id="e85ff-112">**sp_OASetProperty** sets the value of a property.</span></span>  
  
-   <span data-ttu-id="e85ff-113">**sp_OAMethod** ，调用方法。</span><span class="sxs-lookup"><span data-stu-id="e85ff-113">**sp_OAMethod** calls a method.</span></span>  
  
-   <span data-ttu-id="e85ff-114">**sp_OAGetErrorInfo** ，获取最新的错误信息。</span><span class="sxs-lookup"><span data-stu-id="e85ff-114">**sp_OAGetErrorInfo** obtains the most recent error information.</span></span>  
  
 <span data-ttu-id="e85ff-115">当不再需要对象时，调用 **sp_OADestroy** 释放使用 **sp_OACreate**创建的对象实例。</span><span class="sxs-lookup"><span data-stu-id="e85ff-115">When there is no more need for the object, call **sp_OADestroy** to deallocate the instance of the object created by using **sp_OACreate**.</span></span>  
  
 <span data-ttu-id="e85ff-116">OLE 自动化对象通过属性值和方法返回数据。</span><span class="sxs-lookup"><span data-stu-id="e85ff-116">OLE Automation objects return data through property values and methods.</span></span> <span data-ttu-id="e85ff-117">**sp_OAGetProperty** 和 **sp_OAMethod** 以结果集的形式返回这些数据值。</span><span class="sxs-lookup"><span data-stu-id="e85ff-117">**sp_OAGetProperty** and **sp_OAMethod** return these data values in the form of a result set.</span></span>  
  
 <span data-ttu-id="e85ff-118">OLE 自动化对象的作用域是一个批处理。</span><span class="sxs-lookup"><span data-stu-id="e85ff-118">The scope of an OLE Automation object is a batch.</span></span> <span data-ttu-id="e85ff-119">对该对象的所有引用都必须包含在单个批处理、存储过程或触发器中。</span><span class="sxs-lookup"><span data-stu-id="e85ff-119">All references to the object must be contained in a single batch, stored procedure, or trigger.</span></span>  
  
 <span data-ttu-id="e85ff-120">引用对象时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动化对象支持从引用的对象遍历至它包含的其他对象。</span><span class="sxs-lookup"><span data-stu-id="e85ff-120">When it references objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE Automation objects support traversing the referenced object to other objects that it contains.</span></span> <span data-ttu-id="e85ff-121">例如，在使用 SQL-DMO **SQLServer** 对象时，可以引用该服务器上包含的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="e85ff-121">For example, when using the SQL-DMO **SQLServer** object, references can be made to databases and tables contained on that server.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="e85ff-122">相关内容</span><span class="sxs-lookup"><span data-stu-id="e85ff-122">Related Content</span></span>  
 [<span data-ttu-id="e85ff-123">对象层次结构语法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-123">Object Hierarchy Syntax &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [<span data-ttu-id="e85ff-124">外围应用配置器</span><span class="sxs-lookup"><span data-stu-id="e85ff-124">Surface Area Configuration</span></span>](../security/surface-area-configuration.md)  
  
 [<span data-ttu-id="e85ff-125">Ole Automation Procedures 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="e85ff-125">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [<span data-ttu-id="e85ff-126">sp_OACreate (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-126">sp_OACreate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [<span data-ttu-id="e85ff-127">sp_OAGetProperty (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [<span data-ttu-id="e85ff-128">sp_OASetProperty (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-128">sp_OASetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [<span data-ttu-id="e85ff-129">sp_OAMethod (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-129">sp_OAMethod &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [<span data-ttu-id="e85ff-130">sp_OAGetErrorInfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [<span data-ttu-id="e85ff-131">sp_OADestroy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e85ff-131">sp_OADestroy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  
