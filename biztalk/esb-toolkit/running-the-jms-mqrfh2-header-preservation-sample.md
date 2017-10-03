---
title: "Exécution de l’exemple de conservation de l’en-tête JMS MQRFH2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65982dca-77e1-4267-9528-26c59237e9b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab840ed1d319f8fd50d3a386e0ffc9b349f61b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-jms-mqrfh2-header-preservation-sample"></a>Exécution de l’exemple de conservation de JMS MQRFH2 en-tête
Cette partie de cet exemple dépose un message dans une file d’attente WebSphere. L’architecture ESB récupère ce message et le dépose dans une file d’attente WebSphere sortant. Cela montre que les Microsoft BizTalk ESB conservent des en-têtes de RFH2 haute fidélité comme un message transite par BizTalk Server.  
  
 **Pour exécuter l’exemple de conservation de l’en-tête**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Exécutez l’utilitaire IBM RfhUtil, puis sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente.  
  
3.  Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK, comme indiqué dans la Figure 1.  
  
     ![Gestionnaire de file d’attente](../esb-toolkit/media/ch6-queuemanager.gif "§ 6-QueueManager")  
  
     **Figure 1**  
  
     **Connexion au Gestionnaire de file d’attente et de la file d’attente sortante dans RfhUtil**  
  
4.  Si la liste déroulante ne contient pas toutes les files d’attente, assurez-vous que le Gestionnaire de file d’attente s’exécute en vérifiant l’élément WebSphere MQ Services, comme indiqué dans la Figure 2.  
  
     ![Web sphère](../esb-toolkit/media/ch6-websphere.gif "§ 6-WebSphere")  
  
     **Figure 2**  
  
     **Vérification que le Gestionnaire de file d’attente est en cours d’exécution dans l’élément WebSphere Services**  
  
5.  Cliquez sur le **ReadFile** bouton dans l’utilitaire RfhUtil et accédez au fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\. Ce fichier contient un lot de messages de test 128, mais l’utilitaire charge seul le premier.  
  
6.  Cliquez sur le **RFH** onglet et assurez-vous que seuls les **JMS** case à cocher est activée.  
  
7.  Cliquez sur le **jms** onglet et assurez-vous que le texte sélectionné **répondre à** file d’attente est ESB. JMS. EXEMPLE. DYNAMICQ1 et que le texte sélectionné **file d’attente de Destination** est ESB. JMS. EXEMPLE. DYNAMICQ2.  
  
8.  Cliquez sur le **principal** onglet, puis cliquez sur le **Q d’écrire** bouton pour écrire le message dans la file d’attente.  
  
9. Après un certain délai pendant que l’application s’exécute, le message de sortie ESB apparaît dans l’architecture ESB. JMS. EXEMPLE. DYNAMICQ1 et ESB. JMS. EXEMPLE. DYNAMICQ1 les files d’attente. Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.  
  
10. Revenez à l’utilitaire RfhUtil et se connecter à des files d’attente pour afficher les messages. Cliquez sur le **MQMD, RFH,** et **jms** onglets pour vérifier que les valeurs d’entrée et de sortie sont identiques pour le message dans la file d’attente de Destination, et que le message dans la file d’attente de la réponse est identique à l’exception, au lieu d’un message JMS standard, le message est marqué comme « autres ».