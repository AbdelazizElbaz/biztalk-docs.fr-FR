---
title: "Comment gérer les erreurs typées contrats dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed fault contracts [orchestrations]
- WCF services, orchestrations
- orchestrations, typed fault contracts
- orchestrations, WCF services
ms.assetid: 5a1a7d22-b0ff-4d09-bebf-4995229784b0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89de313960324ea39ffc8e4eaa4905849dc38b8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-typed-fault-contracts-in-orchestrations"></a><span data-ttu-id="82e7b-102">Gestion des contrats d'erreurs typés dans des orchestrations</span><span class="sxs-lookup"><span data-stu-id="82e7b-102">How to Handle Typed Fault Contracts in Orchestrations</span></span>
<span data-ttu-id="82e7b-103">Cette rubrique décrit la gestion de contrats d'erreurs typées lors de l'utilisation des services WCF dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="82e7b-103">This topic describes how to handle typed fault contracts when consuming WCF services from within orchestrations.</span></span> <span data-ttu-id="82e7b-104">Pour gérer les exceptions d’erreur typées dans les orchestrations, les services WCF que vous utilisez doivent avoir le **FaultContractAttribute** appliqué aux opérations de service ; par conséquent, les erreurs peuvent être levées à l’aide de  **FaultException**\<T > où T peut être n’importe quel contrat de données valide ou d’un type sérialisable à partir des services WCF.</span><span class="sxs-lookup"><span data-stu-id="82e7b-104">To handle typed fault exceptions in orchestrations, the WCF services that you are consuming must have the **FaultContractAttribute** applied to the service operations; therefore, the faults can be thrown by using **FaultException**\<T> where T can be any valid data contract or serializable type from the WCF services.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="82e7b-105">Procédures</span><span class="sxs-lookup"><span data-stu-id="82e7b-105">Procedures</span></span>  
  
#### <a name="to-handle-typed-fault-contracts-in-orchestrations"></a><span data-ttu-id="82e7b-106">Pour gérer les contrats du type erreur dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="82e7b-106">To handle typed fault contracts in orchestrations</span></span>  
  
1.  <span data-ttu-id="82e7b-107">Dans votre Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-107">In your Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="82e7b-108">Dans le **ajouter les éléments générés - \<**  *nom du projet*  **>**  boîte de dialogue le **modèles** section, Sélectionnez **utiliser le Service WCF**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-108">In the **Add Generated Items - \<***Project name***>** dialog box, in the **Templates** section, select **Consume WCF Service**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="82e7b-109">Sur le **Bienvenue dans l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-109">On the **Welcome to the BizTalk WCF Service Consuming Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="82e7b-110">Sur le **source des métadonnées** page, sélectionnez **point de terminaison MEX (Metadata Exchange)**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-110">On the **Metadata source** page, select **Metadata Exchange (MEX) endpoint**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="82e7b-111">Sur le **point de terminaison de métadonnées** page, spécifiez l’URL du service en cours d’exécution qui fournit des métadonnées à télécharger via WS-Metadata Exchange ou Http-Get, par exemple, http://localhost : 8005.</span><span class="sxs-lookup"><span data-stu-id="82e7b-111">On the **Metadata Endpoint** page, specify the URL for the running service that provides metadata for download through WS-Metadata Exchange or Http-Get—for example, http://localhost:8005.</span></span> <span data-ttu-id="82e7b-112">Pour obtenir le document de métadonnées à partir de l’URL, cliquez sur **obtenir**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-112">To get the metadata document from the URL, click **Get**.</span></span> <span data-ttu-id="82e7b-113">Si le service en cours d’exécution requiert une information d’identification de l’utilisateur avec le schéma d’authentification de base, cliquez sur **modifier** pour ouvrir le **Assistant consommation de Service WCF de BizTalk** boîte de dialogue dans laquelle vous pouvez fournir le nom d’utilisateur et mot de passe à utiliser lors de l’accès au service en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="82e7b-113">If the running service requires a user credential with the basic authentication scheme, click **Edit** to open the **BizTalk WCF Service Consuming Wizard** dialog box in which you can supply the user name and password to use when accessing the running service.</span></span> <span data-ttu-id="82e7b-114">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-114">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="82e7b-115">Sur le **récapitulatif des métadonnées de Service WCF importation** page, vérifiez vos paramètres.</span><span class="sxs-lookup"><span data-stu-id="82e7b-115">On the **Import WCF Service Metadata Summary** page, review your settings.</span></span> <span data-ttu-id="82e7b-116">Vous pouvez cliquer sur **précédent** d’apporter des modifications.</span><span class="sxs-lookup"><span data-stu-id="82e7b-116">You can click **Back** to make any changes.</span></span> <span data-ttu-id="82e7b-117">Puis cliquez sur **importation** pour créer les artefacts BizTalk et les types à utiliser pour consommer le service WCF.</span><span class="sxs-lookup"><span data-stu-id="82e7b-117">Then click **Import** to create the BizTalk artifacts and types to be used for consuming the WCF service.</span></span>  
  
