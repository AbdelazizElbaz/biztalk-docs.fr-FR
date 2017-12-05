---
title: "Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, testing solution
ms.assetid: 233fbf79-0ab1-4064-b828-6bbbb56cbec2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035925684617e74608246aed99fa98e16d0668a4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-18-test-your-new-message-enrichment-solution"></a>Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message
Dans cette étape, vous testez votre solution à l’aide de l’application WSClient pour envoyer un message à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et de voir si l’application MLLPReceive reçoit un message au format HL7 comme prévu.  
  
### <a name="to-test-your-solution"></a>Pour tester votre solution  
  
1.  Ouvrez une invite de commandes.  
  
    > [!NOTE]
    >  Étape 2 nécessite que vous avez installé l’outil de Test de MLLP à l’aide de la procédure d’installation personnalisée. Si les utilitaires \MLLP répertoire contenant MllpReceive.exe et MllpSend.exe n’existe pas sur votre ordinateur, installez-les en effectuant une installation personnalisée. Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).  
  
2.  À l’invite de commandes, tapez  **cd \<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator HL7\SDK\MLLP utilitaires * * (où \< *lecteur* \> est la lettre de lecteur de votre installation), puis appuyez sur **entrée**.  
  
3.  À l’invite de commandes, tapez **mllpreceive /p 11000 /eb 11/SB 28 /cr 13**, puis appuyez sur **entrée**. Cela exécute l’application d’écouteur MLLP à l’écoute sur le port 11000 et en spécifiant les caractères EB, service bus et CR par défaut du message MLLP et affiche tous les messages reçus à l’écran.  
  
4.  Ouvrez une deuxième invite de commandes.  
  
5.  À l’invite de commandes, tapez  **cd \<* lecteur*\>: \Tutorial\WSClient\bin\Debug**, puis appuyez sur **entrée**.  
  
6.  À l’invite de commandes, tapez **wsclient Jean henry 123456789**, puis appuyez sur **entrée**. Il envoie un message au service Web qui contient un exemple de message avec un nom de patient de Henry de John Smith et un numéro de sécurité sociale exemple 123456789.  
  
7.  Après un court instant, l’application MLLPReceive affiche le message entrant MLLP. Le message doit ressembler à ce qui suit :  
  
    ```  
    MSH|^~\&|TestTrailing^Delimiters|srcFac^srcFacUid|dstApp^dstAppUid|dstFac^dstFacUid|200307092343|sec|ADT^A04|msgid2134|P|2.2PID|||123456789||smith^john  
    ```  
  
     Si vous ne recevez pas de réponse après quelques minutes, vérifiez le journal des événements pour les erreurs et commencez le dépannage.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)