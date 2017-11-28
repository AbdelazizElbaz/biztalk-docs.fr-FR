---
title: "Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving polling-based messages
- how to, receive polling-based message
- polling-based messages, receiving by using the WCF service model
ms.assetid: 0324e8bf-d9d1-46f5-b896-b9fc8e61d514
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd36081bd92c3bfae13916ed7d984fcd5de9763f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="c2d87-102">Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="c2d87-102">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="c2d87-103">Vous pouvez configurer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] réception reposant sur l’interrogation des données modifiées messages par rapport à une table Oracle ou une vue.</span><span class="sxs-lookup"><span data-stu-id="c2d87-103">You can configure the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to receive polling-based data changed messages against an Oracle table or view.</span></span> <span data-ttu-id="c2d87-104">Pour recevoir des messages de données modifiées, l’adaptateur exécute régulièrement une requête SQL sur une table Oracle ou d’une vue, suivi d’un bloc de code PL/SQL facultatif.</span><span class="sxs-lookup"><span data-stu-id="c2d87-104">To receive data-changed messages, the adapter periodically executes a SQL query against an Oracle table or view followed by an optional PL/SQL code block.</span></span> <span data-ttu-id="c2d87-105">Les résultats de la requête SQL sont ensuite retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à votre application comme fortement typée jeu de résultats en une opération POLLINGSTMT entrante.</span><span class="sxs-lookup"><span data-stu-id="c2d87-105">The results of the SQL query are then returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to your application as a strongly-typed result set in an inbound POLLINGSTMT operation.</span></span> <span data-ttu-id="c2d87-106">Pour plus d’informations sur le mécanisme utilisé pour configurer et effectuer d’interrogation sur Oracle de base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c2d87-106">For more information about the mechanism used to configure and perform polling on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="c2d87-107">Nous vous recommandons fortement de lire cette rubrique avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c2d87-107">We strongly recommended that you read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="c2d87-108">Pour recevoir l’opération POLLINGSTMT lorsque vous utilisez le modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="c2d87-108">To receive the POLLINGSTMT operation when you use the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="c2d87-109">Générer un contrat de service WCF (interface) pour l’opération POLLINGSTMT à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c2d87-109">Generate a WCF service contract (interface) for the POLLINGSTMT operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="c2d87-110">Pour ce faire, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe).</span><span class="sxs-lookup"><span data-stu-id="c2d87-110">To do this, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe).</span></span>  
  
-   <span data-ttu-id="c2d87-111">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="c2d87-111">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="c2d87-112">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="c2d87-112">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
 <span data-ttu-id="c2d87-113">Les rubriques de cette section fournissent des informations et des procédures pour vous aider à effectuer d’interrogation sur des tables de base de données Oracle et les vues dans le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="c2d87-113">The topics in this section provide information and procedures to help you perform polling on Oracle database tables and views in the WCF service model.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="c2d87-114">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="c2d87-114">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="c2d87-115">Les exemples de cette rubrique utilisent la table /SCOTT/ACCOUNTACTIVITY et la fonction /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY.</span><span class="sxs-lookup"><span data-stu-id="c2d87-115">The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table and the /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY function.</span></span> <span data-ttu-id="c2d87-116">Un script pour générer ces artefacts est fourni avec les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="c2d87-116">A script to generate these artifacts is supplied with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="c2d87-117">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2d87-117">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="c2d87-118">Configuration d’interrogation dans le modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="c2d87-118">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="c2d87-119">Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour effectuer d’interrogation sur des tables de base de données Oracle et des vues en définissant les propriétés de liaison et une propriété de connexion facultatifs (paramètre).</span><span class="sxs-lookup"><span data-stu-id="c2d87-119">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to perform polling on Oracle database tables and views by setting binding properties and an optional connection property (parameter).</span></span> <span data-ttu-id="c2d87-120">Certaines de ces propriétés sont obligatoires, et certains, avoir un effet, doivent être définie à la fois au moment du design et au moment.</span><span class="sxs-lookup"><span data-stu-id="c2d87-120">Some of these properties are mandatory, and some, to have an effect, must be set both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="c2d87-121">Au moment du design, vous définissez les paramètres de connexion et les propriétés de liaison lorsque vous vous connectez à la base de données Oracle pour générer un contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="c2d87-121">At design-time, you set connection parameters and binding properties when you connect to the Oracle Database to generate a WCF service contract.</span></span>  
  
