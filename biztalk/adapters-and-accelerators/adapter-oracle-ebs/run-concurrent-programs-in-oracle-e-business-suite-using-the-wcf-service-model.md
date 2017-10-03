---
title: "Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e227c60f-f6fe-40bf-bf41-2784a4428ad0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed2b50eab9612e5a2a610047e41560e1dc24576
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model"></a>Appeler des programmes simultanés dans Oracle E-Business Suite à l’aide du modèle de service WCF
Oracle E-Business Suite expose des programmes simultanés que vous pouvez exécuter pour effectuer des opérations spécifiques sur les applications Oracle. Chaque application Oracle a un ensemble de programmes simultanés standard (qui sont les mêmes pour toutes les opérations) et certains programmes simultanés qui sont spécifiques à une application Oracle. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose tous les programmes simultanés en tant qu’opérations que les clients de l’adaptateur peuvent appeler. Pour plus d’informations sur la façon dont l’adaptateur prend en charge des programmes simultanés, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).  
  
> [!NOTE]
>  Pour les programmes simultanés qui n’exposent pas leurs métadonnées, l’adaptateur Oracle E-Business expose 100 paramètres facultatifs pour chacun de ces programmes simultanés. Pour appeler ces programmes simultanés avec succès, l’utilisateur doit consultez la documentation d’Oracle E-Business Suite pour déterminer les paramètres pour un programme simultané qui nécessitent une valeur et puis de les spécifier. Est un exemple d’un tel programme simultané **importation du Journal** (nom réel : **GLLEZL**) dans le **comptabilité** application.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 L’exemple dans cette rubrique appelle la **MS_SAMPLE_COPY_EMP_DATA** simultanées du programme, suivi par le **Get_Status** simultanées du programme pour connaître l’état de la première simultanées du programme. Ces programmes simultanés sont appelées à partir de la **bibliothèque d’objets Application** application. Le **MS_SAMPLE_COPY_EMP_DATA** est créée en exécutant le script fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **ConcurrentProgram_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le nom du client WCF généré pour l’appel des programmes simultanés par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est répertorié dans le tableau suivant.  
  
|Artefact|Nom de Client WCF|  
|--------------|---------------------|  
|Simultanées du programme|Client de ConcurrentPrograms_ [nom_application]|  
  
 [Nom_application] = nom réel de l’application Oracle E-Business Suite ; par exemple, trver aide.  
  
### <a name="method-signature-for-invoking-concurrent-programs"></a>Signature de méthode pour appeler des programmes simultanés  
 Le tableau suivant montre la signature de méthode pour les programmes simultanés.  
  
|Opération|Signature de méthode|  
|---------------|----------------------|  
|Simultanées du programme|public \<type de retour >< Concurrent_program_name > (param 1, param 2,...)|  
  
 Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.  
  
```  
public partial class ConcurrentPrograms_FNDClient : System.ServiceModel.ClientBase<ConcurrentPrograms_FND>, ConcurrentPrograms_FND {      
  
    public string MS_SAMPLE_COPY_EMP_DATA(schemas.microsoft.com.OracleEBS._2008._05.Options.SetOptions SetOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,  
      string Description, string StartTime);  
  
    public bool GetStatusForConcurrentProgram(string RequestId, out string Phase, out string Status,  
      out string DevPhase, out string DevStatus, out string Message);  
}  
```  
  
 Dans cet extrait de code, **ConcurrentPrograms_FNDClient** est le nom de la classe WCF dans le OracleEBSBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. **MS_SAMPLE_COPY_EMP_DATA** est le nom de la méthode à appeler le programme simultané. **GetStatusForConcurrentProgram** est le nom de la méthode à appeler le programme simultané pour obtenir l’état de la première simultanées du programme.  
  
> [!NOTE]
>  **GetStatusForConcurrentProgram** est le nom réel de la **Get_Status** simultanées du programme.  
  
## <a name="creating-a-wcf-client-to-invoke-concurrent-programs"></a>Création d’un Client WCF pour appeler des programmes simultanés  
 L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md). Cette section décrit comment créer un client WCF pour appeler le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.  
  
#### <a name="to-create-a-wcf-client"></a>Pour créer un client WCF  
  
1.  Créez un projet Visual c# dans Visual Studio. Pour cette rubrique, créez une application console.  
  
2.  Générer la classe de client WCF pour le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés. Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
    > [!IMPORTANT]
    >  Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.  
  
3.  Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.  
  
4.  Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    ConcurrentPrograms_FNDClient client = new ConcurrentPrograms_FNDClient(binding, address);  
    ```  
  
     Dans cet extrait de code, `ConcurrentPrograms_FNDClient` est le client WCF défini dans OracleEBSBindingClient.cs. Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!NOTE]
    >  Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application. Vous pouvez également utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).  
  
6.  Définir les informations d’identification pour le client.  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  Étant donné que vous appelez des programmes simultanés dans une application Oracle E-Business Suite, vous devez définir le contexte d’application. Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison. Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :  
  
    ```  
    try  
    {  
       Console.WriteLine("Opening Client...");  
       client.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    ```  
  
9. Appeler le **MS_SAMPLE_COPY_EMP_DATA** et **Get_Status** programmes simultanés.  
  
    ```  
    string RequestID;  
    bool Result;  
    string Phase;  
    string Status;  
    string DevPhase;  
    string DevStatus;  
    string Message;  
  
    try  
    {  
        Console.WriteLine("Invoking the MS_SAMPLE_COPY_EMP_DATA concurrent program");  
        RequestID = client.MS_SAMPLE_COPY_EMP_DATA(null, null, null, null, null);  
        Console.WriteLine("The request ID generated for the concurrent program is : " + RequestID);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nWaiting for 60 seconds for the concurrent program to be complete");  
        System.Threading.Thread.Sleep(60000);  
        Console.WriteLine("\nInvoking the Get_Status concurrent program");  
        Result = client.GetStatusForConcurrentProgram(RequestID, out Phase, out Status, out DevPhase, out DevStatus, out Message);  
        Console.WriteLine("\nResult is  : " + Result);  
        Console.WriteLine("Phase is     : " + Phase);  
        Console.WriteLine("Status is    : " + Status);  
        Console.WriteLine("DevPhase is  : " + DevPhase);  
        Console.WriteLine("DevStatus is : " + DevStatus);  
        Console.WriteLine("Message is   : " + Message);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;                 
    }  
    ```  
  
10. Fermez le client, comme décrit dans l’extrait de code ci-dessous :  
  
    ```  
    client.Close();  
    ```  
  
11. Générez le projet et exécutez-le. L’application appelle la **MS_SAMPLE_COPY_EMP_DATA** et retourne un ID de demande. L’ID est ensuite transmise à la **Get_Status** simultanées du programme, qui enfin fournit l’état de la **MS_SAMPLE_COPY_EMP_DATA** programme de la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)