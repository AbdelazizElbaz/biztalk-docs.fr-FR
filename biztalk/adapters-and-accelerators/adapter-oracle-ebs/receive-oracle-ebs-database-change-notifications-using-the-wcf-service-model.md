---
title: "Recevoir des notifications de modification de base de données Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362193f5-2586-480f-a62e-1ed5e4ef342c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0350a6c16eca4a6639549cb5240f04fa1b8bebf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-using-the-wcf-service-model"></a><span data-ttu-id="11bd5-102">Recevoir des notifications de modification de base de données Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="11bd5-102">Receive Oracle E-Business Suite database change notifications using the WCF service model</span></span>
<span data-ttu-id="11bd5-103">Cette rubrique montre comment configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de notification de requête à partir d’une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="11bd5-103">This topic demonstrates how to configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive query notification messages from an Oracle database.</span></span> <span data-ttu-id="11bd5-104">Pour illustrer des notifications, considérez une table, ACCOUNTACTIVITY, avec une colonne « Traitement ».</span><span class="sxs-lookup"><span data-stu-id="11bd5-104">To demonstrate notifications, consider a table, ACCOUNTACTIVITY, with a “Processed” column.</span></span> <span data-ttu-id="11bd5-105">Lorsqu’un nouvel enregistrement est inséré à cette table, la valeur de la colonne d’état est définie à « n ».</span><span class="sxs-lookup"><span data-stu-id="11bd5-105">When a new record is inserted to this table, the value of the Status column is set to “n.”</span></span> <span data-ttu-id="11bd5-106">Vous pouvez configurer l’adaptateur pour recevoir des notifications par l’inscription aux notifications à l’aide d’une instruction SQL qui Récupère tous les enregistrements dont la colonne « Traitement » en tant que « n ».</span><span class="sxs-lookup"><span data-stu-id="11bd5-106">You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have “Processed” column as “n.”</span></span> <span data-ttu-id="11bd5-107">Vous pouvez le faire en spécifiant l’instruction SQL pour le **NotificationStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="11bd5-107">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="11bd5-108">Une fois que le client de l’adaptateur reçoit la notification, il peut contenir la logique pour effectuer les tâches suivantes sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="11bd5-108">After the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the Oracle database.</span></span> <span data-ttu-id="11bd5-109">Dans cet exemple, par souci de simplicité, le client de carte répertorie tous les enregistrements dans la table dont la colonne « Traitement » en tant que « n ».</span><span class="sxs-lookup"><span data-stu-id="11bd5-109">In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the “Processed” column as “n.”</span></span>  
  
## <a name="configuring-notifications-with-the-oracle-e-business-adapter-binding-properties"></a><span data-ttu-id="11bd5-110">Configuration des Notifications avec l’adaptateur Oracle E-Business propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="11bd5-110">Configuring Notifications with the Oracle E-Business Adapter Binding Properties</span></span>  
 <span data-ttu-id="11bd5-111">Le tableau ci-dessous récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] propriétés de liaison qui vous permet de configurer la réception des notifications à partir d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="11bd5-111">The table below summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure receiving notifications from Oracle E-Business Suite.</span></span> <span data-ttu-id="11bd5-112">Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application .NET pour recevoir des notifications.</span><span class="sxs-lookup"><span data-stu-id="11bd5-112">You must specify these binding properties while running the .NET application to receive notifications.</span></span>  
  
