---
title: BtarnConfig | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, exporting configuration data
- BTARN, BtarnConfig utility
- BtarnConfig utility
- BTARN, importing configuration data
ms.assetid: 8c95be2a-7df5-47fb-ae2d-64fa27e2811a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78ab62a86e97bf70e07629052a850b5aea2cee27
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="btarnconfig"></a>BtarnConfig
Vous utilisez l’utilitaire BtarnConfig pour importer des données de configuration dans, ou exporter des données de configuration à partir, un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] environnement. Ces données de configuration sont les données que vous définissez à l’aide de la Console de gestion BTARN, y compris les paramètres de configuration de processus, des organisations de base, des partenaires et des accords.  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*\>\ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK  
  
## <a name="running-btarnconfig"></a>BtarnConfig en cours d’exécution  
  
#### <a name="to-run-btarnconfig"></a>Pour exécuter BtarnConfig  
  
1.  Ouvrez une invite de commandes.  
  
2.  Déplacer vers \< *lecteur*\>\ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
3.  À l’invite de commandes, tapez **BtarnConfig**, tapez les commutateurs appropriés, puis appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  La section suivante décrit les commutateurs.  
  
## <a name="syntax-for-btarnconfig"></a>Syntaxe de BtarnConfig  
 Voici la syntaxe que vous utilisez pour démarrer cet outil de ligne de commande :  
  
### <a name="syntax-for-importing-configuration-data"></a>Syntaxe pour l’importation de données de Configuration  
  
```  
BTARNCONFIG /IMPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-for-exporting-configuration-data"></a>Syntaxe pour l’exportation des données de Configuration  
  
```  
BTARNCONFIG /EXPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-description"></a>Description de la syntaxe  
 Le tableau suivant décrit chaque partie de la syntaxe utilisée par l’utilitaire BtarnConfig.  
  
|Syntaxe| Description|  
|------------|-----------------|  
|\<*nom de fichier*.xml\>|Chemin d’accès complet du fichier à importer ou exporter à partir de. Si vous ne fournissez pas un chemin d’accès, BTARN suppose que le chemin d’accès est \< *lecteur*\>\ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour RosettaNet \SDK.|  
|**/ IMPORTATION**|Importe les données XML à partir de \< *nom de fichier*.xml\> dans la configuration de BTARN.|  
|**/ EXPORT**|Exporte la configuration de BTARN en tant que données XML dans \< *nom de fichier*.xml\>.|  
|**/H**|Importe ou exporte les données de configuration de l’organisation d’origine.|  
|**/P**|Importe ou exporte les données de configuration de serveur partenaire.|  
|**/R**|Importe ou exporte les données de configuration de processus.|  
|**/A**|Importe ou exporte les données de configuration d’accord.|  
  
## <a name="remarks"></a>Notes  
 Si vous ne fournissez pas l’un de le **/H**, **/P**, **/R**, ou **/A** bascule, la BtarnConfig utilitaire importe ou exporte toutes les données. Lorsque vous exportez toutes les données en une seule opération, BtarnConfig exporte les données dans le fichier XML dans l’ordre suivant : accueil organisations, partenaires, la configuration du processus et des accords.  
  
 S’il existe un problème de structure avec le fichier que vous importez à partir de, BTARN va détecter l’erreur lors de l’étape de validation de schéma, et l’opération échoue avant l’importation de toutes les données. Si une autre erreur se produit, par exemple, vous essayez d’importer un artefact en double ou HTTPS est requis pour le PIP/de contrat, puis l’opération d’importation échoue. Toutefois, toutes les données importées jusqu'à seront conservés dans la configuration.  
  
 Vous devez être un administrateur BizTalk pour importer ou exporter des données de configuration à l’aide de BtarnConfig. Si vous n’êtes pas un administrateur BizTalk, certaines opérations d’importation peuvent échouer en raison de problèmes d’accès. Toutefois, les autres opérations d’importation dans la même commande BtarnConfig peuvent réussir.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)