---
title: "L’importation de certificats à l’aide de l’utilitaire CertWizard | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, root keys
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- CertWizard utility
- certificates, importing
- root keys
ms.assetid: 0c54d7ab-69cf-4f4a-b976-6f740a41280b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64be28927a49a1fc751870785ff3fc3f55a36cb1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="importing-certificates-using-the-certwizard-utility"></a>L’importation de certificats à l’aide de l’utilitaire CertWizard
Cette rubrique décrit comment importer un certificat en utilisant l’utilitaire CertWizard, un utilitaire de ligne de commande de pas à pas disponible dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel. Cette rubrique décrit l’importation d’un private, public ou clé racine. Elle décrit les commutateurs qui vous permet de configurer le certificat.  
  
 L’utilitaire CertWizard automatise une grande partie des étapes que vous devriez faire manuellement à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC). L’utilitaire CertWizard effectue la **runas** commande pour ouvrir la console MMC comme compte de service hôte. Si vous n’ajoutez pas une **Useridentity** commutateur, il détecte et utilise le compte de service d’hôte, vous invite à entrer un mot de passe. Il stocke et configure le certificat.  
  
 Vous pouvez importer plusieurs certificats en même temps en créant un fichier de commandes avec plusieurs commandes d’utilitaire CertWizard.  
  
### <a name="to-import-a-private-key"></a>Pour importer une clé privée  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** .  
  
    > [!NOTE]
    >  Pour obtenir de l’utilitaire CertWizard, tapez **CertWizard / ?** à l’invite de commandes.  
  
3.  À l’invite de commandes, tapez **CertWizard /Privatekey \<nom de fichier\>.pfx**, où \< *nom de fichier*\>.pfx contient le certificat privé. Pour fournir le mot de passe pour le fichier, ajoutez **/Filepassword \<filepassword\>**  à la commande.  
  
4.  Si vous souhaitez importer le certificat dans un compte spécifique utilisé par l’hôte BizTalk, ajoutez **/Useridentity \<useridentity\> /password \<mot de passe\>**  à la commande.  
  
5.  Si vous souhaitez désigner une empreinte numérique spécifique au cas où le fichier .pfx contient plusieurs certificats, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.  
  
6.  Si vous souhaitez configurer l’utilisation du certificat, ajoutez **/Usage** à la commande, puis ajoutez une des valeurs suivantes :  
  
    -   Ajouter **signe** pour ajouter l’empreinte du certificat en tant que le certificat de signature pour le groupe BizTalk. tel que défini dans la boîte de dialogue pour Microsoft BizTalk Server (Local) dans la Console Administration de BizTalk.  
  
    -   Ajouter **déchiffrer** pour ajouter l’empreinte du certificat en tant que le certificat de déchiffrement pour les hôtes BizTalk, tel que défini dans l’onglet certificat des pages de propriétés pour chaque hôte dans la Console Administration de BizTalk.  
  
    -   Ajouter **les deux** pour ajouter le certificat de l’empreinte numérique pour les deux BizTalk du groupe de la signature du certificat et le certificat de déchiffrement de l’hôte BizTalk.  
  
    -   Ajouter **aucun** lorsque vous ne souhaitez pas définir la configuration pour le groupe BizTalk ou les hôtes BizTalk.  
  
7.  Si vous souhaitez configurer le certificat comme exportable, ajoutez **/Exportable true**. Pour définir le certificat comme non exportable, ajoutez **/Exportable false**, qui est le comportement par défaut.  
  
8.  Appuyez sur **Entrée**.  
  
9. Si vous n’avez pas tapé un des mots de passe requis dans la commande, l’outil vous invite à entrer pour celle-ci. Tapez le mot de passe, puis appuyez sur **entrée**.  
  
10. Si le fichier contient plusieurs certificats, mais vous n’avez pas tapé une empreinte numérique dans la commande, l’outil affiche les empreintes numériques disponibles et vous invite à sélectionner un. Tapez le numéro de l’empreinte numérique que vous souhaitez, puis appuyez sur **entrée**.  
  
     L’outil importe le certificat dans le magasin de \Personal\Certificates pour l’utilisateur spécifié dans le **/useridentity** basculer. Si vous ne spécifiez pas un utilisateur, l’utilisateur par défaut est l’identité de l’utilisateur pour l’hôte BizTalkServerApplication l’hôte BizTalkServerIsolatedHost.  
  
### <a name="to-import-a-public-key"></a>Pour importer une clé publique  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.  
  
3.  À l’invite de commandes, tapez **/PublicKey de CertWizard \<nom de fichier\>.cer**, où \< *nom de fichier*\>.cer contient le certificat public.  
  
4.  Si vous souhaitez désigner une empreinte numérique du certificat dans le fichier .cer ou .der, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.  
  
     L’outil importe le certificat dans le magasin de \Other People\Certificates de certificats (ordinateur Local) et définit sa configuration.  
  
### <a name="to-import-a-root-key"></a>Pour importer une clé racine  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.  
  
3.  À l’invite de commandes, tapez **CertWizard /Rootkey \<nom de fichier\>.cer**, où \< *nom de fichier*\>.cer contient le certificat racine.  
  
4.  Si vous souhaitez désigner une empreinte numérique du certificat dans le fichier .cer ou .der, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.  
  
     L’outil importe le certificat dans le magasin de \Trusted Root Certification Authority\Certificates de certificats (ordinateur Local) et définit sa configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)   
 [Gestion des certificats](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)