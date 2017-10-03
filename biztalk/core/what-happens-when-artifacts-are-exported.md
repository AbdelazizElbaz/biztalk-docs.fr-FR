---
title: "Que se passe-t-il lorsque les artefacts sont exportées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting, artifacts
- artifacts, exporting
ms.assetid: accc9a81-01fb-4da7-a5a5-167835d393a2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d92a65889ea642706ae5c51849748fd8ad085a02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-artifacts-are-exported"></a>Effets de l'exportation d'artefacts
Cette rubrique décrit les effets de l'exportation d'artefacts. Vous pouvez exporter des artefacts de trois manières :  
  
-   Exportation d'une application BizTalk et de ses artefacts dans un fichier .msi BizTalk (Windows Installer)  
  
-   Exportation d'une stratégie dans un fichier .xml.  
  
-   Exportation de liaisons dans un fichier .xml.  
  
## <a name="exporting-a-biztalk-application"></a>Exportation d’une application BizTalk  
 Lorsque vous exportez une application BizTalk et les artefacts qu'elle contient, les informations de configuration de l'application et les données des artefacts sont exportées dans un fichier .msi BizTalk. La plupart des données des artefacts sont exportées à partir de la base de données de gestion BizTalk, sauf dans les cas suivants :  
  
-   Les données des stratégies sont exportées à partir de la base de données du moteur de règle du groupe.  
  
-   Les données des répertoires virtuels sont exportées à partir de la métabase Internet Information Services (IIS) si elles n'existent pas dans la base de données de gestion. Ce sera le cas lorsque le répertoire virtuel n’a pas été ajouté explicitement à l’application (comme décrit dans [comment ajouter un répertoire virtuel à une Application](../core/how-to-add-a-virtual-directory-to-an-application.md)) ou l’application n’a pas été importée dans ce groupe à partir d’un fichier .msi qui a été exporté à partir d’un autre groupe BizTalk.  
  
-   Les données des certificats sont exportées à partir du magasin de certificats Autres personnes sur l'ordinateur local, si elles n'existent pas dans la base de données de gestion. Ce sera le cas lorsque le certificat n’a pas été ajouté explicitement à l’application (comme décrit dans [comment ajouter un certificat à une Application](../core/how-to-add-a-certificate-to-an-application.md)) ou l’application n’a pas été importée dans ce groupe à partir d’un fichier .msi qui a été exporter à partir d’un autre groupe BizTalk. Les certificats sont exportés lors de l'exportation d'une application avec un port de réception auquel un certificat est associé. Les clés privées sont supprimées des certificats au moment de l'exportation.  
  
 Vous pouvez utiliser ce fichier .msi pour importer les artefacts de l'application, ainsi que l'ensemble de leurs données, dans une application d'un autre groupe BizTalk. Ce fichier .msi vous permet également d'installer l'application sur un ordinateur.  
  
## <a name="exporting-a-policy"></a>Exportation d’une stratégie  
 Lorsque vous utilisez la console d'administration pour exporter une stratégie pour une application ou un groupe BizTalk, elle génère un fichier .xml contenant les informations de stratégie. Vous pouvez importer ce fichier dans un autre groupe BizTalk pour y créer la stratégie, et permettre ainsi aux applications du groupe de l'utiliser. Vous pouvez également exporter des informations de stratégie pour une application à l'aide de BTSTask. Cependant, BTSTask ne comporte pas de commande permettant d'exporter le fichier .xml d'une stratégie. Vous pouvez à la place exporter le fichier .msi d'une application contenant uniquement la stratégie. Vous pouvez ensuite importer le fichier .msi dans une application d'un autre groupe.  
  
## <a name="exporting-bindings"></a>Exportation des liaisons  
 Vous pouvez exporter les liaisons d'un assembly, d'une application ou d'un groupe BizTalk à l'aide de la console d'administration ou de BTSTask. Lorsque vous procédez ainsi, BizTalk Server génère un fichier .xml contenant les informations de liaison pour le groupe, l'application ou l'assembly. Lorsque vous exportez des liaisons, vous pouvez également exporter les informations de tiers global pour le groupe. Vous pouvez ensuite ajouter ce fichier de liaison à une application ou l'importer dans une application ou un groupe BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il pour les artefacts au cours du déploiement](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [Exportation de stratégies, les liaisons et les Applications BizTalk](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Comment ajouter un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md)