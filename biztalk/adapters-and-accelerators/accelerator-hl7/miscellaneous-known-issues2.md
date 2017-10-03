---
title: "Les « Incidents2 » connus divers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: known issues
ms.assetid: 01cd896f-6c7f-4734-b953-81a92195a5c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af644ead6ecb825d6d6960145958c176946e844c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="miscellaneous-known-issues"></a>Divers problèmes connus
Cette section contient des informations utiles sur les erreurs diverses.  
  
## <a name="duplicate-errors-logged-for-the-same-message-segment-sequence-and-field-number"></a>Dupliquer les erreurs enregistrées pour le même segment de message, la séquence et le numéro de champ  
 S’il existe des erreurs dans les composants d’un champ de types de données complexes, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) signale une erreur pour chaque erreur de ce type. L’ID de segment et le numéro de champ sera identique. Le numéro d’erreur et la description peuvent différer HL7 du mécanisme de rapport d’erreurs ne prenant pas en charge les rapports d’erreurs au niveau du composant et au sous-composant.  
  
## <a name="segment-sequence-errors"></a>Erreurs de séquence de segment  
 Si nécessaire les segments de message sont manquants, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] signale un message « Erreur de séquence (fin inattendue du corps de message trouvé) du Segment » dans le dernier segment correct analysé par le moteur.  
  
## <a name="invalid-error-can-be-recorded-when-the-msh3-header-field-is-structurally-incorrect"></a>Erreur non valide peut être enregistrée lorsque le champ d’en-tête MSH3 est structurellement incorrect  
 Si un champ d’en-tête MSH3 est structurellement incorrect, le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur ne peut pas copier le contenu du champ MSH3 dans l’en-tête de MSH5 et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne peut pas envoyer un accusé de réception (ACK). Cela peut indiquer que le problème a été avec le champ MSH5, pas le champ MSH3.  
  
## <a name="access-database-errors"></a>Erreurs de base de données Access  
 Les bases de données HL7 accès contenaient les erreurs suivantes :  
  
-   27 de champ du segment OBR dans la base de données HL7 version 2.3 accès a été incorrectement marquée comme non reproductibles et requis. A été modifiée dans cette [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] champ des schémas pour les valeurs correctes de reproductibles et facultatif.  
  
-   Champ 2 du segment OBX dans la base de données a été incorrectement marquée comme l’accès version 2.3 HL7 requis et champ 10 du segment OBX dans la base de données HL7 version 2.3 accès a été incorrectement marquée comme non renouvelable. Dans la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] schémas, champ 2 est marqué comme facultatif et champ 10 est marqué comme étant répétitifs.  
  
-   Champ 4 du segment dans la base de données a été incorrectement marquée comme l’accès V2.3.1 HL7 OBX requis. Ce champ dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] schémas est marqué correctement comme facultatifs.  
  
## <a name="logging-service-account-may-not-have-access-to-databases-that-are-not-created-by-the-setup-program"></a>Compte de service de journalisation n’aient pas accès aux bases de données qui ne sont pas créés par le programme d’installation  
 Lorsque vous configurez le magasin de journalisation pour pointer vers une base de données nouvellement créé, le programme d’installation n’a pas été créé, la nouvelle base de données peut-être pas le compte de service de journalisation répertorié pour l’accès. Assurez-vous que le compte de service de journalisation a accès à toutes les nouvelles bases de données de journalisation.  
  
## <a name="leading-spaces-not-allowed-in-nm-and-si-data-types"></a>Interdit dans les types de données NM et SI des espaces de début  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]rejette les instances des types de données NM et SI qui ont des espaces de début et de fin.  
  
## <a name="btahl7-accepts-a-value-of-0-for-hl7-v21-si-data-type"></a>BTAHL7 accepte une valeur de « 0 » pour le type de données HL7 V2.1 SI  
 Dans la norme HL7 pour HL7 V2.1, la valeur « 0 » n’est pas acceptable dans une instance du type de données SI. Toutefois, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] accepte « 0 » comme valeur valide dans une instance du type de données SI.  
  
