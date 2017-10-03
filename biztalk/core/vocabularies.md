---
title: Vocabulaires | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, vocabularies
- vocabularies, about vocabularies
- vocabularies
- Business Rules Engine, vocabularies
ms.assetid: 591673a0-2c4d-41ca-9997-b363c086dd66
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9e20dfead51d54822d3316c8819d04a259cfa83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="vocabularies"></a>Vocabulaires
Les termes utilisés pour définir les conditions et actions de règles appartiennent généralement à une nomenclature propre à un domaine ou à un secteur d'activités. Par exemple, un utilisateur de messagerie écrit des règles basées sur des termes, tels que « reçu de » et « reçu après le » alors qu'un analyste du secteur des assurances écrit des règles basées sur des termes, tels que « facteurs de risque » ou « montant couvert ».  
  
 La terminologie propre à un domaine repose sur des artefacts technologiques (objets, tables de base de données et documents XML) qui implémentent les conditions et les actions de règles. Vocabulariesare conçu pour combler l’écart entre la sémantique d’entreprise et de l’implémentation.  
  
 Par exemple, la liaison de données d'un état d'approbation peut pointer vers une colonne d'une ligne d'une base de données, représentée sous la forme d'une requête SQL. Au lieu d'insérer cette représentation complexe dans une règle, il est préférable de créer une définition de vocabulaire associée à cette liaison de donnée et de lui attribuer le nom convivial « État ». Cet « État » peut alors être inclus par la suite dans n'importe quelle règle. Le moteur de règles pourra récupérer les données correspondantes dans la table.  
  
 A *vocabulaire* est une collection de définitions qui consistent en des noms conviviaux pour les faits utilisés dans des conditions de règle et les actions. Grâce aux définitions, les règles sont plus faciles à lire et à comprendre et peuvent être utilisées par les personnes travaillant dans un domaine d'activités particulier.  
  
 Vous pouvez utiliser l'Éditeur des règles d'entreprise pour définir les vocabulaires destinés à être enregistrés dans le magasin de règles partagé. Les vocabulaires peuvent également être utilisés par les développeurs chargés de l'intégration de la création de règles dans des applications, qu'elles soient nouvelles ou existantes.  
  
 Avant qu'un vocabulaire ne puisse être utilisé, celui-ci doit être associé à une version et publié dans un magasin de règles afin de garantir que les définitions du vocabulaire ne seront pas modifiées et afin de conserver l'intégrité du référentiel. Ceci signifie que toute stratégie utilisant une version donnée du vocabulaire ne peut pas échouer de façon inattendue en raison de modifications apportées au vocabulaire sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur des règles d’entreprise](../core/business-rules-engine.md)