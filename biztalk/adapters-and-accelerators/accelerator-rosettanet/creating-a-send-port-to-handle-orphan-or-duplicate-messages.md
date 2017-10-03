---
title: "Création d’un Port d’envoi pour gérer orphelines ou des Messages en double | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, duplicate messages
- messages, orphaned messages
- send ports, duplicate messages
- send ports, orphaned messages
- messages, send ports
ms.assetid: 61d51206-13e3-4d32-a184-866248db9b45
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9a5e52197c81e86bac69603e72d294cfbcd6faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-send-port-to-handle-orphan-or-duplicate-messages"></a>Création d’un Port d’envoi pour gérer orphelines ou des Messages en double
Cette rubrique décrit comment configurer un port d’envoi que vous pouvez utiliser pour supprimer orphelines ou des messages en double.  
  
 Orphelines ou des messages en double peuvent être un problème si [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] reçoit des copies supplémentaires d’un message une fois l’orchestration de processus publics a terminé le traitement de la première copie du message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]marque les messages comme des doublons et les interrompt. Vous pouvez afficher ces messages dans la Console Administration de BizTalk. Pour plus d’informations sur la Console Administration de BizTalk, consultez « À l’aide de la Console d’Administration BizTalk » dans le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Orphelin ou des messages en double restent dans la Console Administration de BizTalk, jusqu'à ce que vous passez en revue ou les supprimer. Il est le moyen le plus efficace de les supprimer pour configurer un port d’envoi avec les filtres définis pour orphelin ou des messages en double. Vous pouvez les déplacer à l’aide de n’importe quel moyen de transport disponibles dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]. Par exemple, vous pouvez les déplacer à l’aide du transport File. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie les messages en double orphelin sous forme de fichiers vers un emplacement sur un disque dur. Vous pouvez ainsi facilement la supprimer. Le port peut être dans l’inscrit et arrêté état, dans laquelle les cas de tous les messages envoyés à ce dernier apparaît comme suspendu sous ce port d’envoi.  
  
> [!NOTE]
>  Au lieu de créer un port d’envoi pour traiter les messages en double et orphelines, vous pouvez créer un composant de pipeline spécial pour supprimer ces messages à partir de la base de données MessageBox. Vous pouvez utiliser le composant FixMsg dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Kit de développement logiciel en tant que modèle. Vous devez modifier le `IComponent.Execute` méthode pour retourner une valeur null. Cela entraîne [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour ignorer les messages envoyés à un pipeline qui contient le composant. Vous devez compiler ce composant de pipeline et ajoutez-le à un pipeline d’envoi, puis le compiler, déployer et sélectionnez le pipeline d’envoi pour le port récepteur. Pour plus d’informations, consultez « CustomComponent ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] exemple) » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
### <a name="to-create-a-send-port-to-handle-orphan-or-duplicate-messages"></a>Pour créer un port d’envoi pour gérer orphelines ou des messages en double  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **vue** menu, cliquez sur **l’Explorateur BizTalk**.  
  
2.  Dans l’Explorateur BizTalk, développez **base de données de gestion BizTalk**, puis développez **Ports d’envoi**.  
  
3.  Cliquez avec le bouton droit sur **Ports d'envoi**, puis cliquez sur **Ajouter un port d'envoi**.  
  
4.  Dans la fenêtre Créer un Port d’envoi, sélectionnez **Port statique unidirectionnel**, puis cliquez sur **OK**.  
  
5.  Dans la fenêtre statique propriétés du Port d’envoi unidirectionnel, dans le **nom** , tapez un nom pour le port d’envoi.  
  
6.  Dans le volet gauche, cliquez sur **Transport**. Dans le volet droit, cliquez sur **Type de Transport**, puis sélectionnez **fichier** pour le type de transport. Cliquez sur le bouton de sélection (...) à côté de **adresse (URI)**, tapez un emplacement sur votre disque dur, puis cliquez sur **OK**.  
  
7.  Dans le volet gauche, cliquez sur **envoyer**, cliquez sur **Pipeline d’envoi**, puis sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
8.  Dans le volet gauche, cliquez sur **filtre et mappe**, puis cliquez sur **filtres**.  
  
9. Sur la première ligne dans le volet droit, pour **propriété**, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.IsDuplicateMessage** dans la liste déroulante, laissez le **opérateur**en tant que  **==** , entrez **True** pour **valeur**, puis sélectionnez **ou** dans la liste déroulante pour  **Groupe**.  
  
10. Sur la deuxième ligne dans le volet droit, pour **propriété**, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.IsOrphanMessage** dans la liste déroulante, laissez le **opérateur**en tant que  **==** , puis entrez **True** pour **valeur**.  
  
11. Cliquez sur **OK**.  
  
12. Dans l’Explorateur BizTalk, cliquez sur le nom du port d’envoi, cliquez sur **Enlist**. Une fois que le port d’envoi a été inscrit, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)