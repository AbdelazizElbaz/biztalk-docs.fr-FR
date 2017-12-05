---
title: Importer des applications PeopleSoft | Documents Microsoft
description: "Utiliser un fichier de liaison XML à importer vos applications de l’adaptateur PeopleSoft dans BizTalk Server et lire toutes les restrictions lors de l’importation"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f53d1b4-e1df-41ff-b554-1bb1d20b9111
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed076bd238eff5106bb0b2f08449144d922fed4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploy-biztalk-adapter-for-peoplesoft-enterprise"></a>Déployez l’adaptateur BizTalk pour PeopleSoft Enterprise
Cette section fournit des informations sur le déploiement de l'adaptaeur BizTalk pour PeopleSoft Enterprise.  

## <a name="overview"></a>Vue d'ensemble
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'effectuer les tâches suivantes :  
  
-   déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;  
  
-   installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;  
  
-   importation/exportation des informations de liaison des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers/à partir de fichiers de liaison.  
  
Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise requiert l'installation de Visual Studio sur un ordinateur (de développement) source. Visual Studio n'est pas requis sur l'ordinateur de production.  

## <a name="confirm-your-setup"></a>Vérifiez votre configuration
Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft. Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****. Consultez **Limitations** dans cette rubrique.

> [!NOTE]
>  Le déploiement remplace la configuration de l'emplacement de réception. Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
 Pour obtenir des instructions sur l’importation de fichiers de liaison, consultez [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md). 
  
## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible
Pour nettoyer l’ordinateur cible pour le déploiement de la nouvelle application, supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**  
  
Par exemple, à une invite de commandes, exécutez :  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## <a name="limitations"></a>Limitations
Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (*) dans le fichier de liaison exporté par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison à l’issue de l’opération d’importation.  
  

### <a name="work-around-the-password-limitation"></a>Contourner la limitation de mot de passe  

**Option 1**   
  
-   Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par du texte brut.  
  
    > [!CAUTION]
    >  Cette pratique n'est pas recommandée pour des raisons de sécurité.  
  
-   Avant d’importer, mettre à jour le fileby de liaison en remplaçant les astérisques par des valeurs aléatoires (c'est-à-dire, pas le mot de passe). Après avoir importé, entrez le mot de passe correct dans la **propriétés du Transport** dans Administration de BizTalk Server.  
  
    > [!NOTE]
    >  Cette solution de contournement ne peut être utilisée que si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur cible ou en développant un outil personnalisé.  
  
**Option 2**  
  
-   Utilisez l'authentification unique de l'entreprise (SSO) plutôt que des mots de passe. L'utilisation de l'option SSO nécessite l'importation d'un fichier de liaison.  
  
- Vérifiez le système logique et le transmettre et recevoir des services. 
  
## <a name="next-steps"></a>Étapes suivantes
[Utiliser BizTalk Server des exceptions dans votre orchestration](../core/using-biztalk-server-exception-handling2.md)