---
title: Assistant utilitaire de certificat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff72810-c7b3-4f67-8f9f-e127eacc153e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3acbb1198034e76bb1e0f45c0f9755ec6ac95d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-wizard-utility"></a>Utilitaire de l'Assistant Certificat
L'utilitaire CertWizard permet d'importer un certificat d'un fichier .pfx ou .cer dans un magasin privé ou public pour l'utiliser avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Vous trouverez le code source pour l’Assistant de certificat dans le **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Utilities\Certificate Assistant** dossier. Avec un système d’exploitation 64 bits et une version de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], doivent être dans le **(x86) de C:\Program Files \Microsoft BizTalk Server \<version > \SDK\Utilities\Certificate Assistant** dossier. Pour utiliser l'Assistant Certificat, vous devez commencer par le créer à l'aide de [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
 L'utilitaire CertWizard importe une clé privée d'un fichier .pfx dans le magasin personnel, et importe une clé publique d'un fichier .cer dans un magasin public. Lors de l'importation d'une clé privée, le certificat peut être un certificat de déchiffrement pour les messages entrants, ou un certificat de signature pour les messages sortants.  
  
 **Description de la syntaxe**  
  
 Le tableau suivant décrit les éléments de la syntaxe utilisée par l'utilitaire CertWizard.  
  
|||  
|-|-|  
|Syntaxe| Description|  
|Privatekey|Utilisée pour importer une clé privée.|  
|Publickey|Utilisée pour importer une clé publique.|  
|Rootkey|Utilisée pour importer une clé racine (d’une autorité de certification).|  
|nom_fichier.pfx (ou .cer)|Chemin d'accès complet du fichier .pfx (clés privées) ou .cer (clés publiques).|  
|Filepassword|Mot de passe requis pour déverrouiller le fichier .pfx.|  
|Useridentity|Identité de service utilisée par un ou plusieurs hôtes BizTalk. Entrez un compte d'utilisateur si vous ne souhaitez pas spécifier l'hôte mais importer un certificat sous un compte d'utilisateur. **Remarque :** si vous n’ajoutez pas le commutateur Useridentity, l’utilitaire importe et définir le certificat pour tous les utilisateurs. **Remarque :** si vous ajoutez le commutateur Useridentity, mais que vous n’entrez pas de valeur, WMI génère automatiquement l’identité de l’utilisateur.|  
|Mot de passe|Mot de passe de l'utilisateur de l'identité du service.|  
|Thumbprint|Empreinte d'un certificat spécifique, au cas où le fichier contient plusieurs certificats. **Remarque :** pour un fichier de certificat public, si le fichier contient plusieurs certificats et que vous ne spécifiez pas l’empreinte numérique, l’utilitaire importe tous les certificats dans le fichier. Dans le cas d'un fichier de certificat privé, l'utilitaire vous invite à sélectionner le certificat à importer.|  
|Utilisation|Utilisation prévue du certificat privé importé. Les valeurs possibles sont les suivantes :<br /><br /> **signe** (pour un certificat de signature)<br /><br /> **déchiffrer** (pour un certificat de déchiffrement)<br /><br /> **les deux** (pour un certificat est un certificat de signature et un certificat de déchiffrement)<br /><br /> **aucun** (également pour un certificat qui est un certificat de signature et un certificat de déchiffrement). **Remarque :** si vous définissez le commutateur /Usage sur None, l’Assistant ne définit pas l’empreinte numérique du certificat sur les hôtes BizTalk ou le groupe BizTalk.|  
|Exportable|Peut être **True** ou **False**. Si **True**, la clé privée peut être de nouveau exportée.|  
  
 **Syntaxe pour l’importation d’une clé privée**  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
 **Syntaxe pour l’importation d’une clé publique**  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
 **Syntaxe pour l’importation d’une clé racine**  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-run-the-certificate-wizard"></a>Pour exécuter l'Assistant Certificat  
  
1.  Ouvrez une invite de commandes.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities.  
  
3.  À l’invite de commandes, tapez **CertWizard**, tapez les interrupteurs requis, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Si vous n'entrez pas l'intégralité de la commande dans l'invite, CertWizard vous invite à fournir les valeurs requises.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires dans le Kit de développement](../core/utilities-in-the-sdk.md)