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
# <a name="run-a-query-using-the-select-command-in-sap"></a>Exécuter une requête à l’aide de la commande SELECT dans SAP
Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET. Avec la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], vous pouvez interroger les artefacts SAP en exécutant une instruction SELECT.  
  
## <a name="how-to-perform-a-query-by-using-the-select-command"></a>Comment effectuer une requête à l’aide de la commande SELECT  
 Pour les artefacts SAP de requête à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :  
  
#### <a name="to-perform-a-query"></a>Pour exécuter une requête  
  
1.  Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.  
  
2.  Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP. Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
3.  Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.  
  
4.  Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.  
  
5.  Spécifiez l’instruction SELECT de la **CommandText** propriété de la **SAPCommand**. Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets. Pour plus d’informations sur comment interroger les artefacts SAP à l’aide d’une instruction SELECT, consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md). Pour obtenir des exemples montrant comment spécifier un BAPI ou les RFC, consultez [exemples d’instruction SELECT](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).  
  
6.  Exécutez la commande pour exécuter la requête et obtenir les résultats dans un **SAPDataReader**.  
  
7.  Lisez les résultats à partir de la **SAPDataReader**.  
  
8.  Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets. Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant écrit les résultats d’une instruction select sur une instruction de jointure interne paramétrable sur la console.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)   
 [Exemples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)