---
title: "Solution orientée services de composants du Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, pipelines
- pipelines, service solutions
- service solution tutorial, assemblies
- service solution tutorial, components [BizTalk Server]
- service solution tutorial, client applications
- assemblies, service solutions
- orchestrations, service solutions
- client applications, service solutions
- back-end systems
- service solution tutorial, orchestrations
- service solution tutorial, back-end applications
ms.assetid: 97b7b754-abfb-48f9-87bf-7fe171121166
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a50743b178f9394c74b137e265532542af2b579c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="components-of-the-service-oriented-solution"></a>Solution orientée services de composants du Service
Cette section décrit les principaux composants BizTalk Server de la solution orientée services. Le diagramme suivant montre les principaux composants de la solution :  
  
 ![Diagramme de flux de Solution orientée services](../core/media/service-oriented-flow-diagram.gif "Service_Oriented_Flow_Diagram")  
  
 La solution orientée services possède trois versions des orchestrations :  
  
-   Une version dans laquelle les trois applications principales sont toutes en version stub  
  
-   Une version dans laquelle les trois applications principales sont toutes appelées inline  
  
-   Une version qui utilise des adaptateurs pour se connecter aux applications  
  
 Toutes les versions des orchestrations apparaissent dans le répertoire SDK\Scenarios\SO\BTSSoln\Orchestrations.  
  
 La version Inline des orchestrations offre le temps de latence le plus faible dans la solution entre les demandes et les réponses.  
  
 Pour plus d’informations sur les fichiers source, consultez [inventaire des fichiers de la Solution orientée services](../core/file-inventory-for-the-service-oriented-solution.md).  
  
## <a name="orchestrations-in-the-service-oriented-solution"></a>Orchestrations dans la solution orientée services  
 Trois orchestrations, **CustomerServiceReceiveSend**, **CustomerServiceNativeRequestResponse**, et **CustomerService** constituent la majeure de la solution. Le **CustomerServiceReceiveSend** et **CustomerServiceNativeRequestResponse** orchestrations agissent en tant que les serveurs frontaux qui appellent le **CustomerService** orchestration. Le **CustomerService** orchestration exécute la plupart des travaux : envoi de demandes pour les applications principales, collecte de réponses, combinaison de réponses dans un message unique et envoi du message approprié frontal orchestration. Étant donné que les orchestrations frontales appellent le **CustomerService** orchestration, les orchestrations frontales attendent le **CustomerService** orchestration terminée.  
  
 La solution expose le **CustomerServiceNativeRequestResponse** orchestration en tant que service Web. Le **CustomerServiceReceiveSend** orchestration prend des messages à partir d’une file d’attente MQSeries.  
  
## <a name="back-end-applications"></a>Applications principales  
 La solution orientée services communique avec trois applications principales :  
  
-   Le **PaymentTracker** application renvoie une liste simulée de paiements récents. **PaymentTracker** lit la demande à partir d’une file d’attente MQSeries et envoie la réponse à une autre file d’attente de MQSeries.  
  
-   Le **PendingTransaction** application signale la somme des transactions en attente sur le compte client. L'application est un service Web qui, à son tour, utilise Microsoft Host Integration Server (HIS) pour communiquer avec un programme CICS/COBOL sur un macroordinateur.  
  
-   L'application SAP fournit des informations sur la limite de crédit générale du client. La solution se connecte à l'application SAP comme un service Web. L'application utilise l'adaptateur SAP dans [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour communiquer avec un système SAP.  
  
## <a name="pipelines"></a>Pipelines  
 La solution orientée services utilise des pipelines par défaut, sauf à deux emplacements : le pipeline de réception pour le **CustomerServiceReceiveSend** orchestration et le **CustomerService** envoi de l’orchestration pipeline à la **PaymentTracker**. Les deux pipelines utilisent des composants personnalisés.  
  
 Le pipeline de réception pour **CustomerServiceReceiveSend** inclut un composant résolution du tiers personnalisé, **composant de Pipeline Ticket SSO**. Les messages qui la **CustomerServiceReceiveSend** orchestration reçoit n’ont pas d’informations d’identification. Cela simule ce qui se passerait si les messages provenaient d'un système de réponse vocal interactif. Le composant de pipeline personnalisé ajoute des informations d'identification à l'aide du compte de service de l'hôte de réception BizTalk.  
  
 En revanche, les messages de la **CustomerSericeNativeRequestResponse** orchestration reçoit déjà disposer d’informations d’identification. Comme le répertoire virtuel pour le service Web est configuré pour la sécurité intégrée et que l'emplacement de réception SOAP est configuré pour intégrer l'authentification unique de l'entreprise, l'adaptateur SOAP génère un ticket pour le message.  
  
 L’autre pipeline personnalisé s’affiche dans le **CustomerService** pipeline d’envoi pour le **PaymentTracker** application. Le composant, Composant de pipeline qui définit l'en-tête MQSeries, définit des valeurs pour les deux propriétés d'en-tête de message MQSeries. Le composant définit le premier, le Format de données de Message (**MQMD_Format**), pour indiquer le message sous la forme d’un **MQCIH** structure, une structure couramment utilisé pour communiquer avec des programmes CICS. La seconde, le format des données elles-mêmes dans le **MQCIH** structure (**MQCIH_Format**), est définie pour afficher le message est une chaîne.  
  
 À l’aide de la **MQCIH** format permet de transmettre l’ID utilisateur et un mot de passe dans le **MQCIH** structure. Applications associées SSO mappent l’ID d’utilisateur Windows de l’application BizTalk pour pseudos du suivi des système de paiement passé dans le **MQCIH** structure.  
  
> [!NOTE]
>  La version Inline de la solution utilise les mêmes pipelines en les appelant à partir de l'orchestration. Cela permet de réutiliser le code de pipeline.  
  
## <a name="client-application"></a>Application cliente  
 La solution comprend une application cliente écrite en C#. Vous pouvez utiliser l'application pour envoyer des demandes en tant que messages SOAP ou MQSeries et examiner les résultats.  
  
## <a name="other-assemblies"></a>Autres assemblys  
 L'application inclut plusieurs assemblys auxiliaires qui ne figurent pas dans le diagramme récapitulatif ci-avant. Le **utilitaires** les fonctions d’utilitaire assembly pour la solution.  
  
 Le **ErrorHelper** assembly contient des classes pour convertir les codes d’erreur en messages et pour convertir des messages d’erreur en codes d’erreur.  
  
 Le **ServiceLevelTracking** assembly inclut des méthodes d’assistance à l’aide de l’analyse BAM (Business Activity) API pour effectuer le suivi des données de l’accord de niveau de service.  
  
 Le **ConfigHelper** assembly contient des méthodes d’assistance pour récupérer les valeurs de configuration de la solution à partir de la **SSOConfigStore** application.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)   
 [Solution orientée services l’inventaire des fichiers pour le Service](../core/file-inventory-for-the-service-oriented-solution.md)