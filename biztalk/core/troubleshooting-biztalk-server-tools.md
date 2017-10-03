---
title: "Dépannage des outils de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 038a5f5c-d6eb-42db-88d6-70f3deba7a8a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7aedd8977042d15176781b0595bd5bb225a2fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-tools"></a>Dépannage des outils BizTalk Server
Cette rubrique centralise les informations sur les problèmes connus rencontrés lors de l'utilisation des outils inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="known-issues"></a>Problèmes connus  
  
### <a name="biztalk-server-tools-and-utilities-may-not-function-correctly-on-a-windows-system-that-supports-uac"></a>Les outils et utilitaires BizTalk Server peuvent ne pas fonctionner correctement sous un système Windows prenant en charge le contrôle de compte d'utilisateur  
 **Problème**  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur un système prenant en charge le contrôle de compte d'utilisateur, les outils inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent ne pas se lancer ou ne pas fonctionner correctement.  
  
 **Cause**  
  
 Dans le cadre de l'exécution d'une application associée à un niveau de privilège spécifique, si le niveau requis est supérieur à celui de l'utilisateur qui exécute l'application, le contrôle de compte d'utilisateur affiche une invite permettant d'élever provisoirement le privilège de l'application au niveau requis. Les outils intégrés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne sont pas associés aux indicateurs adéquats pour demander automatiquement une élévation de privilège. C'est pourquoi ils tentent de s'exécuter avec le niveau de privilège actuel de l'utilisateur exécutant l'application et échouent si un niveau de privilège supérieur est requis.  
  
 **Résolution**  
  
 Pour résoudre ce problème, exécutez tous les outils BizTalk Server avec des privilèges d'administrateur. Pour exécuter un outil avec des privilèges d’administrateur, cliquez sur l’application, puis sélectionnez **exécuter en tant qu’administrateur**.  
  
 Pour plus d’informations sur le contrôle de compte d’utilisateur, consultez [http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167).  
  
### <a name="sometimes-biztalk-mapper-toolbox-may-appear-empty"></a>La boîte à outils du Mappeur BizTalk apparaît parfois comme étant vide  
 **Problème**  
  
 Parfois, lorsque vous ouvrez la boîte à outils du Mappeur dans Visual Studio, celle-ci ne contient aucun fonctoid.  
  
 **Cause**  
  
 Il se peut que des éléments soient endommagés lors de l'installation/désinstallation des compléments et/ou correctifs de Visual Studio.  
  
 **Résolution**  
  
 Pour rectifier ce problème :  
  
1.  Fermez toutes les instances en cours d’exécution de Visual Studio.  
  
2.  Démarrer **invite de commandes Visual Studio** en tant qu’administrateur.  
  
3.  À l'invite de commandes, tapez la commande suivante :  
  
    ```  
    devenv.exe /setup  
    ```