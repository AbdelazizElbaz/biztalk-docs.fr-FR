---
title: "Didacticiel 2 : EDI Interface Developer Tutorial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d10fb650-cbb9-41e5-a80d-06afd0513814
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cb84454d2570ae6833847b598b55af6cf7777e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-edi-interface-developer-tutorial"></a>Didacticiel 2 : EDI Interface Developer Tutorial.
Ce didacticiel décrit l'utilisation de la fonctionnalité EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le cadre d'un scénario pour développeur d'interface.  
  
 **Scénario du didacticiel**  
  
 Votre partenaire commercial envoie des bons de commande à votre entreprise à l'aide du document informatisé 850 ANSI X12 Version 4010 (message 850). Votre entreprise utilise une application interne (OrderSystem) pour traiter les bons de commande.  
  
 Développeur d'interface, vous êtes un responsable de la conception de l'interface entre le message 850 reçu de votre partenaire commercial et le système OrderSystem interne de votre entreprise. Votre partenaire commercial requiert un accusé de réception fonctionnel (997) pour chaque message 850 qu'il envoie.  
  
 Pour faciliter la compréhension des références, les identificateurs suivants sont utilisés :  
  
|Entité|Identificateur|  
|------------|----------------|  
|Votre entreprise|OrderSystem|  
|Votre partenaire commercial|Fabrikam|  
  
 Le flux de messages de la solution terminée ressemble à ce qui suit :  
  
 ![Flux de messages EDI Interface Developer Tutorial](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")  
  
 **Flux de messages**  
  
 La solution de ce didacticiel effectue les opérations suivantes :  
  
1.  réception d'un échange de fichier plat de la part du partenaire commercial Fabrikam ;  
  
    > [!NOTE]
    >  Les événements dans cette liste peuvent se produire dans un ordre différent de celui indiqué.  
  
2.  validation de l'échange EDI selon son schéma, désassemblage du message en XML, puis déplacement du message XML dans la base de données MessageBox ;  
  
3.  génération d'un accusé de réception 997 vers l'échange EDI reçu, puis déplacement dans la base de données MessageBox ;  
  
4.  récupération du message 997 XML par un port d'envoi unidirectionnel, puis assemblage de l'échange du message 997 EDI ;  
  
5.  envoi de l'échange 997 à Fabrikam.  
  
6.  Récupération du XML de message par un port d’envoi unidirectionnel, puis assemblage de l’échange du message EDI.  
  
7.  envoi de l'échange EDI à OrderSystem.  
  
 **Configuration**  
  
 Dans ce didacticiel, vous allez effectuer les actions suivantes :  
  
-   configuration de BizTalk pour attendre le message 850 de votre partenaire commercial et renvoyer un accusé de réception 997 ;  
  
-   utilisation d'un mappage BizTalk pour convertir les données du message 850 au format requis par le système de commande (OrderSystem). Ce mappage est inclus dans les fichiers de didacticiel dans le Kit de développement logiciel (SDK) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   configuration d'un port de réception pour la réception du message 850 ;  
  
-   configuration d'un port d'envoi pour l'envoi du message 850 à OrderSystem au format approprié ;  
  
-   configuration d'un port d'envoi pour l'abonnement à l'accusé de réception 997 généré par BizTalk et acheminé en réponse au partenaire commercial, Fabrikam.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Préparer le didacticiel pour développeur d’Interface EDI](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)  
  
-   [Étape 2 : Mettre à jour et déployer la Solution du didacticiel](../core/step-2-update-and-deploy-the-tutorial-solution.md)  
  
-   [Étape 3 : Configurer un tiers et un profil d’entreprise pour votre organisation](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
-   [Étape 4 : Configurer un tiers et un profil d’entreprise pour votre partenaire commercial](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)  
  
-   [Étape 5 : Configurer un Port de réception et l’emplacement de réception](../core/step-5-configure-a-receive-port-and-receive-location.md)  
  
-   [Étape 6 : Configurer un Port d’envoi pour envoyer des données à votre organisation](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)  
  
-   [Étape 7 : Configurer un Port d’envoi pour envoyer l’accusé de réception à votre partenaire commercial](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)  
  
-   [Étape 8 : Configurer l’accord de partenariat commercial entre les Parties](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)  
  
-   [Étape 9 : Tester la Solution EDI](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de BizTalk Server](../core/biztalk-server-tutorials.md)