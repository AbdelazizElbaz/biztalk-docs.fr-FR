---
title: Compilation des mappages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, compiling
- XSLT, generating
- maps, validating
- BizTalk Mapper, compiling
- BizTalk Mapper, validating
ms.assetid: 967181d6-22a9-4a76-ae45-3317c0c6321b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346769519343afe9456a7b1e7cf9a3bd5bb159ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="compiling-maps"></a>Compilation des mappages
Lorsque vous validez des mappages, le composant de compilation du Mappeur BizTalk génère une feuille de style XSLT (Extensible Stylesheet Language Transformations). Cela entraîne la création d'un mappage compilé qui transforme un message d'instance défini par le schéma source en un message d'instance défini par le schéma de destination. La compilation d'un mappage met en œuvre les transformations et règles de structure spécifiées dans les pages de grille.  
  
 Les transformations, dont les liens font partie, sont traitées dans le même ordre que celui dans lequel les enregistrements et les champs apparaissent dans le schéma de destination. Par exemple, lorsque le Mappeur BizTalk atteint une destination **enregistrement** ou **champ** nœud avec un lien, le Mappeur BizTalk compile les propriétés de la liaison. L'action peut être une simple valeur de copie issue d'un enregistrement ou d'un champ du schéma source, ou peut impliquer plusieurs calculs basés sur des fonctoids et divers enregistrements et champs.  
  
 Le Mappeur BizTalk génère des avertissements dans le **sortie** fenêtre et **liste des tâches** fenêtre lorsque le compilateur rencontre une situation qui peut entraîner un résultat incorrect. Par exemple, si un fonctoid requiert un paramètre d’entrée et n’a aucun paramètre d’entrée, le Mappeur BizTalk génère un avertissement dans le **sortie** fenêtre. En général, évitez d'utiliser un mappage dans un environnement de production s'il génère des avertissements.  
  
 Un lien vers la feuille de style XSLT générée apparaît également dans le **sortie** fenêtre lorsque le mappage se compile correctement.  
  
 BizTalk Server se sert du mappage compilé pour opérer la conversion d'un message d'instance d'entrée dans un message d'instance de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Test de mappages](../core/testing-maps.md)   
 [Configuration de Transformation de données](../core/data-transformation-configuration.md)   
 [Correspondance au niveau de hiérarchie de nœuds](../core/node-hierarchy-level-matching.md)