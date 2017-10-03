---
title: "Configuration de l’environnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43027efc-acec-4110-96bd-cc4a19daaeab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c91221162cccb7b6821c0edad12f8e76de2f10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-environment"></a>Configuration de l’environnement
**Pour définir l’environnement :**  
  
1.  Assurez-vous que le Pack de messages SWIFT est configuré. Consultez la documentation du Pack de messages Swift pour configurer la même.  
  
2.  Exécutez le script SQL  *\<lecteur >*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql. Modifiez le nom de la base de données dans le script sql si le Swift et MessagePack sont configurés pour le nom de la base de données autre que A4Swift.  
  
3.  Définir la valeur de clé « datasource » comme nom d’ordinateur et la clé « database » comme nom de la base de données (pour lesquels la Swift et MessagePack est configuré) dans le fichier  *\<lecteur >*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools\DataImport\DataImport.exe.config.  
  
    > [!NOTE]
    >  Le fichier de données d’entrée ne doit pas être dans le même dossier que le fichier DataImport.exe.  
  
4.  Exécutez l’utilitaire DataImport pour importer des données dans les tables BICplusIBAN et SEPA.