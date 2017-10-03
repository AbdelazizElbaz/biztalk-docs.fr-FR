---
title: Extension BTARN avec un nouveau PIP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, extending functionality
- PIPs, extending BTARN
- BTARN, PIPs
ms.assetid: 3db5cd5c-031f-4451-9be5-4b5d6163c3b1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbf18261b1b6b30ab43816f4052022c652cec687
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-btarn-with-a-new-pip"></a>Extension de BTARN avec un nouveau PIP
Cette rubrique décrit comment étendre [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] avec un nouveau schéma de processus PIP (Partner Interface). Cela vous permet d’ajouter un schéma basé sur un PIP RosettaNet lorsque ce PIP n’est pas associé avec les schémas installés par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation.  
  
 Lorsque vous étendez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] avec une adresse PIP à nouveau, vous déployez le nouveau schéma dans son propre assembly. Vous pouvez également modifier un schéma existant qui est déployé dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly RNPIPs. Pour plus d’informations, consultez [modifiant un PIP existants dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  
  
### <a name="to-extend-btarn-with-a-new-pip"></a>Pour étendre BTARN avec un nouveau PIP  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l’invite de commandes, accédez au \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator pour RosettaNet\SDK\Utilities\Schema générateur.  
  
3.  À l’invite de commandes, tapez **CScript InstallDTD.vbs**, puis appuyez sur **entrée**.  
  
    > [!NOTE]
    >  Vous devez uniquement effectuer les étapes 1 à 3 fois après l’installation de [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
4.  Démarrez [!INCLUDE[vs2012](../../includes/vs2012-md.md)].  
  
5.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
6.  Dans la boîte de dialogue Nouveau projet, sélectionnez **projets BizTalk** dans le volet gauche, puis cliquez sur **projet BizTalk Server vide** dans le volet droit.  
  
7.  Cliquez sur **Parcourir** et pointer vers le répertoire où vous souhaitez enregistrer votre projet.  
  
8.  Dans le **nom** , tapez un nom de projet, tel que **MyCustomPIP**, puis cliquez sur **OK**.  
  
9. Démarrer [!INCLUDE[vs2012](../../includes/vs2012-md.md)] invite de commandes.  
  
10. À l’invite de commandes, accédez à l’emplacement entré à l’étape 7, type **sn -k \<name.snk du projet >**, puis appuyez sur **entrée**.  
  
11. Dans l’Explorateur de Solutions, cliquez sur le nom du projet, puis cliquez sur **propriétés**.  
  
12. Dans le **Pages de propriétés** boîte de dialogue, cliquez sur **Assembly** sous **propriétés communes** dans le volet gauche.  
  
13. Dans le volet droit, faites défiler jusqu'à **Strong Name**, cliquez sur **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...) dans le volet droit. Déplacer vers l’emplacement entré à l’étape 7 et sélectionnez le nom du fichier .snk créé à l’étape 10.  
  
14. Dans la boîte de dialogue Pages de propriétés, développez **propriétés de Configuration**, puis cliquez sur **déploiement**. Dans le volet droit, cliquez sur **redéployer**, sélectionnez `True`, puis cliquez sur **OK**.  
  
15. Dans l’Explorateur de solutions, cliquez sur le nom du projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
16. Dans le **ajouter un élément existant** boîte de dialogue, accédez à \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator pour RosettaNet\SDK\Schemas, sélectionnez **xml.xsd**, puis cliquez sur **ajouter**.  
  
17. Téléchargez le PIP que vous vous apprêtez à étendre RNPIPs avec RosettaNet.org. Pour plus d’informations, consultez [comprenant un nouveau Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).  
  
18. Dans l’Explorateur de solutions, développez le nom du projet, cliquez sur **référence**, puis cliquez sur **ajouter une référence**.  
  
19. Dans le **ajouter une référence** boîte de dialogue, cliquez sur **Parcourir**et les déplacer vers \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accélérateur pour RosettaNet\Bin, puis sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**. Cliquez sur **ouvrir**, puis cliquez sur **OK**.  
  
20. Dans l’Explorateur de solutions, cliquez sur le nom du projet, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
21. Dans le **ajouter les éléments générés** boîte de dialogue le **catégories** volet, cliquez sur **générer les schémas**. Dans le **modèles** volet, cliquez sur **générer les schémas**, puis cliquez sur **ajouter**.  
  
22. Dans la boîte de dialogue Générer les schémas, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Type de document**|Sélectionnez **DTD schéma**.|  
    |**Fichier d’entrée**|Cliquez sur **Parcourir**, accédez au dossier qui contient le fichier DTD à partir de RosettaNet.org, sélectionnez le fichier DTD que vous souhaitez, puis cliquez sur **ouvrir**.|  
  
23. Dans la boîte de dialogue Générer les schémas, cliquez sur **OK**.  
  
24. Dans l’Explorateur de solutions, double-cliquez sur le fichier .xsd que vous venez d’importer.  
  
25. Dans l’Éditeur BizTalk, sélectionnez le \< *schéma*> nœud.  
  
26. Dans la fenêtre Propriétés, faites défiler jusqu'à **Type de Document**. Dans le **Type de Document** boîte, **PIP**\<*code de trois chiffres*>, par exemple, **PIP3A2**. Dans le **Version du Document** , tapez **v**\<*xx.xx*> ou **R**\<*xx.xx*>, par exemple, **R01.02**. Cette version doit être documentée dans la spécification PIP RosettaNet.  
  
27. Dans la fenêtre Propriétés, faites défiler jusqu'à **référence de racine**. Cliquez sur **référence de racine**et dans la liste déroulante, sélectionnez le nœud racine du schéma, par exemple, sélectionnez **Pip3C5BillingStatementNotification**.  
  
28. Dans la fenêtre Propriétés, faites défiler jusqu'à **cible Namespace**. Pour **cible Namespace**, type **http://schemas.microsoft.com/biztalk/btarn/2004/\<nom de fichier DTD > .dtd**, où est le nom du fichier DTD, par exemple, **3C5_MS_R01_00_ BillingStatementNotification.dtd**.  
  
    > [!NOTE]
    >  Cette convention d’affectation de noms pour l’espace de noms cible est requise pour BTARN. Si vous utilisez une autre convention d’espace de noms, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne traitera pas les documents PIP pour la validation de schéma.  
  
    > [!NOTE]
    >  Le nom de fichier DTD dans la propriété d’espace de noms cible inclut le numéro de version du PIP. Cela vous permet d’utiliser plusieurs versions du même code PIP.  
  
29. Dans la fenêtre Propriétés, faites défiler jusqu'à **importations**. Cliquez sur le bouton de sélection (...) à côté de **importations**, puis cliquez sur **ajouter**.  
  
30. Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez \< *nom du projet*>, développez **références**, développez  **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, développez **schémas**, sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs.BaseDataTypes**, cliquez sur **OK** , puis cliquez sur **OK** à nouveau.  
  
31. Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.  
  
32. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
33. Dans la Console Administration de BizTalk, développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, puis développez **hôtes**. Sous **hôte**, cliquez sur **BizTalkServerApplication**.  
  
34. Dans le volet droit, cliquez sur le nom de l’hôte, puis cliquez sur **redémarrer**.  
  
    > [!NOTE]
    >  Après avoir étendu RNPIPs avec une adresse PIP nouvellement importé, vous devez créer la configuration correcte de PIP, ainsi qu’un accord à l’aide de ce PIP, dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vous incorporez un nouveau Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)   
 [Utilisation des adresses PIP](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [Modification d’un PIP existant dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)