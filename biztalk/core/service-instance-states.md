---
title: "États de l’Instance service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service instances, states
- messages, processing
- states, service instances
ms.assetid: 38189538-72b3-49df-810b-e134362e35ef
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27bb6cac8925055bb8ed5359b3d038c44c136335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-instance-states"></a>États d'instance de service
Lors du traitement d'un message, les actions suivantes sont exécutées :  
  
-   Dans l'emplacement de réception, l'adaptateur de réception (ou le composant de transport) reçoit le message d'une application externe et le soumet à BizTalk Server pour traitement.  
  
    > [!NOTE]
    >  Un message est reçu par le système dans divers formats : XML, un fichier plat, ou sous la forme d’un échange de données informatisé (EDI) entre les entreprises.  
  
-   Le pipeline de réception déchiffre, décode et désassemble le message.  
  
-   Le moteur de messagerie envoie le message et ses propriétés de raccourci, tels que le type et l'origine du message, à la base de données MessageBox.  
  
-   Lorsqu'un abonnement correspondant est détecté, le message est traité selon un ensemble de schémas et de mappages, et parfois selon les règles ou stratégies d'entreprise résidant sur le serveur hôte.  
  
-   Une fois traité, le message obtenu est conservé (écrit) dans la base de données MessageBox. Les propriétés de raccourci ont été modifiées de manière à indiquer où envoyer le message, par exemple, en précisant le port d'envoi à utiliser.  
  
-   Les propriétés de raccourci du message sont évaluées par rapport aux expressions de filtre définies pour le port d'envoi, et la base de données MessageBox remet le message au port d'envoi approprié.  
  
-   Un abonnement à un pipeline d'envoi ou à un port d'envoi doit correspondre au message à envoyer. Le message est chiffré et transmis.  
  
 Chaque processus du cycle génère son propre ensemble d'événements.  
  
 Les messages transitant par BizTalk Server étant traités par des instances de service, celles-ci peuvent présenter divers états. Cette section présente ces états et montre des exemples d'état correspondant aux divers stades du cycle de vie des instances de service.  
  
## <a name="service-instance-states"></a>États d'instance de service  
 Le tableau suivant répertorie les divers états possibles d'une instance de service, avec une explication de chacun d'eux.  
  
|État|Explication|  
|-----------|-----------------|  
|**Point d’arrêt**|Une orchestration active atteint un point d'arrêt, généralement défini par un développeur de solutions BizTalk Server. Cet état est valide uniquement pour les orchestrations.|  
|**Prêt à s’exécuter**|Instance de service qui a été activée, mais dont l'exécution n'a pas encore commencé, généralement à cause d'une indisponibilité temporaire de ressources, comme une charge importante sur le serveur.|  
|**Actif**|Instance de service en cours d'exécution.|  
|**Mise en attente**|L'instance est conservée dans le même état dans la base de données MessageBox et aucun service Windows ne l'exécute.|  
|**Terminé avec des messages ignorés**|L'instance de service s'est terminée, mais elle n'a pas utilisé certains messages.|  
|**Suspendu (peut être repris)**|L'instance est suspendue et peut être reprise. **Important :** la reprise d’une instance de messagerie procède comme suit : <ul><li>reprise d’une instance de messagerie ;</li><li>envoi du message au port d’envoi.</li><li>Le port d’envoi remet le message à l’emplacement de destination, même si son état n’est pas Démarré.</li></ul> <br /><br /> Notez que, lorsque vous interrompez une instance planifiée, puis la reprenez, elle est mise en attente.|  
|**Suspendu (ne peut être repris)**|L'instance est suspendue, mais ne peut pas être reprise. Vous pouvez enregistrer les messages référencés par l'instance, puis terminer l'instance.<br /><br /> Notez que, lorsque vous interrompez une instance planifiée, puis la reprenez, elle est mise en attente.|  
|**Suspension en attente / arrêt en attente**|Il s'agit d'un statut, non d'un état indépendant. Vous pouvez l'associer à d'autres états.<br /><br /> Un message de contrôle de suspension ou d'arrêt a été envoyé à une instance de service, mais n'a pas encore été récupéré par l'instance. Une seule opération en attente est autorisée à la fois. Quand une instance avec une opération en cours devient en attente, vous pouvez y mettre fin.|  
  
### <a name="tracked-service-instance-states"></a>États d'instance de service suivis  
 Le tableau suivant répertorie les divers états de suivi d'instance de service avec une explication pour chacun d'eux.  
  
|État|Explication|  
|-----------|-----------------|  
|**Démarré**|Toute instance de service actuellement dans la base de données MessageBox, par exemple, en état Suspendu (peut être repris) ou Point d'arrêt, s'affiche avec l'état Démarré dans la base de données des suivis BizTalk.|  
|**Terminé**|Le traitement de l'instance de service a été correctement effectué.|  
|**Arrêté**|L'instance de service est terminée.|  
  
## <a name="message-states"></a>États des messages  
 Le tableau suivant répertorie les divers états possibles d'un message, avec une explication pour chacun d'eux.  
  