-   <span data-ttu-id="c2d87-122">Lors de l’exécution, vous définissez des propriétés de liaison sur l’objet OracleDBBinding qui vous permet de créer l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-122">At runtime you set binding properties on the OracleDBBinding object that you use to create the service host.</span></span> <span data-ttu-id="c2d87-123">Vous définissez le paramètre de connexion lorsque vous ajoutez un écouteur de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-123">You set the connection parameter when you add a service listener to the service host.</span></span>  
  
 <span data-ttu-id="c2d87-124">La liste suivante fournit une vue d’ensemble des propriétés de liaison et les paramètres de connexion utilisés pour configurer d’interrogation :</span><span class="sxs-lookup"><span data-stu-id="c2d87-124">The following list provides a brief overview of the binding properties and connection parameters used to configure polling:</span></span>  
  
-   <span data-ttu-id="c2d87-125">Le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="c2d87-125">The **PollingStatement** binding property.</span></span> <span data-ttu-id="c2d87-126">Vous devez définir cette propriété de liaison à la fois au moment du design et au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2d87-126">You must set this binding property both at design-time and at run-time.</span></span>  
  
-   <span data-ttu-id="c2d87-127">Propriétés de liaison facultative.</span><span class="sxs-lookup"><span data-stu-id="c2d87-127">Optional binding properties.</span></span> <span data-ttu-id="c2d87-128">Ils doivent uniquement être définie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2d87-128">These only have to be set at run-time.</span></span>  
  
-   <span data-ttu-id="c2d87-129">Le **AcceptCredentialsInUri** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="c2d87-129">The **AcceptCredentialsInUri** binding property.</span></span> <span data-ttu-id="c2d87-130">Vous devez définir cette propriété de liaison **true** pendant l’exécution si vous souhaitez activer les informations d’identification dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-130">You must set this binding property to **true** during run-time if you want to enable credentials in the connection URI.</span></span> <span data-ttu-id="c2d87-131">Le nom d’utilisateur et un mot de passe doivent être présents dans l’URI de connexion lorsque vous ajoutez un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-131">The user name and password must be present in the connection URI when you add a service endpoint to the service host.</span></span>  
  
-   <span data-ttu-id="c2d87-132">Le **PollingId** dans l’URI de connexion paramètre de chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="c2d87-132">The **PollingId** query string parameter in the connection URI.</span></span> <span data-ttu-id="c2d87-133">Si vous souhaitez modifier l’espace de noms de l’opération POLLINGSTMT, vous devez définir cette propriété de connexion à la fois au moment de la conception et d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2d87-133">If you want to change the namespace of the POLLINGSTMT operation, you must set this connection property both at design-time and run-time.</span></span>  
  
 <span data-ttu-id="c2d87-134">Pour obtenir une description complète des propriétés de liaison et les paramètres de connexion utilisés pour configurer l’interrogation, consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c2d87-134">For a complete description of the binding properties and connection parameters used to configure polling, see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="c2d87-135">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="c2d87-135">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="c2d87-136">Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour créer un service WCF service contrat (interface) et les classes de prise en charge pour l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-136">You use either the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to create a WCF service contract (interface) and supporting classes for the POLLINGSTMT operation.</span></span>  
  
 <span data-ttu-id="c2d87-137">Lorsque vous vous connectez à la base de données Oracle avec un de ces outils pour générer un contrat de service pour l’opération POLLINGSTMT :</span><span class="sxs-lookup"><span data-stu-id="c2d87-137">When you connect to the Oracle database with either of these tools to generate a service contract for the POLLINGSTMT operation:</span></span>  
  
-   <span data-ttu-id="c2d87-138">Vous devez spécifier le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="c2d87-138">You must specify the **PollingStatement** binding property.</span></span> <span data-ttu-id="c2d87-139">L’adaptateur utilise l’instruction SELECT dans cette propriété de liaison pour générer les métadonnées correctes pour le jeu de résultats de fortement typé retourné par l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-139">The adapter uses the SELECT statement in this binding property to generate the correct metadata for the strongly-typed result set returned by the POLLINGSTMT operation.</span></span>  
  
