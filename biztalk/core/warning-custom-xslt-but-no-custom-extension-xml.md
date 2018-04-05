---
title: 'Avertissement : XSLT personnalisé, mais aucun XML avec extensions personnalisées | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.customXsltButNoCustomExtensionXML
ms.assetid: af008ac2-e9ae-4753-a5ba-bf4dbb711a4e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b67591e0e0dbb6b3ecac9aee1566c3245c9969a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-xslt-but-no-custom-extension-xml"></a>Avertissement : XSLT personnalisé, mais aucun XML avec extensions personnalisées
**Code d’erreur**  
  
 btm1034  
  
 **Explication**  
  
 Le **chemin du XSLT personnalisé** propriété a été remplacée, mais pas les **XML avec extensions personnalisées** propriété substituée. Si cela est intentionnel, ne tenez pas compte de cet avertissement.  
  
 Mappeur BizTalk va utiliser l’élément XSLT défini par le **chemin du XSLT personnalisé** propriété et générer un fichier de mappage XML avec extensions factice. Si vous appelez des assemblys externes depuis l’élément XSLT personnalisé fourni, vous devez spécifier un fichier en utilisant le **XML avec extensions personnalisées** propriété qui contient le préfixe de mappage de nom d’assembly.  
  
 **Action de l’utilisateur**  
  
 Si la condition indiquée par cet avertissement n’est pas intentionnelle, vous devez attribuer une valeur compatible à la **XML avec extensions personnalisées** propriété ou supprimez la valeur de remplacement pour le **chemin du XSLT personnalisé** propriété.