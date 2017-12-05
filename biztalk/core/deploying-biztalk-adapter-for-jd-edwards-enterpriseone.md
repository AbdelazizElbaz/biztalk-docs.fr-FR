---
title: Importer des applications JD Edwards EnterpriseOne | Documents Microsoft
description: "Confirmer l’installation, importez le fichier de liaison d’application et examiner les limitations de l’adaptateur JD Edwards EnterpriseOne dans BizTalk Server"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 852f948b-48ba-4ae2-b1eb-7c88c1542a52
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55374c87192c993e26cc11cb496d89074d527868
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="import-the-jd-edwards-enterpriseone-application"></a>Importez l’application JD Edwards EnterpriseOne
  
## <a name="overview"></a>Vue d'ensemble
Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :  
  
-   Déployer ou supprimer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys dans une base de données de Configuration de BizTalk  
  
-   Installer ou désinstaller des assemblys dans le global assembly cache (GAC)  
  
-   Importer ou exporter des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations de liaison d’assembly vers et à partir de fichiers de liaison  
  
Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert l'installation de Visual Studio sur un ordinateur (de développement) source. Visual Studio n'est pas requis sur l'ordinateur de production.  

## <a name="confirm-your-setup"></a>Vérifiez votre configuration
Avant d'utiliser le serveur BizTalk pour importer un fichier de liaison, vous devez vérifier les éléments suivants se réalisent :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards EnterpriseOne. Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les mots de passe du système JD Edwards EnterpriseOne, si cette option a été définie dans la configuration, sont enregistrés en tant que ***** dans le fichier de liaison. Pour plus d’informations, consultez **Limitations** dans cette rubrique.

## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible
Lors du redéploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur réimportation.  
  
Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration. Si Visual Studio n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  

Par exemple, à l'invite de commandes, exécutez :  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
## <a name="limitations"></a>Limitations
Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoile (*) dans le fichier de liaison exporté par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et transmis au composant de gestion dans le même format. Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné).  
  
 Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. La prochaine fois que le fichier vous permet d’importer les informations de liaison, vous devez entrer les mots de passe en utilisant l’interface utilisateur des pages propriété transport.  
  
 Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe du fichier de liaison une fois l'opération d'importation terminée.  
  
### <a name="work-around-the-password-limitation"></a>Contourner la limitation de mot de passe  
  
1.  Utilisez l'authentification unique de l'entreprise plutôt que des mots de passe. Outre l'importation du fichier de liaison, l'utilisation de l'option d'authentification unique n'implique pas d'autres opérations.  
  
2.  Vérifiez le système logique et les services de transmission et de réception.  


## <a name="next-steps"></a>Étapes suivantes
[Utiliser BizTalk Server des exceptions dans votre orchestration](../core/using-biztalk-server-exception-handling3.md)