---
title: Importer l’adaptateur BizTalk pour JD Edwards OneWorld | Documents Microsoft
description: Importez le fichier de liaison d’application et passer en revue les limitations de l’adaptateur JD Edwards OneWorld dans BizTalk Server
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f308d2fe-39dd-4008-94ed-292c4c26fe06
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4a452d61b3bdb5f5d0fee9e0916811645938d70
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a>Importez l’application JD Edwards EnterpriseOne
  
## <a name="overview"></a>Vue d'ensemble
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible. BizTalk Server exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.  
  
 Vous pouvez utiliser BizTalk Server pour effectuer les tâches suivantes :  
  
-   déploiement ou suppression des assemblys BizTalk Server dans une base de données de configuration BizTalk ;  
  
-   Installer ou désinstaller des assemblys dans le global assembly cache (GAC)  
  
-   importation/exportation des informations de liaison des assemblys BizTalk Server vers/à partir de fichiers de liaison.  

Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld requiert l'installation de Visual Studio sur un ordinateur (de développement) source. Visual Studio n'est pas requis sur l'ordinateur de production.  

## <a name="confirm-your-setup"></a>Vérifiez votre configuration
Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards. Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme *****. Consultez **Limitations** dans cette rubrique.

  
> [!NOTE]
>  Déploiement remplace la configuration de l’emplacement de réception. Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.  
  
  
## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible
Déploiement remplace la configuration d’emplacement de réception. Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
Par exemple, à une invite de commandes, exécutez :  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="limitations"></a>Limitations
Le mot de passe d’adaptateur de Transport est stocké sous forme d’astérisques (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par l’Assistant Déploiement BizTalk et est transmis à la gestion composant dans le même format. Avant d'importer le fichier de liaison, vous devez le modifier en remplaçant les astérisques par des valeurs alphanumériques aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page après l’importation du fichier de liaison.  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.  
  
> [!NOTE]
>  Lors de l’importation d’un fichier .msi dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application contenant des informations de liaison pour un adaptateur d’entreprise, vous pouvez recevoir un message d’erreur d’importation. Un correctif est disponible auprès de Microsoft, ainsi qu’une description complète de l’erreur à [ http://support.microsoft.com/kb/923733/en-us ](http://support.microsoft.com/kb/923733/en-us).  
  
### <a name="work-around-the-password-limitation"></a>Contourner la limitation de mot de passe  

**Option 1**  

- Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par du texte brut.  
  
    > [!CAUTION]
    >  Cette opération n'est pas recommandée pour des raisons de sécurité.  
  
- Avant d’importer, mettre à jour le fichier de liaison en remplaçant les astérisques par des valeurs aléatoires (c'est-à-dire, pas le mot de passe). Après avoir importé, entrez le mot de passe correct à l’aide de la **propriétés du Transport**.  
  
    > [!NOTE]
    >  Cette solution de contournement peut être utilisée uniquement si Microsoft Visual Studio est installé sur l’ordinateur cible ou en développant un outil personnalisé.  
  
**Option 2**  
  
1.  Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe. Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.  
  
2.  Vérifiez le système logique et les services de transmission et de réception.  

## <a name="next-steps"></a>Étapes suivantes
[Utiliser BizTalk Server des exceptions dans votre orchestration](../core/using-biztalk-server-exception-handling1.md)