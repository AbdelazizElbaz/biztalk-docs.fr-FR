---
title: "Effectuer des opérations sur les tables avec des types de données de grande taille dans la base de données Oracle à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations on tables and views
- how to, invoke the ReadLOB and UpdateLOB operations
ms.assetid: 5d0e84d3-7ffa-47c7-aaf2-a1007f7a71a2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88ae5a616e71e27a4d6fa8cd27473665f7bc96b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-database-using-the-wcf-service-model"></a>Effectuer des opérations sur les tables avec des types de données de grande taille dans la base de données Oracle à l’aide du modèle de service WCF
Cette section contient des informations sur la façon d’appeler les opérations ReadLOB et UpdateLOB à partir du modèle de service WCF. Les opérations ReadLOB et UpdateLOB sont signalées pour les tables et vues qui contiennent des colonnes LOB ; c'est-à-dire les colonnes qui sont utilisés pour stocker les données Oracle LOB (large object). Pour connaître les types de données Oracle LOB pris en charge par le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] et des opérations ReadLOB et UpdateLOB, consultez [opérations sur les Tables et vues que contiennent LOB des données dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).  
  
> [!IMPORTANT]
>  Colonnes de données LOB peuvent contenir de grandes quantités de données, jusqu'à 4 gigaoctets (Go). Une limitation importante de l’utilisation d’un client WCF pour fonctionner sur des colonnes LOB est que le modèle de service WCF prend en charge les données de diffusion en continu de l’opération ReadLOB, pas sur l’opération UpdateLOB. Il s’agit, car WCF requiert que, pour la diffusion en continu pour travailler à partir du modèle de service, le paramètre doit être diffusé en continu doit être le seul paramètre dans sa direction. L’opération UpdateLOB a deux autres paramètres IN (un nom et la ligne de filtre de colonne) en plus des données LOB ; pour cette raison, diffusion en continu n'est pas pris en charge sur ce dernier dans le modèle de service WCF. Par conséquent, si vous mettez à jour une colonne LOB avec une grande quantité de données, vous souhaiterez utiliser le modèle de canal WCF. Pour plus d’informations sur la façon d’utiliser le modèle de canal WCF afin de diffuser des données LOB à l’aide de l’opération UpdateLOB, consultez [de diffusion en continu LOB Types de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent la table /SCOTT/CUSTOMER. Cette table contient une colonne BLOB nommée PHOTO. Un script pour générer cette table est fourni avec les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 L’exemple suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations ReadLOB et UpdateLOB sur la table /SCOTT/CUSTOMER.  
  
```  
public partial class SCOTTTableCUSTOMERClient : System.ServiceModel.ClientBase<SCOTTTableCUSTOMER>,   
                                                SCOTTTableCUSTOMER   
{  
    public System.IO.Stream ReadLOB(string LOB_COLUMN, string FILTER);   
  
    public void UpdateLOB(string LOB_COLUMN, string FILTER, byte[] Stream);  
}  
```  
  
> [!NOTE]
>  Notez que **ReadLOB** retourne un flux de données, mais qui **UpdateLOB** ne fonctionne pas sur un flux de données.  
  
## <a name="invoking-the-readlob-and-updatelob-operations"></a>Appeler les opérations de UpdateLOB et de ReadLOB  
 Les deux le **ReadLOB** et **UpdateLOB** méthodes peuvent fonctionner que sur une seule colonne LOB dans une ligne de base de données unique. Vous définissez les paramètres suivants pour identifier la ligne ou colonne cible.  
  
|Paramètre|Définition|  
|---------------|----------------|  
|LOB_COLUMN|Le nom de la colonne cible dans la ligne identifiée par le paramètre de filtre ; par exemple, « PHOTO ».|  
|FILTER|Le contenu d’une instruction SQL SELECT clause WHERE qui spécifie la ligne cible ; par exemple, « nom = 'Kim Ralls' ». Le filtre doit spécifier qu’une seule ligne. Si le filtre correspond à plusieurs lignes :<br /><br /> -   **ReadLOB** renvoie les données LOB de la première ligne correspondante.<br />-   **UpdateLOB** lève une exception.|  
  
> [!NOTE]
>  Le flux retourné par **ReadLOB** ne prend pas en charge **recherche**. Cela signifie que les propriétés telles que **longueur** ne sont pas pris en charge, soit.  
  
> [!CAUTION]
>  Le **UpdateLOB** opération doit être effectuée dans une étendue de transaction. En outre, le **UseAmbientTransaction** liaison de la propriété doit être définie sur **true** avant d’effectuer la **UpdateLOB** opération.  
  
 Le code suivant montre comment utiliser un client WCF pour mettre à jour la colonne PHOTO de l’objet BLOB dans la table /SCOTT/CUSTOMER à partir d’un fichier et de lire les nouvelles données de colonne dans un fichier. Vous trouverez un exemple complet dans les exemples du Kit de développement logiciel. Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Transaction;  
  
// Include for file streaming  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for the WCF channel model  
using System.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using CustomerTablens = microsoft.lobservices.oracledb._2007._03;  
  
namespace OracleLobOpsSnippetSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.UseAmbientTransaction = true; //set this to true for UpdateLOB operation  
  
                EndpointAddress endpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
  
                using (SCOTTTableCUSTOMERClient customerTableClient =  
                    new SCOTTTableCUSTOMERClient(binding, endpointAddress))  
                {  
                    customerTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    customerTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    // Open the client to read the LOB data back  
                    customerTableClient.Open();  
  
                    // Add a photo to the customer record    
                    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
                    {  
                        Console.WriteLine("Updating photo");  
                        int count = 0;  
                        byte[] photo = new byte[fs.Length];  
                        while ((count += fs.Read(photo, count, (int) (((fs.Length-count)>4096)? 4096:fs.Length-count))) \< fs.Length) ;  
  
                        // UpdateLOB operation must be performed within a transaction scope  
                        using(TransactionScope tx = new TransactionScope())  
                        {  
                           customerTableClient.UpdateLOB("PHOTO", "NAME='Kim Ralls'", photo);  
                           Console.WriteLine("Photo updated");  
                           tx.Complete();  
                        }  
                    }  
  
                    // Read the data back and store it to another file  
                    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
                    {  
                        Console.WriteLine("Reading photo data");  
                        Stream photoStream = customerTableClient.ReadLOB("PHOTO", "NAME='Kim Ralls'");  
                        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  
  
                        int count;  
                        int length = 0;  
                        byte[] buffer = new byte[4096];  
                        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
                        {  
                            fs.Write(buffer, 0, count);  
                            length+=count;  
                        }  
                        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
                    }  
  
                }  
  
                Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
                Console.ReadLine();  
  
            }  
            catch (Exception ex)  
            {  
                // handle exception  
                Console.WriteLine("Exception caught: " + ex.Message);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)