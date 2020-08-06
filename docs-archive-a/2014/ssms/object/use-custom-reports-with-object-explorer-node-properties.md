---
title: 将自定义报表与对象资源管理器节点属性一起使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: c7b84355-71ba-402d-85af-23826f18b7da
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98701c091dc4729eec487e21102158a30ac369e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682637"
---
# <a name="use-custom-reports-with-object-explorer-node-properties"></a><span data-ttu-id="3a3a6-102">将自定义报表与对象资源管理器节点属性一起使用</span><span class="sxs-lookup"><span data-stu-id="3a3a6-102">Use Custom Reports with Object Explorer Node Properties</span></span>
  <span data-ttu-id="3a3a6-103">如果自定义报表引用所选对象资源管理器节点的报表参数，则将在此节点的上下文中执行自定义报表。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-103">Custom reports can execute in the context of a selected Object Explorer node if the custom reports reference the report parameters of that node.</span></span> <span data-ttu-id="3a3a6-104">这样，自定义报表可以使用当前上下文（如当前数据库）或者数据库或服务器对象。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-104">This enables a custom report to use the current context, for example the current database, or a database or server object.</span></span>  
  
  
## <a name="object-explorer-node-report-parameters"></a><span data-ttu-id="3a3a6-105">对象资源管理器节点的报表参数</span><span class="sxs-lookup"><span data-stu-id="3a3a6-105">Object Explorer Node Report Parameters</span></span>  
  
|<span data-ttu-id="3a3a6-106">参数名称</span><span class="sxs-lookup"><span data-stu-id="3a3a6-106">Parameter name</span></span>|<span data-ttu-id="3a3a6-107">数据类型</span><span class="sxs-lookup"><span data-stu-id="3a3a6-107">Data type</span></span>|  
|--------------------|---------------|  
|`ObjectName`|`String`|  
|`ObjectTypeName`|`String`|  
|`Filtered`|`Boolean`|  
|`ServerName`|`String`|  
|`FontName`|`String`|  
|`DatabaseName`|`String`|  
  
## <a name="object-explorer-node-report-parameters-example"></a><span data-ttu-id="3a3a6-108">对象资源管理器节点的报表参数示例</span><span class="sxs-lookup"><span data-stu-id="3a3a6-108">Object Explorer Node Report Parameters Example</span></span>  
 <span data-ttu-id="3a3a6-109">若要运行此示例，请按以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-109">To run the example, use the following procedure.</span></span>  
  
 <span data-ttu-id="3a3a6-110">**查看对象资源管理器中的节点的报表参数值**</span><span class="sxs-lookup"><span data-stu-id="3a3a6-110">**To view the report parameter values for a node in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="3a3a6-111">将以下示例代码复制到一个新文本文件中，然后在使用扩展名 .rdl 命名此文件。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-111">Copy the following sample code into a new text file and name the file by using an .rdl extension.</span></span>  
  
2.  <span data-ttu-id="3a3a6-112">将此报表文件复制到您在数据库服务器上为自定义报表创建的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-112">Copy the report file to a folder that you have created on the database server for custom reports.</span></span>  
  
3.  <span data-ttu-id="3a3a6-113">在中 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ，右键单击对象资源管理器中的节点，指向 "**报表**"，然后单击 "自定义报表"。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-113">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a node in Object Explorer, point to **Reports**, click Custom Reports.</span></span> <span data-ttu-id="3a3a6-114">在“打开文件”\*\*\*\* 对话框中，找到自定义报表文件夹并选择此报表文件，再单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-114">In the **Open File** dialog box, locate the custom reports folder and select the report file, and then click **Open**.</span></span>  
  
     <span data-ttu-id="3a3a6-115">第一次从对象资源管理器节点打开新的自定义报表时，该报表将添加到该节点的快捷菜单上“自定义报表”\*\*\*\* 下最近使用的文件列表中。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-115">When a new custom report is first opened from an Object Explorer node, the custom report is added to the most recently used list under **Custom Reports** on the shortcut menu of that node.</span></span> <span data-ttu-id="3a3a6-116">第一次打开标准报表时，该报表也将出现在“自定义报表”\*\*\*\* 下最近使用的文件列表中。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-116">When a standard report is opened for the first time, it will also appear on the most recently used list under **Custom Reports**.</span></span> <span data-ttu-id="3a3a6-117">如果某个自定义报表文件已删除，则下一次选择该项时，系统将提示您从最近使用的文件列表中删除该项。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-117">If a custom report file is deleted, the next time that the item is selected, a prompt will appear to delete the item from the most recently used list.</span></span>  
  
    1.  <span data-ttu-id="3a3a6-118">若要更改最近使用的文件列表中所显示的文件个数，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，展开“环境”\*\*\*\* 文件夹，再单击“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-118">To change the number of files displayed on the recently used list, on the **Tools** menu, click **Options**, expand the **Environment** folder, and then click **General**.</span></span>  
  
    2.  <span data-ttu-id="3a3a6-119">调整“显示最近使用列表中的文件”\*\*\*\* 的数量。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-119">Adjust the number for **Display files in recently used list**.</span></span>  
  
