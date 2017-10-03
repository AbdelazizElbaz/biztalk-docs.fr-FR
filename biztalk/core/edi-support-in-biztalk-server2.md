---
title: Prise en charge EDI dans BizTalk Server2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6162276e5e394bd17b75825535ddaf097a7f589c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-support-in-biztalk-server"></a>Prise en charge d'EDI dans BizTalk Server
Les différentes versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prennent en charge l'EDI à travers les fonctions et composants suivants :  
  
|Version|Composant/fonctionnalité prenant en charge l'échange de données informatisé|  
|---|---|  
|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]et toutes les versions plus récentes|Fonctionnalité EDI native|  
|[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|Adaptateur EDI de base|  
|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]|Adaptateur EDI de base|  
|[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|Fonctionnalité EDI native|  
  
## <a name="feature-set-comparison-chart"></a>Tableau comparatif des fonctionnalités  
 Le tableau suivant indique la prise en charge de l'échange de données informatisé qu'offrent les composants/fonctionnalités EDI inclus dans les versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. « O » indique la prise en charge de la fonctionnalité ; « N » indique la non prise en charge de la fonctionnalité.  
  
|Fonctionnalité|[!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] - [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]|[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] - [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]|BizTalk Server 2009|BizTalk Server 2010|Commentaire|  
|---|---|---|---|---|---|---|  
|Modification du Segment ISA au jeu de transactions|O|N|O|O|O|Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures via la création d'accords spécifiques aux documents informatisés.|  
|ISA11 : US ou autre type de standard|O|N|O|O|O|-|  
|ISA12 : Version de contrôle d’échange|O|N|O|O|O|-|  
|ISA13 : Numéro de contrôle d’échange (incrémentation d’un nombre)|O|N|O|O|O|-|  
|ISA15 : Test ou Production|O|N|O|O|O|-|  
|Modification du Segment GS au niveau du document/de la transaction|O|N|O|O|O|-|  
|GS expéditeur/destinataire GS différents de ISA|O|N|O|O|O|-|  
|ID de Document entrants différents ISA et GS sortants|O|N|O|O|O|-|  
|GS01 : Possibilité de modifier le type de document|O|N|O|O|O|-|  
|GS04 : Date (possibilité de modifier le format)|N|N|O|O|O|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures incluent une option permettant de sélectionner les formats SSAAMMJJ et AAMMJJ|  
|GS05 : Heure (possibilité de modifier le format)|N|N|O|O|O|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures incluent une option permettant de sélectionner les formats HHMM, HHMMSS et HHMMSSjj|  
|GS06 : Modifier le numéro de contrôle|O|N|O|O|O|-|  
|GS07 : Code d’agence|O|N|O|O|O|-|  
|GS08 : Peut placer dans la version de norme|O|N|O|O|O|-|  
|possibilité de remplacer l'enveloppe EDI au moment de l'exécution|N|N|N|O|O|-|  
|Schémas EDI personnalisés|O|N|O|O|O|-|  
|Paramètre organisation/tiers|O|O (minimal)|O|O|O|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et BizTalk Server 2009 permettent de créer un tiers sur la base de modèles.<br /><br /> BizTalk Server 2010 et versions ultérieures remodèlent ceci en séparant le tiers et les accords. Permet de créer des accords sur la base de modèles.|  
|Document EDI routage via la définition de document|O|-|O|O|O|-|  
|Automatique 997 aux partenaires commerciaux|O|O|O|O|O|Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et BizTalk Server 2009 via la configuration spécifique des tiers<br /><br /> Prise en charge dans BizTalk Server 2010 et version ultérieures par une configuration spécifique aux profils d'entreprise.|  
|Sortant EDI fiables sortants via 997|O|O|O|O|O|-|  
|Prise en charge d’EDIFACT|O|O (minimal)|O|O|O|Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures (D93 à D05 selon ISO 9735 v4.1)|  
|X12 prend en charge|O|O (minimal)|O|O|O|Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures (2040 à 5030)|  
|Prise en charge de HIPAA|N|O (dans [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)])|O|O|O|Prise en charge dans [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] comme Microsoft BizTalk Accelerator pour HIPAA (BTAHIPAA) 3.3. Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures via la fonctionnalité EDI native.|  
|Possibilité de supprimer les énumérateurs/CodeList|O|N|O|O|O|Prise en charge dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures par l'Éditeur BizTalk/Visual Studio|  
|AS2 Envoi/réception|N|N|O|O|O|Dans BizTalk Server 2009 et versions ultérieures, AS2 est certifiée par Drummond pour la prise en charge des pièces jointes, support de conservation de nom de fichier et l’interopérabilité.|  
|Conservation des noms de fichier AS2|N|N|N|O|O|-|  
|Messages fiables AS2|N|N|N|O|O|-|  
|Peut migrer [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] des schémas EDI XDR personnalisés à l’espace de stockage EDI|-|N|N|N|N|Vous devez migrer les applications EDI de base vers [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou BizTalk Server 2009, puis migrer les applications vers BizTalk Server 2010 et versions ultérieures à l'aide de l'outil de migration de tiers.|  
|Traitement par lot sortant (accumulation de plusieurs types de transactions dans une transaction unique)|N|N|O|O|O|BizTalk Server 2009 et versions ultérieures prennent en charge plusieurs configurations de lot pour chaque profil d'entreprise.|  
|Trafic entrant de traitement par lot : échange XML (en conservant un échange « traité par lot » entrant) ou XML de document informatisé basée sur les options de configuration|N|N|O|O|O|Dans [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et versions ultérieures, cette fonctionnalité vient s'ajouter à la prise en charge de la décomposition des lots entrants (fractionnement d'un échange en fichiers XML de document informatisé individuels) |  
|Échange et Transaction défini génération et Validation au moment du Design dans Visual Studio|N|N|O|O|O|-|  
|Rapprochement et la génération TA1 (accusé de réception technique)|N|N|O|O|O|-|  
|Indicateurs de Validation facultatif EDI et XSD|N|N|O|O|O|-|  
|Format de document/définition au niveau GS|N|N|O|O|O|-|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des normes EDI](../core/edi-standards-support.md)   
 [Prise en charge des schémas de Document EDI](../core/edi-document-schema-support.md)   
 [Prise en charge du jeu de caractères EDI](../core/edi-character-set-support.md)