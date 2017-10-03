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
# <a name="execute-an-sap-query-using-the-execquery-command"></a>Exécuter une requête SAP à l’aide de la commande EXECQUERY
Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET. Avec la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], vous pouvez exécuter des requêtes prédéfinies dans le système SAP en exécutant une instruction EXECQUERY.  
  
## <a name="how-to-perform-a-query-by-using-the-execquery-command"></a>Comment effectuer une requête à l’aide de la commande EXECQUERY  
 Pour exécuter SAP prédéfini des requêtes à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :  
  
#### <a name="to-perform-a-query"></a>Pour exécuter une requête  
  
1.  Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.  
  
2.  Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP. Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
3.  Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.  
  
4.  Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.  
  
5.  Spécifiez l’instruction EXECQUERY dans le **CommandText** propriété de la **SAPCommand**. Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets. Pour plus d’informations sur la façon d’exécuter des requêtes définies dans un système SAP à l’aide d’une instruction EXECQUERY, consultez [syntaxe pour une instruction EXECQUERY dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).  
  
6.  Exécutez la commande pour exécuter la requête et obtenir les résultats dans un **SAPDataReader**.  
  
7.  Lisez les résultats à partir de la **SAPDataReader**.  
  
8.  Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets. Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant écrit les résultats d’une requête, ZTEST1, dans la console.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)  
 [Exemples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)