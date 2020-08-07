---
title: 对类型 xs： dateTime、xs： date 和 xs： time 的存储格式的更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xs:date
- xs:time
- storage format
- DateTime
ms.assetid: b9f758df-030c-4aec-8ade-1bf904aa2c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e1ad0b80ee6963dde4b906a38c72e5c0fd8bab72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586212"
---
# <a name="changes-to-the-storage-format-for-types-xsdatetime-xsdate-and-xstime"></a><span data-ttu-id="4adf4-102">xs:dateTime、xs:date 和 xs:time 类型的存储格式发生更改</span><span class="sxs-lookup"><span data-stu-id="4adf4-102">Changes to the storage format for types xs:dateTime, xs:date, and xs:time</span></span>
  <span data-ttu-id="4adf4-103">XMLDATETIME 规则可确定您的数据库是否包含在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后将变为无效的类型化 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="4adf4-103">The XMLDATETIME rule identifies whether or not your databases contain typed XML data that will become invalid after upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="4adf4-104">组件</span><span class="sxs-lookup"><span data-stu-id="4adf4-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4adf4-105">说明</span><span class="sxs-lookup"><span data-stu-id="4adf4-105">Description</span></span>  
 <span data-ttu-id="4adf4-106">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]类型为 xs： dateTime、xs： date 和 xs： time 的存储格式已更改为支持带有或不带时区信息的值，并允许保留时区。</span><span class="sxs-lookup"><span data-stu-id="4adf4-106">The storage format in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for types xs:dateTime, xs:date, and xs:time has been changed to support values with or without time zone information and to allow for preservation of the time zone.</span></span>  
  
 <span data-ttu-id="4adf4-107">如果一个 XML 架构集合引用了上述某一类型，则在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后，将会禁用与此集合关联的所有列的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4adf4-107">If an XML Schema Collection references one of those types, XML indexes on all columns that are associated with the collection will be disabled after upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4adf4-108">您将可以使用 SELECT 和/或 XQUERIES 查询它们，但无法使用相应的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4adf4-108">You will be able to query them by using SELECT and/or XQUERIES, but the XML index will not be used.</span></span> <span data-ttu-id="4adf4-109">如果遇到负年份值，将会造成运行时错误。</span><span class="sxs-lookup"><span data-stu-id="4adf4-109">If a negative year value is encountered, a runtime error will result.</span></span>  
  
 <span data-ttu-id="4adf4-110">此外，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 不支持含负年份的值。</span><span class="sxs-lookup"><span data-stu-id="4adf4-110">Additionally, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] does not support values with negative years.</span></span>  
  
 <span data-ttu-id="4adf4-111">XMLDATETIME 规则会检查是否有任何 XML 架构集合引用其中一个受影响的类型以及是否有任何 XML 列由此类集合类型化。</span><span class="sxs-lookup"><span data-stu-id="4adf4-111">The XMLDATETIME rule checks if any of your XML Schema Collections reference one of the affected types and if there are any XML columns typed by such collections.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4adf4-112">纠正措施</span><span class="sxs-lookup"><span data-stu-id="4adf4-112">Corrective Action</span></span>  
 <span data-ttu-id="4adf4-113">如果 XMLDATETIME 规则确认您的一些 XML 列是根据引用 xs:date、xs:time 或 xs:dateTime 的架构集合类型化的，则您必须先确定数据中是否有任何包含负年份的值。</span><span class="sxs-lookup"><span data-stu-id="4adf4-113">If the XMLDATETIME rule confirms that you have XML columns typed according to a schema collection that references xs:date, xs:time or xs:dateTime, you must first find out whether or not there are any values with negative years in your data.</span></span> <span data-ttu-id="4adf4-114">如果存在这样的值，则在升级之后，您将无法重新生成 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4adf4-114">The presence of such values would prevent you from rebuilding your XML indexes after upgrading.</span></span>  
  
 <span data-ttu-id="4adf4-115">下面的查询将搜索引用受影响类型的 XML 架构集合并搜索每个类型化的 XML 列。</span><span class="sxs-lookup"><span data-stu-id="4adf4-115">The following query will search for XML schema collections that reference the affected types and for each typed XML column.</span></span> <span data-ttu-id="4adf4-116">这样，您就会知道是否存在含负年份值的实例。</span><span class="sxs-lookup"><span data-stu-id="4adf4-116">This will tell you whether or not there are instances with negative year values.</span></span>  
  
