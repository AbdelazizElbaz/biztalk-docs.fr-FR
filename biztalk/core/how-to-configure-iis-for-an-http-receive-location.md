---
title: "Configuration d’IIS pour l’emplacement de réception HTTP | Documents Microsoft"
description: "Créer l’application de réception HTTP BTS dans IIS et de tester les paramètres de pool d’applications dans BizTalk Server"
ms.custom: 
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e09768d6616a33a4900995f3dd3225fa34318b3c
ms.sourcegitcommit: 75d35f6f230f0846c29a4b146c6d5b074e60b13c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="configure-iis-for-an-http-receive-location"></a>Configuration d’IIS pour l’emplacement de réception HTTP
Utilisations de l’emplacement de réception HTTP une application dans Internet Information Services (IIS). Emplacement dans les services IIS de réception de cette rubrique répertorie les étapes pour activer le protocole HTTP. 

Selon votre système d’exploitation, les étapes de configuration de l’application IIS peuvent varier. Utilisez ces étapes comme guide, comme l’interface utilisateur peut être différent sur votre système d’exploitation.
  
## <a name="32-bit-vs-64-bit"></a>éditions 32 bits et 64 bits

Emplacement utilise le BTSHTTPReceive.dll de réception HTTP. Il existe une version 32 bits et une version 64 bits de la DLL. Vous choisissez la version que vous souhaitez utiliser. processus 64 bits ont plus de mémoire disponible, par conséquent, si vous traitez des messages plus volumineux, la version 64 bits peut être préférable. 

**emplacement d’installation 32 bits**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive*.
**emplacement d’installation 64 bits**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive64*

Pour exécuter la version 64 bits du HTTP adaptateur de réception en mode natif de 64 bits, ouvrez une invite de commandes et exécuter les scripts suivants :  

1. Type :`cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  

2. Type :`C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide. Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.  
  
##  <a name="configure-the-iis-application"></a>Configurer l’application IIS
  
1.  Ouvrez **Internet Information Services** (ouvrir **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **Gestionnaire des Services Internet**). 
  
2.  Dans IIS, sélectionnez le nom de votre serveur. Dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires**. Dans le volet Actions, sélectionnez **ajouter un mappage de scripts**.  
  
    > [!NOTE]
    >  Lorsque vous configurez le mappage du script au niveau du serveur web-, le mappage s’applique à tous les sites web. Si vous souhaitez limiter le mappage vers un site Web spécifique ou d’un dossier virtuel, sélectionnez ce site web ou un dossier et puis ajoutez le mappage de script.  
  
3.  Dans **ajouter un mappage de scripts**, sélectionnez **chemin d’accès de la demande**et le type `BtsHttpReceive.dll`.  
  
4.  Dans **exécutable**, sélectionnez les points de suspension (**...** ), puis accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive. Sélectionnez **BtsHttpReceive.dll**, puis sélectionnez **ouvrir**.  
  
5.  Dans **nom**, entrez `BizTalk HTTP Receive`, puis sélectionnez **Restrictions des demandes**. Dans la fenêtre :
  
    1. Dans **verbes**, sélectionnez **un des verbes suivants**, puis entrez `POST`.  
  
    2. Dans **accès**, sélectionnez **Script**, puis sélectionnez **OK**.  
  
    3. Lorsque vous êtes invité à autoriser l’extension ISAPI, sélectionnez **Oui**.  
  
6. Créer un nouveau pool d’applications (avec le bouton droit **Pools d’applications**, sélectionnez **ajouter le pool d’applications**). **Nom** votre pool d’applications (telles que `BTSHTTPReceive`), sélectionnez **.NET Framework v4.0.30319**, puis sélectionnez **OK**.  
  
    > [!NOTE]
    >  Le numéro de version .NET peut varier selon la version de .NET Framework installée sur l’ordinateur.  
  
     Le pool d’applications est répertorié.  
  
7. Sélectionnez votre nouveau pool d’applications, puis ouvrez le **paramètres avancés** (**Actions** volet). Dans la fenêtre :

    - **Activer l’Application 32 bits**: la valeur **True** si vous avez choisi de 32 bits **BtsHttpReceive.dll**
    - **Modèle de processus** section, **identité**: sélectionnez les points de suspension (**...** ), sélectionnez **compte personnalisé**, puis **définir** à un compte qui est membre de la **utilisateurs d’hôtes BizTalk isolés** et **IIS_WPG** groupes. Sélectionnez **OK**. 
  
8. Ajoutez une nouvelle application pour le site web (avec le bouton droit le **Site Web par défaut**, sélectionnez **ajouter une Application**). Dans la fenêtre :
  
    1. **Alias** : entrez un alias que vous associez à l’application (tel que `BTS HTTP Receive`, puis **sélectionnez**.  
    2. Sélectionnez le nouveau pool d’applications que vous venez créé, puis **OK**.  
    3. **Chemin d’accès physique**: sélectionnez les points de suspension (**...** ), puis accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.  
    4. **Paramètres de test** vérifier aucun message d’erreur dans le **tester la connexion** boîte de dialogue. **Fermer**, puis sélectionnez **OK**.  
  
    > [!TIP]
    > Si les paramètres de Test renvoie un avertissement, l’identité du pool d’applications est absent des autorisations pour un dossier ou accès à un groupe. En tant qu’étape de dépannage, sélectionnez **connecter en tant que**, entrez la **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs. 

9. La nouvelle application s’affiche est répertorié sous **Sites Web par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer les emplacement de réception HTTP](../core/how-to-configure-an-http-receive-location.md)
