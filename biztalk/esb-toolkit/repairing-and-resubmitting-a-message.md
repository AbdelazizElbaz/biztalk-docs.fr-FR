---
title: "La réparation et la soumettre à nouveau un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd720b4-44a2-4c44-bf6e-8cf5e9ded1aa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e524ffca1b79032dce55f74e195032d14ec1bf9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-and-resubmitting-a-message"></a>La réparation et la soumettre à nouveau un Message
Pour réparer et renvoyer un message ayant échoué, utilisez la page d’erreurs du portail de gestion ESB.  
  
### <a name="to-repair-and-resubmit-a-message-for-processing"></a>Réparer et de renvoyer un message pour le traitement  
  
1.  Recherchez le message d’erreur souhaité sur le [portail défauts de Page](../esb-toolkit/portal-faults-page.md) page du portail de gestion ESB. Utilisez les fonctionnalités de filtrage dans la page d’erreurs pour rechercher un message spécifique. Renseignez les contrôles pour récupérer tous les messages. Notez que le filtrage sur une base de données de l’erreur très volumineux peut prendre plusieurs secondes pour afficher les résultats appropriés. La figure 1 illustre la page d’erreurs.  
  
     ![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")  
  
     **Figure 1**  
  
     **La page d’erreurs du portail de gestion ESB**  
  
2.  Cliquez n’importe où dans la ligne du message d’erreur souhaité pour ouvrir la [Afficheur des messages d’erreur Portal](../esb-toolkit/portal-fault-message-viewer.md) page [vue des détails d’erreur](../esb-toolkit/fault-details-view.md).  
  
3.  Faites défiler vers le bas de la vue Détails de l’erreur à la liste des messages contenus dans le message d’erreur. La figure 2 illustre les **Messages** section de la page de la visionneuse de l’erreur.  
  
     ![Section des messages](../esb-toolkit/media/ch8-messagessection.gif "Ch8-MessagesSection")  
  
     **Figure 2**  
  
     **La section des Messages de la page de la visionneuse de l’erreur du portail de gestion ESB**  
  
4.  Cliquez sur l’identificateur de message du message que vous souhaitez soumettre à nouveau. Cette opération ouvre le message dans [affichage Détails](../esb-toolkit/message-details-view.md), qui affiche les détails du message individuel et le contenu du message, comme illustré dans la Figure 3.  
  
     ![Afficheur de messages](../esb-toolkit/media/ch8-messageviewer.gif "Ch8-MessageViewer")  
  
     **Figure 3**  
  
     **La page de l’Afficheur des messages du portail de gestion ESB**  
  
5.  Cliquez sur le **modifier** lien situé sous la zone de texte qui contient le contenu du message pour basculer en mode édition, puis modifier le contenu du message en fonction des besoins. Par exemple, vous devrez peut-être modifier les paramètres d’appels de méthode de service contenues dans le message. Notez que vous devez respecter le style document natif (par exemple, XML ou le format de fichier plat) pour empêcher les refus du message lorsque renvoyé. La figure 4 illustre les **détails du Message** section de la page de l’éditeur de Message.  
  
     ![Les détails du message](../esb-toolkit/media/ch8-messagedetails.gif "Ch8-MessageDetails")  
  
     **Figure 4**  
  
     **La section Détails du Message de la page de l’Afficheur des messages du portail de gestion ESB**  
  
6.  Après avoir modifié le message, sélectionnez un emplacement de la nouvelle soumission dans la liste déroulante sous la zone de texte du message. Cette liste montre la liste récupérée dynamiquement des points de terminaison disponibles. Vous devez sélectionner un point de terminaison configuré comme un point de terminaison renvoyés. Les points de terminaison suivants conviennent pour la nouvelle soumission :  
  
    -   **WCF rampe d’entrée**. Ce point de terminaison est ESB itinéraire Services WCF rampe et est disponible uniquement pour les fichiers XML. Le fichier Web.config du portail définit l’URL pour cette rampe d’entrée.  
  
    -   **SOAP-démarrage**. Ce point de terminaison est ESB itinéraire Services ASMX rampe et est disponible uniquement pour les fichiers XML. Le fichier Web.config du portail définit l’URL pour cette rampe d’entrée.  
  
    -   **Un emplacement à l’aide de l’adaptateur HTTP BizTalk de réception**. Cette option est disponible pour les fichiers XML et les fichiers plats.  
  
7.  Cliquez sur le **renvoyer** lien pour renvoyer le message. Un message indiquant le **état de la nouvelle soumission** s’affiche sous la zone de texte du contenu du message.  
  
8.  Si nécessaire, ouvrez le [Page du journal d’Audit](../esb-toolkit/audit-log-page.md) à partir de la **Admin** onglet pour confirmer la nouvelle soumission de message, comme illustré dans la Figure 5.  
  
     ![La page AuditLog](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8-AuditLogPageSmallView")  
  
     **Figure 5**  
  
     **La page journal d’Audit du portail de gestion ESB**