7.  <span data-ttu-id="82e7b-118">Sur le **fin de l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-118">On the **Completing the BizTalk WCF Service Consuming Wizard** page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="82e7b-119">Supposez que le service WCF que vous consommez lève l'exception d'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="82e7b-119">Suppose that the WCF service that you are consuming throws the following fault exception:</span></span>  
  
    ```  
    throw new FaultException<MyOperationException>(divideException);  
    ```  
  
     <span data-ttu-id="82e7b-120">L’opération d’erreur sur le port d’envoi attend un message de type **MyOperationException**, mais le message de réponse WCF contient le corps d’erreur entier.</span><span class="sxs-lookup"><span data-stu-id="82e7b-120">The fault operation on the send port expects a message of type **MyOperationException**, but the WCF response message contains the whole fault body.</span></span> <span data-ttu-id="82e7b-121">Par conséquent, vous devez extraire le **MyOperationException** dans le cadre du message en configurant le **le corps du message BizTalk entrant** option dans la boîte de dialogue Propriétés du transport.</span><span class="sxs-lookup"><span data-stu-id="82e7b-121">Therefore, you need to extract the **MyOperationException** part from the message by configuring the **Inbound BizTalk message body** option in the transport properties dialog box.</span></span> <span data-ttu-id="82e7b-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="82e7b-122">For example,</span></span>  
  
    -   <span data-ttu-id="82e7b-123">Sélectionnez **chemin--contenu localisé par le chemin du corps**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-123">Select **Path -- content located by body path**.</span></span>  
  
    -   <span data-ttu-id="82e7b-124">Définissez l'expression du chemin du corps comme suit :</span><span class="sxs-lookup"><span data-stu-id="82e7b-124">Set the Body path expression to the following:</span></span>  
  
        ```  
        /*[local-name()='Fault']/*[local-name()='Detail']/* | /*[local-name()='DivideResponse']  
        ```  
  
    -   <span data-ttu-id="82e7b-125">Sélectionnez **Xml** à partir de la **codage de nœud** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="82e7b-125">Select **Xml** from the **Node encoding** drop-down list.</span></span>  
  
9. <span data-ttu-id="82e7b-126">Vous devez ajouter une étendue et deux gestionnaires d'exception dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="82e7b-126">In the orchestration, you will need to add a scope and two exception handlers.</span></span> <span data-ttu-id="82e7b-127">Un gestionnaire d’exceptions est pour l’opération d’erreur semblable à **MyOperationException** indiqué dans l’exemple précédent, l’autre gestionnaire d’exception est d’intercepter générique **SOAPExceptions**.</span><span class="sxs-lookup"><span data-stu-id="82e7b-127">One exception handler is for the Fault operation, similar to **MyOperationException** shown in the preceding example; the other exception handler is for catching generic **SOAPExceptions**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e7b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82e7b-128">See Also</span></span>  
 <span data-ttu-id="82e7b-129">[Levée des Exceptions d’erreur à partir d’Orchestrations publiées en tant que Services WCF](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="82e7b-129">[How to Throw Fault Exceptions from Orchestrations Published as WCF Services](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md) </span></span>  
 [<span data-ttu-id="82e7b-130">Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF</span><span class="sxs-lookup"><span data-stu-id="82e7b-130">How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service</span></span>](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)