-   <span data-ttu-id="c2d87-140">Vous pouvez éventuellement spécifier un paramètre PollingId dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-140">You can optionally specify a PollingId parameter in the connection URI.</span></span> <span data-ttu-id="c2d87-141">L’adaptateur utilise ce paramètre pour générer l’espace de noms pour l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-141">The adapter uses this parameter to generate the namespace for the POLLINGSTMT operation.</span></span>  
  
 <span data-ttu-id="c2d87-142">Dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="c2d87-142">In the following examples:</span></span>  
  
-   <span data-ttu-id="c2d87-143">**PollingStatement** est défini sur « Sélectionner * à partir de ACCOUNTACTIVITY de mise à jour ».</span><span class="sxs-lookup"><span data-stu-id="c2d87-143">**PollingStatement** is set to "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE".</span></span>  
  
-   <span data-ttu-id="c2d87-144">**PollingId** est défini sur « AcctActivity ».</span><span class="sxs-lookup"><span data-stu-id="c2d87-144">**PollingId** is set to "AcctActivity".</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="c2d87-145">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="c2d87-145">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="c2d87-146">Le code suivant illustre le contrat de service WCF (interface) généré pour l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-146">The following code shows the WCF service contract (interface) generated for the POLLINGSTMT operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="POLLINGSTMT_OperationGroup")]  
public interface POLLINGSTMT_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)  
    // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT")]  
    void POLLINGSTMT(POLLINGSTMT request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="c2d87-147">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="c2d87-147">The Message Contracts</span></span>  
 <span data-ttu-id="c2d87-148">L’espace de noms de contrat de message est modifié par le paramètre PollingId dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-148">The message contract namespace is modified by the PollingId parameter in the connection URI.</span></span> <span data-ttu-id="c2d87-149">Le message de requête retourne un jeu d’enregistrements de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="c2d87-149">The request message returns a set of strongly-typed records.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="POLLINGSTMT", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", IsWrapped=true)]  
public partial class POLLINGSTMT {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD;  
  
    public POLLINGSTMT() {  
    }  
  
