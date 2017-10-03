---
title: Outil de MllpSend | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MllpSend tool
- MLLP-encoded messages, receive adapters
- MLLP-encoded messages, MllpSend tool
ms.assetid: b1723d52-4909-4543-8215-4f73802b6c4f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a15da306f61cb4297d9ba8cdc036035310474d8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllpsend-tool"></a>Outil de MllpSend
Vous pouvez utiliser l’outil MllpSend pour envoyer l’emplacement de réception de données à un MLLP.  
  
 Vous installez cet outil via le [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] procédure d’installation personnalisée. Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement. Sur l’écran d’installation personnalisée, sélectionnez **outil de Test MLLP** à partir de la **adaptateur** dossier, puis sélectionnez **Instances Test** à partir de la **artefacts** dossier. Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).  
  
 Le programme d’installation BTAHL7 installe cet outil dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\MLLP utilitaires.  
  
 Vous utilisez cet outil dans le [didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), le [didacticiel Interrogative](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), le [didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)et le [didacticiel enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). Si vous avez installé [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] via l’installation par défaut et vous n’avez pas installé le Testtools MLLP (y compris MllpSend et MllpReceive), vous ne serez pas en mesure de tester vos résultats du didacticiels.  
  
## <a name="tool-usage"></a>Utilisation de l’outil  
 Voici la syntaxe à qu'utiliser pour appeler cet outil de ligne de commande :  
  
```  
mllpsend.exe [/?] [/I <IP>] [/P <PORT>] [/TWOWAY] [/REPEAT <n>] [/F <FILENAME> | "TEXT"] /SB nn /EB nn /CR nn  
```  
  
 Le tableau suivant décrit chaque partie de la syntaxe de que l’outil MllpSend utilise.  
  
|Syntaxe| Description|  
|------------|-----------------|  
|**/?**|Affiche l’aide dans la fenêtre d’invite de commandes.|  
|**/I \<IP >**|Indique l’adresse de destination. La valeur par défaut est localhost.|  
|**/P \<PORT >**|Indique le numéro de port de destination. La valeur par défaut est **11000**.|  
|**/F**|Envoie le contenu du fichier du nom de fichier.|  
|**/ RÉPÉTITION\<n>**|Envoie le message même  *n*  fois. Les caractères de wrapper seront appliquées à chaque message.|  
|**/ TWOWAY (BIDIRECTIONNEL).**|L’expéditeur attend une réponse du récepteur. Service bus et EB doivent être spécifiés. CR est facultative. En mode de fichier, la réponse est stockée dans le fichier. RÉPONSE.|  
|**/ SB**|Définit la valeur ASCII de l’octet de délimiteur Démarrer de bloc. La valeur par défaut est none.|  
|**/EB**|Définit la valeur ASCII de l’octet de délimiteur de bloc de fin. La valeur par défaut est none.|  
|**/CR**|Définit la valeur ASCII de l’octet le délimiteur de retour chariot. La valeur par défaut est none.|  
  
## <a name="examples-of-tool-use"></a>Exemples d’utilisation de l’outil  
 Les exemples suivants montrent comment vous pouvez utiliser l’outil MllpSend.  
  
 **Exemple 1.** Vous pouvez utiliser la commande suivante pour envoyer un message à une carte à sens unique à l’écoute sur le port 13000 sur le serveur « myserver ». Les valeurs ASCII de caractères wrapper sont SB 11, EB 28 et CR 13.  
  
```  
mllpsend.exe /I myserver /P 13000 /SB 11 /EB 28 /CR 13 "A short message"  
```  
  
 **Exemple 2.** Vous pouvez utiliser la commande suivante pour envoyer un message de 100 fois à une carte bidirectionnelle à l’écoute sur le port 11000 sur le serveur « localhost ». Les valeurs ASCII de caractères wrapper sont SB 11, EB 28 et CR 13.  
  
```  
mllpsend.exe /SB 11 /EB 28 /CR 13 /TWOWAY /REPEAT 100 "A short message"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)