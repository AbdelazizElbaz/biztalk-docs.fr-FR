---
title: "Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: 66c4b524-c8ff-43b5-9c44-6d7bc759ae2c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c25a348fb739f4558f1507eda0d46d209cd44c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-the-adta03-message-to-the-rx-system-using-the-file-adapter"></a>Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier
Dans cette étape, vous créez le port d’envoi pour le système pharmacie (RX) à l’aide de l’adaptateur File.  
  
### <a name="to-create-the-tutorialsendmsgrx-send-port"></a>Pour créer le port d’envoi Tutorial_sendMsg_RX  
  
1.  Dans le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, effectuez les actions suivantes, puis sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_sendMsg_RX**.|  
    |**Type de transport**|Sélectionnez **fichier** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.|  
  
3.  Dans la boîte de dialogue Propriétés du Transport FILE, effectuez les actions suivantes, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Accédez à  **\<**  *lecteur***: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendMsg_RX** .|  
    |**Nom de fichier**|Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).|  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue, pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
5.  Dans le volet gauche, sélectionnez **filtres**, puis effectuez les actions suivantes. Pour continuer, cliquez sur **OK** .  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété** (première ligne)|Sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez **! =** dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **ou** dans la liste déroulante.|  
    |**Propriété** (deuxième ligne)|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez **! =** dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété** ((troisième ligne)|Sélectionnez **BTAHL7Schemas.MSH3_1**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **Tutorial_ADTSystem**.|  
  
    > [!NOTE]
    >  Le premier filtre signifie que le système d’informations hôpital (HIS) s’abonnant à un message, pas un accusé de réception. Le deuxième filtre signifie que son s’abonne aux messages dont la source est la décharge d’admission et le système de transfert (ADT).  
  
    > [!NOTE]
    >  BTAHL7 dépose le message à l’emplacement de dépôt du fichier \< *lecteur*> : programme FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd en bout TutorialTutorial_sendMsg_RX.  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK.**  
  
7.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_sendMsg_RX**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 7 : créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md).