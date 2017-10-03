---
title: "Déploiement localisée des fichiers XML de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, unicode mapping
- unicode mapping [BAM]
ms.assetid: 8e7e3431-cd20-45db-b7f2-0df23e9df42b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3452f13569ca6a0c0bb5843995c07a15b30f4da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-localized-bam-xml-files"></a>Déploiement de fichiers XML d'analyse BAM localisés
Microsoft SQL Server Analysis Services prend en charge le mappage Unicode. Le mappage Unicode de SQL Server Analysis Services et Visual Basic Unicode pose cependant des problèmes identifiés de corruption de caractères. En effet, si les paramètres régionaux ne sont pas définis sur la langue localisée appropriée au moment où la conversion ANSI-Unicode se produit, cette conversion n'est pas effectuée avec les bonnes informations régionales et une corruption de caractères a lieu.  
  
 Avant de pouvoir correctement déployer le fichier XML de définition d'analyse BAM qui contient des caractères localisés, vous devez basculer les paramètres régionaux de votre système sur les paramètres régionaux appropriés.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)