    public POLLINGSTMT(microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD) {  
        this.POLLINGSTMTRECORD = POLLINGSTMTRECORD;  
    }  
}  
```  
  
### <a name="the-data-contract-namespace"></a><span data-ttu-id="c2d87-150">Le Namespace de contrat de données</span><span class="sxs-lookup"><span data-stu-id="c2d87-150">The Data Contract Namespace</span></span>  
 <span data-ttu-id="c2d87-151">Un contrat de données est un contrat formel entre un service et un client qui due décrit l’échange de données.</span><span class="sxs-lookup"><span data-stu-id="c2d87-151">A data contract is a formal agreement between a service and a client that abstractly describes the data to be exchanged.</span></span> <span data-ttu-id="c2d87-152">Autrement dit, afin de communiquer, le client et le service est inutile de partager les mêmes types, les mêmes contrats de données.</span><span class="sxs-lookup"><span data-stu-id="c2d87-152">That is, in order to communicate, the client and the service do not have to share the same types, only the same data contracts.</span></span>  
  
 <span data-ttu-id="c2d87-153">En cas de données des messages de modification, l’espace de noms de contrat de données est également modifiée par le paramètre PollingId (si spécifiée) dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-153">In case of data change messages, the data contract namespace is also modified by the PollingId parameter (if specified) in the connection URI.</span></span> <span data-ttu-id="c2d87-154">Le contrat de données se compose d’une classe qui représente un enregistrement dans le jeu de résultats de requête fortement typée.</span><span class="sxs-lookup"><span data-stu-id="c2d87-154">The data contract is composed of a class that represents a strongly-typed record in the query result set.</span></span> <span data-ttu-id="c2d87-155">Dans cet exemple, les détails de la définition de classe sont omis.</span><span class="sxs-lookup"><span data-stu-id="c2d87-155">The details of the class definition are omitted in this example.</span></span> <span data-ttu-id="c2d87-156">La classe contient des propriétés qui représentent les colonnes dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="c2d87-156">The class contains properties that represent the columns in the result set.</span></span>  
  
 <span data-ttu-id="c2d87-157">Dans l’exemple suivant, la PollingId « AcctActivity » est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c2d87-157">In the following example, the PollingId “AcctActivity” is used.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity {  
    using System.Runtime.Serialization;  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute(Name="POLLINGSTMTRECORD", Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity")]  
    public partial class POLLINGSTMTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
     }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="c2d87-158">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="c2d87-158">WCF Service Class</span></span>  
 <span data-ttu-id="c2d87-159">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="c2d87-159">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="c2d87-160">Le nom du fichier est OracleDBBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="c2d87-160">The name of the file is OracleDBBindingService.cs.</span></span> <span data-ttu-id="c2d87-161">Vous pouvez insérer la logique pour traiter l’opération POLLINGSTMT directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="c2d87-161">You can insert the logic to process the POLLINGSTMT operation directly into this class.</span></span> <span data-ttu-id="c2d87-162">Si vous utilisez svcutil.exe pour générer l’interface de contrat de service, vous devez implémenter cette classe vous-même.</span><span class="sxs-lookup"><span data-stu-id="c2d87-162">If you use svcutil.exe to generate the service contract interface, you must implement this class yourself.</span></span> <span data-ttu-id="c2d87-163">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2d87-163">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : POLLINGSTMT_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)   
        // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void POLLINGSTMT(POLLINGSTMT request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-the-pollingstmt-operation"></a><span data-ttu-id="c2d87-164">Réception de l’opération POLLINGSTMT</span><span class="sxs-lookup"><span data-stu-id="c2d87-164">Receiving the POLLINGSTMT Operation</span></span>  
  
#### <a name="to-receive-polling-data-from-the-oracle-database-adapter"></a><span data-ttu-id="c2d87-165">Pour recevoir des données de l’interrogation de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="c2d87-165">To receive polling data from the Oracle Database adapter</span></span>  
  
1.  <span data-ttu-id="c2d87-166">Utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou svcutil.exe pour générer un service WCF service contrat (interface) et des classes d’assistance pour l’opération POLLINGSTMT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-166">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) and helper classes for the POLLINGSTMT operation.</span></span> <span data-ttu-id="c2d87-167">Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="c2d87-167">For more information, see [Generate a WCF client or a WCF service contract for Oracle Database solution artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span> <span data-ttu-id="c2d87-168">Au minimum, vous devez définir le **PollingStatement** propriété de liaison lorsque vous vous connectez à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c2d87-168">At a minimum, you must set the **PollingStatement** binding property when you connect to the adapter.</span></span> <span data-ttu-id="c2d87-169">Vous pouvez éventuellement spécifier un paramètre PollingId dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-169">You can optionally specify a PollingId parameter in the connection URI.</span></span> <span data-ttu-id="c2d87-170">Si vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous devez définir tous les paramètres de liaison est nécessaire pour votre configuration.</span><span class="sxs-lookup"><span data-stu-id="c2d87-170">If you are using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you should set all of the binding parameters necessary for your configuration.</span></span> <span data-ttu-id="c2d87-171">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="c2d87-171">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="c2d87-172">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="c2d87-172">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="c2d87-173">La méthode POLLINGSTMT de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur s’est produite le traitement des données provenance de l’opération POLLINGSTMT ; Sinon, la méthode ne retourne rien.</span><span class="sxs-lookup"><span data-stu-id="c2d87-173">The POLLINGSTMT method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the POLLINGSTMT operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="c2d87-174">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2d87-174">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  <span data-ttu-id="c2d87-175">Si vous avez utilisé le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer l’interface, vous pouvez implémenter votre logique directement dans le **POLLINGSTMT** méthode dans le texte généré **OracleDBBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="c2d87-175">If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the **POLLINGSTMT** method in the generated **OracleDBBindingService** class.</span></span> <span data-ttu-id="c2d87-176">Cette classe peut être trouvée dans OracleDBBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="c2d87-176">This class can be found in OracleDBBindingService.cs.</span></span> <span data-ttu-id="c2d87-177">Ce code dans cet exemple montre comment des classes le **OracleDBBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="c2d87-177">This code in this example sub-classes the **OracleDBBindingService** class.</span></span>  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
        public class PollingStmtService : OracleDBBindingService  
        {  
            public override void POLLINGSTMT(POLLINGSTMT request)  
            {  
                Console.WriteLine("\nNew Polling Records Received");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                        request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                        request.POLLINGSTMTRECORD[i].AMOUNT,  
                                        request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                        request.POLLINGSTMTRECORD[i].DESCRIPTION);  
                }  
            }  
        }  
        ```  
  
    2.  <span data-ttu-id="c2d87-178">Si vous utilisez svcutil.exe pour générer l’interface, vous devez créer un service WCF qui implémente l’interface et implémenter votre logique dans le **POLLINGSTMT** méthode de cette classe.</span><span class="sxs-lookup"><span data-stu-id="c2d87-178">If you used svcutil.exe to generate the interface, you must create a WCF service that implements the interface and implement your logic in the **POLLINGSTMT** method of this class.</span></span>  
  
