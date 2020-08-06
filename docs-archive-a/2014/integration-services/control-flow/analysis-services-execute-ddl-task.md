---
title: Analysis Services 执行 DDL 任务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a75bae174c816cdabd07ce688e068cbadb016b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586911"
---
# <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="09264-102">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="09264-102">Analysis Services Execute DDL Task</span></span>
  <span data-ttu-id="09264-103">“ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 执行 DDL”任务运行数据定义语言 (DDL) 语句，这些语句可以创建、删除或更改挖掘模型和多维对象，如多维数据集和维度。</span><span class="sxs-lookup"><span data-stu-id="09264-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task runs data definition language (DDL) statements that can create, drop, or alter mining models and multidimensional objects such as cubes and dimensions.</span></span> <span data-ttu-id="09264-104">例如，DDL 语句可在 **Adventure Works** 多维数据集中创建分区，或删除 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]（即 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中包含的示例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库）中的维度。</span><span class="sxs-lookup"><span data-stu-id="09264-104">For example, a DDL statement can create a partition in the **Adventure Works** cube, or delete a dimension in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="09264-105">“ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 执行 DDL”任务使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="09264-105">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="09264-106">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="09264-106">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="09264-107">包含许多执行商业智能操作（如处理分析对象和运行数据挖掘预测查询）的任务。</span><span class="sxs-lookup"><span data-stu-id="09264-107">includes a number of tasks that perform business intelligence operations, such as processing analytic objects and running data mining prediction queries.</span></span>  
  
 <span data-ttu-id="09264-108">有关相关商业智能任务的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="09264-108">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="09264-109">Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="09264-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="09264-110">数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="09264-110">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="ddl-statements"></a><span data-ttu-id="09264-111">DDL 语句</span><span class="sxs-lookup"><span data-stu-id="09264-111">DDL Statements</span></span>  
 <span data-ttu-id="09264-112">DDL 语句表示为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 中的语句，并且嵌入 XML for Analysis (XMLA) 命令中。</span><span class="sxs-lookup"><span data-stu-id="09264-112">The DDL statements are represented as statements in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL), and framed in an XML for Analysis (XMLA) command.</span></span>  
  
-   <span data-ttu-id="09264-113">ASSL 用于定义和说明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例及其包含的数据库和数据库对象。</span><span class="sxs-lookup"><span data-stu-id="09264-113">ASSL is used to define and describe an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and the databases and database objects it contains.</span></span> <span data-ttu-id="09264-114">有关详细信息，请参阅[Analysis Services 脚本语言 &#40;ASSL&#41; 引用](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="09264-114">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
-   <span data-ttu-id="09264-115">XMLA 是用于向 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例发送操作命令（如 Create、Alter 或 Process）的命令语言。</span><span class="sxs-lookup"><span data-stu-id="09264-115">XMLA is a command language that is used to send action commands, such as Create, Alter, or Process, to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="09264-116">有关详细信息，请参阅 [XML for Analysis (XMLA) 参考](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)。</span><span class="sxs-lookup"><span data-stu-id="09264-116">For more information, see [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="09264-117">如果 DDL 代码存储在单独的文件中，则“ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 执行 DDL”任务使用文件连接管理器来指定该文件的路径。</span><span class="sxs-lookup"><span data-stu-id="09264-117">If the DDL code is stored in a separate file, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses a File connection manager to specify the path of the file.</span></span> <span data-ttu-id="09264-118">有关详细信息，请参阅 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="09264-118">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="09264-119">因为 DDL 语句可以包含密码和其他敏感信息，所以包含一个或多个“[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 执行 DDL”任务的包应该使用包保护级别 `EncryptAllWithUserKey` 或 `EncryptAllWithPassword`。</span><span class="sxs-lookup"><span data-stu-id="09264-119">Because DDL statements can contain passwords and other sensitive information, a package that contains one or more [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL tasks should use the package protection level `EncryptAllWithUserKey` or `EncryptAllWithPassword`.</span></span> <span data-ttu-id="09264-120">有关详细信息，请参阅 [Integration Services (SSIS) 包](../integration-services-ssis-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="09264-120">For more information, see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md).</span></span>  
  
### <a name="ddl-examples"></a><span data-ttu-id="09264-121">DDL 示例</span><span class="sxs-lookup"><span data-stu-id="09264-121">DDL Examples</span></span>  
 <span data-ttu-id="09264-122">以下三个 DDL 语句是通过对 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]（包含在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库）中的对象编写脚本而生成。</span><span class="sxs-lookup"><span data-stu-id="09264-122">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="09264-123">下面的 DDL 语句删除 **Promotion** 维度。</span><span class="sxs-lookup"><span data-stu-id="09264-123">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="09264-124">以下 DDL 语句处理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="09264-124">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="09264-125">下面的 DDL 语句创建 **Forecasting** 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="09264-125">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 <span data-ttu-id="09264-126">以下三个 DDL 语句是通过对 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]（包含在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库）中的对象编写脚本而生成。</span><span class="sxs-lookup"><span data-stu-id="09264-126">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="09264-127">下面的 DDL 语句删除 **Promotion** 维度。</span><span class="sxs-lookup"><span data-stu-id="09264-127">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="09264-128">以下 DDL 语句处理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="09264-128">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="09264-129">下面的 DDL 语句创建 **Forecasting** 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="09264-129">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="09264-130">“Analysis Services 执行 DDL”任务的配置</span><span class="sxs-lookup"><span data-stu-id="09264-130">Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="09264-131">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="09264-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="09264-132">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="09264-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="09264-133">Analysis Services 执行 DDL 任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="09264-133">Analysis Services Execute DDL Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="09264-134">Analysis Services 执行 DDL 任务编辑器（DDL 页）</span><span class="sxs-lookup"><span data-stu-id="09264-134">Analysis Services Execute DDL Task Editor &#40;DDL Page&#41;</span></span>](../analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [<span data-ttu-id="09264-135">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="09264-135">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="09264-136">有关在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="09264-136">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="09264-137">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="09264-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="09264-138">“Analysis Services 执行 DDL”任务的编程配置</span><span class="sxs-lookup"><span data-stu-id="09264-138">Programmatic Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="09264-139">有关以编程方式设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="09264-139">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
