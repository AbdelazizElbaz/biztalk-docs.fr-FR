---
title: "Appeler les RFC et BAPI dans SAP à l’aide de la commande EXEC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EXEC command, invoking RFCs and BAPIs
- BAPIs and RFCs, invoking by using the EXEC command
- RFCs and BAPIs, invoking by using the EXEC command
ms.assetid: 55443679-2fa8-4c13-ac3b-1c85b5166cd2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 500e0f932a8245f76954aa7a8785dbec012321e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-rfcs-and-bapis-using-the-exec-command-in-sap"></a>Appeler les RFC et BAPI à l’aide de la commande EXEC dans SAP
Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET. À l’aide de [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], vous pouvez appeler des RFC et BAPI sur le système SAP via une commande EXEC.  
  
## <a name="how-to-invoke-rfcs-and-bapis-on-the-sap-system"></a>Comment appeler des RFC et BAPI sur le système SAP  
 Pour appeler un RFC ou BAPI à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :  
  
#### <a name="to-invoke-an-rfc-or-bapi"></a>Pour appeler RFC ou BAPI  
  
1.  Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.  
  
2.  Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP. Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
3.  Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.  
  
4.  Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.  
  
5.  Spécifiez l’appel BAPI ou RFC dans le **CommandText** propriété de la **SAPCommand**. Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets. Pour plus d’informations sur la façon de spécifier un appel BAPI ou RFC à l’aide d’une instruction EXEC, consultez [syntaxe pour une instruction EXEC dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md). Pour obtenir des exemples montrant comment spécifier un BAPI ou les RFC, consultez [exemples pour l’instruction EXEC](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).  
  
6.  Exécutez la commande à appeler la RFC ou BAPI et obtenir les résultats dans un **SAPDataReader**.  
  
7.  Lisez les résultats à partir de la **SAPDataReader**.  
  
8.  Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.  
  
 Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets. Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle SD_RFC_CUSTOMER_GET pour extraire les informations client pour tous les clients dont le nom commence par « AB ». Il écrit ensuite le client enregistre dans la console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExec  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string connstr = "TYPE=A; ASHOST=YourSAPHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
            using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "exec sd_rfc_customer_get @name1='AB*' ";  
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
                                    b.Append(dr[i].ToString() + " ");  
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
 [Exemples](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)