---
title: "Boîte de dialogue Propriétés de JD Edwards OneWorld Transport | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JDEOneWorld
helpviewer_keywords: Transport Properties dialog box [JD Edwards OneWorld adapters]
ms.assetid: 34d6b5d0-4bd9-4522-a540-8415d3143762
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dd6f1be076a8d5bc02942e55dc5e5fa88640ae6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="jd-edwards-oneworld-transport-properties-dialog-box"></a>Boîte de dialogue Propriétés du transport JD Edwards OneWorld.
La boîte de dialogue Propriétés du transport JD Edwards OneWorld permet de définir les propriétés obligatoires de l'adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Propriétés obligatoires de l’adaptateur**||  
|Hôte|Tapez le nom de l’ordinateur du serveur hôte (par exemple, `actsvr1`).<br /><br /> --ou--<br /><br /> Tapez l’adresse IP de l’ordinateur (par exemple, `123.456.0.789`).|  
|JAVA_HOME|Tapez le chemin d’accès complet à votre installation JDK.|  
|Environnement JDEdwards|Tapez le nom d’un environnement de JD Edwards OneWorld (par exemple, `DV7333`).<br /><br /> DV7333 correspond à un nom commun d'environnement de développement, PY7333 au nom commun de l'environnement de prototype et PD7333 au nom commun de l'environnement de production.|  
|Fichiers JAR JDEdwards|Entrez le nom complet du fichier et du chemin d'accès pour chaque fichier JAR :<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br />-BTSLIBInterop.jar<br /><br /> Chaque fichier jar doit être séparé par un point-virgule ( ;) et aucun espace (par exemple, `<c:>\Connector.jar;<c:>\Kernel.jar;`).|  
|Mot de passe|Tapez un mot de passe utilisateur. Si vous n'utilisez pas l'authentification unique (SSO), vous devez alors définir des paramètres d'informations d'identification pour l'adaptateur BizTalk pour JD Edwards OneWorld afin d'accéder au système du serveur. Le mot de passe correspond au nom d'utilisateur. Le mot de passe détermine les privilèges qui que vous sont octroyées lors de l’accès à la base de données.|  
|Port|Tapez l’identificateur numérique de l’envoi ou de port de réception (par exemple, `6009`).|  
|Nom d'utilisateur|Tapez le nom de l’utilisateur, puis cliquez sur **OK**.|  
|Nombre maximal d'appels simultanés|Tapez une valeur numérique pour le **nombre maximal d’appels simultanés**. Ce nombre représente le nombre maximal d’appels simultanés, par exemple, **10**.<br /><br /> La valeur par défaut pour ce champ est **5**, ce qui signifie aucune protection se produit.|  
|Actualiser l'agent|Sélectionnez **Oui** pour le **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.<br /><br /> Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.|  
|Application associée|Sélectionnez l'application associée dans la liste uniquement si vous utilisez l'authentification unique.|  
|Utiliser SSO|Sélectionnez **Oui** si vous utilisez l’authentification unique ; un mot de passe n’est pas obligatoire dans ce cas.|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on3.md)   
 [Création d’Applications associées](../core/creating-affiliate-applications3.md)   
 [Référence de l’interface utilisateur de l’adaptateur BizTalk pour JDE OneWorld](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md)