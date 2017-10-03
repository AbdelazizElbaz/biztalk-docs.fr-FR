---
title: Le portail de gestion ESB et erreur Message visionneuse | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4a1636c-2e45-4ee5-92c2-81c976582da3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9a6e7272e7b707b6ba7650cfb93506c3a54a00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-management-portal-and-fault-message-viewer"></a>Le portail de gestion ESB et l’Afficheur des messages d’erreur
Un composant majeur de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est basé sur un Web portail qui fournit un large éventail d’exception fonctionnalités de notification d’alerte et de gestion ; en outre, il joue le rôle de gestion de la configuration utile (Universal Description, Discovery and Integration Interface d’inscription UDDI). Figure 1 montre la page d’accueil du portail, qui fournit une vue d’ensemble de l’intégrité des applications en cours d’exécution.  
  
 ![Page d’accueil du portail](../esb-toolkit/media/portalhomepage.gif "PortalHomePage")  
  
 **Figure 1**  
  
 **La page d’accueil du portail de gestion ESB**  
  
 Les utilisateurs peuvent sélectionner un message d’erreur affiché dans le portail de gestion ESB pour afficher les propriétés ambiantes et statiques de l’erreur et une liste des messages d’origine contenues dans le message d’erreur, comme indiqué dans la Figure 2.  
  
 ![Page Afficheur des erreurs](../esb-toolkit/media/ch4-faultviewerpage.gif "FaultViewerPage de chapitre 4")  
  
 **Figure 2**  
  
 **La page de la visionneuse de pannes ESB du portail de gestion ESB**  
  
 Les messages d’erreur de ESB affichées dans le portail de gestion ESB peuvent être le résultat d’une erreur dans les valeurs du message d’origine lorsque envoyé pour traitement. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge la fonctionnalité « Réparer et soumettez à nouveau », ce qui permet aux administrateurs ou utilisateurs de modifier les messages ayant échoué et les soumettre à une rampe d’entrée pour le traitement.  
  
 Sélectionnant une de la relation contenant-contenu des messages permet d’ouvrir la page en mode de Message dans la vue des détails du Message, comme indiqué dans la Figure 3. Dans cette vue, les utilisateurs peuvent voir le message de contenu, téléchargez le message ou cliquez sur **modifier** pour basculer en mode édition, où ils peuvent réparer et renvoyez le message.  
  
 ![Page Afficheur de messages](../esb-toolkit/media/ch4-messageviewerpage.gif "MessageViewerPage de chapitre 4")  
  
 **Figure 3**  
  
 **L’Afficheur des messages ESB affichant la vue des détails de l’erreur**  
  
 Pour obtenir une description complète et les options d’utilisation du portail de gestion ESB, y compris la visionneuse de l’erreur, le processus de nouvelle soumission de messages et les techniques utilisées pour la liste, le tri et l’analyse des erreurs, consultez [Administration avec le BizTalk ESB Kit de ressources](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md).