---
title: "Étape 4 : Sécurisé Sockets Layer dans IIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Secure Socket Layers
- IIS
- double action tutorial, enabling SSL in IIS
- SSL
ms.assetid: 96109294-595a-46ac-974e-33123df79ed5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2964b6ac26d6685a1c38b88c5bbf98e8119f3502
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-enabling-secure-sockets-layer-in-iis"></a>Étape 4 : Sécurisé Sockets Layer dans IIS
Couche de Sockets sécurisée (SSL) est un protocole conçu pour sécuriser le canal de communication entre un client et un serveur. L’activation de SSL dans Microsoft® Internet Information Services (IIS) 7.5/7.0, les organisations de Contoso et Fabrikam de communiquer à l’aide de l’authentification et le chiffrement pour tous les transferts de données. Dans cette étape, vous allez apprendre à activer le protocole SSL dans IIS 7.5/7.0.  
  
> [!NOTE]
>  Vous devez effectuer cette étape sur les ordinateurs de Contoso et Fabrikam.  
  
### <a name="to-prepare-a-new-server-certificate"></a>Pour préparer un nouveau certificat de serveur  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le volet gauche de Internet Information Services, développez  **\<**  *Nom_Ordinateur*  **\>**  (*ordinateur local*), développez **Sites Web**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **propriétés**.  
  
3.  Dans la boîte de dialogue de Sites Web par défaut sur le **sécurité du répertoire** , cliquez sur **certificat de serveur** pour démarrer le **Assistant certificat IIS**.  
  
4.  Sur le **Bienvenue dans l’Assistant certificat de serveur Web** , cliquez sur **suivant**.  
  
5.  Sur le **certificat de serveur** page, sélectionnez **créer un nouveau certificat**, puis cliquez sur **suivant**.  
  
6.  Sur le **demande ultérieure ou immédiate** , cliquez sur **suivant**.  
  
7.  Sur le **nom et les paramètres de sécurité** , cliquez sur **suivant**, en conservant les valeurs par défaut.  
  
8.  Sur le **informations de l’organisation** page, dans le **organisation** , tapez **Contoso** if sur l’ordinateur Contoso ou **Fabrikam** if sur la Ordinateur Fabrikam, dans le **unité d’organisation** , tapez **Test**, puis cliquez sur **suivant**.  
  
9. Sur le **nom commun de votre Site** page, dans le **nom commun** zone, tapez le nom de votre ordinateur, puis cliquez sur **suivant**.  
  
10. Sur le **informations géographiques** page, dans le **State/province** , tapez votre département/province, dans le **Ville/localité** zone, tapez votre ville/localité, puis cliquez sur **Suivant**.  
  
11. Sur le **nom du fichier de demande de certificat** page, dans le **nom de fichier** zone, laissez la valeur par défaut **C:\certreq.txt**, puis cliquez sur **suivant**.  
  
12. Sur le **résumé du fichier de demande** , cliquez sur **suivant**.  
  
13. Sur le **fin de l’Assistant certificat de serveur Web** , cliquez sur **Terminer** pour fermer la **Assistant certificat IIS**.  
  
### <a name="to-generate-a-new-server-certificate"></a>Pour générer un nouveau certificat de serveur  
  
1.  Dans Internet Explorer, recherchez et ouvrez http://\<*contoso_machine*\>/CertSrv.  
  
    > [!NOTE]
    >  À l’étape 1, ouvrez http://\<*contoso_machine*\>/CertSrv sur l’ordinateur Contoso ou Fabrikam.  
  
2.  Sur le **Microsoft Services Assistant certificat** , cliquez sur **demander un certificat.**  
  
3.  Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.  
  
4.  Sur le **demande de certificat avancée** , cliquez sur **soumettre une demande de certificat en utilisant un fichier CMC ou PKCS #10 codé en base 64, ou soumettre une demande de renouvellement en utilisant un fichier PKCS #7 codé en base 64**.  
  
5.  Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **Parcourir pour insérer un fichier**.  
  
    > [!NOTE]
    >  Si vous recevez une erreur de sécurité lorsque vous cliquez sur le lien, ouvrez le fichier C:\certreq.txt dans le bloc-notes ou un autre éditeur de texte, copiez le contenu du fichier et coller ces informations dans le **demande enregistrée** zone, puis cliquez sur  **Envoyer**. Vous pouvez ensuite accéder à l’étape 10.  
  
6.  Cliquez sur **Parcourir** pour ouvrir le **choisir un fichier** boîte de dialogue.  
  
7.  Dans le **choisir un fichier** boîte de dialogue, recherchez le  *\<lecteur\>*: \ dossier, sélectionnez le fichier certreq.txt, puis cliquez sur **ouvrir**.  
  
8.  Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **en lecture**.  
  
9. Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **Submit** pour générer le nouveau certificat.  
  
10. Sur le **délivré** , cliquez sur **télécharger le certificat**.  
  
11. Dans le **télécharger le fichier** boîte de dialogue, cliquez sur **enregistrer**.  
  
12. Dans le **enregistrer en tant que** boîte de dialogue, enregistrez le certificat à \<lecteur\>: \Certs\SSLCert.cer, puis cliquez sur **enregistrer**.  
  
13. Cliquez sur **fermer** pour fermer la **téléchargement terminé** boîte de dialogue.  
  
