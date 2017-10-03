---
title: "Boîte de dialogue Propriétés de JD Edwards EnterpriseOne Transport | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JDE
helpviewer_keywords: Transport Properties dialog box [JD Edwards EnterpriseOne adapters
ms.assetid: 6a37eeb2-af91-4f58-9699-7a7cbe296862
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21bbb6b4469399aa1952d0a9bdcc41ff7e14c842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="jd-edwards-enterpriseone-transport-properties-dialog-box"></a>Boîte de dialogue Propriétés du transport JD Edwards EnterpriseOne
La boîte de dialogue Propriétés du transport JD Edwards EnterpriseOne permet de définir les propriétés obligatoires de l'adaptateur.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Propriétés obligatoires de l’adaptateur**||  
|Hôte|Tapez le nom de l’ordinateur du serveur hôte (par exemple, `actsvr1`).<br /><br /> -ou-<br /><br /> Tapez l’adresse IP de l’ordinateur (par exemple, `123.456.0.789`).|  
|JAVA_HOME|Tapez le chemin d'accès complet à votre installation JDK (par exemple,<br /><br /> `C:\jdk1sdk1.4.2_07`).|  
|Environnement JDEdwards|Tapez le nom d’un environnement de JD Edwards EnterpriseOne (par exemple, `DV7333`).<br /><br /> DV7333 correspond à un nom commun pour l’environnement de développement ; PY7333 est courant pour l’environnement de prototype. et PD7333 est courant pour l’environnement de production.|  
|Fichiers JAR JDEdwards|Entrez le nom complet du fichier et du chemin d'accès pour chaque fichier JAR :<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br /><br /> Chaque fichier JAR doit être séparé par un point-virgule (;) et ne doit comporter aucun espace (par exemple,<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`).|  
|Mot de passe|Tapez un mot de passe utilisateur. Si vous le faites pas useSingle Sign-On (SSO), vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour JD Edwards EnterpriseOne accéder au système de serveur. Le mot de passe correspond au nom d'utilisateur. Il détermine les autorisations qui vous sont octroyées lors de l'accès à la base de données.|  
|Port|Tapez l’identificateur numérique de l’envoi ou de port de réception (par exemple, `6009`).|  
|Nom d'utilisateur|Tapez le nom de l’utilisateur, puis cliquez sur **OK**.|  
|**Propriétés de Source de données d’amorçage**||  
|Nom de la source de données|Tapez le nom de la source de données. Ce nom est obligatoire pour tous les types de données.|  
|Propriétaire de la base de données|Tapez le nom du propriétaire de la base de données|  
|Nom du serveur de base de données|Tapez le nom du serveur de base de données|  
|Port du serveur de base de données|Tapez le numéro d'identification du port du serveur de base de données|  
|Type de base de données|Tapez un seul caractère pour le type de base de données. Exemple :<br /><br /> **Je** -iSeries<br /><br /> **O** -Oracle<br /><br /> **S** -SQL Server<br /><br /> **L** -SQL Server OLEDB<br /><br /> **W** -UDB|  
|Nom de la base de données physique|Tapez le nom de la base de données physique. Ce nom est obligatoire pour tous les types de bases de données.|  
|**Contrôle de l’accès concurrentiel**||  
|Nombre maximal d'appels simultanés|Tapez une valeur numérique pour le **nombre maximal d’appels simultanés**. Ce nombre représente le nombre maximal d’appels simultanés, par exemple, **10**.<br /><br /> La valeur par défaut de ce champ est 5.|  
|**Actualiser l’Agent**||  
|Actualiser l'agent|Sélectionnez **Oui** pour le **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.<br /><br /> Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.|  
|**Serveur de sécurité**||  
|Nom du serveur de sécurité|Tapez le nom du serveur d'administration de la sécurité. Ce champ est facultatif et il contient par défaut l'hôte du serveur JD Edwards.|  
|Connexion Nom de service|Tapez le numéro du port utilisé par le serveur d'administration de la sécurité et par le mappage de la configuration de l'objet. La valeur par défaut est le port du serveur JD Edwards.|  
|**L’authentification unique**||  
|Application associée|Sélectionnez l’application associée dans la liste déroulante uniquement si vous utilisez Single Sign-On (SSO).|  
|Utiliser SSO|Sélectionnez **Oui** si vous utilisez l’authentification unique ; un mot de passe n’est pas obligatoire dans ce cas.|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on1.md)   
 [Création d’Applications associées](../core/creating-affiliate-applications4.md)   
 [Référence de l’interface utilisateur de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md)