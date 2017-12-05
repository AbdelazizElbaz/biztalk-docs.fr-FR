---
title: "Remplacez l’utilitaire de jeton de clé publique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Replace Public Key Token Utility
- utilities, Replace Public Key Token Utility
- public key token
ms.assetid: ed8673b9-af06-4bd7-b8b7-7371e4dd0fed
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 344b25b83060143b339a6791ecae6f3ab7028055
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="replace-public-key-token-utility"></a>Utilitaire de remplacement d'un jeton de clé publique
Cet utilitaire permet de remplacer un jeton de clé publique ou une variable d'un fichier par un jeton de clé publique dérivé d'un fichier de clé d'assembly de nom fort (.snk).  
  
 Cet utilitaire peut être utile lorsqu’un développeur écrit un script qui utilise le [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md) pour déployer un assembly. Pour que le déploiement réussisse, le nom de l'assembly doit être complet et donc inclure son jeton de clé publique. Le jeton de clé publique d'un assembly est extrait d'un fichier .snk et affecté à l'assembly lors de sa création. Avant que l'assembly soit déployé dans un nouvel environnement, cependant, il est souvent recréé à l'aide d'un jeton de clé publique différent. Par conséquent, le développeur peut ne pas connaître le jeton de clé publique utilisé pour l'assembly au moment de l'exécution du script de déploiement.  
  
 Il existe deux façons d'utiliser l'utilitaire de remplacement d'un jeton de clé publique pour résoudre ce problème :  
  
-   **Scénario 1.** Dans le script de déploiement, le développeur peut utiliser un jeton de clé publique ou un espace réservé représentant le jeton de clé publique. Avant d'exécuter le script, l'utilisateur peut exécuter l'utilitaire de remplacement d'un jeton de clé publique pour remplacer le jeton de clé publique ou l'espace réservé du fichier de script par le jeton de clé publique extrait du fichier .snk utilisé pour créer l'assembly de l'environnement de destination.  
  
-   **Scénario 2.** Le développeur peut configurer le script pour qu’il remplace automatiquement le jeton de clé publique, comme suit : au début du script, appelez l’utilitaire de jeton de clé publique qu’elle pointe vers un fichier .snk qui contient le jeton de clé publique. Dans le script, utilisez la variable d'environnement %NEWTOKEN% pour représenter le jeton de clé publique. Pendant l'exécution du script, l'utilitaire extrait la valeur du jeton de clé publique du fichier .snk et la définit dans une variable d'environnement %NEWTOKEN%. Chaque instance de la variable %NEWTOKEN% est alors remplacée par le jeton de clé publique du fichier .snk spécifié. Exemple :  
  
    ```  
    ReplacePKT.bat key.snk  
    ...  
    ...  
    gacutil /u Assembly, ... PublicKey=%NEWTOKEN% ...  
    ```  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 L'utilitaire de remplacement d'un jeton de clé publique se trouve dans :  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\ReplacePublicKeyToken\\.  
  
 Il se compose de trois fichiers :  
  
-   ReplacePKT.bat  
  
-   ReplacePKT.vbs  
  
-   ReplacePKT.wsf  
  
## <a name="procedures"></a>Procédures  
 Procédez comme indiqué ci-dessous pour remplacer toutes les instances d'un jeton de clé publique ou d'un espace réservé d'un fichier par un jeton de clé publique extrait d'un fichier .snk (scénario 1).  
  
#### <a name="to-replace-instances-of-a-public-key-token-or-a-placeholder-in-a-file"></a>Pour remplacer toutes les instances d'un jeton de clé publique ou d'un espace réservé d'un fichier  
  
1.  Assurez-vous que les trois fichiers de l'utilitaire de remplacement d'un jeton de clé publique (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf), le fichier de script et le fichier .snk sont tous présents sur l'ordinateur local.  
  
2.  Dans une fenêtre de commande, remplacez le répertoire par le dossier contenant les fichiers de l'utilitaire de remplacement d'un jeton de clé publique.  
  
3.  À partir d'une invite de commande, tapez la commande suivante :  
  
4.  **ReplacePKT \<**  *fichier .snk*  **\> \<**  *ancien jeton de clé publique*  **\> \<**  *fichier à remplacer***\>**  
  
    |Option| Description|  
    |------------|-----------------|  
    |**\<***fichier .snk***\>**|Chemin d'accès complet du fichier .snk contenant le jeton de clé publique que vous voulez substituer au jeton ou à l'espace réservé existant.|  
    |**\<***ancien jeton de clé publique***\>**|Jeton de clé publique ou espace réservé à remplacer.|  
    |**\<***fichier à remplacer***\>**|Chemin d'accès complet du fichier dans lequel vous voulez remplacer le jeton de clé publique ou l'espace réservé.|  
  
     Exemple :  
  
     **ReplacePKT.bat C:\Tokens\MyToken.snk 12ab3456cd789e12 C:\Scripts\MyScript.vbs**  
  
 Procédez comme indiqué ci-dessous pour définir automatiquement une variable d'environnement de script utilisant un jeton de clé publique dérivé d'un fichier .snk (scénario 2).  
  
#### <a name="to-set-an-environment-variable-that-uses-a-public-key-token"></a>Pour définir une variable d'environnement utilisant un jeton de clé publique  
  
1.  Au début du fichier de script, ajoutez la ligne de code suivante :  
  
    ```  
    ReplacePKT <filename>.snk  
    ```  
  
     Où \< *nom de fichier* \> est le nom du fichier .snk à partir de laquelle dériver le jeton de clé publique.  
  
    ```  
    Example: ReplacePKT.bat MyToken.snk  
    ```  
  
2.  Dans le fichier de script, utilisez `%NEWTOKEN%` pour représenter le jeton de clé publique.  
  
     Exemple :  
  
    ```  
    PublicKey=%NEWTOKEN%  
    ```  
  
3.  Lorsque vous fournissez le fichier de script aux utilisateurs, incluez les trois fichiers composant l'utilitaire de remplacement d'un jeton de clé publique (ReplacePKT.bat, ReplacePKT.vbs, ReplacePKT.wsf). Veillez à ce que ces utilisateurs copient tous les fichiers dans un même dossier du système avant d'exécuter le script.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires du SDK](../core/utilities-in-the-sdk.md)