3.  <span data-ttu-id="c2d87-179">Créez une instance du service WCF créé à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="c2d87-179">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingStmtService pollingInstance = new PollingStmtService();  
    ```  
  
4.  <span data-ttu-id="c2d87-180">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="c2d87-180">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="c2d87-181">L’URI de la connexion de base ne peut pas contenir userinfoparams ou un query_string.</span><span class="sxs-lookup"><span data-stu-id="c2d87-181">The base connection URI cannot contain userinfoparams or a query_string.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracledb://Adapter") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  <span data-ttu-id="c2d87-182">Créer un **OracleDBBinding** et configurer l’opération d’interrogation en définissant ses propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="c2d87-182">Create an **OracleDBBinding** and configure the polling operation by setting its binding properties.</span></span> <span data-ttu-id="c2d87-183">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="c2d87-183">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="c2d87-184">Au minimum, vous devez spécifier l’instruction de l’interrogation et l’intervalle d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="c2d87-184">At a minimum, you must specify the polling statement and polling interval.</span></span> <span data-ttu-id="c2d87-185">Dans cet exemple, vous spécifiez les informations d’identification en tant que partie de l’URI que vous devez également attribuer le **AcceptCredentialsInUri** à **true**.</span><span class="sxs-lookup"><span data-stu-id="c2d87-185">In this example, you specify the credentials as part of the URI so you must also set the **AcceptCredentialsInUri** to **true**.</span></span>  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    OracleDBBinding binding = new OracleDBBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
  
    // Same as statement specified in Configure Adapter dialog box  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
    // Be sure to set the interval long enough to complete processing before  
    // the next poll  
    binding.PollingInterval = 15;  
    // Polling is transactional; be sure to set an adequate isolation level   
    // for your environment  
    binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
    ```  
  