## <a name="mismatch-of-source-and-destination-party-namespaces"></a>Incompatibilité d’espaces de noms tiers source et de destination  
 Si l’espace de noms configuré dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration sur le **Validation** onglet ne correspond pas à l’espace de noms dans le schéma source pour une V2 HL7. X message, le sérialiseur peut générer des messages d’erreur qui n’identifient pas clairement le problème. Ces messages d’erreur peut indiquer les erreurs de séquence de segment ou une fin inattendue du corps du message est trouvée. Si vous ne pouvez pas expliquer la cause d’une erreur, vous pouvez vérifier une incompatibilité d’espace de noms de tiers.  
  
## <a name="lack-of-segments-fts-or-bts-results-in-error-but-the-message-still-parses"></a>Un manque de segments de recherche en texte intégral ou BTS entraîne erreur, mais le message est toujours analyse  
 Lorsque le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] désassembleur analyse un lot de messages qui contient les segments FHS ou BHS, mais ne contient-elle pas de correspondant segment FTS et/ou BTS, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère une erreur, mais le message est toujours analyse.  
  
## <a name="modifying-a-message-header-tag-results-in-multiple-errors"></a>Modification d’un message en-tête balise entraîne plusieurs erreurs  
 Si le Concepteur d’Orchestration modifie une balise d’en-tête de message, vous pouvez voir les erreurs qui ne sont pas compréhensibles, par exemple « premier segment non valide » ou « erreur de séquence de segment ».  
  
## <a name="configuration-data-can-be-affected-by-other-biztalk-server-applications"></a>Données de configuration peuvent être affectées par d’autres applications de BizTalk Server  
 Si vous entrez des données personnalisées dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration ou la configuration du jeu de données par programmation via la Configuration Application Programming Interface (API), les données personnalisées sont stockées dans la base de données de Configuration.  Vous pouvez utiliser la base de données de Configuration d’autres informations spécifiques aux tiers à partir d’autres applications BizTalk. Si une autre application stocke des données dans le même emplacement que le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] les données de configuration, le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] données ne peuvent pas être stockées correctement. Si cela se produit, modifier l’emplacement de stockage des données de l’autre application, enregistrez le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] à nouveau les données de configuration.  
  
## <a name="errors-might-not-be-logged-in-the-error-log-due-to-a-size-limitation-of-the-event-log-store"></a>Erreurs ne peuvent pas être enregistrées dans le journal des erreurs en raison d’une limite de taille de la banque de journal des événements  
 Lorsque le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur génère un nombre important d’erreurs, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] ne peut pas enregistrer certaines des erreurs, en raison d’une limite de taille de la banque de journal des événements. Vous pouvez afficher toutes les erreurs dans l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT), mais vous n’êtes peut-être pas en mesure de tous les afficher dans le journal des erreurs.  
  
## <a name="reinstalling-btahl7-under-a-different-folder-will-cause-the-default-receive-locations-not-to-work"></a>Réinstaller BTAHL7 sous un autre dossier sera la valeur par défaut de cause emplacements de réception de fonctionner  
 Réinstallation de BTAHL7 sous un autre dossier entraînera l’emplacement par défaut pour BatchControlPort ou aux ports créés par lancer le didacticiel de fonctionner, car l’URI (conformément à l’installation précédente) pour ces ports ne correspondront pas les nouveaux dossiers créés par le programme d’installation. Pour ces ports à utiliser, vous devez mettre à jour le chemin d’accès du dossier dans la boîte de dialogue Propriétés du Transport FILE pour ces ports.  
  
 Si un ou plusieurs ports MLLP existent dans BizTalk lors de la désinstallation de BTAHL7, l’adaptateur MLLP ne sera pas supprimé. Une fois que cela se produit, si vous installez le produit à un autre emplacement, tous les ports MLLP nouveau ou anciens cesseront de fonctionner. Pour MLLP fonctionne, vous devez désinstaller et réinstaller l’adaptateur MLLP. Pour plus d’informations, consultez « l’adaptateur MLLP n’est pas supprimé pendant la désinstallation » dans [autres problèmes de dépannage](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-other-issues.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)