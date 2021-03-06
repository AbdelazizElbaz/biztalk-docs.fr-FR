---
title: "Étapes du scénario Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77751c15-9b67-4587-8bc8-2be65f13d339
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff3b2feda86ad0b8edbbded26a290c7276a63af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-solution-steps"></a>Étapes Solution du scénario
L’infrastructure de gestion d’Exception ESB fournit une solution simple pour gérer une exception lorsqu’un message de facture contient des données non valides qui provoque une erreur lors du traitement, comme décrit précédemment dans cette rubrique. Voici une approche, que vous pouvez prendre :  
  
1.  Affecter la responsabilité de l’application récemment déployée Financial Reporting, basée sur Microsoft BizTalk à un développeur de votre équipe.  
  
2.  Un nouveau message d’erreur ESB arrive dans le portail de gestion ESB ; le message indique un problème d’intégrité de données dans une orchestration dans l’application BizTalk de création de rapports financiers.  
  
3.  L’administrateur ou opérateur notifie le développeur de la nouvelle exception, ou le développeur inscrit pour la notification automatique lorsqu’une exception se produit. Cette notification peut se produire pour l’une des raisons suivantes :  
  
    -   Il peut se produire, car l’exception dépassé un seuil prédéfini dans basés sur les événements d’analyse BAM (Business Activity).  
  
    -   Il peut se produire, car il existe un abonnement de BizTalk pour l’application spécifique, service, étendue et code d’erreur qui transfère l’exception au développeur.  
  
4.  Le développeur examine le message d’erreur, les messages individuels d’orchestration et leurs valeurs de propriété de contexte persistante. Les développeurs peuvent afficher ces informations via le portail de gestion ESB ou à l’aide de Microsoft Outlook via un abonnement de BizTalk.  
  
5.  Le développeur détermine qu’il s’agit d’une erreur courante. Cela nécessite une intervention manuelle et la correction par l’équipe Finances, suivie de la nouvelle soumission dans le système.  
  
6.  Le développeur crée et déploie un projet d’orchestration BizTalk indépendant qui s’abonne pour le type d’application et de l’exception spécifique.  
  
7.  Le projet d’orchestration récupère le message non valide à partir du message d’erreur ESB envoie le message à l’équipe Finances pour la correction, met en corrélation le message corrigé à l’orchestration et le renvoie s’il.  
  
8.  Une semaine plus tard, le développeur accède au portail de gestion ESB pour découvrir que les tendances exception d’application pour les messages non valides ont considérablement diminué, car cette solution a été déployée.