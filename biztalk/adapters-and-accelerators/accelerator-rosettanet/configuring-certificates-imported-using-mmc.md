---
title: "Configuration des certificats importés à l’aide de MMC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decryption certificates
- certificates, decryption certificates
- certificates, signing certificates
- importing certificates
- signing certificates
- certificates, importing
ms.assetid: 64dbfbcf-6026-4c68-a93a-f483ec52deac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f60811a8b6875c8cbcf4a8037501855a08fe0be6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-certificates-imported-using-mmc"></a>Configuration des certificats importés à l’aide de MMC
Après avoir importé des certificats à l’aide du composant logiciel enfichable Certificats pour le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC), vous devez configurer leur utilisation. Cela nécessite la configuration du groupe BizTalk, les comptes de service d’hôte BizTalk et l’hôte isolé, PIP (PIP), commercial des accords de partenariat et partenaires. Vous devez effectuer les étapes suivantes :  
  
> [!NOTE]
>  Si vous utilisez l’utilitaire CertWizard pour importer et configurer un certificat, vous n’avez pas à effectuer ces étapes manuelles.  
  
-   Configurer l’utilisation d’un certificat de signature pour l’organisation d’origine. Cela signifie que vous utilisez une clé privée pour identifier l’organisation d’origine dans les messages sortants. Pour ce faire, vous configurez le certificat de signature pour le groupe BizTalk.  
  
-   Configurer l’utilisation d’un certificat de déchiffrement pour l’organisation d’origine. Cela signifie que vous utilisez une clé privée, ce qui correspond à la clé publique partenaire, pour déchiffrer les messages entrants. Pour ce faire, vous configurez le certificat de déchiffrement pour chaque hôte BizTalk et les comptes de service d’hôte BizTalk isolé. Vous devez entrer le même certificat de déchiffrement pour l’hôte et les comptes de service hôte isolé pour [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] vous devez définir le même compte.  
  
    > [!NOTE]
    >  Les hôtes BizTalk et l’hôte isolé doivent avoir le même certificat de déchiffrement afin qu’ils peuvent déchiffrer les messages entrants chiffrées mêmes. L’hôte BizTalk isolé qui exécute l’adaptateur HTTP doit disposer du certificat pour recevoir les messages, car il n’a pas accès au certificat d’ordinateur hôte. L’hôte BizTalk doit avoir le certificat pour traiter les messages après [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] a reçus.  
  
-   Configurez le chiffrement et la signature des certificats pour chaque partenaire. Pour ce faire, vous entrez les certificats sur le **général** onglet de la **partenaire** page de propriétés dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Console de gestion. Ceux-ci incluent un certificat de chiffrement à clé publique pour chiffrer les messages sortants à un partenaire et un certificat de signature de clé publique pour vérifier l’identité du partenaire sur les messages entrants. Pour plus d’informations, consultez [création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
-   Configurer la stratégie de chiffrement entre une organisation d’origine et un partenaire commercial. Pour ce faire, vous configurez l’accord de partenariat commercial sur les **protocole** onglet de la **propriétés de l’accord** page dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
### <a name="to-configure-the-signing-certificate-for-a-biztalk-group-or-the-decryption-certificate-for-a-biztalk-host"></a>Pour configurer le certificat de signature pour un groupe BizTalk ou le certificat de déchiffrement d’un hôte BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **runas/user :\<héberger service > mmc**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour \< *héberger le service*>, tapez le nom du service que vous avez associé le service hôte lors de l’installation [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
2.  Tapez le mot de passe \< *héberger le service*>, puis appuyez sur ENTRÉE.  
  
3.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
4.  Développez **Certificats - Utilisateur actuel**, développez **Personnel**, puis cliquez sur **Certificats**.  
  
5.  Dans le volet droit, double-cliquez sur un certificat privé.  
  
6.  Dans la fenêtre certificat, sur le **détails** , cliquez sur **l’empreinte numérique**, puis sélectionnez le numéro d’identification hexadécimal dans la fenêtre d’affichage. Appuyez sur CTRL + C pour le copier.  
  
7.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
8.  Pour configurer le certificat de signature pour un groupe BizTalk, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, puis cliquez sur **propriétés**. Cliquez dans la zone de texte à droite de **l’empreinte numérique**, appuyez sur CTRL + V pour coller le numéro d’empreinte numérique dans la zone de texte, puis cliquez sur **OK**.  
  
9. Pour configurer le certificat de déchiffrement pour un hôte BizTalk, développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, développez **hôtes**, cliquez sur l’ordinateur hôte que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
10. Sur le **certificat** , cliquez sur dans la zone de texte à droite de **l’empreinte numérique**, appuyez sur CTRL + V pour coller le numéro d’empreinte numérique dans la zone de texte, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Vous devez configurer les certificats de déchiffrement sur l’hôte BizTalk (BizTalkServerApplication) et l’hôte BizTalk isolé (BizTalkServerIsolatedHost).  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des certificats](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)