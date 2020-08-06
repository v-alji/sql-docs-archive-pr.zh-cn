---
title: OLE DB 命令转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6b0498d0ae5fa61a00cc7f6fc89e4dc506cd25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694552"
---
# <a name="ole-db-command-transformation"></a><span data-ttu-id="907fb-102">OLE DB 命令转换</span><span class="sxs-lookup"><span data-stu-id="907fb-102">OLE DB Command Transformation</span></span>
  <span data-ttu-id="907fb-103">OLE DB 命令转换对数据流中的每一行运行一条 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="907fb-103">The OLE DB Command transformation runs an SQL statement for each row in a data flow.</span></span> <span data-ttu-id="907fb-104">例如，您可以运行 SQL 语句以在数据库表中插入、更新或删除行。</span><span class="sxs-lookup"><span data-stu-id="907fb-104">For example, you can run an SQL statement that inserts, updates, or deletes rows in a database table.</span></span>  
  
 <span data-ttu-id="907fb-105">可以按下列方式配置 OLE DB 命令转换：</span><span class="sxs-lookup"><span data-stu-id="907fb-105">You can configure the OLE DB Command Transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="907fb-106">提供转换为每一行所运行的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="907fb-106">Provide the SQL statement that the transformation runs for each row.</span></span>  
  
-   <span data-ttu-id="907fb-107">指定一个秒数，到此秒数该 SQL 语句即告超时。</span><span class="sxs-lookup"><span data-stu-id="907fb-107">Specify the number of seconds before the SQL statement times out.</span></span>  
  
