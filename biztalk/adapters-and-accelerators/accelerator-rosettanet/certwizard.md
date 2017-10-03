---
title: CertWizard | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, CertWizard utility
- CertWizard utility
- certificates, importing
ms.assetid: beeab3c0-d7b1-4bb9-8b19-f79b049d5aa1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8d9daf4ea1ea996680088c7a7a1333e9d26906b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certwizard"></a>CertWizard
L’utilitaire CertWizard permet d’importer un certificat à partir d’un fichier .pfx ou .cer dans un magasin privé ou public pour une utilisation avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*> \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\  
  
## <a name="running-certwizard"></a>CertWizard en cours d’exécution  
  
#### <a name="to-run-certwizard"></a>Pour exécuter CertWizard  
  
1.  Ouvrez une invite de commandes.  
  
2.  Déplacer vers \< *lecteur*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\\.  
  
3.  À l’invite de commandes, tapez **CertWizard**, tapez les interrupteurs requis, puis appuyez sur ENTRÉE.  
  
## <a name="syntax-for-certwizard"></a>Syntaxe de CertWizard  
 Voici la syntaxe que vous utilisez pour démarrer cet utilitaire de ligne de commande :  
  
### <a name="syntax-for-importing-a-private-key"></a>Syntaxe pour l'importation d'une clé privée  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
### <a name="syntax-for-importing-a-public-key"></a>Syntaxe pour l'importation d'une clé publique  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-for-importing-a-root-key"></a>Syntaxe pour l'importation d'une clé racine  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-description"></a>Description de la syntaxe  
 Le tableau suivant décrit les éléments de la syntaxe utilisée par l'utilitaire CertWizard.  
  
|**Syntaxe**|**Description**|  
|----------------|---------------------|  
|**PrivateKey**|Utilisée pour importer une clé privée.|  
|**Clé publique**|Utilisée pour importer une clé publique.|  
|**Cle_principale**|Utilisée pour importer une clé racine (d’une autorité de certification).|  
|**nom_fichier.pfx (ou .cer)**|Chemin d'accès complet du fichier .pfx (clés privées) ou .cer (clés publiques).|  
|**Filepassword**|Mot de passe requis pour déverrouiller le fichier .pfx.|  
|**Identité de l’utilisateur**|Identité de service utilisée par un ou plusieurs hôtes BizTalk. Entrez un compte d'utilisateur si vous ne souhaitez pas spécifier l'hôte mais importer un certificat sous un compte d'utilisateur. **Remarque :** si vous n’ajoutez pas le **Useridentity** basculer, les importations d’utilitaire et de définir le certificat pour tous les utilisateurs. **Remarque :** si vous ajoutez le **Useridentity** commutateur, mais n’entrez pas de valeur, WMI génère automatiquement l’identité de l’utilisateur.|  
|**Mot de passe**|Mot de passe de l'utilisateur de l'identité du service.|  
|**Empreinte numérique**|Empreinte d'un certificat spécifique, au cas où le fichier contient plusieurs certificats. **Remarque :** pour un fichier de certificat public, si le fichier contient plusieurs certificats et que vous ne spécifiez pas l’empreinte numérique, l’utilitaire importe tous les certificats dans le fichier. Dans le cas d'un fichier de certificat privé, l'utilitaire vous invite à sélectionner le certificat à importer.|  
|**Utilisation**|Utilisation prévue du certificat privé importé. Peut être l’authentification (pour un certificat de signature), déchiffrer (pour un certificat de déchiffrement), à la fois (pour un certificat est un certificat de signature et un certificat de déchiffrement) ou none (également pour un certificat est un certificat de signature et un certificat de déchiffrement ). **Remarque :** si vous définissez la **/Usage** commutateur None, l’Assistant ne définit pas de l’empreinte numérique du certificat sur les hôtes BizTalk ou le groupe BizTalk.|  
|**Exportable**|Peut être `True` ou `False`. Si `True`, la clé privée peut être de nouveau exportée.|  
  
## <a name="remarks"></a>Notes  
 L'utilitaire CertWizard importe une clé privée d'un fichier .pfx dans le magasin personnel, et importe une clé publique d'un fichier .cer dans un magasin public. Lors de l'importation d'une clé privée, le certificat peut être un certificat de déchiffrement pour les messages entrants, ou un certificat de signature pour les messages sortants.  
  
 Si vous n'entrez pas l'intégralité de la commande dans l'invite, CertWizard vous invite à fournir les valeurs requises.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [L’importation de certificats à l’aide de l’utilitaire CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)