|<span data-ttu-id="11bd5-113">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="11bd5-113">Binding Property</span></span>|<span data-ttu-id="11bd5-114"> Description</span><span class="sxs-lookup"><span data-stu-id="11bd5-114">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="11bd5-115">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="11bd5-115">**InboundOperationType**</span></span>|<span data-ttu-id="11bd5-116">Spécifie l’opération entrante que vous souhaitez effectuer.</span><span class="sxs-lookup"><span data-stu-id="11bd5-116">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="11bd5-117">Pour recevoir des messages de notification, affectez la valeur **Notification**.</span><span class="sxs-lookup"><span data-stu-id="11bd5-117">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="11bd5-118">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="11bd5-118">**NotificationPort**</span></span>|<span data-ttu-id="11bd5-119">Spécifie le numéro de port ODP.NET doit ouvrir pour l’écoute de notification de modification de base de données à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="11bd5-119">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span>|  
|<span data-ttu-id="11bd5-120">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="11bd5-120">**NotificationStatement**</span></span>|<span data-ttu-id="11bd5-121">Spécifie l’instruction Select utilisée pour s’inscrire aux notifications de requête.</span><span class="sxs-lookup"><span data-stu-id="11bd5-121">Specifies the Select statement used to register for query notifications.</span></span> <span data-ttu-id="11bd5-122">L’adaptateur reçoit un message de notification uniquement lorsque le jeu de résultats pour que les modifications de l’instruction Select spécifiée.</span><span class="sxs-lookup"><span data-stu-id="11bd5-122">The adapter gets a notification message only when the result set for the specified Select statement changes.</span></span>|  
|<span data-ttu-id="11bd5-123">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="11bd5-123">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="11bd5-124">Spécifie si l’adaptateur envoie une notification pour les clients de la carte au démarrage de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="11bd5-124">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="11bd5-125">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="11bd5-125">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="11bd5-126">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des notifications d’Oracle E-Business Suite, lire le reste de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="11bd5-126">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive notifications from Oracle E-Business Suite, read the remainder of this topic.</span></span>  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a><span data-ttu-id="11bd5-127">Configuration des Notifications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="11bd5-127">Configuring Notifications Using the WCF Service Model</span></span>  
 <span data-ttu-id="11bd5-128">Pour recevoir les notifications à l’aide du modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="11bd5-128">To receive the notifications using the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="11bd5-129">Générer un contrat de service WCF (interface) pour le **Notification** opération à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="11bd5-129">Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="11bd5-130">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11bd5-130">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="11bd5-131">Générer un client WCF pour le **sélectionnez** opération sur la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="11bd5-131">Generate a WCF client for the **Select** operation on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="11bd5-132">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11bd5-132">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="11bd5-133">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="11bd5-133">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="11bd5-134">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="11bd5-134">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="11bd5-135">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="11bd5-135">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="11bd5-136">Les exemples de cette rubrique reçoit la notification de la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="11bd5-136">The examples in this topic receives notification for the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="11bd5-137">Un script pour générer la table est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="11bd5-137">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="11bd5-138">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="11bd5-138">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="11bd5-139">Un exemple, **Notification_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="11bd5-139">A sample, **Notification_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="11bd5-140">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="11bd5-140">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="11bd5-141">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="11bd5-141">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation.</span></span> <span data-ttu-id="11bd5-142">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="11bd5-142">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="11bd5-143">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="11bd5-143">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="11bd5-144">Le code suivant illustre le contrat de service WCF (interface) généré pour le **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="11bd5-144">The following code shows the WCF service contract (interface) generated for the **Notification** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="Notification_")]  
