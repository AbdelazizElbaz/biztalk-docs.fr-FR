---
title: "Mettre à jour, réparer ou désinstaller BizTalk Accelerator pour HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2fc84d2-1262-4a6e-ae9c-488a00ab4099
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4fa1dba322e830114a76a0ca69134edbb1d06
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="update-repair-or-uninstall-biztalk-accelerator-for-hl7"></a>Mettre à jour, réparer ou désinstaller BizTalk Accelerator pour HL7

Modifier, réparer ou désinstaller le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].  
  
> [!IMPORTANT]
>  Veillez à désinstaller [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] avant de désinstaller [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]ne peut pas être désinstallé si [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] n’est plus installé.  

## <a name="prerequisites"></a>Configuration requise
* Connectez-vous à l’aide d’un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  

* Ce compte d’utilisateur doit également être membre du groupe Administrateurs sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] qui stocke le BizTalk Accelerator pour HL7 données.  
    
## <a name="update-an-existing-installation"></a>Mettre à jour une installation existante

> [!NOTE]
>  Lorsque vous modifiez votre installation de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], le didacticiel de bout en bout ne s’exécute pas automatiquement. 
> 
> Pour exécuter le didacticiel et vérifier que l’installation modifiée exécutées correctement, exécutez le didacticiel manuellement à partir de la  ***\<lecteur\>***  **\Program Files\Microsoft BizTalk \< version\> Accelerator pour le didacticiel de bout en HL7\SDK\End** dossier.
  
1. Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** en tant qu’administrateur 
  
2.  Dans la page de bienvenue, sélectionnez **suivant**.  
  
3.  Dans **Maintenance du programme**, sélectionnez **modifier**, puis sélectionnez **suivant**.  
  
4.  Dans **installation personnalisée**, sélectionnez les fonctionnalités que vous souhaitez installer, désactivez les fonctionnalités vous ne souhaitez, puis sélectionnez **suivant**.  
  
5.  Dans la section Résumé, sélectionnez **suivant**.  
  
6.  Sélectionnez **Installer**.  
  
7. Lorsque vous avez terminé, sélectionnez **Terminer**.  

## <a name="repair-an-existing-installation"></a>Réparer une installation existante
Le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] Assistant répare une installation en corrigeant les fichiers manquants ou endommagés, les raccourcis ou les entrées de Registre.  
  
1. Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** en tant qu’administrateur.  
  
2.  Dans la page de bienvenue, sélectionnez **suivant**.  
  
3.  Dans **Maintenance du programme**, sélectionnez **réparation**, puis sélectionnez **suivant**.  
  
4.  Dans **compte de Service de journalisation**, entrez de nouveau le compte d’utilisateur, puis sélectionnez **OK**.  
  
4.  Si vous y êtes invité **le nom du compte a été accordé d’ouverture de session en tant que service droit**, puis sélectionnez **OK** pour continuer.  
  
5.  Lorsque vous êtes prêt à réparer, sélectionnez **installer**.  
  
6. Lorsque terminée, sélectionnez **Terminer**. 

  
## <a name="uninstall-btahl7"></a>Désinstaller BTAHL7  

> [!IMPORTANT]
>  S’il existe un emplacement de réception ou un port d’envoi à l’aide du type de transport MLLP, le programme d’installation BTAHL7 ne supprime pas l’adaptateur MLLP lors de la désinstallation de BTAHL7. Avant de désinstaller, supprimer tous les emplacements de réception ou envoient ports utilisant le transport MLLP. Ou bien, modifiez le type de transport à partir de MLLP à un autre type. Ensuite, la désinstallation supprime l’adaptateur MLLP.  
      
1.  Ouvrez **Programmes et fonctionnalités**.  
  
2.  Sélectionnez [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], puis sélectionnez **désinstallation**.  
  
4.  Sélectionnez **Oui** si vous êtes invité à confirmer. 
  
5.  Lorsque terminée, sélectionnez **Terminer**.  
  
    > [!NOTE]
    >  BTAHL7 ne désinstalle pas automatiquement [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artefacts et les assemblys.  
  

  
## <a name="troubleshooting-installation-issues"></a>Résolution des problèmes d’Installation  
 Si le serveur est incapable de vérifier si l’utilisateur est un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] administrateur, désinstallation de BTAHL7 retourne l’erreur suivante : 
 
 `Fatal error during uninstallation`  
  
Pour poursuivre la désinstallation, procédez comme suit :  
  
1.  Connectez-vous au serveur en tant qu’administrateur local.  
  
2.  Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Désinstallez [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[Installer ou mettre à niveau Microsoft BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)