---
title: "Ajout de l’adaptateur à BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards OneWorld adapters], installing
- installing, JD Edwards OneWorld adapters
- JD Edwards OneWorld adapters, installing
ms.assetid: e2018856-1943-48e9-b43f-7d527880e4bd
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63de8824112c9891c6d67eee424a84dd4968976c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-adapter-to-biztalk-server"></a>Ajout de l’adaptateur à BizTalk Server
L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld contient les dossiers du gestionnaire de réception et du gestionnaire d'envoi. Le dossier du gestionnaire d'envoi contient BizTalkServerApplication. L'adaptateur BizTalk pour JD Edwards OneWorld peut être créé. Il est exécuté de façon In-process avec BizTalk Server et n'est pas exécuté dans un processus d'hôte isolé.  
  
 Pour ajouter l'adaptateur à BizTalk Server, procédez comme suit.  
  
### <a name="to-add-biztalk-adapter-for-jd-edwards-oneworld"></a>Pour ajouter l'adaptateur BizTalk pour JD Edwards OneWorld  
  
1.  Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server** pour démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration.  
  
2.  Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **paramètres de plateforme**.  
  
3.  Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.  
  
4.  Dans le **propriétés de l’adaptateur** boîte de dialogue, tapez un nom pour l’adaptateur. Par exemple, JDEdwards.  
  
5.  Sélectionnez **JDEOneWorld** à partir de la **carte** liste, puis cliquez sur **OK**.  
  
## <a name="verifying-the-adapter"></a>Vérification de l'adaptateur  
 Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, vous pouvez vérifier que l’adaptateur fonctionne correctement en examinant le **système logique** fenêtre. Lors de l'installation initiale, cette fenêtre est vide car vous n'avez pas encore établi de connexion au système serveur, ni créé de système logique.  
  
#### <a name="to-verify-that-the-adapter-is-running-correctly"></a>Pour vérifier le bon fonctionnement de l'adaptateur  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez **paramètres de plateforme**, développez **cartes**, puis sélectionnez  **JDEOneWorld**.  
  
2.  Dans le volet détails, cliquez sur **BizTalkServerApplication**, puis sélectionnez **propriétés**.  
  
3.  Cliquez sur l’onglet **Propriétés** .  
  
4.  Définissez les paramètres de connexion SQL.  
  
    -   **Définir des paramètres de base de données SQL -** le nom du serveur SQL et la base de données sont ceux que vous définissez lors de l’installation. Il s'agit de la zone de texte dans laquelle vous pouvez redéfinir le serveur et la base de données pour cet adaptateur.  
  
5.  Cliquez sur **fermer** pour quitter le **système logique** fenêtre.  
  
     La prochaine étape consiste à ajouter un système logique à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et Architecture](../core/planning-and-architecture17.md)   
 [Sécurité de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Ajout de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)