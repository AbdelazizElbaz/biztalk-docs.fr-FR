---
title: "Installer le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e9d4dfe5818e28e1ccd73b077c19c9d45ecb8cc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-wcf-lob-adapter-sdk"></a>Installer le Kit de développement logiciel de l’adaptateur LOB WCF
Installer et configurer le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. 
  
## <a name="requirements"></a>Spécifications 
Installer les composants sur le système sur lequel vous installez la suite la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. 

> [!NOTE]
> **Pour obtenir la liste des versions prises en charge**, consultez : 
> 
> [Configurations logicielle et matérielle pour BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [Configuration matérielle et logicielle requise pour BizTalk Server 2013 et 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)
 
 | | | 
 | --- | --- |
 | Windows | x86 ou x64 <br/><br/>Les ressources du système d’exploitation requises sont les suivantes :<br/> <ul><li>Microsoft Distributed Transaction Coordinator (MSDTC) : Requis pour prendre en charge les transactions OleTx</li><li>Message Queuing (MSMQ) : Requis pour prendre en charge la messagerie fiable</li><li>Internet Information Services (IIS) : Requis si vous souhaitez héberger votre application dans IIS</li><li>Windows Process Activation Service (WAS) : Requis si vous souhaitez héberger votre application dans WAS</li></ul> |
 |Windows Communication Foundation| | 
 | [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] | | 
 | [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] | Requis si vous générez des adaptateurs personnalisés ou développer des solutions qui utilisent les adaptateurs générée à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] | Requis si vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  |


  
## <a name="install"></a>Install

> [!IMPORTANT]
> * Fermez toutes les instances de Visual Studio
> * Pour effectuer un **terminé** le programme d’installation, vérifiez que BizTalk Server est installé sur l’ordinateur.  
  
1.  Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** en tant qu’administrateur.
  
2.  Sélectionnez **installer des adaptateurs Microsoft BizTalk**, puis sélectionnez **installer Microsoft WCF LOB Adapter SDK**.  
  
3.  Sur le **Bienvenue** écran, sélectionnez **suivant**.  
  
4.  Acceptez le contrat de licence et sélectionnez **Suivant**.  
  
5.  Dans **choisir le Type de programme d’installation**, sélectionnez le type d’installation :  
  
    -   Pour installer les outils et le moment de l’exécution courantes, sélectionnez **standard**.  
  
    -   Pour sélectionner les fonctionnalités que vous souhaitez installer et l’emplacement d’installation, sélectionnez **personnalisé**, puis sélectionnez les fonctionnalités que vous souhaitez installer.  
  
    -   Pour installer toutes les fonctionnalités, sélectionnez **Complete**.  
  
6.  Sélectionnez **Installer**.  
  
## <a name="update-or-remove"></a>Mise à jour ou supprimer
  
1.  Ouvrez **programmes et fonctionnalités**. 
  
2.  Dans la liste, sélectionnez **Windows Communication Foundation LOB Adapter SDK**, puis sélectionnez **modification**.  
  
3.  Sur le **Bienvenue** écran, sélectionnez **suivant**.  
  
4.  Procédez de l'une des manières suivantes :  
  
    -   Pour sélectionner les composants que vous souhaitez installer, sélectionnez **modification**.  
  
    -   Pour réparer les erreurs dans l’installation la plus récente, sélectionnez **réparer**.  
  
    -   Pour supprimer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] à partir de l’ordinateur, sélectionnez **supprimer**.  
  
5.  Si vous choisissez de modifier l’installation :  
  
    1.  Sélectionnez **Suivant**.  
  
    2.  Sélectionnez **modification**, puis sélectionnez **Terminer**.  
  
6.  Si vous choisissez de réparer l’installation, dans le **prêt à réparer WCF LOB Adapter SDK** boîte de dialogue, sélectionnez **réparer**, puis sélectionnez **Terminer**.  
  
7.  Si vous choisissez de supprimer les adaptateurs, dans le **prêt à supprimer WCF LOB Adapter SDK** boîte de dialogue, sélectionnez **supprimer**, puis sélectionnez **Terminer**.  
  
  
#### <a name="remove-custom-adapters-after-uninstalling-the-wcf-lob-adapter-sdk"></a>Supprimer les cartes personnalisées après la désinstallation de WCF LOB Adapter SDK  

 Si vous avez développé des adaptateurs personnalisés à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]et que vous avez enregistré ces adaptateurs sur votre ordinateur, vous devez également effectuer la procédure suivante.  
  
1.  Supprimer l’adaptateur personnalisé dans le global assembly cache (GAC).  
  
    1.  Ouvrir un **invite de commandes Visual Studio**.  
  
    2.  Supprimer personnalisé **.dll de l’adaptateur** à partir du GAC avec **commande gacutil /u**.  
  
2.  Supprimez les références à la liaison de l’adaptateur personnalisé à partir de machine.config  
  
    1.  Accédez au fichier machine.config sous \< *lecteur système*\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.  
  
    2.  Ouvrez le fichier à l’aide d’un éditeur de texte.  
  
    3.  Recherche de l’élément bindingExtensions client et bindingElementExtensions sous system.serviceModel\extensions.  
  
    4.  Supprimez la liaison WCF qui se rapporte à votre adaptateur personnalisé.  
  
## <a name="do-a-silent-installation"></a>Effectuez une installation sans assistance  
 Une installation sans assistance est idéale pour les scénarios de test ou dans le cadre d’un déploiement d’entreprise à grande échelle. [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]Fournit des paramètres de ligne de commande que vous pouvez utiliser avec AdapterFramework.msi pour effectuer une installation sans assistance.  
 
> [!NOTE]
>  Pour effectuer une installation sans assistance, vous devez être un administrateur sur l’ordinateur. 

  
1.  Ouvrez une invite de commandes comme administrateur.  
  
2.  Tapez la commande suivante :
  
    ```  
    AdapterFramework.msi /quiet MUOPTIN=”Yes”  
    ```  
  
    Utilisez les options de ligne de commande suivantes conjointement avec AdapterFramework.msi :  
  
    * Utilisez `/quiet` pour installer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en mode silencieux.  
  
    * Utilisez MUOPTIN = « Yes » &#124; » Non » pour indiquer si le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] doit rechercher des mises à jour avec Microsoft Update.  
    
        Lorsque la valeur Oui, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] vérifie les mises à jour via Microsoft Update. Lorsque la valeur non [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] ne vérifie pas les mises à jour avec Microsoft Update.  
  
> [!NOTE]
>  Pour afficher des options supplémentaires pour l’installation de ligne de commande, tapez `AdapterFramework.msi /?`à l’invite de commandes.  
  
