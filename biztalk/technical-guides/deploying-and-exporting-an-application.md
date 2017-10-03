---
title: "Déploiement et d’exportation d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4106a0a7-878d-4052-8eca-02d546233048
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b33762f50f32dda58f1453fde7be37bc959af6aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-exporting-an-application"></a>Déploiement et exportation d’une Application
Cette section contient des informations détaillées sur la façon d’effectuer les étapes impliquées dans le déploiement d’une application BizTalk. Les rubriques de cette section prennent en charge les listes de vérification suivantes :  
  
-   [Liste de vérification : Déploiement d’une Application](../technical-guides/checklist-deploying-an-application.md), qui montre comment déployer une application dans un environnement de développement, l’exporter dans un fichier .msi, puis l’importer dans un environnement de production à partir du fichier .msi.  
  
-   [Liste de vérification : Exportation des liaisons à partir d’une Application vers un autre](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md), qui montre comment exporter des liaisons à partir d’une application dans une autre application, que ce soit un environnement de développement ou de production.  
  
 Vous pouvez utiliser les outils suivants pour déployer et gérer une application BizTalk :  
  
|Outil|Utiliser|  
|----------|---------|  
|Console d’Administration de BizTalk Server|À partir de l’interface graphique utilisateur, vous pouvez effectuer toutes les opérations de déploiement et la gestion d’une application BizTalk, notamment les suivantes :<br /><br /> -Démarrage de l’importation, l’Installation et les Assistants Exportation<br />-Ajouter et supprimer les artefacts d’une application et effectuer d’autres modifications à l’application<br />-Générer des fichiers .msi de BizTalk Server pour une application BizTalk<br />-Installation de l’application sur un ordinateur à partir du fichier .msi ou l’importation de l’application à partir du fichier .msi dans un autre groupe BizTalk<br />-Importer les liaisons pour une application à partir d’un fichier de liaison<br /><br /> Pour plus d’informations sur la console d’administration, consultez [à l’aide de la Console Administration de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154689) (http://go.microsoft.com/fwlink/?LinkID=154689).|  
|outil de ligne de commande BTSTask|Vous pouvez effectuer de nombreuses tâches de gestion d’applications à partir de la ligne de commande. Pour plus d’informations sur l’outil de ligne de commande, consultez [référence de ligne de commande BTSTask](http://go.microsoft.com/fwlink/?LinkId=155003) (http://go.microsoft.com/fwlink/?LinkId=155003).|  
|API de création de scripts et de programmabilité|Vous pouvez utiliser Microsoft Windows Management Instrumentation (WMI) ou le Modèle objet de l'Explorateur BizTalk pour créer et exécuter des scripts automatisant de nombreuses tâches de gestion d'applications. Pour plus d’informations sur les scripts, consultez [référence de classe WMI](http://go.microsoft.com/fwlink/?LinkId=155004) (http://go.microsoft.com/fwlink/?LinkId=155004).|  
|[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]|Vous pouvez créer des assemblys BizTalk dans Visual Studio, utilisez la commande de déploiement pour les déployer automatiquement dans une application BizTalk et utilisez l’Explorateur BizTalk pour configurer les artefacts de l’application à partir de Visual Studio. Pour plus d’informations sur l’utilisation de Visual Studio, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d’une Application](../technical-guides/creating-an-application.md)  
  
-   [Déploiement d’un Assembly](../technical-guides/deploying-an-assembly.md)  
  
-   [Ajout d’artefacts à une Application](../technical-guides/adding-artifacts-to-an-application.md)  
  
-   [Comment exporter une Application vers un fichier .msi](../technical-guides/how-to-export-an-application-to-an-msi-file.md)  
  
-   [Comment exporter des liaisons vers un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md)  
  
-   [L’ajout d’un fichier de liaison à un Application1](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)  
  
-   [Comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md)  
  
-   [Comment installer une Application](../technical-guides/how-to-install-an-application.md)  
  
-   [Comment importer des liaisons à partir d’un fichier de liaison](../technical-guides/how-to-import-bindings-from-a-binding-file.md)  
  
-   [Test d’une Application](../technical-guides/testing-an-application.md)  
  
-   [Comment ajouter une référence à une Application](../technical-guides/how-to-add-a-reference-to-an-application.md)