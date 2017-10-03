---
title: "Déploiement d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bb4496-b1e9-400b-a849-a355381849ff
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61bc0e446e635fd4111804f7160651df6492a60c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-an-application"></a>Déploiement d’une Application
Le déploiement est la distribution logistique des artefacts de l’application pour vérifier que tous les composants nécessaires sont disponibles pour les systèmes qui en ont besoin. Ces artefacts incluent notamment BizTalk Server assemblys, .NET assemblys, schémas, mappages, liaisons, des règles d’entreprise et les certificats. L’application BizTalk peut être exploitée pour aider à déployer des artefacts à d’autres ordinateurs ajoutés au groupe ou pour l’environnement intermédiaire (lors du transport d’une application vers un autre environnement).  
  
 Il existe de nombreuses façons de déployer les artefacts BizTalk par exemple en les important dans le cadre d’une application à l’aide de l’Assistant de déploiement (à partir d’un fichier .msi), en les important à l’aide de BTSTask.exe, à les déployer à partir de Visual Studio ou à l’aide de MSBuild. Si vous les importez à l’aide de BTSTask.exe ou de les déployer à partir de Visual Studio, vous pouvez spécifier une application pour les déployer sur, ou laissez le nom d’application vide, auquel cas elles sont déployées à l’application par défaut.  
  
## <a name="deploying-by-using-an-msi-file"></a>Déploiement à l’aide d’un fichier .msi  
 Avec BizTalk Server, vous pouvez déployer une application et ses artefacts en les exportant vers un fichier .msi. (Pour plus d’informations sur les applications et artefacts, consultez [qu’est une Application BizTalk ?](http://go.microsoft.com/fwlink/?LinkId=154994) (http://go.microsoft.com/fwlink/?LinkId=154994). Déploiement d’une application BizTalk implique l’importation des artefacts de l’application dans la base de données de gestion BizTalk ainsi que les artefacts sur chaque ordinateur qui est membre du groupe. Déploiement vers un fichier .msi, tous les artefacts de l’application sérialise dans un package. Cela peut être effectué en effectuant une opération d’exportation à partir de la console d’Administration ou à l’aide de BTSTask.exe à partir de la ligne de commande. Une fois que vous avez un fichier .msi, vous pouvez déployer tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des assemblys à l’administration de BizTalk pour le groupe de base de données ou exécuter des scripts pour s’exécuter au moment de l’importation. Cela permet à l’aide de Microsoft Management Console (MMC) et d’effectuer une opération d’importation du fichier .msi (ou via une opération d’importation à partir de la ligne de commande BTSTASK). L’opération d’importation du fichier .msi crée l’application BizTalk de destination.  
  
 Le fichier .msi, vous pouvez déployer l’application sur un seul ordinateur, afin que tous les assemblys BizTalk Server et les assemblys de dépendance sont stockées dans le Global Assembly Cache sur l’ordinateur. L’ordinateur a ensuite tous les fichiers binaires dont il a besoin pour le moment de l’exécution. Dans cette opération, vous pouvez également déployer des services Web qui font partie de la solution, ou appliquer les modifications spécifiques à l’ordinateur par les scripts. Cette opération est effectuée en exécutant le fichier .msi. Vous pouvez effectuer cette opération sur chaque ordinateur exécutant BizTalk Server qui est membre du groupe BizTalk approprié. Vous pouvez également utiliser un fichier .msi pour installer une application sur un nouveau serveur ajouté à un groupe.  
  
 Si vous migrez votre application BizTalk à un nouveau groupe, vous devez exécuter l’installation .msi sur tous les serveurs dans le nouveau groupe. Vous devez importer le fichier .msi pour le groupe. Lorsque vous procédez ainsi, l’application et son contenu est installés sur tous les ordinateurs d’exécution dans le nouveau groupe et est également inscrits avec la base de données de gestion BizTalk pour le groupe. Vous pouvez également ajouter plusieurs fichiers de liaison vers un fichier .msi, outre les liaisons implicites. Chaque fichier de liaison supplémentaires peut être associé à un « environnement ». Lorsque plusieurs fichiers de liaison sont associés à une Application BizTalk au cours du déploiement, vous pouvez choisir les fichiers de liaison à utiliser basée sur l’environnement (de production, de mise en lots ou de test) à laquelle vous déployez.  
  
 Vous pouvez utiliser des scripts avec les fichiers .msi pour personnaliser un serveur (l’opération d’installation) ou le groupe (opération d’importation). Pour plus d’informations sur l’utilisation de scripts avec les fichiers .msi, consultez [à l’aide de Scripts de pré-traitement et post-traitement au déploiement d’Application personnaliser](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).  
  
 Pour obtenir la liste des étapes de déploiement d’une application, consultez [liste de vérification : déploiement d’une Application](../technical-guides/checklist-deploying-an-application.md).  
  
## <a name="exporting-an-applications-bindings-by-using-a-binding-file"></a>Exporter les liaisons d’une Application à l’aide d’un fichier de liaison  
 Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez exporter les liaisons d’une application vers un fichier de liaison et ensuite importer ces liaisons à partir du fichier de liaison à une autre application. Pour ce faire, l’application de destination doit déjà exister. la procédure d’importation ne crée pas de l’application. Le fichier de liaison est un fichier XML qui contient les liaisons de tous les artefacts dans une application, un groupe ou un assembly. Vous pouvez également exporter toutes les liaisons pour un groupe BizTalk, ou les liaisons pour un assembly BizTalk. Pour plus d’informations sur l’utilisation des liaisons, consultez [comment exporter les liaisons dans un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md) et [comment importer les liaisons à partir d’un fichier de liaison](../technical-guides/how-to-import-bindings-from-a-binding-file.md).  
  
 Vous pouvez également ajouter un fichier de liaison en tant que ressource dans un fichier .msi. Pour plus d’informations sur l’ajout d’un fichier de liaison en tant que ressource, consultez [comment exporter une Application dans un fichier .msi](../technical-guides/how-to-export-an-application-to-an-msi-file.md).  
  
 Pour plus d’informations sur le déploiement de l’application en général, consultez [gestion et déploiement d’applications BizTalk compréhension](http://go.microsoft.com/fwlink/?LinkId=154996) (http://go.microsoft.com/fwlink/?LinkId=154996).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md)  
  
-   [Problèmes connus avec le déploiement d’une Application](../technical-guides/known-issues-with-deploying-an-application.md)  
  
-   [Autorisations permettant de gérer une Application](../technical-guides/permissions-for-managing-an-application.md)  
  
-   [Artefacts qui doivent être uniques dans une Application](../technical-guides/artifacts-that-must-be-unique-in-an-application.md)  
  
-   [Déploiement et exportation d’une Application](../technical-guides/deploying-and-exporting-an-application.md)