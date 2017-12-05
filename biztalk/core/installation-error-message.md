---
title: "Message d’erreur installation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation, error message
- error messages, installation
ms.assetid: 593b033f-03da-43ae-a948-f87aa5e4bccd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ec99a2e9f20b09c4daddad0336037c7f539782a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="installation-error-message"></a>Message d'erreur relatif à l'installation
Après avoir installé l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service, la définition d'un emplacement d'envoi et de réception qui lui sont associés risque d'entraîner l'erreur suivante :  
  
 Le moteur de messagerie Impossible d’ajouter une URL de réception «\< envoi/réception\>» à l’adaptateur « TIBCO EMS ». Raison : « assembly nom de fichier ou TIBCO. EMS, ou une de ses dépendances, est introuvable. »  
  
## <a name="possible-causes"></a>Causes possibles  
 Cette erreur provient généralement d'une des causes suivantes.  
  
### <a name="assembly-not-in-gac"></a>L'assembly ne se trouve pas dans le GAC  
 L’adaptateur BizTalk pour TIBCO EMS est une application .NET Framework et utilise l’assembly .NET Framework, TIBCO. EMS. Cet assembly doit être présent dans le .NET Framework global assembly cache (GAC) pour le .NET Framework se trouve en cours d’exécution.  
  
#### <a name="solution"></a>Solution  
 Pour déterminer si l'assembly est présent dans le GAC ou non, ouvrez une invite de commandes, puis tapez la commande suivante :  
  
 `GACUTIL /L TIBCO.EMS`  
  
 Si le résultat n'affiche aucun élément, vous devez ajouter l'assembly au GAC. Pour ce faire, ouvrez une invite de commandes, accédez au répertoire client/cs de l'installation de TIBCO EMS (l'emplacement d'installation par défaut est C:\TIBCO\EMS\Clients\CS), puis exécutez la commande suivante :  
  
 `GACUTIL /i TIBCO.EMS.DLL`  
  
### <a name="different-version-of-assembly-in-gac"></a>Version de l'assembly différente dans le GAC  
 L'assembly TIBCO.EMS.dll est présent dans le GAC, mais il s'agit d'une version différente de celle utilisée pour créer l'adaptateur BizTalk pour TIBCO EMS. Si l'assembly TIBCO.EMS installé sur l'ordinateur provient d'une version 4.2 ou supérieure, il doit être compatible avec la version utilisée pour créer l'adaptateur (vous pouvez vérifiez cette information avec TIBCO).  
  
#### <a name="solution"></a>Solution  
 Le .NET Framework fournit une méthode permettant de contourner ce problème. Il est appelé *la redirection de liaison*, qui utilise un fichier de configuration.  
  
 Suivez la procédure suivante pour éliminer le message d'erreur :  
  
1.  À l'aide d'un éditeur de texte, ouvrez le fichier BTSNTSVC.exe.config.  
  
     Ce fichier est situé dans le répertoire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (l'emplacement d'installation par défaut est [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).  
  
2.  Ajoutez l’entrée suivante au fichier BTSNTSVC.exe.config, en tant qu’enfant de la \<assemblyBinding\> élément :  
  
```  
<dependentAssembly>  
    <assemblyIdentity name='TIBCO.EMS'  
        publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
    <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
        newVersion='1.0.0.0' />  
</dependentAssembly>  
```  
  
 Si le fichier BTSNTSVC.exe.config n’a pas été préalablement modifié, le \<assemblyBinding\> élément ne peut pas ressembler à ceci :  
  
```  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
    <probing privatePath="BizTalk Assemblies;Developer  
        Tools;Tracking;Tracking\interop" />  
    <dependentAssembly>  
        <assemblyIdentity name='TIBCO.EMS'  
            publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
        <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
            newVersion='1.0.0.0' />  
    </dependentAssembly>  
</assemblyBinding>  
```  
  
1.  Dans une invite de commandes, tapez la commande : `GACUTIL /L TIBCO.EMS`.  
  
2.  Copiez le numéro de version de l'assembly TIBCO.EMS à partir de la sortie.  
  
    > [!CAUTION]
    >  Deux numéros de version s’affichent : un est le numéro de version de l’utilitaire gacutil. Vous souhaitez que le deuxième numéro de version, il apparaît juste après **Version =**.  
  
3.  Collez le numéro de version dans le fichier BTSNTSVC.exe.config, entre guillemets, juste après **newVersion =** (gras les caractères dans l’exemple XML précédent).  
  
4.  Enregistrez le fichier BTSNTSVC.exe.config modifié.  
  
5.  Redémarrez l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de TIBCO Enterprise Message Service](../core/troubleshooting-tibco-enterprise-message-service.md)