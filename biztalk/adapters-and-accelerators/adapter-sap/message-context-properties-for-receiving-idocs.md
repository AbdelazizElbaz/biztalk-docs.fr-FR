---
title: Propriétés de contexte de message pour recevoir des IDOC | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDOCs, message context properties for receiving
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca289e37cac15972e75c69d7ad20928b72911963
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-context-properties-for-receiving-idocs"></a>Propriétés de contexte de message pour recevoir des IDOC
Pour la réception d’un IDOC à l’aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les propriétés de contexte de message suivant.  
  
 **Propriétés de l’enregistrement de contrôle IDOC.**  
  
-   **TABNAM** -nom de la structure de table  
  
-   **SITUATION** -Client  
  
-   **DOCNUM** -numéro IDOC  
  
-   **DOCREL** -version SAP pour IDOC  
  
-   **ÉTAT** -état de IDOC  
  
-   **DIRECT** -Direction  
  
-   **OUTMOD** -mode de sortie  
  
-   **EXPRSS** - substitution dans le traitement entrant  
  
-   **TEST** -indicateur de Test  
  
-   **IDOCTYP** -nom du type de base  
  
-   **CIMTYP** -Extension (défini par le client)  
  
-   **MESTYP** -type de Message  
  
-   **MESCOD** -code de Message  
  
-   **MESFCT** -Message (fonction)  
  
-   **STD** -indicateur de standard, EDI  
  
-   **STDVRS** -EDI standard, version et mise en production  
  
-   **STDMES** -type de message EDI  
  
-   **SNDPOR** -port de l’expéditeur (système SAP, sous-système externe)  
  
-   **SNDPRT** -type d’expéditeur du partenaire  
  
-   **SNDPFC** -partenaire de l’expéditeur (fonction)  
  
-   **SNDPRN** -nombre de l’expéditeur du partenaire  
  
-   **SNDSAD** -adresse d’expéditeur (SADR)  
  
-   **SNDLAD** -adresse logique d’expéditeur  
  
-   **RCVPOR** -port de réception  
  
-   **RCVPRT** -Type de partenaire du récepteur  
  
-   **RCVPFC** -partenaire du destinataire (fonction)  
  
-   **RCVPRN** -numéro du destinataire de partenaire  
  
-   **RCVSAD** -l’adresse du destinataire (SADR)  
  
-   **RCVLAD** -adresse logique du destinataire  
  
-   **CREDAT** - créé sur  
  
-   **CRETIM** -heure de création  
  
-   **REFINT** -fichier de Transmission (échange EDI)  
  
-   **REFGRP** -groupe de messages (groupe de messages EDI)  
  
-   **REFMES** -Message (Message EDI)  
  
-   **ARCKEY** - Key pour l’archivage de message externe  
  
-   **SÉRIE** -sérialisation  
  
-   **DOCTYP** -type IDOC (il est disponible dans EDI_DC uniquement. Doit être présent dans la propriété de contexte, mais doit être promu uniquement pour la Version 2 IDOC)  
  
 **TID** – représente le TID envoyé par le système SAP pour l’appel entrant TRFC.  
  
 **GUID** – représente le GUID qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise en interne. Cela a un mappage avec le TID qui a été reçu à partir du système SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)