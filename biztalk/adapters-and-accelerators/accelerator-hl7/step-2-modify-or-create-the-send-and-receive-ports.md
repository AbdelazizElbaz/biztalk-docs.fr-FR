---
title: "Étape 2 : Modifier ou créer l’envoi et Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61f201f8b20d5824b1b037cc61edaa1d64729135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-modify-or-create-the-send-and-receive-ports"></a>Étape 2 : Modifier ou créer l’envoi et Ports de réception
Vous avez besoin d’envoi de fichiers et les ports de réception pour le lot dans / Out didacticiel du lot. Si vous avez cliqué sur le **lancer le didacticiel** bouton à la fin de l’installation de l’édition Enterprise de [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] créé ces ports : un port d’envoi nommé Tutorial_BTAHL7Drop et un port de réception nommé Tutorial_BTAHL7PickUp. Si vous disposez de ces ports, vous devez modifier le port d’envoi Tutorial_BTAHL7Drop.  
  
 Si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation ne pas créer de l’envoi et ports de réception pour vous, consultez « Pour créer le BIBOTutorialPickup port de réception » la procédure dans cette rubrique et puis consultez « Pour créer le BIBOTutorialDrop port d’envoi » la procédure dans cette rubrique.  
  
### <a name="to-modify-the-tutorialbtahl7drop-send-port"></a>Pour modifier le port d’envoi Tutorial_BTAHL7Drop  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.  
  
3.  Cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **propriétés**.  
  
4.  Dans l’arborescence de la console, cliquez sur **filtres**.  
  
5.  Dans le **filtres** volet, dans la deuxième ligne, sélectionnez **BTAHL7Schemas.MessageClass** pour **propriétés**, sélectionnez  **==**  pour **Opérateur**et le type **MessageClass2X** pour **valeur**. Cliquez sur **Entrée**.  
  
6.  Définissez **regrouper par** sur la **BTS. ReceivePortName** à la ligne **ou**, puis cliquez sur **OK**.  
  
7.  Dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fenêtre Administration, développez **paramètres de plateforme**, développez **Instances d’hôte**. Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.  
  
    > [!NOTE]
    >  Utilisez uniquement les procédures suivantes si vous avez installé l’Édition Standard de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], ou si vous n’avez pas cliqué sur le **lancer le didacticiel** bouton lorsque vous configurez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].  
  
### <a name="to-create-the-tutorialbtahl7pickup-receive-port-and-location"></a>Pour créer le Tutorial_BTAHL7Pickup port de réception et emplacement  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la Console d’Administration, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez  **BizTalk Application 1**.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
4.  Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **Tutorial_BTAHL7PickUp**.  
  
5.  Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.  
  
6.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
7.  Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **Tutorial_BTAHL7PickUp**, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **Tutorial_FileReceiveLoc**.  
  
9. Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.  
  
10. Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
11. Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Accédez à  **\<**  *lecteur***> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7PickUp** . **Remarque :** il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] prennent en charge le fichier.|  
    |**Masque de fichier**|Type  **\*.txt**.|  
  
12. Cliquez sur **OK**.  
  
13. Dans la boîte de dialogue Propriétés de l’emplacement de réception, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Gestionnaire de réception**|Conserver **BizTalkServerApplication** comme étant sélectionnée.|  
    |**Pipeline de réception**|Sélectionnez **BTAHL72XPipelines.BTAHL72XReceivePipeline**.|  
  
14. Cliquez sur **OK**.  
  
15. Dans l’Explorateur BizTalk, cliquez sur **Tutorial_FileReceiveLoc**, puis cliquez sur **activer**.  
  
### <a name="to-create-the-tutorialbtahl7drop-send-port"></a>Pour créer le port d’envoi Tutorial_BTAHL7Drop  
  
1.  Dans le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_BTAHL7Drop**.|  
    |**Type**|Sélectionnez **fichier** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir le **propriétés du Transport FILE** boîte de dialogue.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Accédez à  **\<**  *lecteur***: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7Drop** . **Remarque :** le chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier.|  
    |**Nom de fichier**|Type **%MessageID%.txt** (Notez que l’extension est txt, xml pas).|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline** dans la liste déroulante.  
  
6.  Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. ReceivePortName** dans la liste déroulante.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Valeur**|Type **Tutorial_BTAHL7PickUp**.|  
    |**Regrouper par**|Sélectionnez **ou** dans la liste déroulante.|  
    |**Propriété**|Sélectionnez **BTAHL7Schemas.MessageClass**.|  
    |**Opérateur**|Laissez  **==**  comme l’opérateur.|  
    |**Valeur**|Type **MessageClass2X**.|  
  
7.  Cliquez sur **Entrée**. Dans le volet du bas de la boîte de dialogue, vérifiez que l’expression de filtre est correcte.  
  
8.  Cliquez sur **OK**.  
  
9. Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_BTAHL7Drop**, puis cliquez sur **Démarrer**.  
  
10. Développez **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**. Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.  
  
 Passez à [étape 3 : tester le lot dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md).