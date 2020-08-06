---
title: Azure Data Lake Store 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693022"
---
# <a name="azure-data-lake-store-destination"></a><span data-ttu-id="6156a-102">Azure Data Lake Store 目标</span><span class="sxs-lookup"><span data-stu-id="6156a-102">Azure Data Lake Store Destination</span></span>
  <span data-ttu-id="6156a-103">“Azure Data Lake Store 目标”  组件允许 SSIS 包将数据写入 Azure Data Lake Store。</span><span class="sxs-lookup"><span data-stu-id="6156a-103">The **Azure Data Lake Store Destination** component enables an SSIS package to write data to an Azure Data Lake Store.</span></span> <span data-ttu-id="6156a-104">支持的文件格式：文本、Avro 和 ORC。</span><span class="sxs-lookup"><span data-stu-id="6156a-104">The supported file formats are: Text, Avro and ORC.</span></span> 
  
## <a name="configure-the-azure-data-lake-store-destination"></a><span data-ttu-id="6156a-105">配置 Azure Data Lake Store 目标</span><span class="sxs-lookup"><span data-stu-id="6156a-105">Configure the Azure Data Lake Store Destination</span></span> 

1. <span data-ttu-id="6156a-106">将“Azure Data Lake Store 目标” \*\*\*\* 拖放到数据流设计器中，然后双击该组件打开编辑器。</span><span class="sxs-lookup"><span data-stu-id="6156a-106">Drag-drop **Azure Data Lake Store Destination** to the data flow designer and double-click it to see the editor.</span></span>  

2.  <span data-ttu-id="6156a-107">对于“Azure Data Lake Store 连接管理器” \*\*\*\* 字段，请指定一个现有的 Azure Data Lake Store 连接管理器，或新建一个引用 Azure Data Lake Store 服务的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="6156a-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="6156a-108">对于“文件路径” \*\*\*\* 字段，请指定要将数据写入到的文件名。</span><span class="sxs-lookup"><span data-stu-id="6156a-108">For the **File Path** field, specify the file name you want to write data to.</span></span> <span data-ttu-id="6156a-109">如果此文件已存在，则将覆盖其内容。</span><span class="sxs-lookup"><span data-stu-id="6156a-109">If this file already exist, its content will be overwritten.</span></span>  
  
    2.  <span data-ttu-id="6156a-110">对于“文件格式” \*\*\*\* 字段，请指定要使用的文件格式。</span><span class="sxs-lookup"><span data-stu-id="6156a-110">For the **File format** field, specify the file format you want to use.</span></span>  
  
        <span data-ttu-id="6156a-111">如果文件格式是文本，则必须指定 "**列分隔符字符**" 值。</span><span class="sxs-lookup"><span data-stu-id="6156a-111">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="6156a-112">如果文件中的第一行包含列名称，则还应选择**第一个数据行中的列名称**。</span><span class="sxs-lookup"><span data-stu-id="6156a-112">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  

        <span data-ttu-id="6156a-113">如果文件格式是 ORC，请安装相应平台的 JRE。</span><span class="sxs-lookup"><span data-stu-id="6156a-113">If the file format is ORC, you need to install JRE of corresponding platform.</span></span> 
  
3.  <span data-ttu-id="6156a-114">指定连接信息后，切换到“列” \*\*\*\* 页，将源列映射到 SSIS 数据流的目标列。</span><span class="sxs-lookup"><span data-stu-id="6156a-114">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
