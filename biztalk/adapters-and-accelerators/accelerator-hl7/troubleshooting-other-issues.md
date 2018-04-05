---
title: Résolution d’autres problèmes | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 1f115f64-45ce-445d-ab18-092f4a6a232c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796482df7234e2699b5b9bd3d1c12f6e98ccb923
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-other-issues"></a>Résolution d’autres problèmes
Autres problèmes liés à des adresses [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].  
  
## <a name="message-rejected-by-the-btahl7-engine"></a>Message rejeté par le moteur de BTAHL7  
  
### <a name="symptom"></a>Symptôme  
 Les messages sont rejetés aléatoirement par le moteur de messagerie.  
  
**Cause possible** : selon la norme HL7, valeurs d’énumération pour la table 0338 contient la valeur « L & I ». 6 de champ du segment PRA peut contenir cette valeur. Étant donné que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traite le caractère « & » comme un délimiteur, le message est rejeté.  
  
**Résolution** : il existe trois solutions possibles pour résoudre ce problème :  
  
1.  Dans l’instance de message, gérer le caractère « & » via une séquence d’échappement, telles que l’utilisation de la combinaison de caractères L\T\I.  
  
2.  Ajouter une valeur d’énumération de « LI » à PRA 6 dans le schéma et utiliser à la place de cette valeur dans l’instance de message.  
  
3.  Utilisez un séparateur de sous-composant complètement différentes dans où MSH2 a été ; Toutefois, cette solution ne peut pas être pratique, en fonction de votre environnement.  
  
## <a name="cannot-edit-the-hl7-schema-using-visual-studio"></a>Impossible de modifier le schéma HL7 à l’aide de Visual Studio  
  
### <a name="symptom"></a>Symptôme  
 Impossible de modifier le schéma HL7 avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
**Cause possible** : [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ne prend pas en charge certains schémas HL7.  
  
**Résolution** : utiliser les autres éditeurs, tels que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] le bloc-notes, pour modifier les schémas HL7.  
  
## <a name="message-handling-fails-with-no-errors-logged"></a>Échec de la gestion des messages sans erreur connecté  
  
### <a name="symptom"></a>Symptôme  
 Le système traite les messages sans enregistrer les messages d’erreur ou de placer les messages dans la file d’attente de message suspendu.  
  
**Cause possible** : le **HeaderSpecType** et **DocumentSpecType** les valeurs de propriété respectent la casse. Lorsque vous déployez vos pipelines, une erreur typographique dans ces noms peut entraîner des messages d’erreur de manipulation et de supprimée sans erreur connecté.  
  
**Résolution** : observer le respect de la casse lors de l’utilisation du **HeaderSpecType** et **DocumentSpecType** les noms de valeurs de propriété.  
  
## <a name="message-header-fields-are-not-validated-correctly"></a>Champs d’en-tête de message ne sont pas validés correctement  
  
### <a name="symptom"></a>Symptôme  
 Échec de la validation d’un champ d’en-tête.  
  
 Raison : Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur validé une propriété promue, pas la propriété de contexte de champ d’en-tête réelle.  
  
**Cause possible** : une modification s’est produite à la propriété promue correspondant à l’en-tête via une orchestration ou un mappage.  
  
**Résolution** : les propriétés de contexte de message, en-têtes MSH1, où MSH2 a été et MSH5 {1-3} devoir être mis à jour afin qu’ils soient synchronisés avec les données.  
  
## <a name="the-mllp-adapter-is-not-removed-during-uninstall"></a>L’adaptateur MLLP n’est pas supprimé lors de la désinstallation  
  
### <a name="symptom"></a>Symptôme  
 Le programme d’installation BTAHL7 n’a pas supprimé l’adaptateur MLLP lors de la désinstallation de BTAHL7.  
  
**Cause possible** : il y a un port de réception emplacement ou d’envoi avec un type de transport de MLLP. Le programme d’installation BTAHL7 ne peut pas supprimer l’adaptateur MLLP si elle est référencée dans un des projets BizTalk Server.  
  
**Résolution** : à l’issue de la désinstallation de BTAHL7, procédez comme suit :  
  
1.  Dans la Console Administration de BizTalk Server, supprimez tous les emplacements de réception et ports d’envoi qui ont un type de transport de MLLP, ou modifier le type de transport, les emplacements de réception ou ports d’envoi à un autre type.  
  
2.  Dans la Console d’Administration, supprimez l’adaptateur MLLP.  
  
3.  Redémarrez l’instance d’hôte.  
  
## <a name="btahl7-cannot-be-uninstalled-if-biztalk-server-has-already-been-uninstalled"></a>BTAHL7 ne peut pas être désinstallé si BizTalk Server a déjà été désinstallé  
  
### <a name="symptom"></a>Symptôme  
 Désinstallation [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] entraîne l’erreur suivante :  
  
`A network error while attempting to read from file C:\Windows\Installer\Microsoft BizTalk <version\> Accelerator for HL7.msi`
  
**Cause possible** : [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] a été désinstallée avant la désinstallation de [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] a été tentée. Vous devez désinstaller [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] avant de désinstaller [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].  
  
**Résolution** : Réinstallez [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], puis désinstallez [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], puis désinstallez [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="messages-are-still-sent-after-the-applicable-mllp-send-port-has-been-stopped"></a>Les messages sont toujours envoyés une fois que le port d’envoi MLLP applicable a été arrêté.  
  
### <a name="symptom"></a>Symptôme  
 Après avoir arrêter un MLLP port d’envoi, les messages qui sont envoyées via ce port d’envoi n’arrêtez pas, mais continuer à envoyer.  
  
**Cause possible** : lorsque vous arrêtez un port d’envoi, la connexion reste établie jusqu'à ce qu’il soit supprimé par l’arrêt de l’hôte BizTalk. Par conséquent, les messages sont envoyés encore une fois que le port d’envoi a été arrêté. Cela se produit, car Biztalk Server n’appelle pas dans l’adaptateur MLLP au cours de démarrage ou d’arrêt du port d’envoi. BizTalk Server appelle l’adaptateur MLLP uniquement pendant le démarrage et arrêt du service hôte.  
  
**Résolution** : vous pouvez supprimer la transmission de connexion et d’arrêter des messages par l’arrêt de l’instance d’hôte qui est le Gestionnaire d’envoi pour le port d’envoi que vous avez arrêtés. Toutefois, l’arrêt de cette instance d’hôte peut affecter les autres messages que vous ne souhaitez pas arrêter. Si vous savez que c’est le cas, vous devez configurer le port d’envoi différemment lorsque vous la créez. Vous devez créer une autre instance de l’hôte pour servir le Gestionnaire d’envoi pour seulement ce port d’envoi MLLP (ou un sous-ensemble de vos ports d’envoi). Vous pouvez ensuite arrêter la transmission des messages à partir de ce port d’envoi par l’arrêt de cette instance d’hôte. Cela affectera puis pas la transmission d’autres messages d’autres ports d’envoi qui utilisent d’autres gestionnaires d’envoi.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus et dépannage dans HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)