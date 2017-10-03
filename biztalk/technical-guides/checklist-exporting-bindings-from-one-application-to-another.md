---
title: "Liste de vérification : Exportation des liaisons à partir d’une Application vers un autre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 152924e6-da64-4db9-a852-bdb4e79687fb
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df60a6fd1b266403a5c43b5f76bf7594cad4f41a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-exporting-bindings-from-one-application-to-another"></a>Liste de vérification : Exportation des liaisons à partir d’une Application vers un autre
Cette rubrique décrit les étapes nécessaires pour transférer les liaisons d’une application à une autre application dans l’environnement soit un développement ou de production. Ce processus est similaire au processus de déploiement d’une application à l’aide d’un fichier .msi. Toutefois, lorsque vous déployez une application à l’aide d’un fichier .msi, le processus crée automatiquement l’application. Lorsque vous transférez les liaisons d’une application vers un autre, en revanche, l’application de destination doit déjà exister.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Assurez-vous que vous disposez des autorisations appropriées pour effectuer l’opération d’exportation.|[Autorisations permettant de gérer une Application](../technical-guides/permissions-for-managing-an-application.md)|  
|Créez une application de destination pour importer les liaisons de l’application dans.|-   [Création d’une Application](../technical-guides/creating-an-application.md)<br />-Section « Création d’une Application BizTalk » [meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md)|  
|Exporter les liaisons d’une application source dans un fichier de liaison.|-   [Comment exporter des liaisons vers un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md)<br />-Section « Exportation d’une Application BizTalk » [meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md)<br />-Section « Exportation d’une Application BizTalk » [problèmes connus avec le déploiement d’une Application](../technical-guides/known-issues-with-deploying-an-application.md).|  
|Importer les liaisons dans un fichier de liaison à l’application de destination.|-   [Comment importer des liaisons à partir d’un fichier de liaison](../technical-guides/how-to-import-bindings-from-a-binding-file.md)<br />-« L’importation d’une Application BizTalk » de section de [meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md)<br />-« L’importation d’une Application BizTalk » de section de [problèmes connus avec le déploiement d’une Application](../technical-guides/known-issues-with-deploying-an-application.md).|