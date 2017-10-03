---
title: "Étape 2 : Création publics et privés certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating certificates
- public certificates
- certificates, public certificates
- creating, certificates
- private certificates
ms.assetid: 0a925d89-03d9-41fe-907b-85a6ae42362a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d9653f1ec72e56b225142d2d6c9fdff24198e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-public-and-private-certificates"></a>Étape 2 : Création publiques et privées des certificats
Dans cette étape, vous utilisez l’autorité de Certification créé dans [étape 1 : création d’une autorité de Certification &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md) pour générer les certificats publics et privés qui utilisent des organisations Contoso et Fabrikam.  
  
### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a>Pour générer les certificats de chiffrement de Contoso et Fabrikam  
  
1.  Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv.  
  
2.  Sur le **Bienvenue** , cliquez sur **demander un certificat**.  
  
3.  Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.  
  
4.  Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.  
  
5.  Sur le **demande de certificat avancée** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam chiffrement**.|  
    |**Courrier électronique**|Type  **jdoe@fabrikam.com** .|  
    |**Company**|Type **Fabrikam**.|  
    |**Service**|Type **Test**.|  
    |**Ville**|Type **Test**.|  
    |**État**|Type **Test**.|  
    |**Pays/région**|Type **US**.|  
    |**Type de certificat nécessaire**|Sélectionnez **certificat de Protection de courrier électronique** à partir de la zone de liste déroulante.|  
    |**Utilisation de la clé**|Sélectionnez le **Exchange** option.|  
    |**Options de clé supplémentaires**|Activez les options suivantes :<br /><br /> -   **Marquer les clés comme étant exportables**<br />-   **Stocker le certificat dans le magasin de certificats ordinateur local**|  
    |**Nom convivial**|Type **Fabrikam chiffrement**.|  
  
6.  Cliquez sur **Submit**, puis cliquez sur **Oui** dans **Confirmation d’accès au Web** boîte de dialogue.  
  
7.  Sur le **délivré** , cliquez sur **installer ce certificat**.  
  
8.  Répétez les étapes 1 à 7, en modifiant les informations contenues dans le **nom** zone le **Information d’identification** section et le **nom convivial** boîte à **Contoso Chiffrement**.  
  
### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a>Pour générer de Contoso et Fabrikam des certificats de signature  
  
1.  Dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv.  
  
2.  Sur le **Bienvenue** , cliquez sur **demander un certificat**.  
  
3.  Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.  
  
4.  Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.  
  
5.  Sur le **demande de certificat avancée** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam Signature**.|  
    |**Courrier électronique**|Type  **jdoe@fabrikam.com** .|  
    |**Company**|Type **Fabrikam**.|  
    |**Service**|Type **Test**.|  
    |**Ville**|Type **Test**.|  
    |**État**|Type **Test**.|  
    |**Pays/région**|Type **US**.|  
    |**Type de certificat nécessaire**|Sélectionnez **certificat de Protection de courrier électronique**contre la zone de liste déroulante.|  
    |**Utilisation de la clé**|Sélectionnez le **Signature** option.|  
    |**Options de clé supplémentaires**|Activez les options suivantes :<br /><br /> -   **Marquer les clés comme étant exportables**<br />-   **Stocker le certificat dans le magasin de certificats ordinateur local**|  
    |**Nom convivial**|Type **Fabrikam Signature**.|  
  
6.  Cliquez sur **Submit**, puis cliquez sur **Oui** lorsque vous êtes invité à la demande de certificat.  
  
7.  Sur le **délivré** , cliquez sur **installer ce certificat**.  
  
8.  Répétez les étapes 1 à 7, en modifiant les informations contenues dans le **nom** zone le **Information d’identification** section et le **nom convivial** boîte à **Contoso Signature**.  
  
### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a>Pour générer les certificats privés pour les certificats de chiffrement et de Signature  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **MMC**, puis cliquez sur **OK**.  
  
2.  Dans la fenêtre Console1, sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.  
  
3.  Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable sur le **autonome** , cliquez sur **ajouter**.  
  
