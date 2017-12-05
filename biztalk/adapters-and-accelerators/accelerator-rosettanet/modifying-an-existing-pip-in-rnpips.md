---
title: "Modification d’un PIP existant dans RNPIPs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNPIPs
- modifying, PIPs
- PIPs, modifying
- assemblies, RNPIPs
ms.assetid: f2ed25c4-1979-4691-9315-e7568e7cca8b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7f87d9af24e6388199e76e9cbf0eba076ceacf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="modifying-an-existing-pip-in-rnpips"></a>Modification d’un PIP existant dans RNPIPs
Cette rubrique décrit comment modifier et redéployer l’un des schémas de processus PIP (Partner Interface) installés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] le programme d’installation. Vous déployez le schéma dans le cadre de l'assembly RNPIPs.  
  
### <a name="to-modify-an-existing-pip-in-rnpips"></a>Pour modifier un PIP existant dans RNPIPs  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  Recherchez le \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator pour le dossier du Générateur de RosettaNet\SDK\Utilities\Schema.  
  
3.  À l'invite de commandes, tapez **CScript InstallDTD.vbs**, puis appuyez sur Entrée.  
  
    > [!NOTE]
    >  Vous devez uniquement effectuer les étapes 1 et 2 une fois après l’installation de BizTalk Server.  
  
4.  Démarrez **Microsoft Visual Studio 2012**.  
  
5.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
6.  Dans le **ouvrir le projet** boîte de dialogue, accédez à \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\ Schémas, puis sélectionnez **RNPIPs.btproj**.  
  
7.  Dans le menu **Affichage** , cliquez sur **Explorateur BizTalk**. Développez **Assemblys**, puis cliquez avec le bouton droit sur **Microsoft.Solutions.BTARN.Schemas.RNPIPs(3.3.0.0)**. Cliquez sur **Annuler le déploiement**.  
  
8.  Démarrez une **invite de commandes Visual Studio 2012**.  
  
9. Accédez à l'emplacement entré à l'étape 6. À l'invite de commandes, tapez **sn -k RNPIPs.snk**, puis appuyez sur **Entrée**.  
  
10. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **RNPIPs**, cliquez sur **Propriétés**, sur **Propriétés communes**, puis sur **Assembly.**  
  
11. Dans le volet droit, faites défiler jusqu'à **Nom fort**. Dans la section **Fichier de clé de l'assembly** , cliquez sur le bouton de sélection (...) et accédez à l'emplacement entré à l'étape 6. À l'invite de commandes, tapez **RNPIPs.snk**, puis cliquez sur **OK**.  
  
12. Dans la boîte de dialogue **Pages de propriétés** , cliquez sur **Propriétés de configuration**, sur **Déploiement**, sur **Redéployer**, sélectionnez `True`, puis cliquez sur **OK**.  
  
13. Modifiez tous les schémas existants dans RNPIPs, en fonction des besoins.  
  
14. Cliquez sur **Fichier**, puis sur **Enregistrer**.  
  
15. Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.  
  
16. Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.  
  
17. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
18. Dans la Console Administration de BizTalk, développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, puis développez **hôtes**.  
  
19. Dans le volet droit, cliquez avec le bouton droit sur le nom de l'hôte, puis cliquez sur **Arrêter**. Une fois le service arrêté, cliquez avec le bouton droit sur le nom de l'hôte, puis cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [Incorporation d’un nouveau processus PIP](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)