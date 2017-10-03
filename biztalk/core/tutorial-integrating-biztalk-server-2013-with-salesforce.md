---
title: "Didacticiel : Intégration de BizTalk Server 2013 avec Salesforce | Documents Microsoft"
description: "Utiliser Service Bus et BIzTalk Server pour intégrer avec Salesforce"
ms.custom: 
ms.date: 12/07/2015
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c9ae51-3f48-4086-883b-ab4d5b6e62e3
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af013bc97ae9618dc19cab57d52fcb4829f0842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-integrating-biztalk-server-2013-with-salesforce"></a>Didacticiel : Intégration de BizTalk Server 2013 avec Salesforce
Relecteurs : [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/), [Steef Jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]introduit quelques nouveaux adaptateurs qui créent beaucoup de scénarios hybrides, impliquant des locaux et des technologies Azure désormais possibles. Dans ce didacticiel, nous verrons comment intégrer une entité purement cloud comme Salesforce avec un serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur site à l'aide de certains de ces nouveaux adaptateurs et [!INCLUDE[winazure](../includes/winazure-md.md)]. Avant de commencer, essayons de comprendre l'objectif métier que nous essayons de réaliser en intégrant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec Salesforce.  
  
 Nous pourrions également créer des solutions hybrides impliquant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et Salesforce avec la version précédente de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], mais la solution serait beaucoup plus complexe puisqu'elle impliquerait une interaction avec Salesforce en consommant un service Web (SOAP). Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les nouveaux adaptateurs, la solution est beaucoup plus simple.  
  
## <a name="business-scenario"></a>Scénario d'entreprise  
 Northwind utilise le système CRM en ligne de Salesforce comme solution pour effectuer le suivi des clients dans le pipeline des ventes. Chaque fois qu'une opportunité de vente est créée dans le système Salesforce, Northwind veut que ses systèmes sur site, comme [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], en reçoivent notification de façon que les systèmes en aval puissent collecter les données et lancer d'autres processus pertinents. Northwind prévoit d'implémenter cette solution en utilisant les nouveaux adaptateurs disponibles avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et également en y intégrant quelques composants de [!INCLUDE[winazure](../includes/winazure-md.md)]. Voici à quoi s'apparente le flux de données de bout en bout pour la solution :  
  
-   Un commercial crée une « opportunité » dans le système Salesforce.  
  
-   Lorsque le statut de l'opportunité est défini sur « Fermées/gagnées », une notification est envoyée à un point de terminaison de relais hébergé sur [!INCLUDE[winazure](../includes/winazure-md.md)].  
  
-   En utilisant le nouvel adaptateur WCF-BasicHttpRelay, les informations de notification sont transmises au système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergé sur site.  
  
-   En reprenant les informations reçues dans le cadre de la notification, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] appelle un point de terminaison REST dans Salesforce, en utilisant le nouvel adaptateur WCF-WebHttp, pour obtenir plus d'informations sur l'opportunité.  
  
-   Enfin, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les informations reçues de Salesforce pour créer une entrée de bon de commande dans une table de base de données SQL Server interne.  
  
 Ce sont là toutes les étapes que vous devez effectuer pour atteindre l'objectif d'intégration décrit dans cette solution. Chacune de ces étapes implique un large éventail d'activités que nous allons passer en revue au fur et à mesure que nous progressons dans la création de la solution.  
  
 Voici une illustration qui décrit la solution d'intégration de bout en bout :  
  
 ![Scénario d’intégration de BizTalk Server et de Salesforce](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les logiciels suivants doivent être installés sur l'ordinateur sur lequel vous installez cette solution :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
-   [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]  
  
-   [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]  
  
 Vous devez avoir les abonnements aux services suivants :  
  
-   Un abonnement [!INCLUDE[winazure](../includes/winazure-md.md)]  
  
-   Un compte Salesforce Developer Edition  
  
## <a name="more-resources"></a>Plus de ressources  
 En plus de ce didacticiel, vous pouvez également consulter les ressources suivantes pour en savoir plus sur l’intégration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec Salesforce en utilisant les nouveaux adaptateurs introduites dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Une démonstration de laboratoire virtuel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et intégration de Salesforce est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=290930](http://go.microsoft.com/fwlink/?LinkId=290930).  
  
-   Un exemple en fonction de ce didacticiel est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=290932](http://go.microsoft.com/fwlink/?LinkId=290932).  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Étape 1 : Créer un Namespace de Bus de Service](../core/step-1-create-a-service-bus-namespace.md)  
  
-   [Étape 2 : Configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md)  
  
-   [Étape 3 : Créer la Solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)  
  
-   [Étape 4 : Configurer la Solution BizTalk Server](../core/step-4-configure-the-biztalk-server-solution.md)  
  
-   [Étape 5 : Tester la Solution](../core/step-5-test-the-solution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de BizTalk Server](../core/biztalk-server-tutorials.md)