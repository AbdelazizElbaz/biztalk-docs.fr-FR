---
title: "Étape 1 : Création d’une autorité de Certification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, creating
- double action tutorial, creating certificates
- creating, certificates
ms.assetid: b6ecd534-6b03-4336-8337-33ec18a0802a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94a2b02b654983701323703edcc1b3ba3fcca13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-a-certification-authority"></a>Étape 1 : Création d’une autorité de Certification
Dans cette rubrique, vous installez les Services de certificats [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composant. Il permet de générer les certificats que vous devez promouvoir une communication sécurisée entre les organisations de Contoso et Fabrikam. Chaque partenaire commercial aura un certificat de chiffrement privé pour la communication et un certificat de signature privée à des fins d’identification. En outre, les partenaires partagent leurs certificats de clé publique entre eux pour promouvoir une communication sécurisée lors de l’implémentation de la 3A2 processus PIP (Partner Interface).  
  
### <a name="to-install-the-certificate-server"></a>Pour installer le certificat de serveur  
  
1.  Cliquez sur **Démarrer**, pointez sur **paramètres**, puis cliquez sur **le panneau de configuration**. Double-cliquez sur **ajouter ou supprimer des programmes**.  
  
2.  Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.  
  
3.  Sur le **Assistant Composants de Windows** page, dans le **composants** section, sélectionnez **les Services de certificats**, cliquez sur **Oui**, puis cliquez sur **Suivant** pour démarrer l’Assistant Configuration de composants.  
  
    > [!NOTE]
    >  Si le **ServicesWindows de certificats** composant est déjà activée, ignorez le reste de cette procédure.  
  
4.  Sur le **Type d’autorité de certification** , assurez-vous que **autorité racine autonome** est sélectionné, puis cliquez sur **suivant**.  
  
5.  Sur le **les informations d’identification autorité de certification** page, dans le **nom commun de cette autorité de certification** , tapez **Contoso-FabrikamCA**, puis cliquez sur **suivant**.  
  
6.  Sur le **paramètres de base de données de certificat** page, laissez les valeurs par défaut, puis cliquez sur **suivant**.  
  
7.  Cliquez sur **Oui** lorsque l’Assistant vous invite à arrêter les Internet Information Services (IIS).  
  
8.  Cliquez sur **Oui** si le **Assistant Composants de configuration** vous invite à activer Active Server Pages.  
  
9. Cliquez sur **Terminer** pour fermer la **Assistant Composants de Windows**.  
  
    > [!NOTE]
    >  Vous devez uniquement utiliser un seul ordinateur en tant que l’autorité de Certification. Il est inutile de répéter cette procédure sur le deuxième ordinateur. Ce didacticiel utilise l’ordinateur Contoso en tant que l’autorité de Certification.  
  
### <a name="to-install-a-root-certification-authority-ca-for-windows-server-2008"></a>Pour installer une autorité de Certification (CA) racine pour Windows Server 2008  
  
1.  Ouvrez le Gestionnaire de serveur, cliquez sur **ajouter des rôles** dans des rôles, cliquez sur **suivant**, puis cliquez sur **certificat Active Directory** Services case à cocher. Cliquez sur **suivant** à deux reprises.  
  
2.  Dans la page Sélectionner les Services de rôle, cliquez sur **autorité de Certification et inscription de l’autorité de Certification via le Web**. Cliquez sur **Suivant**.  
  
3.  Dans la page spécifier le Type d’installation, cliquez sur **autonome**. Cliquez sur **Suivant**.  
  
4.  Dans la page spécifier le Type autorité de certification, cliquez sur l’autorité de certification racine. Cliquez sur **Suivant**.  
  
5.  Dans la page Configurer la clé privée, cliquez sur Créer une nouvelle clé privée. Cliquez sur **Suivant**.  
  
6.  Sur la cryptographie configurer pour la page de l’autorité de certification. Cliquez sur **Suivant**.  
  
7.  Configurer des nom d’autorité de certification, dans la zone Nom commun de cette autorité de certification, tapez Contoso-FabrikamCA, puis cliquez sur **suivant**.  
  
8.  Dans la page Définir la période de validité, cliquez sur **suivant**.  
  
9. Dans la page Configuration de base de données de certificat, cliquez sur **suivant**.  
  
10. Dans la page Confirmer les Options d’Installation, cliquez sur **installer**.  
  
### <a name="configuring-the-web-site-for-the-ca-to-use-https-authentication"></a>Configuration du site Web de l’autorité de certification à utiliser l’authentification HTTPS  
  
1.  Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, cliquez sur Démarrer, pointez sur tous les programmes, pointez sur Outils d’administration, puis cliquez sur Gestionnaire des Services Internet (IIS).  
  
2.  Dans la boîte de dialogue Gestionnaire des Services Internet (IIS), cliquez droit **Site Web par défaut et sélectionnez Modifier les liaisons...** dans le menu contextuel.  
  
3.  Dans la boîte de dialogue liaisons de Site, cliquez sur **ajouter**.  
  
4.  Dans la boîte de dialogue Ajouter une liaison de Site, sélectionnez **https** dans la liste déroulante Type, sélectionnez le certificat à partir de **certificat SSL** liste déroulante et cliquez sur **OK**.  
  
5.  Cliquez sur **fermer** pour fermer les liaisons du Site... boîte de dialogue.  
  
### <a name="to-download-the-ca-certificate"></a>Pour télécharger le certificat d’autorité de certification  
  
1.  Dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv/Default.asp.  
  
2.  Dans la page Default.asp, cliquez sur **télécharger un certificat autorité de certification, chaîne de certificats ou la liste de révocation**.  
  
3.  Assurez-vous que **actuel [Contoso-FabrikamCA]** est sélectionné dans le **certificat d’autorité de certification** liste, puis cliquez sur **télécharger le certificat de CA**.  
  
4.  Enregistrez le certificat sur C:\Certs\Contoso-FabrikamCA.cer sur l’ordinateur Fabrikam et Contoso.  
  
### <a name="to-import-the-ca-certificate-to-the-trusted-root-certification-authorities-store"></a>Pour importer le certificat d’autorité de certification dans le magasin d’autorités de Certification racines de confiance  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au  **\<lecteur > : \Program Files\MicrosoftBizTalk \<version > Accelerator for RosettaNet\SDK**, puis appuyez sur **entrée**.  
  
3.  À l’invite de commandes, tapez **CertWizard /Rootkey »\<lecteur > : \Certs\Contoso-FabrikamCA.cer «**, puis appuyez sur **entrée**.  
  
    > [!IMPORTANT]
    >  Effectuez cette procédure sur les ordinateurs de Contoso et Fabrikam.  
  
### <a name="to-enable-automatic-certificate-issuing"></a>Pour activer l’émission de certificat automatique  
  
1.  Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur  **Autorité de certification**.  
  
2.  Dans la boîte de dialogue Autorité de Certification, cliquez sur **Contoso-FabrikamCA**, puis cliquez sur **propriétés**.  
  
3.  Dans la boîte de dialogue Propriétés de Contoso-FabrikamCA sur la **Module de stratégie** , cliquez sur **propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés, sélectionnez **suivre les paramètres dans le modèle de certificat**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue FabrikamCA de Contoso.  
  
6.  Fermez la boîte de dialogue Autorité de Certification.  
  
    > [!NOTE]
    >  En activant l’émission automatique de certificats, les Services de certificats automatise la procédure d’émission des certificats. Vous devez redémarrer les Services de certificats pour appliquer cette modification.  
    >   
    >  Vous devrez peut-être installer le certificat racine Contoso-FabrikamCA.cer dans les autorités de Certification de racine User\Trusted actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Création publiques et privées des certificats](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)