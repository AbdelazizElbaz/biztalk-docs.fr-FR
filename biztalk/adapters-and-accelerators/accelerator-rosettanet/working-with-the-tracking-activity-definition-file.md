---
title: "Utilisation avec le fichier de définition d’activité suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking, activity definition file
- activity definition file
- activity definition file, about activity definition file
- tracking, managing views
- activity definition file, activity fields
ms.assetid: 0592a844-aad7-4054-b1e7-344f1086f0b1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 751b05f28682ecc0a0230fc924cf706d0531784d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-the-tracking-activity-definition-file"></a>Utilisation avec le fichier de définition des activités de suivi
Le fichier de définition d’activité contient des informations sur le suivi des activités de processus et le message dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]utilise ce fichier pour gérer les données de suivi dans BizTalk d’analyse BAM (Business Activity). Le fichier de définition est un fichier XML (Tracking.xml) qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] le programme d’installation installe dans le \< *lecteur*> : \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet \BAMTracking dossier. Les activités définies dans Tracking.xml peuvent suffire à vos besoins.  
  
 Pour plus d’informations sur le suivi des activités, des vues et tables, consultez [amélioré de suivi](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md). Pour plus d’informations sur BAM, consultez « analyse BAM (Business Activity) » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="managing-tracking-views"></a>La gestion des vues de suivi  
 Vous n’utilisez pas l’éditeur de modèle de suivi BizTalk avec [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] de suivi. Les points de suivi ne sont pas personnalisables ; ne modifiez pas les définitions d’activité. Toutefois, vous pouvez gérer le déploiement et les vues BAM. Pour ce faire, vous modifiez un [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] feuille de calcul (Tracking.xls) qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] le programme d’installation installe dans le \< *lecteur*> : \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\BAMTracking dossier. Pour plus d’informations, consultez « Gestion de suivi des vues » ci-dessous.  
  
 Si les vues définies dans Tracking.xml ne suffisent pas à vos besoins, vous pouvez définir des vues différentes des informations de suivi de l’analyse BAM comme suit.  
  
#### <a name="to-create-different-tracking-views"></a>Pour créer des vues de suivi différent  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**. Entrez **cmd** dans la zone de texte Ouvrir de la boîte de dialogue Exécuter, puis cliquez sur **OK**. Dans la boîte de dialogue ligne de commande, entrez le code suivant pour annuler le déploiement de tracking.xml, puis cliquez sur **OK**:  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm remove-all  -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking\<filename>.xml"  
    ```  
  
2.  Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à  *\<lecteur >*: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM de suivi. Double-cliquez sur Tracking.xls.  
  
3.  Créer une nouvelle vue dans l’analyse BAM. Pour plus d’informations sur la marche à suivre, consultez « Gestion de l’analyse BAM » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
4.  Cliquez sur **BAM**, puis cliquez sur **exporter XML**. Déplacer vers l’emplacement souhaité, entrez un nom de fichier (autres que Tracking.xml), puis cliquez sur **enregistrer**.  
  
    > [!IMPORTANT]
    >  Lorsque vous définissez de nouveaux affichages de suivi dans un fichier XLS de suivi et exportez un fichier XML à partir du fichier XLS de suivi, certains des nouveaux noms de champs peuvent être légèrement modifiées. Corriger ce problème en vérifiant les champs dans votre personnalisés de suivi de fichier XML dans le champ tracking.xml standard installé par le programme d’installation BTARN.  
  
5.  Déployer le suivi de nouveau fichier XML. Pour ce faire, cliquez sur **Démarrer**, puis cliquez sur **exécuter**. Entrez **cmd** dans la zone de texte Ouvrir de la boîte de dialogue Exécuter, puis cliquez sur **OK**. Dans la boîte de dialogue ligne de commande, entrez le code suivant pour déployer votre nouveau fichier de suivi, puis cliquez sur **OK**. Il est recommandé de renommer le fichier XML de suivi afin que vous ne pas Remplacez le fichier tracking.xml par défaut.  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
    bm.exe deploy-all -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2030 Accelerator for RosettaNet\BAMTracking\<filename>.xml"  
    ```  
  
 Les informations de suivi dans BAM n’incluent pas le contenu du message, car qui est stocké dans un [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] base de données.  
  
 Vous pouvez gérer le déploiement de suivi à l’aide de l’entreprise activité analyse utilitaire de gestion BAM. Pour plus d’informations sur cet utilitaire, consultez « À l’aide de l’utilitaire de Business activité analyse gestion » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="activity-fields"></a>Champs d’activité  
 Les champs de l’activité d’un message dans le fichier de définition d’activité sont les suivants :  
  
-   NomActivité  
  
-   Catégorie  
  
-   ContentKey  
  
-   DestinationPartyName  
  
-   ErrorDescription  
  
-   HasError  
  
-   InReplyToMessageID  
  
-   IsReceived  
  
-   MessageTrackingID  
  
-   NoFPipInstance  
  
-   PipCode  
  
-   PipInstanceID  
  
-   PiPVersion  
  
-   SourcePartName  
  
-   Horodateur  
  
 Les champs de l’activité de processus dans le fichier de définition d’activité sont les suivants :  
  
-   EndTime  
  
-   InitiatorPartyName  
  
-   IsInitiatorRole  
  
-   PipCode  
  
-   PipInstanceID  
  
-   PipName  
  
-   PipVersion  
  
-   ResponderPartyName  
  
-   StartTime  
  
-   État  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi amélioré](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)