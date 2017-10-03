---
title: "Étape 3 : Créer et déployer un Project_hl7_main d’événement (Message) de déclencheur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, trigger events
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7abfcf363d26d068fab067378eb61d5bcf5c3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-projecthl7main"></a>Étape 3 : Créer et déployer un Project_hl7_main d’événement (Message) de déclencheur
Dans cette étape, vous créez le schéma utilisé par un message d’événement déclencheur. Par exemple, le système décharge d’admission et de transfert (ADT) qui envoie un message à l’hôpital informations système (HIS). Ce schéma permet de définir le format de votre message.  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a>Pour créer le projet pour le message d’événement déclencheur  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.  
  
3.  Dans le **modèles** , cliquez sur **projet BTAHL7 vide**.  
  
4.  Dans le **nom** , tapez **BTAHL7V24Body projet**, puis cliquez sur **OK**.  
  
5.  Dans l’Explorateur de solutions, sous le nœud pour votre nouveau **BTAHL7V24Body** de projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
6.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **projets** onglet, sélectionnez **Interrogative_24Schemas**, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
## <a name="step-3a-add-the-schemas"></a>Étape 3 a : ajoutez les schémas  
 Utilisez la procédure suivante pour ajouter les nouveaux schémas au projet.  
  
#### <a name="to-add-the-schemas-to-the-project"></a>Pour ajouter les schémas au projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V24Body projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, développez **des éléments de projet BizTalk**, puis double-cliquez sur **BTAHL7 schémas** dans le volet droit.  
  
3.  Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Classe de message**|Conserver **V2.X** sélectionné.|  
    |**Version**|Sélectionnez **2.4**.|  
    |**Type de message**|Sélectionnez **req**.|  
    |**Événement déclencheur**|Sélectionnez **Q01**.|  
  
4.  Cliquez sur **Terminer** pour ajouter le schéma au projet.  
  
     Cette opération crée le fichier de schéma de requête QRY_Q01_24_GLO_DEF.xsd.  
  
    > [!NOTE]
    >  Ne fermez pas la boîte de dialogue Sélecteur de schémas HL7.  
  
5.  Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Classe de message**|Conserver **V2.X** sélectionné.|  
    |**Version**|Sélectionnez **2.4**.|  
    |**Type de message**|Sélectionnez **DSR**.|  
    |**Événement déclencheur**|Sélectionnez **Q01**.|  
  
6.  Cliquez sur **Terminer** pour ajouter le schéma au projet.  
  
     Cette opération crée le fichier de schéma de réponse DSR_Q01_24_GLO_DEF.xsd.  
  
7.  Cliquez sur **Annuler** pour fermer la **sélecteur de schémas HL7** boîte de dialogue.  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a>Étape 3 b : assigner une clé forte à l’Assembly et le déployer  
 Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>Pour affecter une clé forte et de déployer l’assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V24Body** de projet, puis cliquez sur **propriétés**.  
  
2.  Dans le **Pages de propriétés BTAHL7V24Body** boîte de dialogue, cliquez sur **Assembly**.  
  
3.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).  
  
4.  Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for HL7\SDK\ Cliquez (didacticiel), interrogative **key.snk**, puis cliquez sur **ouvrir**.  
  
5.  Dans le **Pages de propriétés BTAHL7V24Body** boîte de dialogue, cliquez sur **OK** pour enregistrer vos modifications.  
  
6.  Dans l’Explorateur de solutions avec le bouton droit **BTAHL7V24Body projet**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si un message de réussite de déploiement n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.  
  
 Passez à [étape 4 : créer le Port de réception pour accepter les Messages de requête ADT](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).