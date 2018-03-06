---
title: Prise en charge EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04cd9c14b9c3663bdf332155cc9824e1681ca7a6
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="edi-support-in-biztalk-server"></a>Prise en charge d'EDI dans BizTalk Server
EDI est intégré à BizTalk Server et est un composant facultatif lorsque vous installez et configurez BizTalk Server. 
  
## <a name="feature-set-comparison-chart"></a>Tableau comparatif des fonctionnalités  
 Le tableau suivant présente la prise en charge EDI inclus dans BizTalk Server.
  
|Fonctionnalité|Commentaire|  
|---|---|
|Modification du Segment ISA au jeu de transactions| Créer des accords spécifiques|  
|ISA11 : US ou autre type de standard| |  
|ISA12 : Version de contrôle d’échange| |  
|ISA13 : Numéro de contrôle d’échange (incrémentation d’un nombre)| |  
|ISA15 : Test ou Production| |  
|Modification du Segment GS au niveau du document/de la transaction| |  
|GS expéditeur/destinataire GS différents de ISA| |  
|ID de Document entrants différents ISA et GS sortants| |  
|GS01 : Possibilité de modifier le type de document| |  
|GS04 : Date (possibilité de modifier le format)|Contient l’interface utilisateur pour sélectionner les formats SSAAMMJJ et aammjj|  
|GS05 : Heure (possibilité de modifier le format)|Contient l’interface utilisateur pour sélectionner les formats HHMM, HHMMSS et Hhmmssjj|  
|GS06 : Modifier le numéro de contrôle| |  
|GS07 : Code d’agence| |  
|GS08 : Peut placer dans la version de norme| |  
|possibilité de remplacer l'enveloppe EDI au moment de l'exécution| |  
|Schémas EDI personnalisés| |  
|Paramètre organisation/tiers|Créer des tiers distinct des accords. Également créer des modèles d’accords.|  
|Document EDI routage via la définition de document| |  
|Automatique 997 aux partenaires commerciaux|Configuration spécifique des profils d’entreprise|  
|Sortant EDI fiables sortants via 997| |  
|Prise en charge d’EDIFACT|Prend en charge D93 à D05 par ISO 9735 v4.1|  
|X12    Support|2040 à 5030|  
|Prise en charge de HIPAA| Microsoft BizTalk Accelerator pour HIPAA (BTAHIPAA) dans le cadre de la fonctionnalité EDI native|  
|Possibilité de supprimer les énumérateurs/CodeList|Utilisez Visual Studio / l’Éditeur BizTalk|  
|AS2 Envoi/réception| AS2 est certifiée par Drummond pour la prise en charge des pièces jointes, support de conservation de nom de fichier et l’interopérabilité.|  
|Conservation des noms de fichier AS2| |  
|Messages fiables AS2| |  
|Traitement par lot sortant (accumulation de plusieurs types de transactions dans une transaction unique)|Prend en charge plusieurs configurations de lot pour chaque profil d’entreprise|  
|Trafic entrant de traitement par lot : échange XML (en conservant un échange « traité par lot » entrant) ou XML de document informatisé basée sur les options de configuration|Prend également en charge le trafic entrant décomposition, fractionner l’échange en individuels XML de document informatisé|  
|Échange et Transaction défini génération et Validation au moment du Design dans Visual Studio| |  
|Rapprochement et la génération TA1 (accusé de réception technique)| |  
|Indicateurs de Validation facultatif EDI et XSD| |  
|Format de document/définition au niveau GS| |  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des normes EDI](../core/edi-standards-support.md)   
 [Prise en charge des schémas de Document EDI](../core/edi-document-schema-support.md)   
 [Prise en charge du jeu de caractères EDI](../core/edi-character-set-support.md)