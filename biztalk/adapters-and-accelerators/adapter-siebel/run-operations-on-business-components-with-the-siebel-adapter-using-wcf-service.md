---
title: "Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations on business components
- how to, perform operations using the proxy
- business components, performing operations by using the WCF service model
- performing operations, using the proxy
ms.assetid: 7a5fdc95-6159-4f43-aac5-4e2f84e9138b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99ac40efda9ed8c27fb5ac5fedfbe782b9a4f645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-business-components-with-the-siebel-adapter-using-the-wcf-service-model"></a><span data-ttu-id="84770-102">Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="84770-102">Run Operations on Business Components with the Siebel adapter using the WCF Service Model</span></span>
<span data-ttu-id="84770-103">Vous pouvez créer un client WCF qui cible un composant d’entreprise Siebel.</span><span class="sxs-lookup"><span data-stu-id="84770-103">You can create a WCF client that targets a Siebel business component.</span></span> <span data-ttu-id="84770-104">Vous pouvez ensuite utiliser le client WCF pour effectuer une insertion, mise à jour, requête, Delete, associer, recréez-la et les opérations de requête d’enregistrement enfant sur le composant de gestion sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="84770-104">You can then use the WCF client to perform Insert, Update, Query, Delete, Associate, Dissociate, and child record query operations on the business component on the Siebel system.</span></span> <span data-ttu-id="84770-105">Les objets métier Siebel sont signalées sous le nœud des objets métier dans le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84770-105">Siebel business objects are surfaced under the Business Objects node in the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="84770-106">Les composants d’entreprise qui composent chaque objet métier sont signalées sous le nœud correspondant à cet objet.</span><span class="sxs-lookup"><span data-stu-id="84770-106">The business components that compose each business object are surfaced under the node corresponding to that object.</span></span> <span data-ttu-id="84770-107">Vous pouvez suivre les étapes de [vue d’ensemble du modèle de Service WCF avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md) pour générer un client WCF pour un composant métier qui cible des opérations spécifiques et utiliser le client pour appeler ces opérations sur l’entreprise composant.</span><span class="sxs-lookup"><span data-stu-id="84770-107">You can follow the steps in [Overview of the WCF Service Model with the Siebel Adapter](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md) to generate a WCF client for a business component that targets specific operations and use the client to invoke these operations on the business component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84770-108">Cette rubrique fournit des informations sur l’exécution d’opérations de base (insertion, mise à jour, la requête, suppression) sur les composants d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="84770-108">This topic provides information about performing basic operations (Insert, Update, Query, Delete) on business components.</span></span> <span data-ttu-id="84770-109">Pour plus d’informations sur l’exécution d’opérations de requête d’enregistrement enfant, recréez-la et associer, consultez [exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)</span><span class="sxs-lookup"><span data-stu-id="84770-109">For more information about performing Associate, Dissociate, and child record query operations, see [Run Operations on Business Components with MVG Fields by Using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)</span></span>  
  
 <span data-ttu-id="84770-110">Le code suivant utilise un client WCF pour effectuer des opérations Insert, Update et Delete sur un enregistrement dans le composant de gestion de compte de l’objet compte d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="84770-110">The following code uses a WCF client to perform Insert, Update, and Delete operations on a record in the Account business component of the Account business object.</span></span> <span data-ttu-id="84770-111">Entre chaque opération, une opération de requête est effectuée pour vérifier les résultats.</span><span class="sxs-lookup"><span data-stu-id="84770-111">Between each operation, a Query operation is performed to verify the results.</span></span> <span data-ttu-id="84770-112">Le client WCF dans cet exemple est initialisé à partir d’un fichier de configuration qui est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84770-112">The WCF client in this example is initialized from a configuration file that is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="84770-113">Pour obtenir un exemple de fichier de configuration généré, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).</span><span class="sxs-lookup"><span data-stu-id="84770-113">For an example of a generated configuration file, see [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).</span></span>  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using microsoft.lobservices.siebel._2007._03.BusinessObjects;  
using microsoft.lobservices.siebel._2007._03;  
  
namespace Business_Component_Operations  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BusinessObjects_Account_Account_OperationClient client = null;  
  
            try  
            {  
  
                client = new BusinessObjects_Account_Account_OperationClient("SiebelBinding_BusinessObjects_Account_Account_Operation");  
                client.ClientCredentials.UserName.UserName = "YourUserName";  
                client.ClientCredentials.UserName.Password = "YourPassword";  
  
                Console.WriteLine("Opening connection to " + client.Endpoint.Address.Uri.Host);  
                client.Open();  
                AccountInsertRecord[] air = new AccountInsertRecord[1];  
                air[0] = new AccountInsertRecord();  
                Random r = new Random();  
                int count = r.Next();  
  
                air[0].Name = "Anil" + count.ToString();  
                Console.WriteLine("Inserting " + air[0].Name + " ...");  
                client.Insert(air);  
  
                //Query for the record.  
                Console.WriteLine("Querying to check inserted record ...");  
                AccountQueryInputRecord aqir = new AccountQueryInputRecord();  
                short viewmode = new short(); viewmode = 3;  
                string[] fields = new string[2];  
                fields[0] = "Name";  
                fields[1] = "Id";  
                aqir.QueryFields = fields;  
                aqir.SearchExpr = "[Name] LIKE \"Anil*\"";  
                AccountQueryRecord[] aqr = client.Query(viewmode, aqir);  
                Console.WriteLine(aqr.Length + " records returned");  
                string[] ids = new string[1];  
                AccountUpdateRecord[] aur = new AccountUpdateRecord[1];  
                aur[0] = new AccountUpdateRecord();  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine("Name: " + rec.Name);  
                    Console.WriteLine("Id: " + rec.Id);  
                    Console.WriteLine("");  
                    ids[0] = rec.Id;  
                    aur[0].Name = rec.Name;  
                    aur[0].Id = rec.Id;  
                }  
  
                //Update it.  
  
                aur[0].Name = "Anil" + count.ToString() + "modified";  
                Console.WriteLine("Update the record to " + aur[0].Name + " ...");  
                client.Update(viewmode, aur);  
                //query again  
                aqr = client.Query(viewmode, aqir);  
                Console.WriteLine(aqr.Length + " records returned");  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine("Name: " + rec.Name);  
                    Console.WriteLine("Id: " + rec.Id);  
                    Console.WriteLine("");  
                }  
  
                //Delete it.  
                Console.WriteLine("Deleting record ...");  
                client.Delete(viewmode, ids, "");  
  
                //Check again.  
                Console.WriteLine("Check that " + aur[0].Name + " is not present");  
                aqr = client.Query(viewmode, aqir);  
  
                Console.WriteLine(aqr.Length + " records returned");  
                foreach (AccountQueryRecord rec in aqr)  
                {  
                    Console.WriteLine(rec.Name);  
                    Console.WriteLine(rec.Id);  
  
                }  
  
                // Wait for <RETURN> to end sample.  
                Console.WriteLine("\nHit <RETURN> to finish");  
                Console.ReadLine();  
  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            finally  
            {  
                // Close the client.  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="84770-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84770-114">See Also</span></span>  
 [<span data-ttu-id="84770-115">Développer des Applications Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="84770-115">Develop Siebel Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)