public interface Notification_ {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/Notification/) of message Notification   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Notification")]  
    void Notification(Notification request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="11bd5-145">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="11bd5-145">The Message Contracts</span></span>  
 <span data-ttu-id="11bd5-146">Voici le contrat de message pour l’opération de Notification.</span><span class="sxs-lookup"><span data-stu-id="11bd5-146">Following is the message contract for the Notification operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.Notification.NotificationDetails[] Details;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=1)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=2)]  
    public string[] ResourceNames;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=3)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=4)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(schemas.microsoft.com.OracleEBS._2008._05.Notification.NotificationDetails[] Details, string Info, string[] ResourceNames, string Source, string Type) {  
        this.Details = Details;  
        this.Info = Info;  
        this.ResourceNames = ResourceNames;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="11bd5-147">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="11bd5-147">WCF Service Class</span></span>  
 <span data-ttu-id="11bd5-148">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="11bd5-148">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="11bd5-149">Le nom du fichier est OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="11bd5-149">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="11bd5-150">Vous pouvez insérer la logique pour traiter les **Notification** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="11bd5-150">You can insert the logic to process the **Notification** operation directly into this class.</span></span> <span data-ttu-id="11bd5-151">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11bd5-151">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : Notification_ {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/Notification/) of message Notification   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-query-notifications-using-wcf-service-model"></a><span data-ttu-id="11bd5-152">Réception des Notifications de requête à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="11bd5-152">Receiving Query Notifications Using WCF Service Model</span></span>  
 <span data-ttu-id="11bd5-153">Cette section fournit des instructions sur l’écriture d’une application .NET pour recevoir des notifications de requête à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11bd5-153">This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-query-notifications"></a><span data-ttu-id="11bd5-154">Pour recevoir des notifications de requête</span><span class="sxs-lookup"><span data-stu-id="11bd5-154">To receive query notifications</span></span>  
  
1.  <span data-ttu-id="11bd5-155">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un client WCF pour **sélectionnez** opération sur le **ACCOUNTACTIVITY** table.</span><span class="sxs-lookup"><span data-stu-id="11bd5-155">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **ACCOUNTACTIVITY** table.</span></span> <span data-ttu-id="11bd5-156">Vous allez utiliser ce client pour effectuer des opérations de sélection après avoir reçu un message de notification.</span><span class="sxs-lookup"><span data-stu-id="11bd5-156">You will use this client to perform Select operations after receiving a notification message.</span></span> <span data-ttu-id="11bd5-157">Ajouter une nouvelle classe, TableOperation.cs, à votre projet et ajouter l’extrait de code suivant pour effectuer une opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="11bd5-157">Add a new class, TableOperation.cs, to your project and add the following code snippet to perform a Select operation.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace Notification_ServiceModel  
    {  
        class TableOperation  
        {  
            public void TableOp()  
            {  
                //////////////////////////////////////////////////////////////////////  
                // CREATING THE CLIENT AND SETTING CLIENT CREDENTIALS  
                //////////////////////////////////////////////////////////////////////  
  
                Tables_APPS_ACCOUNTACTIVITYClient client = new Tables_APPS_ACCOUNTACTIVITYClient();  
                client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
                client.ClientCredentials.UserName.Password = "<Enter password here>";  
  
                ////////////////////////////////////////////////////////////////////  
                // OPENING THE CLIENT  
                //////////////////////////////////////////////////////////////////////  
                try  
                {  
                    Console.WriteLine("Opening the client ...");  
                    client.Open();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                ////////////////////////////////////////////////////////////////////////////////////////  
                // SELECTING THE LAST INSERTED VALUES  
                ////////////////////////////////////////////////////////////////////////////////////////  
                Console.WriteLine("The application will now select the last inserted record");  
  
                schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.ACCOUNTACTIVITY.SelectRecord[] selectRecords;  
  
                try  
                {  
                    selectRecords = client.Select("*", "WHERE PROCESSED = 'n'");  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                Console.WriteLine("The details of the newly added records are:");  
                Console.WriteLine("********************************************");  
                for (int i = 0; i < selectRecords.Length; i++)  
                {  
                    Console.WriteLine("Transaction ID   : " + selectRecords[i].TID);  
                    Console.WriteLine("Account ID       : " + selectRecords[i].ACCOUNT);  
                    Console.WriteLine("Processed Status : " + selectRecords[i].PROCESSED);  
                    Console.WriteLine();  
                }  
                Console.WriteLine("********************************************");  
            }  
        }  
    }  
  
    ```  
  
2.  <span data-ttu-id="11bd5-158">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="11bd5-158">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.</span></span>  
  
     <span data-ttu-id="11bd5-159">Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="11bd5-159">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="11bd5-160">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="11bd5-160">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="11bd5-161">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="11bd5-161">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
3.  <span data-ttu-id="11bd5-162">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="11bd5-162">Implement a WCF service from the interface and helper classes generated in step 2.</span></span> <span data-ttu-id="11bd5-163">Le **Notification** méthode de cette classe peut lever une exception pour annuler l’opération, si une erreur est rencontrée, le traitement des données provenance de la **Notification** opération ; sinon, la méthode ne ne renvoie rien.</span><span class="sxs-lookup"><span data-stu-id="11bd5-163">The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="11bd5-164">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="11bd5-164">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="11bd5-165">Dans le **Notification** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="11bd5-165">Within the **Notification** method, you can implement your application logic directly.</span></span> <span data-ttu-id="11bd5-166">Cette classe peut être trouvée dans OracleEBSBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="11bd5-166">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="11bd5-167">Ce code dans cet exemple montre comment des classes le **OracleEBSBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="11bd5-167">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="11bd5-168">Dans ce code, le message de notification reçu est écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="11bd5-168">In this code, the notification message received is written to the console.</span></span> <span data-ttu-id="11bd5-169">En outre, le **TableOp** méthode au sein de la **TableOperation** classe est appelée pour effectuer l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="11bd5-169">Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="11bd5-170">Vous devez implémenter la classe suivante pour transmettre des informations d’identification d’Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="11bd5-170">You must implement the following class to pass credentials for the Oracle E-Business Suite.</span></span> <span data-ttu-id="11bd5-171">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="11bd5-171">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
    ```  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="11bd5-172">Créer un **OracleEBSBinding** et configurez la carte pour recevoir des notifications de requête en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="11bd5-172">Create an **OracleEBSBinding** and configure the adapter to receive query notifications by specifying the binding properties.</span></span> <span data-ttu-id="11bd5-173">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="11bd5-173">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="11bd5-174">Au minimum, vous devez spécifier le **InboundOperationType** et **NotificationStatement** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="11bd5-174">At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Notification;  
    binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
    binding.NotifyOnListenerStart = true;  
    binding.NotificationPort = 10;  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="11bd5-175">La valeur de la **NotificationPort** liaison de la propriété doit être définie sur le même numéro de port que vous devez avoir ajouté à la liste d’exceptions de pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="11bd5-175">The value for the **NotificationPort** binding property must be set to the same port number that you must have added to the Windows Firewall exceptions list.</span></span> <span data-ttu-id="11bd5-176">Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span><span class="sxs-lookup"><span data-stu-id="11bd5-176">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="11bd5-177">Si vous ne définissez pas le **NotificationPort** propriété de liaison, l’adaptateur suppose que la valeur par défaut de -1 pour cette propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="11bd5-177">If you do not set the **NotificationPort** binding property, the adapter will assume the default value of -1 for this binding property.</span></span> <span data-ttu-id="11bd5-178">Dans ce cas, vous devez désactiver complètement le pare-feu Windows pour recevoir des messages de notification.</span><span class="sxs-lookup"><span data-stu-id="11bd5-178">In such a case, you will have to completely disable Windows Firewall to receive notification messages.</span></span>  
  
6.  <span data-ttu-id="11bd5-179">Spécifiez les informations d’identification Oracle E-Business Suite en instanciant le **NotificationCredentials** classe que vous avez créé à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="11bd5-179">Specify Oracle E-Business Suite credentials by instantiating the **NotificationCredentials** class you created in Step 4.</span></span>  
  
    ```  
    NotificationCredentials credentials = new NotificationCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  <span data-ttu-id="11bd5-180">Créez une instance du service WCF créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="11bd5-180">Create an instance of the WCF service created in step 3.</span></span>  
  
    ```  
    // create service instance  
    NotificationService service = new NotificationService();  
    ```  
  
8.  <span data-ttu-id="11bd5-181">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="11bd5-181">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="11bd5-182">Vous devez également spécifier les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="11bd5-182">You must also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="11bd5-183">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="11bd5-183">Add a service endpoint to the service host.</span></span> <span data-ttu-id="11bd5-184">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="11bd5-184">To do this:</span></span>  
  
    -   <span data-ttu-id="11bd5-185">Utilisez la liaison créée à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="11bd5-185">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="11bd5-186">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="11bd5-186">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="11bd5-187">Spécifiez le contrat en tant que « Notification_ ».</span><span class="sxs-lookup"><span data-stu-id="11bd5-187">Specify the contract as "Notification_".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify Notification_ as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  
    serviceHost.AddServiceEndpoint("Notification_", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="11bd5-188">Pour recevoir un message de notification, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="11bd5-188">To receive notification message, open the service host.</span></span>  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="11bd5-189">Pour arrêter de recevoir des notifications, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="11bd5-189">To stop receiving notifications, close the service host.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="11bd5-190">Exemple</span><span class="sxs-lookup"><span data-stu-id="11bd5-190">Example</span></span>  
 <span data-ttu-id="11bd5-191">L’exemple suivant montre une application .NET pour recevoir des messages de notification pour la table ACCOUNTACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="11bd5-191">The following example shows a .NET application to receive notification messages for the ACCOUNTACTIVITY table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11bd5-192">L’extrait de code suivant instancie un **TableOperation.cs** classe et appelle le **TableOp** (méthode).</span><span class="sxs-lookup"><span data-stu-id="11bd5-192">The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method.</span></span> <span data-ttu-id="11bd5-193">La classe et la méthode sont décrites à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="11bd5-193">The class and the method are described in Step 1.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
  
        }  
    }  
  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start receiving notifications...");  
                Console.ReadLine();  
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
                binding.NotifyOnListenerStart = true;  
                binding.NotificationPort = 10;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("Notification_", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Waiting for notification...");  
  
                Console.WriteLine("\nHit <RETURN> to stop receiving notification");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="11bd5-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11bd5-194">See Also</span></span>  
 [<span data-ttu-id="11bd5-195">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="11bd5-195">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)