-   <span data-ttu-id="907fb-108">指定默认的代码页。</span><span class="sxs-lookup"><span data-stu-id="907fb-108">Specify the default code page.</span></span>  
  
 <span data-ttu-id="907fb-109">通常，所运行的 SQL 语句会包含一些参数。</span><span class="sxs-lookup"><span data-stu-id="907fb-109">Typically, the SQL statement includes parameters.</span></span> <span data-ttu-id="907fb-110">参数值存储在转换输入的外部列中，将输入列映射到外部列便可将输入列映射到参数。</span><span class="sxs-lookup"><span data-stu-id="907fb-110">The parameter values are stored in external columns in the transformation input, and mapping an input column to an external column maps an input column to a parameter.</span></span> <span data-ttu-id="907fb-111">例如，若要按 **ProductKey** 列中的值在 **DimProduct** 表中查找行，然后删除这些行，可将名为 **Param_0** 的外部列映射到名为 **ProductKey** 的输入列，然后再运行 SQL 语句 `DELETE FROM DimProduct WHERE ProductKey = ?`。</span><span class="sxs-lookup"><span data-stu-id="907fb-111">For example, to locate rows in the **DimProduct** table by the value in their **ProductKey** column and then delete them, you can map the external column named **Param_0** to the input column named **ProductKey,** and then run the SQL statement `DELETE FROM DimProduct WHERE ProductKey = ?`..</span></span> <span data-ttu-id="907fb-112">OLE DB 命令转换提供参数的名称，这些参数名不可修改。</span><span class="sxs-lookup"><span data-stu-id="907fb-112">The OLE DB Command transformation provides the parameter names and you cannot modify them.</span></span> <span data-ttu-id="907fb-113">参数名的形式为 **Param_0**、 **Param_1**等，依此类推。</span><span class="sxs-lookup"><span data-stu-id="907fb-113">The parameter names are **Param_0**, **Param_1**, and so on.</span></span>  
  
 <span data-ttu-id="907fb-114">如果使用 **“高级编辑器”** 对话框配置 OLE DB 命令转换，单击 **“刷新”** 按钮便可将 SQL 语句中的参数自动映射到转换输入中的外部列，并定义每个参数的特征。</span><span class="sxs-lookup"><span data-stu-id="907fb-114">If you configure the OLE DB Command transformation by using the **Advanced Editor** dialog box, the parameters in the SQL statement may be mapped automatically to external columns in the transformation input, and the characteristics of each parameter defined, by clicking the **Refresh** button.</span></span> <span data-ttu-id="907fb-115">但是，如果 OLE DB 命令转换所使用的 OLE DB 访问接口不支持从参数派生参数信息，则必须手动配置外部列。</span><span class="sxs-lookup"><span data-stu-id="907fb-115">However, if the OLE DB provider that the OLE DB Command transformation uses does not support deriving parameter information from the parameter, you must configure the external columns manually.</span></span> <span data-ttu-id="907fb-116">这意味着对每个参数，必须在转换的外部输入中添加一列，用类似 **Param_0**的名称更新列名，指定 DBParamInfoFlags 属性的值，并将包含参数值的输入列映射到这些外部列。</span><span class="sxs-lookup"><span data-stu-id="907fb-116">This means that you must add a column for each parameter to the external input to the transformation, update the column names to use names like **Param_0**, specify the value of the DBParamInfoFlags property, and map the input columns that contain parameter values to the external columns.</span></span>  
  
 <span data-ttu-id="907fb-117">DBParamInfoFlags 的值表示参数的特征。</span><span class="sxs-lookup"><span data-stu-id="907fb-117">The value of DBParamInfoFlags represents the characteristics of the parameter.</span></span> <span data-ttu-id="907fb-118">例如，值 **1** 指定参数为输入参数，而值 **65** 则指定参数为输入参数，且可能包含空值。</span><span class="sxs-lookup"><span data-stu-id="907fb-118">For example, the value **1** specifies that the parameter is an input parameter, and the value **65** specifies that the parameter is an input parameter and may contain a null value.</span></span> <span data-ttu-id="907fb-119">该值必须与 OLE DB DBPARAMFLAGSENUM 枚举中包含的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="907fb-119">The values must match the values in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="907fb-120">有关详细信息，请参阅 OLE DB 参考文档。</span><span class="sxs-lookup"><span data-stu-id="907fb-120">For more information, see the OLE DB reference documentation.</span></span>  
  
 <span data-ttu-id="907fb-121">OLE DB 命令转换包括 `SQLCommand` 自定义属性。</span><span class="sxs-lookup"><span data-stu-id="907fb-121">The OLE DB Command transformation includes the `SQLCommand` custom property.</span></span> <span data-ttu-id="907fb-122">加载包时，可以通过属性表达式更新此属性。</span><span class="sxs-lookup"><span data-stu-id="907fb-122">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="907fb-123">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../expressions/use-property-expressions-in-packages.md)和[转换自定义属性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="907fb-123">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="907fb-124">此转换有一个输入、一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="907fb-124">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="907fb-125">日志记录</span><span class="sxs-lookup"><span data-stu-id="907fb-125">Logging</span></span>  
 <span data-ttu-id="907fb-126">可以记录 OLE DB 命令转换对外部数据访问接口所做的调用。</span><span class="sxs-lookup"><span data-stu-id="907fb-126">You can log the calls that the OLE DB Command transformation makes to external data providers.</span></span> <span data-ttu-id="907fb-127">利用此日志记录功能，可以排除 OLE DB 命令转换对外部数据源执行的连接和命令中发生的故障。</span><span class="sxs-lookup"><span data-stu-id="907fb-127">You can use this logging capability to troubleshoot the connections and commands to external data sources that the OLE DB Command transformation performs.</span></span> <span data-ttu-id="907fb-128">若要记录 OLE DB 命令转换对外部数据访问接口所做的调用，请在包级别启用包日志记录并选择 **“诊断”** 事件。</span><span class="sxs-lookup"><span data-stu-id="907fb-128">To log the calls that the OLE DB Command transformation makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="907fb-129">有关详细信息，请参阅 [包执行的疑难解答工具](../../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="907fb-129">For more information, see [Troubleshooting Tools for Package Execution](../../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="907fb-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="907fb-130">Related Tasks</span></span>  
 <span data-ttu-id="907fb-131">可通过使用 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或对象模型配置转换。</span><span class="sxs-lookup"><span data-stu-id="907fb-131">You can configure the transformation by either using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or the object model.</span></span> <span data-ttu-id="907fb-132">有关使用 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器配置转换的详细信息，请参阅  [配置 OLE DB 命令转换](../../configure-the-ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="907fb-132">For details about configuring the transformation using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer, see  [Configure the OLE DB Command Transformation](../../configure-the-ole-db-command-transformation.md).</span></span> <span data-ttu-id="907fb-133">有关以编程方式配置此转换的详细信息，请参阅开发人员指南。</span><span class="sxs-lookup"><span data-stu-id="907fb-133">See the Developer Guide for details about programmatically configuring this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907fb-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="907fb-134">See Also</span></span>  
 <span data-ttu-id="907fb-135">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="907fb-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="907fb-136">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="907fb-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
