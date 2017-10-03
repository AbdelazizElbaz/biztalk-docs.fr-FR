---
title: "Le Gestionnaire du Port d’envoi dynamique est Configurable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eb8f5ef-af95-4b2e-9a43-6f1240b25855
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11dffbe28d44d7665bc86ff0842c17ea01f7b3d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-send-port-handler-is-configurable"></a>Le Gestionnaire du Port d’envoi dynamique est Configurable
Lors de la création d’un port d’envoi dynamique, un gestionnaire d’envoi d’adaptateur peut être configuré pour *chaque* adaptateur installé. Examinez le cas suivant :  
  
 **Scénario**  
  
 Il existe deux itinéraires ESB dans une application. L'itinéraire 1 utilise un port d'envoi dynamique pour envoyer des données à un partage de fichier. L'itinéraire 2 utilise un port d'envoi dynamique pour envoyer un courrier électronique. Avant, les ports d'envoi dynamiques étaient exécutés dans l'hôte par défaut de l'adaptateur. L'itinéraire 1 est conçu pour cibler un scénario de petit volume de messages de taille élevée. L'itinéraire 2 cible un scénario de volume élevé de messages de petite taille. Étant donné qu’il existe uniquement un hôte par défaut pour un adaptateur, tous les messages sont routés à l'aide du même hôte, ce qui réduit les performances.  
  
 **La modification**  
  
 Pour améliorer les performances des ports d'envoi dynamiques, un gestionnaire d'envoi d'adaptateur peut être configuré pour utiliser un hôte. Dans le scénario ESB, l'itinéraire 1 utilise HostA pour envoyer des données à un partage de fichiers. L'itinéraire 2 utilise le port HostB pour envoyer des courriers électroniques.  
  
## <a name="select-a-send-handler"></a>Sélection d'un gestionnaire d'envoi  
 Lors de la création d'un port d'envoi unidirectionnel dynamique ou d'un port d'envoi dynamique avec sollicitation-réponse, le gestionnaire d'envoi peut être configuré pour chaque adaptateur installé. Étapes :  
  
1.  Dans le **Administration de BizTalk Server** de la console, développez  **groupe BizTalk [*GroupName*] **, développez **Applications**, puis développez l’application pour contenir le port d’envoi.  
  
2.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel dynamique** ou **Port d’envoi dynamique avec sollicitation-réponse**.  
  
3.  Dans **propriétés**, cliquez sur **configurer**.  
  
     Les adaptateurs sont répertoriés avec le gestionnaire d'envoi par défaut. Cliquez sur la flèche pointant vers le bas pour sélectionner un autre hôte.  
  
4.  Cliquez sur **OK** enregistrer les paramètres.  
  
5.  Désinscrivez, puis réinscrivez le nouveau port d'envoi dynamique.  
  
6.  Redémarrez l'instance de l'hôte d'origine.  
  
7.  Redémarrez la nouvelle instance de l'hôte.  
  
 Autres options de configuration du port d'envoi :  
  
-   [Configuration des options avancées de transport pour un port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267697)  
  
-   [Comment configurer les Options de Transport secondaire pour un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267698)  
  
-   [Comment configurer les mappages sortants pour un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267699)  
  
-   [Comment configurer des filtres pour un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267700)  
  
-   [Comment attribuer un certificat à un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267701)  
  
-   [Comment configurer le suivi d’un Port d’envoi](http://go.microsoft.com/fwlink/p/?LinkId=267702)  
  
 Les hôtes différents peuvent être ajustés. Les liens suivants traitent de l'optimisation des performances :  
  
 [Optimisations générales de BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkId=267703)  
  
 [Gestion des paramètres de performances de BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkId=267704)