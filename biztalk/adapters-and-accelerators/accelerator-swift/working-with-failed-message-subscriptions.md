---
title: "Utilisation des échecs de Message abonnements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed messages, subscriptions
- failed messages, developing
- developing, failed message subscriptions
ms.assetid: 8dee0aa8-53bf-40be-866b-f1b83960dc99
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6540259fd6983fd418e57ff700de3f1b550016ec
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="working-with-failed-message-subscriptions"></a>Utilisation des abonnements aux messages ayant échoué
Lorsque le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] processus du désassembleur (traite et valide) un message, il promeut les propriétés pour ce message. Ces propriétés promues fournissent des informations sur l’exactitude et la validité du message, ainsi que des informations relatives au traitement par lots si A4SWIFT a reçu le message dans le cadre d’un traitement entrant. Pour obtenir une liste complète de ces propriétés, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
 Contrairement aux natif désassembleurs de BizTalk, le désassembleur A4SWIFT ne suspend pas un message lors du traitement des erreurs de produit ou des échecs. Au lieu de cela, elle publie le message ayant échoué dans la base de données MessageBox comme il le ferait un message valide. Par conséquent, les messages ayant échoué peuvent contenir des détails de l’erreur dans la base de données MessageBox. Vous pouvez extraire le message à partir de la base de données MessageBox, gérer et réparer le message et même renvoyer le message dans la base de données MessageBox. Vous ne serez pas en mesure d’effectuer la plupart de ces tâches si le message a été réellement *suspendu*.  
  
 Vous pouvez identifier un message A4SWIFT a publié la base de données MessageBox comme erronée ou non par ses propriétés promues. Lors du traitement d’un message ayant échoué, le désassembleur SWIFT remplit et promeut le **A4SWIFT_Failed** propriété et la valeur d’un ou plusieurs des autres propriétés suivantes, avant de publier le message à la base de données MessageBox :  
  
-   **A4SWIFT_ParseErrors** indique le nombre d’erreurs (par exemple, les données mal formées) rencontrées lors du traitement d’analyse.  
  
-   **A4SWIFT_XmlValidationErrors** indique le nombre d’erreurs de validation XML (par exemple, les données non valides ou un type incorrect en ce qui concerne le schéma) rencontrées lors du traitement.  
  
-   **A4SWIFT_BreValidationErrors** indique le nombre d’erreurs de validation du moteur de règles d’entreprise (BRE) (telles que les données violent une règle de réseau rapide) a rencontré au cours du traitement.  
  
-   **A4SWIFT_Failed** est **true** lorsque le nombre des propriétés ci-dessus est supérieur à zéro, ou **false** lorsque le nombre est égal à zéro.  
  
 Ces propriétés sont toutes les parties de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Espace de noms Solutions.A4SWIFT.Property. Pour plus d’informations sur ces autres propriétés promues et, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
 Pour intercepter ou récupérer des messages ayant échoué, vous devez créer des expressions de filtre (abonnements) pour les ports d’envoi ou réception d’orchestration des formes qui incluent des propriétés répertoriées ci-dessus, en tant que **AND** clauses de l’expression.  
  
 Par exemple, pour vous abonner à tous les messages ayant échouées, vous ajoutez la clause suivante (comme un **AND** clause s’il existe d’autres clauses) :  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.A4SWIFT.Property.A4SWIFT_Failed == **true**  
  
 Pour vous abonner aux messages avec uniquement les échecs d’analyse, vous additionner les clauses suivantes :  
  
 **ET** [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.A4SWIFT.Property.A4SWIFT_Failed == **true**,**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.A4SWIFT.Property.A4SWIFT_XmlValidationErrors == 0,**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.A4SWIFT.Property.A4SWIFT_BreValidationErrors == 0 ;  
  
 À l’inverse, pour les ports d’envoi ou orchestrations conçues pour gérer uniquement les messages valides, inclure «**AND**[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.A4SWIFT.Property.A4SWIFT_Failed == **false**« comme une clause dans les expressions de filtre.  
  
> [!NOTE]
>  Si les abonnements se chevauchent, A4SWIFT effectuera tous les abonnements. Autrement dit, si plusieurs services (port d’envoi ou d’orchestration) possède des expressions de filtre remplies par un message particulier, tous les services de ce type seront le même message. Par exemple, si un port d’envoi s’abonne à tous les messages ayant échoué et une orchestration s’abonne aux messages uniquement avec des erreurs d’analyse, les deux abonnements soit remplies lorsque A4SWIFT rencontre des erreurs d’analyse lors du traitement d’un message. Veillez à éliminer les chevauchements indésirables dans les abonnements entre les services.  
  
> [!NOTE]
>  Si A4SWIFT reçoit et traite un message et publie le message à la base de données MessageBox, mais le message ne satisfait pas les abonnements, A4SWIFT suspend le message avec un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] message d’erreur indiquant un manque d’abonnés. Par exemple, si vous avez un abonnement à tous les messages de service « A4SWIFT_Failed == false », mais aucun service de s’abonner aux messages où « A4SWIFT_Failed == true », puis les messages dont l’analyse a échoué ou la validation est effectivement interrompue en raison d’un manque d’abonnés. Ce scénario réellement vous permet de reproduire traditionnelle suspension des messages ayant échoué. Veillez à vous abonner à tous les messages que vous ne souhaitez pas avoir suspendu. Consultez l’aide de BizTalk Server pour plus d’informations sur les abonnements de base de données MessageBox, ports d’envoi, orchestrations et les expressions de filtre.  
  
 Contenu de cette section :  
  
-   [Échecs de messages et objets ErrorCollection](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)