---
title: La nécessité pour l’intégration de systèmes de santé | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- health care organizations
ms.assetid: e747b633-c898-473c-be7d-ba00bfdbdc21
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7674cff1c9c1e787c0ab9638e0abad407adafea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-need-for-health-care-systems-integration"></a>La nécessité pour l’intégration de systèmes de soins de santé
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] permet aux fournisseurs de soins de santé avec les solutions de leurs besoins d’automation application intégration et processus d’entreprise. Cette rubrique décrit certains des défis métier auxquelles sont confrontées les entreprises de soins de santé et la manière dont les systèmes incorporant [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] peuvent aider les organisations à ces défis. Également Examinons un scénario courant illustrant un exemple de scénario d’entreprise avec [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].  
  
## <a name="health-care-business-challenge"></a>Défi de soins de santé

Les organisations de soins de santé sont des entités de métier complexe avec de nombreuses parties distinctes, mais il est connectés. Pour un hôpital, ces services peuvent inclure Admission labs, postes de soins, médecins et facturation. Ensemble de ces départements générer et utiliser des données. Les données peuvent inclure des informations sur les patients, la facturation, procédures et médicaments. Les organisations doivent souvent, ces données auprès de plusieurs de leurs services. Un commun pour l’organisation de soins de santé consiste à faire face efficacement à l’échange de données entre les services.  
  
 L’illustration suivante montre le nombre de services peuvent communiquer entre eux, création d’un système complex.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-no-btahl7.gif "hl7_no_btahl7")  
  
 La plupart de ces services ont également des processus d’entreprise distinctes. Le personnel d’un service peut avoir créé, implémenté et géré leur propre processus. Ces processus peuvent affecter les autres services, mais le service technique peuvent ne pas avoir conçus les avec les autres services à l’esprit.  
  
 Mieux maîtriser les processus sur l’éventail complet de l’organisation est un problème pour de nombreuses organisations de soins de santé.  
  
## <a name="health-care-business-solution"></a>Solution d’entreprise de soins de santé

La technologie peut aider à résoudre les défis liés aux données et des processus d’entreprise. Les systèmes informatiques peuvent aider les organisations de soins de santé à transformer leurs opérations internes des processus déconnectés, incompatible, à intégré, des informations normalisé ceux.  
  
### <a name="integration"></a>Intégration  
 Même si les processus de parties distinctes d’une organisation de soins de santé ne sont pas fondamentalement compatibles, vous pouvez les intégrer. Vous pouvez les lier avec la technologie qui transforme un système caractérisé par des connexions de point à point (comme indiqué dans la figure enjeux de soins de santé (dans cette rubrique) pour une selon une disposition « hub and spoke », comme indiqué dans l’illustration suivante.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-yes-btahl7.gif "hl7_yes_btahl7")  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]Permet d’obtenir cette intégration par la connexion à chaque service distincts ou d’une entité et fournir les mécanismes de lier les processus, résolution de leurs différences. Il automatise également l’échange de données, afin que le processus d’entreprise peuvent fonctionner avec un minimum d’intervention humaine.  
  
### <a name="standardization"></a>Normalisation  
 Une fois que vous avez connecté des processus d’entreprise, les processus peuvent échanger des données. Toutefois, si les données gérées par des services distincts seront dans différents formats et systèmes il cependant des données différentes des protocoles de transport, l’échange de données peut nécessiter des efforts considérables dans la conception du système. Vous pouvez considérablement améliorer l’efficacité de ce processus si chacun des services connectés normalise le format et le protocole utilisé avec leur échange de données.  
  
 Il s’agit de l’organisation HL7 terminée. Qu’ils ont créés formats courants pour les données de soins de santé, sous la forme de schémas de fichier plat. Leurs efforts ont été très réussies, jusqu'à ce qu’un pourcentage élevé d’un grand nombre ont adopté leurs normes.  
  
### <a name="solutions-specific-to-the-health-care-industry"></a>Solutions spécifiques à l’industrie de soins de santé  
 Systèmes informatiques intégrés et échange de données standardisé ont fourni la Fondation de plus efficace d’intégrité des processus de soins. Une solution d’informatique réellement efficace pour les systèmes de soins de santé est celle qui se concentre sur les problèmes dans ce secteur d’activité et fournit des fonctionnalités, les fonctionnalités et les outils qui répondent aux besoins des entreprises de soins de santé.  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]fournit cette solution. Vous installez [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] sur [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]fonctionne avec les schémas créés et gérés par l’organisation HL7. En outre, il fournit des fonctionnalités et des outils conçus spécifiquement pour les applications de soins de santé. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]permet le traitement par lot, les accusés de réception, validation des données, l’audit et journalisation requis par les organisations de soins de santé.  
  
## <a name="next"></a>Suivant
Lire un [exemple de scénario commercial](../../adapters-and-accelerators/accelerator-hl7/sample-business-scenario.md).
