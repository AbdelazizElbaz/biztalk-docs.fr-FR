---
title: "Autorisations requises pour déployer et gérer une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], security
- permissions, EDI adapters
- deploying, security
- security, applications
- security, EDI adapters
- assemblies, permissions
- permissions, deploying
- EDI adapters, security
- permissions, assemblies
- security, assemblies
- permissions, applications
- deploying, permissions
- applications, importing
- applications, exporting
- permissions, exporting
- installing, permissions
- applications, security
- security, permissions
- applications, installing
- assemblies, security
- managing, security
ms.assetid: 4a459ff1-661d-403a-99e0-d54b82e008d0
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 608da93cd1960d26304f4dcebe239367de2404e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="permissions-required-for-deploying-and-managing-a-biztalk-application"></a>Autorisations nécessaires au déploiement et à la gestion d'une application BizTalk
Le déploiement d'une application consiste à déployer des assemblys BizTalk à partir de Visual Studio, ainsi qu'à importer, exporter et installer des applications BizTalk. Les autorisations de base nécessaires à la réalisation de ces tâches sont les suivantes :  
  
-   En tant que membre du groupe d'administrateurs BizTalk Server, vous disposez des autorisations nécessaires au déploiement des assemblys BizTalk à partir de Visual Studio.  
  
-   En tant que membre du groupe d'administrateurs BizTalk Server, vous disposez des autorisations nécessaires à l'importation des applications BizTalk dans un groupe BizTalk. Si l'option permettant d'ajouter un assembly inclus dans l'application au Global Assembly Cache (GAC) lors de l'importation a été spécifiée, vous devez également disposer des autorisations en écriture sur le dossier de l'assembly. Si vous faites partie du groupe Administrateurs locaux, cette autorisation vous est déjà accordée.  
  
-   En tant que membre du groupe d'administrateurs BizTalk Server ou du groupe des opérateurs BizTalk Server, vous disposez des autorisations nécessaires pour :  
  
    -   exporter des applications BizTalk ;  
  
    -   démarrer et arrêter des ports d'envoi, des groupes de ports d'envoi et des orchestrations ;  
  
    -   activer et désactiver des emplacements de réception ;  
  
    -   interrompre, reprendre et terminer des instances ;  
  
    -   démarrer et arrêter des applications.  
  
-   En tant que membre du groupe Administrateurs locaux, vous êtes habilité à installer des applications BizTalk sur l'ordinateur local.  
  
 Vous avez la possibilité de restreindre les droits des utilisateurs pour la réalisation de ces tâches. Vous trouverez davantage de détails sur les autorisations requises dans les sections suivantes.  
  
