---
title: "Exécute le bloc charger l’exemple de routage basé sur le contenu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e981567-7c6c-4c13-bd5b-597efdd3fb50
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36c5348563cc52c31b14dbceddf35bdb3d5d94cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-bulk-load-content-based-routing-sample"></a>La charge en fonction du contenu routage échantillon global en cours d’exécution
Cette partie de l’exemple illustre une file d’attente des messages que les Microsoft BizTalk ESB achemine vers les files d’attente de destination différent en fonction du nom de la file d’attente spécifié dans chaque message de chargement en masse. Il utilise les fonctionnalités de l’exemple que vous avez vu dans les parties précédentes.  
  
 **Pour exécuter l’exemple d’accès en fonction du contenu de chargement en masse de routage**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Exécutez l’utilitaire IBM RfhUtil, puis sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente, comme dans les 2 partie de cet exemple.  
  
3.  Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK, comme dans les 2 partie de cet exemple.  
  
4.  Cliquez sur le **charge Q** bouton dans l’utilitaire RfhUtil et cliquez sur le fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\. Ce fichier contient un lot de messages test 128 que l’exemple va envoyer à l’architecture ESB.  
  
5.  Dans le **charge** boîte de dialogue, laissez toutes les valeurs définies à leurs valeurs par défaut.  
  
6.  Dans le **charge** boîte de dialogue, cliquez sur **OK** pour ajouter tous les messages à la file d’attente d’entrée.  
  
7.  Après un certain délai pendant que l’application s’exécute, les messages de sortie ESB apparaissent dans les files d’attente de destination différentes, en fonction des valeurs dans leurs en-têtes JMS. Toutefois, tous les spécifient la même réponse à file d’attente, pour toutes les réponses apparaissent dans l’architecture ESB. JMS. EXEMPLE. File d’attente de la réponse. Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.