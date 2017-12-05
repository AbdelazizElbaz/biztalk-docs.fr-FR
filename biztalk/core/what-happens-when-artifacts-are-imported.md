---
title: "Que se passe-t-il quand les artefacts sont importés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing, artifacts
- artifacts, importing
ms.assetid: a83957df-6e16-419a-b693-87985b498cc4
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa252b520f985667820861403a46d39c8527ea07
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="what-happens-when-artifacts-are-imported"></a>Effets de l'importation d'artefacts
Cette rubrique décrit les effets de l'importation d'artefacts. Vous pouvez importer des artefacts de trois manières :  
  
-   Importation des artefacts d'un fichier .msi BizTalk dans un groupe ou une application BizTalk.  
  
-   Importation d'un fichier de stratégie .xml dans un groupe BizTalk.  
  
-   Importation d'un fichier de liaison dans un groupe ou une application BizTalk.  
  
## <a name="importing-a-biztalk-msi-file"></a>Importation d'un fichier .msi BizTalk  
 Lorsque vous importez un fichier .msi BizTalk dans un groupe ou une application BizTalk, BizTalk Server traite les artefacts qu'il contient comme suit :  
  
-   Si lors de l'importation vous avez ajouté une référence à partir de cette application ou d'autres applications du groupe, celle-ci est également ajoutée à la base de données de gestion BizTalk.  
  
-   Si vous avez spécifié cette option, les artefacts existants de l'application sont remplacés par ceux du fichier .msi ayant le même nom complet et numéro de version (le cas échéant).  
  
-   Si des fichiers de liaison ont été ajoutés à l'application, et que vous sélectionnez leur environnement cible lors de l'importation, les liaisons sont appliquées.  
  
-   Les scripts de prétraitement et de post-traitement configurés pour s'exécuter lors de l'importation s'exécuteront.  
  
-   Les données des artefacts basés sur des fichiers sont sérialisées et stockées dans la base de données de gestion BizTalk. Cela inclut les données relatives aux assemblys, répertoires virtuels, fichiers, scripts, certificats et artefacts BAM.  
  
    > [!IMPORTANT]
    >  Pour des raisons de sécurité, la clé privée est supprimée de chaque certificat lorsqu'il est exporté. En conséquence, aucune clé privée n'est stockée dans la base de données de gestion BizTalk.  
  
-   Les données de stratégie sont stockées dans la base de données du moteur de règles.  
  
-   Les artefacts BAM sont stockés dans la base de données d'importation principale BAM. Les définitions BAM sont déployées.  
  
-   Les assemblys BizTalk et .NET dont l'option de déploiement « Ajouter au Global Assembly Cache lors de l'importation du fichier MSI » est configurée sont ajoutés au GAC.  
  
> [!NOTE]
>  Les données d'artefact étant stockées dans les bases de données de BizTalk Server, lorsque vous exportez ultérieurement l'application dans un fichier .msi, BizTalk Server peut extraire de ces bases toutes les informations de configuration et données associées à l'application et à ses artefacts, puis les inclure dans le fichier .msi. Lorsque vous importez le fichier .msi dans un autre groupe BizTalk, toutes les donnés et informations de configuration d'artefact sont recréées dans le nouveau groupe.  
  
 Après avoir importé une application, vous pouvez afficher, gérer et déployer les artefacts de l'application en tant qu'entité unique ou individuellement à l'aide de la console Administration ou de BTSTask. Pour plus d’informations, consultez [déploiement d’Application et les outils de gestion](../core/application-deployment-and-management-tools.md).  
  
## <a name="importing-a-policy"></a>Importation d'une stratégie  
 Lorsque vous importez une stratégie à partir d'un fichier .xml, elle est ajoutée à la base de données du moteur de règles. À la différence de l'importation d'une stratégie dans un fichier .msi BizTalk, la stratégie n'est associée à aucune application de la base de données de gestion BizTalk. La stratégie s’affiche dans le nœud Stratégies de la \<tous les artefacts\> dossier dans la console Administration de BizTalk Server. Après avoir importé une stratégie, vous pouvez la publier afin qu'elle devienne accessible aux applications du groupe à utiliser. Pour plus d’informations, consultez [gestion des stratégies de](../core/managing-policies.md).  
  
## <a name="importing-a-binding-file"></a>Importation d'un fichier de liaison  
 Lorsque vous importez un fichier de liaison dans un groupe BizTalk, les liaisons qui existent déjà dans le groupe, dont le nom est le même que les liaisons du fichier, sont remplacées par les liaisons importées, et la configuration est appliquée.  
  
 Lorsque vous importez un fichier de liaison dans une application BizTalk, que ce soit individuellement ou dans le cadre d'une application, les liaisons qui existent déjà dans l'application, dont le nom est le même que les liaisons du fichier, sont remplacées par les liaisons importées, et la configuration est appliquée.  
  
> [!IMPORTANT]
>  Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception. Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il pour les artefacts au cours du déploiement](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Dépendances et déploiement des applications](../core/dependencies-and-application-deployment.md)