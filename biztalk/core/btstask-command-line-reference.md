---
title: "Référence de ligne de commande BTSTask | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c350695-13e9-441a-9f1e-03cdc3e41328
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2de1e2e616b57d0cc8eda0cb9de9eae5c72d26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btstask-command-line-reference"></a>Informations techniques sur l'outil de ligne de commande BTSTask
Les rubriques de cette section contiennent des informations d'ordre technique relatives à l'outil de ligne de commande BTSTask inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez utiliser l'outil BTSTask pour effectuer de nombreuses tâches de déploiement des applications à partir d'une ligne de commande :  
  
-   Utilisez la commande AddApp pour ajouter une application BizTalk à la base de données de gestion BizTalk.  
  
-   Utilisez la commande AddResource pour ajouter un artefact à une application.  
  
-   Servez-vous de la commande ExportApp pour exporter une application et ses artefacts vers un fichier .msi.  
  
-   Exportez les informations de liaison vers un fichier .xml à l'aide de la commande ExportBindings.  
  
-   Importez une application d'un fichier .msi en utilisant la commande ImportApp.  
  
-   Utilisez la commande ImportBindings pour importer les informations de liaison dans un fichier .xml.  
  
-   Répertoriez les artefacts inclus dans une application ainsi que leurs identificateurs uniques locaux (LUID) en utilisant la commande ListApp.  
  
-   Dressez la liste de toutes les applications dans la base de données de gestion BizTalk pour le groupe BizTalk à l'aide de la commande ListApps.  
  
-   Servez-vous de la commande ListPackage pour répertorier les ressources dans un fichier .msi.  
  
-   Dressez la liste de tous les types d'artefacts pris en charge par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de la commande ListTypes.  
  
-   Utilisez la commande RemoveApp pour supprimer une application de la base de données de gestion BizTalk et de la console Administration de BizTalk.  
  
-   Utilisez la commande RemoveResource pour supprimer un artefact d'une application.  
  
-   Désinstallez une application de l'ordinateur local à l'aide de la commande UninstallApp.  
  
> [!IMPORTANT]
>  Vous ne pouvez pas utiliser les commandes BTSTask dans un script de pré-traitement ou de post-traitement qui s'exécute pendant l'importation d'une application. L'utilisation d'une telle commande peut entraîner l'échec de l'importation. En effet, les modifications apportées lors d'une importation ne sont pas visibles pour les scripts.  
  
 En outre, vous pouvez obtenir des informations sur la façon dont les couleurs de premier plan de la console peuvent être modifiées pour BTSTask. Si l'arrière-plan de votre console est blanc, vous aurez des difficultés à lire les données de sortie BTSTask de la console. Il se peut donc que vous deviez modifier les couleurs de premier plan de la console.  
  
> [!NOTE]
>  Lorsqu'un script est terminé, il renvoie zéro (0) pour indiquer qu'il s'est terminé correctement ou un nombre différent de zéro en cas d'échec.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Commande AddApp](../core/addapp-command.md)  
  
-   [Commande AddResource](../core/addresource-command.md)  
  
-   [Commande ExportApp](../core/exportapp-command.md)  
  
-   [Commande ExportBindings](../core/exportbindings-command.md)  

- [Commande de ExportParties](../core/exportparties-command.md)

- [Commande ExportSettings](../core/exportsettings-command.md)
  
-   [Commande ImportApp](../core/importapp-command.md)  
  
-   [Commande ImportBindings](../core/importbindings-command.md)  

- [Commande de ImportParties](../core/importparties-command.md)

- [Commande ImportSettings](../core/importsettings-command.md)
  
-   [Commande ListApp](../core/listapp-command.md)  
  
-   [Commande ListApps](../core/listapps-command.md)  
  
-   [Commande ListPackage](../core/listpackage-command.md)  
  
-   [Commande ListTypes](../core/listtypes-command.md)  
  
-   [Commande RemoveApp](../core/removeapp-command.md)  
  
-   [Commande RemoveResource](../core/removeresource-command.md)  
  
-   [Commande UninstallApp](../core/uninstallapp-command.md)  
  
-   [Comment modifier les couleurs de Console pour BTSTask](../core/how-to-edit-the-console-colors-for-btstask.md)