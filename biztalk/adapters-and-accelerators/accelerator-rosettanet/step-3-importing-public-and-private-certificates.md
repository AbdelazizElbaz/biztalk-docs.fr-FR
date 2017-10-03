---
title: "Étape 3 : Importation publics et privés certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public certificates
- importing certificates
- private certificates
- double action tutorial, importing certificates
- certificates, importing
ms.assetid: 955bdd69-9fbc-4100-ab8a-8f5dd4a17cbb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c910a72f3e5ef39bb2e07e410f484e8c5cbececa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-importing-public-and-private-certificates"></a>Étape 3 : Importation publiques et privées des certificats
Dans cette étape, vous importez les certificats que vous avez créé dans [étape 2 : création d’un Public et privé certificats &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) sur les ordinateurs de Contoso et Fabrikam. Chaque ordinateur importe ses propres certificats privés et importe les certificats publics de l’autre organisation.  
  
> [!NOTE]
>  Vous devez transférer les certificats privés de Fabrikam et les certificats publics de Contoso à l’ordinateur Fabrikam pour les importer. Cette étape suppose que vous placez ces certificats dans le dossier C:\Certs sur l’ordinateur Fabrikam.  
  
### <a name="to-import-the-contoso-private-certificates-on-the-contoso-computer"></a>Pour importer les certificats privés Contoso sur l’ordinateur Contoso  
  
1.  Sur l’ordinateur Contoso, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au  **\<**  *lecteur***> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** puis appuyez sur **entrée**.  
  
3.  À l’invite de commandes, tapez **CertWizard /Privatekey »\<***lecteur***> : \Certs\Contoso privé Encryption.pfx «**, puis appuyez sur  **Entrez**.  
  
4.  À la **Veuillez entrer le mot de passe pour le fichier de certificat** tapez **mysecret**, puis appuyez sur **entrée**.  
  
5.  À la **Entrez le mot de passe pour l’identité < contoso_machine > \HostSvc** invite, tapez le mot de passe du compte HostSvc, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Si votre BizTalkServerApplication s’exécute sous un nom de compte différent de HostSvc, l’invite doit être différent.  
  
6.  À la **ce certificat accueil sera utilisé pour** tapez **D**, puis appuyez sur **entrée**.  
  
     Le CertWizard importe le certificat dans le magasin de \Personal\Certificates pour hôtes BizTalkServerApplication et BizTalkServerIsolatedHost s’exécutent sous les comptes d’utilisateur.  
  
7.  Répétez les étapes 3 à 6 pour le certificat privé de Contoso Signature.pfx spécifiant qu’il est un certificat de signature en tapant **S** à la **ce certificat accueil sera utilisé pour** invite indiqué à l’étape 6.  
  
### <a name="to-import-the-fabrikam-public-certificates-on-the-contoso-computer"></a>Pour importer les certificats publics Fabrikam sur l’ordinateur Contoso  
  
1.  Sur l’ordinateur Contoso, cliquez sur **Démarrer**, cliquez sur **exécuter,** type **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .  
  
3.  À l’invite de commandes, tapez **/PublicKey de CertWizard «***\<lecteur >***: \Certs\Fabrikam Encryption.cer publique «**, puis appuyez sur  **Entrez**.  
  
4.  Répétez l’étape 3 pour le certificat Signature.cer Public de Fabrikam.  
  
### <a name="to-import-the-fabrikam-private-certificates-on-the-fabrikam-computer"></a>Pour importer les certificats privés Fabrikam sur l’ordinateur Fabrikam  
  
1.  Copiez les fichiers suivants à partir de l’ordinateur Contoso à la \<lecteur > : dossier \Certs sur l’ordinateur Fabrikam : Encryption.cer publics de Contoso, Signature.cer publics de Contoso, Encryption.pfx privé de Fabrikam et Fabrikam privé Signature.pfx.  
  
2.  Sur l’ordinateur Fabrikum, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
3.  À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .  
  
4.  À l’invite de commandes, tapez **CertWizard /Privatekey »***\<lecteur >***: \Certs\Fabrikam privé Encryption.pfx «**, puis appuyez sur **Entrez**.  
  
5.  À la **Veuillez entrer le mot de passe pour le fichier de certificat** tapez **mysecret**, puis appuyez sur **entrée**.  
  
6.  À la **Entrez le mot de passe pour l’identité < fabrikam_machine > \HostSvc** invite, tapez le mot de passe du compte HostSvc, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Si votre BizTalkServerApplication s’exécute sous un nom de compte différent de HostSvc, l’invite doit être différent.  
  
7.  À la **ce certificat accueil sera utilisé pour** tapez **D**, puis appuyez sur **entrée**.  
  
     Le CertWizard importe le certificat dans le magasin de \Personal\Certificates pour hôtes BizTalkServerApplication et BizTalkServerIsolatedHost s’exécutent sous les comptes d’utilisateur.  
  
8.  Répétez les étapes 4 à 7 pour le certificat privé de Fabrikam Signature.pfx spécifiant qu’il est un certificat de signature en tapant **S** à la **ce certificat accueil sera utilisé pour** invite de commandes à l’étape 6.  
  
### <a name="to-import-the-contoso-public-certificates-on-the-fabrikam-computer"></a>Pour importer les certificats publics Contoso sur l’ordinateur Fabrikam  
  
1.  Sur l’ordinateur Fabrikum, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .  
  
3.  À l’invite de commandes, tapez **/PublicKey de CertWizard «***\<lecteur >***: \Certs\Contoso Encryption.cer publique «**, puis appuyez sur  **Entrez**.  
  
4.  Répétez l’étape 3 pour le certificat Signature.cer publics de Contoso.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Sécurisé Sockets Layer dans IIS](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)