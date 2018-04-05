---
title: Boîte de dialogue Propriétés du Transport PeopleSoft | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PeopleSoft
helpviewer_keywords:
- PeopleSoft Transport Properties dialog box
ms.assetid: 660f0a0b-e076-4f4e-8b2a-6d976acfc5ce
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50362e60b982a2d304efea8c26f58019148e5c16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-transport-properties-dialog-box"></a>Boîte de dialogue Propriétés du transport PeopleSoft
La boîte de dialogue Propriétés du transport PeopleSoft permet de définir les propriétés obligatoires de l'adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Propriétés obligatoires de l’adaptateur**||  
|Chemin d'accès au serveur de l'application|Tapez le chemin d’accès pour le serveur de PeopleSoft (par exemple, `//psserver.domain.com:9000`).|  
|JAVA_HOME|Tapez le nom de l’emplacement JAVA_HOME (par exemple, `<drive:>\jdk1.4.2_08`).|  
|Mot de passe|Tapez le mot de passe de l'utilisateur.|  
|Fichiers JAR PeopleSoft 8.x|Tapez le chemin d’accès pour l’emplacement des fichiers JAR PeopleSoft (par exemple, `<drive:>\JAR_FILES\Peoplesoft_8.4\psjoa.jar`).|  
|Nom d'utilisateur|Tapez le nom de l’utilisateur, puis cliquez sur **OK**.|  
|**Paramètres supplémentaires**||  
|Format de date de la base de données|Tapez le format dans lequel vous souhaitez que l’affichage des dates (par exemple,**AAAA-MM-jj**).<br /><br /> Le format de la date est différent si celle-ci est utilisée comme une clé.|  
|**Contrôle de l’accès concurrentiel**||  
|Nombre maximal d'appels simultanés|Tapez une valeur numérique pour le **nombre maximal d’appels simultanés**. Ce nombre correspond au nombre maximal d'appels simultanés (par exemple, 200).<br /><br /> La valeur par défaut de ce champ est -1, ce qui correspond à l'absence de protection.|  
|**Connexion**||  
|Nombre maximal de sessions|Tapez un nombre représentant le nombre maximal de sessions.<br /><br /> Le nombre de connexions par défaut est 40.|  
|**Actualiser l’Agent**||  
|Actualiser l'agent|Sélectionnez **Oui** pour le **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.<br /><br /> Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion avec le serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur.|  
|**L’authentification unique**||  
|Application associée|Sélectionnez l’application associée dans la liste uniquement si vous utilisez l’authentification unique (SSO).|  
|Utiliser SSO|Sélectionnez **Oui** si vous utilisez l’authentification unique ; un mot de passe n’est pas obligatoire dans ce cas. **Remarque :** si vous avez déjà entré un mot de passe et que vous souhaitez utiliser l’authentification unique, cliquez sur le mot de passe champ et sélectionnez **annuler le mot de passe**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’interface utilisateur de l’adaptateur BizTalk pour PeopleSoft Enterprise](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md)