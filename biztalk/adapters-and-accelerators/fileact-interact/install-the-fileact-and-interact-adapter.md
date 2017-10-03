---
title: Installer le FileAct et interagir adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf387d59-373b-4151-9dfd-30c511978862
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a3beccd6179bcb4526ba41f4f41a7923f5f966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-fileact-and-interact-adapter"></a>Installer le FileAct et interagir de carte
Cette section fournit des instructions pour installer [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] – pour SWIFT. Avant d’installer les adaptateurs, vous devez installer les logiciels requis.  
  
## <a name="prerequisites"></a>Conditions préalables  

* Connectez-vous avec un compte qui est membre du groupe Administrateurs local et membre du groupe Administrateurs de BizTalk Server
  
## <a name="step-1-install-biztalk-server-and-configure-bam"></a>Étape 1 : Installez BizTalk Server et configurer l’analyse BAM

1. Installer [BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md), ou [BizTalk Server 2013 R2 / 2013](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)et d’installer l’analyse BAM (Business Activity).

2. Configurer [BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md)et configurer l’analyse BAM (Business Activity).
  
3. Assurez-vous que vous avez suffisamment des privilèges de sécurité pour accéder à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. [Les droits de sécurité minimaux pour BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) est un bon point de départ.
  
## <a name="step-2-install-biztalk-accelerator-for-swift-a4swift"></a>Étape 2 : Installer BizTalk Accelerator pour SWIFT (A4SWIFT)  

Installer et configurer le [BizTalk Accelerator pour SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md).

  
## <a name="step-3-install-swiftalliance-gateway-sag"></a>Étape 3 : Installer SWIFTAlliance passerelle (trous)  
 Avant d’installer les adaptateurs FileAct et InterAct, créez les partenaires de Message anti-COULURE, Points de terminaison et des règles de routage et tester la connectivité de trous sur l’ordinateur sur lequel vous installez les adaptateurs FileAct et InterAct.

Consultez [https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway) pour plus d’informations sur la passerelle SWIFTAlliance.  

## <a name="step-4-install-the-biztalk-fileact-and-interact-adapters"></a>Étape 4 : Installer les adaptateurs BizTalk FileAct et InterAct  
  
1. Exécutez le **Setup.exe** en tant qu’administrateur pour démarrer l’installation.  
  
2.  Sélectionnez **Installer**.  
  
3.  Entrez votre nom d’utilisateur et le nom de l’organisation, puis sélectionnez **suivant**.  
  
4.  **Accepter** le contrat de licence.
  
5.  Sur le **Options d’Installation** page, effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le **Complete** option pour installer tous les composants de la FileAct et interagir de cartes.  
  
    -   Sélectionnez le **personnalisé** permet de choisir les composants à installer.  
  
     Vérifiez l’emplacement d’installation, ou sélectionnez **Parcourir** pour sélectionner un autre emplacement d’installation. Sélectionnez **Suivant**.  
  
6.  Sur le **Résumé** page, sélectionnez **installer** pour installer les composants répertoriés.  
  
    > [!NOTE]
    >  Lorsque **exécuter l’Assistant Configuration** est activée (valeur par défaut), le **Microsoft BizTalk FileAct et Configuration de l’adaptateur interagir** Assistant s’exécute automatiquement lorsque vous sélectionnez **Terminer**.  
  
7. Lors de l’installation terminée, sélectionnez **Terminer**. 

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’adaptateur FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/configure-the-fileact-and-interact-adapter.md)  
[Messages exemple interagir et FileAct](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)  
[Désinstaller ou réparer l’adaptateur FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[Lecture de l’installation des problèmes connus](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
  
## <a name="see-also"></a>Voir aussi  
[Mise en route avec les adaptateurs FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)  
[Comprendre l’architecture de l’adaptateur FileAct et InterAct](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)