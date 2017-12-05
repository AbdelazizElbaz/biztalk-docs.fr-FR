---
title: "Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6e63590c8cc84a6c6c1a7e957900aa44cdcd61c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-5-create-a-send-port-to-deliver-acknowledgments-to-the-adt-system-using-the-file-adapter"></a>Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur de fichier
Dans cette étape, vous créez le port d’envoi pour générer des accusés de réception à l’aide de l’adaptateur File.  
  
### <a name="to-create-the-tutorialsendackadt-send-port"></a>Pour créer le port d’envoi Tutorial_sendAck_ADT  
  
1.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, créer le \< *lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ sendAck_ADT dossier.  
  
2.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Tutorial_sendAck_ADT**.|  
    |**Type de transport**|Sélectionnez **fichier** dans la liste déroulante.|  
    |**Configurer**|Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.|  
  
4.  Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit, puis **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de destination**|Accédez à  **\<**  *lecteur***:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendAck_ADT**.|  
    |**Nom de fichier**|Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).|  
  
5.  Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.  
  
6.  Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :  
  
    > [!NOTE]
    >  Le premier filtre signifie que vous vous abonnez pour le message d’accusé de réception. Le deuxième filtre signifie que vous vous abonnez à l’accusé de réception vers le serveur de publication Tutorial_ADTSystem.  
  
     Cliquez sur **OK** lorsque vous êtes prêt à continuer.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.|  
    |**Regrouper par**|Sélectionnez **ou** dans la liste déroulante.|  
    |**Propriété (deuxième ligne)**|Cliquez sur le champ sous **propriété**, puis sélectionnez **BTS. MessageType** dans la liste déroulante.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**|  
    |**Regrouper par**|Sélectionnez **et** dans la liste déroulante.|  
    |**Propriété**|Dans la première propriété, cliquez sur la zone vierge, puis **BTAHL7Schemas.MSH5_1**.|  
    |**Opérateur**|Sélectionnez  **==**  dans la liste déroulante.|  
    |**Valeur**|Type **Tutorial_ADTSystem**.|  
  
    > [!NOTE]
    >  Pour le port d’envoi Tutorial_sendAck_ADT BTAHL7 supprime les accusés de réception à l’emplacement de dépôt du fichier \< *lecteur*\>: programme FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd en bout TutorialTutorial_sendAck_ADT.  
  
7.  Cliquez sur **appliquer**, puis cliquez sur **OK.**  
  
8.  Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_sendAck_ADT**, puis cliquez sur **Démarrer**.  
  
 Passez à [étape 6 : créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md).