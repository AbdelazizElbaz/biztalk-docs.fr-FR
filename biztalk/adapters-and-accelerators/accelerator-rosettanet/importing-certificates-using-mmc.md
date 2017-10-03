---
title: "L’importation de certificats à l’aide de MMC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- certificates, importing
ms.assetid: 58fb1711-e295-4aa6-902e-e28e4a2cd921
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030b711e0fd48d2632ff84428e1cb9ffc6e0402
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates-using-mmc"></a>L’importation de certificats à l’aide de MMC
Cette rubrique décrit comment importer un numérique de certificat qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise pour authentifier un partenaire commercial, déchiffrer un message entrant, ou chiffrer ou signer un message sortant.  
  
 Cette procédure utilise le composant logiciel enfichable Certificats pour le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC). Ce processus manuel importe un certificat dans le magasin de certificats que vous ayez besoin de configurer séparément les utilisation de certificats. Vous pouvez également importer un certificat à l’aide de l’utilitaire CertWizard qui configure automatiquement le certificat utilisé pour vous.  
  
 Pour importer les certificats privés, vous devez utiliser les comptes d’utilisateur sous lequel exécuter les hôtes BizTalk.  
  
### <a name="to-import-a-public-key-certificate"></a>Pour importer un certificat de clé publique  
  
1.  Copie le certificat de clé publique (.cer) du fichier vers un emplacement sur le disque dur du serveur sur lequel vous copiez des certificats.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
3.  Dans le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, développez **certificats (ordinateur Local)**. L’utilisateur connecté doit disposer d’autorisations administratives sur l’ordinateur.  
  
4.  Avec le bouton droit **autres personnes**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.  
  
5.  Sur le **certificat Assistant Importation de** , cliquez sur **suivant**.  
  
6.  Sur le **fichier à importer** , cliquez sur **Parcourir** et recherchez le dossier qui contienne les fichiers de certificat. Sélectionnez le fichier à partir de laquelle vous souhaitez importer le certificat, puis cliquez sur **ouvrir**.  
  
7.  Sur le **magasin de certificats** page, sélectionnez **sélectionner automatiquement le certificat basé sur le type de certificat** ou **placer tous les certificats dans le magasin suivant**. Si vous sélectionnez **placer tous les certificats dans le magasin suivant**, cliquez sur **Parcourir**, sélectionnez le magasin de certificats, cliquez sur **OK**, puis cliquez sur **suivant**.  
  
8.  Cliquez sur **Terminer**.  
  
### <a name="to-import-a-private-key-certificate"></a>Pour importer un certificat de clé privée  
  
1.  Certificat de clé privée (.pfx) copie les fichiers vers un emplacement sur le disque dur du serveur sur lequel vous copiez des certificats.  
  
2.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **d’identification/User :\<hôte de service > mmc**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour \< *héberger le service*>, tapez le nom du service qui a été automatiquement sélectionné pour le service hôte lors de l’installation [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
3.  Tapez le mot de passe \< *héberger le service*>, puis appuyez sur **entrée**.  
  
4.  Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] gestion de la Console, sous le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.  
  
5.  Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **ajouter**.  
  
6.  Dans la boîte de dialogue Ajouter Standalone Snap-in, sélectionnez **certificats**, cliquez sur **ajouter**, cliquez sur **fermer**, puis cliquez sur **OK**.  
  
7.  Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, développez **certificats - utilisateur actuel**, avec le bouton droit **personnel**, pointez sur **toutes les tâches**, puis cliquez sur  **Importation**.  
  
8.  Sur le **certificat Assistant Importation de** , cliquez sur **suivant**.  
  
9. Sur le **fichier à importer** , cliquez sur **Parcourir** et recherchez le dossier qui contient le fichier de certificat .pfx qui contient le certificat que vous souhaitez importer. Sélectionnez le fichier approprié, puis cliquez sur **ouvrir**.  
  
10. Sur le **mot de passe** page, dans le **mot de passe** , tapez le mot de passe pour le fichier de clé privée.  
  
11. Sélectionnez **activer la protection renforcée par clé privée** ou **marquer cette clé comme exportable**, puis cliquez sur **suivant**.  
  
12. Sur le **magasin de certificats** page, sélectionnez **sélectionner automatiquement le certificat basé sur le type de certificat** ou **placer tous les certificats dans le magasin suivant**. Si vous sélectionnez **placer tous les certificats dans le magasin suivant**, cliquez sur **Parcourir**, sélectionnez le magasin, cliquez sur **OK**, puis cliquez sur **suivant**.  
  
13. Sur le **fin de l’Assistant Importation de certificat** , cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des certificats importés à l’aide de MMC](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md)   
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)