-   [Autorisations pour déployer les assemblys BizTalk à partir de Visual Studio](#BKMK_Permissions_for_deploying)  
  
-   [Autorisations permettant d’importer une application](#BKMK_Permissions_for_importing)  
  
-   [Autorisations permettant d’exporter une application](#BKMK_Permissions_for_exporting)  
  
-   [Autorisations pour l’installation d’une application](#BKMK_Permissions_for_installing_an_application)  
  
##  <a name="BKMK_Permissions_for_deploying"></a>Autorisations pour déployer les assemblys BizTalk à partir de Visual Studio  
 Pour déployer des assemblys BizTalk à partir de Visual Studio, vous devez au moins disposer des autorisations en écriture sur la base de données de gestion BizTalk. Cette autorisation vous est octroyée d'office si vous appartenez au groupe d'administrateurs BizTalk Server.  
  
##  <a name="BKMK_Permissions_for_importing"></a>Autorisations permettant d’importer une application  
 Pour importer une application BizTalk, vous devez au moins disposer des autorisations énumérées ci-après. Si vous appartenez au groupe Administrateurs BizTalk Server, toutes ces autorisations vous sont acquises, à l'exception de celle vous permettant d'installer des assemblys dans le GAC. Pour cette opération, des autorisations en écriture sur le dossier de l'assembly sont indispensables.  
  
|Élément|Permissions|Obligatoire ?|  
|----------|-----------------|-------------------|  
|Base de données de gestion BizTalk|Lecture/Écriture|Toujours obligatoire.|  
|Base de données du moteur de règles BizTalk|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources de règles.|  
|Base de données BAM|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources BAM.|  
|Global Assembly Cache (GAC)|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources d'assemblys et que vous souhaitiez les ajouter dans le GAC lors de l'importation. (Voir la remarque ci-dessous.)|  
  
> [!NOTE]
>  Lorsque vous importez un assembly à l'aide de l'Assistant Importation, vous avez la possibilité d'ajouter l'assembly au Global Assembly Cache (GAC). Dans ce cas, vous devez disposer de l'autorisation en écriture sur le dossier de l'assembly. Pour plus d’informations sur le dossier de l’assembly, consultez [autorisations pour l’installation d’une application](#BKMK_Permissions_for_installing_an_application).  
>   
>  Si votre application comprend un script permettant de déployer des éléments autres que ceux répertoriés ici, il vous faudra également disposer des autorisations correspondantes.  
  
##  <a name="BKMK_Permissions_for_exporting"></a>Autorisations permettant d’exporter une application  
 Pour exporter une application BizTalk, vous devez au moins disposer des autorisations énumérées ci-après. Ces autorisations vous sont octroyées d'office si vous appartenez au groupe des opérateurs BizTalk.  
  
|Élément|Permissions|Obligatoire ?|  
|----------|-----------------|-------------------|  
|Base de données de gestion BizTalk|Lecture|Toujours obligatoire.|  
|Base de données du moteur de règles BizTalk|Lecture|Obligatoire uniquement si l'application comporte des ressources de règles.|  
|Magasin de certificats|Lecture|Obligatoire uniquement si l'application comporte des ressources de certificats.|  
|Services Internet (IIS)|Lecture|Obligatoire uniquement si l'application comporte des ressources de répertoire virtuel.|  
  
##  <a name="BKMK_Permissions_for_installing_an_application"></a>Autorisations pour l’installation d’une application  
 Par défaut, les membres du groupe Administrateurs locaux sont habilités à installer des applications BizTalk sur l'ordinateur local. Pour restreindre les droits des utilisateurs devant procéder à l'installation d'applications, reportez-vous au tableau ci-après. Il contient les autorisations minimales à configurer. Si votre application comporte des ressources autres que celles indiquées ici (par exemple, pour créer une base de données ou une table de base de données), il vous faudra également disposer des autorisations correspondantes.  
  
|Élément|Permissions|Obligatoire ?|  
|----------|-----------------|-------------------|  
|Magasin de certificats|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources de certificats.|  
|Services Internet (IIS)|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources de répertoire virtuel.|  
|GAC|Lecture/Écriture|Obligatoire uniquement si l'application comporte des ressources d'assemblys et que vous souhaitiez les ajouter dans le GAC lors de l'installation. (Voir la remarque ci-après.)|  
|Système de fichiers|Lecture/Écriture|Obligatoire uniquement si une propriété de destination a été définie pour une ressource.|  
|Registre|Lecture/Écriture|Obligatoire si le **regsvcs** ou **regasm**est définie sur True pour une ressource d’assembly contenant gérés par des composants COM ou COM +.|  
|Registre|Lecture/Écriture|Obligatoire si l'application comporte des ressources COM non gérées.|  
  
> [!NOTE]
>  À partir de la console Administration de BizTalk Server, vous avez la possibilité d'ajouter un assembly au GAC lors de l'installation de l'application (pour cela, cliquez avec le bouton droit sur l'assembly dans le dossier des ressources, puis cliquez sur Modifier). Si vous faites ce choix, il vous faudra disposer de l'autorisation en écriture sur le dossier de l'assembly contenant le GAC pour pouvoir installer l'application BizTalk. Le chemin d'accès au dossier de l'assembly est le suivant : %SystemRoot%\assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité pour le déploiement d’Application](../core/security-considerations-for-application-deployment.md)