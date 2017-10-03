---
title: "L’installation du logiciel BAM-événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3638d34-f5a8-4ffd-99eb-d38aed4c0732
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c41606f6056dcc4edb90b4db5ef6a41901835b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-bam-eventing-software"></a>Installation du logiciel BAM-Événements
Pour mettre en œuvre des solutions BAM à l'aide des API d'événements BAM ou configurer votre application Windows Workflow Foundation ou Windows Communication Foundation afin d'utiliser l'intercepteur BAM pour Windows Workflow Foundation, vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce logiciel peut être installé dans le cadre de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou séparément en sélectionnant Prise en charge de BAM-Événements sous Logiciels complémentaires dans l'application d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-install-the-bam-eventing-software"></a>Pour installer le logiciel BAM-Événements  
  
1.  Connectez-vous à l'ordinateur qui hébergera l'application WF en utilisant un compte disposant des privilèges d'administrateur.  
  
2.  Exécutez le programme d'installation disponible sur le CD-ROM d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Désactivez toutes les options sélectionnées. Si vous ne le faites pas, vous risquez d'installer des logiciels dont vous n'avez pas besoin.  
  
4.  Développez **des logiciels supplémentaires**, puis sélectionnez le **BAM-événements** case à cocher.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Cliquez sur **Installer**.  
  
7.  Lorsque la procédure d’installation est terminée, cliquez sur **OK**.  
  
     Le logiciel BAM-Événements est maintenant installé.  
  
> [!NOTE]
>  L'installation de la bibliothèque d'intercepteurs BAM à l'aide de cette méthode ne requiert pas l'achat de licences supplémentaires.  
  
 Si vous souhaitez surveiller les données des compteurs de performance des intercepteurs BAM, vous devez d'abord les enregistrer à l'aide du fichier InstallUtil.exe.  
  
### <a name="to-register-bam-interceptor-performance-counters-by-using-installutilexe"></a>Pour enregistrer des compteurs de performance d'intercepteur BAM à l'aide du fichier InstallUtil.exe  
  
1.  Démarrer  **[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes** en tant qu’administrateur.  
  
2.  À l'invite de commande, entrez la commande suivante :  
  
     InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll  
  
3.  Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.  
  
     Les compteurs de performance d'intercepteur BAM ne sont pas disponibles.  
  
> [!NOTE]
>  Par défaut, seuls les administrateurs et certains comptes système sont autorisés à enregistrer les données de performance. Pour activer l'accès sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], ajoutez le compte utilisé pour l'exécution des applications de workflow au groupe Utilisateurs du journal de performance.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de Solutions BAM](../core/implementing-bam-solutions.md)   
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)