6.  <span data-ttu-id="c2d87-186">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-186">Add a service endpoint to the service host.</span></span> <span data-ttu-id="c2d87-187">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="c2d87-187">To do this:</span></span>  
  
    -   <span data-ttu-id="c2d87-188">Utilisez la liaison créée à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="c2d87-188">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="c2d87-189">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un PollingId.</span><span class="sxs-lookup"><span data-stu-id="c2d87-189">Specify a connection URI that contains credentials and, if needed, a PollingId.</span></span>  
  
    -   <span data-ttu-id="c2d87-190">Spécifiez le contrat en tant que « POLLINGSTMT_OperationGroup ».</span><span class="sxs-lookup"><span data-stu-id="c2d87-190">Specify the contract as "POLLINGSTMT_OperationGroup".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
    Uri serviceUri = new Uri("oracledb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
    srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
    ```  
  
7.  <span data-ttu-id="c2d87-191">Pour recevoir les données d’interrogation, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-191">To receive polling data, open the service host.</span></span> <span data-ttu-id="c2d87-192">L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="c2d87-192">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    srvHost.Open();  
    ```  
  
8.  <span data-ttu-id="c2d87-193">Pour mettre fin à l’interrogation, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c2d87-193">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c2d87-194">La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.</span><span class="sxs-lookup"><span data-stu-id="c2d87-194">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    srvHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="c2d87-195">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2d87-195">Example</span></span>  
 <span data-ttu-id="c2d87-196">L’exemple suivant montre une requête d’interrogation qui s’exécute sur la table ACCOUNTACTIVITY/SCOTT.</span><span class="sxs-lookup"><span data-stu-id="c2d87-196">The following example shows a polling query that executes against the /SCOTT/ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="c2d87-197">L’instruction après interrogation appelle une fonction d’Oracle qui déplace les enregistrements traités à une autre table /SCOTT/ACCOUNTHISTORY.</span><span class="sxs-lookup"><span data-stu-id="c2d87-197">The post-poll statement invokes an Oracle function that moves the processed records to another table /SCOTT/ACCOUNTHISTORY.</span></span> <span data-ttu-id="c2d87-198">L’espace de noms de l’opération POLLINGSTMT est modifié en définissant le paramètre PollingId à « AccountActivity » dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="c2d87-198">The namespace of the POLLINGSTMT operation is modified by setting the PollingId parameter to "AccountActivity" in the connection URI.</span></span> <span data-ttu-id="c2d87-199">Dans cet exemple, le service WCF pour l’opération POLLINGSTMT est créé en définissant une sous-classe généré **OracleDBBindingService** classe ; Toutefois, vous pouvez implémenter votre logique directement dans la classe générée.</span><span class="sxs-lookup"><span data-stu-id="c2d87-199">In this example, the WCF service for the POLLINGSTMT operation is created by sub-classing the generated **OracleDBBindingService** class; however, you can implement your logic directly in the generated class.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add these three references to use the Oracle adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
using microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity;  
using OracleDBBindingNamespace;  
  
namespace OraclePollingSM  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingStmtService : OracleDBBindingService  
    {  
        public override void POLLINGSTMT(POLLINGSTMT request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
            for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                    request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                    request.POLLINGSTMTRECORD[i].AMOUNT,  
                                    request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                    request.POLLINGSTMTRECORD[i].DESCRIPTION);  
  
            }  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
         }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost srvHost = null;  
  
            // This URI is used to specify the address for the ServiceEndpoint  
            // It must contain credentials and the PollingId (if any) that was used to generate  
            // the WCF service callback interface  
            Uri serviceUri = new Uri("OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
  
            // This URI is used to initialize the ServiceHost. It cannot contain  
            // userinfoparms (credentials) or a query_string (PollingId); otherwise,  
            // an exception is thrown when the ServiceHost is initialized.  
            Uri[] baseUri = new Uri[] { new Uri("OracleDb://Adapter") };  
  
            Console.WriteLine("Sample started, initializing service host -- please wait");  
  
            // create an instanc of the WCF service callback class  
            PollingStmtService pollingInstance = new PollingStmtService();  
  
            try  
            {  
                // Create a ServiceHost with the service callback instance and a base URI (address)  
                srvHost = new ServiceHost(pollingInstance, baseUri);  
  
                // Create and configure a binding for the service endpoint. Note: binding  
                // parameters are set here for clarity but these are already set in the  
                // generated configuration file  
                //  
                // The following properties are set  
                //    AcceptCredentialsInUri (true) to enable credentials in the connection URI for AddServiceEndpoint  
                //    PollingStatement  
                //    PostPollStatement calls PROCESS_ACTIVITY on Oracle. This procedure moves the queried records to  
                //                      the ACCOUNTHISTORY table  
                //    PollingInterval (15 seconds)  
                //    TransactionIsolationLevel   
  
                OracleDBBinding binding = new OracleDBBinding();  
  
                // The Credentials are included in the Connection Uri so set this property true  
                binding.AcceptCredentialsInUri = true;  
  
                // Same as statement specified in Configure Adapter dialog box  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Be sure to set the interval long enough to complete processing before  
                // the next poll  
                binding.PollingInterval = 15;  
  
                // Polling is transactional, be sure to set an adequate isolation level   
                // for your environment  
                binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
  
                // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
                srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
  
                Console.WriteLine("Opening the service host");  
                // Open the service host to begin polling  
                srvHost.Open();  
  
                // Wait to receive request  
                Console.WriteLine("\nPolling started. Returned records will be written to the console.");  
                Console.WriteLine("Hit <RETURN> to stop polling");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an Oracle Error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (srvHost.State == CommunicationState.Opened)  
                    srvHost.Close();  
                else  
                    srvHost.Abort();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2d87-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2d87-200">See Also</span></span>  
 [<span data-ttu-id="c2d87-201">Développer des applications de base de données Oracle à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="c2d87-201">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)