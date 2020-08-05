---
title: 表格)  (的连接表示形式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60f3fdc10baf5dc3be9cd1b0ee6196d2a8da3d2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580425"
---
# <a name="connection-representation-tabular"></a><span data-ttu-id="1e5a6-102">连接表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="1e5a6-102">Connection Representation (Tabular)</span></span>
  <span data-ttu-id="1e5a6-103">连接对象定义填充表格模型的数据的源。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-103">The connection object defines the source of the data that populates the tabular model.</span></span>  
  
## <a name="connection-representation"></a><span data-ttu-id="1e5a6-104">连接表示形式</span><span class="sxs-lookup"><span data-stu-id="1e5a6-104">Connection Representation</span></span>  
 <span data-ttu-id="1e5a6-105">连接对象的规范遵循 OLE DB 访问接口的规则。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-105">The specification for the connection object follows the rules of OLE DB providers.</span></span>  
  
### <a name="connection-in-amo"></a><span data-ttu-id="1e5a6-106">AMO 中的连接</span><span class="sxs-lookup"><span data-stu-id="1e5a6-106">Connection in AMO</span></span>  
 <span data-ttu-id="1e5a6-107">在使用 AMO 管理表格模型数据库时，AMO 中的 <xref:Microsoft.AnalysisServices.DataSource> 对象与连接逻辑对象一对一匹配。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-107">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.DataSource> object in AMO matches one-to-one to the connection logical object.</span></span>  
  
 <span data-ttu-id="1e5a6-108">下面的代码段演示如何在表格模型中创建 AMO 数据源或 Connection 对象。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-108">The following code snippet shows how to create an AMO data source, or Connection object in a tabular model.</span></span>  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a><span data-ttu-id="1e5a6-109">“表格 AMO 2012”示例</span><span class="sxs-lookup"><span data-stu-id="1e5a6-109">Tabular AMO 2012 sample</span></span>  
 <span data-ttu-id="1e5a6-110">为了更好地理解如何使用 AMO 创建和操作连接表示形式，请参阅“表格 AMO 2012”示例中的源代码；请具体查看以下源文件：Database.cs。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-110">To have a better understanding on how to use AMO to create and manipulate connection representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="1e5a6-111">该示例位于 Codeplex。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="1e5a6-112">示例代码仅作为对此处所述逻辑概念的支持提供，不应用于生产环境中。</span><span class="sxs-lookup"><span data-stu-id="1e5a6-112">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
