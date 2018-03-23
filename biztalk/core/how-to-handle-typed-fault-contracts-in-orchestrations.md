---
title: Comment gérer les erreurs typées contrats dans les Orchestrations | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- typed fault contracts [orchestrations]
- WCF services, orchestrations
- orchestrations, typed fault contracts
- orchestrations, WCF services
ms.assetid: 5a1a7d22-b0ff-4d09-bebf-4995229784b0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a7643c4a39785018368572d721eed3ef6545c6b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-handle-typed-fault-contracts-in-orchestrations"></a>Gestion des contrats d'erreurs typés dans des orchestrations
Cette rubrique décrit la gestion de contrats d'erreurs typées lors de l'utilisation des services WCF dans les orchestrations. Pour gérer les exceptions d’erreur typées dans les orchestrations, les services WCF que vous utilisez doivent avoir le **FaultContractAttribute** appliqué aux opérations de service ; par conséquent, les erreurs peuvent être levées à l’aide de  **FaultException**\<T\> où T peut être n’importe quel contrat de données valide ou d’un type sérialisable à partir des services WCF.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-handle-typed-fault-contracts-in-orchestrations"></a>Pour gérer les contrats du type erreur dans les orchestrations  
  
1.  Dans votre Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans l’Explorateur de solutions, cliquez sur votre projet, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés - \< ***nom du projet*** \>**  boîte de dialogue le **modèles** section, sélectionnez **consommer de WCF Service**, puis cliquez sur **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **suivant**.  
  
4.  Sur le **source des métadonnées** page, sélectionnez **point de terminaison MEX (Metadata Exchange)**, puis cliquez sur **suivant**.  
  
5.  Sur le **point de terminaison de métadonnées** page, spécifiez l’URL du service en cours d’exécution qui fournit des métadonnées à télécharger via WS-Metadata Exchange ou Http-Get, par exemple, http://localhost : 8005. Pour obtenir le document de métadonnées à partir de l’URL, cliquez sur **obtenir**. Si le service en cours d’exécution requiert une information d’identification de l’utilisateur avec le schéma d’authentification de base, cliquez sur **modifier** pour ouvrir le **Assistant consommation de Service WCF de BizTalk** boîte de dialogue dans laquelle vous pouvez fournir le nom d’utilisateur et mot de passe à utiliser lors de l’accès au service en cours d’exécution. Cliquez sur **Suivant**.  
  
6.  Sur le **récapitulatif des métadonnées de Service WCF importation** page, vérifiez vos paramètres. Vous pouvez cliquer sur **précédent** d’apporter des modifications. Puis cliquez sur **importation** pour créer les artefacts BizTalk et les types à utiliser pour consommer le service WCF.  
  
7.  Sur le **fin de l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **Terminer**.  
  
8.  Supposez que le service WCF que vous consommez lève l'exception d'erreur suivante :  
  
    ```  
    throw new FaultException<MyOperationException>(divideException);  
    ```  
  
     L’opération d’erreur sur le port d’envoi attend un message de type **MyOperationException**, mais le message de réponse WCF contient le corps d’erreur entier. Par conséquent, vous devez extraire le **MyOperationException** dans le cadre du message en configurant le **le corps du message BizTalk entrant** option dans la boîte de dialogue Propriétés du transport. Par exemple :  
  
    -   Sélectionnez **chemin--contenu localisé par le chemin du corps**.  
  
    -   Définissez l'expression du chemin du corps comme suit :  
  
        ```  
        /*[local-name()='Fault']/*[local-name()='Detail']/* | /*[local-name()='DivideResponse']  
        ```  
  
    -   Sélectionnez **Xml** à partir de la **codage de nœud** liste déroulante.  
  
9. Vous devez ajouter une étendue et deux gestionnaires d'exception dans l'orchestration. Un gestionnaire d’exceptions est pour l’opération d’erreur semblable à **MyOperationException** indiqué dans l’exemple précédent, l’autre gestionnaire d’exception est d’intercepter générique **SOAPExceptions**.  
  
## <a name="see-also"></a>Voir aussi  
 [Levée des Exceptions d’erreur à partir d’Orchestrations publiées en tant que Services WCF](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)   
 [Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)