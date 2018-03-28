---
title: 'Étape 10 : Vérifier que le scénario Interrogative | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, verifying solution
ms.assetid: 1f28800b-4a1d-4f29-8123-5cdea4b4a365
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b932ab2f179faab1381609c007dcdd148f200f7e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-10-verify-the-interrogative-scenario"></a>Étape 10 : Vérifier que le scénario Interrogative
Dans cette étape, vous vérifiez le scénario de bout en bout pour ce didacticiel.  
  
### <a name="to-send-the-query-message"></a>Pour envoyer le message de requête  
  
1.  Ouvrez une invite de commandes.  
  
2.  Dans l’invite de commandes, accédez à  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP utilitaires**.  
  
3.  Dans l’invite de commandes, tapez **MllpReceive /P 24000**, puis appuyez sur **entrée**. Cela exécute l’application d’écouteur MLLP écouter le port 24000 et affiche tous les messages reçus à l’écran. Cette application simule un système d’informations.  
  
4.  Ouvrez une invite de commandes supplémentaire.  
  
5.  Dans la deuxième fenêtre d’invite de commandes, accédez à  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP utilitaires**.  
  
6.  Dans la seconde invite de commandes, tapez **MllpSend/SB 11 /EB 28 /CR 13/TwoWay (bidirectionnel) /P 22000 /F «\<*lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator pour HL7\SDK\Interrogative Tutorial\QRY^Q01.txt**, puis appuyez sur **entrée.**  
  
    > [!NOTE]
    >  Cette commande envoie le message de requête que vous avez créé au début de ce didacticiel pour le port MLLP 22000 et attend une réponse (accusé de réception). Le ADT récupère ce message port de réception et le traite.  
  
7.  Vérifiez que vous disposez les résultats suivants :  
  
    -   L’application du récepteur MLLP doit afficher un message avec les valeurs suivantes :  
  
        ```  
        MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        ```  
  
    -   En outre, l’utilitaire MllpSend crée un fichier de l’accusé de réception dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Dossier Tutorial interrogative nommé QRY^Q01.txt.RESPONSE. Ce fichier contient les informations suivantes en tant que l’accusé de réception :  
  
        ```  
        MSH|^~\&|HIS||ADT||20040331154031.2222-0800||ACK^Q01^ACK|10000GSM|P|2.4  
        MSA|CA|MSG00001  
        ****END ACK****  
        ```  
  
### <a name="to-send-the-response-message"></a>Pour envoyer le message de réponse  
  
1.  Dans l’invite de commandes qui exécute l’application MllpReceive, appuyez sur **Ctrl-C** pour annuler l’opération précédente.  
  
2.  À l’invite de commandes, tapez **MllpReceive /P 25000**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Étape 2 s’exécute l’application du récepteur MLLP écouter le port 25000 et affiche tous les messages reçus à l’écran. Cette application simule le système ADT.  
  
3.  Dans la seconde invite de commandes, tapez **MllpSend/SB 11 /EB 28 /CR 13 /P 23000 /F «\<*lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial\DSR.txt »**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Étape 3 envoie le message de réponse que vous avez créé au début de ce didacticiel pour le port MLLP 23000. LE port récupère ce message de réception et le traite.  
  
4.  Vérifiez que vous disposez les résultats suivants :  
  
    -   L’application du récepteur MLLP doit afficher un message avec les valeurs suivantes :  
  
        ```  
        MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
        MSA|AA|MSG00003  
        QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
        DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
        DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
        DSP|||ELECTROLYTES  
        DSP||| SODIUM 136 [135-148] MEQ/L STAT  
        DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
        DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
        DSP||| CO2 25 [20-30] MEQ/L STAT  
        DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
        ```  
  
    > [!NOTE]
    >  Si les messages ci-dessus ne s’affichent pas correctement, utilisez l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT) pour résoudre l’erreur.  
  
 Félicitations ! Vous avez terminé le didacticiel Interrogative BTAHL7.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [Didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)   
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)