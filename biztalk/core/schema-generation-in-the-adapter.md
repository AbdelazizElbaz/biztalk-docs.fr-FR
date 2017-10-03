---
title: "Génération de schéma dans l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, generating
- writing, schemas
ms.assetid: 43b69383-bae0-401b-9620-d4302db799b2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d10d927e4ede59e716b3f9838c96bac8cd144a81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-generation-in-the-adapter"></a>Génération de schémas dans l'adaptateur
Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages. La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous. À cause de cette limitation, l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'est pas en mesure d'offrir des fonctionnalités de génération de schémas.  
  
## <a name="writing-schemas"></a>Écriture de schémas  
 Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations. Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio. Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)