---
title: "Vue d’ensemble de la création d’une commande RFC dans un SAP à utiliser avec l’adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Créer une demande de changement, RFC destination et envoyer une demande de changement du système SAP - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 802a2e33b8bc902dc784276ce7c1d9c3f37f3b12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-and-send-an-rfc-in-sap"></a>Créer et envoyer une demande de changement dans SAP
Répertorie les principales tâches à effectuer sur le système SAP pour créer une demande de changement. Chaque tâche peut impliquer des procédures très détaillées. Par conséquent, nous vous recommandons de contacter votre administrateur SAP pour effectuer ces tâches, ou reportez-vous au Guide de SAP.  
  
## <a name="create-an-rfc"></a>Créer une demande de changement  
  
1.  Démarrez l’interface utilisateur graphique SAP.  
  
2.  Accédez à la Transaction SE37 (Générateur de fonction), entrez le nom de la RFC, puis cliquez sur **créer**.  
  
3.  Entrez un groupe fonction existant sous lequel la demande de modification est créée, une brève description de la RFC, puis cliquez sur **enregistrer**.  
  
4.  Dans le **attributs** onglet, sélectionnez le **Remote-Enabled Module** case d’option.  
  
5.  Dans le **importer** , entrez les paramètres d’importation. Ces paramètres sont utilisés pour passer les données externes au module de fonction.  
  
6.  Dans le **exporter** , entrez les paramètres d’exportation.  
  
7.  Dans le **Changing** , entrez les paramètres de modification.  
  
8.  Dans le **Tables** , entrez les noms de table.  
  
9. Dans le **Exceptions** , entrez les exceptions pour gérer les erreurs.  
  
10. Dans le **Code Source** , entrez le code source (logique) pour le document RFC.  
  
11. Cliquez sur le **activer** icône dans la barre d’outils pour activer le module de fonction.  

## <a name="create-an-rfc-destination"></a>Créer une destination RFC  
  
1.  Démarrez l’interface utilisateur graphique SAP.  
  
2.  Accédez à la Transaction SM59 (afficher et mettre à jour les Destinations RFC).  
  
3.  Dans la barre de menus, cliquez sur **créer**.  
  
4.  Entrez la destination RFC, le type de connexion, la description, puis appuyez sur ENTRÉE.  
  
5.  Sélectionnez le **programme de serveur inscrit** case d’option, entrez l’ID de programme, un hôte de passerelle et un service de passerelle.  
  
6.  Enregistrez la destination RFC.  

## <a name="send-an-rfc-from-an-sap-system"></a>Envoyer une demande de changement d’un système SAP  
  
1.  Démarrez l’interface utilisateur graphique SAP.  
  
2.  Créer un système logique à l’aide de la transaction de BD54.  
  
3.  Créer une destination RFC dans les connexions TCP/IP à l’aide de la transaction de SM59.  
  
4.  Créer un port à l’aide de la transaction de WE21 et l’attacher à la destination RFC créée dans la dernière étape.  
  
5.  Déclencher une commande RFC à l’aide de SE37. Ce document RFC doit contenir la logique pour effectuer une demande de changement de l’appel à une application externe et puis recevoir une réponse à partir de cette application.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)