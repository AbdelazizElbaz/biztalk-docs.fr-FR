---
title: "Exécuter une requête SAP à l’aide de la commande EXECQUERY | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520153bf-9477-4b35-8953-3f5cb444ab9f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86159a03858ae5aa31bb37da56b6e5ea68dac3ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-an-sap-query-using-the-execquery-command"></a><span data-ttu-id="1f7cd-102">Exécuter une requête SAP à l’aide de la commande EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="1f7cd-102">Execute an SAP Query Using the EXECQUERY Command</span></span>
<span data-ttu-id="1f7cd-103">Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-103">The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source.</span></span> <span data-ttu-id="1f7cd-104">Avec la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], vous pouvez exécuter des requêtes prédéfinies dans le système SAP en exécutant une instruction EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-104">With the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], you can execute pre-defined queries in the SAP system by executing an EXECQUERY statement.</span></span>  
  
## <a name="how-to-perform-a-query-by-using-the-execquery-command"></a><span data-ttu-id="1f7cd-105">Comment effectuer une requête à l’aide de la commande EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="1f7cd-105">How to Perform a Query by Using the EXECQUERY Command</span></span>  
 <span data-ttu-id="1f7cd-106">Pour exécuter SAP prédéfini des requêtes à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1f7cd-106">To execute pre-defined SAP queries using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:</span></span>  
  
#### <a name="to-perform-a-query"></a><span data-ttu-id="1f7cd-107">Pour exécuter une requête</span><span class="sxs-lookup"><span data-stu-id="1f7cd-107">To perform a query</span></span>  
  
1.  <span data-ttu-id="1f7cd-108">Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-108">Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.</span></span>  
  
2.  <span data-ttu-id="1f7cd-109">Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-109">Create a **SAPConnection** object by using a Data Provider for SAP connection string.</span></span> <span data-ttu-id="1f7cd-110">Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="1f7cd-110">For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
3.  <span data-ttu-id="1f7cd-111">Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-111">Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.</span></span>  
  
4.  <span data-ttu-id="1f7cd-112">Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-112">Create a **SAPCommand** object from the **SAPConnection**.</span></span>  
  
5.  <span data-ttu-id="1f7cd-113">Spécifiez l’instruction EXECQUERY dans le **CommandText** propriété de la **SAPCommand**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-113">Specify the EXECQUERY statement in the **CommandText** property of the **SAPCommand**.</span></span> <span data-ttu-id="1f7cd-114">Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-114">If necessary, you can specify parameters using **SAPParameter** objects.</span></span> <span data-ttu-id="1f7cd-115">Pour plus d’informations sur la façon d’exécuter des requêtes définies dans un système SAP à l’aide d’une instruction EXECQUERY, consultez [syntaxe pour une instruction EXECQUERY dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="1f7cd-115">For more information about how to execute queries defined in an SAP system using an EXECQUERY statement, see [Syntax for an EXECQUERY Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).</span></span>  
  
6.  <span data-ttu-id="1f7cd-116">Exécutez la commande pour exécuter la requête et obtenir les résultats dans un **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-116">Execute the command to perform the query and obtain the results in a **SAPDataReader**.</span></span>  
  
7.  <span data-ttu-id="1f7cd-117">Lisez les résultats à partir de la **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-117">Read the results from the **SAPDataReader**.</span></span>  
  
8.  <span data-ttu-id="1f7cd-118">Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-118">When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.</span></span>  
  
 <span data-ttu-id="1f7cd-119">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-119">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects.</span></span> <span data-ttu-id="1f7cd-120">Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1f7cd-120">For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f7cd-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f7cd-121">Example</span></span>  
 <span data-ttu-id="1f7cd-122">L’exemple suivant écrit les résultats d’une requête, ZTEST1, dans la console.</span><span class="sxs-lookup"><span data-stu-id="1f7cd-122">The following example writes the results of a query, ZTEST1, to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExecQuery  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
           string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "EXECQUERY ZTEST1 @userGRoup='SYSTQV000024',@P1='0000001390',@P2='0000080150'";  
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
  
## <a name="see-also"></a><span data-ttu-id="1f7cd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f7cd-123">See Also</span></span>  
 [<span data-ttu-id="1f7cd-124">Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="1f7cd-124">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)  
 [<span data-ttu-id="1f7cd-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="1f7cd-125">Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)