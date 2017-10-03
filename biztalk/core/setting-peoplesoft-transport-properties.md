---
title: "Définition des propriétés du Transport PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: 44b5f015-59f1-43a3-9673-a5ba40266843
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ecfd221d28312e84dcbaf7d8c83abc4f5191f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-peoplesoft-transport-properties"></a>Définition des propriétés du transport PeopleSoft
Les propriétés de transport PeopleSoft sont utilisées au moment de la conception et de l'exécution. Dans le **propriétés du Transport** boîte de dialogue, vous définissez les paramètres de connexion et les informations d’identification spécifique sur le système du serveur et les objets que vous essayez d’accéder.  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Développez les propriétés obligatoires de l'adaptateur et indiquez toutes les informations requises pour la connexion au serveur PeopleSoft.  
  
     Vous devez définir les paramètres de configuration afin de connecter l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise à PeopleSoft Enterprise. Ces données respectent la casse.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Application Server Path`|Chaîne représentant l'ordinateur et le port sur lesquels le serveur d'applications PeopleSoft est exécuté et à l'écoute. La syntaxe du chemin d’accès d’URL pour l’Application PeopleSoft 8 est / / < nom_ordinateur > :\<port >. Demandez à votre administrateur PeopleSoft pour le \<port > valeur. Le \<port > valeur est le JOLT port d’écoute de protocole, pas le port du serveur d’applications. Le port JOLT par défaut est 9000.|  
    |`JAVA_HOME`|Définissez la variable JAVA_HOME pointe vers votre installation JDK, par exemple : **C:\j2sdk1.4.2_08**.|  
    |`Password`|Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.<br /><br /> Chaîne représentant le mot de passe de l'utilisateur pour la connexion à un système PeopleSoft. Les caractères ne sont pas visibles, mais sont représentés par des astérisques (*).|  
    |`PeopleSoft 8.x Jar Files`|Pour utiliser des interfaces Ccmponent (PeopleSoft 8 uniquement), vous devez mettre à jour le paramètre CLASSPATH de façon à inclure le fichier jar de l'interface de composant pour PeopleSoft. Par exemple : **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**.|  
    |`User Name`|Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.<br /><br /> Chaîne représentant un nom d'utilisateur requis pour la connexion à un système PeopleSoft.|  
  
2.  Entrez un **des paramètres supplémentaires** de valeur lorsqu’une date est utilisée en tant que clé ; il a un format différent. Le format par défaut est JJ-MM-AAAA.  
  
3.  Entrez un **contrôle d’accès concurrentiel** valeur représentant le nombre d’appels, par exemple 200, dans **nombre maximal d’appels simultanés** si nécessaire.  
  
     Le **nombre maximal d’appels simultanés** paramètre active une protection contre la surcharge si le serveur principal ne peut pas traiter la quantité de données. Un appel simultané est une requête pour laquelle l'adaptateur n'a pas encore de réponse. Définissez **nombre maximal d’appels simultanés** dans les cas où le débit dépasse les capacités de traitement principal.  
  
     La valeur par défaut de ce champ est -1, ce qui correspond à l'absence de protection.  
  
     Si BizTalk Server envoie une demande pour l’adaptateur de transmission et le nombre d’appelle égal à ou dépasse la valeur définie pour **nombre maximal d’appels simultanés**, le thread qui soumet la demande est enregistrée jusqu'à ce que le d’appels simultanés nombre descend en dessous de la valeur définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’envoi PeopleSoft](../core/creating-peoplesoft-send-handlers.md)