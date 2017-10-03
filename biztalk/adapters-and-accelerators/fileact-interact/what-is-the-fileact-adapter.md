---
title: "Nouveautés de l’adaptateur FileAct ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ec8f1e-57f9-4e2d-ab8b-22b5c4b28055
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62b83fc723bbebce857eb442384b14179c1072ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-fileact-adapter"></a>Nouveautés de l’adaptateur FileAct ?
L’adaptateur FileAct pour SWIFTNet assure la connectivité entre BizTalk Server et de la société de télécommunication financières Interbank (SWIFT) dans le monde Secure IP réseau (SIPN) pour le transfert de fichiers. Le SIPN transfère des messages et des fichiers sur un réseau privé sécurisé qui connecte les établissements financiers, les infrastructures financiers et les clients. L’adaptateur FileAct utilise l’interface de programmation d’application (API) s pour se connecter à la SIPN SWIFTNet lien (SNL).  
  
 L’adaptateur FileAct fournit un mécanisme pour SWIFT aux participants de manière sécurisée et fiable échanger des fichiers et les informations relatives à ces fichiers. Il prend en charge les fonctionnalités suivantes :  
  
-   Envoi de fichiers à un utilisateur SWIFTNet  
  
-   La récupération de fichiers à partir d’un utilisateur SWIFTNet  
  
-   Confirmer la réception du fichier par un récepteur de notification de remise  
  
-   Abandon des transferts en cours  
  
-   Analyse d’état du transfert de fichiers  
  
-   Transferts de fichiers simultanés  
  
-   Garantie de l’authenticité des données et l’intégrité  
  
-   Confidentialité des données de fichier en transit  
  
-   Non répudiation de transferts de fichiers  
  
-   Horodatage  
  
## <a name="the-fileact-service"></a>Le Service de FileAct  
 L’adaptateur FileAct pour SWIFTNet fournit un transfert fiable et sécurisé de fichiers, tels que les lots de messages financiers structurés ou des rapports volumineux. Les applications classiques incluent des virements répétitives, telles que retraite ou paiements de salaire, informations de courtage à valeur ajoutée et des rapports et reporting réglementaire. SWIFTNet FileAct offre une variété de modes de messagerie :  
  
-   **Transfert de fichiers de stockage et de transfert.** Capacité de stockage et transfert de SWIFTNet FileAct supprime l’incertitude et les problèmes de préoccuper ou non vos correspondants sont en ligne au moment de que vous transmettez le fichier. Le fichier est remis dès que le destinataire est prêt à le recevoir. Par conséquent, il fournit un moyen idéal pour envoyer des fichiers à un grand nombre de correspondants, dont certaines peuvent être dans des fuseaux horaires différents.  
  
-   **Transfert de fichiers en temps réel.** Messagerie en temps réel offre une solution économique pour stocker et transférer des fichiers qui sont destinés à correspondants qui sont en ligne au moment de la transmission. Par conséquent, il est idéal pour l’envoi de fichiers à quelques correspondants volumineux ou des infrastructures de marché.  
  
-   **Récupération de fichiers en temps réel.** Il s’agit d’un service interactif généralement utilisé pour récupérer des fichiers dans le contexte de systèmes basés sur une station de travail et souvent conjointement avec SWIFTNet Parcourir. Nous prendrons en charge ce mode.  
  
 Les fonctionnalités facultatives de SWIFTNet FileAct (sur une base par fichier) sont les suivantes :  
  
-   **Priorité du message.** Transferts de fichiers peuvent être marquées comme « Urgente » dans le message afin de permettre approprié de traitement par vos correspondants.  
  
-   **Accusé de réception (modes de stockage et transmission et en temps réel).** Fournit la confirmation que votre correspondant votre fichier.  
  
-   **Non-répudiation de réception et d’émission.** En cas de litige, permet de SWIFT confirmer que le transfert de fichiers n’a eu lieu comme demandé.  
  
 Les fonctionnalités de SWIFTNet FileAct standards incluent la sécurité de SWIFTNet PKI**.** SWIFTNet FileAct est sécurisé avec SWIFTNet PKI et offre l’authentification des messages et contrôle d’intégrité.  
  
 Tous les messages et les fichiers échangés sur SWIFTNet subissent un ensemble commun de contrôles pour s’assurer qu’aucun utilisateur ne peut contourner la sécurité, de validation et de règles de routage de la plateforme. Ces vérifications sont effectuées par l’application de la passerelle SWIFTAlliance (trous).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route avec l’Adaptateurs FileAct et interagir de cartes](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [Qu’est SWIFTNet ?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [Quelle est l’interagir adaptateur ?](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)