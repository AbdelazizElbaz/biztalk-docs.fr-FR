---
title: 'Étape 10 : Vérifier que le scénario de bout en bout | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, verifying solution
ms.assetid: 24b74ba6-e303-4ab1-8a93-25a430e4894d
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d38f137625554bd689477964e3a969142eca0658
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-10-verify-the-end-to-end-scenario"></a>Étape 10 : Vérifier que le scénario de bout en bout
Dans cette étape, vous vérifiez le scénario de bout en bout pour ce didacticiel.  
  
### <a name="to-verify-the-end-to-end-tutorial-scenario"></a>Pour vérifier le scénario de didacticiel de bout en bout  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.  
  
2.  Dans la fenêtre d’invite de commandes, accédez à  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP utilitaires**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Si vous ne trouvez pas un dossier MLLP utilitaires sous le dossier du Kit de développement logiciel, les outils de test MLLP ne peuvent pas être installés. Ouvrez le panneau de configuration, puis ouvrez **Ajout / Suppression de programmes**. Sélectionnez **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis sélectionnez **modification**. Dans l’Assistant d’installation BTAHL7, sélectionnez **modifier**. Développez le **carte** dossier pour voir si le **outil de Test MLLP** a été installé. Si ce n’est pas le cas, installez-le.  
  
3.  Dans la fenêtre d’invite de commandes, tapez **mllpreceive /p 14000**, puis appuyez sur **entrée**. Cela exécute l’application d’écouteur MLLP écouter le port 14000 et en spécifiant les caractères EB, service bus et CR par défaut du message MLLP et affiche tous les messages reçus à l’écran.  
  
4.  Démarrez une invite de commandes supplémentaire en cliquant sur **Démarrer**, pointez sur **programmes**, pointez sur **Accessoires**, puis cliquez sur **l’invite de commandes**.  
  
5.  Dans la deuxième fenêtre d’invite de commandes, accédez à  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP utilitaires**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  L’étape suivante envoie le message.  
  
6.  Dans la fenêtre d’invite de commandes, tapez **mllpsend/SB 11 /EB 28 /CR 13 /f «\<*lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Tutorial\ADT de bout en bout ^ A03.txt «**, où \< *lecteur* \> est la lettre de lecteur de votre installation. Appuyez sur **Entrée**.  
  
7.  Vérifiez que vous disposez les résultats suivants :  
  
    -   L’application du récepteur MLLP doit afficher un message. La première ligne du message doit avoir les valeurs suivantes :  
  
        ```  
        MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
        ```  
  
    -   Un message s’affiche dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendMsg_RX. Ce message doit être le même que le message affiché par l’application d’écouteur MLLP. Vérifiez que la première ligne du message a les mêmes valeurs de message comme suit. Notez que les valeurs pour MSH3 un nd MSH5 dans le code suivant correspondent les valeurs que vous avez spécifié pour le Tutorial_RXSystem :  
  
        ```  
        MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
        ```  
  
    -   Deux messages s’affichent dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendAck_ADT. Un de ces messages est un accusé de réception application ; l’autre est un accusé de réception de la validation. L’accusé de réception d’application doit avoir le contenu suivant :  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
        MSA|AA|000001  
        ```  
  
    -   L’accusé de réception de validation doit avoir le contenu suivant :  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
        MSA|CA|000001  
        ```  
  
    > [!NOTE]
    >  Si les messages ne s’affichent pas correctement, utilisez l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT) pour résoudre l’erreur.  
  
 Félicitations ! Vous avez terminé le didacticiel de bout en bout BTAHL7.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)