```sql
CREATE PROCEDURE DateTimeInvestigation(@withdata bit)  
-- @withdata = 0: only get the affected meta data information  
-- @withdata = 1: get the affected meta data and instance information  
AS  
BEGIN  
-- First get XML containing all schema collections containing affected element and attributes  
-- components (model groups?)   
-- and columns that are affected by the schema collections.   
CREATE table #_dt_collector(x xml);   
;with dttypes as  
  (SELECT * FROM sys.xml_schema_components   
   where base_xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
      )   
   union all  
   SELECT * FROM sys.xml_schema_components  
   where xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
       or kind='N' or kind='Z')   
   ),   
dtplaced as  
  (SELECT scp.*   
   FROM sys.xml_schema_component_placements scp   
   JOIN dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
  )   
insert into #_dt_collector SELECT x FROM (SELECT  
  xsc.xml_collection_id as "@collid"  
, s.name as "@schema"  
, xscol.name as "@name"  
, count(xsc.xml_component_id) as "@affected_elems_and_attrs"  
, (SELECT S.Name as "@schema", T.Name as "@table"  
        , C.Name as "@column"   
   FROM sys.columns C   
   JOIN sys.tables T ON C.object_id = T.object_id  
   JOIN sys.schemas S ON S.schema_id = T.schema_id  
   WHERE C.xml_collection_id = xsc.xml_collection_id  
   FOR XML PATH('Columns'), TYPE  
  )   
FROM sys.xml_schema_components xsc  
JOIN dtplaced on xsc.xml_component_id=dtplaced.xml_component_id  
JOIN sys.xml_schema_collections xscol on xsc.xml_collection_id =xscol.xml_collection_id  
JOIN sys.schemas s on xscol.schema_id=s.schema_id  
group by xsc.xml_collection_id, s.name, xscol.name  
FOR XML PATH('XML_Schema_Collections'), TYPE) as T(x);   
if (@withdata = 0)    
  BEGIN  
  SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
  drop table #_dt_collector;   
  return;   
  END;   
-- Declare cursor to find all columns bound to the schema collections  
DECLARE C CURSOR FOR  
SELECT S.Name, T.Name, C.Name   
FROM sys.columns C   
JOIN sys.tables T ON C.object_id = T.object_id  
JOIN sys.schemas S ON S.schema_id = T.schema_id  
WHERE C.xml_collection_id  
IN (SELECT distinct xsc.xml_collection_id  
    FROM sys.xml_schema_components xsc  
    JOIN (SELECT scp.*   
          FROM sys.xml_schema_component_placements scp   
          JOIN (SELECT * FROM sys.xml_schema_components   
                where base_xml_component_id    
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                   )   
                union all  
                SELECT * FROM sys.xml_schema_components  
                where xml_component_id   
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                    or kind='N' or kind='Z')   
               ) dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
          ) dtplaced on xsc.xml_component_id=dtplaced.xml_component_id);   
DECLARE @SchemaName nvarchar(max);   
DECLARE @TableName nvarchar(max);   
DECLARE @ColumnName nvarchar(max);   
DECLARE @strSQL nvarchar(MAX);   
OPEN C;   
FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
WHILE (@@FETCH_STATUS = 0)   
BEGIN  
      SET @strSQL = 'INSERT INTO #_dt_collector SELECT x FROM ( ';   
      SET @strSQL = @strSQL +    
                    'SELECT ''' + @SchemaName + '.' + @TableName + '.' + @ColumnName   
                  + ''' as "@Column", ';   
      SET @strSQL = @strSQL +    
      'sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)])'', ''bigint'')) as "@dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)])'', ''bigint'')) as "@date_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_date_elements"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)  
                      where $v instance of xs:dateTime?   
                      return 1)'', ''bigint'')) as "@dT_attributes"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:dateTime?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_dt_attributes"  
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      return 1)'', ''bigint'')) as "@date_attributes"   
     , sum('+ @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_date_attributes"'  
      + ' FROM ' + @SchemaName + '.' + @TableName  
      + ' FOR XML PATH(''data''), type) T(x)';   
      --SELECT @strSQL;   
      EXEC sp_executesql @strSQL;   
      FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
END;   
CLOSE C;   
DEALLOCATE C;   
SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
drop table #_dt_collector;   
END;   
go  
-- Get the dependent columns per affected XML Schema Collection and the  
-- number of affected values  
EXECUTE DateTimeInvestigation 1;   
```  
  
 <span data-ttu-id="4adf4-117">如果找到负年份值，则有多种解决方案：</span><span class="sxs-lookup"><span data-stu-id="4adf4-117">If negative year values are found, you have multiple solutions:</span></span>  
  
-   <span data-ttu-id="4adf4-118">删除相应行。</span><span class="sxs-lookup"><span data-stu-id="4adf4-118">Delete the rows.</span></span>  
  
-   <span data-ttu-id="4adf4-119">更新这些值。</span><span class="sxs-lookup"><span data-stu-id="4adf4-119">Update those values.</span></span>  
  
-   <span data-ttu-id="4adf4-120">清除整个 XML 列。</span><span class="sxs-lookup"><span data-stu-id="4adf4-120">Clear the entire XML column.</span></span>  
  
-   <span data-ttu-id="4adf4-121">用不使用 xs:date 或 xs:dateTime（例如，使用 xs:string）的架构集合重新类型化 XML 列。</span><span class="sxs-lookup"><span data-stu-id="4adf4-121">Retype the XML column with a schema collection that doesn't use xs:date or xs:dateTime (use xs:string for example)</span></span>  
  
 <span data-ttu-id="4adf4-122">解决了负年份问题之后，就可以升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4adf4-122">After you have reconciled negative year issues, you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="4adf4-123">若要在升级之后在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 XML 索引，必须为使用 xs:date、xs:time 或 xs:dateTime 的所有列重新生成 XML 索引或重新类型化 XML 列。</span><span class="sxs-lookup"><span data-stu-id="4adf4-123">To use XML indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after the upgrade, you must rebuild XML indexes or retype XML columns for all columns that use xs:date, xs:time or xs:dateTime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adf4-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4adf4-124">See Also</span></span>  
 [<span data-ttu-id="4adf4-125">数据库引擎升级问题</span><span class="sxs-lookup"><span data-stu-id="4adf4-125">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
