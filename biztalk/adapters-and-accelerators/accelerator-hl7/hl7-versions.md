---
title: HL7 Les Versions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HL7, standards
- HL7, versions
ms.assetid: 47299c6f-55c3-4434-8170-5ad73fe9a84c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c7edcfa6c44467c0660efd8a9b4b02df7010de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-versions"></a>Versions HL7
HL7 Version 2 est une famille de normes étroitement liées au lieu d’un seul standard. L’organisation HL7 vise à ces normes pour être compatible vers le haut dans l’application des règles de compatibilité des versions entre HL7. Ces règles garantissent que, dans les limites de la Version 2, une interface définie selon les règles d’une version HL7 continuera à fonctionner dans la définition des versions de successeur. Afin qu’un système de réception soit en mesure d’accepter des messages à partir de versions ultérieures sans rompre son implémentation et l’envoi d’un système sera en mesure de continuer à envoyer des messages à des destinataires qui prennent en charge les versions ultérieures.  
  
 Il est important de noter que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) :  
  
-   Prend en charge toutes les versions HL7 dynamiques à partir de la Version 2.1 via la Version 2.5  
  
-   Fournit les fonctionnalités requises pour le mappage entre les versions HL7 et permet l’interopérabilité de plusieurs versions sur un seul site  
  
-   Prend en charge la localisation en prenant en charge des segments de Z et Active le mappage entre l’interprétation du remplacement ou utilise des messages standards  
  
 Il est important de noter la différence entre les versions de la norme de messagerie :  
  
-   Version 1 fonctionnait comme une preuve de concept  
  
-   Version 2 fournit une collection de spécifications de message pour prendre en charge l’échange de messages entre des applications  
  
-   Version 3 fournit un ensemble intégré basé sur un modèle de spécifications pour prendre en charge une variété de besoins de l’interopérabilité  
  
 Fondamentalement, Version 2 met l’accent sur une approche pragmatique pour fournir aux utilisateurs les spécifications nécessaires pour mener à bien les tâches spécifiées, tandis que la Version 3 se concentre sur la garantie de cohérence et à long terme d’extensibilité pour le corps de spécifications de message prise comme une dans son ensemble.  
  
 L’Architecture de Document cliniques fournit une extension significative à la norme HL7 en introduisant des normes pour la représentation sous forme de documents cliniques à l’aide de XML.  
  
 Le tableau suivant affiche la progression de développement standard de HL7.  
  
|Événement|Année|Détails|  
|-----------|----------|-------------|  
|HL7 fondée|1987|La première réunion dans Stanford, autorité de certification, inclus 12 participants.|  
|V1.0|1987|Brouillon présenté à la réunion de pleine HL7.|  
|V2.0|1988|Brouillon présenté à la réunion de pleine HL7.|  
|V2.1 publié|1990|La première largement implémenté la version|  
|Version 2.2 publié|1994||  
|V.2.3 publié|1997|ANSI approuvé|  
|V2.3.1 publié|1999|ANSI approuvé|  
|V2.4 publié|2000|ANSI approuvé|  
|Architecture de Document clinique|2000|ANSI approuvé|  
|2.5 publié|2003|Terminer l’approbation dans HL7, soumis à la norme ANSI pour approbation.|  
|Version 3.0 en cours|2003||  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Modes de messages](../../adapters-and-accelerators/accelerator-hl7/message-modes.md)   
 [La messagerie HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)