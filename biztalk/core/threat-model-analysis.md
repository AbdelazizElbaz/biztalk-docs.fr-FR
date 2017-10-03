---
title: "Analyse du modèle de menace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TMA, about TMA
- TMA
- TMA, procedure steps
ms.assetid: dfbf46aa-0a35-4925-8718-df8591efc279
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06f5de73434d2c3a7bf67e659c6566b530b38aeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="threat-model-analysis"></a>Analyse du modèle des menaces
Une analyse du modèle des menaces est une analyse qui aide à déterminer les risques de sécurité liés à un produit, une application, un réseau ou un environnement, et l'origine des attaques. L'objectif est de déterminer les menaces nécessitant une prévention et la manière de les prévenir.  
  
 Cette section fournit des informations très détaillées sur le processus d'analyse du modèle des menaces. Pour plus d’informations, consultez le chapitre 4 de *Writing Secure Code, Second edition*, de Michael Howard et David LeBlanc.  
  
 Les avantages d'une analyse du modèle des menaces sont notamment :  
  
-   Fournit une meilleure compréhension de votre application  
  
-   Vous aide à trouver des bogues  
  
-   Peut aider les nouveaux membres de l'équipe à comprendre l'application en détail  
  
-   Contient des informations importantes pour les autres équipes qui améliorent votre application  
  
-   Utile pour les testeurs  
  
 Les étapes détaillées à suivre pour effectuer une analyse du modèle des menaces sont les suivantes :  
  
-   Étape 1. Collecter les informations générales  
  
-   Étape 2. Créer et analyser le modèle de menace  
  
-   Étape 3. Examen des menaces  
  
-   Étape 4. Identifier les Technologies et Techniques de prévention  
  
-   Étape 5. Modèle de sécurité et des considérations relatives au déploiement de document  
  
-   Étape 6. Implémenter et tester les préventions  
  
-   Étape 7. Conserver le modèle des menaces synchronisé avec la conception  
  
## <a name="step-1-collect-background-information"></a>Étape 1. Collecter les informations générales  
 Pour préparer une analyse du modèle des menaces réussie, vous devez recueillir des informations générales. Elles permettent d'analyser votre environnement cible (une application, un programme ou l'infrastructure entière) comme suit :  
  
-   Identification des scénarios de cas d'utilisation. Pour chaque scénario de cas d'utilisation pour votre environnement cible, identifiez la manière dont vous pensez que votre entreprise utilise l'environnement cible et toutes limitations ou restrictions liées à ce dernier. Ces informations permettent de définir l'étendue de la discussion sur le modèle des menaces et fournissent des pointeurs aux ressources (actifs de valeur de votre entreprise, tels que des données et des ordinateurs) et des points d'entrée.  
  
-   Création d'un diagramme de flux de données pour chaque scénario. Assurez-vous d'être suffisamment précis pour comprendre vos menaces.  
  
-   Détermination des limites et de l'étendue de l'environnement cible.  
  
-   Compréhension des limites entre les composants approuvés et non approuvés.  
  
-   Compréhension du modèle de configuration et d'administration pour chaque composant.  
  
-   Création d'une liste de dépendances externes.  
  
-   Création d'une liste d'hypothèses sur les autres composants dont dépend chaque composant. Cela permet de valider des hypothèses entre composants, des éléments d'action et des éléments de suivi avec d'autres équipes.  
  
## <a name="step-2-create-and-analyze-the-threat-model"></a>Étape 2. Créer et analyser le modèle de menace  
 Après avoir recueilli des informations générales, vous devez organiser une ou plusieurs réunions sur le modèle des menaces. Assurez-vous qu'au moins un membre de chaque étape de développement est présent (par exemple, responsable de programme, développeur et testeur). Veillez à rappeler aux participants que le but de la réunion est de trouver des menaces et non de les prévenir. Au cours de la réunion sur le modèle des menaces, procédez comme suit :  
  
-   Examinez le diagramme de flux de données pour chaque cas d'utilisation. Pour chaque cas d'utilisation, identifiez :  
  
    -   Points d'entrée  
  
    -   Limites de confiance  
  
    -   Flux de données du point d'entrée à l'emplacement de repos final (et inversement)  
  
-   Notez les actifs impliqués.  
  
-   Discutez chaque DFD et recherche les menaces dans les catégories suivantes pour toutes les entrées du diagramme : **S**urpation identifier, **T**ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges.  
  