### <a name="to-prepare-a-new-server-certificate-for-iis"></a>Pour préparer un nouveau certificat de serveur IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le volet gauche de Internet Information Services, cliquez sur < nom_ordinateur > (ordinateur local), double-cliquez sur **des certificats de serveur** dans le volet droit. Sélectionnez **créer une demande de certificat** à partir du volet Actions.  
  
3.  Dans la boîte de dialogue Propriétés du nom unique, tapez le nom de l’ordinateur dans le nom commun : zone de texte, de l’organisation :, tapez **Contoso** if sur l’ordinateur Contoso ou **Fabrikam** if sur Fabrikam ordinateur, dans l’unité d’organisation : type de Test, dans la zone Ville/Localité, tapez votre ville/localité, dans la zone État/province, tapez votre département/province, dans la pays/région de liste déroulante, sélectionnez votre pays/région et puis cliquez sur **suivant**.  
  
4.  Dans la boîte de dialogue Propriétés de fournisseur de chiffrement Service, cliquez sur **suivant**.  
  
5.  Dans la boîte de dialogue Nom de fichier, spécifiez C:\certreq.txt dans la zone de texte, cliquez sur **Terminer**.  
  
### <a name="to-generate-a-new-server-certificate-for-iis"></a>Pour générer un nouveau certificat de serveur pour IIS  
  
1.  Dans Internet Explorer, recherchez et ouvrez http://<contoso_machine>/CertSrv.  
  
    > [!NOTE]
    >  À l’étape 1, ouvrez http://<contoso_machine>/CertSrv sur l’ordinateur Contoso ou Fabrikam.  
  
2.  Dans la page Microsoft Services Assistant certificat, cliquez sur **demander un certificat**.  
  
3.  Dans la page demander un certificat, cliquez sur **demande de certificat avancée**.  
  
4.  Dans la page de demande de certificat avancée, cliquez sur **soumettre une demande de certificat** en utilisant un fichier CMC ou PKCS #10 codé en base 64, ou soumettre une demande de renouvellement en utilisant un fichier PKCS #7 codé en base 64.  
  
5.  Ouvrez le fichier C:\certreq.txt dans le bloc-notes ou un autre éditeur de texte, copiez le contenu du fichier et coller ces informations dans le **demande enregistrée** zone sur l’envoi d’une page de demande de certificat ou une demande de renouvellement, puis cliquez sur **Envoyer**.  
  
6.  Dans la page certificat émis, cliquez sur **télécharger le certificat**.  
  
7.  Dans la boîte de dialogue Téléchargement de fichier, cliquez sur **enregistrer**.  
  
8.  Dans la boîte de dialogue Enregistrer sous, enregistrer le certificat \<lecteur\>: \Certs\SSLCert.cer, puis cliquez sur **enregistrer**.  
  
### <a name="to-import-the-server-certificate-into-iis"></a>Pour importer le certificat de serveur dans IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le volet gauche de Internet Information Services, cliquez sur **(ordinateur local)**, double-cliquez sur **des certificats de serveur** dans le volet droit. Sélectionnez **demande de certificat complète** dans le volet Actions.  
  
3.  Dans le type de boîte de dialogue de réponse de l’autorité spécifier un certificat  **\<lecteur\>: \Certs\SSLCert.cer** dans **nom du fichier contenant la réponse de l’autorité de certification** zone de texte. Dans le type de zone de texte Nom convivial **ContosoSSLCert**.  
  
### <a name="to-enable-ssl-bindings-for-iis"></a>Pour activer les liaisons SSL pour IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le volet gauche de Internet Information Services, développez **(ordinateur local)**, développez **Sites**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **modifier Liaisons**.  
  
3.  Dans la boîte de dialogue liaisons de Site, cliquez sur **ajouter**. Dans la boîte de dialogue Ajouter la liaison de Site, sélectionnez **https** à partir de la liste déroulante Type, sélectionnez **ContosoSSLCert** à partir de la liste de certificats SSL vers le bas, cliquez sur **OK**, cliquez sur **fermer** .  
  
### <a name="to-import-the-server-certificate-into-iis"></a>Pour importer le certificat de serveur dans IIS  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le volet gauche de Internet Information Services, développez  **\<**  *Nom_Ordinateur* \> (*ordinateur local*), développez **Web Sites**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **propriétés**.  
  
3.  Dans la boîte de dialogue Propriétés du Site Web par défaut sur le **sécurité du répertoire** , cliquez sur **certificat de serveur** pour démarrer le **Assistant certificat IIS**.  
  
4.  Sur le **Bienvenue dans l’Assistant certificat de serveur Web** , cliquez sur **suivant**.  
  
5.  Sur le **demande de certificat en attente** page, sélectionnez **traiter la demande en attente et installer le certificat**, puis cliquez sur **suivant**.  
  
6.  Sur le **traiter une demande en attente** page, dans le **chemin d’accès et nom de fichier** , tapez  **\<lecteur\>: \Certs\SSLCert.cer** (ou accédez à ce fichier) puis cliquez sur **suivant**.  
  
7.  Sur le **page Port SSL**, cliquez sur **suivant**.  
  
8.  Sur le **résumé du certificat** , cliquez sur **suivant**.  
  
9. Sur le **fin de l’Assistant certificat de serveur Web** , cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration de la solution Contoso](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)