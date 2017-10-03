---
title: Outil de MllpReceive | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- MllpReceive tool
- MLLP-encoded messages, MllpReceive tool
ms.assetid: 7069444b-1412-40bf-b567-fa86f76cd007
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c23aac352b47a328cfc8f412bb3beca50a61e1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllpreceive-tool"></a>Outil de MllpReceive
Vous pouvez utiliser l’outil MllpReceive pour recevoir des données à partir d’un port d’envoi MLLP.  
  
 Vous installez cet outil via le [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] procédure d’installation personnalisée. Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement. Sur l’écran d’installation personnalisée, sélectionnez **outil de Test MLLP** à partir de la **adaptateur** dossier, puis sélectionnez **Instances Test** à partir de la **artefacts** dossier. Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).  
  
 Le programme d’installation BTAHL7 installe cet outil dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\MLLP utilitaires.  
  
 Vous utilisez cet outil dans le [didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), le [didacticiel Interrogative](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), le [didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)et le [didacticiel enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). Si vous avez installé [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] via l’installation par défaut et vous n’avez pas installé l’outil MLLPTest (y compris MllpReceive et MllpSend), vous ne serez pas en mesure de tester vos résultats du didacticiels.  
  
## <a name="tool-usage"></a>Utilisation de l’outil  
 Voici la syntaxe à qu'utiliser pour appeler cet outil de ligne de commande :  
  
```  
mllpreceive.exe [/?] [/I <IP>] [/P <PORT>] [/SPLIT] [/D <DIRECTORY>] [/STATICACK "ACKTEXT" | /HL7ACK <FILENAME>] /SB nn /EB nn /CR nn  
```  
  
 Le tableau suivant décrit chaque partie de la syntaxe de que l’outil MllpReceive utilise.  
  
|Syntaxe|Signification|  
|------------|-------------|  
|/?|Affiche cette aide.|  
|/I \<IP >|Indique l’adresse de manière à écouter. La valeur par défaut est disponible de toutes les adresses IP.|  
|/P \<PORT >|Indique le numéro de port pour écouter. La valeur par défaut est 12000.|  
|/D \<RÉPERTOIRE >|Stocke le reçu tous les messages dans le répertoire \<DIRECTORY >. Si vous ne spécifiez pas \<DIRECTORY >, le répertoire par défaut est % Temp%.|  
|/ FRACTIONNEMENT|Fractionne les données reçues en messages distincts selon les délimiteurs. Service bus et EB sont requis. CR est facultative.|  
|/ STATICACK|L’accusé de réception statique renvoyé à l’expéditeur. Mode fractionné appliquera.|  
|/ HL7ACK|L’accusé de réception HL7 renvoyé à l’expéditeur. Nom de fichier indique le nom du fichier contenant les accusés de réception HL7. Mode fractionné appliquera.|  
|/ SB|Définit la valeur ASCII de démarrer un octet de séparateur de bloc. La valeur par défaut est none.|  
|/EB|Définit la valeur ASCII d’octet de délimiteur de bloc de fin. La valeur par défaut est none.|  
|/CR|Définit la valeur ASCII d’octet de séparateur retour chariot. La valeur par défaut est none.|  
  
## <a name="example-of-tool-use"></a>Exemple d’utilisation de l’outil  
 Vous pouvez utiliser la commande suivante pour écouter le port 10000 sur localhost et enregistrer des messages pour séparer les fichiers dans C:\TEMP :  
  
```  
mllpreceive.exe /P 10000 /SPLIT /SB 11 /EB 28 /CR 13 /D C:\TEMP  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)