|État|Explication|  
|-----------|-----------------|  
|**Consommée**|Le message est en cours de traitement par une instance de service.|  
|**Dans le processus**|Le message a été transmis au moteur et est en cours de traitement. Il se trouve dans la mémoire.|  
|**En file d’attente**|L'état Mis en file d'attente englobe les états d'instance Mis en file d'attente (en attente de traitement), Mis en file d'attente (planifié pour une remise ultérieure) et Mis en file d'attente (en attente de nouvel essai).|  
|**En file d’attente (en attente de traitement)**|Le message se trouve dans un scénario de livraison chronologique lorsque de nouvelles tentatives d'envoi ont lieu pour un message précédent sur le port d'envoi pour lequel l'option de livraison chronologique a été activée.|  
|**En file d’attente (planifié pour une remise ultérieure)**|Le message est en attente de transmission par un port d'envoi pour lequel une fenêtre de service est définie.|  
|**En file d’attente (attente de nouvel essai)**|Le message est associé à un port d'envoi qui tente de le renvoyer, car l'URI de destination n'est pas disponible.|  
|**Suspendu**|L'état Exécution suspendue englobe les états Suspendu (peut être repris) et Suspendu (ne peut être repris).|  
|**Suspendu (peut être repris)**|L'exécution de l'instance de service associée au message est interrompue, mais peut être reprise.<br /><br /> La reprise d’une instance de messagerie effectue les opérations suivantes :<br /><br /> -Reprendre l’instance de messagerie.<br />-Envoyer le message au port d’envoi.<br />-Le port d’envoi remet le message à la destination ; même si le port d’envoi n’est pas dans un état démarré.|  
|**Suspendu (ne peut être repris)**|L'exécution de l'instance de service associée au message est interrompue, sans possibilité de reprise.|  
  
## <a name="instance-states-before-and-after-an-operation"></a>États des instances avant et après une opération  
 Le tableau ci-dessous présente les différents états avant et après une opération.  
  
> [!NOTE]
>  Les états initiaux et finaux sont affichés en gras dans la colonne de gauche et la ligne supérieure. L'opération figure dans le corps du tableau.  
  
|État initial|Nouvel état après l'opération|||||||  
|--------------------|------------------------------------------|------|------|------|------|------|------|  
||**Point d’arrêt**|**Actif**|**Mise en attente**|**Suspendu**|**Arrêté**|**Arrêt en attente**|**Suspension en attente**|  
|**Point d’arrêt**|Joindre à partir du débogueur|Continuer à partir du débogueur|Arrêter le service Windows|||Terminate|Suspendre|  
|**Point d’arrêt (en attente)**|Joindre à partir du débogueur|Continuer à partir du débogueur|Arrêter le service Windows|Suspendre|Terminate|||  
|**Prêt à s’exécuter**||||Suspendre|Terminate|||  
|**Planifié**||L'exécution récupère l'instance parce que la fenêtre du service a démarré.||||||  
|**Actif**|||Arrêter le service Windows|||Terminate|Suspendre|  
|**Mise en attente**||L'exécution récupère l'instance.|Arrêter le service Windows|Suspendre|Terminate|||  
|**Suspendu (peut être repris)**|Reprendre au point d'arrêt à partir du débogueur|Reprendre|||Terminate|||  
|**Suspendu (ne peut être repris)**|||||Terminate|||  
|**S’est terminé avec des messages non utilisés**|||||Terminate|||  
|**Suspension en attente**|L'opération Joindre est possible, mais finit généralement par échouer.||Arrêter le service Windows|Requête traitée|L'opération Terminer ne fonctionne que si l'instance est en attente.|||  
|**Arrêt en attente**|L'opération Joindre est possible, mais finit généralement par échouer.||Arrêter le service Windows ; l'instance est en attente.||Requête traitée ou instance en attente.|||  
  
## <a name="instance-states-during-an-operation"></a>États d'instance pendant une opération  
 Le tableau ci-dessous présente les modifications d'état lorsque le système effectue une opération sur une instance.  
  
|État initial|Opération||||||  
|--------------------|---------------|------|------|------|------|------|  
||**Arrêter**|**Suspendre**|**Reprendre**|**Reprendre au point d’arrêt**|**Continuer**|**Attacher**|  
|**Point d’arrêt**|Arrêté|Suspendu|||Actif|Point d’arrêt|  
|**Point d’arrêt (en attente)**|Arrêté|Suspendu|||Actif|Point d’arrêt|  
|**Prêt à s’exécuter**|Arrêté|Suspendu|||||  
|**Planifié**|Arrêté|Suspendu|||||  
|**Actif**|Arrêté|Suspendu|||||  
|**Mise en attente**|Arrêté|Suspendu|||||  
|**Suspendu (peut être repris)**|Arrêté||Actif|Point d’arrêt|||  
|**Suspendu (ne peut être repris)**|Arrêté||||||  
|**S’est terminé avec des messages non utilisés**|Arrêté||||||  
|**Suspension en attente**|Terminée ; ne fonctionne que si l'instance est en attente.|||||Condition de concurrence|  
|**Arrêt en attente**|S’est arrêté ; fonctionne uniquement, lorsque l’instance est en attente.|||||Condition de concurrence|  
  
> [!NOTE]
>  Une condition d'engorgement se produit lorsque le système transmet plusieurs messages de contrôle à l'instance, et que l'ordre dans lequel l'instance les traite n'est pas assuré.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la Page Hub du groupe](../core/using-the-group-hub-page.md)