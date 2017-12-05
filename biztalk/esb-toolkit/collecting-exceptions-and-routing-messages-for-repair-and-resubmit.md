---
title: "Collecte des Exceptions et le routage des Messages pour la réparation et soumettez à nouveau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a61658a-0bac-4802-b506-02e61a3d2a9b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a1d080cc3b87cf371729c51e1b1f26e07ae521e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="collecting-exceptions-and-routing-messages-for-repair-and-resubmit"></a>Collecte des Exceptions et le routage des Messages pour la réparation et soumettez à nouveau
Dans ce cas de figure, un gestionnaire d’exceptions personnalisé récupère un message d’erreur reçu via un service Web et l’achemine vers un fichier de disque dans un format compatible avec un modèle InfoPath inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. L’utilisateur peut ouvrir le fichier à l’aide de Microsoft InfoPath, modifier le contenu du message et renvoyer le message pour le traitement, comme illustré dans la Figure 1.  
  
 ![Collecte de réparation des Exceptions](../esb-toolkit/media/ch3-collectingexceptionsrepair.gif "Ch3-CollectingExceptionsRepair")  
  
 **Figure 1**  
  
 **Routage d’un message pour la réparation et renvoyés**  
  
 L’exemple de réparation et soumettez à nouveau gestionnaire d’exceptions personnalisé fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Quand un processus dans une orchestration rencontre une erreur, le Gestionnaire d’exceptions dans cette orchestration génère et publie un message d’erreur ESB. Ce message d’erreur inclut, dans sa charge utile, les messages (y compris leurs propriétés de contexte qui sont associées à BizTalk Server) qui ont été « en vol » lorsque l’exception s’est produite et l’exception actuelle est interceptée par le moteur d’Orchestration BizTalk. Après la publication d’un message d’erreur ESB, il est la file d’attente une orchestration d’abonnement (un gestionnaire d’exceptions personnalisé) qui extrait et inspecte les messages en vol et l’objet d’exception système et achemine les messages en cours dans un dossier, à partir de laquelle un utilisateur peut modifier le message à l’aide d’InfoPath et le renvoyer à BizTalk Server pour traitement.  
  
 Pour plus d’informations, consultez [en cours d’exécution la réparation et la soumettre à nouveau une Exception personnalisée, exemple de gestionnaire](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md).