-   Créez une liste des menaces identifiées. Nous recommandons que cette liste inclue un titre, une brève description (y compris des arborescences de menaces), les ressources, le ou les impacts, le risque, les techniques de prévention, l'état de prévention et un numéro de bogue.  
  
    > [!NOTE]
    >  Vous pouvez ajouter le risque, les techniques de prévention et l'état de prévention lorsque vous passez en revue les menaces. Ne consacrez pas trop de temps à ces domaines pendant la réunion sur le modèle des menaces.  
  
## <a name="step-3-review-threats"></a>Étape 3. Examen des menaces  
 Une fois que vous avez identifié les menaces pour votre environnement, vous devez classer le risque de chaque menace et déterminer la manière dont vous voulez répondre à chaque menace. Vous pouvez le faire grâce à des réunions d'équipe supplémentaires ou par courrier électronique. Vous pouvez utiliser les catégories d’effet suivantes pour calculer l’exposition aux risques : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **un**tteinte des utilisateurs et **D**étectabilité.  
  
 Une fois que vous avez une liste des menaces pour votre environnement cible classée par risque, vous devez déterminer la manière dont vous répondrez à chaque menace. Votre réponse peut être de ne rien faire (rarement un bon choix), de prévenir les utilisateurs du problème potentiel, de supprimer le problème ou de le résoudre.  
  
## <a name="step-4-identify-mitigation-techniques-and-technologies"></a>Étape 4. Identifier les Technologies et Techniques de prévention  
 Une fois que vous avez identifié les menaces à prévenir, vous devez déterminer les techniques de prévention disponibles pour chaque menace et la technologie la plus appropriée pour réduire l'effet de chaque menace.  
  
 Par exemple, en fonction des détails de votre environnement cible, vous pouvez réduire l'effet des menaces de falsification des données en utilisant des techniques d'autorisation. Vous devez alors déterminer la technologie d'autorisation appropriée à utiliser (par exemple, listes de contrôle d'accès discrétionnaire, autorisations ou restrictions d'IP).  
  
> [!IMPORTANT]
>  Lorsque vous évaluez les techniques et technologies de prévention à utiliser, vous devez considérer ce qui est approprié pour votre entreprise, ainsi que toute stratégie d'entreprise pouvant affecter la technique de prévention à choisir.  
  
 Après avoir terminé l'analyse du modèle des menaces, procédez comme suit :  
  
-   Documentez le modèle de sécurité et les considérations relatives au déploiement.  
  
-   Mettez en œuvre et testez les préventions.  
  
-   Conservez le modèle des menaces synchronisé avec la conception.  
  
## <a name="step-5-document-security-model-and-deployment-considerations"></a>Étape 5. Modèle de sécurité et des considérations relatives au déploiement de document  
 Il est important de documenter ce que vous avez découvert lors de l'analyse du modèle des menaces et comment vous avez décidé de réduire l'effet des menaces pour votre environnement cible. Cette documentation peut être utile pour le personnel de l'assurance qualité, du test, du support technique et du back-office. Incluez des informations sur d'autres applications qui interagissent ou assurent l'interface avec votre environnement cible, ainsi que les recommandations et les exigences en matière de pare-feu et de topologie.  
  
## <a name="step-6-implement-and-test-mitigations"></a>Étape 6. Implémenter et tester les préventions  
 Lorsque votre équipe est prête à prévenir les menaces identifiées lors de l'analyse du modèle des menaces, veillez à utiliser des listes de vérification de développement et de déploiement pour suivre le code sécurisé et les normes de déploiement permettant de minimiser l'introduction de nouvelles menaces.  
  
 Une fois que vous avez implémenté une prévention, veillez à la tester pour vous assurer qu'elle offre le niveau de protection souhaité contre la menace.  
  
## <a name="step-7-keep-the-threat-model-in-sync-with-design"></a>Étape 7. Conserver le modèle des menaces synchronisé avec la conception  
 Lorsque vous ajoutez de nouvelles applications, de nouveaux serveurs ou autres éléments à votre environnement, veillez à revoir vos conclusions de l'analyse du modèle des menaces et à procéder à d'autres analyses pour chaque nouvelle fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
[Études de cas de sécurité pour les petites et moyennes entreprises](../core/security-case-studies-for-small-to-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)