4.  Dans la boîte de dialogue Ajouter Standalone Snap-in, sélectionnez le **certificats** -composant logiciel enfichable à partir de la **enfichables Standalone** liste, puis cliquez sur **ajouter**.  
  
5.  Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **mon compte d’utilisateur**, puis cliquez sur **suivant**.  
  
6.  Dans la boîte de dialogue Sélectionner un ordinateur, cliquez sur **Terminer**.  
  
7.  Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **fermer**.  
  
8.  Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **OK**.  
  
9. Dans la fenêtre Console1, développez **certificats (ordinateur Local)**, développez **personnel**, puis cliquez sur **certificats**.  
  
10. Dans le volet droit, cliquez sur le **Fabrikam chiffrement** de certificat, pointez sur **toutes les tâches**, puis cliquez sur **exporter**.  
  
11. Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.  
  
12. Sur le **exporter la clé privée** page, sélectionnez **Oui, exporter la clé privée**, puis cliquez sur **suivant**.  
  
13. Sur le **Format de fichier d’exportation** , assurez-vous que **Personal Information Exchange** est la seule option sélectionnée, puis cliquez sur **suivant**.  
  
14. Sur le **mot de passe** page, dans le **mot de passe** et **confirmer le mot de passe** zones, tapez **mysecret**, puis cliquez sur **suivant** .  
  
15. Sur le **fichier à exporter** , cliquez sur **Parcourir**.  
  
16. Dans le **enregistrer en tant que** boîte de dialogue Enregistrer le certificat en utilisant le chemin d’accès du fichier  *\<lecteur >*: \Certs\Fabrikam privé Encryption.pfx.  
  
17. Sur le **fichier à exporter** , cliquez sur **suivant**.  
  
18. Sur le **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**.  
  
19. Dans le menu contextuel Assistant Exportation de certificat indiquant la réussite de l’exportation, cliquez sur **OK**.  
  
20. Répétez les étapes 10 à 19 pour le certificat de Signature de Fabrikam en utilisant le nom de fichier Signature.pfx de Fabrikam privé.  
  
21. Répétez les étapes 10 à 19 pour les certificats de Signature de Contoso et le chiffrement Contoso en utilisant les noms de fichiers Contoso privé Signature.pfx et Contoso privé Encryption.pfx, respectivement.  
  
### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a>Pour générer les certificats publics pour les certificats de chiffrement et de Signature  
  
1.  Dans la fenêtre Console1, développez **certificats-utilisateur actuel**, développez **personnel**, puis cliquez sur **certificats**.  
  
2.  Avec le bouton droit le **Fabrikam chiffrement** de certificat, pointez sur **toutes les tâches**, puis cliquez sur **exporter**.  
  
3.  Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.  
  
4.  Sur le **exporter la clé privée** page, sélectionnez **non, ne pas exporter de la clé privée**, puis cliquez sur **suivant**.  
  
5.  Sur le **Format de fichier d’exportation** , cliquez sur **suivant**.  
  
6.  Sur le **fichier à exporter** , cliquez sur **Parcourir**.  
  
7.  Dans la boîte de dialogue Enregistrer sous, entrez  **\<lecteur > : \Certs** pour **enregistrer dans**, **Encryption.cer Public de Fabrikam** comme **nom de fichier**, et  **\*.cer** pour **enregistrer en tant que type**, puis cliquez sur **enregistrer**.  
  
8.  Sur le **fichier à exporter** , cliquez sur **suivant**.  
  
9. Sur le **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**.  
  
10. Dans le menu contextuel Assistant Exportation de certificat indiquant la réussite de l’exportation, cliquez sur **OK**.  
  
11. Répétez les étapes 1 à 9 pour le certificat de Signature de Fabrikam en utilisant le nom de fichier Signature.cer Public de Fabrikam.  
  
12. Répétez les étapes 1 à 9 pour les certificats de Signature de Contoso et le chiffrement Contoso en utilisant les noms de fichiers Signature.cer publics de Contoso et Encryption.cer publics de Contoso, respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Importation publiques et privées des certificats](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)