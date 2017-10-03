---
title: "Pipeline de réception BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, receive pipelines
- RNMimeDecoder component
- ReceiveMessageNonRepudiate component
- RNDAsm component
- receive pipelines, message flow
- RNPartyRes component
- receive pipelines, BTARN
- MessageUpdater component
- messages, message flow
ms.assetid: 811f2a6a-ddd2-49cc-a00b-4c9d0110a0d1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80d7d5951b40b5c76b533e6425ee4d898b41c6cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btarn-receive-pipeline"></a>BTARN, pipeline de réception
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] effectue la réception des messages Framework RNIF (RosettaNet Implementation) avec le pipeline RNIFReceive (RNIFReceive.btp). Le pipeline de réception inclut les composants suivants :  
  
-   ReceiveMessageNonRepudiate  
  
-   RNMimeDecoder (préprocesseur/décodeur MIME)  
  
-   RNDAsm (désassembleur XML)  
  
-   RNPartyRes (composant Résolution du tiers)  
  
-   MessageUpdater  
  
## <a name="receivemessagenonrepudiate"></a>ReceiveMessageNonRepudiate  
 Ce composant stocke le message reçu dans la table MessageStorageIn. Ce composant effectue le traitement de non répudiation requis par les normes RNIF.  
  
## <a name="rnmimedecoder"></a>RNMimeDecoder  
 Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] préprocesseur/décodeur MIME. RNMimeDecoder ajoute les fonctionnalités suivantes pour le traitement RNIF :  
  
-   Pour RNIF 2.01, déchiffre le contenu de service et les pièces jointes, s’ils sont présents.  
  
-   Pour RNIF 1.1, gère l’en-tête de 8 octets et l’en-tête de signature détachée à la fin de la charge utile.  
  
 Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] préprocesseur/décodeur, consultez « Composant de Pipeline décodeur MIME/SMIME » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="rndasm"></a>RNDAsm  
 Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] désassembleur XML. RNDAsm ajoute les fonctionnalités suivantes pour le traitement RNIF :  
  
-   Si un document entrant comporte un en-tête de type de document, ce composant génère un espace de noms à partir de celui-ci et déplace tous les nœuds dans le document entrant pour cet espace de noms.  
  
-   Effectue la corrélation de message pour déterminer si un message entrant est un doublon et génère un message d’erreur si le message est un doublon.  
  
-   Stocke des pièces jointes en tant que parties supplémentaires du message.  
  
-   Promeut les propriétés de message.  
  
 Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] désassembleur, consultez « Composant de Pipeline désassembleur XML » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="rnpartyres"></a>RNPartyRes  
 Ce composant est basé sur natif [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] composant résolution du tiers. RNPartyRes ajoute les fonctionnalités suivantes pour le traitement RNIF :  
  
-   Mappe le certificat de l’expéditeur si le message entrant est signé à un tiers BizTalk. Si le message entrant n’est pas signé, et permet l’accord de partenariat commercial, ce composant extrait le tiers expéditeur à partir de l’en-tête de remise pour RNIF 2.01 ou l’en-tête de Service pour RNIF 1.1.  
  
-   Valide que l’expéditeur existe et que l’expéditeur a un accord de partenariat commercial avec l’organisation d’origine.  
  
 Pour plus d’informations sur natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] composant résolution de tiers, consultez « Composant de Pipeline résolution de tiers » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="messageupdater"></a>MessageUpdater  
 Ce composant ajoute les fonctionnalités suivantes pour le traitement RNIF :  
  
-   Met à jour la table MessageStorageIn avec des détails sur le Code PIP PIP Version, tiers Source, tiers de Destination et ID de suivi de Message du message qui a été enregistrée par le receivemessagenonrepudiate, composant câble.  
  
-   Si le PIP ne requiert pas la non répudiation, marque l’enregistrement pour la suppression, le paramètre `ToBePurged = True`.  
  
## <a name="message-flow"></a>Flux de messages  
 Le flux de messages via le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] réception pipeline est comme suit :  
  
1.  L’adaptateur HTTP reçoit un objet RNIF 1.1 ou un message d’entreprise RNIF 2.01 via HTTP POST.  
  
2.  Si l’adaptateur reçoit correctement le message, l’adaptateur extrait le message d’objet ou d’entreprise RosettaNet et l’achemine vers le pipeline de réception.  
  
3.  Si le message de l’objet ou business est signé, le préprocesseur/décodeur MIME supprime la signature.  
  
4.  Si la signature est valide, le désassembleur lit le préambule.  
  
5.  Si le message est un message d’action, et non répudiation est requise (le **non-répudiation de l’origine et du contenu** paramètre dans les paramètres de configuration de processus est `True`), le décodeur calcule et persiste le résumé.  
  
6.  Le désassembleur valide le préambule (avec les instructions du message (message) et le schéma de préambule dans les variables globales).  
  
7.  Pour RNIF 2.01, le désassembleur lit l’en-tête de remise et valide l’en-tête en utilisant les instructions du message et le schéma d’en-tête de remise dans les variables globales.  
  
8.  Pour RNIF 2.01, le désassembleur extrait les informations du partenaire à partir de l’en-tête de remise et examine la signature pour vérifier qu’il appartient au partenaire.  
  
9. Pour RNIF 2.01, si la charge utile est chiffrée, le décodeur déchiffre le conteneur de charge utile.  
  
10. Le désassembleur lit l’en-tête de service et valide l’en-tête en utilisant les instructions du message et le schéma d’en-tête de service dans les variables globales.  
  
11. Pour RNIF 1.1, le désassembleur extrait les informations du partenaire à partir de l’en-tête de service et examine la signature pour vérifier qu’il appartient au partenaire.  
  
12. Le désassembleur vérifie si le partenaire est autorisé pour le PIP. Si ce n’est pas le cas, le désassembleur de répondre à un HTTP POST avec un message d’état HTTP 403, si nécessaire et consigne une erreur.  
  
13. Si le message est un message d’action signé et **non-répudiation de l’origine et du contenu** a la valeur `True`, le receivemessagenonrepudiate, composant stocke le message d’origine dans la table MessageStorageIn.  
  
14. Si le message est un message de signal signé et **requis Non répudiation** a la valeur `True`, le receivemessagenonrepudiate, composant stocke le message de signal dans la table MessageStorageIn.  
  
15. Si le message a été conservé dans la table MessageStorageIn de non répudiation, la MessageUpdater met à jour la table MessageStorageIn avec les propriétés de la configuration de processus du message.  
  
16. Si le message est un message d’action qui est un doublon d’un message d’action traités précédemment, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] génère une erreur.  
  
17. Pour RNIF 2.01, le décodeur déchiffrera la charge utile si le message d’action est chiffré et il existe une correspondance entre le synchronisme HTTP et les exigences de synchronisme PIP.  
  
18. Le désassembleur lit le contenu de service et le valide utilisant les instructions du message et le schéma.  
  
19. Le désassembleur RNIF 2.01, vérifie que le manifeste est valide et que l’ID de contenu est présente.  
  
20. Pour RNIF 2.01, le désassembleur lit les pièces jointes.  
  
21. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine les en-têtes, le contenu de service et les pièces jointes dans le processus public RosettaNet.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)