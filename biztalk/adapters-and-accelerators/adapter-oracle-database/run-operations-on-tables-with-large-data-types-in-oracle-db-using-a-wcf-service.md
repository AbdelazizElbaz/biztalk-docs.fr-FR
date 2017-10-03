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
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="89b27-102">Effectuer des opérations sur les tables avec des types de données de grande taille dans la base de données Oracle à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="89b27-102">Complete operations on tables with large data types in Oracle Database using the WCF service model</span></span>
<span data-ttu-id="89b27-103">Cette section contient des informations sur la façon d’appeler les opérations ReadLOB et UpdateLOB à partir du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="89b27-103">This section contains information about how to invoke the ReadLOB and UpdateLOB operations from the WCF service model.</span></span> <span data-ttu-id="89b27-104">Les opérations ReadLOB et UpdateLOB sont signalées pour les tables et vues qui contiennent des colonnes LOB ; c'est-à-dire les colonnes qui sont utilisés pour stocker les données Oracle LOB (large object).</span><span class="sxs-lookup"><span data-stu-id="89b27-104">The ReadLOB and UpdateLOB operations are surfaced for tables and views that contain LOB columns; that is columns that are used to store Oracle large object (LOB) data.</span></span> <span data-ttu-id="89b27-105">Pour connaître les types de données Oracle LOB pris en charge par le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] et des opérations ReadLOB et UpdateLOB, consultez [opérations sur les Tables et vues que contiennent LOB des données dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="89b27-105">For an overview of the Oracle LOB data types supported by the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and of the ReadLOB and UpdateLOB operations, see [Operations on Tables and Views That Contain LOB Data in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89b27-106">Colonnes de données LOB peuvent contenir de grandes quantités de données, jusqu'à 4 gigaoctets (Go).</span><span class="sxs-lookup"><span data-stu-id="89b27-106">LOB data columns can contain large amounts of data—up to 4 gigabytes (GB).</span></span> <span data-ttu-id="89b27-107">Une limitation importante de l’utilisation d’un client WCF pour fonctionner sur des colonnes LOB est que le modèle de service WCF prend en charge les données de diffusion en continu de l’opération ReadLOB, pas sur l’opération UpdateLOB.</span><span class="sxs-lookup"><span data-stu-id="89b27-107">A significant limitation of using a WCF client to operate on LOB columns is that the WCF service model only supports data streaming on the ReadLOB operation, not on the UpdateLOB operation.</span></span> <span data-ttu-id="89b27-108">Il s’agit, car WCF requiert que, pour la diffusion en continu pour travailler à partir du modèle de service, le paramètre doit être diffusé en continu doit être le seul paramètre dans sa direction.</span><span class="sxs-lookup"><span data-stu-id="89b27-108">This is because WCF requires that for streaming to work from service model, the parameter to be streamed must be the only parameter in its direction.</span></span> <span data-ttu-id="89b27-109">L’opération UpdateLOB a deux autres paramètres IN (un nom et la ligne de filtre de colonne) en plus des données LOB ; pour cette raison, diffusion en continu n'est pas pris en charge sur ce dernier dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="89b27-109">The UpdateLOB operation has two other IN parameters (a column name and row filter) in addition to the LOB data; for this reason, streaming is not supported on it in the WCF service model.</span></span> <span data-ttu-id="89b27-110">Par conséquent, si vous mettez à jour une colonne LOB avec une grande quantité de données, vous souhaiterez utiliser le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="89b27-110">Therefore, if you are updating a LOB column with a large amount of data, you might want to use the WCF channel model.</span></span> <span data-ttu-id="89b27-111">Pour plus d’informations sur la façon d’utiliser le modèle de canal WCF afin de diffuser des données LOB à l’aide de l’opération UpdateLOB, consultez [de diffusion en continu LOB Types de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="89b27-111">For more information on how to use the WCF channel model to stream LOB data using the UpdateLOB operation, see [Streaming Oracle LOB Data Types by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="89b27-112">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="89b27-112">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="89b27-113">Les exemples de cette rubrique utilisent la table /SCOTT/CUSTOMER.</span><span class="sxs-lookup"><span data-stu-id="89b27-113">The examples in this topic use the /SCOTT/CUSTOMER table.</span></span> <span data-ttu-id="89b27-114">Cette table contient une colonne BLOB nommée PHOTO. Un script pour générer cette table est fourni avec les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="89b27-114">This table contains a BLOB column named PHOTO.A script to generate this table is supplied with the SDK samples.</span></span> <span data-ttu-id="89b27-115">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="89b27-115">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="89b27-116">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="89b27-116">The WCF Client Class</span></span>  
 <span data-ttu-id="89b27-117">L’exemple suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations ReadLOB et UpdateLOB sur la table /SCOTT/CUSTOMER.</span><span class="sxs-lookup"><span data-stu-id="89b27-117">The following example shows the method signatures for a WCF client class generated for the ReadLOB and UpdateLOB operations on the /SCOTT/CUSTOMER table.</span></span>  
  
