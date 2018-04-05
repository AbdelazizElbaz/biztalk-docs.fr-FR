---
title: Propriétés de Configuration désassembleur SWIFT | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, configuration properties
ms.assetid: 610cc68f-521f-4a9f-9f81-823a2fe55eb1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28bb9cfb95e253eaf6930d14e3856b5fee64deee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler-configuration-properties"></a>Propriétés de Configuration désassembleur SWIFT
Le tableau suivant fournit des propriétés du désassembleur SWIFT (DASM), les descriptions, les types de données et les plages de valeurs.  
  
|Nom de la propriété| Description|Type de données|Plage de valeurs|  
|-------------------|-----------------|---------------|-----------------|  
|**Schéma d’en-tête de lot**|Spécifie le schéma de fichier plat que vous utilisez pour l’analyse de l’en-tête d’enveloppe de lot. Utiliser uniquement si **entrant Debatching** a la valeur **True**.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Schéma de code de fin du lot**|Spécifie le schéma de fichier plat à utiliser pour l’analyse du code de fin enveloppe lot. Utiliser uniquement si **entrant Debatching** a la valeur **True**.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Validation de BRE**|Active/désactive l’appel de validation du moteur de règles d’entreprise (BRE). Si la valeur **True**, les messages sont validés par le moteur BRE par rapport aux stratégies déployées (par exemple, pour appliquer des règles de réseau SWIFT). Si la valeur **False**, validation de BRE n’est pas appelée.|Booléen|True, False|  
|**Liste des messages de Type double**|Spécifie les types de messages SWIFT qui doivent inspecter un deuxième champ d’en-tête pour déterminer le sous-type du message lors de la résolution de type de message dynamique. La liste par défaut est **102 103 521 523 574**. **Remarque :** si tout ou partie des chaînes de type de message sont supprimés de la liste de messages de Type double, pour tous les messages autres que MT574, le schéma d’origine et ses règles d’entreprise sont utilisés dans le traitement du message. Par exemple, une instance MT102 PLUS utilise MT102, une instance MT103PLUS utilise MT103, une instance MT521_ISITC utilise MT521, et une instance MT523_ISITC utilise MT523. Pour toutes les instances de MT574, l’erreur suivante est retournée : Échec de la recherche de spécification de document par type de message « http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/ SWIFT/Category5/MT&#574;SWIFT_CATEGORY5_MT574_Interchange ». Vérifiez que le schéma est déployé correctement. »|Chaîne|Liste séparée par espace de 3 chiffres|  
|**Fragmentation**|Active/désactive la fragmentation de lots entrants. Si la valeur **True**, les messages dans un lot entrant sont publiées pour la base de données MessageBox en tant que messages séparés. Si la valeur **False**, la totalité du traitement entrant est publié pour la base de données MessageBox en tant qu’un seul message (en tant qu’une copie exacte de l’entrée). Utilisez uniquement si debatching entrant est définie sur **True**.|Booléen|True, False|  
|**Trafic entrant Debatching**|Active/désactive le traitement de lots entrants. Si la valeur **True**, lots entrants sont attendus et sont dégroupés au cours du traitement. Si la valeur **False**, messages uniques sont attendus et ne nécessitent pas de debatching.|Booléen|True, False|  
|**Schéma d’en-tête de message**|Spécifie le schéma de fichier plat à utiliser pour l’analyse de l’en-tête d’enveloppe de message (pour un message dans un lot). Utiliser uniquement si **entrant Debatching** a la valeur **True**.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Schéma de code de fin de message**|Spécifie le schéma de fichier plat à utiliser pour l’analyse de l’enveloppe le code de fin (pour un message dans un lot). Utiliser uniquement si **entrant Debatching** a la valeur **True**.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Préserver l’en-tête de lot**|Active/désactive la conservation de l’en-tête de l’enveloppe par lots lorsque **Fragmentation** est activé. Si la valeur **True**, l’en-tête d’enveloppe de lot est publié dans la base de données MessageBox en tant qu’un message distinct. Si la valeur **False**, l’en-tête d’enveloppe de lot est abandonné une fois qu’il est analysé. Utiliser uniquement si **schéma d’en-tête de lot** est spécifié.|Booléen|True, False|  
|**Conserver le code de fin du lot**|Active/désactive la conservation de l’enveloppe de lot remorque lorsque **Fragmentation** est activé. Si la valeur **True**, le code de fin enveloppe lot est publié dans la base de données MessageBox en tant qu’un message distinct. Si la valeur **False**, le code de fin enveloppe lot est abandonné une fois qu’il est analysé. Utiliser uniquement si **schéma de code de fin du lot** est spécifié.|Booléen|True, False|  
|**Préserver l’en-tête de Message**|Active/désactive la préservation de l’en-tête d’enveloppe de message (pour un message dans un lot) lorsque **Fragmentation** est activé. Si la valeur **True**, l’en-tête d’enveloppe de message est publié dans la base de données MessageBox dans la partie de l’en-tête du message SWIFT correspondant dans le lot. Si la valeur **False**, l’en-tête d’enveloppe de message est abandonné une fois qu’il est analysé. Utiliser uniquement si **schéma d’en-tête de Message** est spécifié.|Booléen|True, False|  
|**Conserver le code de fin**|Active/désactive la préservation de l’enveloppe le code de fin (pour un message dans un lot) lorsque **Fragmentation** est activé. Si la valeur **True**, le code de fin d’enveloppe de message est publié dans la base de données MessageBox dans la partie du code de fin du message SWIFT correspondant dans le lot. Si la valeur **False**, le code de fin d’enveloppe de message est abandonné une fois qu’il est analysé. Utiliser uniquement si **schéma de code de fin de Message** est spécifié.|Booléen|True, False|  
|**Preserve Session et le numéro de séquence**|Si la valeur **True**, conserver toutes les chaînes de caractères dans les champs de session et le numéro de séquence dans le bloc d’en-tête 1.<br /><br /> Si la valeur **False**, insérer des espaces tronquées dans ces champs.|Booléen|True, False|  
|**Promouvoir les propriétés de SWIFTBound A4SWIFT**|Si la valeur **True**, promouvoir le **SWIFTBound** propriété pour les messages reçus par ce pipeline dans un bloc d’en-tête 2 (entrée).<br /><br /> Si la valeur **False**, ne promouvez pas le **SWIFTBound** propriété dans tous les cas.|Booléen|True, False|  
|**Supprimer manquant des avertissements de stratégie**|Active/désactive la journalisation des avertissements de moteur de règles d’entreprise (BRE) dans le journal des événements manquants des stratégies de validation BRE (annulés). Si la valeur **True**, les avertissements sont supprimés. Si la valeur **False**, un avertissement est enregistré chaque fois qu’une stratégie de validation est introuvable. Utiliser uniquement si **BRE Validation** est activé.|Booléen|True, False|  
|**Schéma d’en-tête SWIFT**|Spécifie le schéma de fichier plat à utiliser pour l’analyse de l’en-tête de message SWIFT et inspecter les valeurs analysées à découvrir dynamiquement le type de message. Spécifiez uniquement si la résolution de type de message dynamique est requise (pipeline traitera les messages SWIFT de types différents). Spécifiez si **le schéma d’échange SWIFT** n’est pas spécifié. Si **SWIFT échange** et **schéma d’en-tête SWIFT** sont n’est pas spécifié, **schéma d’en-tête SWIFT** par défaut est  **Micrsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Schéma de l’échange rapide**|Spécifie le schéma de fichier plat à utiliser pour l’analyse de l’intégralité du message SWIFT (d’échange). Spécifiez uniquement si la résolution de type de message dynamique n’est pas obligatoire (pipeline traite uniquement les messages SWIFT du type spécifié). Doit être spécifié si **schéma d’en-tête SWIFT** n’est pas spécifié.|Chaîne|Aucun ou n’importe quel nom de schéma déployé|  
|**Traiter les lignes vides comme des erreurs d’analyse**|Si la valeur **True**, lorsque des lignes vides sont rencontrées dans de nombreux champs sur plusieurs lignes, ils sont marqués comme des erreurs (lignes vides ne sont pas bonnes pratiques en fonction de SWIFT) d’analyse. Notez que pour debatching des scénarios, ces erreurs d’analyse n’interrompez pas le traitement par lots (le message est traité comme un message d’erreur et génère une partie de l’erreur), et les messages dans le traitement sans erreurs sont traitées correctement.<br /><br /> Si la valeur **False**, les lignes vides sont autorisées dans de nombreux champs sur plusieurs lignes.|Booléen|True, False|  
|**Validation XML**|Active/désactive l’appel de la validation XML. Si la valeur **True**, les messages sont validés par le XML de validation de lecture par rapport aux contraintes de schéma (par exemple, pour appliquer la longueur ou la plage de valeurs). Si la valeur **False**, validation XML n’est pas appelée.|Booléen|True, False|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)   
 [Configuration de l’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)