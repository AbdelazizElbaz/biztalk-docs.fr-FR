---
title: "Gérer les assemblys .NET, certificats et autres ressources | Documents Microsoft"
description: "Liens pour ajouter des fichiers de liaison, les certificats, les assemblys, répertoires virtuels, fichiers, etc. dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efe27a11-19d8-4eb3-9f8c-f4336e4c3d66
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb74762bdf08e6e9e2a79650a26dedb0915ea8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-net-assemblies-certificates-and-other-resources"></a>Gérer les assemblys .NET, certificats et autres ressources

## <a name="overview"></a>Vue d'ensemble
Cette rubrique fournit des instructions sur l'utilisation de la console Administration de BizTalk Server et de l'outil de ligne de commande BTSTask pour la gestion des types suivants d'artefacts de ressource d'une application BizTalk. Ces artefacts de ressource ne peuvent pas être automatiquement déployés dans une application BizTalk à partir de Visual Studio. Vous devez donc les ajouter manuellement à l'application. Une fois que vous les avez ajoutés à l'application, cependant, vous pouvez les importer, exporter et installer sous la forme d'une unité avec l'application et ses autres artefacts.  
  
-   **Les fichiers.** Vous pouvez inclure les fichiers ad hoc, tels qu'un fichier Lisezmoi. Lorsque vous installez l'application, les fichiers sont copiés dans le dossier d'installation.  
  
-   **Certificats.** Vous pouvez ajouter un fichier de certificat à une application afin de pouvoir transférer le certificat d'un groupe BizTalk à un autre, au sein d'une application. Vous attribuez des certificats aux ports d'envoi et emplacements de réception afin de vérifier les identités et d'établir des liaisons sécurisées.  
  
-   **Composants COM et COM +.** Vous pouvez inclure des composants COM gérés et COM+ gérés afin de fournir des fonctionnalités supplémentaires à une application BizTalk.  
  
-   **Assemblys .NET.** Vous pouvez ajouter à une application BizTalk des assemblys .NET qui ne sont pas des assemblys spécifiques à BizTalk. (Les assemblys BizTalk sont des assemblys .NET contenant des orchestrations, pipelines, schémas ou mappages BizTalk.)  
  
-   **Fichiers de définition BAM.** Pour faciliter le déploiement de l'analyse BAM, vous pouvez créer une application BizTalk et lui ajouter des définitions d'analyse BAM. Vous pouvez ensuite utiliser les fonctionnalités de déploiement d'applications BizTalk pour déployer les définitions d'analyse BAM dans différents environnements.  
  
-   **Fichiers de liaison.** Vous pouvez ajouter des fichiers de liaison à une application afin d'accélérer et de faciliter le déplacement de cette application d'un environnement de déploiement à un autre.  
  
-   **Répertoires virtuels.** Vous pouvez ajouter des répertoires virtuels à votre application, afin qu'ils soient déployés avec celle-ci.  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Ajouter un fichier à une Application](../core/how-to-add-a-file-to-an-application.md)  
  
-   [Ajouter un certificat à une Application](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [Ajouter un composant COM à une Application](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [Ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [Ajouter un artefact BAM à une Application](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [Ajouter un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
-   [Ajouter un répertoire virtuel à une Application](../core/how-to-add-a-virtual-directory-to-an-application.md)  
  
-   [Modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)  
  
-   [Supprimer un Assembly .NET, certificat ou autre artefact de ressource d’une Application](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)