```  
public partial class SCOTTTableCUSTOMERClient : System.ServiceModel.ClientBase<SCOTTTableCUSTOMER>,   
                                                SCOTTTableCUSTOMER   
{  
    public System.IO.Stream ReadLOB(string LOB_COLUMN, string FILTER);   
  
    public void UpdateLOB(string LOB_COLUMN, string FILTER, byte[] Stream);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="89b27-118">Notez que **ReadLOB** retourne un flux de données, mais qui **UpdateLOB** ne fonctionne pas sur un flux de données.</span><span class="sxs-lookup"><span data-stu-id="89b27-118">Note that **ReadLOB** returns a data stream, but that **UpdateLOB** does not operate on a stream.</span></span>  
  
## <a name="invoking-the-readlob-and-updatelob-operations"></a><span data-ttu-id="89b27-119">Appeler les opérations de UpdateLOB et de ReadLOB</span><span class="sxs-lookup"><span data-stu-id="89b27-119">Invoking the ReadLOB and UpdateLOB Operations</span></span>  
 <span data-ttu-id="89b27-120">Les deux le **ReadLOB** et **UpdateLOB** méthodes peuvent fonctionner que sur une seule colonne LOB dans une ligne de base de données unique.</span><span class="sxs-lookup"><span data-stu-id="89b27-120">Both the **ReadLOB** and **UpdateLOB** methods can operate only on a single LOB column in a single database row.</span></span> <span data-ttu-id="89b27-121">Vous définissez les paramètres suivants pour identifier la ligne ou colonne cible.</span><span class="sxs-lookup"><span data-stu-id="89b27-121">You set the following parameters to identify the target column/row.</span></span>  
  
|<span data-ttu-id="89b27-122">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89b27-122">Parameter</span></span>|<span data-ttu-id="89b27-123">Définition</span><span class="sxs-lookup"><span data-stu-id="89b27-123">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="89b27-124">LOB_COLUMN</span><span class="sxs-lookup"><span data-stu-id="89b27-124">LOB_COLUMN</span></span>|<span data-ttu-id="89b27-125">Le nom de la colonne cible dans la ligne identifiée par le paramètre de filtre ; par exemple, « PHOTO ».</span><span class="sxs-lookup"><span data-stu-id="89b27-125">The name of the target column within the row identified by the FILTER parameter; for example, "PHOTO".</span></span>|  
|<span data-ttu-id="89b27-126">FILTER</span><span class="sxs-lookup"><span data-stu-id="89b27-126">FILTER</span></span>|<span data-ttu-id="89b27-127">Le contenu d’une instruction SQL SELECT clause WHERE qui spécifie la ligne cible ; par exemple, « nom = 'Kim Ralls' ».</span><span class="sxs-lookup"><span data-stu-id="89b27-127">The contents of a SQL SELECT statement WHERE clause that specifies the target row; for example, "NAME='Kim Ralls'".</span></span> <span data-ttu-id="89b27-128">Le filtre doit spécifier qu’une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="89b27-128">The filter must specify one and only one row.</span></span> <span data-ttu-id="89b27-129">Si le filtre correspond à plusieurs lignes :</span><span class="sxs-lookup"><span data-stu-id="89b27-129">If the filter matches more than one row:</span></span><br /><br /> <span data-ttu-id="89b27-130">-   **ReadLOB** renvoie les données LOB de la première ligne correspondante.</span><span class="sxs-lookup"><span data-stu-id="89b27-130">-   **ReadLOB** returns LOB data for the first matching row.</span></span><br /><span data-ttu-id="89b27-131">-   **UpdateLOB** lève une exception.</span><span class="sxs-lookup"><span data-stu-id="89b27-131">-   **UpdateLOB** throws an exception.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="89b27-132">Le flux retourné par **ReadLOB** ne prend pas en charge **recherche**.</span><span class="sxs-lookup"><span data-stu-id="89b27-132">The stream returned by **ReadLOB** does not support **Seek**.</span></span> <span data-ttu-id="89b27-133">Cela signifie que les propriétés telles que **longueur** ne sont pas pris en charge, soit.</span><span class="sxs-lookup"><span data-stu-id="89b27-133">This means that properties such as **Length** are not supported, either.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="89b27-134">Le **UpdateLOB** opération doit être effectuée dans une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="89b27-134">The **UpdateLOB** operation must be performed within a transaction scope.</span></span> <span data-ttu-id="89b27-135">En outre, le **UseAmbientTransaction** liaison de la propriété doit être définie sur **true** avant d’effectuer la **UpdateLOB** opération.</span><span class="sxs-lookup"><span data-stu-id="89b27-135">Also, the **UseAmbientTransaction** binding property must be set to **true** before performing the **UpdateLOB** operation.</span></span>  
  
 <span data-ttu-id="89b27-136">Le code suivant montre comment utiliser un client WCF pour mettre à jour la colonne PHOTO de l’objet BLOB dans la table /SCOTT/CUSTOMER à partir d’un fichier et de lire les nouvelles données de colonne dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="89b27-136">The following code shows how to use a WCF client to update the BLOB PHOTO column in the /SCOTT/CUSTOMER table from a file and read the new column data back to a file.</span></span> <span data-ttu-id="89b27-137">Vous trouverez un exemple complet dans les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="89b27-137">You can find a full sample in the SDK samples.</span></span> <span data-ttu-id="89b27-138">Pour plus d’informations sur les exemples SDK, consultez [exemples du SDK](../../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="89b27-138">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89b27-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b27-139">See Also</span></span>  
 [<span data-ttu-id="89b27-140">Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="89b27-140">Develop Oracle Database Applications Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)