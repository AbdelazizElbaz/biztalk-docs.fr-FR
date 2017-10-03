---
title: "Exécuter une requête à l’aide de la commande SELECT dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SELECT command, performing a query
- query, performing by using the SELECT command
ms.assetid: 6f03243c-ef50-4a4a-8fe6-4e525bd7efe3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e03ac093e0fb7b2b8f95d770661bd702d988f01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-query-using-the-select-command-in-sap"></a><span data-ttu-id="295b0-102">Exécuter une requête à l’aide de la commande SELECT dans SAP</span><span class="sxs-lookup"><span data-stu-id="295b0-102">Run a Query Using the SELECT Command in SAP</span></span>
<span data-ttu-id="295b0-103">Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="295b0-103">The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source.</span></span> <span data-ttu-id="295b0-104">Avec la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], vous pouvez interroger les artefacts SAP en exécutant une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="295b0-104">With the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], you can query SAP artifacts by executing a SELECT statement.</span></span>  
  
## <a name="how-to-perform-a-query-by-using-the-select-command"></a><span data-ttu-id="295b0-105">Comment effectuer une requête à l’aide de la commande SELECT</span><span class="sxs-lookup"><span data-stu-id="295b0-105">How to Perform a Query by Using the SELECT Command</span></span>  
 <span data-ttu-id="295b0-106">Pour les artefacts SAP de requête à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="295b0-106">To query SAP artifacts using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:</span></span>  
  
#### <a name="to-perform-a-query"></a><span data-ttu-id="295b0-107">Pour exécuter une requête</span><span class="sxs-lookup"><span data-stu-id="295b0-107">To perform a query</span></span>  
  
1.  <span data-ttu-id="295b0-108">Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.</span><span class="sxs-lookup"><span data-stu-id="295b0-108">Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.</span></span>  
  
2.  <span data-ttu-id="295b0-109">Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="295b0-109">Create a **SAPConnection** object by using a Data Provider for SAP connection string.</span></span> <span data-ttu-id="295b0-110">Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="295b0-110">For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
3.  <span data-ttu-id="295b0-111">Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="295b0-111">Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.</span></span>  
  
4.  <span data-ttu-id="295b0-112">Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="295b0-112">Create a **SAPCommand** object from the **SAPConnection**.</span></span>  
  
5.  <span data-ttu-id="295b0-113">Spécifiez l’instruction SELECT de la **CommandText** propriété de la **SAPCommand**.</span><span class="sxs-lookup"><span data-stu-id="295b0-113">Specify the SELECT statement in the **CommandText** property of the **SAPCommand**.</span></span> <span data-ttu-id="295b0-114">Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets.</span><span class="sxs-lookup"><span data-stu-id="295b0-114">If necessary, you can specify parameters using **SAPParameter** objects.</span></span> <span data-ttu-id="295b0-115">Pour plus d’informations sur comment interroger les artefacts SAP à l’aide d’une instruction SELECT, consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="295b0-115">For more information about how to query SAP artifacts using a SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span> <span data-ttu-id="295b0-116">Pour obtenir des exemples montrant comment spécifier un BAPI ou les RFC, consultez [exemples d’instruction SELECT](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span><span class="sxs-lookup"><span data-stu-id="295b0-116">For examples of how to specify a BAPI or RFC, see [Examples for SELECT Statement](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span></span>  
  
6.  <span data-ttu-id="295b0-117">Exécutez la commande pour exécuter la requête et obtenir les résultats dans un **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="295b0-117">Execute the command to perform the query and obtain the results in a **SAPDataReader**.</span></span>  
  
7.  <span data-ttu-id="295b0-118">Lisez les résultats à partir de la **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="295b0-118">Read the results from the **SAPDataReader**.</span></span>  
  
8.  <span data-ttu-id="295b0-119">Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="295b0-119">When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.</span></span>  
  
 <span data-ttu-id="295b0-120">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets.</span><span class="sxs-lookup"><span data-stu-id="295b0-120">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects.</span></span> <span data-ttu-id="295b0-121">Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="295b0-121">For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="295b0-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="295b0-122">Example</span></span>  
 <span data-ttu-id="295b0-123">L’exemple suivant écrit les résultats d’une instruction select sur une instruction de jointure interne paramétrable sur la console.</span><span class="sxs-lookup"><span data-stu-id="295b0-123">The following example writes the results of a select on a parameterized inner join statement to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoSelect  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        /// <summary>  
        /// select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid  
        /// </summary>  
  
        string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid";  
                    cmd.Parameters.Add(new SAPParameter("@connid", 17));                      
                    using (SAPDataReader dr = cmd.ExecuteReader())  
                    {  
                        do  
                        {  
                            int rows = 0;  
                            while (dr.Read())  
                            {  
                                rows++;  
                                StringBuilder b = new StringBuilder();  
                                for (int i = 0; i < dr.FieldCount; i++)  
                                {  
                                    b.Append(dr[i].ToString()+" ");  
                                }  
                                Console.WriteLine("row {0}: {1} ", rows, b.ToString());  
                            }  
                            Console.WriteLine("Number of rows:{0}", rows);  
  
                        } while (dr.NextResult());  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="295b0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="295b0-124">See Also</span></span>  
 <span data-ttu-id="295b0-125">[Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span><span class="sxs-lookup"><span data-stu-id="295b0-125">[Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span></span>  
 [<span data-ttu-id="295b0-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="295b0-126">Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)