## <a name="custom-report-code-sample"></a><span data-ttu-id="3a3a6-120">自定义报表代码示例</span><span class="sxs-lookup"><span data-stu-id="3a3a6-120">Custom Report Code Sample</span></span>  
 <span data-ttu-id="3a3a6-121">使用以下代码创建的报表将使用与对象资源管理器节点关联的参数。</span><span class="sxs-lookup"><span data-stu-id="3a3a6-121">The report that is created by using the following code will use the parameters that are associated with an Object Explorer node.</span></span>  
  
 `<?xml version="1.0" encoding="utf-8"?>`  
  
 `<Report xmlns="https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition" xmlns:rd="https://schemas.microsoft.com/SQLServer/reporting/reportdesigner">`  
  
 `<ReportParameters>`  
  
 `<ReportParameter Name="ObjectName">`  
  
 `<DataType>String</DataType>`  
  
 `<Nullable>true</Nullable>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>ObjectName</Prompt>`  
  
 `</ReportParameter>`  
  
 `<ReportParameter Name="ObjectTypeName">`  
  
 `<DataType>String</DataType>`  
  
 `<Nullable>true</Nullable>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>ObjectTypeName</Prompt>`  
  
 `</ReportParameter>`  
  
 `<ReportParameter Name="Filtered">`  
  
 `<DataType>Boolean</DataType>`  
  
 `<Nullable>true</Nullable>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>Filtered</Prompt>`  
  
 `</ReportParameter>`  
  
 `<ReportParameter Name="ServerName">`  
  
 `<DataType>String</DataType>`  
  
 `<Nullable>true</Nullable>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>ServerName</Prompt>`  
  
 `</ReportParameter>`  
  
 `<ReportParameter Name="FontName">`  
  
 `<DataType>String</DataType>`  
  
 `<DefaultValue>`  
  
 `<Values>`  
  
 `<Value>Tahoma</Value>`  
  
 `</Values>`  
  
 `</DefaultValue>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>FontName</Prompt>`  
  
 `</ReportParameter>`  
  
 `<ReportParameter Name="DatabaseName">`  
  
 `<DataType>String</DataType>`  
  
 `<Nullable>true</Nullable>`  
  
 `<DefaultValue>`  
  
 `<Values>`  
  
 `<Value>master</Value>`  
  
 `</Values>`  
  
 `</DefaultValue>`  
  
 `<AllowBlank>true</AllowBlank>`  
  
 `<Prompt>DatabaseName</Prompt>`  
  
 `</ReportParameter>`  
  
 `</ReportParameters>`  
  
 `<DataSources>`  
  
 `<DataSource Name="AllReportParameters">`  
  
 `<ConnectionProperties>`  
  
 `<IntegratedSecurity>true</IntegratedSecurity>`  
  
 `<ConnectString>Data Source=.</ConnectString>`  
  
 `<DataProvider>SQL</DataProvider>`  
  
 `</ConnectionProperties>`  
  
 `<rd:DataSourceID>f1feee4c-0fdc-4301-9efa-3cd89eed2d9f</rd:DataSourceID>`  
  
 `</DataSource>`  
  
 `</DataSources>`  
  
 `<BottomMargin>1in</BottomMargin>`  
  
 `<RightMargin>1in</RightMargin>`  
  
 `<rd:DrawGrid>true</rd:DrawGrid>`  
  
 `<InteractiveWidth>8.5in</InteractiveWidth>`  
  
 `<rd:SnapToGrid>true</rd:SnapToGrid>`  
  
 `<Body>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox1">`  
  
 `<rd:DefaultName>textbox1</rd:DefaultName>`  
  
 `<ZIndex>1</ZIndex>`  
  
 `<Width>6in</Width>`  
  
 `<Style>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>20pt</FontSize>`  
  
 `<Color>SteelBlue</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Height>0.36in</Height>`  
  
 `<Value>AllReportParameters</Value>`  
  
 `</Textbox>`  
  
 `<Table Name="table1">`  
  
 `<DataSetName>AllReportParameters</DataSetName>`  
  
 `<Top>0.36in</Top>`  
  
 `<Details>`  
  
 `<TableRows>`  
  
 `<TableRow>`  
  
 `<TableCells>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="ObjectName">`  
  
 `<rd:DefaultName>ObjectName</rd:DefaultName>`  
  
 `<ZIndex>5</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!ObjectName.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="ObjectTypeName">`  
  
 `<rd:DefaultName>ObjectTypeName</rd:DefaultName>`  
  
 `<ZIndex>4</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!ObjectTypeName.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="Filtered">`  
  
 `<rd:DefaultName>Filtered</rd:DefaultName>`  
  
 `<ZIndex>3</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!Filtered.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="ServerName">`  
  
 `<rd:DefaultName>ServerName</rd:DefaultName>`  
  
 `<ZIndex>2</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!ServerName.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="FontName">`  
  
 `<rd:DefaultName>FontName</rd:DefaultName>`  
  
 `<ZIndex>1</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!FontName.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="DatabaseName">`  
  
 `<rd:DefaultName>DatabaseName</rd:DefaultName>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>=Parameters!DatabaseName.Value</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `</TableCells>`  
  
 `<Height>0.21in</Height>`  
  
 `</TableRow>`  
  
 `</TableRows>`  
  
 `</Details>`  
  
 `<Header>`  
  
 `<TableRows>`  
  
 `<TableRow>`  
  
 `<TableCells>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox2">`  
  
 `<rd:DefaultName>textbox2</rd:DefaultName>`  
  
 `<ZIndex>11</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>ObjectName</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox3">`  
  
 `<rd:DefaultName>textbox3</rd:DefaultName>`  
  
 `<ZIndex>10</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>ObjectTypeName</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox4">`  
  
 `<rd:DefaultName>textbox4</rd:DefaultName>`  
  
 `<ZIndex>9</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>Filtered</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox5">`  
  
 `<rd:DefaultName>textbox5</rd:DefaultName>`  
  
 `<ZIndex>8</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>ServerName</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox6">`  
  
 `<rd:DefaultName>textbox6</rd:DefaultName>`  
  
 `<ZIndex>7</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>FontName</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `<TableCell>`  
  
 `<ReportItems>`  
  
 `<Textbox Name="textbox7">`  
  
 `<rd:DefaultName>textbox7</rd:DefaultName>`  
  
 `<ZIndex>6</ZIndex>`  
  
 `<Style>`  
  
 `<BorderStyle>`  
  
 `<Default>Solid</Default>`  
  
 `</BorderStyle>`  
  
 `<PaddingLeft>2pt</PaddingLeft>`  
  
 `<PaddingBottom>2pt</PaddingBottom>`  
  
 `<FontFamily>Tahoma</FontFamily>`  
  
 `<FontWeight>700</FontWeight>`  
  
 `<FontSize>11pt</FontSize>`  
  
 `<BorderColor>`  
  
 `<Default>LightGrey</Default>`  
  
 `</BorderColor>`  
  
 `<BackgroundColor>SteelBlue</BackgroundColor>`  
  
 `<Color>White</Color>`  
  
 `<PaddingRight>2pt</PaddingRight>`  
  
 `<PaddingTop>2pt</PaddingTop>`  
  
 `</Style>`  
  
 `<CanGrow>true</CanGrow>`  
  
 `<Value>DatabaseName</Value>`  
  
 `</Textbox>`  
  
 `</ReportItems>`  
  
 `</TableCell>`  
  
 `</TableCells>`  
  
 `<Height>0.22in</Height>`  
  
 `</TableRow>`  
  
 `</TableRows>`  
  
 `<RepeatOnNewPage>true</RepeatOnNewPage>`  
  
 `</Header>`  
  
 `<TableColumns>`  
  
 `<TableColumn>`  
  
 `<Width>3in</Width>`  
  
 `</TableColumn>`  
  
 `<TableColumn>`  
  
 `<Width>1.5in</Width>`  
  
 `</TableColumn>`  
  
 `<TableColumn>`  
  
 `<Width>0.75in</Width>`  
  
 `</TableColumn>`  
  
 `<TableColumn>`  
  
 `<Width>1.125in</Width>`  
  
 `</TableColumn>`  
  
 `<TableColumn>`  
  
 `<Width>2in</Width>`  
  
 `</TableColumn>`  
  
 `<TableColumn>`  
  
 `<Width>1.375in</Width>`  
  
 `</TableColumn>`  
  
 `</TableColumns>`  
  
 `</Table>`  
  
 `</ReportItems>`  
  
 `<Height>0.79in</Height>`  
  
 `</Body>`  
  
 `<rd:ReportID>abb14e58-fd36-495a-89ff-b66f29ef287b</rd:ReportID>`  
  
 `<LeftMargin>1in</LeftMargin>`  
  
 `<DataSets>`  
  
 `<DataSet Name="AllReportParameters">`  
  
 `<Query>`  
  
 `<rd:UseGenericDesigner>true</rd:UseGenericDesigner>`  
  
 `<CommandText>SELECT 1`  
  
 `</CommandText>`  
  
 `<DataSourceName>AllReportParameters</DataSourceName>`  
  
 `</Query>`  
  
 `<Fields>`  
  
 `<Field Name="ObjectName">`  
  
 `<rd:TypeName>System.String</rd:TypeName>`  
  
 `<DataField>ObjectName</DataField>`  
  
 `</Field>`  
  
 `<Field Name="ObjectTypeName">`  
  
 `<rd:TypeName>System.String</rd:TypeName>`  
  
 `<DataField>ObjectTypeName</DataField>`  
  
 `</Field>`  
  
 `<Field Name="Filtered">`  
  
 `<rd:TypeName>System.Boolean</rd:TypeName>`  
  
 `<DataField>Filtered</DataField>`  
  
 `</Field>`  
  
 `<Field Name="ServerName">`  
  
 `<rd:TypeName>System.String</rd:TypeName>`  
  
 `<DataField>ServerName</DataField>`  
  
 `</Field>`  
  
 `<Field Name="FontName">`  
  
 `<rd:TypeName>System.String</rd:TypeName>`  
  
 `<DataField>FontName</DataField>`  
  
 `</Field>`  
  
 `<Field Name="DatabaseName">`  
  
 `<rd:TypeName>System.String</rd:TypeName>`  
  
 `<DataField>DatabaseName</DataField>`  
  
 `</Field>`  
  
 `</Fields>`  
  
 `</DataSet>`  
  
 `</DataSets>`  
  
 `<Width>6.875in</Width>`  
  
 `<InteractiveHeight>11in</InteractiveHeight>`  
  
 `<Language>en-US</Language>`  
  
 `<TopMargin>1in</TopMargin>`  
  
 `</Report>`  
  
## <a name="see-also"></a><span data-ttu-id="3a3a6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a3a6-122">See Also</span></span>  
 <span data-ttu-id="3a3a6-123">[Management Studio 中的自定义报表](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3a3a6-123">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="3a3a6-124">[将自定义报表添加到 Management Studio](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3a3a6-124">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 [<span data-ttu-id="3a3a6-125">启用运行自定义报表警告</span><span class="sxs-lookup"><span data-stu-id="3a3a6-125">Unsuppress Run Custom Report Warnings</span></span>](unsuppress-run-custom-report-warnings.md)  
  
  
